---
title: "VB6 what is difference between call and just running a sub"
date: 2009-01-14
forum: Programming Talk
---

### Post by fokuslee on 2009-01-14
Hi 
2 questions:

1. What is the difference between Call a procedure like a function
or just run the procedure..
Thanks abunch

2. How do i initialize some var values in class, so that everytime an object is created it has those initial variables

---

### Post by eye208 on 2009-01-14
The Call keyword is optional. It is a relic from older BASIC versions.

To initialize a class object, write a subroutine "Class_Initialize". Note that this is only valid for VB6. VB.NET uses proper constructor functions.

Are you using VB6 on Linux?

---

### Post by fokuslee on 2009-01-14
thank you for the explaination 

no im programming extension to ESRI's GIS. windows only  

I just posted here b/c of friendly help i got from past.

but im learning python and they have a few ide for linux 

currrently running on vm

---

