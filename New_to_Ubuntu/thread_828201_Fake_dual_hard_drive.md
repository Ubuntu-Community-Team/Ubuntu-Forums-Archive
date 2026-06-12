---
title: "Fake dual hard drive"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by cristo-father on 2008-06-13
Can i create a fake hard drive or more in my only hard drive?
What i want from this is if i install linux in one and windows in the other
each will have their own MBR and data transfer will only be allowed with a password.
Thanks

---

### Post by blazercist on 2008-06-13
the ubuntu install cd will do it for you, its called a partition and you just have to make sure you defrag your windows really well and have a few Gigs of free space on the harddrive.

---

### Post by gr4nf on 2008-06-13
Fake HD? A partition? a VM? Any of these what you want?

---

### Post by cristo-father on 2008-06-13
> **blazercist said:**
> the ubuntu install cd will do it for you, its called a partition and you just have to make sure you defrag your windows really well and have a few Gigs of free space on the harddrive.
Will each have their own MBR?

---

### Post by cristo-father on 2008-06-13
> **gr4nf said:**
> Fake HD? A partition? a VM? Any of these what you want?
Fake HD

---

### Post by gr4nf on 2008-06-13
If they both had their own master boot record, which one would the computer boot into on startup? How would it know? Would you have a master-er boot record?

---

### Post by Gannon8 on 2008-06-13
No, they will not have their own MBR, but why would you need it if GRUB allows you to boot to both partitions?

---

### Post by cristo-father on 2008-06-13
> **gr4nf said:**
> If they both had their own master boot record, which one would the computer boot into on startup? How would it know? Would you have a master-er boot record?

linux

---

### Post by jordanmthomas on 2008-06-13
You can install GRUB to any partition.  I think I may have a setup kind of like what you're talking about.

On my first partition(s) I have Archlinux installed with GRUB installed to my disk's MBR.  
After that, I have my "distro of the week" installed.  I have an entry in my Arch's GRUB to boot off my second partition.  It looks something like this:
```
title Other distro
root (hd0,2)
chainloader +1
boot

```

Then, any time distro #2  gets swapped out, I tell its installer to install to /dev/sda3 instead of /dev/sda.  This way, I can ALWAYS get to my main install of Arch and I can always get to my second distro by using its GRUB.

Does this make any sense?  Is it at all what you're looking to do?

---

### Post by cristo-father on 2008-06-13
> **Gannon8 said:**
> No, they will not have their own MBR, but why would you need it if GRUB allows you to boot to both partitions?
Security reasons, if for example a windows virus destroys my MBR then i am pretty f*****...

---

### Post by jordanmthomas on 2008-06-13
> **cristo-father said:**
> Security reasons, if for example a windows virus destroys my MBR then i am pretty f*****...

Not really.  If your MBR gets busted it's as simple as booting off a LiveCD and putting GRUB back on.  Even the Windows XP install disc has a similar function called FIXMBR.

It'd be a nuisance, of course.

---

### Post by cristo-father on 2008-06-13
> **jordanmthomas said:**
> Not really.  If your MBR gets busted it's as simple as booting off a LiveCD and putting GRUB back on.  Even the Windows XP install disc has a similar function called FIXMBR.

It'd be a nuisance, of course.
Are you talking about the OS livecd? and if my MBR gets damaged does my data pay for it?

---

### Post by jordanmthomas on 2008-06-13
> **cristo-father said:**
> Are you talking about the OS livecd? and if my MBR gets damaged does my data pay for it?

No, if your MBR is gone, the rest of your stuff should still be there provided the virus wasn't nasty and didn't mess it up too.

---

### Post by cristo-father on 2008-06-13
> **jordanmthomas said:**
> No, if your MBR is gone, the rest of your stuff should still be there provided the virus wasn't nasty and didn't mess it up too.

Thanks for the info. I still have some questions.
1. Does the ubuntu livecd and/or linux mint have the GRUB fixing option?
2. Which should i install first,linux mint or windows(in terms of security)?
3. Is it possible to disable transfers from windows to linux?

---

### Post by jordanmthomas on 2008-06-14
> **cristo-father said:**
> Thanks for the info. I still have some questions.
1. Does the ubuntu livecd and/or linux mint have the GRUB fixing option?
2. Which should i install first,linux mint or windows(in terms of security)?
3. Is it possible to disable transfers from windows to linux?

1.  Sure, you just boot off the CD, open a terminal and run ```
sudo grub
```
You'll need to look up online how to do this as I am tired and can't explain it completely at the moment.  What I do at the grub prompt is type
```

root (hd0,0)  #tells grub this is where it should look for configuration files
setup (hd0)  #installs grub to the MBR of my first disk
exit

```
2.  Securitywise, it doesn't matter what order you install in.  However, if you're starting with a blank drive, install Windows first because it will remove grub and replace it with its own MBR.  Again, just annoying...nothing devastating
3.  To make it so windows can't write to your Linux drives, you don't have to do anything.  You have to go out of your way to be able to read ext3 (default Ubuntu filesystem type) in Windows.

---

### Post by cristo-father on 2008-06-14
> **jordanmthomas said:**
> 
3.  To make it so windows can't write to your Linux drives, you don't have to do anything.  You have to go out of your way to be able to read ext3 (default Ubuntu filesystem type) in Windows.

Can it(windows virus) erase data from my Linux partition?
If so, how can i deny that access?

---

### Post by blazercist on 2008-06-16
dude, for a virus to do even half of what you are inquiring about it would have to be the mother of all viruses written for years by a team of professional hackers specifically for your computer, your computer is not a Central Bank Mainframe or the FBI database i think you can relax

---

