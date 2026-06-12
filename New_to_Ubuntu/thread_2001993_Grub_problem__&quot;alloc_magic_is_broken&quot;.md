---
title: "Grub problem:  &quot;alloc magic is broken&quot;"
date: 2012-06-11
forum: New to Ubuntu
---

### Post by diablo75 on 2012-06-11
I have an ASUS X54C that client has asked me to take a look at.

When I turn the system on I get the following message:

> alloc magic is broken at 0xbae15eb0
Aborted.  Press any key to exit.

I am able to access the grub menu itself by holding shift, but choosing any entry from the list produces the same message.  The only other thing that I can do is access the grub's command prompt by pressing 'c'.  Any way to repair this from the command line?

---

### Post by wilee-nilee on 2012-06-11
Post the bootscript run this command set it will be in home as the results.txt use a live cd, and wrap it in codetags.

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript
```The chroot below may work, I have never seen this error before but the web does show some hits, I would look at google a bit before doing anything myself.

---

### Post by carl4926 on 2012-06-11
Use a Live CD
chroot in to the installed system
run synaptic, fix broken packages
then update grub

---

### Post by diablo75 on 2012-06-12
> **carl4926 said:**
> Use a Live CD
chroot in to the installed system
run synaptic, fix broken packages
then update grub

When you say "chroot into the installed system" could you tell me exactly what that means/how to do that please?  This is a unique first for me I think.

---

### Post by carl4926 on 2012-06-12
You CD must be the same Arch as install ie; 64  or 32 bit

```
* Open a terminal and type

$ sudo fdisk -l

    * Now, you need to remember which device listed is your linux distribution, for reference, /dev/sda1 will be used. Now we need to mount the filesystem to /mnt

$ sudo mount /dev/sda1 /mnt

    * Now mount the rest of your devices

$ sudo mount --bind /dev /mnt/dev

    * Now chroot into your system

$ sudo chroot /mnt
```

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by wilee-nilee on 2012-06-12
> **carl4926 said:**
> You CD must be the same Arch as install ie; 64  or 32 bit

```
* Open a terminal and type

$ sudo fdisk -l

    * Now, you need to remember which device listed is your linux distribution, for reference, /dev/sda1 will be used. Now we need to mount the filesystem to /mnt

$ sudo mount /dev/sda1 /mnt

    * Now mount the rest of your devices

$ sudo mount --bind /dev /mnt/dev

    * Now chroot into your system

$ sudo chroot /mnt
```[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

Here is the chroot I use generally.
[https://help.ubuntu.com/community/Grub2/Installing#ChRoot](https://help.ubuntu.com/community/Grub2/Installing#ChRoot)

This is what it looks like.
```
sudo mount /dev/sdXX /mnt
``````
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
``````
sudo chroot /mnt
```
Work done here then.
```
Exit chroot: CTRL-D on keyboard
``` 
```
sudo reboot
``` 
Just passing the info on.

---

### Post by diablo75 on 2012-06-12
I think I figured out the problem with this laptop.  I booted into the RAM testing utility from a Live CD and discovered that the RAM is faulty.  But here's the kicker.  This laptop's factory RAM is built into the motherboard and is non-removable.  Yet another reason I'll never buy a laptop from Asus...  Thanks for your help everybody.  Sorry for the goose chase.

---

