---
title: "OJT's RUIN OUR SERVER"
date: 2009-06-15
forum: Philippine Team
---

### Post by kiminaiseah on 2009-06-15
any suggestion to optimized mysql, lakas kumain kasi ng resources nung mysql nila

---

### Post by loell on 2009-06-15
probably look at the PHP code that's accessing MySQL server.

---

### Post by jsgotangco on 2009-06-15
If its an OJT deploying code, then check the code - it must be loading every object in the DB.

But if an OJT is doing the code, why are you letting them deploy to the production server without testing? :D

---

### Post by Samhain13 on 2009-06-16
RE: second image.

Grabe naman yan, one hour ganyan kabigat yung load ninyo dahil lang sa PHP/MySQL? Maiintindihan ko pa kung nagre-render kayo ng 3D sa box niyo.

Oo nga, agree ako kila Loell at Jerome, check the code, yung PHP. Baka naman gumawa na ng IRC trivia bot yang mga yan (joke!).

---

### Post by kiminaiseah on 2009-06-16
thanks for reply..

sabi nga ng senior programmer/developer namin mali yung approach nung accessing ng php code sa mysql, 1 php script multiple query on 1 table read/write.


anyway its our development server.. pero sa sobrang liit ng timeline na bnbgay ng partners misan release candidate or beta pero nasa production line na... haaayyy.......

this new screen shot 1 of our production server

---

