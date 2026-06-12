---
title: "64-bit Install of Intrepid (8.10) - Not working"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by BassKozz on 2008-10-30
I am on a Dell e1505 laptop w/ a T2500 Intel Core Duo Proc w/ 4GB of ram.
I tried installing Intrepid (8.10) 64-bit, but when I boot to the CD it says I don't have a 64bit CPU...

Isn't a T2500 64-bit?
-BassKozz

EDIT: Nevermind: [http://ark.intel.com/cpu.aspx?groupID=27236](http://ark.intel.com/cpu.aspx?groupID=27236)

---

### Post by phidia on 2008-10-30
Standard questions: Are you using the release candidate or the final, Have you checked the md5sum and the cd for integrity?

I saw your edit too late :) I thought all core duos were 64 bit but apparently not!

---

### Post by Idefix82 on 2008-10-30
I am afraid, the Intel Core Duo are all 32 bit. The Intel core 2 Duo are 64 bit.

Edit: see for example here: [http://www.cpu-world.com/CPUs/Core_Duo/Intel-Core%20Duo%20T2500%20LE80539GF0412M.html]("http://www.cpu-world.com/CPUs/Core_Duo/Intel-Core%20Duo%20T2500%20LE80539GF0412M.html")

---

### Post by BassKozz on 2008-10-30
> **phidia said:**
> A core duo is 64 bit. It's sort of hard to find a recently made computer that isn't.

Not true: [http://ark.intel.com/cpu.aspx?groupID=27236](http://ark.intel.com/cpu.aspx?groupID=27236)

---

### Post by roger_1960 on 2008-10-30
Hi

Core 2 processors are 64 bit.

Core duo are not, so you have the wrong install CD!

See [http://answers.yahoo.com/question/index?qid=20080202203553AAlZCBk](http://answers.yahoo.com/question/index?qid=20080202203553AAlZCBk)

---

### Post by phidia on 2008-10-30
> **BassKozz said:**
> Not true: [http://ark.intel.com/cpu.aspx?groupID=27236](http://ark.intel.com/cpu.aspx?groupID=27236)

Intel's cpu naming scheme isn't easy to keep track of.:lolflag:

---

### Post by LowSky on 2008-10-30
Should have called the Core ships Pentium 5, core 2 Pentium 6, Core i7 Pentium 7. People whould  understand the chip names better

---

### Post by RedneckNerd on 2008-10-30
google didn't bing up any 64 bit answers.  Usually when its 64 bit they advertise the fact, even though most people don't use it.  Also I think the inspirons only come in 64 bit with AMD.

Just intalled 8.10 and I'm going to try the 64 bit on my 1526 later.  
Seeing that you are useing 64 bit on another system what are the advantages?

---

### Post by RedneckNerd on 2008-10-30
Wow I'm slow.

---

### Post by Laibcoms on 2008-10-30
Intel Core Duo have 32-bit and 64-bit.
Intel Core **2** Duo are *only* 64-bit, or to be exact x86-64 (not really a true or pure 64-bit)

---

### Post by phidia on 2008-10-30
> **Laibcoms said:**
> Intel Core Duo have 32-bit and 64-bit.
Intel Core **2** Duo are *only* 64-bit, or to be exact x86-64 (not really a true or pure 64-bit)

What do you mean by that and do you have any links to back up that assertion?

AFAIK x86_64 is a label used by developers and software providers.
ie x86 is a processor type that runs a specific code type (contrasted to processors like older apple types but including others too that use a different code type) the _64 means it is capable of 64 bit.

This  > (not really a true or pure 64-bit) does not make any sense to me so if you can explain and back that up with a link I'd be grateful.

---

### Post by BassKozz on 2008-10-30
> **RedneckNerd said:**
> Just intalled 8.10 and I'm going to try the 64 bit on my 1526 later.  
Seeing that you are useing 64 bit on another system what are the advantages?

4GB of ram gets put to use, FULLY ;)
32-bit OS only supports 3GB~3.5GB of ram :(

**_EDIT_**
I stand corrected, after a couple of crafty google searches ;)
I found this: [http://en.wikipedia.org/wiki/Physical_Address_Extension#Linux](http://en.wikipedia.org/wiki/Physical_Address_Extension#Linux)
> **Linux**

The Linux kernel includes full PAE support starting with version 2.6,[7] enabling access of up to 64 GB of memory on 32-bit machines. A PAE-enabled Linux-kernel requires that the CPU also support PAE. As of 2008, many common Linux distributions come with a PAE-enabled kernel as the distribution-specific default.

So apparently you don't need a 64-bit OS to see all the RAM ?
Now to find out if my T2500 supports PAE? I assume Ubuntu does too?

**_EDIT 2_**
Maybe Ubuntu doesn't support PAE: [http://brainstorm.ubuntu.com/idea/1553/](http://brainstorm.ubuntu.com/idea/1553/)

---

