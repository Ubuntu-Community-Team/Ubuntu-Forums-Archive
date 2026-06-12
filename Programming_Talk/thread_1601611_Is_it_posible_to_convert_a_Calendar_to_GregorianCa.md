---
title: "Is it posible to convert a Calendar to GregorianCalendar  in java ?"
date: 2010-10-20
forum: Programming Talk
---

### Post by hoboy on 2010-10-20
I have actually google for this.
 is it possible to convert a Calendar to Gregorian calendar using java ?
does any body has an example java code that can do this ?

---

### Post by Some Penguin on 2010-10-20
Usually a Calendar will actually *be* a GregorianCalendar.  The former is an abstract base class and the latter is an actual implementation.

Otherwise, create a GregorianCalendar and newGC.setTimeInMillis(oldNonGC.getTimeInMillis()).

---

### Post by hoboy on 2010-10-20
> **Some Penguin said:**
> Usually a Calendar will actually *be* a GregorianCalendar.  The former is an abstract base class and the latter is an actual implementation.

Otherwise, create a GregorianCalendar and newGC.setTimeInMillis(oldNonGC.getTimeInMillis()).

tks.
you are right.
Calendar local = new GregorianCalendar();		
GregorianCalendar locals= new GregorianCalendar();

---

