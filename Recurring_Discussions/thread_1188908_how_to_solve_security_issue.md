---
title: "how to solve security issue"
date: 2009-06-16
forum: Recurring Discussions
---

### Post by hero1900 on 2009-06-16
i heard from friend that ubuntu has a serious security issue, he said that an unauthenticated user  can access to your root account without any problem, from boot menu.
so what is this issue and how to fix it.

---

### Post by yogg on 2009-06-16
I think he means that he could start the backup system from the grub bootloader.

To solve it:
Set a password to your bootloader

-> Does not help against Live CD's
Set a password for your Bios an only let the System boot from your hard drive

-> Does not help against a Bios reset
Encrypt your entire System and use a good passphrase

-> Solved ;)

---

### Post by iponeverything on 2009-06-16
> **hero1900 said:**
> i heard from friend that ubuntu has a serious security issue, he said that an unauthenticated user  can access to your root account without any problem, from boot menu.
so what is this issue and how to fix it.

A compromise based on physical access to a machine is not a "serious security issue" for the operating system.  It is  "serious security issue" for you. If a bad guy as physical access to your machine, you have bigger issues than him stealing your cookies.

---

### Post by bodhi.zazen on 2009-06-16
> **hero1900 said:**
> i heard from friend that ubuntu has a serious security issue, he said that an unauthenticated user  can access to your root account without any problem, from boot menu.
so what is this issue and how to fix it.

Physical access is a problem.

So far the best solution is to encrypt your installation.

I now routinely encrypt my installation on my laptop.

Edit: forgot to mention, as suggested by [iponeverything]("http://ubuntuforums.org/member.php?u=643833") ,this is not a flaw in the operating system. Every computer is vulnerable if an intruder has physical access. This has nothing to do with what operating system you run.

---

### Post by bodhi.zazen on 2009-06-16
> **yogg said:**
> I think he means that he could start the backup system from the grub bootloader.

To solve it:
Set a password to your bootloader

-> Does not help against Live CD's
Set a password for your Bios an only let the System boot from your hard drive

-> Does not help against a Bios reset
Encrypt your entire System and use a good passphrase

-> Solved ;)

Those "solutions" are very superficial and are easily circumvented. Sure they will deter the casual intruder, but I would not claim them as "Solved". The problem physical access represents is a serious issue.

---

### Post by bodhi.zazen on 2009-06-16
Note: There is a flurry of similar posts in the security section recently, I am going to move some of them to recurring discussions as this topic come us from time to time.

---

### Post by aysiu on 2009-06-16
> **bodhi.zazen said:**
> Physical access is a problem.

So far the best solution is to encrypt your installation. This is also not unique to Ubuntu.

This is true for all Linux distributions. This is true for Windows. This is true for Mac OS X.

---

### Post by bodhi.zazen on 2009-06-16
> **aysiu said:**
> This is also not unique to Ubuntu.

This is true for all Linux distributions. This is true for Windows. This is true for Mac OS X.

Good point, as always.

---

### Post by CharmyBee on 2009-06-16
Strip your screws.

---

### Post by hero1900 on 2009-06-19
OK thank you all
its really clear in other threads and how you can get access to computer that is physically with you, so if i had a encrypted system and it was offline is their any way to get the information (in case of forensic procedure) or it will take time using brute force

---

### Post by Chemical Imbalance on 2009-06-19
> **aysiu said:**
> This is also not unique to Ubuntu.

This is true for all Linux distributions. This is true for Windows. This is true for Mac OS X.

+1 

No OS is safe from physical access.  
If one can get to the harddrive, you might as well say ):P

---

### Post by iponeverything on 2009-06-21
> **hero1900 said:**
> OK thank you all
its really clear in other threads and how you can get access to computer that is physically with you, so if i had a encrypted system and it was offline is their any way to get the information (in case of forensic procedure) or it will take time using brute force

If you have full disk encryption using LUKS and strong passphrase, I don't think anyone is going to get to your data for the next few years. Bar, the maybe the NSA and even then only if you have something that they really want.

---

### Post by rookcifer on 2009-06-21
> **iponeverything said:**
> If you have full disk encryption using LUKS and strong passphrase, I don't think anyone is going to get to your data for the next few years. Bar, the maybe the NSA and even then only if you have something that they really want.

NSA isn't going to be able to get it either.  AES-256 is a long way off from being successfully broken (in the cryptanalysis sense) and will never likely be broken by brute force (even with quantum computers it is no guarantee).

If anything the NSA would use some sort of side-channel attack, or perhaps find a way to compromise the machine so that the user unintentionally provides his password (i.e. keyloggers).  Or perhaps a few weeks at Gitmo might solve their problem. :)

---

### Post by bodhi.zazen on 2009-06-21
> **iponeverything said:**
> If you have full disk encryption using LUKS and strong passphrase, I don't think anyone is going to get to your data for the next few years. Bar, the maybe the NSA and even then only if you have something that they really want.

It is already possible to crack encryption.

[http://citp.princeton.edu/pub/coldboot.pdf](http://citp.princeton.edu/pub/coldboot.pdf)

All major encryption techniques have been cracked.

[http://citp.princeton.edu/memory/](http://citp.princeton.edu/memory/)

Now it is true the machine needs to be running, but still it is not something that takes years and years to crack.

---

### Post by juancarlospaco on 2009-06-21
I don't use Truecrypt and alike, 
i use SeaHorse *(rightclick--->encrypt&sign)* 
with big key and strong password, 
Ubuntu have the option *"Flush Cache"* 
on the Tray everytime you use the key, its Shred the memory,
...and no, i don't store the key on the HD, its Shreded,
i keep the key on UbuntuOne, 
i login to UbuntuOne with OnScreen keyboard,
the key is transfered to my PC over SSL connection.
I give you a memory dump on a pendrive, and you can't decrypt nothing.

*More safe than Truecrypt*
:)

---

### Post by Bachstelze on 2009-06-21
> **hero1900 said:**
> OK thank you all
its really clear in other threads and how you can get access to computer that is physically with you, so if i had a encrypted system and it was offline is their any way to get the information (in case of forensic procedure) or it will take time using brute force

Tickle you with a feather till you give them the passphrase.

Or this:

[img]http://imgs.xkcd.com/comics/security.png[/img]

---

