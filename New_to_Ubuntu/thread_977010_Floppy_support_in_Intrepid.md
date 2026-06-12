---
title: "Floppy support in Intrepid"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by kansasnoob on 2008-11-09
I've been using Intrepid on a test drive since Alpha 6 but hadn't even noticed the lack of Floppy support until today. I needed to burn a new Super Grub Floppy because I'd loaned mine out.

Anyway, right now I have two Intrepid's on this test drive. One is a fresh install, the other is an upgrade from 8.04. The upgrade still has floppy support, while the fresh install does not.

Now, I can see the difference in /etc/fstab between the two, but I'm unsure if that's the only thing I'd have to change:confused:

Clear as mud:)

Learning is fun!

---

### Post by Dr Small on 2008-11-09
Do you still have /dev/floppy?
Maybe you need to:
```
sudo modprobe floppy
```

---

### Post by Kellemora on 2008-11-09
Hi KN

Floppies were not really supported in Hardy either!

Although they worked and you could format a single default size, the normal code to format a disk was completely absent.

You could only write to one formatted in msDOS, not in EXT2.

So far, I've had to go back to Mickey$oft in order to, format floppies (not supported in Ubuntu), change the laser printers toner cartridges (not supported in Linux), print 2 up and 4 up documents (not supported in Linux), print on glossy paper which requires a slower path through the fuser (not supported in Linux), Scan documents on one of the most popular scanners ever built (not supported in Linux), hit some web sites using Firefox on Windows because the plug-ins either don't work or are not available for Linux or Ubuntu.  Keep WinDOZE for back office accounting, due to no decent accounting program available for Linux, etc. etc. etc.....

That might sound like I'm knocking Linux!
Actually I'm not!
Considering the SHORT time Ubuntu has been around, it has far excelled any other Distro, including Mickey$oft at 2 to 4 times their experience at the same point in time.

When manufacturers WAKE UP and see the LIGHT, Ubuntu will surely put Mickey$oft to rest in short order.

But not if they keep downgrading what services are included in the Ubuntu package rather than enhancing those services and making them better.  

TTUL
Gary

---

### Post by kansasnoob on 2008-11-09
> **Dr Small said:**
> Do you still have /dev/floppy?
Maybe you need to:
```
sudo modprobe floppy
```

OK, I tried that and it works, but I must do it every time.

Of course this is kind of a ridiculous problem. The need for a floppy drive is almost non-existent now.

It's just one of those "things"!

---

### Post by Dr Small on 2008-11-09
> **kansasnoob said:**
> OK, I tried that and it works, but I must do it every time.

Of course this is kind of a ridiculous problem. The need for a floppy drive is almost non-existent now.

It's just one of those "things"!
There's a way to get it to load at bootup, but I am having a difficult time finding it. From reading from search engines, they say try reading the man page for 'modprobe.conf'. It might be helpful. But on Arch, this is a simple feat... Meerly add it to the Modules list in /etc/rc.conf

Dr Small

---

### Post by kansasnoob on 2008-11-09
> **Kellemora said:**
> Hi KN

Floppies were not really supported in Hardy either!

Although they worked and you could format a single default size, the normal code to format a disk was completely absent.

You could only write to one formatted in msDOS, not in EXT2.

So far, I've had to go back to Mickey$oft in order to, format floppies (not supported in Ubuntu), change the laser printers toner cartridges (not supported in Linux), print 2 up and 4 up documents (not supported in Linux), print on glossy paper which requires a slower path through the fuser (not supported in Linux), Scan documents on one of the most popular scanners ever built (not supported in Linux), hit some web sites using Firefox on Windows because the plug-ins either don't work or are not available for Linux or Ubuntu.  Keep WinDOZE for back office accounting, due to no decent accounting program available for Linux, etc. etc. etc.....

That might sound like I'm knocking Linux!
Actually I'm not!
Considering the SHORT time Ubuntu has been around, it has far excelled any other Distro, including Mickey$oft at 2 to 4 times their experience at the same point in time.

When manufacturers WAKE UP and see the LIGHT, Ubuntu will surely put Mickey$oft to rest in short order.

But not if they keep downgrading what services are included in the Ubuntu package rather than enhancing those services and making them better.  

TTUL
Gary

I have nothing left on floppy that I can try to read. It's a dead technology for the most part, but I rebuilt about 20 computers using VIA PC2500E motherboards and various spare parts, and I didn't have enough spare parts (or money) to put decent CD drives in all of them.

I only know that I was able to burn a SuperGrubDisk in an 8.10 OS that was upgraded from 8.04 but not in a freshly installed 8.10!

I'm just trying to figure out exactly what files I need to modify to make one like the other.

I'll bet I can figure it out!

---

### Post by kansasnoob on 2008-11-09
> **Dr Small said:**
> There's a way to get it to load at bootup, but I am having a difficult time finding it. From reading from search engines, they say try reading the man page for 'modprobe.conf'. It might be helpful. But on Arch, this is a simple feat... Meerly add it to the Modules list in /etc/rc.conf

Dr Small

That's cool! As I said it works as well as I want it to in a 8.04 to 8.10 upgrade. Just not in a 8.10 fresh install.

I'll just play a bit! The beauty of playing around is you always learn something!

---

### Post by glennric on 2008-11-09
To get the floppy to load when you boot add the line "floppy" to the file /etc/modules.

---

### Post by fromgi on 2008-11-11
Thank you glennric!  Worked perfectly!!  Most every other thread said there is no easy way... you proved them wrong!!!

---

### Post by kansasnoob on 2008-11-15
> **glennric said:**
> To get the floppy to load when you boot add the line "floppy" to the file /etc/modules.

Awesome! That gives me just what I needed!

As I said it's a seldom used thing, but it's nice to know it works when wanted. Many thanks!

---

### Post by AndrewWalker on 2009-01-20
I'm still having trouble. I get this
sudo modprobe floppy
FATAL: Error inserting floppy (/lib/modules/2.6.27-11-generic/kernel/drivers/block/floppy.ko): No such device

although the floppy disk is accessable and appears in device notifier!

Anyone know how the floppy disk can be working if the module isn't?

---

### Post by Nadrek on 2009-03-01
I would note that while a physical floppy may be mostly dead, a virtual floppy is not.

On my whitebox VMWare ESXi server, given that I want to keep the networking locked down extremely tightly, a virtual floppy transferred through the VMWare datastore browser is my #1 way of moving around small files (like certificates and encryption keys).

---

### Post by CEB2nd on 2009-03-27
FWIW, I noticed that floppies are automatically supported in the beta version of 9.04. =D>

---

