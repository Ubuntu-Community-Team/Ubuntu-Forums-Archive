---
title: "BadDevice, invalid or uninitialized input device 167"
date: 2007-04-22
forum: Programming Talk
---

### Post by Ne0z on 2007-04-22
> X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device



hi guys 
any idea what error is this ?

i'm a program to set up my pc as a server but when i ran my program it gave the above error. 

thanks for ur help guys :)

regards

---

### Post by JT673 on 2007-04-22
Woah!  You're a program :O?  You must be a very smart program to report here!  Can I meet your programmer?

Back to business...I get that error sometimes, but it doesn't affect my Internet connection.  I wouldn't worry too much on it, maybe look it up on Google or Launchpad.

---

### Post by Ne0z on 2007-04-23
oops, 

correction ! 
 
I HAVE a program .. 
haha

---

### Post by lptr on 2007-04-28
Same here on Feisty:

```
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```Any time I'm running adept updater getting this error. Nothing appears in /var/log/messages.

Would be great to know where it comes from.

Anyone of the X-guys hanging in here to give us a hint?

rob*

---

### Post by nemarona on 2007-04-30
Good to know I'm not the only one. I've had this error ever since the early days of Hoary. No idea what it is, although it seems to do no harm...
```
eduardo@altepc:~$ kate foo.txt
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```
It happens quite often, with a variety of commands. I have no clue. Anyone?

---

### Post by nemarona on 2007-04-30
OK guys, the solution's here:

[http://kubuntuforums.net/forums/index.php?topic=7964.0;topicseen](http://kubuntuforums.net/forums/index.php?topic=7964.0;topicseen)

It amounts to commenting out some offending lines in your /etc/X11/xorg.conf file. No idea why it works, though.

---

### Post by cyberslayer on 2007-04-30
You need to remove the wacom devices in xorg.conf.  Type the following:

```

cd /etc/X11
sudo cp xorg.conf xorgbackup.conf
sudo gedit xorg.conf

```

There are three sections in xorg.conf for wacom devices.  Delete all three.  Now go down to the bottom of the file and remove the three InputDevice entries for the wacom devices under the ServerLayout section.  Save the file and reboot.  This should fix the errors.

---

### Post by lptr on 2007-05-02
yes, this does the job. Thank you guys. 

Wacom: Well, I expect here on this box I will never need such a thing.

rob*

---

