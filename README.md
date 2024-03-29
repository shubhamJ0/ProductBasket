# ProductBasket
It is a simple basket developed on Node JS platform with loopback 3.0 Version framework. (Ex : Clone of Flipkart Add cart/product basket and pay logic). <br />
# Required Tool and Steps to Run The Project
1 : oracle DB  <br />
2 : Node Envoiroment  <br />
3 : Clone the folder into your System  <br />
4 : Unzip Folder ProductCart_Basket <br />
5 : Go inside folder and run into CMD.  <br />
6 : npm install  <br />
7 : Goto project Structure inside server/datasource.json change the connection ip with your system IP.Also configure user and password to connect from schema <br />
8 : For creating Tabel with script into oracle change Tabel Name into server/bin/create_tabel.js and Run.  <br />
9 : nodemon .  <br />
Product will start listening on the port number 3000.  <br /> 
Web server listening at: http://localhost:3000  <br />
Browse your REST API at http://localhost:3000/explorer  <br />
# PFB API's with Request and Response  <br />
1 : Basic API for Admin to register A,B,C,D Products  <br />

Api : https://localhost:3000/api/getList/product
Method : POST
Request :

{
  "prodCategory": "B",
  "prodName": "Apple",
  "prodPrice": "20",
  "prodDiscount": "1"
}
Response :
{
    "message": "Product added Successfully."
}

2 : Add Items :

API : https://localhost:3000/api/user/addItems

Method : POST

Request :

{
  "prodId": 262,
  "prodName": "Mango",
  "prodPrice": 30,
  "prodDiscount" : 15
}

Response :
{
   message : 'Product added successfully'.
}

3: Updating Quantity of Items :

Method  : POST
API : https://localhost:3000/api/user/updating_Items

Request :

{
  "prodId": 262,
  "prodName": "Potato",
  "prodPrice": 20,
  "prodDiscount" : 5,
  "totalNumber" : 2
}

Response :

{
    "message": "Quantity added successfully."
}

4 : Returning list of data basket/cart(with individual price and discount data),the total price and total discounts applied.
Method : GET <br />
- NOTE : Pass ProdId as a unique guest user and basketCheckout_Price is a total amount and discount calculation object.  <br />
API : https://localhost:3000/api/user/calcItems?prodId=262

Response :

[
    {
        "prodA_Price": 30,
        "prodA_Discount": 15,
        "total_Price": 180,
        "discount_Applied": 30
    },
    {
        "prodB_Price": 20,
        "prodB_Discount": 5,
        "total_Price": 35,
        "discount_Applied": 5
    },
    {
        "prodC_Price": 50,
        "prodC_Discount": 0,
        "total_Price": 50,
        "discount_Applied": 0
    },
    {
        "prodD_Price": 15,
        "prodD_Discount": 0,
        "total_Price": 45,
        "discount_Applied": 0
    },
    {
        "basketCheckout_Price": {
            "payable": {
                "Total_Price": 290,
                "Total_Discount": 55
            }
        }
    }
]
# Discount Logic : <br />
if cart_Total> 150 then add discount 20 rs. Else Discount based on product as given below. <br />
+ If 3 of Item A is purchased, the price of all three is Rs 75(i.e multiples of 3 discount) <br />
+ If 2 of Item B is purchased, the price of both is Rs 35(i.e multiples of 2 discount) <br />
+ If the total basket price(after previous discounts) is over Rs 150, the basket receives an <br />
additional discount of Rs 20.<br />
+ Above condition could achieve after calculating total price from cart if totalPrice > 150 then discount will be applied -20. <br/>
+ Please go threw Test Cases attached with project for more clarity.
