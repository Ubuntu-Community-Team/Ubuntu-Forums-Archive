---
title: "Gambas and QT"
date: 2011-06-24
forum: Programming Talk
---

### Post by KoolPenguin on 2011-06-24
I have been fool'n with Gambas a bit and from what I have read it is supposed to support QT.  How are you supposed to import the QT Designer *.ui file into Gambas?  I cannot seem to find a way to import the form.

I know you can design forms within Gambas but, I prefer the QT Designer interface.

Thanks

--
Chris

---

### Post by kalaharix on 2011-06-24
Hi

Gambas 2 uses QT3. The new Gambas 3 (currently release candidate) uses QT4 (both can use GTK+ as well). All of these are graphics toolkits.

Gambas can't use a QT designer .ui file. It would be a interesting project to write an interface between Gambas and QT designer but ultimately pointless as the end result and method of getting there are the same.

---

### Post by KoolPenguin on 2011-06-24
> **kalaharix said:**
> Hi

Gambas 2 uses QT3. The new Gambas 3 (currently release candidate) uses QT4 (both can use GTK+ as well). All of these are graphics toolkits.

Gambas can't use a QT designer .ui file. It would be a interesting project to write an interface between Gambas and QT designer but ultimately pointless as the end result and method of getting there are the same.

So when it says on the Gambas website design your program GUI with QT4 they are refering to components that implement the GUI classes based on the QT library and not actually import the .ui file from QT designer?

--

Chris

---

### Post by kalaharix on 2011-06-24
Yup. Thats it.

---

### Post by KoolPenguin on 2011-06-25
> **kalaharix said:**
> Yup. Thats it.

Okay...Thanks!
--

Chris

---

