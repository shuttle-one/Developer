# Developer
## Developer API for test how Shuttle One work
Shuttle One API (2020-03-03) (Test net)

## Releases
2020-03-03 V1 Release

## Base URL
The base URL is: http://shuttleone.network:9007/api

## API documentation
   Refer to the following for description of each endpoint
   
### GET /api/servertime
#### Description:
    Get server timestamp.
#### Query:

    write api (for test encrypt)
#### Response: unix time stamp
    1529999999

### GET api/szo/create
	example api/szo/create
#### Description:
	Create new wallet account
#### Query:
	write api NO ENCRYPT
#### Response: 
      return wallet address if success. if error return 0
---------------------------------------------
### GET api/szo/kyc_put/(walletaddr)/(Name)/(Surname)/(country)/(id card or passport)
	example api/szo/kyc_put/0xe2453621ae8ff76c3f952206fac6399b5efab6eb/John/Gate/USA/AB1243234
#### Description:
	KYC this wallet address. if wallet address not create by this system it can’t KYC (in production version can do it)
#### Query:
	write api
#### Response: return json
      Success
         {
         "code" : 0,
         "data" : (txhash)
         }
      Error
         {
         "code" : 1,
         "data" : Error string
         }
--------------------------------------
### GET api/szo/kyc_get/(walletaddr)
	example api/szo/kyc_get/0xe2453621ae8ff76c3f952206fac6399b5efab6eb/John/Gate/USA/AB1243234
#### Description:
	Read KYC Data From blockchain
#### Query:
	read api
#### Response: return json
      Success
      {
         "code" : 0,
         "data" : 
         {
            "kyc" : 
            {
               "country" : "USA",
               "idcard" : "US334212312234",
               "name" : "Steve",
               "surname" : "Job"
            }
         }
      }
      Error
         {
         "code" : 1,
         "data" : Error string
         }

--------------------------------------
### GET api/szo/topup/(Wallet Address)/(Amount)/(currency)
	example api/szo/wallet/topup/0x8C44d3475e4784fc1D30746473F5cBd8Db227179/12.32/PHP
#### Description:
	Topup money then Agent will give DAI to use 	Amount = Amount in that currency
	Currency Support SGD,USD,THB,MYR,IDR,PHP 	Maximum per time are 500 USD Minimum 10 USD
#### Query:
	write api
#### Response: return Json data
      Success
         {
         "code" : 0,
         "data" : (txhash)
         }
      Error
         {
         "code" : 1,
         "data" : Error string
         }
         
#### GET /api/szo/wallet/balance/(Wallet Address)/(Currency
	example api/szo/wallet/balance/0x8C44d3475e4784fc1D30746473F5cBd8Db227179/PHP
### Description:
	Get balance
### Query:
	read api
### Response: return balance in that currency with 4 digit
      123.3342
-------------------------------------------
#### GET /api/szo/send/(From Wallet)/(To Wallet)/(Amount)/(Currency)
	example api/szo/send/0x…../0x…../342.334/PHP
### Description:
	Send Money to other fee 3% minimum send 5 USD
### Query:
	write api
### Response: return json
      Success
         {
         "code" : 0,
         "data" : (txhash)
         “receive” : xxxx 
         “fee” :    xxxx
         }
      Error
         {
         "code" : 1,
         "data" : Error string
         }
------------------------------------------
#### GET /api/szo/withdraw/(wallet address)/(amount)/(currency)
	example api/szo/withdraw/0x…./342.334/USD
### Description:
	Withdraw to fiat money and transfer balance back to agent
### Query:

### Response: return json
      Success
         {
         "code" : 0,
         "data" : (txhash)
         “recieve” : xxxx 
         “fee” :    xxxx
         }
      Error
         {
         "code" : 1,
         "data" : Error string
         }


