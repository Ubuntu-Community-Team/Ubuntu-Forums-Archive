---
title: "new partitions with gparted-Live"
date: 2013-10-09
forum: New to Ubuntu
---

### Post by linuxnewbie3 on 2013-10-09
Hi,

I am going to use dualboot on my PC (Windows 7 already is on the PC and I am adding Ubuntu).

After some research, I know, that I will have to do new partitions that everything works.

Now my partitions are like you see in the screen below

I want to format them like that:

sda1 Recovery   
sda2 Windows-Boot-Partition
sda3 NTFS Windows about 100 GB 
sda4 Extendet
sda5 ext4 Ubuntu / 30GB
sda6 swap swap      8GB
sda7 NTFS Data (rest size of my harddrive.)

Like you can see also resizing sda 3 which has to be my first step is not possible.

I was tolt that this doesnt work with Ubuntu live because Ubuntu Live uses C: and therefore it can't resize it because C: is being used. Like I'm told I got gparted-Live but the same warning sign (and no sizes) are beeing showed. Addtionaly I cant use my mouse, neither touchpad from my laptop nor the external Logitech Wireless mouse with gparted.

How can I solve both problems (resizing C: and using mouse with gparted-Live)?


Screen:
[http://s7.directupload.net/images/131008/n95bag5j.png](http://s7.directupload.net/images/131008/n95bag5j.png)

---

### Post by deadflowr on 2013-10-09
Don't know what you mean by C, but if you mean the C drive of Windows, then no Ubuntu-LiveCd doesn't mount it, so it shouldn't be in use.

That being said, in terms of resizing Windows partitions, always use Windows partition tools (Windows disk management, if I remember right).
Disk Management on Windows does a better job dealing what the ways and means of Windows partitions than gparted or any other partition tool used for linux.

More
[https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)

---

### Post by mastablasta on 2013-10-09
+1 on using widnows disk management

also ubuntu live does not use the drive but loads itself into RAM (which is why all changes are lost on reboot (well except if you put them on hard disk).

---

### Post by linuxnewbie3 on 2013-10-09
Argh, on an other ubuntu-forum (a german one where I asked firstly because my english is not that good) they said I should only use gparted and no Windows Disk managment.

Ok, I resize my main drive to 100GB and all the other stuff I do with Gparted on my Ubuntu Live-CD and then I am readdy to install Dualboot, correct?

---

### Post by westie457 on 2013-10-09
Hello, have just had a look at your screenshot.

Gparted will not resize the Windows partition because there is a lot of errors on the file system and the Linux file system checking tools will not repair them.

Boot Windows into 'Safe Mode with a Command Prompt' tapping the F8 key during the POST screen.

At the Command Prompt type in 'CHKDSK /F' and hit Enter. When that has finished run the command again, just in case not all the errors were fixed on the first run.
When the CHKDSK command has run with no reported errors then you can reboot Windows normally and do your partition (drive) resizing.

Then you should be good to go with the Ubuntu install.

---

### Post by mastablasta on 2013-10-09
so if you really have errors then repair them first as suggested.
defrag the drive 2 times.
resize using the windows disk manager tool (it's safer)
leave the empty space unformatted

now install and when you do choose to largest empty disk space. if not then manually set / (root) partition formatted in ext 4 and /swap paritition (in kubuntu i think it says the file system format for this one is swap). and then continue. it will all go smoothly as long as you do not have 4 primary parittions already. if you do then just change the resized partition into extended (secondary/logical)

---

### Post by linuxnewbie3 on 2013-10-09
Using CHKDSK worked fine thanks.

But with Windows I only can size it to about 270GB but I want it to resize it to 80 - 100GB. I used the system defragmentation and the tool Auslogics Diskdefrag but no change.

Then i tried to resize it with Ubuntu. It crashed and I had to use CHKDSK again.

I heard that I should use the gparted Live-CD but with that one my mouse doesnt work and therefore I cant use it.
What can I do now to resize it to 100GB

Screen:

[http://s1.directupload.net/images/131009/2bna4jg3.jpg](http://s1.directupload.net/images/131009/2bna4jg3.jpg)

---

### Post by westie457 on 2013-10-09
Me again.
To be able to shrink Windows to a much smaller space you have to remove 'hiberfil.sys'. This file is created near the end of the drive space and Windows marks it as unmovable.

You must have Windows running to be able to remove the file. Any other will probably break your system.

This tutorial from 'sevenforums' should be able to help you.

[http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html](http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html)

---

