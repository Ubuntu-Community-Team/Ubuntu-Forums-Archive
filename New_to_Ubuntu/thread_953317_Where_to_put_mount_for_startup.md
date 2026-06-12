---
title: "Where to put mount for startup"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by TideMan on 2008-10-20
I currently have my mount commands:
```
mount -t smbfs -o username=etc
```
in ~/.bashrc, but they don't work at startup because "only root can do that".  So where should I put them?

---

### Post by Liviu-Theodor on 2008-10-20
What happens if you put that command in [FONT="Courier New"]System->Preferences->Sessions[/FONT]?

---

### Post by loomsen on 2008-10-20
Depending on when you want it to be mounted you could put a script (see manpages first) into one of the /etc/rc1.d - /etc/rc5.d

If you'd knew what runlevel are you prlly wouldnt have asked, so I'd suggest reading a documentation. rc5.d however is the last runlevel, so, if you just wanna make sure it's started, but it doesn't matter when, start it after S30gdm. 

Note that rc6.d is the shutdown runlevel. So the one you as GUI user usually act in is rc5.

runlevel:
```

ID	Name	Description
1	Single-User Mode	Does not: configure network interfaces, start daemons, or allow non-root logins.[2]
2	Multi-User Mode	Does not: configure network interfaces or start daemons.[3]
3	Multi-User Mode with Networking	Starts the system normally.[4]
4	Unused	in special purpose
5	X11	As runlevel 3 + display manager.

```

from [http://en.wikipedia.org/wiki/Runlevel](http://en.wikipedia.org/wiki/Runlevel)

---

### Post by DemonBob on 2008-10-20
You can add the share to your fstab to mount at boot. 



[http://www.cyberciti.biz/faq/configure-a-system-to-automount-a-samba-share-with-etcfstab/](http://www.cyberciti.biz/faq/configure-a-system-to-automount-a-samba-share-with-etcfstab/)

---

### Post by TideMan on 2008-10-20
Here is my new fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=55600746-7e24-4692-b901-5e909680acbe /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=1227b33b-9b53-4954-8250-62249708c124 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
"//benji/Kodak Pictures" /home/TideMan/Pictures   smbfs   username=me,password=pwd 0 0
```

but when I re-booted nothing happened, whereas if I do this:
```
sudo mount -t smbfs -o username=me,password=pwd "//benji/Kodak Pictures" /home/TideMan/Pictures
```
it works fine.

What am I doing wrong?

---

### Post by TideMan on 2008-10-20
> **Liviu-Theodor said:**
> What happens if you put that command in [FONT="Courier New"]System->Prefernces->Sessions[/FONT]?

Nothing happens.  It doesn't mount.
Perhaps it's the order in which things get done?
If Samba does her thing **after** I've tried to mount, it won't work.
I have to mount after Samba has connected to the network.

---

### Post by loomsen on 2008-10-20
Oh well, you can't edit your fstab like this. 

You should definetely read some manuals bout namespace definitions. And I'd definetely recommend just creating a bash script you run on startup until then...
You'll encounter many many more problems if you keep editing systemfiles like that ^^

[http://linux.about.com/od/linux101/l/blnewbie3_1_1.htm](http://linux.about.com/od/linux101/l/blnewbie3_1_1.htm) start there for instance

---

### Post by TideMan on 2008-10-20
> **loomsen said:**
> Oh well, you can't edit your fstab like this. 

You should definetely read some manuals bout namespace definitions. And I'd definetely recommend just creating a bash script you run on startup until then...
You'll encounter many many more problems if you keep editing systemfiles like that ^^

[http://linux.about.com/od/linux101/l/blnewbie3_1_1.htm](http://linux.about.com/od/linux101/l/blnewbie3_1_1.htm) start there for instance

When you say I **can't** edit my fstab like this, you're wrong. I just did.  Do you mean that I **shouldn't** edit it like that?  Then how?
I was following this: 
[http://www.cyberciti.biz/faq/configure-a-system-to-automount-a-samba-share-with-etcfstab/]("http://www.cyberciti.biz/faq/configure-a-system-to-automount-a-samba-share-with-etcfstab/")

Yes, I first tried using a bash script, but it said that "only root can do that".  How can I do root stuff in a bash script?

---

### Post by loomsen on 2008-10-20
Copy this:

```

#!/bin/bash
sudo mount -t smbfs -o username=me,password=pwd "//benji/Kodak Pictures" /home/TideMan/Pictures

```
to a file, name it whatever, foo_bar.sh
save and close the editor.
Open up a terminal and do:
```

sudo chmod +x /path/to/foo_bar.sh && sudo chown root:root /path/to/foo_bar.sh

```

Either add /path/to/foo_bar.sh to your startup in:
System-->Pref-->Sessions (which I'd recommend)
##############

Just do it.

---

### Post by TideMan on 2008-10-20
OK, I've created a file MountPics.sh:
```
#!/bin/bash
sudo mount -t smbfs -o username=me,password=pwd "//benji/Kodak Pictures" /home/tideman/Pictures
sudo mount -t smbfs -o username=me,password=pwd "//xcase/My Pictures" /home/tideman/Pictures/xcase
```

When I run this by double clicking it, it works.  Both Kodak Pictures on benji and My Pictures on xcase mount correctly.

But it doesn't seem to work from System/Preferences/Sessions when I re-boot.  Yet I have a conky start up that works from there OK, and I've set this one up the same way, so I think I've configured it correctly (it's pretty much wanker-proof I think).

---

### Post by ianhaycox on 2008-10-20
Try using the fstab solution but remove the quotes and escape the space. E.g.

```
//benji/Kodak\ Pictures /home/TideMan/Pictures   smbfs   username=me,password=pwd 0 0

```

or possibly change the share name to remove the space avoiding the need for quotes or escapes.

You can test it without rebooting by

```
sudo mount -a
```

---

### Post by tjandracom on 2008-10-20
if you are using static ip address, you could try to use the ip address instead of host name on fstab:
```
//192.168.0.111/Kodak_Pictures /home/TideMan/Pictures   smbfs   username=me,password=pwd 0 0
```

if you must use the hostname, then you should edit file /etc/hosts to add the computer name and its ip address.
works for me.

---

### Post by TideMan on 2008-10-20
Actually, what I said in my last post was not quite correct.
When I double click MountPics.sh or run it from a Terminal, it asks me for the password.  Is there some way of setting it so that it does not require a password?

---

### Post by TideMan on 2008-10-20
But how do I handle the directory in Win XP which is:
Kodak Pictures i.e. it has a space, not _ between the words?
I tried ianhaycox solution, but got:
[mntent]: line 11 in /etc/fstab is bad

---

### Post by ilrudie on 2008-10-20
From the man pages for fstab:

If the  name  of  the  mount point contains spaces these can be escaped as ‘\040’.

It does not mention what to do if the device (samba share in your case) has a space in it but this is probably worth a try:

'//192.168.0.111/Kodak\040Pictures'

Also samba (or any network share) should not be mounted in fstab.  If you have a network share in fstab that is not available your system may lock when trying to boot.  Its best to set network shares to noauto and give users who may need to mount them sudo permissions to do so.

---

### Post by TideMan on 2008-10-20
```
Also samba (or any network share) should not be mounted in fstab. If you have a network share in fstab that is not available your system may lock when trying to boot.
```

Yes, I had this problem and had to use my live CD to edit fstab and remove the line I had added.  Now, I'm back working again (phew!!), having learned my lesson about editing files like fstab.

So, I'm back to trying to make my file MountPics.sh load automatically.  It looks like this:
```
#!/bin/bash
sudo mount -t smbfs -o username=me,password=pwd "//benji/Kodak Pictures" /home/tideman/Pictures
sudo mount -t smbfs -o username=me,password=pwd "//xcase/My Pictures" /home/tideman/Pictures/xcase
```

When I double click it, it opens a terminal window and asks for my password, then it mounts the directories correctly.  I've inserted it into Preferences/Sessions, but when I re-boot the directories are not mounted.  Any further suggestions?

---

### Post by bodhi.zazen on 2008-10-20
LOL

The line in fstab can not use spaces. you need to use \040

```
//benji/Kodak**\040**Pictures  /home/TideMan/Pictures  cifs   auto,username=me,password=pwd 0 0
```

You can also put your user name and password in a file and call it with 'credentials=file'

See :

[How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131") 

(yes, there is a samba section).

Although your grammar is correct, and even funny, take care you do not bite the hand that feeds you.

---

### Post by ilrudie on 2008-10-20
Just continue using fstab except with the noauto option instead.  This allows you to shortcut a lot of the mount command and just say sudo mount <mountpoint>.  You can even give yourself permission to mount (and umount if you like) these mountpoints without requiring a password.  

If you still want to use a script to auto mount them you need to make sure its linked with a high S number (not sure how to do this in the sessions program so I just manually put the script in /etc/init.d and manualy sym link it to /etc/rc2.d) so you have all the required services started up.  Also you shouldn't need to use sudo in an init script.

---

### Post by Liviu-Theodor on 2008-10-23
I encountered a similar problem to yours, and solved it. But for me it was just the swapfile. Read [[SOLVED] Swap partition not mounted automatically]("http://ubuntuforums.org/showthread.php?p=6011607") and apply according to your configuration.

---

