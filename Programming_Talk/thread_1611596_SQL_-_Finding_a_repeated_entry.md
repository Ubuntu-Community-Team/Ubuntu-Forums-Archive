---
title: "SQL - Finding a repeated entry"
date: 2010-11-02
forum: Programming Talk
---

### Post by lazypeterson on 2010-11-02
Alright, I'm trying to find outHere's a breakdown of the tables, if it helps:


Products
ProductID
ProductName
SupplierID
CategoryID
UnitPrice
QuantityPerUnit

Order Details
OrderID
ProductID
UnitPrice
Quantity

Orders
OrderID
CustomerID
EmployeeID
OrderDate
etc.


Any help would be greatly appreciated.  who ordered a product more than once.

So far I've got: 

```
Select ContactName, Orders.OrderID, ProductID From Customers
inner join Orders on Customers.CustomerID = Orders.CustomerID
join [Order Details] on [Order Details].OrderID = Orders.OrderID;
```

---

### Post by Some Penguin on 2010-11-02
Blargh.  That looks grossly inefficient.  And I wouldn't use spaces in table names, as you get into silly quoting needs. 

```

SELECT T1.ProductID AS ProductID, T2.CustomerID AS CustomerID, count(*)
FROM Order_Details T1, Orders T2
WHERE T1.OrderID = T2.OrderID
GROUP BY ProductID, CustomerID
HAVING count(*) > 1;

```

is one straightforward approach that'd work in PostgreSQL.  There's your mapping.  SELECT INTO a temporary table and use the results however you like if you need more metadata.

---

### Post by lazypeterson on 2010-11-02
Thank you so much, that was very helpful.

---

