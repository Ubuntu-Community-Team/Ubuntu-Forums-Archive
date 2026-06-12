---
title: "HP printer error 'filter failed'"
date: 2013-04-19
forum: New to Ubuntu
---

### Post by Sheenders on 2013-04-19
I am really new to Ubuntu and very limited in experience and troubleshooting skills  Have been Using Ubuntu 12.10 for a month or so and while I have had some problems there haven't been any printing problems once I had the HP Photosmart B210 working wirelessly.  That is until today.  Nothing really changed in settings, but now I get an error message 'filter failed' and printing doesn't work.  Tried to print hard wired and it doesn't work either.  I've looked on line and haven't found much in the form of help so I thought I would try the forum.  Hopefully, someone can shed some light on what is going on and what I need to do.  
 
Any help or guidance you can give would really be appreciated.

Thanks

---

### Post by tgalati4 on 2013-04-19
Look in /var/log/cups for clues to the problem.  Create another printer with a slightly different name and see if it prints.  If that works, then delete the old printer.  Sometimes the print queues get messed up and the only way to fix them is to delete and create a new printer.

Sometimes the printer needs to be reset.  Try unplugging for 10 minutes.

---

### Post by Sheenders on 2013-04-20
Finally got this working.  Creating a new printer worked perfectly.  That is something I would never have thought to do.

Thanks very much for your help and for getting me unstuck.

---

### Post by tgalati4 on 2013-04-20
I don't know why, but just like in Windows, when the print queue gets messed up, the only recourse is to delete it and create a new one.  Since this procedure works so consistently, I've never dug into why the queue gets messed up in the first place.  Certainly a stuck print job will stop a queue, but those are easy to see and delete.  But when the queue ceases to function and the error messages are cryptic, just delete and recreate.

Sometimes a power outage or flicker will cause a printer to not boot correctly, so the printer shows online or power, but doesn't respond normally.  Since many printers are power hogs and not recommended to hang off of an UPS, this is a common problem.

I'm glad you got it fixed.

---

