---
title: "Understanding SUDO"
date: 2014-04-10
forum: New to Ubuntu
---

### Post by kellyvotrenom on 2014-04-10
I had been pursuing this in "Hardware" but my question now is about running programs.  I finally got my Griffin Powermate to work - but I can only run it if I invoke 'sudo'


Here's what I did:

- Clean install of Lubuntu

- Installed evrouter

- Created /etc/udev/rules.d/powermate.rules and made sure I was part of the powermate group:
SUBSYSTEM=="input", ATTRS{idVendor}=="077d", ATTRS{idProduct}=="0410", SYMLINK+="powermate", MODE="660", GROUP="powermate"

- ran 'sudo restart udev'

- The content of /etc/evrouterrc is this:
Window ""
"Griffin PowerMate" "" any key/256 "XKey/XF86AudioMute"
"Griffin PowerMate" "" any rel/7/1 "XKey/XF86AudioRaiseVolume"
"Griffin PowerMate" "" any rel/7/-1 "XKey/XF86AudioLowerVolume"


- And then created  /usr/local/bin/powermate:
#!/bin/sh
evrouter -c  /etc/evrouterrc  /dev/powermate


- Logged out and back in an it didn't run so I tried this command in terminal:
'evrouter -c /etc/evrouterrc /dev/powermate'

 - That didn't work, but this did:
'sudo evrouter -c /etc/evrouterrc /dev/powermate'


Why does it only run as sudo? My understanding of 'sudo' is that I am running it as root, not as a user. I tried placing 'evrouterrc' (as well as .evrouterrc) in the home folder and my user folder, but it wouldn't run using  'evrouter -c /etc/evrouterrc /dev/powermate' or a few other variations I tried.  I tried to re-log in and reboot but it won't run unless I run it as sudo.  Can someone tell me why and how to fix this?  


And then - how would I get it to run on log-in?


Thanks


Mark Springer
industrial arts




I found the information on these links:
 [http://screamingroot.org/node/5](http://screamingroot.org/node/5)
[http://www.mp3car.com/input-devices/146252-using-griffin-powermate-in-linux.html](http://www.mp3car.com/input-devices/146252-using-griffin-powermate-in-linux.html)
[http://www.linuxquestions.org/questions/linux-hardware-18/don't-understand-instructions-for-griffin-powermate-mouse-4175490996/](http://www.linuxquestions.org/questions/linux-hardware-18/don't-understand-instructions-for-griffin-powermate-mouse-4175490996/)

---

### Post by grahammechanical on 2014-04-10
Just a guess. Who owns the script "powermate?" We usually need administrator privileges to create scripts in system folders. That, I think can cause the script to be owned by root/administrator. Try, with administrator/sudo privileges, to change the ownership to any user.

Regards.

---

### Post by Lars Noodén on 2014-04-10
What is the exact error message, if any?  Also, what are the actual permissions for /dev/powermate?  Check that it is in the right group for your user and that the group has write permission.

---

### Post by kellyvotrenom on 2014-04-13
Here are the results from terminal when I attempt to invoke the program

evrouter -c /etc/evrouterrc /dev/powermate
evrouter: error opening device /dev/powermate: Permission denied
evrouter: no input devices were opened. Exiting.


sudo evrouter -c /etc/evrouterrc /dev/powermate
 device  0: /dev/powermate: Griffin PowerMate
Display name: :0
Parsed 3 rules, 144 bytes


Went to check the permissions on etc/evrouterrc & etc/udev/rules.d/powermate.  Both were set to 'only owner' & 'nobody' for change and execute, respectively.  Changed to 'owner and group' in both fields on both files with no results & then tried 'anyone'. Logged out and in after every change.  Still the same - only runs with sudo.  What am I missing?


Thanks
Mark Springer
industrial arts

---

