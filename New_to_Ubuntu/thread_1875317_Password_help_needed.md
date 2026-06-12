---
title: "Password help needed"
date: 2011-11-04
forum: New to Ubuntu
---

### Post by jfever311 on 2011-11-04
For some reason my laptop is no longer asking for my password upon opening it up. It has been like this for a week or two, ever since I put xscreensaver on it. How do I get it back to where it asks for a password every time it goes to sleep or gets closed for the night? Passwords are important to me, and my privacy.

My terminal looks like this upon opening it:

jason@jason-Compaq-Presario-CQ60-Notebook-PC:~$ 
 

Am I in root mode?

Any help would be greatly appreciated.

Jason

---

### Post by jnorthr on 2011-11-04
as i understand it, you will never be asked for a password to close down your sessions. Password entry is only for 1)the initial log on you have been booting system from power-up or 2) if you close the lid on a laptop, or otherwise place your system into sleep mode. Then it MAY or MAYNOT ask for a password depending on how your system is set.

doing some backups just now so cannot test this myself. will try this shortly.

---

### Post by jfever311 on 2011-11-04
Okay, I uninstalled xscreensaver thinking that would do the trick. Nope, still is not asking for my password upon opening my laptop. As of right now anyone could steal my computer and use it like their own. Not cool at all!!

---

### Post by jfever311 on 2011-11-04
> **jnorthr said:**
> as i understand it, you will never be asked for a password to close down your sessions. Password entry is only for 1)the initial log on you have been booting system from power-up or_** 2) if you close the lid on a laptop, or otherwise place your system into sleep mode**_. Then it MAY or MAYNOT ask for a password depending on how your system is set.

doing some backups just now so cannot test this myself. will try this shortly.

This is what it is NOT doing. Until a week or so ago, every time I opened my laptop, I would have to enter my password, and that is how I like it to be.

---

### Post by jnorthr on 2011-11-04
are you using a gui for your work or do you only use console terminal access ?

UPDATE: just found this which may/not help: [http://ubuntuforums.org/showthread.php?t=1874577](http://ubuntuforums.org/showthread.php?t=1874577)

---

### Post by jfever311 on 2011-11-04
[SIZE=2]> **jnorthr said:**
> are you using a gui for your work or do you only use console terminal access ?

UPDATE: just found this which may/not help: [/SIZE] [SIZE=2][http://ubuntuforums.org/showthread.php?t=1874577](http://ubuntuforums.org/showthread.php?t=1874577)


I am new to all this, and I have no idea what you just said.... :confused:

On the second note, I have read that one. I know my password, so that does not need reset. 

Most of the threads on here have been to DISABLE the password prompt in Oneiric Ocelot (11.10). Mine is already disabled, and I want to ENABLE it. This latest version has a bug.[/SIZE]

---

### Post by jfever311 on 2011-11-04
:guitar:

SOLVED!!!

I had to reinstall gnome screen saver, enable the lock feature in system settings, and then reboot. Now upon closing the lid and then opening it back up, I am asked for my password. My computer is safe again. Yay!!

Only thing is.... no screen saver. Oh well, I will gladly trade off some screen savers for the security of my system.

---

