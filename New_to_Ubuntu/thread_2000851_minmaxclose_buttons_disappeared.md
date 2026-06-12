---
title: "min/max/close buttons disappeared"
date: 2012-06-10
forum: New to Ubuntu
---

### Post by zhanglini on 2012-06-10
Hi, 
I use ubutnu 12.04 32bit and Gnome Fallback, all worked fine for a while and all of a sudden (don't remember what exactly I have changed), when I open apps, they don't show in the bottom panel any more, and min/max/clse buttons disappear.  Nor am I able to move any windows that are open.
When I click "show desktop" in the bottom left corner, it says "window manager" does not support the "show desktop" button, or "desktop manager" is not running.
How do I fix?
Thanks

---

### Post by Fuzzv on 2012-06-10
Sounds like your window manager crashed. Open a terminal with CTRL+ALT+T and type "compiz --replace &" (without quotes) and if that doesn't work try "metacity --replace &"

---

### Post by zhanglini on 2012-06-10
> **Fuzzv said:**
> Sounds like your window manager crashed. Open a terminal with CTRL+ALT+T and type "compiz --replace &" (without quotes) and if that doesn't work try "metacity --replace &"
The compiz command did not work, metacity works only when the terminal with the command is open.  When the terminal closes, it goes back to its broken state.
I also reinstalled metacity, to no avail.
Thanks

---

### Post by TVTrukChik on 2012-06-10
Try hitting Alt-F2, and then running the "metacity --replace" command from there.  That usually fixes it for me.

---

### Post by zombifier25 on 2012-06-10
> **zhanglini said:**
> The compiz command did not work, metacity works only when the terminal with the command is open. When the terminal closes, it goes back to its broken state.

That is because metacity is a job of the opening terminal. Closing the terminal will terminate all of its job too. Run this to "disown" the process:
```
metacity & disown
```

---

### Post by zhanglini on 2012-06-13
Thanks @TVTrukChick and @Zombifier25.
Alt+F2 did not invoke anything, I suppose gksudo does the same thing, so I tried that (gksudo metacity --replace) which was not accepted.  I also tried metacity & disown, and it worked only when the terminal was open.
Anyway, after many changes it was totally broken so I reinstalled 12.04 (which /home intact) and the problems remain (I can't even type in a terminal any more), so I figure there must be some settings in /home.  Do I Ctrl+Alt+F2, and add a user there.  Sure enough, the new user does not have these problems.
Is there a file I can copy from the new user to old user directory to fix this?  or I could start using my new identity...
Thanks

---

### Post by TVTrukChik on 2012-06-13
Look at the hidden folders in your home directory (the ones that start with a ".").  I want to say that it's probably the ones that start with ".gconf", but it's been a loooong while since I had to mess with this, and then it was with a much older version.  Maybe someone with a better memory will come by and give you a better answer. Don't think that I really know what I'm talking about here.

Two ways I found to enable a program to still run after you close the terminal you used to start them are "nohup command-name" and "command-name & disown -h".  Since you can't type in a terminal, maybe you could create a bash script in gedit and then run it by double-clicking in Nautilus, but I don't know if that would work or not.

---

### Post by zhanglini on 2012-06-14
> **TVTrukChik said:**
> Look at the hidden folders in your home directory (the ones that start with a ".").  I want to say that it's probably the ones that start with ".gconf", but it's been a loooong while since I had to mess with this, and then it was with a much older version.  Maybe someone with a better memory will come by and give you a better answer. Don't think that I really know what I'm talking about here.

Two ways I found to enable a program to still run after you close the terminal you used to start them are "nohup command-name" and "command-name & disown -h".  Since you can't type in a terminal, maybe you could create a bash script in gedit and then run it by double-clicking in Nautilus, but I don't know if that would work or not.

Thanks,
I solved the problem --- I had a script that sync my /home folder to a usb flash.  So I reverse-engineered it to sync the usb (only the hidden files/folders, with some exclusions such as firefox, libreoffice etc) back to /home.  All is working now.
Thanks for the help.

---

