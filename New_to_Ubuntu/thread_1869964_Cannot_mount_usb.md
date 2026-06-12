---
title: "Cannot mount usb"
date: 2011-10-26
forum: New to Ubuntu
---

### Post by beew on 2011-10-26
I have installed Lubuntu 11.04 in a friend's older machine and am currently doing some testings.

When I plug in an usb drive or external drive it shows up on the left panel of the file manager but somehow I can't mount them by clicking, or more exactly, there is no guarantee, sometimes it works, sometimes it doesn't . 

I have a multiple partition external drive, when I plug it in all the partitions show up on the left panel on the file manager, but most of them wont mount most of the time except for a ntfs partition (the rest are all ext4). 

Now I have installed Compiz and I am wondering if it has anything to do with allowing Compiz to manage the desktop (The computer is old, but with Lubuntu it is light enough to run Compiz on top and still lighting fast, OOTB Lubuntu is just too ugly :))

P.S Also short cuts like alt+f2, ctr+alt+t don't work.

---

### Post by ajgreeny on 2011-10-26
I think installing compiz will have stopped those keyboard shortcuts from working, and you may need to change settings with CCSM to get them going again.

Even in gnome the Alt+F2 shortcut will not work if compiz is the WM, unless you set the shortcut in the Gnome Compatibility.  Unfortunately I don't know how you do the same in LXDE, but you could try setting those in the Command tab of that plugin, if it is present, and see if it works.

I also have a problem sometimes with mounting usb flash drives on an old laptop, but mine is definitely a hardware problem as the drives are not recognised at all by the system; even dmesg does not respond in any way.  I think your problem is the ext4 filesystem needing appropriate permissions to mount the partition as user;  I expect you can mount them as root if you try.  If you label those ext4 partitions with tune2fs commands ```
sudo tune2fs -L <labelname> /dev/sdx#
```they will always mount to /media/*label*, with those labels as the folder name and you can then set ownership as needed for those folders with ```
sudo chown user:user /media/label
``` and permissions if you need to with ```
sudo chmod 7xx /media/label
```choosing the 7xx as you want.  The deafult for /home in Ubuntu is 755, so that may be the most appropriate for that folder as well.

---

### Post by beew on 2011-10-26
It is not a hardware problem, it boots from usb. Also, I can mount usb on the same machine automatically with Ubuntu (also 11.04).

---

### Post by amjjawad on 2011-10-26
Need to do some search and see what's the problem in your case :)

---

### Post by beew on 2011-10-26
Thanks, my friend. :)

---

### Post by Rex Bouwense on 2011-10-26
Those guys are supposed to mount automatically.  Are you saying that they are showing up in the left hand column and are not mounted or some are not showing up in the left hand column?  By the way, what kind of machine did you install Lubuntu 11.04.

---

### Post by beew on 2011-10-26
> **Rex Bouwense said:**
> Those guys are supposed to mount automatically.  Are you saying that they are showing up in the left hand column and are not mounted or some are not showing up in the left hand column?  By the way, what kind of machine did you install Lubuntu 11.04.

Yes, they show up on the left panel if you open a file folder but they don't mount automatically. To mount them you right click and if mounted you will see a little black triangle on the mounted partition/drive as well as the content in the file folder. The problem is that right clicking doesn't mount the usb/partition, at least not consistently. 

It is an old hp laptop, as I said I have no problem mounting anything using Ubuntu and it can boot off usbs so I doubt that it is a hardware issue.

---

### Post by amjjawad on 2011-10-26
[IMG]http://i54.tinypic.com/dgl99f.jpg[/IMG]


PCManFM > Edit > Preferences 

Check these settings, please!

---

### Post by amjjawad on 2011-10-26
> **beew said:**
> Thanks, my friend. :)

You most welcome :)

By the way, next time, PM me the link of your thread ;)

---

### Post by beew on 2011-10-26
Hi,

Those boxes were already checked. :(

---

