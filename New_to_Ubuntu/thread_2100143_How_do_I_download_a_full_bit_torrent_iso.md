---
title: "How do I download a full bit torrent iso?"
date: 2012-12-31
forum: New to Ubuntu
---

### Post by raydpratt on 2012-12-31
After reading some online instructions for installing Ubuntu into Oracle's Virtual Box, I went to the Ubuntu website and tried to download the Ubuntu 12.10 desktop 386 iso bit torrent using the opera web browser (built-in bit torrent downloader).

What I got was about 30 little kilobytes that downloaded immediately, but it doesn't seem to do or start anything when I try to run it or open it.

I later downloaded Ubuntu 12.10 in full, but I don't think it was the iso, and I ended up installing it as dual boot OS, but it got buggy fast (I think it is because of my Logitech wireless optical mouse), and so I deleted the OS.

I tried going back to the Ubuntu site to download a 12.04 LTS 386 iso bit torrent, but I saw right away that its file size is only 27 KB (tiny), so I know that there is something that I do not understand or that there is a problem.

How should I get the full Ubuntu 12.04 desktop 386 iso bit torrent downloaded as an iso?

---

### Post by mamamia88 on 2012-12-31
> **raydpratt said:**
> After reading some online instructions for installing Ubuntu into Oracle's Virtual Box, I went to the Ubuntu website and tried to download the Ubuntu 12.10 desktop 386 iso bit torrent using the opera web browser (built-in bit torrent downloader).

What I got was about 30 little kilobytes that downloaded immediately, but it doesn't seem to do or start anything when I try to run it or open it.

I later downloaded Ubuntu 12.10 in full, but I don't think it was the iso, and I ended up installing it as dual boot OS, but it got buggy fast (I think it is because of my Logitech wireless optical mouse), and so I deleted the OS.

I tried going back to the Ubuntu site to download a 12.04 LTS 386 iso bit torrent, but I saw right away that its file size is only 27 KB (tiny), so I know that there is something that I do not understand or that there is a problem.

How should I get the full Ubuntu 12.04 desktop 386 iso bit torrent downloaded as an iso?
you probably downloaded just the .torrent file which is a file that you need to run in a torrent client to get the actual content of the .torrent

---

### Post by pqwoerituytrueiwoq on 2012-12-31
open the .torrent file with transmission (ubuntu/debian) or utorrent (windows)

---

### Post by andrew.46 on 2013-01-01
> **mamamia88 said:**
> you probably downloaded just the .torrent file which is a file that you need to run in a torrent client to get the actual content of the .torrent

Mind you Opera has its own torrent client built in apparently:

[http://help.opera.com/Windows/9.00/en/bittorrent.html](http://help.opera.com/Windows/9.00/en/bittorrent.html)

I have no experience with this, might be worth installing Opera to have a look.

---

### Post by raydpratt on 2013-01-01
Thank you, your comments made me look deeper at torrent downloads, and I got as far as learning from google searches that I would have to alter my port numbers, and that's where I gave up on torrents.

However, I also learned that the jZip file that I downloaded earlier is actually an iso file, but the name shows up as a jZip file until I choose to burn it as an image with the default Windows program.  Apparently, zip and iso files are similar enough that a program like jZip will give it a wrong ending, even though it will correctly pass an MD5sum check with the false jZip ending (I downloaded and used an MD5sum checker).

I also learned that to get the burned disk to boot at start-up, that I would have to change my boot order choices in BIOS to start with the cd/dvd rom drive. I got the instructions for getting into my BIOS from my computer manufacturer's website for my machine.

However, when I try to install, I get a working version going, but it doesn't appear as a dual boot choice on restart.  The instructions before the restart clearly tell me to take out the disk.

This has been a good learning experience, and I have been doing it to get closer to the working environment and tools that I need for a free online course to learn programming in C.  

However, I'm behind in the class, and time is precious, so I may have to live with the Windows gcc compiler and editor that I have.  If anyone has any thoughts, I'll check back later. But, again, thank you.

---

### Post by mysteriousdarren on 2013-01-11
I would just use Deluge or Transmission for the ease of use. Some provide more functionality, but I would always use encryption to stop prying eyes.

---

### Post by zombifier25 on 2013-01-11
> **raydpratt said:**
> Thank you, your comments made me look deeper at torrent downloads, and I got as far as learning from google searches that I would have to alter my port numbers, and that's where I gave up on torrents.

?
Why would you even need to "alter the port number"? Downloading a torrent is as simple as launching a torrent program, point the program to the downloaded torrent file, and sit back and wait.

For your dual-boot problems, I would suggest you create a new thread.

---

