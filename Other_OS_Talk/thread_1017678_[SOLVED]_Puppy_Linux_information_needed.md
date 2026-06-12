---
title: "[SOLVED] Puppy Linux information needed"
date: 2008-12-21
forum: Other OS Talk
---

### Post by som1special2 on 2008-12-21
Got a few questions about Puppy Linux. I looked on the site and couldn't find answers to these ?'s. I also joined the forum there and I await answers from it, but would like to know what my Ubuntu friends think.

1.The live CD is booted, (or copied) to ram. Should one decide to keep it, can it be placed into a HDD/SSD like normal? Or does it get installed into ram permanantly?

2.I am pretty sure Puppy uses ICEWM for a DE... Am I wrong?

3.I tried the live cd and it is o.k. in terms of comparisons to larger OS's, (ie Ubuntu like I use now), but I could not get the internet to work through the wizard.

4.I also would like to know what file systems are compatible with Puppy and what is used as default.

5.I am attempting to find a small , full function OS for a laptop that uses a 32gb SSD. I don't feel the need to have these BIG OS's when I know there are smaller OS's that use less and offer as much! Puppy seems to fit the bill, right? Or is Xubuntu the way???

6. please feel free to tell me anything else you may feel is important!

---

### Post by maybeway36 on 2008-12-21
1. The OS can be put on an HDD. What happens is that each time you load Puppy from the HDD it is loaded into RAM.

2. The main edition of Puppy uses JWM, the same window manager used by DSL.

3. Wired Ethernet connections have worked for me in Puppy, but I haven't gotten wireless to work yet.

4. I know for a frugal install (the default) Puppy can be on a FAT, NTFS or ext2/3 volume. It can also read and write these types. Not sure about reiserfs, XFS, etc.

5. Try puppy first; if that doesn't have enough, try Slax, or maybe command-line-Ubuntu and raw XFCE. Xubuntu uses a lot more RAM than regular Xfce (but still less than Ubuntu.)

---

### Post by Zimmer on 2008-12-21
1. No. RAM is only temporary... you need to boot each time using the CD but specifying the toram option (or whatever Puppy calls it)  it is a faster working option for a small OS if you have enough RAM than running from the CD.

---

### Post by som1special2 on 2008-12-21
I've definitely got enough power to run just about ANY OS, I guess I'm just being space and memory frugal. Seeing as there is no reason to run such a BIG OS I have decided to look for little space use and comparable design/options in other OS's. Thanks!

---

### Post by bumanie on 2008-12-21
1. Puppy can be installed on a hard drive as per normal, run from a live cd, where, as you say it is copied to ram. You can choose to save changes to a place on your hard drive or if burnt to a cd-rw, it will save changes there. Upon power being cut ram dumps whatever may be in it.

2. I think the desktop manager is JWM.

3. I have managed to hook internet up with ethernet, but not managed wireless as yet.

4. Default filesystem is ext3 as far as I know, what maybeway36 has said, I believe is correct for the frugal installation.

5. Puppy is very good for its size - you can run it off a usb too and it will install into ram as the live cd does. On a small laptop, I would use the usb method and you can write changes to the usb stick.

It is not the size of the SSD card that is important re choosing puppy vs. xubuntu (32gb is plenty for either), but the other specs. such as CPU and amount of ram available may dictate which one to use. Due to running from ram, puppy is lightening quick.

---

### Post by gTinker on 2008-12-21
[QUOTE=maybeway361] The OS can be put on an HDD. What happens is that each time you load Puppy from the HDD it is loaded into RAM.[/quote]

Strictly speaking this isn't correct. On a HDD install, if your kernel line includes pfix=ram it will be loaded to RAM. Without that it will use the disk too. You can use pdev= and psubdir= to specify folders.

One of the really neat ways to use Puppy is from a writeable CD, it gives you the option of saving a session, at shutdown, and the option, at boot, to choose restore of a saved session.

---

### Post by oldos2er on 2008-12-21
You might get more info if you post this on the 'Other OS Talk' subforum.

---

### Post by wolfen69 on 2008-12-21
try installing puppy to a usb thumbdrive. it doesn't have to be installed to a hard drive since it all loads into ram anyway.

---

### Post by Kevbert on 2008-12-21
Puppy can be ideally installed on a USB drive (provided your PC can boot from USB). You want to get yourself a copy of [[COLOR="Red"]unetbootin[/COLOR]]("http://sourceforge.net/projects/unetbootin/")
To install Puppy:-
1) Format your USB to FAT32 using any Partition Editor.
2) Copy iso file to desktop
3) In terminal
```
    sudo bash
    chmod +x /unetbootin-linux-304
``` (or whatever version you have to make executable).
4) Quit bash and to run, enter
  ```
./unetbootin-linux-304
```
5) With Diskimage selected, browse to iso file and select USB drive.

---

### Post by ugm6hr on 2008-12-21
Puppy 4.x uses JWM (I think 2.x used IceWM).

It is designed to be installed "frugally" rather than to HD.  This is because it uses the root user only; user files can be stored separately from the system files in a frugal install.  Running in RAM obviously makes it super-fast.

The networking wizard is pretty good - surprised you couldn't get it to work.  I haven't used it extensively since 2.14, so that may have changed.

---

### Post by smartboyathome on 2008-12-21
I use Puppy on my old laptop with a full HDD install. I don't care if its running root, its an old computer, so I don't care as much about security. I would install arch, but I don't feel like it. :p

Anyway, if you're looking for space saving, I would recommend Arch, not Puppy, since Puppy doesn't have as many up to date packages available as Arch.

---

### Post by Plumtreed on 2008-12-21
I might just point you in the direction of a very 'dynamic' OS that is small but goes well...Slitaz

Google it and try it, downloads quickly!

---

### Post by nitehawk777 on 2008-12-21
Hmmm,...(I simply MUST try Arch)...
but I run Puppy 4.1 most of the time on both my computers.  I could run other OSs,...but it's just that Puppy is much faster.  It uses JWM by default (window manager).  But you can download the "EZPup",..which will give you a nice IceWm WM. (good eye candy).

---

### Post by wolfen69 on 2008-12-21
> **Kevbert said:**
> Puppy can be ideally installed on a USB drive (provided your PC can boot from USB). You want to get yourself a copy of [[COLOR="Red"]unetbootin[/COLOR]]("http://sourceforge.net/projects/unetbootin/")
To install Puppy:-
1) Format your USB to FAT32 using any Partition Editor.
2) Copy iso file to desktop
3) In terminal
```
    sudo bash
    chmod +x /unetbootin-linux-304
``` (or whatever version you have to make executable).
4) Quit bash and to run, enter
  ```
./unetbootin-linux-304
```
5) With Diskimage selected, browse to iso file and select USB drive.

an easier way is to click the install icon on the desktop (when you're running the puppy live cd) and select usb flash drive. done. why would you go through all that other stuff? unless, of course, you like doing things the hard way. ;-)

---

### Post by spcwingo on 2008-12-21
> **Kevbert said:**
> Puppy can be ideally installed on a USB drive (provided your PC can boot from USB). You want to get yourself a copy of [[COLOR="Red"]unetbootin[/COLOR]]("http://sourceforge.net/projects/unetbootin/")
To install Puppy:-
1) Format your USB to FAT32 using any Partition Editor.
2) Copy iso file to desktop
3) In terminal
```
    sudo bash
    chmod +x /unetbootin-linux-304
``` (or whatever version you have to make executable).
4) Quit bash and to run, enter
  ```
./unetbootin-linux-304
```
5) With Diskimage selected, browse to iso file and select USB drive.

You can also boot Puppy from a USB even if it doesn't support booting from USB...let me explain.  I have an old Panasonic Toughbook that doesn't support booting from USB.  All you have to do is install Puppy via the universal installer to a FAT32 formatted flash drive.  Don't install grub.  Then use Wakepup to create a boot floppy.  It works for me because I refuse to pay almost $100 just for a HDD connector and caddy.

---

