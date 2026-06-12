---
title: "Low disk space error when Trial-run of 12.04 from CD"
date: 2012-12-28
forum: New to Ubuntu
---

### Post by burkeaw on 2012-12-28
Hi,
trying out Ubuntu for first time on a 2.2G machine with 65G showing free on C: ( according to W7). 

I can get as far as using the desktop and connecting wirelessly but then get messages such as ".. only 32M of disk space".

Any ideas please?
Thanks, Tony

---

### Post by rrich1974 on 2012-12-28
if i get it right: are you telling me that you run ubuntu inside windows.....that is a bad idea. 
just insert the disk in the drive and boot from DVD. choose "try ubuntu" 
never use ubuntu inside windows.

---

### Post by chubble10 on 2012-12-28
If you're booting directly from the live CD, then low storage errors mean that you don't have enough RAM to run the live CD correctly.
(Everything is loaded into RAM instead of the hard drive when using the try Ubuntu option, hence the free space reported in Windows doesn't match what is available to the live CD.)

You can check how much RAM you have by clicking the gear in the top right corner, and choosing 'About this Computer'.

---

### Post by audiomick on 2012-12-28
> **burkeaw said:**
> Hi,
trying out Ubuntu for first time

Exactly how are you trying Ubuntu? That error message sounds like one I got when using "try Ubuntu" from a USB stick with persistance. You have installed wireless drivers, by the sound of it. The message would be referring to the amount of space left on the USB stick in the "persistance" storage.

As you can see from the varied answers you have already recieved, the first thing is to tell us exactly how you are "trying Ubuntu".

It as, I believe, a sure bet that the error message is not referring to the hard drive on the computer.

---

### Post by burkeaw on 2012-12-30
Hi,
please see the requested info/clarifications below.

I am booting from the CD and then using the "try ubuntu" option on the CD.
I didn't install any wireless drivers ( only entered my wi-fi key)
When I check using "About computer" in Ubuntu, it reports  "Disk 987Mbyte, Memory 1.8 Gbyte"

Thanks for your help,
Tony

---

### Post by squakie on 2012-12-30
It will be available memory as mentioned by chubble10.  The "Try Ubuntu" option runs off the CD but uses, in Windows/Dos terms, a ramdisk - memory is reserved as a pseudo disk drive.  How Much - I don't know as I've never checked it.  I've only used "Try Ubuntu" when I have a problem with an install and need to try somethings from the command line to debug it.

---

