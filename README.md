# Winter--2022-shopify-Intern-Challenge



Question 2: For this question you’ll need to use SQL. Follow this link to access the data set required for the challenge. Please use queries to answer the following questions. Paste your queries along with your final numerical answers below.

<span style="color: red;">a. How many orders were shipped by Speedy Express in total?</span>

 <span style="color: blue;">Query: SELECT ShipperName, COUNT (*)
        FROM (Orders
        INNER JOIN Shippers ON Shippers.ShipperID=Orders.ShipperID)
        WHERE ShipperName='Speedy Express’;</span>

<span style="color: Green;">Result:
Shipper Name 	    COUNT (*)
Speedy Express	    54</span> 

<span style="color: red;">b. What is the last name of the employee with the most orders?</span>
<span style="color: blue;">Query: SELECT LastName, MAX(OrderID)
       FROM (SELECT LastName,COUNT(*) AS ORDERID
       FROM (Orders
       INNER JOIN Employees ON Orders.EmployeeID=Employees.EmployeeID)
       GROUP By Employees.EmployeeID);</span> 
<span style="color: Green;">Result:
LastName	MAX(OrderID)
Peacock	  40</span>


<span style="color: red;">c.What product was ordered the most by customers in Germany?</span>
<span style="color: blue;">Query: SELECT ProductID, ProductName,MAX(GermanyOrders)
     FROM (SELECT Products.ProductID,ProductName,SUM(Quantity)AS  GermanyOrders
     FROM (((Products
     INNER JOIN OrderDetails ON Products.ProductID=OrderDetails.ProductID)
     INNERJOIN Orders ON OrderDetails.OrderID=Orders.OrderID)
     INNER JOIN Customers ON Orders.CustomerID=Customers.CustomerID)
     WHERE Country='Germany'
     GROUP BY Products.ProductID);</span> 

<span style="color: Green;">Result:
ProductID	ProductName	MAX(GermanyOrders)
40	Boston Crab Meat	160</span> 




