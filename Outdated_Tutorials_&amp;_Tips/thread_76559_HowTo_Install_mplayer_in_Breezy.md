---
title: "HowTo: Install mplayer in Breezy"
date: 2005-10-15
forum: Outdated Tutorials &amp; Tips
---

### Post by verzonnen on 2005-10-15
To install mplayer in breezy I had to add the uncomment the universe repositories and add the "multiverse" repositories.

deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy multiverse

I am posting this in the hope it will help others

---

### Post by aysiu on 2005-10-15
Can you give a little more step-by-step than that?

---

### Post by verzonnen on 2005-10-15
Well I'll try to add more detail, but I am not good at writing documentation, nor do I know apt, anyway this is what I did.

1) edit /etc/apt/sources.list and uncomment the lines for universe 
(remove the "#" in front of the lines)

2) add a line similar to universe see the example; [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy  multiverse
(note I am in Canada, I sugest you get a miiror closer to you)

3) download any extra codecs; wget [http://www2.mplayerhq.hu/MPlayer/releases/codecs/all-20050412.tar.bz2](http://www2.mplayerhq.hu/MPlayer/releases/codecs/all-20050412.tar.bz2)

4) unpack the codecs;  tar -xvjf all-20050412.tar.bz2

5) become root ; su - root

6) change directory to /tmp; cd /tmp
 
7) create the directory for the codecs; mkdir /usr/lib/win32

8) move the "codecs" to the new directory; mv all-20050412/* /usr/lib/win32

9) install mplayer; apt-get install mplayer-586

Good luck

---

### Post by soulestream on 2005-10-15
you also need a 

sudo apt-get install mplayer-fonts

other than that cool


soule

---

### Post by Sale on 2005-10-16
Does 
sudo apt-get install mplayer-fonts
retrieve the fonts available at:
[http://www2.mplayerhq.hu/homepage/design7/dload.html](http://www2.mplayerhq.hu/homepage/design7/dload.html)
If not, where do I put those after I manually download them?

TIA

Sale

---

### Post by rush_ad on 2005-10-16
anyone having full screen problem? it goes full screen but picture size stayes the same and borders are black.

---

### Post by djkork on 2005-10-16
This is because you are using X11 video output option... that doesn't support hw scaling
Change video output option to XV...

---

### Post by Omnios on 2005-10-16
> verzonnen Wrote:
Well I'll try to add more detail, but I am not good at writing documentation, nor do I know apt, anyway this is what I did.

1) edit /etc/apt/sources.list and uncomment the lines for universe
(remove the "#" in front of the lines)

2) add a line similar to universe see the example; [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy multiverse
(note I am in Canada, I sugest you get a miiror closer to you)

3) download any extra codecs; wget [http://www2.mplayerhq.hu/MPlayer/rel...050412.tar.bz2](http://www2.mplayerhq.hu/MPlayer/rel...050412.tar.bz2)

4) unpack the codecs; tar -xvjf all-20050412.tar.bz2



tom@main:~/dtemp$ wget [http://www2.mplayerhq.hu/MPlayer/rel...050412.tar.bz2](http://www2.mplayerhq.hu/MPlayer/rel...050412.tar.bz2)
--19:43:42--  [http://www2.mplayerhq.hu/MPlayer/rel...050412.tar.bz2](http://www2.mplayerhq.hu/MPlayer/rel...050412.tar.bz2)
           => `rel...050412.tar.bz2'
Resolving www2.mplayerhq.hu... 193.225.187.202
Connecting to www2.mplayerhq.hu|193.225.187.202|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
19:43:43 ERROR 404: Not Found.

 Got an 404 error can anyone confirm this hope they didnt drop this file

---

### Post by bored2k on 2005-10-16
You have to copy and paste the URL. The link automatically gets shrinked by the forums.

---

### Post by afnola on 2005-10-16
Yea, Im getting that error also....

---

### Post by Omnios on 2005-10-16
K got it to work had to copy link location the original link from the original post and type wget in front of it and past in the address. 

 Thanks

---

### Post by afnola on 2005-10-16
If you have trouble with dead link (like I did) you should put those repositories in that were listed in the first post...  Then go into synaptic and search for mplayer and it will be there to download.

---

### Post by Murgle on 2005-10-16
[QUOTE=rush_ad]anyone having full screen problem? it goes full screen but picture size stayes the same and borders are black.[/QUOTE]

to get fullscreen in mplayer just add -zoom at the commandline

---

### Post by arnieboy on 2005-10-16
[QUOTE=Murgle]to get fullscreen in mplayer just add -zoom at the commandline[/QUOTE]
or change **zoom=no** to **zoom=yes** in */etc/mplayer/mplayer.conf *

---

### Post by rush_ad on 2005-10-16
[QUOTE=arnieboy]or change **zoom=no** to **zoom=yes** in */etc/mplayer/mplayer.conf *[/QUOTE]

your solution works but gnome top and bottom panels are still visible. full screen only overlaps the desktop area

---

### Post by arnieboy on 2005-10-16
[QUOTE=rush_ad]your solution works but gnome top and bottom panels are still visible. full screen only overlaps the desktop area[/QUOTE]
do u run mplayer (from terminal) or gmplayer (the GUI version of mplayer with the fancy controls and stuff)?

---

### Post by t2kburl on 2005-10-17
trying to do this using adept in kubuntu and it keeps coming up broken

---

### Post by era on 2005-10-17
To reiterate, the link which is displayed in the forum is shortened automatically by the forum software, so you can't just copy and paste the "wget" command line from here. The URL you should "wget" is 

[http://www2.mplayerhq.hu/](http://www2.mplayerhq.hu/)
MPlayer/releases/codecs/
all-20050412.tar.bz2

all on one line of course.

As you can tell, it's a version from April of this year. It's probably be replaced by a newer version some day.

---

### Post by rush_ad on 2005-10-17
[QUOTE=djkork]This is because you are using X11 video output option... that doesn't support hw scaling
Change video output option to XV...[/QUOTE]

thanks, it worked

---

### Post by rush_ad on 2005-10-17
how do i fix that full screen error in vlc?

---

### Post by Azrael on 2005-10-17
double post

---

### Post by Azrael on 2005-10-17
> **verzonnen]1) edit /etc/apt/sources.list and uncomment the lines for universe (remove the "#" in front of the lines)

2) add a line similar to universe see the example said:**
> http://ca.archive.ubuntu.com/ubuntu[/url] breezy  multiverse
(note I am in Canada, I sugest you get a miiror closer to you)

[...]

9) install mplayer; apt-get install mplayer-586
I chose the multiverse repositories like you suggested, but "sudo apt-get update", "sudo apt-get install mplayer-586" gives me:

sudo apt-get install mplayer-586
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer-586: Depends: libpolyp0 but it is not installable
               Depends: libsvga1 but it is not installable or
                        svgalib-dummyg1 but it is not installable

---

### Post by Mastodront on 2005-10-17
I'm getting "mplayer-586:
 Beror (Depends): libdirectfb-0.9-20  but it is not installable"

:(

---

### Post by kayas80 on 2005-10-17
[quote=djkork]This is because you are using X11 video output option... that doesn't support hw scaling
Change video output option to XV...[/quote]

Thanks for teh fix tip djkork, that was really annoying me.

---

### Post by Garde on 2005-10-18
I actually have to use X11 or the OpenGL args instead of XV, because the video won't display.  I've installed all the codecs like you said, but it won't play with -vo xv...  Can anyone tell me how to fix this?

Edit: I have both mplayer (command line) and mplayer-k6 installed.

I installed mplayer-586 over it, and it can't play with xv either, though it can play with x11 and gl.

---

### Post by Azrael on 2005-10-18
[quote=Garde]I actually have to use X11 or the OpenGL args instead of XV, because the video won't display. I've installed all the codecs like you said, but it won't play with -vo xv... Can anyone tell me how to fix this?

Edit: I have both mplayer (command line) and mplayer-k6 installed.

I installed mplayer-586 over it, and it can't play with xv either, though it can play with x11 and gl.[/quote]
xv doesn't work with all video cards. Google for *mplayer* and <*your video card model>* to find out which video output option you should use. also do: *man mplayer* for more info and *mplayer -vo help* for available options.

---

### Post by Luggy on 2005-10-24
About the whole mpalyer-586 thing, this is what it says if you read about it in synaptic.
> This version is for Pentium Pro/Celeron/Pentium II/Pentium IIIPentium
Pro/Celeron/Pentium II/Pentium III/Pentium IV
So unless you are running those processors, I would just use the mplayer-386 version.

If you are having trouble getting fullscreen to work, edit /etc/mplayer/mplayer.conf and change the default video mode to xv. That will make the non-graphical version work.

---

### Post by cledus on 2005-10-24
I need help installing mplayer.
I still can't get it to work.
Can someone explain it like this post for java:
[http://www.ubuntuforums.org/showthread.php?t=76754&highlight=java](http://www.ubuntuforums.org/showthread.php?t=76754&highlight=java)
It worked for me.
I am trying to convert my kids over to Linux, but half the sites they visit don't work.
The latest is [www.wwe.com](www.wwe.com).
I am using Kubuntu.

---

### Post by oskude on 2005-11-03
hi,
[QUOTE=Mastodront]I'm getting "mplayer-586:
 Beror (Depends): libdirectfb-0.9-20  but it is not installable"[/QUOTE]
had the same problem CAUSE i forgot to change "hoary" to "breezy" in the line```
deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse
```that i copy'n'pasted from here [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

:oops: 

cheers
osku[de]

---

### Post by Vetto on 2005-12-18
OK...what repository is mplayer actually in?  I cant find it in breezy universe or multiverse.  Was is removed?

Here is my sources.list
[INDENT]
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted 

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted 
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted 

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe 
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe 

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse 
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe [/INDENT]

---

### Post by htinn on 2005-12-25
I haven't been able to install mplayer at all. I ran this:

sudo apt-get install mplayer-386

and it returned this:

> Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mplayer-386: Depends: libfribidi0 (>= 0.10.5-4) but 0.10.5-2 is to be installed
               Depends: libgcc1 (>= 1:4.0.2) but 1:4.0.1-4ubuntu9 is to be installed
               Depends: libjack0.100.0-0 (>= 0.100.0) but it is not installable
               Depends: libstdc++6 (>= 4.0.2-3) but 4.0.1-4ubuntu9 is to be installed
E: Broken packages

EDIT: Never mind. Found the answer here:

[http://www.ubuntuforums.org/showthread.php?t=105479](http://www.ubuntuforums.org/showthread.php?t=105479)

---

### Post by aptsonic on 2005-12-25
[QUOTE=arnieboy]or change **zoom=no** to **zoom=yes** in */etc/mplayer/mplayer.conf *[/QUOTE]

when i do this i get an error message from mplayer, detailing its crash..

i've tried its default driver output as x11, and gl, i'm running amd64. with a nvidia 6600gt

---

### Post by manishsingh4u on 2006-03-30
[QUOTE=verzonnen]To install mplayer in breezy I had to add the uncomment the universe repositories and add the "multiverse" repositories.

deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy universe
deb [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) breezy multiverse

I am posting this in the hope it will help others[/QUOTE]

Thanks for the help guys, with your help, I successfully installed Mplayer on my Kubuntu 5.10.
It works really smooth this way.

---

### Post by manishsingh4u on 2006-03-30
[QUOTE=aptsonic]when i do this i get an error message from mplayer, detailing its crash..

i've tried its default driver output as x11, and gl, i'm running amd64. with a nvidia 6600gt[/QUOTE]

Choose Xv instead of X11 for video output and it will work fine in fullscreen.

---

### Post by tk40775 on 2006-04-05
[QUOTE=Garde]I actually have to use X11 or the OpenGL args instead of XV, because the video won't display.  I've installed all the codecs like you said, but it won't play with -vo xv...  Can anyone tell me how to fix this?

Edit: I have both mplayer (command line) and mplayer-k6 installed.

I installed mplayer-586 over it, and it can't play with xv either, though it can play with x11 and gl.[/QUOTE]

I've had the same problem and adding the following lines to my /etc/X11/xorg.conf under the "Device" section solved the it:

```
Option "VideoOverlay" "on"
Option "OpenGLOverlay" "off"
```

Btw, I have ATI Radeon 9100 graphic card with fglrx driver installed.

---

