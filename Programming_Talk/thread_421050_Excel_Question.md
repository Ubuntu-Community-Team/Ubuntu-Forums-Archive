---
title: "Excel Question"
date: 2007-04-24
forum: Programming Talk
---

### Post by renzokuken on 2007-04-24
I know this is probably out of place but everyone here is always more helpful and knowledgeable than anywhere on the net.

Anyways. i'm trying to do a simple VAT calculating spreadsheet for my parents business that they can use (they are completely computer illiterate btw).

I have the basic layout and "totalling" functions all set out but i'm having a problem.

May be worth looking at my setup below first.

All the items need to be sperated as either "item" or "service" and each one of these needs to be seperated again into "5%" or "17.5%". Depending which of these is selected determines which column each one appears in. (you'll see in the attachment) i dont want all possible values appearing in all columns

i tried using IF and AND statements to say that if "item" and "5%" were written in the 4th and 5th columns respectively then the apprpriate calculation would be performed on the "Invoice Total" and the answer displayed in the "Cost excluding VAT @ 5%" column only.

this obviously didnt work, hence i'm open to suggestions from anyone who is good at this kind of thing, even a Visual Basic one if one exists

hope this all makes sense and that someone can help

---

### Post by mozetti on 2007-04-24
Is it that the VAT is 5% for services, and 17.5% on items (or vice-versa) -- meaning all services get this % of VAT and all items get this % of VAT? Or, can you have one service that gets 5% VAT and another service that gets 17.5% VAT? And likewise, one item gets 5% VAT and another item can get 17.5% VAT?

---

### Post by renzokuken on 2007-04-24
hi mozetti. the second one is correct. there are four combinations and each calculation needs to go into the appropriate column, as follows

**product/vat combination..............|............... column**
Item at 5%................................ ->...............Cost excluding VAT @ 5%
Item at 17.5%............................ ->...............Cost excluding VAT @ 17.5%
Service at 5%............................. ->...............Service excluding VAT @ 5%
Service at 17.5%......................... -> ...............Service excluding VAT @ 17.5%

---

### Post by mozetti on 2007-04-24
Ok, then I think your answer is in putting nested "IF" statements in each of the total columns. So, in your column labeled "Services excluding VAT @ 5%", you would put an "IF" statement saying:

=IF([item or service column]="service", IF([5%or 17.5% column]=5%, [equation for calculating invoice total less VAT], ""))

You're basically saying:

1) If my [item or service] column says "service", then
2) If my [5% or 17.5% column] says 5%, then
3) Do the calculation, else
4)don't do anything. 

Each of your columns (item less 5%, item less 17.5%, service less 5%, and service less 17.5%) would have the "IF" statements appropriate to what it's calculating. This should work.

---

### Post by renzokuken on 2007-04-24
awesome, thanks mozetti,that is exactly what i wanted. i'll give it a go and let you know.

---

### Post by renzokuken on 2007-04-24
tried it and works perfectly mozetti

only change i made was to add a couple more "" so that it left the field blank instead of writing FALSE, i.e.

=IF([item or service column]="service", IF([5%or 17.5% column]=5%, [equation for calculating invoice total less VAT], ""),[color=red]""[/color])

---

### Post by mozetti on 2007-04-24
Glad it worked. I thought I might have been missing the final "ELSE" statement, and I guess I was.

---

