---
title: "Not running right on my netbook."
date: 2012-06-18
forum: New to Ubuntu
---

### Post by williamwhite on 2012-06-18
I have an acer aspire one 522 with 2gb ram and the latest lubuntu does not boot properly. It either shows the lubuntu logo with the dots below it and then a blank screen or it only shows half of the screen the bottom half being occupied by either the dots from the start up screen or the command line thing from recovery mode.

---

### Post by Hadaka on 2012-06-18
Are you getting any error messages?

---

### Post by williamwhite on 2012-06-18
No error messages pop up but a black screen with some text pops up for fraction of a second after the start up page. I couldn't tell you what it said.

---

### Post by williamwhite on 2012-06-19
I fixed it sort off. I have to start it in recovery mode then login then log out then login again and sometimes I have to log in twice because a second login screen pops up wirh a computer with a flame in front of it.

---

### Post by mikewhatever on 2012-06-19
Judging by the symptoms, it looks like you have Intel's infamous GMA500 inside. Verify that by ruuning **lspci | grep VGA**. If correct, check out the wiki:[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

---

### Post by williamwhite on 2012-07-02
> **mikewhatever said:**
> Judging by the symptoms, it looks like you have Intel's infamous GMA500 inside. Verify that by ruuning **lspci | grep VGA**. If correct, check out the wiki:[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

so how do i know if i have a GMA500. I put that into the termiinal and got this 

"william@ubuntu:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)"

The computer monitor with the flame is something I did. It hasn't happened since unless I shut the netbook which is what I wanted it to do.

---

### Post by mikewhatever on 2012-07-04
Intel's gma500 has been codenamed Poulsbo, and you definitely have it.

---

### Post by williamwhite on 2012-07-05
so can i do anything to fix it

edit: I ran "sudo service lightdm restart" and it works, once. Is there a way I can permanently add that to the boot thing, so that it automatically does it every boot up

---

### Post by bodhi.zazen on 2012-07-06
> **williamwhite said:**
> so can i do anything to fix it

edit: I ran "sudo service lightdm restart" and it works, once. Is there a way I can permanently add that to the boot thing, so that it automatically does it every boot up

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#Option_1_-_console.3Dtty1](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo#Option_1_-_console.3Dtty1)

Or, better IMO, install a newer kernel

[http://packages.qa.dev.stgraber.org/qatracker/milestones/223/builds/16265/downloads](http://packages.qa.dev.stgraber.org/qatracker/milestones/223/builds/16265/downloads)

---

### Post by williamwhite on 2012-08-19
I installed the new kernel and it does not work at all just a black screen. Have to boot twice and then choose old versions and choose the old one. Also after looking for a battery and ram for it i found it was a aspire one za3/751h if that changes anything.

---

