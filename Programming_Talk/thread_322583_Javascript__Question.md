---
title: "Javascript?  Question"
date: 2006-12-20
forum: Programming Talk
---

### Post by teabeartom on 2006-12-20
Does anyone know how I can make a web browser reload a certain page every 5 seconds and if it contains a certain URL to make it go there?  And if it doesn't contain the URL to just reload?

Here's my problem:  I need to register for an envelope of classes at my university.  I need to get into schedule 1, but it is full.  If it ever becomes available, the page will say "Add" rather than "full" and have a link to the following page like this: <a
href="https://marriottschool.byu.edu//studentfile/core_registration/add_schedule.cfm?schedule=1">

Is there a way to make a script that would control a web browser?  For example:
IF PAGE CONTAINS "aboveurl", then goto "aboveurl"
ELSE "reload"

Someone is bound to drop schedule 1 as the new year approaches because it is very early in the morning, I just want to be able to be the first to pick it up when it does get dropped.

Thanks everyone for any help!!!  There is an image attached to see the page.

---

### Post by Swab on 2006-12-20
Maybe you could write a python script to download the page every X seconds, parse it for the required phrase and then open firefox with the URL if it finds the phrase.

However I don't know if this would work for you as the page you are loading seems to be secure, and dependant on sessions most likely.

---

### Post by teabeartom on 2006-12-20
Yes, I have to log in first...  Maybe there is a way to open the page in firefox, then have a script do CTRL + U to open the source, then CTRL + F, then paste the URL, if not found, then do an ALT +F4 and then finally a CTRL +R to reload the page and redo the process?  Thanks for your help!

---

### Post by teabeartom on 2006-12-20
Actually, I just figured out that all I have to do is type in the URL to add schedule 1.  If it is available, it will automatically sign me up, and if not it will tell me that it is sorry that someone must have registered for it before me.  So, all I have to do is get the page to reload every 5 seconds or so... I think I can just do this with simple HTML.  Thanks everyone!

---

### Post by Tomosaur on 2006-12-20
Be careful with this - a lot of hosts will become suspicious of repetetitive requests, and although it's unlikely to be misconstrued as a DoS attack, they may block your IP for a while just to be on the safe side.

---

