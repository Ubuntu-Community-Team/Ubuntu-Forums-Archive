---
title: "Endless Login Loop, Only For One Account, And On An Account that was JUST working"
date: 2012-04-24
forum: New to Ubuntu
---

### Post by ubunoobian on 2012-04-24
I'm having trouble with a new install of 11.10, I set up an account and am perhaps able to login to it several times with no issues, then all of a sudden I am unable to get to the account's desktop, I am just sent back to the login screen every time I enter my credentials.  I am still able to login to my account using ctrl+alt+f1 and am able to enter the desktop of other profiles and guest sessions.
 
I have tried a couple of things that I have read, including deleting the .Xauthority file and have had no luck.  I have noticed that my .xsession-errors file contains things along the lines of "Cannot connect to display!".  I really can't figure out what is wrong as I believe that I had not changed anything that would affect this functionality in the last session before the login loop.
 
Any suggestions?

---

### Post by Peter09 on 2012-04-25
This can occur if you have put a corrupt file onto your desktop. Nautilus by default will try to read it and then crash - sending you back to your login prompt.
 
I would suggest that you backup the problem user directory and start deleting any file that could be read on startup. (Also - have you just installed a non-standard theme- that can sometimes do it - try switching back to a default theme)
 
Most files that are read on startup will be hidden (start with a .  )

---

### Post by ubunoobian on 2012-04-25
So I should just go around deleting any file beginning with a "." in any file?  Is there at least a place I should start or a file which may give me a hint on where to start?  The .xsession-errors file didnt provide much information about a problem file or setting.
 
In the past this has occured even with having added no files to the desktop.  I do recall that this last time it happened after I placed one file on the desktop which is plain text and which I had successfully edited prior to logging out.
 
I do not have any non-standard themes, just the one which came with the install which I got directly off of the ubuntu website.
 
Thanks again.

---

### Post by marl on 2012-04-25
I have the same problem, it's the second time this happens to me, last time I reinstalled ubuntu studio.  Here is the contents of the screen that flashes very quickly just before returning to the login screen:

> 

* Stopping anac(h)ronistic cron
* Stopping save kernel messages

* Starting the Winbind daemon winbind

* Starting bluetooth

* PulseAudio configured for per-user sessions[INDENT]                                              saned disabled; edit /etc/default/saned
[/INDENT][INDENT][INDENT]                                                                                     * Starting configure network device security
[/INDENT][/INDENT]* Starting configure network device

* Stopping cold plug devices

* Stopping log initial device creation

* Starting enable remaining boot-time encrypted block devices

* Starting configure network device security

* Starting configure virtual network devices

* Stopping configure virtual network devices

* Starting CUPS printing spooler/server

* Stopping enable remaining boot-time encrypted block devices

* Stopping Mount filesystems on boot



---

### Post by marl on 2012-04-25
Sorry [abc009]("http://ubuntuforums.org/member.php?u=1622615"), I really tought this forum was about helping people.

---

### Post by Peter09 on 2012-04-25
You could try deleting anything like .gnome*** most of these will be config files that will be recreated when you restart.

---

