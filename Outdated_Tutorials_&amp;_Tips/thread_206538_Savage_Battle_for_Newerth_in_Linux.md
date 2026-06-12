---
title: "Savage: Battle for Newerth in Linux"
date: 2006-06-30
forum: Outdated Tutorials &amp; Tips
---

### Post by gotmonkey on 2006-06-30
The game is a little older, but it has a native linux install. Here is what I did to install the game in linux and get it running.

Running Savage 2.00c Retail in Ubuntu Linux 6.06 gnome

Note: I am terrible at extracting archives in console, so I created a super user launcher on my desktop to make things a little easier for myself and others like me. 


1. download patches
	2.00b: [http://www.dragonsvalley.com/savage/patch/savage_patch_200b.tar.gz](http://www.dragonsvalley.com/savage/patch/savage_patch_200b.tar.gz) 
	2.00C: [http://www.dragonsvalley.com/savage/patch/savage_patch_200b_to_200c.tar.gz](http://www.dragonsvalley.com/savage/patch/savage_patch_200b_to_200c.tar.gz)
	SEP2C: [http://www.notforidiots.com/SEP-2C/SEP-2C.tar.gz](http://www.notforidiots.com/SEP-2C/SEP-2C.tar.gz)

2. Install libtgk 1.2 in package manager

3. Install libtiff (1.3 or higher) in package manager

4. Create Root Nautilis launcher on desktop (this just makes things easier to move around)
	launcher command gksudo nautilus

5. install game
	Open console and cd to /media/cdrom
	verify directory list $ls -la
	sudo sh INSTALL.linux
	after install, don't bother launching game
6. Install patches
	open root nautilus from launcher on desktop
	navigate to directory that the patches are in
	open the patch archives and extract them to /home/'user'/games/Savage in order of list above

7. Symlink libtiff
	in root nautilus, navigate to /usr/lib
	right click on libtiff.so.4.0.4 and click make link
	copy created link
	in root nautilus, navigate to /home/'user'/games/Savage
	paste symlink and rename to libtiff.so.3

8. Create Desktop Launcher
	copy icon.xpm icon from cdrom to desktop
	in console $sudo mv icon.xpm /usr/share/pixmaps/
	right click on desktop, create launcher
	command line gksudo /home/'user'/savage
	choose icon
	"ok"

9. Launch program
	If program does not launch.
	open console and run $sudo /home/'user'/savage
	take note of "import error"

Enjoy!

---

### Post by walkerx on 2006-07-09
I've got the savage install cd's and for linux its stored on the bonus cd, but nowhere can i find the INSTALL.Linux file you mention, even in reading the included textfile for linux it only tells you to copy the files then run savage.bin

Is there another version out there???

---

### Post by gotmonkey on 2006-07-23
That is odd, I haven't heard of savage having more than one cd. What I pulled together was what I found on the savage forums st s2games. 

If you have a multi cd install. check the to see if there is any insight. 

Sorry, I couldn't be much help

---

### Post by soapytheclown on 2006-07-28
> **walkerx said:**
> I've got the savage install cd's and for linux its stored on the bonus cd, but nowhere can i find the INSTALL.Linux file you mention, even in reading the included textfile for linux it only tells you to copy the files then run savage.bin

Is there another version out there???


Hey ive just tried this, incase you still havent got this working, 

firstly im guessing there is a different version as i could only partially follow the steps given, but doing it from the install cd is much simpler. 

Copy the files over, as the CD states, and get the b patch, and then the "b to c" patch (the first two links given by gotmonkey) and then from the notforidiots site get patch F (its the brand new one):

[http://www.notforidiots.com/forum/viewtopic.php?t=686](http://www.notforidiots.com/forum/viewtopic.php?t=686)

copy all the new files in (in the logical order of course), and your done, make sure that "silverback.bin" is executable (in permissions) and then run that, dont run savage.bin.

if for some reason you have problems with your sound as i did, just restart your Xserver, and it should run fine

---

### Post by flebber on 2006-10-10
Cd's I haven't got any I was downloading straight from the the site [http://www.s2games.com/savage/downloads.php](http://www.s2games.com/savage/downloads.php) .

The instructions they refer to are here [http://www.evolvedclan.com/forums/index.php/topic,259.0.html](http://www.evolvedclan.com/forums/index.php/topic,259.0.html) However the linux instructions say just install each as you go but all packages are in various formats, If you have got them going I would love a little more verbose instructions on what you did.

---

