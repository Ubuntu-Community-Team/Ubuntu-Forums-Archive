---
title: "Ubuntu 11.10 64 bit questions concerning running Wine &amp; VirtualBox"
date: 2012-03-09
forum: New to Ubuntu
---

### Post by s1baker on 2012-03-09
Hi,
I am thinking about buying a new box and I want to put 11.10 64 bit
on it.  ( I am currently running Ubuntu 10.10 Meerkat, 32 bit )
So, I have some questions:

1) I noticed on the Ubuntu download page ([http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)) that the recommended version is 32 bit. So is the 64 bit stable?

2) How long is the support for 11.10 64 bit, specifically, is it LTS?

3) Can VirtualBox run under 11.10 64 bit, and if it can, will I be able to run my Windows XP (32 bit) under it and run 32 bit programs?

4) Will Wine run under 11.10 64 bit? I have some old programs that I now run using Wine and would like to do the same with the 11.10 64 bit.

Thanks all

---

### Post by sudodus on 2012-03-09
> **s1baker said:**
> Hi,
I am thinking about buying a new box and I want to put 11.10 64 bit
on it.  ( I am currently running Ubuntu 10.10 Meerkat, 32 bit )
So, I have some questions:

1) I noticed on the Ubuntu download page ([http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)) that the recommended version is 32 bit. So is the 64 bit stable?

Yes.
> 
2) How long is the support for 11.10 64 bit, specifically, is it LTS?

18 months (until April 2013), not LTS, but the next version 12.04 due to be released in April will have 5 years LTS.
> 
3) Can VirtualBox run under 11.10 64 bit, and if it can, will I be able to run my Windows XP (32 bit) under it and run 32 bit programs?

I think so, but others can give a definite answer.
> 
4) Will Wine run under 11.10 64 bit? I have some old programs that I now run using Wine and would like to do the same with the 11.10 64 bit.

Thanks all
I don't know about the fourth question.

---

### Post by jerome1232 on 2012-03-09
> **s1baker said:**
> 
3) Can VirtualBox run under 11.10 64 bit, and if it can, will I be able to run my Windows XP (32 bit) under it and run 32 bit programs?

Yes

> **s1baker said:**
> 
4) Will Wine run under 11.10 64 bit? I have some old programs that I now run using Wine and would like to do the same with the 11.10 64 bit.

Thanks all

Yes,Wine runs fine under Ubuntu 64bit however Wine will only run 32 bit windows executables, not 64 bit windows executables.

---

### Post by kikotiger on 2012-03-09
Hello,
1) The reason Ubuntu 32-bit is recommended is in case you don't know what processor type you have (32 or 64-bit). 32-bit software should run on 32 and 64-bit hardware. But you cannot run a 64-bit software on a 32-bit hardware. 32 and 64-bit are both stable.


3) VirtualBox can run on either 32 and 64-bit. If you have a 64-bit hardware and Ubuntu 64-bit you can run 32 and 64-bit on VirtualBox, I'm not sure if you can run 64-bit OS in VirtualBox if it is installed on Ubuntu 32-bit. 

I have been using 64-bit for years and I have no problems running XP 32-bit on VirtualBox.

---

### Post by forrestcupp on 2012-03-09
> **s1baker said:**
> 
1) I noticed on the Ubuntu download page ([http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)) that the recommended version is 32 bit. So is the 64 bit stable?There is actually a bug report that has been filed for a long time where a bunch of people are trying to get them to change the wording on that because it's confusing to people. Like kikotiger said, some people don't know if they have a 64-bit processor or not, and 32-bit will work on either. A long time ago, 32-bit used to be a lot more usable with a lot less headaches, but that hasn't been the case for a long time.

> **s1baker said:**
> 3) Can VirtualBox run under 11.10 64 bit, and if it can, will I be able to run my Windows XP (32 bit) under it and run 32 bit programs?That will work fine, but don't expect it to be good at running resource heavy games or anything like that. And as for Wine, I use it every day in Ubuntu 11.10 64-bit to run MS Office 2007 and other 32-bit apps.

Just so you know, you usually can run any 32-bit app in a 64-bit OS. It just doesn't work the other way around.

---

