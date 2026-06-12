---
title: "cannot load /home after moving it to new partition"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Unstuck on 2008-05-25
I recently moved /home to a new partition, but now when I try to log in to Ubuntu I get a message saying that /home cannot be found and then it asks me if I want to log in as root.

The files seemed to survive the transfer--I can access them when using the Live CD--but I'm not sure how to get to them when logging in with my regular username.

I checked fstab for the partition that holds Ubuntu (but not /home) and the file is completely blank.

If at all helpful, here is a copy of the fstab backup.
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=eba5c894-af8d-4b42-b740-63213e7ea081 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=a89341e8-72c0-4406-b302-0be1fd051499 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Raccoon1400 on 2008-05-25
How did you move home to a new partition?
Post the output of

cd /

then

dir

---

### Post by robertchahine on 2008-05-25
what's the name of the new partition?

---

### Post by Unstuck on 2008-05-25
I moved the /home partition using [this]("http://www.psychocats.net/ubuntu/separatehome") psychocats how-to.

dir ouptut: 
> ubuntu@ubuntu:~$ cd /
ubuntu@ubuntu:/$ dir
bin   cdrom  etc   initrd      lib    mnt  proc  root  srv  tmp  var
boot  dev    home  initrd.img  media  opt  rofs  sbin  sys  usr  vmlinuz


The name of the new partition is /dev/sda3

---

### Post by sisco311 on 2008-05-25
Add this line to the fstab:
> /dev/sda3     /home           ext3    defaults        0       2

---

### Post by Unstuck on 2008-05-25
Does it matter where I put it?

Any idea why fstab is blank?  I think that's very strange.

---

### Post by robertchahine on 2008-05-25
> **Unstuck said:**
> Does it matter where I put it?

Any idea why fstab is blank?  I think that's very strange.

don't think so

---

### Post by sisco311 on 2008-05-25
> **Unstuck said:**
> Does it matter where I put it?
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=eba5c894-af8d-4b42-b740-63213e7ea081 /               ext3    defaults,errors=remount-ro 0       1[B]
# /dev/sda3
/dev/sda3     /home           ext3    defaults        0       2 			 		[/B] 
# /dev/sda5
UUID=a89341e8-72c0-4406-b302-0be1fd051499 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0 			 		 	 	  		                   		  		  		 		 			
The # /dev/sda3 line is just a comment.

> Any idea why fstab is blank?  I think that's very strange.You need to open fstab as super-user.
Press Alt+F2 and type:
```
gksu gedit
```File menu -> Open ...

---

### Post by bodhi.zazen on 2008-05-25
The most common reasons why /etc/fstab opens a blank file are:

1. Wrong path. ie nano fstab rather then nano /etc/fstab

2. You did not edit the file as root, ie ```
sudo nano /etc/fstab
```

Or

```
gksu gedit /etc/fstab
```

The entry for home should be :

```
/dev/sda3 /home auto nodev,nosuid 0 2
```

---

### Post by Unstuck on 2008-05-25
Edited fstab using > # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=eba5c894-af8d-4b42-b740-63213e7ea081 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda3
/dev/sda3 /home ext3 defaults 0 2
# /dev/sda5
UUID=a89341e8-72c0-4406-b302-0be1fd051499 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0  

then 

> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=eba5c894-af8d-4b42-b740-63213e7ea081 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda3
/dev/sda3 /home auto nodev,nosuid 0 2
# /dev/sda5
UUID=a89341e8-72c0-4406-b302-0be1fd051499 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0 

...neither had success.  This is the message I get when I try to log in
> User's $HOME/.dmrc file is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  User's $HOME directory must be owned by user and not writeable by other users.

---

### Post by sisco311 on 2008-05-25
Press Ctrl+Alt+F2 and log in.
Restore the permissions on your home folder:
```
sudo chown -R $USERNAME\: $HOME
chmod 0750 ~
chmod 0644 ~/.dmrc
```Press Ctrl+Alt+F7 and try to log in.

---

### Post by baddnady23 on 2008-05-25
Don't know if this thread will help, but i did the same thing a few weeks ago and got great support from the comunity.  [Click on this thread]("http://ubuntuforums.org/showthread.php?t=783743") it really steered me in the right direction and now everything works flawlessly  :-)

---

### Post by Unstuck on 2008-05-25
I got this reply after entering the first chown command
> chown: cannot acess /home/ubuntu/.gvfs': Permission denied

I think that when I enter $matt it is pointing me to the Live session, is this correct?  If it is, then I think I need to enter the entire path to the username's directory in /home on sda3?  I tried this and got the following reply
> chown: invalid spec: 'media/disk-1/matt'

I appreciate the advice everyone is giving me; thank you so much.

---

### Post by lswest on 2008-05-25
for chown, either leave it as $USERNAME or else give in "matt" (without the quotes).

---

### Post by sisco311 on 2008-05-25
> **Unstuck said:**
> I got this reply after entering the first chown command


I think that when I enter $matt it is pointing me to the Live session, is this correct?  If it is, then I think I need to enter the entire path to the username's directory in /home on sda3?  I tried this and got the following reply


I appreciate the advice everyone is giving me; thank you so much.

DELETED

Try to reboot your computer and select Recovery Mode from the Grub menu.
When the computer first starts up, you have a few seconds to push esc to go into GRUB.

When the command prompt appears, issue the commands(in hardy select the ??*root shell*?? from the menu):
```
chown -R matt:matt /home/matt[FONT=monospace]
[/FONT]chmod 0750 /home/matt[FONT=monospace]
[/FONT]chmod 0644 /home/matt/.dmrc
```To reboot type:
```
reboot
```In Hardy don't reboot just type *exit* and select the ??*normal boot*?? option from the menu

EDIT: and don't worry about the *chown: cannot acess /home/matt/.gvfs': Permission denied*                      error.

---

### Post by Unstuck on 2008-05-25
> **sisco311 said:**
> DELETED

Try to reboot your computer and select Recovery Mode from the Grub menu.
When the computer first starts up, you have a few seconds to push esc to go into GRUB.

When the command prompt appears, issue the commands(in hardy select the ??*root shell*?? from the menu):
```
chown -R matt:matt /home/matt[FONT=monospace]
[/FONT]chmod 0750 /home/matt[FONT=monospace]
[/FONT]chmod 0644 /home/matt/.dmrc
```To reboot type:
```
reboot
```In Hardy don't reboot just type *exit* and select the ??*normal boot*?? option from the menu

EDIT: and don't worry about the *chown: cannot acess /home/matt/.gvfs': Permission denied*                      error.

It worked!  But now the internet connection is gone...:confused:

Thank you for your help!

---

