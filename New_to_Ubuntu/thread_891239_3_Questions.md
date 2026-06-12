---
title: "3 Questions"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by faron45 on 2008-08-15
Trying to install the "lock screen" option,I right click on the task bar & choose "add new item" click on "action buttons" & "add" [which from there I should be able to log out or lock the screen,right ?].

 Unfortunately,I can add the icon to the panel but,that's all.It is non- functional.When adding the item to the panel,it doesn't even ask me for a password to make it functional.Anybody have any ideas ? 

           All help greatly appreciated.
                   Yer pal,J.Garcia:guitar:

---

### Post by loell on 2008-08-15
what happens when you click it? after adding it?

the password is set to your password.

---

### Post by nicedude on 2008-08-15
I usually use Ubuntu but out of the 3 PC's directly in front of me one has Xubuntu on it and I just tried the same thing you were trying and it would not work for me either. So I guess that panel action app is not working for all :-( You could file a bug report, other than that I don't know what to tell you. Is it super important for you to be able to lock the desktop? 

Could someone help this person with some advice on an alternate way to lock the desktop in Xubuntu ?

---

### Post by faron45 on 2008-08-15
Loell-nothing.Hmph !
nicedude-It [might] be.Important,that is.

Thanks again everybody.Gotta run out for about an hour but,I'll be back ! Fair warning ! Heh,heh.

      
                   J.Garcia:guitar:

---

### Post by t0p on 2008-08-15
Okay, I just succesfully added the Lock Screen button.

This is how I did it:

1. Right click on panel

2. Select Add New Item

3. Select Action Button

4. Panel Actions window appears - Select action type Lock Screen

5. Close Panel Actions window.

A padlock icon appears on the panel - I click on it and the screen locks.

I don't know why this isn't working for you.  I'm running xubuntu hardy.

---

### Post by nicedude on 2008-08-16
I am running 8.04 as well and t0p it doesn't work here, maybe because I am watching a video on that box at the same time ? Maybe because its my torrent download box and thats running ? but it doesn't lock the screen, I could care less as I use physical security to secure my immediate environment, so I don't know as I have never cared for screen lockers anyway as they are all defeated with a simple boot disk anyway ( encrypted disks are the only real digital security ). But if someone knows of another program this person could use to lock his desktop, please sound off.

---

### Post by hansdown on 2008-08-16
This thread might help.  [http://ubuntuforums.org/showthread.php?t=820886](http://ubuntuforums.org/showthread.php?t=820886)

---

### Post by jimmy the saint on 2008-08-17
Check if gnome-screensaver is running.  Many of the screen related security and power settings rely on it to function properly, and it is not set to run at startup by default. This is a bug that should have been addressed by now, but only in new iso images.  check the 7th post in this thread:
[http://ubuntuforums.org/showthread.php?t=854557](http://ubuntuforums.org/showthread.php?t=854557)

it will also fix other issues like password on resuming from suspend, your screen power options, and your screensaver.

---

