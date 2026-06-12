---
title: "DFD and ERD"
date: 2008-01-06
forum: Programming Talk
---

### Post by Jawahir on 2008-01-06
Hello!

I need some help with data flow diagrams and entity relationship diagrams! If anyone can help me, I would very much appreciate it!

1. In DFDs do I have to include error messages? For instance, if I have a DFD for registration, is it necessary to include the error messages the user would get if they do not fill in all the fields or if they choose an already existing username?

2. In ERDs do I include ALL the tables in the database, even if they do not interact? For instance, I have four tables: customer, staff, resource, orders. Only the orders table has foreign keys from the other tables (which are the customer and resource tables), so I understand how the orders table is related to them. Customer can browse resources but neither tables have fields from each other, so are they still related? I'll paste the tables and their fields:

[B][U]
Resources TABLE– [/U][/B]stores details related to each grocery item
Resource id – can uniquely identify a grocery item
Name
Category – 'fresh food', 'kitchen cupboard', 'frozen food', 'drinks', 'toiletry and baby', 'house'
Description – some information about the grocery item
Purchase price
[B]
Customers TABLE[/B] – stores details of individual customers
Customer id – can uniquely identify a customer
Username
First name
Last name
DOB
Address line 1
Address line 2
City
Country
Telephone number
Email
Password
Registration date

**Orders TABLE–** stores details of all the items a customer bought
Order id – can uniquely identify a customer order
Customer id – the customer who placed the order
Resource id – the grocery item that the customer placed an order for
Resource price – price of the grocery item
Quantity
Total purchase price
Order date
[B]
Staff TABLE [/B]– stores details of members of staff who will be using the system
Staff id – can uniquely identify a member of staff
Username
First name
Last name
Role – ‘sales assistant’, ‘supervisor’, ‘store manager’
DOB
Address line 1
Address line 2
City
Country
Telephone number
Email
Password
Registration date


If anyone knows anything please let me know! :)

---

