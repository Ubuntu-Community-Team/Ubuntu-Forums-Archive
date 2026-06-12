---
title: "Automate Math worksheet in LibreOffice Calc"
date: 2013-02-28
forum: Programming Talk
---

### Post by slooksterpsv on 2013-02-28
Does anyone know how I could do the following in LibreOffice Calc:

Cell A2 contains the value: 2+3
Cell A3 should contain the student/users answer, in this case: 5
Cell A4 gives a red X for wrong or a green check for correct

Without having it process =2+3 how can I have LibreOffice Calc convert a string 2+3 to process it like =2+3 ?

If I have to do it manually that's ok, I thought I could automate it.

---

### Post by steeldriver on 2013-03-01
You could do it the other way around, I think i.e.

- create a cell to evaluate the answer =2+3

- use the FORMULA() function to return the text formula (literally =2+3) into A2

You can trim the = off the front e.g. with the MID string function i.e. if A1 contains your actual =2+3 formula, then

=MID(FORMULA(A1),2,LEN(FORMULA(A1)))

inserts literal string 2+3

---

