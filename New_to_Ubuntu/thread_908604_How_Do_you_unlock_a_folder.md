---
title: "How Do you unlock a folder???"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by suomalainen on 2008-09-02
Ubunteros!


I have a few folders stored on a USB flash drive. See attached picture.

I don't know how this happened but all the folders have a "lock" placed on themselves and I cannot edit any of the documents in the folder. I can only view.

Any suggestions on how to remove the lock would be appreciated as I need to edit documents residing within these folders.

Thank YOU!!!!!!

---

### Post by keplerspeed on 2008-09-02
There may be a way to do this by 'clicking' but you can atleast edit these files using vi or gedit (if you have them intslled) by using this command:

sudo gedit /media/nameofusbdrive

The reason that these files are locked is that they are owned by root, for whatever reason, if they were created when logged in as root for example. So by giving the command sudo you should be able to have editing rights to these files.

> You should also use the "chown" command to change the owner of the file(s).
To do this, use the command:

Code:

sudo chown -R [username] [directory]



[http://ubuntuforums.org/showthread.php?t=883985](http://ubuntuforums.org/showthread.php?t=883985)

Here they use the chown command to change file ownership. I havnt used it, but It does appear to work.

---

### Post by t0p on 2008-09-02
1. Press **Alt+F2**

2. In the run box, type **gksudo nautilus**

3. Use the file manager window that opens to navigate to the folders in question

4. Right-click on the folders and go to **Properties**

5. Change the properties so you have write permissions

---

### Post by suomalainen on 2008-09-02
Thanks but I really need to get the "lock" removed as I move the USB flash drive over multiple operating systems.

---

### Post by halitech on 2008-09-02
> **suomalainen said:**
> Ubunteros!


I have a few folders stored on a USB flash drive. See attached picture.

I don't know how this happened but all the folders have a "lock" placed on themselves and I cannot edit any of the documents in the folder. I can only view.

Any suggestions on how to remove the lock would be appreciated as I need to edit documents residing within these folders.

Thank YOU!!!!!!

did you originally create the files/folders on another system or in Windows? if you right click one of the files and go to properties, then go to Permissions, who is the owner showing up as?

---

### Post by halitech on 2008-09-02
> **suomalainen said:**
> Thanks but I really need to get the "lock" removed as I move the USB flash drive over multiple operating systems.

if you create a file or folder in windows, it will have the lock on it.

---

### Post by t0p on 2008-09-02
**suomalainen** - if you used a different operating system to save the folders to the stick, you will have the lock icon on them.  That's the way it is (and the way it should be - your username didn't save them, so your username doesn't own them).  But you can copy them to ubuntu then follow my instructions above to unlock them on your ubuntu system.

---

### Post by suomalainen on 2008-09-02
Thanks for the suggestions.

1. As per the "alt=f2" suggestion, I did this but was unable to navigate to the USB flash drive. For some reason it wasn't showing up.

2. As regards owner. I'm correctly listed as the owner.

3. I have created doc's in both Ubuntu and XP. This is the first time a lock has prevented me from editing my material.

Any other suggestions? I need to get rid of this hinderance.

---

### Post by t0p on 2008-09-02
> **suomalainen said:**
> Thanks for the suggestions.

1. As per the "alt=f2" suggestion, I did this but was unable to navigate to the USB flash drive. For some reason it wasn't showing up.

2. As regards owner. I'm correctly listed as the owner.

3. I have created doc's in both Ubuntu and XP. This is the first time a lock has prevented me from editing my material.

Any other suggestions? I need to get rid of this hinderance.

Copy them to ubuntu.  Follow my instructions.  Edit them.  Save them to the stick.

---

### Post by suomalainen on 2008-09-02
Real sorry but your advice isn't working..... Don't worry I'm doing exactly as per your instructions....

Again I must stress and state.... I have been doing things this way for months! This means creating folders on the stick and putting documents created in both XP and ubuntu into the folders. And then editing the same docs in either xp or Ubuntu.

TODAY is the first day that I have been prevented from opening and editing the folders......

You can believe me if you like or not but this is how it's been working for me.

---

### Post by t0p on 2008-09-02
Exactly how is my advice not working?  What errors are you having?

---

### Post by unutbu on 2008-09-02
Please open a terminal ([http://www.psychocats.net/ubuntu/terminal](http://www.psychocats.net/ubuntu/terminal)) and type
```
chmod -R 777 /media/disk/EURES
```
Is /media/disk/EURES the correct path? You might have to change it if it isn't.

Unlike Alt-F2, if you do this in a terminal, you'll get to see any error messages. Please report back any error messages you see. If there are no error messages, see if the locks are gone.

---

### Post by suomalainen on 2008-09-02
Unutbu, Your advice did indeed remove the locks!!! See attached picture.

However, I still cannot edit the files inside the folders.

Here is the output I got from using your command:

paavo@paavo-desktop:~$ chmod -R 777 /media/disk/EURES
chmod: changing permissions of `/media/disk/EURES/EURES.doc': Read-only file system
chmod: changing permissions of `/media/disk/EURES/&#9576;&#9575;\021&#945;í&#9618;\032ß': Read-only file system
chmod: changing permissions of `/media/disk/EURES/\006': Read-only file system
chmod: changing permissions of `/media/disk/EURES/\001': Read-only file system
chmod: changing permissions of `/media/disk/EURES/&#9532;.\v': Read-only file system
chmod: changing permissions of `/media/disk/EURES/\021.\023': Read-only file system
chmod: changing permissions of `/media/disk/EURES/\031.\033': Read-only file system
chmod: changing permissions of `/media/disk/EURES/!.#': Read-only file system
chmod: changing permissions of `/media/disk/EURES/).+': Read-only file system
chmod: changing permissions of `/media/disk/EURES/1.3': Read-only file system
chmod: changing permissions of `/media/disk/EURES/9.;': Read-only file system
chmod: changing permissions of `/media/disk/EURES/A.C': Read-only file system
chmod: changing permissions of `/media/disk/EURES/i.K': Read-only file system
chmod: changing permissions of `/media/disk/EURES/Q.s': Read-only file system
chmod: changing permissions of `/media/disk/EURES/y.[': Read-only file system
chmod: changing permissions of `/media/disk/EURES/a.c': Read-only file system
chmod: changing permissions of `/media/disk/EURES/i.k': Read-only file system
chmod: changing permissions of `/media/disk/EURES/q.s': Read-only file system
chmod: changing permissions of `/media/disk/EURES/y.{': Read-only file system
chmod: changing permissions of `/media/disk/EURES/r': Read-only file system
chmod: changing permissions of `/media/disk/EURES/\t.\v': Read-only file system
chmod: changing permissions of `/media/disk/EURES/\021.\023': Read-only file system
chmod: changing permissions of `/media/disk/EURES/\031.\033': Read-only file system
chmod: changing permissions of `/media/disk/EURES/!.#': Read-only file system
chmod: changing permissions of `/media/disk/EURES/).+': Read-only file system
chmod: changing permissions of `/media/disk/EURES/1.3': Read-only file system
chmod: changing permissions of `/media/disk/EURES/9.;': Read-only file system
chmod: changing permissions of `/media/disk/EURES/A.C': Read-only file system
chmod: changing permissions of `/media/disk/EURES/i.K': Read-only file system
chmod: changing permissions of `/media/disk/EURES/\001': Read-only file system
chmod: changing permissions of `/media/disk/EURES/\022.[': Read-only file system
chmod: changing permissions of `/media/disk/EURES/\a.a': Read-only file system
chmod: changing permissions of `/media/disk/EURES/$\0017$\0015$\001.3$\001': Read-only file system
chmod: cannot access `/media/disk/EURES/h\t\004sh\t\004k.H\001': Input/output error
chmod: changing permissions of `/media/disk/EURES/H ': Read-only file system
chmod: changing permissions of `/media/disk/EURES/d.r': Read-only file system
chmod: changing permissions of `/media/disk/EURES/t.a': Read-only file system
chmod: changing permissions of `/media/disk/EURES/a.S': Read-only file system
chmod: changing permissions of `/media/disk/EURES/i.r': Read-only file system
chmod: changing permissions of `/media/disk/EURES/W.s': Read-only file system
chmod: changing permissions of `/media/disk/EURES/d.r': Read-only file system
chmod: changing permissions of `/media/disk/EURES/&#8805; !\001L.\036': Read-only file system
chmod: changing permissions of `/media/disk/EURES/t.a': Read-only file system
chmod: changing permissions of `/media/disk/EURES/t': Read-only file system
chmod: changing permissions of `/media/disk/EURES/r': Read-only file system
chmod: changing permissions of `/media/disk/EURES/*\001F.R\001F': Read-only file system
chmod: changing permissions of `/media/disk/EURES/\r.\024ñx': Read-only file system
chmod: changing permissions of `/media/disk/EURES/\a.\034': Read-only file system
chmod: changing permissions of `/media/disk/EURES/.y': Read-only file system
chmod: changing permissions of `/media/disk/EURES/b\001(.l': Read-only file system
chmod: changing permissions of `/media/disk/EURES/^j\b.\001': Read-only file system
chmod: changing permissions of `/media/disk/EURES/d.\005': Read-only file system
chmod: changing permissions of `/media/disk/EURES/\002\020': Read-only file system
chmod: changing permissions of `/media/disk/EURES/\006É\001': Read-only file system
chmod: changing permissions of `/media/disk/EURES/\001': Read-only file system
paavo@paavo-desktop:~$

---

### Post by brentoboy on 2008-09-02
your memory stick is mounted as read only (hence the "read only file system" complaint in your output.)

do you know if the stick is formatted with a fat32 file system or an ntfs file system?

ntfs has a tendancy to "decide" to mount read only if there are any problems with the disk. (such as a "dirty" file system - one that wasnt properly closed before it was unplugged)

try plugging it back in to the windows xp box, and then "safely remove" it with that stupid icon in the system tray.  then try it.  if that doenst help, there are other things we can do, but that is by far the easiest place to start.

---

### Post by suomalainen on 2008-09-02
The file system is vfat. I'll try your suggestion and report back in a minute or two.

---

### Post by suomalainen on 2008-09-02
brentoboy,

Followed your instructions but to no avail!

Also, now the "lock"  icon is back on the folders again.

---

### Post by brentoboy on 2008-09-02
gedit /etc/fstab

and post the contents of the file.

---

### Post by suomalainen on 2008-09-02
Here you go!

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=89acc0eb-3282-4830-a73e-800131a8c83c /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=faf634c1-2bcd-4fd4-8ec6-cd35c3208dbc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by brentoboy on 2008-09-02
unmount it (by right clicking the icon on the desktop) but dont unplug it.

then, open a terminal and mount it manually like so:

sudo mount -o rw -t vfat /dev/?  /media/disk/EURES

the /dev/? needs to be the device name of the usb drive.  I'm not exactly sure what it should be, and I dont know off hand how to find out (not at a linux box right now)

but the -o rw tells it to mount it up in a read write fashion.

Wish I had more to work with - I was hoping your /etc/fstab might have an entry for the usb drive, but it didnt.

if you have this problem repeatedly and end up wanting it to auto-mount corretly, we will need to add a line to the fstab file and tell it what options you want to have automagically applied when you pop that drive in.

---

### Post by halitech on 2008-09-02
hopefully this will help some, before unmounting it, in the terminal do
```
sudo fdisk -l
``` as this will tell us where it is mounting as well as give us the disk identifier (not sure if we may need it or not).

then unmount it and follow Brentoboys instructions

---

### Post by suomalainen on 2008-09-02
All,

After a few "back-and forth" operations between XP and Ubuntu my usb flash drive all of a sudden started to operate correctly. I could even edit files within folders.

However, I did realize the following and not sure if it relates to the problem I was having or not. I had forgotten that I had a DVD in my DVD player. After having re-booted ubuntu numerous times with a dvd in the player, I never saw a DVD icon on the desktop. BUT, when my USB flash drive started to work so too did I realize the DVD icon on the desk top...

Thanks for all your help!!!!!

---

