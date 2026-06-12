---
title: "Mplayer and repositories"
date: 2005-02-23
forum: Repositories &amp; Backports
---

### Post by caiphn on 2005-02-23
Hi, I noticed in the user startup guide it says to click off the other two repositories in synaptic, which I have done (for some reason I have six, but they're all pointing to a ubuntu url) I have them all checked and have reloaded, marked for upgrades, done all that. Afterwards, I try to install mplayer, but it's missing a bunch of libraries.

I guess I posted this in this forum as I was questioning the amount I had, I thought I was only supposed to have two-three, and only one was supposed to be set by default.

mplayer:
 Depends: libggi2 but it is not going to be installed
  Depends: libpng10-0 but 1.0.15-6ubuntu1 is to be installed
  Depends: libsdl1.2debian but 1.2.7-7 is to be insta

----- edit ----

well, no one has responded so what I'll try doing is just googling for these and downloading them.. what directory would I want to download them to? Or does it matter?

---

### Post by Blaze1024 on 2005-03-01
[QUOTE=caiphn]Hi, I noticed in the user startup guide it says to click off the other two repositories in synaptic, which I have done (for some reason I have six, but they're all pointing to a ubuntu url) I have them all checked and have reloaded, marked for upgrades, done all that. Afterwards, I try to install mplayer, but it's missing a bunch of libraries.

I guess I posted this in this forum as I was questioning the amount I had, I thought I was only supposed to have two-three, and only one was supposed to be set by default.

mplayer:
 Depends: libggi2 but it is not going to be installed
  Depends: libpng10-0 but 1.0.15-6ubuntu1 is to be installed
  Depends: libsdl1.2debian but 1.2.7-7 is to be insta


  
----- edit ----

well, no one has responded so what I'll try doing is just googling for these and downloading them.. what directory would I want to download them to? Or does it matter?[/QUOTE]

I had the same problem earlier today and solved it using the info in the link at the bottom of the page.  If you follow this “how to” you wont have much trouble. You do need to compile the source code for Mplayer. Its really not that hard. The sound of it intimidated me a bit as I have only been using Linux for about 4 days. I started trying to compile Mplayers yesterday And I received all sorts of errors on Development files for the cpp compiler. No mater what I tried I could not get them installed. then I ran into this “how to” and it almost got every thing working except one stubborn development  package. I ended up updating the this package with a newer version I just backspaces over the version number and apt-get automatically installed the version that matched the runtime library's  I already had installed.

Try and get the latest version of Mplayer and just update the names of the files he uses in the “how to” 

I think this is the latest “ mplayer_1.0pre6-2_i386.tar.bz2”
also update the codecs  “essential-20050216.tar.bz2”

this is a great Media player it has both a command line version and a GUI version The command line player is fantastic both the GUI and command line versions will play in  fast forward and slow down to under 10% it will do frame by frame and you can even rotate the video. it even has an encoder so you can encode or transcode you videos.  I've been a MS DOS user from way back, long before Windows was around . MS really started to lose me when Windows 95 was release. I was even a BETA tester for 95. When XP came out I was completely frustrated with the product. Windows is a fine product as long as you don't mind periodic system crashes, Lockups and all sorts of memory leak problems. not to mention having to constantly patch the system with there security updates and hot fixes, I feel bad for the people that don't have broad band (I'm lucky as I have a 10 Megabit symmetrical Internet, connection via fiberoptic I downloaded the entire ubuntu ISO in less then 4 or 5 min) contrary to Windows where I think I spent more time patching up the OS and trying to get things to work right then I ever did just using the dam thing   Linux has breathed new life into computers for me, I wish I would have done it years ago..

any how sorry for the rant :-({|=  heres the link and have fun         
[http://www.ubuntuforums.org/showthread.php?t=94](http://www.ubuntuforums.org/showthread.php?t=94)

Blaze1024

---

### Post by caiphn on 2005-03-04
Hey, thanks for the reply! I'll check it out, hopefully all goes well.

---

