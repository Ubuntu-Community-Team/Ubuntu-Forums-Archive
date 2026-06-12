---
title: "[SOLVED] Urgent Help Needed"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by BSAB_80 on 2008-07-06
Hi guys.

A few hours ago i downloaded a flv file and associated it with kaffeine.

I immediately started getting a weird message whenever i tried to open a file or application "Could not find mime type application/octet-stream"

I couldn't get rid of it so i restarted the computer (old windows habits die hard) 

NOW NOTHING WORKS!!

I get that same error message over and over again while kubuntu is loading the desktop, i click all the error boxes away and then im left with a last one saying the same thing whose box title is "Sorry-KDesktop" and i cant click it away:

Seems like all the programs are loaded but i cant access them; i cant do pretty much a thing!

Any clues on how to get my computer back?


----------------------------------------------------------

EDIT:
Using my mate's computer i was able to solve it.

All i needed was to type:
> rm ~/.kde/share/mimelnk/application/octet-stream.desktop

Sorry for the panic guys, but maybe this one will help someone in a future situation!

---

