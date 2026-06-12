---
title: "[SOLVED] mercury in system tray"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by kavmac on 2008-06-15
i'm hoping there's an easy fix for this one...

i just installed hardy on my laptop the other day, got my java going and installed mercury im.  all is well.  except when i go to close the main mercury window, it closes mercury completely.  it doesn't get its own dedicated icon in the system tray (sounds too windows-y, sorry) - my brother's got hardy installed on his desktop, and he is able to get the dedicated icon that will allow him to close the main app window without actually closing mercury... when i had hardy installed on my desktop before i went back to using gutsy on it, it had the dedicated icon....  anyone know how to get it to show up and start using it's job?  it's not a huge issue having the main app window in my panel, but because i'm accustomed to xing it, i fear disconnecting every time!


thanks :)

---

### Post by kavmac on 2008-06-16
has anyone else experienced this situtation?  anyone?!

---

### Post by Joeb454 on 2008-06-16
Try not to bump too often :)

Make sure Mecury is open, and then from a terminal, type ```
sudo apt-get install alltray
``` Then run it from Applications > Accessories > AllTray

Click on the Mecury window, and it should minimize it to the tray :)

---

### Post by taith on 2008-06-16
thanks for that program :P

i was also looking for a way to add custom programs into the notification area... now to find a way of switching the font colours of the window list... lol

---

### Post by Joeb454 on 2008-06-16
I think there's a program to change the font colours in the panel's, but I can't remember what it's called :(

---

### Post by kavmac on 2008-06-16
thanks :)

---

