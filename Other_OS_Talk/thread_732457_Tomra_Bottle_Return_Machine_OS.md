---
title: "Tomra Bottle Return Machine OS"
date: 2008-03-22
forum: Other OS Talk
---

### Post by pezmanlou on 2008-03-22
I found a printout from a tomra bottle machine and it appears to be running some variant of linux or something similar.  I was wondering if anybody could help me extrapolate more information from this printout, especially what operating system it is running.

The printout starts out by giving numbers of different errors it had received, times the bins have been changed, bottles that have been returned, and other statistics.  Near the bottom it lists some files with paths to them.

These are the exact names (I rechecked them and they are all spelled this way on the printout, even though tomla seems like it should be tomra)

//rfs/boot.ini
//wpram/etc/load.ini
//WPRAM/MCB/MCB.INI
//wpram/tomla/default.ttl

It also shows some or all of what is in the files.  This is everything it says about the files.

//rfs/boot.ini

[console]
baudrate=9600
handshake=i
modeminit1=AT~n~p~pATE0Q1
modeminit2=ATB0&B1&H1&R2
EnableInit=1


//wpram/etc/load.ini (appears to be empty)

//WPRAM/MCB/MCB.INI

[Version]
Program=1.9.0X - 991006 (8)
MCB=3
MAB=2
Program2= 1.9.0X - 991006
                                           (6)
MCB2=3
MAB2=X

[Configuration]
Raiser=1
RightSort=1
Transport=2
LeftSort=0
Hoist1=0
Hoist2=0

[TOMRA_PHOTOCELL]
RAISER=96
Use_Tomra_Cells=1
RIGHTHATCH=97
LEFTHATCH=104


//wpram/tomla/default.ttl
default.tlb

DISPLAY.TLB



Then it gives some serial numbers and board versions and also lists some software and its version.  This is a list of the software and what I have found on it.

DrvLib (something to do with windows nt?)
ImgLib (found applications on both windows and linux)
VCBLib  (visualization cookbook library)
BCLib (something to do with big numbers)
TomlaRun (nothing)
Lxndr (somebody uses this as a username, I don't believe that is relevent)
BootProg (bootloader for fat12/16 filesystems)
BootDriv (a dos program for storing the boot drive letter in an environment variable)

Any information on this would be appreciated and interesting.

---

### Post by abzman2000 on 2008-06-01
people, this is interesting! does anyone have any other ideas or info?

---

### Post by cardinals_fan on 2008-06-01
wpram: model for scalable and portable computing

---

