---
title: "how would you join two tables"
date: 2014-07-11
forum: Programming Talk
---

### Post by mastablasta on 2014-07-11
Ok so not a programing question, but perhaps someone here could help me out with this or at leats point me to the tool i could use.

ok so basically there are two tables. one is on sales side where we have info on the order number (also customer but i haven't included as i can later just filter this), order date, ordered quantity, available quantity and code of article. 

the other table comes from supply side where we have their order to supplier, ordered quantity and date of arrival to our warehouse.

now what i need is that the correct date of arrival of the article code to appear next to specific order. the oldest customer order should get the parts first, second oldest cusotmer order is next in line etc. the ERP system we have is supposed to do that but it was rubishly designed and made :(

ofcorusae this is just an example we have hundreds of these taht need to be matched.

[TABLE="width: 453"]
[TR]
[TD]Ref order no[/TD]
[TD]art. code[/TD]
[TD]Ordered qty[/TD]
[TD]available qty[/TD]
[TD]date of order[/TD]
[/TR]
[TR]
[TD]1809202491[/TD]
[TD]700497[/TD]
[TD]60[/TD]
[TD]0[/TD]
[TD]3.7.2014[/TD]
[/TR]
[TR]
[TD]1809200528[/TD]
[TD]700497[/TD]
[TD]13[/TD]
[TD]0[/TD]
[TD]20.6.2014[/TD]
[/TR]
[TR]
[TD]1809198640[/TD]
[TD]700497[/TD]
[TD]7[/TD]
[TD]0[/TD]
[TD]9.6.2014[/TD]
[/TR]
[/TABLE]


[TABLE="width: 367"]
[TR]
[TD]Supply order no[/TD]
[TD] Art. Code[/TD]
[TD]Qty ordered[/TD]
[TD]Date of arrival[/TD]
[/TR]
[TR]
[TD="align: right"]4501243378[/TD]
[TD] 700497[/TD]
[TD="align: right"]50[/TD]
[TD="align: right"]4.8.2014[/TD]
[/TR]
[TR]
[TD="align: right"]4501263437[/TD]
[TD] 700497[/TD]
[TD="align: right"]20[/TD]
[TD="align: right"]6.10.2014[/TD]
[/TR]
[/TABLE]

---

### Post by QIII on 2014-07-11
Not good enough to get a one to one relationship for a join.

"Ref Order No" is the unique key on the first table.  It has no relationship to "Supply Order No".

Both tables need "Ref Order No" to join on a unique key.

Unless you have a third table that has "Ref Order No" and "Supply Order No" as an intermediate table.

---

### Post by mastablasta on 2014-07-11
i do not thing there is such an intermediate table available as that would mean made to order system, while we have to keep stock on hand. [i Will try to find such a table in analysis tool from the ERP]

and the problem is that stock is actually assigned to purchase orders only when it arrives (is accepted into the warehouse after quality control check).

i mean as a human you can calculate and then connect the correct date with correct customer order. but how to tell the computer to perfom this?

in this case it is Quite easy for human to see that the first customer order will get 50 pcs in August and the rest in October. while the seocnd order iwll only get them in october and 10 pcs then while for 3 more there is no date. the third order is missign a supply date completely (i.e. no purchase order for it was made yet).

---

### Post by SeijiSensei on 2014-07-11
As a start you could join on the "article code" and sort the results by date of order and date of arrival.  Still I'd probably end up writing a little application that pulls the data from the two tables and determines the relationship between quantities sold and ordered.  I don't think I could write a single SELECT query that answers the question you're asking.

---

### Post by mastablasta on 2014-07-12
yes, obviously it is not so simple. otherwise the IT guys would have done it in the ERP. but it is doable it seems.
i think our whole system whoever set it up is flawed. there was so many dditionas, patches, ugly solutions to it that no no one even knwos why they did certain things. it's a mess. you get old orders standing in line for 3 months for some chinese manufactuer to deliver - skipped. no one knows the exact reaosn why they get skipped someitmes and why sometimes they do not. it's all a preety big mess. they plan to redo some major part that hopefulyl shoul dsolve our porblem but. this could take years... :(

---

### Post by oldfred on 2014-07-12
The missing table is on hand inventory of item 700497, even if currently 0. By date purchases add to inventory and sales subtract from inventory.

Often MBR/ERP systems do not give data in the way you want. And if a newer better system you can download the data and create your own reports.

Before ISD created a data warehouse, I was downloading masses of data for our smaller division. ISD did not like letting me have access to the data but my boss and the Division President had started to rely on data that ISD could not easy provide, so I kept my access to all the data.

---

### Post by mastablasta on 2014-07-13
> **oldfred said:**
> The missing table is on hand inventory of item 700497, even if currently 0. By date purchases add to inventory and sales subtract from inventory.


That's how humans do it now. check the stock, check the dates and then arrange them. what i do n't knwo is how to make computer do this.

> 
Often MBR/ERP systems do not give data in the way you want. And if a newer better system you can download the data and create your own reports.

that's it my plan, however the issue is that data is still separated in different tables.
the system is very modern apparently capable of almost anything. but no one knows how to handle it. almost no one. It doesn't help much if IT is made up of people with no or very little IT knowledge. most of them did not do a university program for a software engineer. at best we have high school IT students. then there are people that studied logistics or just worked in warehosue that are now "experts" in the ERP. what we would need is database admin but i do not think there is one.

whic is why i am aksing here. To hopefully get some solution or idea on how to solve this. then maybe we could soemohow try to get this solution to those with  little knwoledge in programing the ERP so they can try and tame it. 

or at least to do the merge outside of ERP. we actually do not care how it's done only to get it done by computer. as it looks now we would need to hire two people adiditonally to sift through data and just create such reports.

---

### Post by SeijiSensei on 2014-07-13
Well, lets start with a basic question.  What database is running on the backend?  Can you connect directly to the database over the network, or is everything mediated through the ERP software?

If its Microsoft SQL Server, is ODBC access enabled?  Oracle and the free SQL servers like PostgreSQL and MySQL can be addressed directly from Linux.

---

### Post by mastablasta on 2014-07-14
it' SAP and the only part i get is tables exported to .xls (yeah that's right this is old MS Excel format and probably not even that as it is not really recognised by Excel). 

i can get these 3 tables out and process them in another way if necessary. i just need some pointer how to do the processing where the time would be factored in stock levels. it seems like this is a bit too complex for excel or calc.

anyway i would say the databses are same as in Oracle since SAP took a lot from them. it can also be exported in csv format, but i am not sure if that is any better.

---

### Post by SeijiSensei on 2014-07-14
Ever tried Microsoft Access?  That would be my choice given that the input data reside in Excel.  It was the first real DBMS I ever used, and I found it pretty easy to learn how to join tables and generate reports.  

Plus, if you ever figure out how to access the database tables directly, you can replace the actual tables in Excel with ODBC links to their equivalents in SAP.  Then once you have the report designed to your liking, you can run it in real time against the SQL database rather than exporting the data each time.

---

### Post by oldfred on 2014-07-14
I also used Access, but had been using dBase for years. I wanted to learn SQL and Access showed the SQL in the queries.

I did automate some CVS downloads, so every morning I had new data and then imported that directly into Access. Started off doing everything manually and slowly learned how to automate each part. I still have an Access 97 book on shelf although most of what I did was with Access 2000. Do not know much about the newer versions of Access. Microsoft did not want you connecting too many users as that was competing with SQL server.

Later got direct SQL download and could use Access to connect directly to IBM DB2 databases. And then converted some data to a local Microsoft SQL server. I always downloaded data locally as I only had 30,000 items, 150,000 BOM records and 20,000 routers. Also downloaded Inventory, sales and created in essence my own data warehouse but only for our division before corporate did create one for all of corporate. Then converted to using that.

---

### Post by mastablasta on 2014-07-15
So it could work in Access? i will read up on that then and try to find a solution. i have this feeling that the edpartment "IT team" should be doing this but no one knows what they are actually doing. since  none of them has any software background (one has electronics engineer degree, i think).

at the same time i found SAP forums and will ask there as well. there is maybe a solution in the SAP.

---

