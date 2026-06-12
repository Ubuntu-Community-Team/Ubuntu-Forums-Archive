---
title: "External HD Compatible?"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by RussW210 on 2008-11-21
I just bout this external hard drive:

[http://www.lacie.com/us/products/product.htm?pid=11016](http://www.lacie.com/us/products/product.htm?pid=11016)

Lacie Neil Poulton USB 2.0 1TB External HD.  Anyone think I will have a problem with it being compatible with Linux Ubuntu 8.10?

---

### Post by ECPCLINUX on 2008-11-21
Hello, Very nice looking USB external hard drive. I checked it out and I believe it will work. I have a ZDISC by Cintre and it works, However, the LaCie ‘1-Click’ Backup Software most likely won't work in Ubuntu. At least in my Cintre 1-Button Instant Backup software for PC does not work. The software for your new external is made for PC Windows and Mac.  Hope this helps.

---

### Post by bscbrit on 2008-11-21
I don't think you will have any problem.  Just plug it in and everything should 'just work', with the exception of the provided utility programs - they will be windows and MacOS specific and of no use to you as linux programs.  In other words, you will have a 1TB external hard drive - it will probably NOT do automatic backups or any of the other promises that are made on the the web page that you linked to.

It is also probably formatted for windows, usually with NTFS but perhaps FAT32.  Linux can read/write to this quite happily nowadays but you will not be able to save your linux file permissions on the NTFS formatted drive - windows simply doesn't understand (nor support) the concept of linux file permissions.  Your data will be safe but you could not make an identical copy of a directory on the drive which maintained the appropriate linux file and directory permissions.

If you are **only** going to use the external drive with a linux computer then I would consider reformatting it to something that is linux specific.  If you need to use the drive on both linux and windows than leave it as it is.  However, what you have now will usually work as a storage device.

---

### Post by RussW210 on 2008-11-21
Great, appreciate the advice!  My friend bout the Lacie d2 Quadra and I loved his.  Wasn't quite willing to spend as much money for his but ever since he got it I have been doing quite a bit of research and Lacie seems to be very well known for their long-lasting durable hard drives.  Needless to say, when I found that Neil Poulton hard drive for $123 all-in on Buy.com I was ecstatic (more than $25 less than Newegg.com!)

Looking forward to setting it up.

As for the software, I was aware that it probably wouldn't run and that wasn't a non-selling point for me.  I am using my HD basically for movie and music transfers.

Just looked up the ZDISC, very nice enclosure.  Like how it stands up and supports 1-button backup as well.  My Lacie won't stand up but it is small enough to not be a problem face down.

---

### Post by RussW210 on 2008-11-21
Thanks bscbrit.  When my friend brought his Lacie d2 Quadra over the other day it worked fine.  Though we had permission problems because of the playing around with he did with it on his Mac Computer.  For some reason he could transfer files from my HD to his but I couldn't take any of his to my internal HD.

When I upgraded from 8.04 to 8.10 my current (not Lacie) hard drive stopped working.  It won't be recognized by the computer anymore.  Go figures.  It works fine on my Windows Laptop.

So I'm most likely just going to leave my Lacie connected to my Linux computer and keep my other 250gb external HD with my laptop (and its tiny 32gb internal hard drive).

---

### Post by ECPCLINUX on 2008-11-21
Cool, I first used my Zdisc and used the 1- Button Instant Backup Windows XP and liked it. But the novelty wore off pretty quickly,lol at least for me. So, even when I was using it with Windows I stopped using the 1-button Backup. Now I just connect it to Ubuntu since, I use that computer much more. I share it in my network with the rest of the computers in my home and it's all good for me and my wife.

---

### Post by RussW210 on 2008-11-21
I still have to set up a network.  For basic transfers between my Windows Laptop and Ubuntu Desktop I have been using WinSCP and Putty but the transfers are a little slow.

1-button-backup sounds nice.  But for me I only really need to save my media folders (music, pictures, movies, work documents).  That is as easy as dragging a folder over every few weeks and not overwriting everything currently on the external.

---

### Post by bscbrit on 2008-11-21
I don't know your level of computer expertise, but the task of keeping your external hard drive with a backup of your selected files is a simple script using, say, rsync.  You could easily make it run once a day or whenever you boot up and thus automatically keep your hard drive up-to-date.

Look at 'man rsync' for more details but don't be frightened off if it looks like gibberish.  The basic command that you need is:

```
rsync -var /files/that/you/want/to/back/up /where/you/want/to/back/them/up/to/
```

The -var options simply make the command 'verbose' (i.e. tell you what is happening as it happens), 'archived' (i.e. they keep the same file permissions that the files have now) and 'recursive' (i.e. it will replicate a complete directory structure rather than just the files in the specified directory).  Make some dummy data and have a play with it. One advantage of rsync is that the first time it copies all the files, and subsequently it only copies changes to the data that has been previously copied, making the whole think much quicker than you might imagine.

---

