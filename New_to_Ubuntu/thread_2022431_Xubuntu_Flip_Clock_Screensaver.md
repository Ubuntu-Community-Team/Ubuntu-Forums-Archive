---
title: "Xubuntu Flip Clock Screensaver?"
date: 2012-07-10
forum: New to Ubuntu
---

### Post by S2UIRR3L on 2012-07-10
Can anyone tell me how to get one of these Flip Clock Screensavers on xubuntu 12.04?

I have a crappy little laptop that I use as a radio for my favorite  on-line stream. I would love it if this laptop can double as a desktop  flip clock, as this laptop stays on 24/7.

Can someone point me in a direction to where I can download it and  instructions on how to install it... I'm VERY new to xubuntu 12.04 and  don't know the first thing about XFCE.

(here's a photo of what I'm looking for)
[IMG]http://i292.photobucket.com/albums/mm10/s2uirr3l/clocksaver.jpg[/IMG]
Thanks for everything!
-Leo in Massachusetts

---

### Post by Toz on 2012-07-11
How about noflipqlo ([https://github.com/bhm/noflipqlo]("https://github.com/bhm/noflipqlo"))?

[[img]http://en.zimagez.com/miniature/noflipqlo.png[/img]]("[url=http://en.zimagez.com/zimage/noflipqlo.php)"][[img]http://en.zimagez.com/miniature/noflipqlo.png[/img]](http://en.zimagez.com/zimage/noflipqlo.php)[/URL]

Unfortunately, it looks like you need to manually install it yourself from git (I can't find a PPA). Here are the instructions that worked for me on xubuntu 12.04.

**_Disclaimer:_** this program requires xscreensaver (the default installed with Xubuntu) and if gnome-screensaver is installed, it will disable it and install xscreensaver. To find out which screensaver you have running, use this command:
```
ps -ef | grep screensaver
```



[LIST=1]
[*]Install git
```
sudo apt-get install git
```
[*]Get the source code
```
git clone git://github.com/bhm/noflipqlo
```
[*]Go to the source directory
```
cd noflipqlo
```
[*]Create the required images directory
```
sudo mkdir /usr/share/images
```
[*]Install it (note: the binary is precompiled)
```
sudo make install
```
[*]Install the required dependencies
```
sudo apt-get install fonts-droid libsdl-gfx1.2-4
```
[*]Fix the font location issue
```
sudo ln -s /usr/share/fonts/truetype/droid /usr/share/fonts/truetype/ttf-droid
```
[*]Add the new screensaver
Edit **~/.xscreensaver**:
```
leafpad ~/.xscreensaver
```
...and add:
```
noflipqlo -ampm -root				   \n\
```
...to the end of the list of screensavers and save the file.

[*]Restart xscreensaver
Logout and back in again or run:
```
pkill xscreensaver && xscreensaver -nosplash &
```
[/LIST]

It should then show up in the list of available screensavers.

---

### Post by S2UIRR3L on 2012-07-11
I'm guessing this will take a while, but as long as I do it step by step, in sequence, it will work with this little laptop... I hope it can handle it, only being an old Celeron M 1.80 with about 512-Mb of RAM.



The only thing that I'm a little confused about is step #8.

If I enter:
**leafpad ~/.xscreensaver**
into the terminal, that will open the text document in leafpad and I'll just add:
**noflipqlo -ampm -root                   \n\**
to the very bottom and save before closing that leafpad?



Thanks a million for all your time and for making everything so easy to follow. I've searched up and down, all over Ubuntu Forums and did about 4 hours of Googling and couldn't find anything that I could understand. I found a few things here and there, but nothing that had any instructions to it.

I'll try this as soon as I get home today... Thanks again, Toz!
I'll update this after testing (and hopefully mark it SOLVED)!

---

### Post by Toz on 2012-07-11
> **S2UIRR3L said:**
> I'm guessing this will take a while, but as long as I do it step by step, in sequence, it will work with this little laptop... I hope it can handle it, only being an old Celeron M 1.80 with about 512-Mb of RAM.



The only thing that I'm a little confused about is step #8.

If I enter:
**leafpad ~/.xscreensaver**
into the terminal, that will open the text document in leafpad and I'll just add:
**noflipqlo -ampm -root                   \n\**
to the very bottom and save before closing that leafpad?
You need to pt it in the correct position (programs: ) and I think maybe with the correct formatting. Here is a snippet of the last part of my file (the added part in red):
```

  GL: 				companioncube -root			    \n\
  GL: 				hilbert -root				    \n\
  GL: 				tronbit -root				    \n\
[COLOR="Red"]				noflipqlo -ampm -root			    \n\[/COLOR]

pointerPollTime:    0:00:05
pointerHysteresis:  10
windowCreationTimeout:0:00:30
initialDelay:	0:00:00
GetViewPortIsFullOfLies:False
procInterrupts:	True
xinputExtensionDev: False
overlayStderr:	True
```



> Thanks a million for all your time and for making everything so easy to follow. I've searched up and down, all over Ubuntu Forums and did about 4 hours of Googling and couldn't find anything that I could understand. I found a few things here and there, but nothing that had any instructions to it.

I'll try this as soon as I get home today... Thanks again, Toz!
I'll update this after testing (and hopefully mark it SOLVED)!

No worries, let me know how it goes.

I guess I should add this disclaimer as well: this program requires xscreensaver (the default installed with Xubuntu) and if gnome-screensaver is installed, it will disable it and install xscreensaver. To find out which screensaver you have running, use this command:
```
ps -ef | grep screensaver
```
(I'll add this to the top of my first reply.)

---

### Post by S2UIRR3L on 2012-07-11
Okay - I'm about to restart my computer to see if it will work. As for gnome screensaver, I couldn't care less if it's installed or not, since I'll have this neat little clock. Also, here's a copy of everything that was in the terminal window, just in case it doesn't work... I'll have this as a back up to see where I went wrong lol.

-Leo in Massachusetts

CONTENTS OF TERMINAL AFTER ALL COMMANDS WERE EXECUTED
(I'm very sorry for this long thing, I don't know how to zip files yet)

```
squirrel@inspiron-1000:~$ sudo apt-get install git
[sudo] password for squirrel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  git-man liberror-perl patch
Suggested packages:
  git-daemon-run git-daemon-sysvinit git-doc git-el git-arch git-cvs git-svn
  git-email git-gui gitk gitweb diffutils-doc
The following NEW packages will be installed:
  git git-man liberror-perl patch
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 6,703 kB of archives.
After this operation, 15.5 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/main liberror-perl all 0.17-1 [23.8 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise/main git-man all 1:1.7.9.5-1 [630 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise/main git i386 1:1.7.9.5-1 [5,963 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ precise/main patch i386 2.6.1-3 [86.0 kB]
Fetched 6,703 kB in 18s (366 kB/s)                                             
Selecting previously unselected package liberror-perl.
(Reading database ... 159931 files and directories currently installed.)
Unpacking liberror-perl (from .../liberror-perl_0.17-1_all.deb) ...
Selecting previously unselected package git-man.
Unpacking git-man (from .../git-man_1%3a1.7.9.5-1_all.deb) ...
Selecting previously unselected package git.
Unpacking git (from .../git_1%3a1.7.9.5-1_i386.deb) ...
Selecting previously unselected package patch.
Unpacking patch (from .../patch_2.6.1-3_i386.deb) ...
Processing triggers for man-db ...
Setting up liberror-perl (0.17-1) ...
Setting up git-man (1:1.7.9.5-1) ...
Setting up git (1:1.7.9.5-1) ...
Setting up patch (2.6.1-3) ...
squirrel@inspiron-1000:~$ git clone git://github.com/bhm/noflipqlo
Cloning into 'noflipqlo'...
remote: Counting objects: 66, done.
remote: Compressing objects: 100% (56/56), done.
remote: Total 66 (delta 7), reused 61 (delta 5)
Receiving objects: 100% (66/66), 54.38 KiB, done.
Resolving deltas: 100% (7/7), done.
squirrel@inspiron-1000:~$ cd noflipqlo
squirrel@inspiron-1000:~/noflipqlo$ sudo mkdir /usr/share/images
squirrel@inspiron-1000:~/noflipqlo$ sudo make install
install -o root noflipqlo /usr/lib/xscreensaver/
install -o root noflipqlo.xml /usr/share/xscreensaver/config/
install -o root back.bmp /usr/share/images/        
squirrel@inspiron-1000:~/noflipqlo$ sudo apt-get install fonts-droid libsdl-gfx1.2-4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fonts-droid is already the newest version.
The following NEW packages will be installed:
  libsdl-gfx1.2-4 libsdl1.2debian
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 253 kB of archives.
After this operation, 684 kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise/main libsdl1.2debian i386 1.2.14-6.4ubuntu3 [205 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise/universe libsdl-gfx1.2-4 i386 2.0.23-1 [47.5 kB]
Fetched 253 kB in 0s (337 kB/s)       
Selecting previously unselected package libsdl1.2debian.
(Reading database ... 160590 files and directories currently installed.)
Unpacking libsdl1.2debian (from .../libsdl1.2debian_1.2.14-6.4ubuntu3_i386.deb) ...
Selecting previously unselected package libsdl-gfx1.2-4.
Unpacking libsdl-gfx1.2-4 (from .../libsdl-gfx1.2-4_2.0.23-1_i386.deb) ...
Setting up libsdl1.2debian (1.2.14-6.4ubuntu3) ...
Setting up libsdl-gfx1.2-4 (2.0.23-1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
squirrel@inspiron-1000:~/noflipqlo$ sudo ln -s /usr/share/fonts/truetype/driod /usr/share/fonts/truetype/ttf-driod
squirrel@inspiron-1000:~/noflipqlo$ leafpad ~/.xscreensaver
squirrel@inspiron-1000:~/noflipqlo$ pkill xscreensaver && xscreensaver -nosplash &
[1] 6462
squirrel@inspiron-1000:~/noflipqlo$ 
```

---

### Post by S2UIRR3L on 2012-07-11
It was too easy and I knew I'd screw it up lol...

I rebooted my computer, and tried activating the screensaver. It shows up in the list and lets me click on it, but won't show a preview... and when I try to preview it full screen, this is the message that I get:

```
noflipqlo: error while loading shared libraries: libSDL_ttf-2.0.so.0: can not open shared object file: No cush file or directory
xscreensaver: 12:15:40: 0: child pid 1623 (noflipqlo) exited abnormally code 127.
```Any idea of where I went wrong and could it be fixed?

---

### Post by hakermania on 2012-07-11
> **S2UIRR3L said:**
> It was too easy and I knew I'd screw it up lol...

I rebooted my computer, and tried activating the screensaver. It shows up in the list and lets me click on it, but won't show a preview... and when I try to preview it full screen, this is the message that I get:

```
noflipqlo: error while loading shared libraries: libSDL_ttf-2.0.so.0: can not open shared object file: No cush file or directory
xscreensaver: 12:15:40: 0: child pid 1623 (noflipqlo) exited abnormally code 127.
```Any idea of where I went wrong and could it be fixed?

I'm not 100% sure but try the following:
```

sudo apt-get install libsdl-ttf2.0-0

```
and then retry displaying the screensaver.

---

### Post by S2UIRR3L on 2012-07-11
```

sudo apt-get install libsdl-ttf2.0-0

```

I tried this and now I'm getting a new error code:

```

xscreensaver: 12:57:30 0: child pid 2193 (noflipqlo) terminated with signal 11.

```

---

### Post by Toz on 2012-07-11
What happens if you run:
```
/usr/lib/xscreensaver/noflipqlo -ampm
```
...it should run the screensaver in a window.

---

### Post by Toz on 2012-07-11
Are you running 64-bit Xubuntu?

To recompile, consider this step 4.5:

a. Clean it up:
```
make clean
```

b. Install dev headers and libs:
```
sudo apt-get install libsdl1.2-dev libsdl-ttf2.0-dev libsdl-gfx1.2-dev libx11-dev
```

c. Fix the makefile:
Change the line that reads:
> CFLAGS= -Wall `sdl-config --cflags`  `sdl-config --libs` -lX11 -lSDL_ttf -lSDL_gfx main.cpp -o noflipqlo
...to
```
CFLAGS= -Wall main.cpp -o noflipqlo `sdl-config --cflags`  `sdl-config --libs` -lX11 -lSDL_ttf -lSDL_gfx
```

d. Build the executable:
```
make
```

...follow on with step 5.

---

### Post by S2UIRR3L on 2012-07-11
It almost wanted to start... I seen the little window flash on for a second, then it went away and terminal returned this message:

```
squirrel@inspiron-1000:~$ /usr/lib/xscreensaver/noflipqlo -ampm
TTF_OpenFont: Couldn't open /usr/share/fonts/truetype/ttf-droid/DroidSans-Bold.ttf
Time is: 14 : 59
Segmentation fault (core dumped)
squirrel@inspiron-1000:~$ 
```

---

### Post by S2UIRR3L on 2012-07-11
I'm running 32-bit because it's a really old and slower little laptop.

---

### Post by Toz on 2012-07-11
> **S2UIRR3L said:**
> 
TTF_OpenFont: Couldn't open /usr/share/fonts/truetype/ttf-droid/DroidSans-Bold.ttf
Does this font exist?

Did you install droid-fonts? (step 6)
Did you link ttf directories? (step 7)

---

### Post by S2UIRR3L on 2012-07-11
I just re-did steps 6 and 7 to make sure... here are the results:

here is step 6

```
squirrel@inspiron-1000:~$ sudo apt-get install fonts-droid libsdl-gfx1.2-4
[sudo] password for squirrel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fonts-droid is already the newest version.
libsdl-gfx1.2-4 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
squirrel@inspiron-1000:~$ 
```and here is 7

```
squirrel@inspiron-1000:~$ sudo ln -s /usr/share/fonts/truetype/driod /usr/share/fonts/truetype/ttf-driod
[sudo] password for squirrel: 
ln: failed to create symbolic link `/usr/share/fonts/truetype/ttf-driod': File exists
squirrel@inspiron-1000:~$ 
```I just tried manually searching for the folder with the fonts... This is what I found (photo attached)

---

### Post by Toz on 2012-07-11
OOPS, just realized a typo in Step 7. It should read:
```
sudo ln -s /usr/share/fonts/truetype/dr[COLOR="Red"]oi[/COLOR]d /usr/share/fonts/truetype/ttf-dr[COLOR="Red"]oi[/COLOR]d
```

Sorry about that.

---

### Post by S2UIRR3L on 2012-07-11
This is what I get... and I still get the plain black preview window, and an error message when I try to preview in full screen... Here's what terminal says:

```
squirrel@inspiron-1000:~$ sudo ln -s /usr/share/fonts/truetype/driod /usr/share/fonts/truetype/ttf-droid
[sudo] password for squirrel: 
squirrel@inspiron-1000:~$ sudo ln -s /usr/share/fonts/truetype/driod /usr/share/fonts/truetype/ttf-droid
ln: failed to create symbolic link `/usr/share/fonts/truetype/ttf-droid': File exists
squirrel@inspiron-1000:~$ ls -l /usr/share/fonts/truetype/ttf-droid/DroidSans-Bold.ttf
ls: cannot access /usr/share/fonts/truetype/ttf-droid/DroidSans-Bold.ttf: No such file or directory
squirrel@inspiron-1000:~$
```

And like I tried to edit in my last post, here's a photo of me trying to see what's in the folder, searching for it manually (photo attached)

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=221087&d=1342035525[/IMG]

---

### Post by Toz on 2012-07-11
Looks like you might already have a ttf-droid directory. Try this:
```
sudo ln -s /usr/share/fonts/truetype/droid/DroidSans-Bold.ttf /usr/share/fonts/truetype/ttf-droid/
```

And can you show the results of:
```
ls /usr/share/fonts/truetype/ttf-droid/
```

---

### Post by S2UIRR3L on 2012-07-11
Here's terminal output #1
```
squirrel@inspiron-1000:~$ sudo ln -s /usr/share/fonts/truetype/droid/DroidSans-Bold.ttf /usr/share/fonts/truetype/ttf-droid/
[sudo] password for squirrel: 
ln: target `/usr/share/fonts/truetype/ttf-droid/' is not a directory: No such file or directory
squirrel@inspiron-1000:~$ 
```Here's terminal output #2
```
squirrel@inspiron-1000:~$ ls /usr/share/fonts/truetype/ttf-droid/
ls: cannot access /usr/share/fonts/truetype/ttf-droid/: No such file or directory
squirrel@inspiron-1000:~$ 
```Do these files and directories look correct to you? (photos attached)

---

### Post by Toz on 2012-07-11
Okay, I see. Try this:

```
sudo rm /usr/share/fonts/truetype/ttf-driod
sudo rm /usr/share/fonts/truetype/ttf-droid
sudo ln -s /usr/share/fonts/truetype/droid /usr/share/fonts/truetype/ttf-droid

```

Post back again the results of those commands.

---

### Post by S2UIRR3L on 2012-07-11
It worked!!!

Here's the output of the terminal:
```
squirrel@inspiron-1000:~$ sudo rm /usr/share/fonts/truetype/ttf-driod
[sudo] password for squirrel: 
Sorry, try again.
[sudo] password for squirrel: 
squirrel@inspiron-1000:~$ sudo rm /usr/share/fonts/truetype/ttf-driod
rm: cannot remove `/usr/share/fonts/truetype/ttf-driod': No such file or directory
squirrel@inspiron-1000:~$ sudo rm /usr/share/fonts/truetype/ttf-droid
squirrel@inspiron-1000:~$ sudo ln -s /usr/share/fonts/truetype/droid /usr/share/fonts/truetype/ttf-droid
squirrel@inspiron-1000:~$ 
```

Here's a photo of the preview window (photo attached) but I couldn't capture the screen while it was in screen saver mode... But it works, it flips and it's in sync with the actual system clock at the BIOS level... I LOVE IT SO MUCH!!!

Thank you SOOOOO much Toz!
((((((((((VIRTUAL HUGS))))))))))

I'll let it cycle for a little, and then I'll mark it SOLVED

---

### Post by S2UIRR3L on 2012-07-11
**[SIZE=4]F L A W L E S S[/SIZE]**

[SIZE=3]Thanks a million!

[SIZE=2]I set my laptop to it's lowest brightness and I can see it across the room from my bed. I'll never need to squint at the tiny cable box or my cell phone again lol[/SIZE]

**[SIZE=2]This one's marked[/SIZE]**
[SIZE=4]**[ S O L V E D ]**[/SIZE]
[/SIZE]

---

### Post by churka on 2013-06-29
> **S2UIRR3L said:**
> **[SIZE=4]F L A W L E S S[/SIZE]**

[SIZE=3]Thanks a million!

[SIZE=2]I set my laptop to it's lowest brightness and I can see it across the room from my bed. I'll never need to squint at the tiny cable box or my cell phone again lol[/SIZE]

**[SIZE=2]This one's marked[/SIZE]**
[SIZE=4]**[ S O L V E D ]**[/SIZE]
[/SIZE]


can u plz confirm whether it flips?  or it is just the look of flip-clock.

thanks

---

### Post by S2UIRR3L on 2013-07-01
I have it on a laptop that I was about to throw away.
Dell Inspiron 1000 that barely works anymore... so...
I'm using it as a desk clock / streaming internet radio.

The animation is not as smooth as the one that comes
with an actual HTC smart phone, but it does indeed flip.
Even though my laptop is a crapper, the screen is bright.

I wish you all the best with this - It's definitely worth it!
And thanks a million to everyone who's helped me get it!

Cheers!

---

### Post by Alexander_Kovalenko on 2014-02-19
If someone is still searching for Fliqlo replacement, take a look at my own implementation:
[https://github.com/alexanderk23/gluqlo](https://github.com/alexanderk23/gluqlo) :)
I've tried to make it as close to original as possible; however, animation is still missing.

---

### Post by opn6 on 2014-05-03
thank you Alexander . Very thankful for the PPA

---

