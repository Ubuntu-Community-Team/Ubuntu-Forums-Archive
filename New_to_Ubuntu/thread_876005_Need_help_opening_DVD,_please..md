---
title: "Need help opening DVD, please."
date: 2008-07-31
forum: New to Ubuntu
---

### Post by L Campbell on 2008-07-31
I'm running Hardy 8.04 on a desktop PC and I have a DVD which I can't get to open.  The DVD is a Spanish Tutorial, if that makes any difference.

I insert the DVD and get:-

'cdrom1 - File Browser'

VRD_MC1

Then an error message:-

"The folder contents could not be displayed".

"You do not have the permissions necessary to view the contents of “cdrom1”

I click the 'UP' button to 'media - File Browser'

Now I see 5 folders, one is cdrom1 and has a square with an X in it.

I right click > Properties and get:-

Owner : unknown
Folder access : no list, no create/delete, access

Group : unknown
Folder access : no list, no create/delete, access

Others
Folder access : None

AFAIK my machine is up to date and has all the codecs from Medibuntu.

I would appreciate it if someone could tell me what I need to do now to get this DVD to open.

TIA

---

### Post by Potatoj316 on 2008-07-31
try
```
sudo chown -R USERNAME /media/cdrom1
```

---

### Post by L Campbell on 2008-07-31
> **Potatoj316 said:**
> try
```
sudo chown -R USERNAME /media/cdrom1
```

Thanks for trying.

Unfortunately it didn't make any difference.

---

### Post by L Campbell on 2008-07-31
x

---

### Post by L Campbell on 2008-07-31
> **L Campbell said:**
> I'm running Hardy 8.04 on a desktop PC and I have a DVD which I can't get to open.  The DVD is a Spanish Tutorial, if that makes any difference.

I insert the DVD and get:-

'cdrom1 - File Browser'

VRD_MC1

Then an error message:-

"The folder contents could not be displayed".

"You do not have the permissions necessary to view the contents of “cdrom1”

I click the 'UP' button to 'media - File Browser'

Now I see 5 folders, one is cdrom1 and has a square with an X in it.

I right click > Properties and get:-

Owner : unknown
Folder access : no list, no create/delete, access

Group : unknown
Folder access : no list, no create/delete, access

Others
Folder access : None

AFAIK my machine is up to date and has all the codecs from Medibuntu.

I would appreciate it if someone could tell me what I need to do now to get this DVD to open.

TIA

Anybody want to chime in here, please?

---

### Post by bobnutfield on 2008-07-31
Post the contents of /etc/fstab

---

### Post by Growbag on 2008-07-31
Try to mount it as root.

Open a terminal and type this lot:

```
sudo su
mkdir /mnt/dvd
fdisk -l

```

That last command will give you a list of all connected devices that are recognised by Ubuntu.  Read your DVD device from there, it is usually something like /dev/sdb1 or something like that, now use that device in the following command, replacing **xx** with your device id:


```
mount /dev/sd**xx** /mnt/dvd
```

If you don't get an error message, try listing it:

```
ls -hAlF /mnt/dvd
```

You should get a list of files that are on the DVD, if you do, then it is simply an odd permissions problem.

If you got an error, maybe post the output here for further analysis.

It might be an odd DVD format, maybe even a region lock, in which case try installing libdvdcss (search in Synaptic after adding the restricted repos).

Good luck :).

---

### Post by L Campbell on 2008-07-31
> **Growbag said:**
> Try to mount it as root.

Open a terminal and type this lot:

```
sudo su
mkdir /mnt/dvd
fdisk -l

```

That last command will give you a list of all connected devices that are recognised by Ubuntu.  Read your DVD device from there, it is usually something like /dev/sdb1 or something like that, now use that device in the following command, replacing **xx** with your device id:


```
mount /dev/sd**xx** /mnt/dvd
```

If you don't get an error message, try listing it:

```
ls -hAlF /mnt/dvd
```

You should get a list of files that are on the DVD, if you do, then it is simply an odd permissions problem.

If you got an error, maybe post the output here for further analysis.

It might be an odd DVD format, maybe even a region lock, in which case try installing libdvdcss (search in Synaptic after adding the restricted repos).

Good luck :).

Thank you.

I got this part done:-

qwer@qwer-desktop:~$ sudo su
[sudo] password for qwer: 
root@qwer-desktop:/home/qwer# mkdir /mnt/dvd
root@qwer-desktop:/home/qwer# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b5496

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9352    75119908+  83  Linux
/dev/sda2            9353        9729     3028252+   5  Extended
/dev/sda5            9353        9729     3028221   82  Linux swap / Solaris
root@qwer-desktop:/home/qwer# 

I'm not sure how to do the next part.

---

### Post by Growbag on 2008-08-01
Ooops, sorry, my stupid mistake!!

I gave you the wrong command.

OK, try this in a terminal:

```
ls -hAlF /dev/ | grep dvd
```

here is mine as an example:

```
me> ls -hAlF /dev/ | grep dvd
lrwxrwxrwx  1 root root             3 2008-08-01 17:53 dvd -> sr0
lrwxrwxrwx  1 root root             3 2008-08-01 17:53 dvdrw -> sr0
```

..so my DVD drive would be /dev/sr0

So then do:

```
mount /dev/sr0 /mnt/dvd/

```

Replacing sr0 with the one you get.

---

### Post by L Campbell on 2008-08-01
> **Growbag said:**
> Ooops, sorry, my stupid mistake!!

I gave you the wrong command.

OK, try this in a terminal:

```
ls -hAlF /dev/ | grep dvd
```

here is mine as an example:

```
me> ls -hAlF /dev/ | grep dvd
lrwxrwxrwx  1 root root             3 2008-08-01 17:53 dvd -> sr0
lrwxrwxrwx  1 root root             3 2008-08-01 17:53 dvdrw -> sr0
```

..so my DVD drive would be /dev/sr0

So then do:

```
mount /dev/sr0 /mnt/dvd/

```

Replacing sr0 with the one you get.

Thanks for hanging with me here, I appreciate it.

I'm not sure what I did wrong but here's what I got:-

qwer@qwer-desktop:~$ ls -hAlF /dev/ | grep dvd
lrwxrwxrwx  1 root   root           4 2008-08-01 11:27 dvd -> scd1
qwer@qwer-desktop:~$ mount /dev/scd1 /mnt/dvd/
mount: only root can do that
qwer@qwer-desktop:~$ sudo mount /dev/scd1 /mnt/dvd/
[sudo] password for qwer: 
mount: No medium found
qwer@qwer-desktop:~$ 

Does that mean that I should have had the DVD in the machine?

---

### Post by Growbag on 2008-08-01
OK, good progress.

So your DVD drive is /dev/sr1

Put the disk in the drive and issue the same command again (you got it right).

If there WAS a disk in the drive, then I would suggest that it is a hardware problem :(.

Do you have 2 optical drives?  I ask that because your DVD drive is sr1, not sr0.

That suggests to me that your DVD drive is set as slave, and there should be a master, whether a hard disk or another optical drive.

If you have no second device, ie only 1 hard disk and 1 DVD drive, then you need to look at the jumper settings on the DVD drive.  

Make sure it is set to "master", not "slave".

If it has a "cable select" setting, and it is set to that, maybe try setting it to master as it might be the cause if the problem.

Another problem could be that you have both the hard disk AND the DVd drive attached to the same data cable.  If so, you'll have to buy (or acquire) a second IDE cable and move the DVD onto the 2nd controller (connection on the mainboard) and make sure it is the master, not slave.


Also can you try the Disk in another computer just to make sure the disk is OK?

---

### Post by L Campbell on 2008-08-01
> **Growbag said:**
> OK, good progress.

So your DVD drive is /dev/sr1

Put the disk in the drive and issue the same command again (you got it right).

If there WAS a disk in the drive, then I would suggest that it is a hardware problem :(.

Do you have 2 optical drives?  I ask that because your DVD drive is sr1, not sr0.

That suggests to me that your DVD drive is set as slave, and there should be a master, whether a hard disk or another optical drive.

If you have no second device, ie only 1 hard disk and 1 DVD drive, then you need to look at the jumper settings on the DVD drive.  

Make sure it is set to "master", not "slave".

If it has a "cable select" setting, and it is set to that, maybe try setting it to master as it might be the cause if the problem.

Another problem could be that you have both the hard disk AND the DVd drive attached to the same data cable.  If so, you'll have to buy (or acquire) a second IDE cable and move the DVD onto the 2nd controller (connection on the mainboard) and make sure it is the master, not slave.


Also can you try the Disk in another computer just to make sure the disk is OK?

Thanks again.

Not trying to be a wise guy here but when I got this:-

lrwxrwxrwx 1 root root 4 2008-08-01 11:27 dvd -> scd1

Wouldn't that mean that my DVD drive would be dev/scd1 ?

In answer to your question, my 'puter has a CD burner and a DVDrom.

It's an HP Pavilion 753n.

I tried this:-

qwer@qwer-desktop:~$ mount /dev/scd1 /mnt/dvd/
mount: only root can do that
qwer@qwer-desktop:~$ sudo mount /dev/scd1 /mnt/dvd/
[sudo] password for qwer: 
mount: block device /dev/scd1 is write-protected, mounting read-only
qwer@qwer-desktop:~$ 

Now I can not get my machine to see the DVD when I load it.

---

### Post by L Campbell on 2008-08-01
> **L Campbell said:**
> Thanks again.

Not trying to be a wise guy here but when I got this:-

lrwxrwxrwx 1 root root 4 2008-08-01 11:27 dvd -> scd1

Wouldn't that mean that my DVD drive would be dev/scd1 ?

In answer to your question, my 'puter has a CD burner and a DVDrom.

It's an HP Pavilion 753n.

I tried this:-

qwer@qwer-desktop:~$ mount /dev/scd1 /mnt/dvd/
mount: only root can do that
qwer@qwer-desktop:~$ sudo mount /dev/scd1 /mnt/dvd/
[sudo] password for qwer: 
mount: block device /dev/scd1 is write-protected, mounting read-only
qwer@qwer-desktop:~$ 

Now I can not get my machine to see the DVD when I load it.

I re-booted and can now see the DVD but it will not open and has the same error messages as when I started.

SO, it doesn't look like I'll have it working today.

Hope you have a great weekend.

---

### Post by bobnutfield on 2008-08-01
Try it like this:

> mount -t iso9660 -r /dev/scd1 /mnt/dvd

---

### Post by L Campbell on 2008-08-01
> **bobnutfield said:**
> Try it like this:

Thanks for your suggestion, Bob.

I will not be able to try it till tomorrow, as I am away from my house now.

Kind regards.

---

### Post by L Campbell on 2008-08-02
> **bobnutfield said:**
> Try it like this:

OK, I tried it but it's not quite working correctly.

qwer@qwer-desktop:~$ mount -t iso9660 -r /dev/scd1 /mnt/dvd 
mount: only root can do that
qwer@qwer-desktop:~$ sudo mount -t iso9660 -r /dev/scd1 /mnt/dvd 
[sudo] password for qwer: 
mount: No medium found

I inserted the DVD and tried again:-

qwer@qwer-desktop:~$ sudo mount -t iso9660 -r /dev/scd1 /mnt/dvd 
mount: /dev/scd1 already mounted or /mnt/dvd busy
qwer@qwer-desktop:~$ 

Am I missing something?

---

### Post by Growbag on 2008-08-02
> Not trying to be a wise guy here but when I got this:-

lrwxrwxrwx 1 root root 4 2008-08-01 11:27 dvd -> scd1

Wouldn't that mean that my DVD drive would be dev/scd1 ?


lol, you are right, I must have been tired :).

Try unmounting it first, then mount it again.

```
sudo umount /mnt/dvd
```

or

```
sudo umount /dev/scd1
```

will unmount it!

---

### Post by L Campbell on 2008-08-02
> **Growbag said:**
> lol, you are right, I must have been tired :).

Try unmounting it first, then mount it again.

```
sudo umount /mnt/dvd
```

or

```
sudo umount /dev/scd1
```

will unmount it!

Thank you.

This is what I got:-

qwer@qwer-desktop:~$ sudo umount /dev/scd1
[sudo] password for qwer: 
umount: /dev/scd1: not mounted
qwer@qwer-desktop:~$ sudo mount -t iso9660 -r /dev/scd1 /mnt/dvd 
mount: No medium found

I inserted the DVD and tried again:-

qwer@qwer-desktop:~$ sudo mount -t iso9660 -r /dev/scd1 /mnt/dvd 
mount: /dev/scd1 already mounted or /mnt/dvd busy
mount: according to mtab, /dev/scd1 is mounted on /media/cdrom1
qwer@qwer-desktop:~$ 

Does this give a clue as to what is mixed up here?

---

### Post by Growbag on 2008-08-02
You have to mount it after you insert the DVD in the drive.

1. umount
2. insert DVD disk
3. mount

If it still complains about already being mounted, then maybe the system is mounting it automatically, but to somewhere else.

Run Nautilus (the file manager if you are using Gnome) and look in the folder /media.

If you see your DVD drive or the disk in there, then it is mounting properly and you don't need to do all that mounting stuff.

---

### Post by frank002 on 2008-08-02
Maybe it's a stupid question but have you tried other DVD's? Do they play at all? If not you may need to download the libdvdcss codec. You can find it in Synaptic.

---

### Post by barkalot on 2008-08-02
Okay, first of all, you don't need '-t iso9660'. Just insert the DVD then mount it with

```
sudo mount /dev/scd1 /mnt/dvd
```

Didn't you do this some time ago and it worked? I don't see why it wouldn't work again.

---

### Post by L Campbell on 2008-08-02
> **frank002 said:**
> Maybe it's a stupid question but have you tried other DVD's? Do they play at all? If not you may need to download the libdvdcss codec. You can find it in Synaptic.

Thanks.  I have opened CD's in the DVDrom but I don't have any other DVD's.

In synaptic I have ' libdvdcss2  1.2.9-2 medibuntu4 '

---

### Post by L Campbell on 2008-08-02
> **barkalot said:**
> Okay, first of all, you don't need '-t iso9660'. Just insert the DVD then mount it with

```
sudo mount /dev/scd1 /mnt/dvd
```

Didn't you do this some time ago and it worked? I don't see why it wouldn't work again.

Thanks, I tried this:-

qwer@qwer-desktop:~$ sudo umount /dev/scd1
[sudo] password for qwer: 
umount: /dev/scd1: not mounted
qwer@qwer-desktop:~$ sudo mount /dev/scd1 /mnt/dvd
mount: block device /dev/scd1 is write-protected, mounting read-only
qwer@qwer-desktop:~$

---

### Post by barkalot on 2008-08-02
Right. So every time you want to mount your DVD or CD, you just use the mount command as you did just now. Just remember that you don't need the umount commound if a CD or DVD is not mounted already.

---

### Post by L Campbell on 2008-08-02
> **barkalot said:**
> Right. So every time you want to mount your DVD or CD, you just use the mount command as you did just now. Just remember that you don't need the umount commound if a CD or DVD is not mounted already.

OK but, I guess I should have said this, I still get the same error messages and haven't got the DVD to play.

I insert the DVD and get:-

'cdrom1 - File Browser'

VRD_MC1

Then an error message:-

"The folder contents could not be displayed".

"You do not have the permissions necessary to view the contents of “cdrom1”

I click the 'UP' button to 'media - File Browser'

Now I see 5 folders, one is cdrom1 and has a square with an X in it.

Kind regards.

---

### Post by frank002 on 2008-08-02
Do you also have libdvdread3? It is also in Synaptic.

---

### Post by L Campbell on 2008-08-03
> **frank002 said:**
> Do you also have libdvdread3? It is also in Synaptic.

Thanks.

Yes, I do have that.

Kind regards.

---

