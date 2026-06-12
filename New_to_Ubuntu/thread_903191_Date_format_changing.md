---
title: "Date format changing"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by joshiss on 2008-08-28
I am using ubuntu as a parallel operating system till I am comfortable completely with it after using windows by default for a long time. 
In windows I am using a software for my data logger connected to one of my equipments. The sftware uses a date format as dd/mm/yyyy. When I tried to use wine and run the software from UBUNTU it shows message that the date and time format is not matching to default equirement of dd/mm/yyyy. I am unable to change the format to this format in UBUNTU. 
Can abyone help in solving this problem.

---

### Post by ilrudie on 2008-08-28
```
date +%d/%m/%Y
``` gives you that format.  Not really sure how its getting the date though.

---

