---
title: "Using Parted to Partition Hard Disk"
date: 2012-05-03
forum: New to Ubuntu
---

### Post by miltreynolds on 2012-05-03
I need help understanding how to use Parted to partition a completely wiped hard disk.
 
Here's my goal: Learn to use Linux terminal by building a command-line only web server out of my old PC.
 
Here's what I've accomplished so far (pitifully little, I know!):
 
1. Wiped my old PC using Darik's Boot and Nuke Wipe Tool
 
2. Downloaded Ubuntu 12.04 Desktop iso using Filezilla on my new Windows 7 PC
 
3. Created a LiveCD by burning the iso image to a CD
 
4. Booted my new PC with the Ubuntu LiveCD
 
5. Created a USB Startup Disk
 
6. Booted my old PC with the USB Startup Disk
 
I have not installed Ubuntu on my old PC...I'm running Ubuntu as "Try Only", using the USB drive as a a LiveCD. I want to build a Linux webserver from scratch, using the terminal as much as possible.
 
But I'm stuck! Parted seems to be the program I want to use, and I can start it from the terminal, but I'm too dense to understand the command line options and commands needed to partition my blank hard disk.
 
Could someone tell me the boiler plate command to type in the terminal to at least get me going?
 
I can at least list the devices available:
 
sudo parted -l
Error: /dev/sda: unrecognized disk label
 
Model: SanDisk Cruzer (scsi)
Disk /dev/sdb: 4013MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
 
The disk I want to partition is /dev/sda. I do NOT want to partition my startup drive, /dev/sdb.
 
The Linux from Scratch Guide directs me to create at least two partitions, one for Linux, and one for swap. How do I do this from the terminal using Parted?

---

### Post by papibe on 2012-05-03
Hi miltreynolds.

My guess is there's nothing to read from /dev/sda.

Take a look at this parted [tutorial]("http://www.gnu.org/software/parted/manual/html_chapter/parted_2.html").

Although I admire your resolution to use the command line, I think it is so much easier to partition a HD using the gui version gparted.

Regards.

---

### Post by miltreynolds on 2012-05-03
Thanks, papibe!
 
During the last hour or so I've come to the same conclusion! Story of my life, idealistic-pie-in-the-sky-knights-in-shining-armor, but the pavement takes its toll on my dream! I opened GParted on the desktop, it immediately detected my unpartitioned hard disk and USB drive. With just a few clicks I'm ready to partition the drive!
 
I guess that for as few times in my life I'll do this, my best bet would be to use the GUI version, GParted. Fast and easy!
 
Thanks for the confirmation!
 
Milt

---

### Post by Bucky Ball on 2012-05-03
Just wondering why, if you're intending a web server, you downloaded the desktop ISO and not Ubuntu server? The server edition doesn't have a desktop environment, is designed for your purpose and is run from a terminal.

---

### Post by miltreynolds on 2012-05-03
Good question...it's a sign I'm not entirely sure of what I really want! I've spent the last week trying to wade through all this. I did download the latest ubuntu server iso, but my machine would not boot from the CD I created. I repeated this with several different iso files. My PC CDROM must be out of alignment or something. It ran my wipe tool CD fine, but nothing else. I decided my real goal is not merely to get a server up and running...I miss the old days of 1985-MSDOS-text-based computing...I want to end up with a machine without a GUI, requiring me to do everything from the terminal. To this end I've decided to try Linux From Scratch, hoping that it will give me experience in Linux from the ground up, allowing me to eventually build a text-only webserver.
 
I guess the short answer to your question is that I want to learn the basics of command-line Linux by working towards an actual useable machine.
 
I guess...
 
Thanks for the question!
 
Milt

---

### Post by FormatSeize on 2012-05-03
> **miltreynolds said:**
> I miss the old days of 1985-MSDOS-text-based computing...I want to end up with a machine without a GUI, requiring me to do everything from the terminal. To this end I've decided to try Linux From Scratch, hoping that it will give me experience in Linux from the ground up, allowing me to eventually build a text-only webserver.
 
I guess the short answer to your question is that I want to learn the basics of command-line Linux by working towards an actual useable machine.


In 1985, I was far too young and stupid to understand computers. That's why I didn't own my first computer until 2009 (age 27), and then I installed GNU/Linux. I have to say that Linux From Scratch can potentially teach you a huge amount of things about a wide variety of things. I've tried it four times, and was only successful once. But I still have that one successful attempt on a 40 gigs hard disk that is attached to a motherboard with 1 gig of RAM, and a Pentium 3 processor. And that one attempt, along with the ones that didn't pan out have taught me a lot more than I think I would have learned otherwise.

I admire your drive to learn such things. Especially in today's world where everyone wants things to "just work" with no effort on their own behalf.

Go for it, and good luck.

---

### Post by Bucky Ball on 2012-05-04
Hey, cool. Maybe you should try the minimal install. You install what you require only. This way you can omit a desktop environment altogether (along with anything else). You give it a list of what you want installed during the installation and it drags that off the net. All the install disk does is install a base system. You do the rest. You are looking for the mini.iso if you go that way. It is fun to do if you have the time to experiment and play ... ;)

Linux from Scratch looks kinda similar with a difference: if something breaks you might not get the level of support you would with a Ubuntu release; unaware of how vibrant their community is. ;) Looks like a good way to learn though.

---

