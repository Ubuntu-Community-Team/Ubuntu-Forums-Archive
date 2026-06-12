---
title: "64bit vs 32 bit ??"
date: 2008-04-24
forum: Recurring Discussions
---

### Post by dtrot55 on 2008-04-24
Does the 64bit Ubuntu have the same issues as some 64 bit windows users have...lack of 64bit software and driver support? I am currently using the 32bit 7.10 and going to upgrade to 8.04 and was wondering if it would be better to go 64 or 32??

I just don't want to do it if im going to hit a lot of driver issues.

---

### Post by bodhi.zazen on 2008-04-24
This is a FAQ here and my advice is if you have a 64 bit processor start with 64 bit Ubuntu.

Here is a sticky :

i86_64 : Advantages / Disadvantages : 

[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

---

### Post by bilal.17 on 2008-04-24
yes there are some software and driver issues in 64 bit , 32 bit is more likely to work

---

### Post by overdrank on 2008-04-24
> **bodhi.zazen said:**
> This is a FAQ here and my advice is if you have a 64 bit processor start with 64 bit Ubuntu.

Here is a sticky :

i86_64 : Advantages / Disadvantages : 

[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

+1 :)

---

### Post by superprash2003 on 2008-04-24
give 64bit a chance. if all works stick with it else move to 32bit

---

### Post by dtrot55 on 2008-04-24
thanks bodhi.zazen that is a really good sticky....very informative...i dont think i should have any issues i was just wondering if its any better...i have ran win xp64 and i dont really think  i saw much difference...so i didnt know if ubuntu 64 would show any promise in the performance area.

---

### Post by Paqman on 2008-04-24
You won't see a massive improvement in speed, no. But some types of tasks will definitely benefit. Plus, 64-bit is the way forward. You'll have to start using it eventually.

---

### Post by Bannor on 2008-04-24
unless they have done something in this new release to greatly increase the performance or compatibility of the 64 bit.  I would have to strongly recommend using 32 bit to start. as of Ubuntu Gutsy the 32 bit version ran more programs than the 64bit. If you want to run a none ubuntu program Murphy's law states that it will only work in 32 bit mode.  Furthermore there is no upside to 64 bit. Its not faster or less buggy. 

But I am not here to make the case for 32 bit I would like to know if anyone with, knowledge of hardy could provide some insight to a change that might make me try 64 bit again.  Is there no way to add full 32 bit compatibility to Ubuntu 64?

---

### Post by dtrot55 on 2008-04-25
yeah thats what im worried about...i go through the process of reformatting to 64 just to find out that software isn't supported...its already hard enough for me to install soem things...i dont need a unsupported issue...Although I had very little issues with Windows x64...but im new to ubuntu so i dont know how the 64 bit software has evolved for it.

---

### Post by Sef on 2008-04-25
> yeah thats what im worried about...i go through the process of reformatting to 64 just to find out that software isn't supported.

What software are you talking about?

---

### Post by Bannor on 2008-04-25
epsxe psx2 dosbox runs better on 32 bit and wine 64 bit as of gutsy wasn't in the repositories

---

### Post by dtrot55 on 2008-04-25
so is wine supported in the 64 bit? cause probably the only game i will play in ubuntu is CSS and if wine doesnt work then ill be sad

---

### Post by John.Michael.Kane on 2008-04-25
> **dtrot55 said:**
> so is wine supported in the 64 bit? cause probably the only game i will play in ubuntu is CSS and if wine doesnt work then ill be sad

Looking over the link provided by bodhi.zazen

Shows this Note: wine now has a 64bit deb available for 7.04-8.04. To install it use the command below.

First, add the repository's key to your system's list of trusted APT keys

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -

```
Next:

```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/hardy.list -O /etc/apt/sources.list.d/winehq.list
```

Then

```
sudo aptitude install wine
```

---

