---
title: "Problems after update"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by xdarkday on 2008-08-26
I saw an update this morning, so I updated. It required a restart. When ubuntu booted my mouse no longer worked. I have a wireless Microsoft mouse. The wireless receiver that glows green looks like it doesn't even turn on. Im thinking this might be a USB issue more than a mouse issue, as I booted xp (for the first time in months) to post this message, and the mouse is working.

Would love some help :)

---

### Post by nicedude on 2008-08-26
try seeing if your wireless mouse shows up in the following command and post the results here.

lsusb

I am assuming of course that this is a USB wifi adapter to mouse type setup.

---

### Post by xdarkday on 2008-08-26
Ok weird. I did restart a few times to make sure before, but now it is working all of a sudden.

Here is what that command listed
> Bus 003 Device 002: ID 05e3:0702 Genesys Logic, Inc. USB 2.0 IDE Adapter
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 056a:00b1 Wacom Co., Ltd 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 045e:008c Microsoft Corp. Wireless Intellimouse Explorer 2.0
Bus 001 Device 004: ID 045e:0710 Microsoft Corp. 
Bus 001 Device 003: ID 058f:9254 Alcor Micro Corp. Hub
Bus 001 Device 001: ID 0000:0000  

---

### Post by Crafty Kisses on 2008-08-26
Your mouse is definitely showing. Sorry for all the outputs, post the results of this output > dmesg

---

### Post by xdarkday on 2008-08-26
> richard@richard-desktop:~$ output > dmesg
The program 'output' is currently not installed.  You can install it by typing:
sudo apt-get install yagiuda
bash: output: command not found
richard@richard-desktop:~$ sudo apt-get install yaguida
[sudo] password for richard: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package yaguida
.

---

### Post by nicedude on 2008-08-26
sudo apt-get install yagiuda
bash: output: command not found


richard@richard-desktop:~$ sudo apt-get install yaguida <-- That should have been yagiuda ( I almost didn't catch it myself as that one is a screwy word :-) )

But by its working I am assuming you mean your mouse now works? If so you might see if it is more of a finicky wifi mouse situation and if it will continue to work without further fixing. If you meant that it just shows up in lsusb but doesn't function then that is another matter. Let me know which one and if it is working try putting it through its paces for a day and see if it continues to do so.

Hope all this has helped you out :-)

---

