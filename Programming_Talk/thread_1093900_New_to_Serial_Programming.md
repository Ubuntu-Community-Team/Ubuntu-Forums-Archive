---
title: "New to Serial Programming"
date: 2009-03-12
forum: Programming Talk
---

### Post by talguy on 2009-03-12
I am new to serial programming.  I am trying to write a serial app that will let me send commands and receive the corresponding data from my vehicle's OBD.  I am using Libserial to to communicate with my vehicle.  Does libserial alwas return everything back as a hex string or is there anyway I can get the data to return as hexadecimal integers instead of characters.

---

### Post by CptPicard on 2009-03-12
> **talguy said:**
> Does libserial alwas return everything back as a hex string or is there anyway I can get the data to return as **hexadecimal integers** instead of characters.

:confused:

Well, hex is just a representation of an integer in base-16... the representation is always a string, and the represented number is always an integer.

I don't actually know libserial itself, but are you sure that it actually returns a string and you're not just seeing some rendering of it as hex in your printouts or something? That kind of string-returning would not really sound like a design I would adopt for such a library.

---

