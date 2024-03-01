# AQT

# AQT API WORKFLOW /api

# Version 1 /V1

- User => [/user](#user-api)
- Global => [/global](#global)
- dashboard => [/dashboard](#dashboard)
- key => [/key](#key)

## User api

  - post request

    - [/admin-signup](#admin-signup)
    - [/signIn](#signin)
    - [/refresh-token](#refresh-token)
    - [/change-password](#change-password)
    - [/forgot-password](#forgot-password)
    - [/reset-password](#reset-password)
    - [/registration](#registration)
    - [/info](#info)
    - [/company-product](#company-product)
    - [/upload](#upload)

  - get request
    - [/](#root)
    - [/info](#info)
    - [/profile](#profile)
    - [/companies](#companies)
    - [/company/:id](#companyid)
    - [/company-product](#company-product)
    - [/company-product/:id](#company-productid)
    - [/partner](#partner)
    - [/partner/:id](#partnerid)
    - [/client](#client)
    - [/client/:id](#clientid)
    
  - put request
    - /info
    - /profile
    - /company/:id
    - /company-product
    - /partner/:id
    - /client/:id

## Global

- Get request
  - [/countries](#countries)
  - [/states/:countryId](#statesid)
  - [/cities/:stateId](#citiesid)
  - [/profession](#profession)
  - [/investment-market-ext](#investment-market-exp)
  - [/investment-interest](#investment-interest)

## Dashboard

- Get request
  - [/admin](#admin)
  - [/partner](#partner-1)
  - [/company](#companystateid) => /:stateId require
  - [/client](#clientstateid) => not implemented , It's functionality is same as compaany route

## Key-get-request
   ### /admin-signup
  - @ arguments => none
    1. examples :
  ```json: 
        {
          
        }

  ```
    
  - @ issues: 
    1. no issues found
    1. examples :
  ```json: 
        {
           "status": 200,
    "data": "CqOTLSTGa9yqXTPFA",
    "message": "Random key generated successfully!"
        } 
  ```
 



## User-post-request-api /user

  ### /admin-signup
  - Body => firstName, lastName, username, password, emailId, phoneNo
    1. examples :
  ```json: 
        {
          "firstName":"Rahul",
          "lastName":"Sharma",
          "username":"rahul",
          "password":"12345678",
          "emailId":"rahul@gmail.com",
          "phoneNo":"1234567890"
        }

  ```
    
  - @ issues: 
    1. We can create multiple user using same username, email and phoneNo
  - @ response =>  status, success, time, message
    1. examples :
  ```json: 
        {
          "status": 200,
          "success": true,
          "time": "2024-03-01T12:06:48+05:30",
          "message": "User created successfully."
        } 
  ```
 
  ### /signIn
  - @ arguments => username, password
    1. examples :
  ```json: 
        {
          "username":"vikas",
          "password":"12345678"
        }

  ```
    
  - @ issues: 
    1. No issues yet
  - @ response =>  status, success,detail,  time, message
    1. examples :
  ```json: 
        {
           "status": 200,
    "success": true,
    "detail": {
        "userId": 34,
        "username": "vikas",
        "userType": "PARTNER",
        "userTypeId": 2,
        "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjM0LCJpYXQiOjE3MDkyNzYxMjIsImV4cCI6MTcwOTI3OTcyMn0.3OmqRq8J-P-JOaVJeVPZ17iuyWUdTPU88d4lP_U1zL0",
        "refreshToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjM0LCJpYXQiOjE3MDkyNzYxMjIsImV4cCI6MTcxMTg2ODEyMn0.flBw4pBuPA-c18obhuoo8WrpwjWBmtaNWNysgjK2Ow8",
        "expiresIn": "1h"
    },
    "time": "2024-03-01T12:25:20+05:30",
    "message": "User sign-in successfully."
        } 
  ```
 
  ### /refresh-token
  - @ arguments => refreshToken
    1. examples :
  ```json: 
        {
          "refreshToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjIyLCJpYXQiOjE3MDkxODIzODcsImV4cCI6MTcxMTc3NDM4N30.T8fiLExzTCrdQ1bzoOwb-_jEiF1DbV7IvMhF_5eBWC4"
        }

  ```
    
  - @ issues: 
    1. No issues found yet
  - @ response =>  status, success,detail,  time, message
    1. examples :
  ```json: 
        {
          "status": 200,
    "success": true,
    "detail": {
        "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjIyLCJpYXQiOjE3MDkyNzY0MDMsImV4cCI6MTcwOTI4MDAwM30.XqYAsmUiqVUC0FTS-bmUh-XnRwoMpIVbVEjf52khIh0",
        "refreshToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjIyLCJpYXQiOjE3MDkxODIzODcsImV4cCI6MTcxMTc3NDM4N30.T8fiLExzTCrdQ1bzoOwb-_jEiF1DbV7IvMhF_5eBWC4",
        "expiresIn": "1h"
    },
    "time": "2024-03-01T12:30:03+05:30",
    "message": "New access token."
        } 
  ```
 
  ### /change-password
  - @ arguments => 
    1. body
      - oldPassword, newPassword, confirmPassword
      - examples :
  ```json: 
        {
          "oldPassword":"87654321", "newPassword":"12345678", "confirmPassword":"12345678"
        }

  ```
    2. header
      - Authorization
      - example: 
        
  ```
  Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjIyLCJpYXQiOjE3MDkyNzY0MDMsImV4cCI6MTcwOTI4MDAwM30.XqYAsmUiqVUC0FTS-bmUh-XnRwoMpIVbVEjf52khIh0
  ```
      
    
  - @ issues: 
    1. No issues found yet
  - @ response =>  status, success,  time, message
    1. examples :
  ```json: 
        {
          "status": 200,
    "success": true,
    "time": "2024-03-01T12:35:44+05:30",
    "message": "Successfully password changed."
        } 
  ```
 
  ### /forgot-password
  - @ arguments => email
    1. examples :
  ```json: 
        {
          "email":"satyaprakash5056742@gmail.com"
        }

  ```
    
  - @ issues: 
    1. No issues found yet
  - @ response =>  status, success, time, message
    1. examples :
  ```json: 
        {
          "status": 200,
    "success": true,
    "time": "2024-03-01T12:49:14+05:30",
    "message": "Successfully sends reset password link to your email."
        } 
  ```

  ### /reset-password
  - @ arguments => 
    1. body
      - newPassword, confirmPassword
      - examples :
  ```json: 
        {
           "newPassword":"87654321",
   "confirmPassword":"87654321"
        }

  ```
    2. header
      - Authorization
      - example: 
        
  ```
  Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjIyLCJpYXQiOjE3MDkyNzY0MDMsImV4cCI6MTcwOTI4MDAwM30.XqYAsmUiqVUC0FTS-bmUh-XnRwoMpIVbVEjf52khIh0
  ```
      
    
  - @ issues: 
    1. No issues found yet
  - @ response =>  status, success,  time, message
    1. examples :
  ```json: 
        {
          "status": 200,
    "success": true,
    "time": "2024-03-01T12:55:10+05:30",
    "message": "Successfully password changed."
        } 
  ```
   

  ### /registration
  - @ arguments => 
    1. body
      - newPassword, confirmPassword
      - examples :
  ```json: 
        {
           "firstName":"sangam",
      "lastName":"yadav",
      "email":"rahulsharma@gmail.com",
      "phoneNo":"1234567890",
      "type":"company",
      "gender":"male",
      "dob":"2023-06-30",
      "address":"Bhathat",
      "city":"Gorakhpur",
      "stateId":"4022",
      "countryId":"101",
      "zipCode":"273013",
   "smProfile":"http://google.com",
      "whatDescribeYouBestId":"1",
      "whatDescribeYouBestText":"Business Owner",
      //* client
    //   "lastInvestment":"null",
    //   "investmentInterestId",
    //   investmentInterestText,
      //* company
      "cmpName":"aqt_local",
      "cmpAddress":"Noida",
      "cmpDirectorName":"satya",
    //   cmpProfile,
      "cmpRegistrationDate":"2024-02-29",
      "cmpEmail":"company_local@gmail.com",
      "cmpCity":"Noida",
      "cmpStateId":"4022",
      "cmpCountryId":"101",
      "cmpZipcode":"273013",
      "businessType":"B2bB",
      "fundsRequirement":"none",
      "yearInBusiness":"2023"
    //   //* partner
    //   officeName,
    //   officeAddress,
    //   officeCity,
    //   officeStateId,
    //   officeCountryId,
    //   officeZipcode,
    //   investmentMarketExpId,
    //   investmentMarketExpText,
    //   reference
        }

  ```
    2. header
      - Authorization
      - example: 
        
  ```
  Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjIyLCJpYXQiOjE3MDkyNzY0MDMsImV4cCI6MTcwOTI4MDAwM30.XqYAsmUiqVUC0FTS-bmUh-XnRwoMpIVbVEjf52khIh0
  ```
      
    
  - @ issues: 
    1. No issues found yet
  - @ response =>  status, success,  time, message
    1. examples :
  ```json: 
        {
           "status": 200,
    "success": true,
    "time": "2024-03-01T14:01:09+05:30",
    "message": "User created successfully."
        } 
  ```

  ### /info
  - @ arguments => 
    1. body
      - newPassword, confirmPassword
      - examples :
  ```json: 
        {
          "bankName":"state bank of ",
      "bankBranchName":"Bhatha",
      "bankAccountNo":"12345678905",
      "aadhar":"123456789022",
      "pan":"1234567870",
      "dematStatus":false
    //       dematAccountNo,
    //       dpId,
    //       dpName
        }

  ```
    2. header
      - Authorization
      - example: 
        
  ```
  Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjIyLCJpYXQiOjE3MDkyODk2NTQsImV4cCI6MTcwOTI5MzI1NH0.AjVt4ZMRqArOKtl9AXUZQiIQ_2xNL0Mb2FXsBAUw56s
  ```
      
    
  - @ issues: 
    1. No issues found yet
  - @ response =>  status, success,  time, message
    1. examples :
  ```json: 
        {
            "status": 200,
    "success": true,
    "time": "2024-03-01T16:13:01+05:30",
    "message": "Successfully saved bank information."
        } 
  ```

  ### /company-product
  - @ arguments => 
    1. body
      - newPassword, confirmPassword
      - examples :
  ```json: 
            {
        "cmpId":"3",
        "isin":"12",
        "productName":"toothbrush",
        "shares":"10",
        "cost":"20"
      }

  ```
    2. header
      - Authorization
      - example: 
        
  ```
  Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjIyLCJpYXQiOjE3MDkyODk2NTQsImV4cCI6MTcwOTI5MzI1NH0.AjVt4ZMRqArOKtl9AXUZQiIQ_2xNL0Mb2FXsBAUw56s
  ```
      
    
  - @ issues: 
    1. No issues found yet
  - @ response =>  status, success,  time, message
    1. examples :
  ```json: 
        {
            "status": 200,
    "success": true,
    "time": "2024-03-01T16:17:42+05:30",
    "message": "Company product created successfully."
        } 
  ```

  ### /upload
  - @ arguments => 
    1. body => It should be form-data (for image)
      - file[type: File array], profile,
      - examples :
  ```form-data: 
            {
        "file"[file format]:[file](should be a file),
        "profile"[text format]:true (boolean),
        
      }

  ```
    2. header
      - Authorization
      - example: 
        
  ```
  Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjIyLCJpYXQiOjE3MDkyODk2NTQsImV4cCI6MTcwOTI5MzI1NH0.AjVt4ZMRqArOKtl9AXUZQiIQ_2xNL0Mb2FXsBAUw56s
  ```
      
    
  - @ issues: 
    1. No issues found yet
  - @ response =>  status, success,  time, message
    1. examples :
  ```json: 
        {
             "status": 200,
    "success": true,
    "time": "2024-03-01T16:26:16+05:30",
    "message": "Successfully uploaded."
        } 
  ```


## user-get-request-api /user

  ### /
   
  - @ arguments => 
    1. body => None
    2. header
      - Authorization
      - example: 
        
  ```
  Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjIyLCJpYXQiOjE3MDkyODA2NjgsImV4cCI6MTcwOTI4NDI2OH0.Hma4dZnIYLsiJaFSs43GiPOGJQupI4MJBKeP8xSkoyM
  ```    
    
  - @ issues: 
    1. No issues found yet
  - @ response =>  status, success,  time, message
    1. examples :
  ```json: 
        {
           "status": 200,
    "success": true,
    "detail": {
        "count": 7,
        "rows": [
            {
                "id": 40,
                "firstName": "sangam",
                "lastName": "yadav",
                "email": "rahulsharma@gmail.com",
                "contactNo": "1234567890",
                "phoneNo": "1234567890",
                "status": "I",
                "image": null,
                "userType": "COMPANY"
            },
            {
                "id": 37,
                "firstName": "sangam",
                "lastName": "yadav",
                "email": "satyaprakash505674@gmail.com",
                "contactNo": "1234567890",
                "phoneNo": "1234567890",
                "status": "I",
                "image": null,
                "userType": "COMPANY"
            },
            {
                "id": 36,
                "firstName": "vinod",
                "lastName": "Sharma",
                "email": "vinod@gmail.com",
                "contactNo": "1234567890",
                "phoneNo": "1234567890",
                "status": "A",
                "image": null,
                "userType": "CLIENT"
            },
            {
                "id": 35,
                "firstName": "shivam",
                "lastName": "mishra",
                "email": "shivam@gmail.com",
                "contactNo": "1234567890",
                "phoneNo": "1234567890",
                "status": "A",
                "image": null,
                "userType": "COMPANY"
            },
            {
                "id": 34,
                "firstName": "viaks",
                "lastName": "kumar jaiswal",
                "email": "vikas@gmail.com",
                "contactNo": "1234567890",
                "phoneNo": "1234567890",
                "status": "A",
                "image": null,
                "userType": "PARTNER"
            },
            {
                "id": 33,
                "firstName": "Rahul",
                "lastName": "Sharma",
                "email": "rahul@gmail.com",
                "contactNo": "1234567890",
                "phoneNo": "1234567890",
                "status": "A",
                "image": null,
                "userType": "ADMINSTRATOR"
            },
            {
                "id": 27,
                "firstName": "satyaprakash ",
                "lastName": "yadav",
                "email": "satyaprakash5056742@gmail.com",
                "contactNo": "1234567890",
                "phoneNo": "1234567890",
                "status": "A",
                "image": null,
                "userType": "ADMINSTRATOR"
            }
        ]
    },
    "time": "2024-03-01T14:37:30+05:30",
    "message": "Successfully fetched company listing."
        } 
  ```
   
  ### /info
   
  - @ arguments => 
    1. body => None
    2. header
      - Authorization
      - example: 
        
  ```
  Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjIyLCJpYXQiOjE3MDkyODA2NjgsImV4cCI6MTcwOTI4NDI2OH0.Hma4dZnIYLsiJaFSs43GiPOGJQupI4MJBKeP8xSkoyM
  ```    
    
  - @ issues: 
    1. No issues found yet
  - @ response =>  status, success,  time, message
    1. examples :
  ```json: 
        {
          "status": 200,
    "success": true,
    "detail": {
        "id": 2,
        "aadhar": "123456789012",
        "pan": "1234567890",
        "bankName": "state bank of india",
        "bankBranchName": "Bhathat",
        "bankAccountNo": "12345678909",
        "dematAccountNo": "1234567890123456",
        "dpId": "12345678",
        "dpName": "dp name",
        "createdBy": 22,
        "createdOn": "2024-02-29T11:27:04.000Z",
        "updatedOn": "2024-02-29T11:49:16.000Z",
        "updatedBy": null
    },
    "time": "2024-03-01T14:10:32+05:30",
    "message": "Successfully fetched profile."
        } 
  ```
   

  ### /profile
   
  - @ arguments => 
    1. body => None
    2. header
      - Authorization
      - example: 
        
  ```
  Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjIyLCJpYXQiOjE3MDkyODA2NjgsImV4cCI6MTcwOTI4NDI2OH0.Hma4dZnIYLsiJaFSs43GiPOGJQupI4MJBKeP8xSkoyM
  ```    
    
  - @ issues: 
    1. No issues found yet
  - @ response =>  status, success,  time, message
    1. examples :
  ```json: 
        {
          "status": 200,
    "success": true,
    "detail": {
        "user_id": 22,
        "first_name": "satya",
        "last_name": null,
        "username": "satya",
        "email_id": "satya@gmail.com",
        "contact_no": "1234567891",
        "dob": "2013-04-01",
        "address": "vaishali",
        "city": "Noida",
        "state_id": null,
        "country_id": null,
        "zip_code": null,
        "gender": null,
        "status": "A",
        "image": null,
        "created_by": null,
        "created_on": "2024-02-28T11:03:42.000Z",
        "updated_on": "2024-03-01T07:25:12.000Z",
        "updated_by": 22,
        "userTypes": [
            {
                "userTypeId": 1,
                "userType": "ADMINSTRATOR"
            }
        ],
        "bankDetails": true,
        "dematDetails": true
    },
    "time": "2024-03-01T14:14:38+05:30",
    "message": "Successfully fetched profile."
    }
  ```
   

  ### /companies
   
  - @ arguments => 
    1. body => None
    2. header
      - Authorization
      - example: 
        
  ```
  Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjIyLCJpYXQiOjE3MDkyODA2NjgsImV4cCI6MTcwOTI4NDI2OH0.Hma4dZnIYLsiJaFSs43GiPOGJQupI4MJBKeP8xSkoyM
  ```    
    
  - @ issues: 
    1. No issues found yet
  - @ response =>  status, success,  time, message
    1. examples :
  ```json: 
        {
         "status": 200,
    "success": true,
    "detail": {
        "count": 2,
        "rows": [
            {
                "id": 4,
                "name": "aqt_local",
                "address": "Noida",
                "profile": null,
                "directorName": "satya",
                "registrationDate": "2024-02-29",
                "mail": "company_local@gmail.com",
                "city": "Noida",
                "status": "I"
            },
            {
                "id": 3,
                "name": "aqt",
                "address": "Noida",
                "profile": "smart",
                "directorName": "satya",
                "registrationDate": "2024-02-29",
                "mail": "company@gmail.com",
                "city": "Noida",
                "status": "I"
            }
        ]
    },
    "time": "2024-03-01T14:18:44+05:30",
    "message": "Successfully fetched company listing."
    }
  ```
   

  ### /company/:id
   
  - @ arguments => 
    1. body => None
    2. header
      - Authorization
      - example: 
        
  ```
  Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjIyLCJpYXQiOjE3MDkyODA2NjgsImV4cCI6MTcwOTI4NDI2OH0.Hma4dZnIYLsiJaFSs43GiPOGJQupI4MJBKeP8xSkoyM
  ```    
    
  - @ issues: 
    1. No issues found yet
  - @ response =>  status, success,  time, message
    1. examples :
  ```json: 
        {
         "status": 200,
    "success": true,
    "detail": {
        "firstName": "sangam",
        "lastName": "yadav",
        "email": "satyaprakash505674@gmail.com",
        "phoneNo": "1234567890",
        "dob": "2023-06-30",
        "cmpName": "aqt",
        "cmpAddress": "Noida",
        "cmpImg": null,
        "cmpDirectorName": "satya",
        "cmpProfile": "smart",
        "cmpRegistrationDate": "2024-02-29",
        "cmpEmail": "company@gmail.com",
        "document": null,
        "cmpCity": "Noida",
        "cmpStateId": 4022,
        "cmpCountryId": 101,
        "cmpStatus": "I",
        "cmpZipcode": "273013",
        "smProfile": "http://google.com",
        "businessType": "B2bB",
        "fundsRequirement": "none",
        "yearInBusiness": 2023,
        "cmpCreatedOn": "2024-02-29T11:21:03.000Z",
        "cmpUpdatedOn": "2024-03-01T04:12:10.000Z",
        "cmpCityId": 133230,
        "cmpStateName": "Uttar Pradesh",
        "cmpCountryName": "India"
    },
    "time": "2024-03-01T14:21:17+05:30",
    "message": "Successfully fetched profile."
    }
  ```
   

  ### /company-product
   
  - @ arguments => 
    1. body => None
    2. header
      - Authorization
      - example: 
        
  ```
  Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjIyLCJpYXQiOjE3MDkyODA2NjgsImV4cCI6MTcwOTI4NDI2OH0.Hma4dZnIYLsiJaFSs43GiPOGJQupI4MJBKeP8xSkoyM
  ```    
    
  - @ issues: 
    1. No issues found yet
  - @ response =>  status, success,  time, message
    1. examples :
  ```json: 
        {
         "success": true,
    "detail": {
        "count": 1,
        "rows": [
            {
                "id": 5,
                "isin": "Noida",
                "productName": "toothbrush",
                "cmpId": 3,
                "shares": 100,
                "cost": 20,
                "status": "I",
                "cmpName": "aqt"
            }
        ]
    },
    "time": "2024-03-01T14:22:58+05:30",
    "message": "Successfully fetched company listing."
    }
  ```
   

  ### /company-product/:id
   
  - @ arguments => 
    1. body => None
    2. header
      - Authorization
      - example: 
        
  ```
  Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjIyLCJpYXQiOjE3MDkyODA2NjgsImV4cCI6MTcwOTI4NDI2OH0.Hma4dZnIYLsiJaFSs43GiPOGJQupI4MJBKeP8xSkoyM
  ```    
    
  - @ issues: 
    1. No issues found yet
  - @ response =>  status, success,  time, message
    1. examples :
  ```json: 
        {
         "status": 200,
    "success": true,
    "detail": {
        "id": 5,
        "isin": "Noida",
        "productName": "toothbrush",
        "shares": 100,
        "cost": 20,
        "status": "I"
    },
    "time": "2024-03-01T14:26:19+05:30",
    "message": "Successfully fetched profile."
    }
  ```
   

  ### /partner
   
  - @ arguments => 
    1. body => None
    2. header
      - Authorization
      - example: 
        
  ```
  Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjIyLCJpYXQiOjE3MDkyODA2NjgsImV4cCI6MTcwOTI4NDI2OH0.Hma4dZnIYLsiJaFSs43GiPOGJQupI4MJBKeP8xSkoyM
  ```    
    
  - @ issues: 
    1. No issues found yet
  - @ response =>  status, success,  time, message
    1. examples :
  ```json: 
        {
          "status": 200,
    "success": true,
    "detail": {
        "count": 1,
        "rows": [
            {
                "id": 34,
                "firstName": "viaks",
                "lastName": "kumar jaiswal",
                "email": "vikas@gmail.com",
                "contactNo": "1234567890",
                "phoneNo": "1234567890",
                "status": "A",
                "image": null,
                "userType": "PARTNER"
            }
        ]
    },
    "time": "2024-03-01T14:28:04+05:30",
    "message": "Successfully fetched partner listing."
    }
  ```
   

  ### /partner/:id
   
  - @ arguments => 
    1. body => None
    2. header
      - Authorization
      - example: 
        
  ```
  Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjIyLCJpYXQiOjE3MDkyODA2NjgsImV4cCI6MTcwOTI4NDI2OH0.Hma4dZnIYLsiJaFSs43GiPOGJQupI4MJBKeP8xSkoyM
  ```    
    
  - @ issues: 
    1. No issues found yet
  - @ response =>  status, success,  time, message
    1. examples :
  ```json: 
        {
           "status": 200,
    "success": true,
    "detail": {
        "id": 34,
        "firstName": "viaks",
        "lastName": "kumar jaiswal",
        "email": "vikas@gmail.com",
        "phoneNo": "1234567890",
        "status": "A",
        "address": null,
        "city": null,
        "stateId": null,
        "countryId": null,
        "zipCode": null,
        "dob": null,
        "gender": null,
        "stateName": null,
        "countryName": null,
        "cityId": null,
        "smProfile": null,
        "whatDescribeYouBestId": null,
        "whatDescribeYouBestText": null,
        "officeName": null,
        "officeAddress": null,
        "officeCity": null,
        "officeStateId": null,
        "officeCountryId": null,
        "officeZipcode": null,
        "investmentMarketExpId": null,
        "investmentMarketExpText": null,
        "reference": null
    },
    "time": "2024-03-01T14:30:31+05:30",
    "message": "Successfully fetched profile."
    }
  ```
   

  ### /client
   
  - @ arguments => 
    1. body => None
    2. header
      - Authorization
      - example: 
        
  ```
  Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjIyLCJpYXQiOjE3MDkyODA2NjgsImV4cCI6MTcwOTI4NDI2OH0.Hma4dZnIYLsiJaFSs43GiPOGJQupI4MJBKeP8xSkoyM
  ```    
    
  - @ issues: 
    1. No issues found yet
  - @ response =>  status, success,  time, message
    1. examples :
  ```json: 
        {
            "status": 200,
    "success": true,
    "detail": {
        "count": 1,
        "rows": [
            {
                "id": 36,
                "firstName": "vinod",
                "lastName": "Sharma",
                "email": "vinod@gmail.com",
                "contactNo": "1234567890",
                "phoneNo": "1234567890",
                "status": "A",
                "image": null,
                "userType": "CLIENT"
            }
        ]
    },
    "time": "2024-03-01T14:32:51+05:30",
    "message": "Successfully fetched client listing."
    }
  ```
   

  ### /client/:id
   
  - @ arguments => 
    1. body => None
    2. header
      - Authorization
      - example: 
        
  ```
  Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjIyLCJpYXQiOjE3MDkyODA2NjgsImV4cCI6MTcwOTI4NDI2OH0.Hma4dZnIYLsiJaFSs43GiPOGJQupI4MJBKeP8xSkoyM
  ```    
    
  - @ issues: 
    1. No issues found yet
  - @ response =>  status, success,  time, message
    1. examples :
  ```json: 
        {
             "status": 200,
    "success": true,
    "detail": {
        "id": 36,
        "firstName": "vinod",
        "lastName": "Sharma",
        "email": "vinod@gmail.com",
        "phoneNo": "1234567890",
        "status": "A",
        "address": null,
        "city": null,
        "stateId": null,
        "countryId": null,
        "zipCode": null,
        "dob": "2023-07-01",
        "gender": "male",
        "stateName": null,
        "countryName": null,
        "cityId": null,
        "smProfile": null,
        "whatDescribeYouBestId": null,
        "whatDescribeYouBestText": null,
        "investmentInterestId": null,
        "investmentInterestText": null,
        "lastInvestment": null
    },
    "time": "2024-03-01T14:34:25+05:30",
    "message": "Successfully fetched profile."
    }
  ```

## user-put-request-api /user

  ### /info
  - @ arguments => 
    1. body
      - dematAccountNo, dpId, dpName
      - examples :
  ```json: 
        {
          "dematAccountNo":"2234588812345678",
      "dpId":"22845978",
      "dpName":"axyz abc"

        }

  ```
    2. header
      - Authorization
      - example: 
        
  ```
  Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjIyLCJpYXQiOjE3MDkyODk2NTQsImV4cCI6MTcwOTI5MzI1NH0.AjVt4ZMRqArOKtl9AXUZQiIQ_2xNL0Mb2FXsBAUw56s
  ```
      
    
  - @ issues: 
    1. same user can post multiple info but validation error occur when same user is trying to put (update the bank info)
  - @ response =>  status, success,  time, message
    1. examples :
  ```json: 
        {
            "status": 200,
    "success": true,
    "time": "2024-03-01T17:16:35+05:30",
    "message": "Successfully saved bank information."
        } 
  ```


  
  ### /profile 
  - @ arguments => 
    1. body
      - object must contain at least one of [firstName, lastName, email, phoneNo, username, status] for edit.
      - examples :
  ```json: 
        {
        "userId":22,
        "firstName":"katya",
        "lastName":"yadav"
        }

  ```
    2. header
      - Authorization
      - example: 
        
  ```
  Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjIyLCJpYXQiOjE3MDkyOTI5NTIsImV4cCI6MTcwOTI5NjU1Mn0.aa0ZNjOONoVXjC_OpMEPpWIZcZNLb-3V5HjcfSy5INY
  ```
      
    
  - @ issues: 
    1. No bug found yet
  - @ response =>  status, success,  time, message
    1. examples :
  ```json: 
        {
           "status": 200,
    "success": true,
    "time": "2024-03-01T17:24:46+05:30",
    "message": "User updated successfully."
        } 
  ```


  
  ### /company/:id 
  - @ arguments => 
    1. body
      - "object must contain at least one of  [smProfile,businessType,fundsRequirement,yearInBusiness, cmpName, cmpAddress, cmpDirectorName, cmpEmail, cmpRegistrationDate, cmpProfile, cmpCity, cmpStateId, cmpCountryId, cmpZipCode, cmpStatus] for edit."
      - examples :
  ```json: 
        {
         "cmpCountryId": "101"
        }

  ```
    2. header
      - Authorization
      - example: 
        
  ```
  Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjIyLCJpYXQiOjE3MDkyOTI5NTIsImV4cCI6MTcwOTI5NjU1Mn0.aa0ZNjOONoVXjC_OpMEPpWIZcZNLb-3V5HjcfSy5INY
  ```
      
    
  - @ issues: 
    1. No bug found yet
  - @ response =>  status, success,  time, message
    1. examples :
  ```json: 
        {
          "status": 200,
    "success": true,
    "time": "2024-03-01T17:39:39+05:30",
    "message": "Company detail updated successfully."
        } 
  ```


  
  ### /company-product
  - @ arguments => 
    1. body
      - id is require
      - examples :
  ```json: 
        {
          "id":"5",
    "cmpId":"3",
    
    "productName":"Colgate",
    "shares":"100",
    "cost":"20"
        }

  ```
    2. header
      - Authorization
      - example: 
        
  ```
  Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjIyLCJpYXQiOjE3MDkyOTI5NTIsImV4cCI6MTcwOTI5NjU1Mn0.aa0ZNjOONoVXjC_OpMEPpWIZcZNLb-3V5HjcfSy5INY
  ```
      
    
  - @ issues: 
    1. No bug found yet
  - @ response =>  status, success,  time, message
    1. examples :
  ```json: 
        {
          "status": 200,
    "success": true,
    "time": "2024-03-01T17:52:36+05:30",
    "message": "Company product updated successfully."
        } 
  ```


  
  ### /partner/:id
  - @ arguments => 
    1. body
      - object must contain at least one of [lastInvestment, investmentInterestId, investmentInterestText,firstName, lastName, email, phoneNo, gender, status, dob, address, city, stateId, countryId, zipCode, officeName, officeAddress, officeCity, officeStateId, officeCountryId, officeZipcode, smProfile, whatDescribeYouBestId, whatDescribeYouBestText, investmentMarketExpId, investmentMarketExpText, reference] for edit.
      - examples :
  ```json: 
        {
          "firstName": "viaks",
                "lastName": "kumar jaiswal",
                "email": "vikas@gmail.com",
                "contactNo": "1234567890",
                "phoneNo": "1234567890"
        }

  ```
    2. header
      - Authorization
      - example: 
        
  ```
  Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjIyLCJpYXQiOjE3MDkyOTI5NTIsImV4cCI6MTcwOTI5NjU1Mn0.aa0ZNjOONoVXjC_OpMEPpWIZcZNLb-3V5HjcfSy5INY
  ```
      
    
  - @ issues: 
    1. No bug found yet
  - @ response =>  status, success,  time, message
    1. examples :
  ```json: 
        {
          "status": 200,
    "success": true,
    "time": "2024-03-01T17:57:18+05:30",
    "message": "User Detail updated successfully."
        } 
  ```


  
  ### /client/:id
  - @ arguments => 
    1. body
      - object must contain at least one of [lastInvestment, investmentInterestId, investmentInterestText,firstName, lastName, email, phoneNo, gender, status, dob, address, city, stateId, countryId, zipCode, officeName, officeAddress, officeCity, officeStateId, officeCountryId, officeZipcode, smProfile, whatDescribeYouBestId, whatDescribeYouBestText, investmentMarketExpId, investmentMarketExpText, reference] for edit.
      - examples :
  ```json: 
        {
           "firstName": "vinod",
        "lastName": "Sharma",
        "email": "vinod@gmail.com",
        "phoneNo": "1234567890",
        "status": "A",
        "address": null,
        "city": null,
        "stateId": null,
        "countryId": null,
        "zipCode": null,
        "dob": "2023-07-01",
        "gender": "male"
        
        }

  ```
    2. header
      - Authorization
      - example: 
        
  ```
  Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjIyLCJpYXQiOjE3MDkyOTI5NTIsImV4cCI6MTcwOTI5NjU1Mn0.aa0ZNjOONoVXjC_OpMEPpWIZcZNLb-3V5HjcfSy5INY
  ```
      
    
  - @ issues: 
    1. No bug found yet
  - @ response =>  status, success,  time, message
    1. examples :
  ```json: 
        {
           "status": 200,
    "success": true,
    "time": "2024-03-01T17:59:41+05:30",
    "message": "User Detail updated successfully."
        } 
  ```


  
## global-get-request /global

  ### /investment-interest

  - @ arguments => 
    1. body => None
    2. header => None
 
  - @ issues: 
    1. No issues found yet
    
  - @ response =>  status, success,  time, message
    1. examples :
  ```json: 
        {
             "status": 200,
    "success": true,
    "detail": {
        "count": 0,
        "rows": []
    },
    "time": "2024-03-01T14:44:42+05:30",
    "message": "List of investment interest."
    }
  ```

 
  ### /investment-market-exp

  - @ arguments => 
    1. body => None
    2. header => None
 
  - @ issues: 
    1. No issues found yet

  - @ response =>  status, success,  time, message
    1. examples :
  ```json: 
        {
            
    "status": 200,
    "success": true,
    "detail": {
        "count": 0,
        "rows": []
    },
    "time": "2024-03-01T14:48:03+05:30",
    "message": "List of investment market expertise."

    }
  ```

 
  ### /profession

  - @ arguments => 
    1. body => None
    2. header => None
 
  - @ issues: 
    1. No issues found yet

  - @ response =>  status, success,  time, message
    1. examples :
  ```json: 
        {
              "status": 200,
    "success": true,
    "detail": {
        "count": 9,
        "rows": [
            {
                "id": 1,
                "name": " Business Owner"
            },
            {
                "id": 2,
                "name": "Professional"
            },
            {
                "id": 3,
                "name": "VC& PE professional"
            },
            {
                "id": 4,
                "name": "VC & PE Fund"
            },
            {
                "id": 5,
                "name": "Organisation Institution"
            },
            {
                "id": 6,
                "name": "Family Office ,Incubator"
            },
            {
                "id": 7,
                "name": "Student"
            },
            {
                "id": 8,
                "name": "Financial Advisor"
            },
            {
                "id": 9,
                "name": "Other"
            }
        ]
    },
    "time": "2024-03-01T14:49:16+05:30",
    "message": "List of professions."
    }
  ```

 
  ### /countries

  - @ arguments => 
    1. body => None
    2. header => None
 
  - @ issues: 
    1. No issues found yet

  - @ response =>  status, success,  time, message
    1. examples :
  ```json: 
        {
             "status": 200,
    "success": true,
    "detail": {
        "count": 1,
        "rows": [
            {
                "id": 101,
                "name": "India",
                "phonecode": "91"
            }
        ]
    },
    "time": "2024-03-01T14:50:53+05:30",
    "message": "List of contries."
    }
  ```

 
  ### /states/:id 

  - @ arguments => 
    1. body => None
    2. header => None
 
  - @ issues: 
    1. No issues found yet

  - @ response =>  status, success,  time, message
    1. examples :
  ```json: 
        {
             "status": 200,
    "success": true,
    "detail": {
        "count": 1,
        "rows": [
            {
                "id": 4022,
                "name": "Uttar Pradesh"
            }
        ]
    },
    "time": "2024-03-01T14:52:04+05:30",
    "message": "List of states."
    }
  ```

 
  ### /cities/:id 

  - @ arguments => 
    1. body => None
    2. header => None
 
  - @ issues: 
    1. No issues found yet

  - @ response =>  status, success,  time, message
    1. examples :
  ```json: 
        {
              "status": 200,
    "success": true,
    "detail": {
        "count": 1,
        "rows": [
            {
                "id": 133230,
                "name": "Noida"
            }
        ]
    },
    "time": "2024-03-01T14:53:07+05:30",
    "message": "List of cities."
    }
  ```

 
## Dashboard-get-request /dashboard


  ### /admin
   
  - @ arguments => 
    1. body => None
    2. header
      - Authorization
      - example: 
        
  ```
  Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjIyLCJpYXQiOjE3MDkyODU0MTEsImV4cCI6MTcwOTI4OTAxMX0.KWSmVW0M8irSHyyC3BBvmqCVGEkfKln0QPNTyIbBWR0
  ```    
    
  - @ issues: 
    1. No issues found yet
  - @ response =>  status, success,  time, message
    1. examples :
  ```json: 
        {
            "status": 200,
    "success": true,
    "detail": {
        "totalCompany": 2,
        "totalProduct": 1,
        "totalUser": 17,
        "totalClient": 1,
        "totalPartner": 1,
        "suspendedUser": 0,
        "company": {
            "active": 0,
            "inactive": 2
        },
        "partner": {
            "active": 1,
            "inactive": 0
        },
        "client": {
            "active": 1,
            "inactive": 0
        },
        "product": {
            "active": 0,
            "inactive": 1
        }
    },
    "time": "2024-03-01T15:00:59+05:30",
    "message": "Successfully feched stats."
    }
  ```

  ### /partner
   
  - @ arguments => 
    1. body => None
    2. header
      - Authorization
      - example: 
        
  ```
  Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjM0LCJpYXQiOjE3MDkyODU4NTIsImV4cCI6MTcwOTI4OTQ1Mn0.IQkr9KkSWzxHqoNlDq7JKpfAzTtR9y0tn5G2kPTqaM4
  ```    
    
  - @ issues: 
    1. No issues found yet
  - @ response =>  status, success,  time, message
    1. examples :
  ```json: 
        {
            "status": 200,
    "success": true,
    "detail": {
        "totalCompany": 0,
        "totalProduct": 0,
        "totalUser": 0,
        "totalClient": 0,
        "totalPartner": 0,
        "suspendedUser": 0
    },
    "time": "2024-03-01T15:08:37+05:30",
    "message": "Successfully feched stats."
    }
  ```

  ### /company/:stateId
   
  - @ arguments => 
    1. body => None
    2. header
      - Authorization
      - example: 
        
  ```
  Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjM0LCJpYXQiOjE3MDkyODU4NTIsImV4cCI6MTcwOTI4OTQ1Mn0.IQkr9KkSWzxHqoNlDq7JKpfAzTtR9y0tn5G2kPTqaM4
  ```    
    
  - @ issues: 
    1. It is expecting stateId as params, but :stateId is missing in router code.
  - @ response =>  status, success,  time, message
    1. examples :
  ```json: 
        {
             "status": 200,
    "success": true,
    "detail": {
        "count": 1,
        "rows": [
            {
                "id": 133230,
                "name": "Noida"
            }
        ]
    },
    "time": "2024-03-01T15:11:56+05:30",
    "message": "List of cities."
    }
  ```

  ### /client/:stateId
   
  - @ arguments => 
    1. body => None
    2. header
      - Authorization
      - example: 
        
  ```
  Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOjM0LCJpYXQiOjE3MDkyODU4NTIsImV4cCI6MTcwOTI4OTQ1Mn0.IQkr9KkSWzxHqoNlDq7JKpfAzTtR9y0tn5G2kPTqaM4
  ```    
    
  - @ issues: 
    1. Logic inside client is the same as login inside company.
    2. It is expecting stateId as params, but :stateId is missing in router code
  - @ response =>  status, success,  time, message
    1. examples :
  ```json: 
        {
           "status": 200,
    "success": true,
    "detail": {
        "count": 1,
        "rows": [
            {
                "id": 133230,
                "name": "Noida"
            }
        ]
    },
    "time": "2024-03-01T15:14:44+05:30",
    "message": "List of cities."
    }
  ```
