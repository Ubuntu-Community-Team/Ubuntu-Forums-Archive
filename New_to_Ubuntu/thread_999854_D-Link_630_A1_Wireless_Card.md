---
title: "D-Link 630 A1 Wireless Card"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by wheelerrver on 2008-12-02
I am a real n00b - a few days ago I installed Ubuntu 8.10 (Intrepid Ibex) on my laptop.  I have solved most of my problems, but my D-Link wifi card does not work completely.  It lights up and shows the available networks, it even shows it connects with them, but then no network.  I checked the other posts regarding the D-Link 630, found several of them  One appeared to have solved this problem in the Dapper version of Ubuntu using a procedure shown for the D-Link 650 which has the same chipset.  That post is quoted below.

I have two problems:  

First, I cannot make the link to the download work.  This post was from 2006, so web page has probably moved. Anyone know where?

Second, the instructions given are simple, but I need to know _exactly_ what steps I need to take in Intrepid to do what it says.  How do I replace something like this?



*the post said:* 

Yay fixed.  Will just post my method here in case someone needs reference.

I downloaded
[http://195.66.192.167/linux/acx_patc...34/tiacx111c16](http://195.66.192.167/linux/acx_patc...34/tiacx111c16)
and replaced the one in /lib/firmware/2.6.15-18-386/acx/2.3.1.31 (after backing it up, just in case). Eject the card, and plug it back it, done! It's odd why the Dapper-bundled firmware didn't work though... does this qualify as a bug?

How would I go about replacing something like this.

Oh, I should mention, I am easily able to get on line with my Verizon wireless card, so the problem appears to lie with the card somewhere.

---

### Post by wheelerrver on 2008-12-02
I found the download through [http://acx100.erley.org/fw/acx111_1.2.1.34/](http://acx100.erley.org/fw/acx111_1.2.1.34/)
So I just need to know what to do now.  Or, is this the right approach in Intrepid.

---

