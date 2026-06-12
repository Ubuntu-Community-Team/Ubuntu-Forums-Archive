---
title: "Recover/restore formated ntfs partition/MS files using GNU soft . HOWTO to follow"
date: 2007-01-14
forum: Outdated Tutorials &amp; Tips
---

### Post by john_spiral on 2007-01-14
Hi,

I stupidly formatted a ntfs (Windows 2000) drive on a machine without making a backup of the contents! 

Yes that was stupid!!!

I'm hoping to make a small HOWTO detailing how to recover files from a formated NTFS partition using only GNU (free) software.

I'll expand this HOWTO using our shared hands on experience.

Detailed below, I've used [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec") as a low level file recovery tool. I would love to hear from others out there who have had sucess with other GNU tools. 

I've thus far manged to recover lost files from the partition but I'm getting character encoding errors when attempting to open the recovered document in MS Word. Any ideas how I could reset/fix this? Can this be done within MS Word?

Before I solve my own problem I'll share what I've done thus far.

Partial Solution:

I've booted the trashed machine with a [[COLOR="Blue"]Knoppix[/COLOR] ]("http://www.knoppix.net/") ver 5.1 LiveCD and a 4GB USB memory stick attached to the USB port of the machine. 

Once inside Knoppix I've mounted & enabled the write access on the USB memory stick through two right clicks on the USB key icon:

 ->mount

right click again on the USB key icon

Actions -> Change Read/Write Mode.

Agree to the changes. 

The key is now mounted and has write access (root only). 
The USB key will act as a storage place for all the lovely recovered files.

Next I bring up the Terminal (Small screen with a >_) this gives me access to the PhotoRec application which I'll use to scan the disk for lost files.

To run Photorec and to store files on the USB key you will need to have root access. Type the below command in the Terminal to gain root access:

**sudo su**

your prompt should look like the below:

root@0[knoppix]#

Next change to the directory  where the software lives:

**cd /KNOPPIX/usr/sbin/**

next run PhotoRec with the below command (you must be root throughout the process):

**./photorec**

Please refer to the below page for the operation of the software:

[http://www.beginnerspc.com/articles.cfm?articleid=1869&page=6](http://www.beginnerspc.com/articles.cfm?articleid=1869&page=6)

Come back to me if you have any suggestions & improvements.

Johne

---

### Post by john_spiral on 2007-01-18
I keep running out of disk space on an eternal 40gig hard drive when I'm attempting to recover a 30gig hard drive's files. The solution I've come up with is to narrow down the filetype search, just to say .jpg or ms office docs.

---

