---
title: "Database Table Design"
date: 2009-01-29
forum: Programming Talk
---

### Post by s.fox on 2009-01-29
Hi,

I am currently working on a database design for a project.   Basically the team and myself have a split of opinion on which table design is better. 

We have the scenario where our products cost different amounts depending on the company that places an order.  We have around 50 companies that will  be ordering from ourselves and 200 different products.

To allow better understanding of the problem I have built a spreadsheet with sample data placed into both of the different designs.   I have attached the spreadsheet in this post.   

Personally I think design 2 is better than design 1 because design 2 would need a new column added every time a product is added.  I also believe that it would be bad practice to have the product ID as a column heading in the table.  The reason for the split of opinion in the team is that design 2 would need many many more rows than design 1.

I suppose what I am asking is:-  Which design would be best to go with and why?

Many thanks for taking time out to have a look.

Ash R

P.S.  If any clarification is needed please don't hesitate to ask.

---

### Post by ufis on 2009-01-29
Can you perhaps save the attachment as excel (spit)

I have a windows box only at work and my ms office version cannot read open office formats.

---

### Post by s.fox on 2009-01-29
Hi,

I would, except that the forum won't let me upload an .xls file.  :(

Instead I have put it into a .doc file. 

Hope you can open it.  

Thanks for taking a look

---

### Post by drubin on 2009-01-29
Firstly did some one notice the size differnce between the 2 formats :)

I would go with design 2 not even a question asked! This is called data base normalization.

I mean this way/method has the pro's of being easier to add/remove products with out affecting your underlying data base structure.

From my point of few you have got the basics down with your design 2 and that being said I do not even see a need for you entertaining design 1.

---

### Post by ufis on 2009-01-29
Design1 is a big NO. When you have to make database changes whenever you get a new product/client, then your design is wrong.

You should only ever have to do new data entry(s) should you get a new product/client.

As per the example you provided, **Design2 would be best**, assuming proper use of primary and foreign keys to avoid duplicate and/or dead data.

Depending on your business model a few other options are available.

One option: If your discount/price variation per customer is fixed across all products rather store the product price with the product and a discount % with the client. Then you can work out the amount instead of storing it on the DB - also makes it easier when you change prices. But dont change your business rules to fir in with your DB design. The DB design should fit in with your business.

---

### Post by s.fox on 2009-01-29
Drubin - Yes,  I didn't think design 1 was well normalised.   

ufis- That's exactly what I thought.  Its a bad idea to change structure every time new product is added.  Unfortunately its not a % discount that we are offering to customers.

Thank you for all your thoughts on the designs.  I believe the team will now be going with design 2.

---

