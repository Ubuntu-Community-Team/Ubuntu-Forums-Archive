---
title: "Can Live CD compile C programs?"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by resander on 2008-09-03
I have not yet downloaded Live CD for latest Ubuntu.

Before I do, 

  -- does the Live CD  contain everything needed to compile
     C and C++ programs? 
  -- if not, can I download missing pieces, for
     example C++ (if that would not be included)
     and for these to be stored on the PC so I
     don't have to repeat it everytime I boot from the CD?
  -- is it likely to be very slow?
  -- has anyone tried this, or is it just likely to be 
     a loser?

I am using Windows XP Pro on a 1 GHz P4 PC with 512MB of ram.

---

### Post by Bachstelze on 2008-09-03
> **resander said:**
> 
  -- does the Live CD  contain everything needed to compile
     C and C++ programs? 


No.

> **resander said:**
>   -- if not, can I download missing pieces, for
     example C++ (if that would not be included)
     and for these to be stored on the PC so I
     don't have to repeat it everytime I boot from the CD?


You could, but it would be very bothersome, and not really worth it. Why not just install Ubuntu?

---

### Post by cmay on 2008-09-03
hi. i dont think that ubuntu has the things needed to compile c or c++ programs on the live cd. but knoppix has. if you want to compile a c or c++ program from live cd using ubuntu you have to install the build-essential package . i have many live cd whit gcc and build essentials installed but ubuntu dont have it for some reason. if i compile any programs under live cd enviroment i save them on a usb stick if i want to keep them .
hope it helps.

---

### Post by resander on 2008-09-03
Many thanks.

Your message is clear. It cannot be done, which is a pity
because a C compiler is really quite small.

I just wanted to try C to see what it is like and to
get some idea of possible problems in porting C/C++ Windows programs to the Linux/Unix world.

I was hoping not having to configure an XP & Ubuntu dual-boot, but it really looks I have to do that. I have a question about this that would be off-topic, so will ask in a new thread.

Thanks again.

---

### Post by philinux on 2008-09-03
You could try this.

[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by WRDN on 2008-09-03
The LiveCD doesn't contain the neccessary software (GCC) to compile code 'out of the box'. You would need to install the "build-essential" package before you could compile anything:

```
sudo apt-get install build-essential
```

You could also [customize the LiveCD]("https://help.ubuntu.com/community/LiveCDCustomization") to add the packages.

---

### Post by resander on 2008-09-03
Phillinux:  Many thanks!

This is great and would allow me to run Ubuntu without burning CDs and defining partitions. I think it could well be the answer to my problem.

I downloaded the LIVE CD iso (nearly 700MB), put it in the directory of the wubi.exe 'installer' and ran wubi exe which completed in a minute or so. On reboot, I was given a choice of Windows XP and Ubuntu. On selecting Ubuntu the startup screen with the bouncing Ubuntu horizontal appeared. It then changed to commandline mode and stopped at the ubuntu prompt. Don't yet know how to make it continue for another 15 minutes of installation needed for Ubuntu. Will read what I can find about it, or more likely raise a thread in the Ubuntu Wubi forum.

Again, many thanks for letting me know about Wubi.

---

