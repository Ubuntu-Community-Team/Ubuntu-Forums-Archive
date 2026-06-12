---
title: "[SOLVED] Start up programs"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by waspbr on 2008-07-01
okay, I know this is a silly question so I am posting this in this section... but it is driving me nuts, does anyone know what file do I have to edit to get rid of a few pesky start up programs.

It all started the day, I went to System>Preferences>Sessions and on the session option tab I clicked on the button,'remember currently running apps". Fine, for some time it was convenient, but it got a little old, so I went on to close all the apps running and  repeated the same procedure, now tomboy, songbird and awn manager still pop up every time I boot, and the annoying thing is that I had stopped using the AWN dock and started using the cairo dock. So on the awn option I unchecked the "open at start up option" but no cake for me, still pops up on start up.So I went to the sessions GUI again and to the start up programs tab to remove whatever was left, I did that but they still haunt me...

any help would be trememdously appreciated

---

### Post by bijeeshvs on 2008-07-01
go to System>Preferences>Sessions and use the startup programs tab there, uncheck the programs u dont want to run at startup......................

---

### Post by nkri on 2008-07-01
System>Preferences>Sessions has a lot of the startup programs, but not all.  There are also others and some duplicates in System>Administration>Services, so you should check there and see if there's anything you need to deselect.

Good luck!

---

### Post by waspbr on 2008-07-01
that's exactly my point, I went to System>Preferences>Sessions and then to the start up programs tab, deselected the relevant programs but they still keep on popping up at start up.

---

### Post by seetho on 2008-07-01
What programs exactly that you do not want to run at startup?

---

### Post by waspbr on 2008-07-01
AWN, songbird and tomboy notes, I was using them a lot at some point but now, not so much, AWN takes a while to load. I kinda prefer cairo dock atm... 

I could uninstall some of them,(AWN), but I'd rather keep it around inactive, that's why i am posting here, to find a way out without uninstalling anything...

---

### Post by Najmudin on 2008-07-01
I was having the same issue with awn, you will find a tab named "current session" in session prefrences ,try to find & remove any awn and other application you dont want them to startup from the list , then press apply, try to close all the running applications and save the session.
I hope this can help you.

---

### Post by jspolen on 2008-07-01
Check your $HOME/.config/autostart folder

---

### Post by seetho on 2008-07-01
Try looking in ~/.config/autostart

---

