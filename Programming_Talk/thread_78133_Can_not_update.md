---
title: "Can not update"
date: 2005-10-17
forum: Programming Talk
---

### Post by penguinchrissy on 2005-10-17
When ever I try and update I get this error message

Unable to get exclusive lock and something about apt-get is running. 

I tired restarting the computer and I got the same thing what is up. I just did in install of Easy Ubuntu if that helps

---

### Post by aysiu on 2005-10-17
Only one installer program can be running at any given time--apt-get, Synaptic, KPackage, Adept, etc. Maybe try ```
sudo killall apt-get
```

---

### Post by penguinchrissy on 2005-10-17
I did the 
sudo killall apt-get

dj@dhcppc4:~$ sudo killall apt-get
apt-get: no process killed

I still get the same error message
This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first

I also tired 
sudo killall aptitude

---

### Post by pranith on 2005-10-18
run this command in terminal
[COLOR="Red"]sudo rm /var/lib/apt/lists/lock[/COLOR]
and try updating after running that command

pranith

---

### Post by ad noiseam on 2005-10-19
I have the exact same problem as the original poster, and none of these solutions worked. However, typing "sudo synaptic" in a terminal did the spell.

Br... another thing that was working well in Hoary and is broken in Breezy. :-(

---

### Post by Shabba on 2005-11-01
In terminal type..

sudo dpkg --configure -a

And don't go blaming Breezy again ;)

---

### Post by normanp on 2006-01-07
Thanks for sudo dpkg --configure -a
Thsi did the job after trying to complete a failed real player install and lots of clicking of OK to the Exclusive lock message.
However I still don't have a working Real player (I want to listen to the BBC)!

---

