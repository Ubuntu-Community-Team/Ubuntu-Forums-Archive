---
title: "User's $home/.dmrc file is being ignored"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-05-16
Following the instructions on how to put the /home in a partition from:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I did a clean install of HH. Next, I did the cut & paste at Psychocats pages. When I rebooted I got the following:

(a yellow exclamation point in a triangle) and "User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by others."

I clicked the radio button to dismiss the error message. Then I was asked for my user name and password. Upon inputting those, the disk spun a moment and the I was asked for the user name and password again. So I shut the machine down, and am now here, via LiveCD to work on it.


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       37262       38536    10241437+  83  Linux
/dev/sda2           38537       38913     3028252+   5  Extended
/dev/sda3               1       37261   299298951   83  Linux
/dev/sda5           38537       38913     3028221   82  Linux swap / Solaris

Anybody got a clue as to what went wrong. Again, this is a fresh install. /home is empty, short of the directories that Hardy put into it.

---

### Post by Oldsoldier2003 on 2008-05-16
```
sudo chmod 700 /home/<your_user>
```
you might need to chmod the .drmc file to 644 as well

---

### Post by shifty_powers on 2008-05-16
had exactly the same thing.

do

gsksudo nautilus.

navigate to the .drmc file and right click and then properites.

make sure that the permissions are set to wonwed as you and read and write for you.

then go up until you can right click on your home folder.

click on properties.

go to permissions.

then make sure that only you can acess/read/write the folder.

log off and in again ;)

---

### Post by Mark_in_Hollywood on 2008-05-16
Please say whether the instructions you give can be done during a LiveCD session.

Just out of curiosity, I ran gksudo nautilus. I looked around and can NOT find /.dmrc

---

### Post by Oldsoldier2003 on 2008-05-16
> **Mark_in_Hollywood said:**
> Please say whether the instructions you give can be done during a LiveCD session.

they can but you would have to mount the ubuntu partition. Just login to recovery mode from the grub menu, its probably easier and faster,

---

### Post by shifty_powers on 2008-05-16
i think so, yes. you can certainly gksudo nautilus and if can mount the partition then i don't see why not.

not convinced wether the change will persist mind...

---

### Post by Oldsoldier2003 on 2008-05-16
> **shifty_powers said:**
> i think so, yes. you can certainly gksudo nautilus and if can mount the partition then i don't see why not.

not convinced wether the change will persist mind...

If you mount the partition the changes will persist because you are writing to the hard drive.

---

### Post by shifty_powers on 2008-05-16
true. well i did say i wasn't sure ;)

---

### Post by Mark_in_Hollywood on 2008-05-16
You all have lost me. If I'm in recover mode, how do I call gksudo nautilus? AND, I can't find the .dmrc, even with the disk mounted under the LiveCD session.

---

### Post by Oldsoldier2003 on 2008-05-16
> **Mark_in_Hollywood said:**
> You all have lost me. If I'm in recover mode, how do I call gksudo nautilus? AND, I can't find the .dmrc, even with the disk mounted under the LiveCD session.

from recover mode:

```
chmod 700 /home/<yourusername>
chmod 644 /home/<yourusername>/.dmrc
```

---

### Post by rbc on 2008-05-16
The "." in front of drmc means that it is hidden. In nautilus, hit "Crtl H" to show hidden files

---

### Post by Mark_in_Hollywood on 2008-05-16
From the Recover Mode:

First time on reboot from the LiveCD, I get a garbled screen which on another reboot shows the X-Session screen. I selected root terminal. 

Tried chmod 700 /home/mark

that worked.

tried: 

chmod 644 /mark/.dmrc

and received: No such file or directory error

---

### Post by Oldsoldier2003 on 2008-05-16
> **Mark_in_Hollywood said:**
> From the Recover Mode:

First time on reboot from the LiveCD, I get a garbled screen which on another reboot shows the X-Session screen. I selected root terminal. 

Tried chmod 700 /home/mark

that worked.

tried: 

chmod 644 /mark/.dmrc

and received: No such file or directory error
```

chmod 644 /home/mark/.drmc
reboot now
```
and everything should be fine

---

### Post by das7002 on 2008-05-18
Thanks Oldsoldier2003 your first post worked
sudo chmod 700 /home/<your user>
sudo chmod 644 /home/.dmrc

I used that and tada no more annoying popup before login!!

---

### Post by thojoh on 2008-12-10
YES! SOLVED! :guitar:

Seconding das7002 and Oldsoldier2003.

I do not know exactly why I had the "User's $home/.dmrc file is being ignored..." error coming up at startup, but I could solve it easily with Oldsoldiers commands, to be typed in the terminal window:

```

chmod 700 /home/<yourusername>
chmod 644 /home/<yourusername>/.dmrc

```

Thanks!

---

