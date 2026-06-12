---
title: "I got a currency rate problem in my firm"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by Hunden on 2008-11-19
Hi.
I am the owner of a small Danish firm. We buy and sell goods from other countries. Every day I calculate a lot of currency rates, but now I want an easier path. The manually calculating is very expensive in time!
I would be very grateful if someone can help me, cause I'm not good in VBA.

It could be nice if i could get this in a clean code (if it is easy enorgh for you), cause then i can add and learn more as the time goes.


This is a simple example:
Workbook1, Worksheet 1:: I earned this:
Earning 1: 10 EUR
Earning 2: 5 EUR
Earning 3: 3 EUR
Earning 4: 90 USD
Earning 5: 10 DK
Earning 6: 1 GP

Workbook 2: And the currency rates (DK= 100.00)
USD 605.00
EUR 730.00
GP 80.00

I want a top 3 of my earnings but calculated in DK. In this case the result would be:
1) 10 * 7,30 = 73
2) 5 * 7,30 = 36,5
3) 3 * 7,30 = 21,9
4) 90 * 6,05 = 544,5
5) 10 * 1 = 10
6) 1 * 0,8 = 0,8

Workbook 1, Worksheet2: And top 3 is:
544,5
73
35,5


Hope to hear from someone cause i dont even know where to start.

---

### Post by Bölvaður on 2008-11-19
Give me a new example to understand the problem better (and see what is varying and what isn't)

[added]
is this what you are talking about?

---

### Post by Hunden on 2008-11-19
> **Bölvaður said:**
> Give me a new example to understand the problem better (and see what is varying and what isn't)

Yeah sure.
There are two Excel files with data that are necessary in order to solve the job. The file "SalesAmount.xlsx" contains a list of sales amount and the currency they are denominated as. The file "ExchangeRates.xlsx" contains a list of the currencies and their respective rates/prizes.

Eksample:


ExchangeRates
DKK = 100
  A    B    C    D
1 USD 622
2 EUR 768
3 JPY 64
4

 
Salesamount
  A    B    C    D
1 USD  54.5
2 USD  33.6
3 EUR  14.7
4 USD  77.7
5 EUR  11,9
6 JPY  0,01

Now the job is to make a top 3 list of the largest sales measured in Danish kroner (DKK), which of course requires that all amounts are converted from their original currency to DKK.


In this case the top 3 is: (1): 77,7*6,22. And (2): 54,5*6,22. And (3): 33,6*6,22... Because in DKK these values is the top 3 hightest.

At the moment i got this in formulars and in some recorded makros i dont understand... if this could be made in simple vba it would be very greatfull. Then i can add, and learn more, as the time goes.

---

### Post by Bölvaður on 2008-11-19
hm, I solved the problem in the last post I did, you only need to tailor it to suit your needs. You do not need to use more than one file or anything else than what you can do in a single spreadsheet with perhaps 2 tabs (I guess it would be considered 2 spreadsheets then).

There is high likely hood that this isn't what you are looking for but this is the best I can do (you cant build anything better than what is on the blue prints, and people never say what they need correctly).


Enjoy the file I attached (look above)

---

