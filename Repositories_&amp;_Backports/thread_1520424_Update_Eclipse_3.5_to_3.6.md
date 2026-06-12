---
title: "Update Eclipse 3.5 to 3.6"
date: 2010-06-29
forum: Repositories &amp; Backports
---

### Post by topviet on 2010-06-29
My Ubuntu 10.04 already had Eclipse 3.5 along with Android stuff. I downloaded a new version Eclipse 3.6 Helios Java EE for Ubuntu and unzipped it. So how can I get Eclipse 3.6 running when I type eclipse at terminal or click on the menu (Applications -> Programming -> Eclipse)

It seem to Eclipse 3.6 is not add to the Ubuntu repository yet. 

What is the location of Eclipse 3.5 on my Ubuntu 10.04?

---

### Post by NoBugs! on 2010-07-03
Don't know about the installation, but "whereis eclipse" command should show where it is, you can also see in the properties in Synaptic Package Manager.

---

### Post by GregBrannon on 2010-07-04
To get your 3.6 download running:

 - Unzip the download into a directory you have complete control of, usually a directory under your username, preserving folders.

 - Create a shortcut to the eclipse executable, usually in the resulting "eclipse" folder.

 - Run the program using the resulting shortcut.

 - When your new eclipse install starts, point to your existing workspace.

You can continue with both 3.5 and 3.6 installed using the same workspace, or you can remove 3.5 by deselecting it from your software management program (one of several ways.)

Good luck!

---

### Post by tuthmosis on 2010-07-04
Another counter intuitive phenomenon !
Is it restricted to Linux ?

Is it just me or am i seeing an "Update" button greyedout when selecting the "eclipse 3.5" item in the "installed software" list ?

Why not use this apparent feature ?

Anyway !](*,)

---

### Post by slowpoison on 2010-07-05
> Is it just me or am i seeing an "Update" button greyedout when selecting the "eclipse 3.5" item in the "installed software" list ?

That will always be grayed out till there is an update for Eclipse package available from the Ubuntu team.

---

### Post by SKLP on 2010-07-14
Is there any Eclipse 3.6 PPA?

---

### Post by mobrien118 on 2010-12-11
> **SKLP said:**
> Is there any Eclipse 3.6 PPA?

I second this question (suggestion?)

How hard is it to make a PPA? With all the eclipse users out there, this seems like something that would be done already. Maybe I'll give it a shot some day, when I have time...

--mobrien118

---

### Post by afv on 2010-12-15
There's this PPA: [https://launchpad.net/~eclipse-team/+archive/debian-package](https://launchpad.net/~eclipse-team/+archive/debian-package)

---

### Post by Urhixidur on 2011-01-07
When I found this ppa, I thought "At last!", 'cause I badly need 3.6 for my work...

But once upgraded, Eclipse 3.6 won't run: even if called with "-clean", all I get is the splash screen, then it quits without any message whatsoever.

What is going on?

---

### Post by microcris on 2011-02-14
Same here :(

Does anyone have the solution for this?

---

### Post by waw2637 on 2011-02-23
Well I tried the PPA and no luck. I got the same error. I even removed all 3.5 eclipse junk before hand.

My solution, I might add not very pretty, download eclipse from the main site and then used sudo nautilus and copy the files from the eclipse download to /usr/lib/eclipse. All done. Eclipse 3.6 ready to code. Probably not ideal, but it works.

---

### Post by pauljwells on 2011-03-16
My experience of Eclipse on Ubuntu is that the first run has to be as root, I guess Eclipse tries to save some config files in system directories. You also have to run as root if you want to install plugins, pydev for example. After that you can run as a normal user.
You have to remember that Eclipse is written in (I think, pure) Java to be very portable. This means it's a bit of a mess and doesn't run the same as native programs on any platform! Some tweaking will always be inevitable...
I have it running very nicely here on 64 bit Ubuntu 10.10 PowerPC, one of the least-loved Ubuntus, so if it works here it should work on any x86 box!

---

### Post by hypatia on 2011-04-01
the eclipse-team ppa hasn't been updated since 2009 :(

i ended up installing [s]the binary from [http://www.eclipse.org/downloads/](http://www.eclipse.org/downloads/) as well.[/s] this newer ppa! [https://launchpad.net/~eclipse-team/+archive/debian-package](https://launchpad.net/~eclipse-team/+archive/debian-package) which works great.

---

### Post by stchman on 2011-04-05
All you need to do is go to the Eclipse website and download the pre-compiled binaries for Linux 32 or 64 bit.  They work well.

---

### Post by lores on 2011-05-18
> **Urhixidur said:**
> When I found this ppa, I thought "At last!", 'cause I badly need 3.6 for my work...

But once upgraded, Eclipse 3.6 won't run: even if called with "-clean", all I get is the splash screen, then it quits without any message whatsoever.

What is going on?
Same problem here, has been happening since I installed Eclipse 3.6.0 from [https://launchpad.net/~eclipse-team/+archive/debian-package](https://launchpad.net/~eclipse-team/+archive/debian-package) on 11.04...

---

### Post by stinkinrich88 on 2011-06-09
> **hypatia said:**
> the eclipse-team ppa hasn't been updated since 2009 :(

i ended up installing [s]the binary from [http://www.eclipse.org/downloads/](http://www.eclipse.org/downloads/) as well.[/s] this newer ppa! [https://launchpad.net/~eclipse-team/+archive/debian-package](https://launchpad.net/~eclipse-team/+archive/debian-package) which works great.

This installs fine on 64bit, but Eclipse fails to start. Shame!

---

### Post by gecko_gp on 2011-07-07
I used the ppa and had the same issue, but then i installed the libswt-gtk-3.6-java and problem solved.

---

### Post by Roberto.Maurizzi on 2011-07-20
I just tried on 10.04 and there's no libswt-gtk-3.6-java, only libswt-gtk-3.5-java and... it doesn't work -__-;
I'll see if there is/I can open a packaging bug for the PPA

---

### Post by kimusan on 2011-08-24
I have found a fix for the 3.6 ppa (at least on Natty).

After installation, make sure you have  xulrunner-2.0 and all the libswt-*-3.6* packages (both the -java and -jni). 

go into /usr/lib/eclipse/debian-swt and run the following

sudo ln -s /usr/lib/jni/libswt-*

Now you should be able to run eclipse 3.6 Helios without any problem

---

### Post by steve_c on 2011-08-25
As an alternative, I've been using Pulse for the last year or two. It manages all the sometimes-overly-complicated Eclipse plugin issues and updates, and lets me save profiles that I can run on any machine I use (home/laptop/office). Free for individual use.

[Pulse Community Edition]("http://www.poweredbypulse.com/community_edition.php/")

That said if the PPA is working well (now or ever), I'll probably switch to that because I would prefer to manage as much of my software as possible with apt-based package management so I can use the same package manager for everything.

---

### Post by matiasw on 2011-11-04
> **kimusan said:**
> I have found a fix for the 3.6 ppa (at least on Natty).

After installation, make sure you have  xulrunner-2.0 and all the libswt-*-3.6* packages (both the -java and -jni). 

go into /usr/lib/eclipse/debian-swt and run the following

sudo ln -s /usr/lib/jni/libswt-*

Now you should be able to run eclipse 3.6 Helios without any problem

Nuh-uh (sorry). 
I've installed xulrunner-2.0 and the libswt packages, and I've symlinked as you said. However, Eclipse still won't start - here's [the bug report]("https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/886088").

---

### Post by matiasw on 2011-11-25
Just to update - the new 3.7 (Indigo) release seems to work fine in Oneiric.

---

### Post by hwertz on 2012-01-12
I just got it running.  There's a possible type in the above directions.
      I used the repository mentioned, installed xulrunner-2.0 and the swt libs.  Then (as root) I did:
```
cd /usr/lib/eclipse/debian-swt
ln -s ../../jni/libswt* .
```

(This is effectively equivalent
```
ln -s /usr/lib/jni/libswt* .
```
unless you nfs export your drive, which I do sometimes.)

     That period makes all the difference!  I did run eclipse as root the first time, but I don't know if that's necessary or not.
     Probably someone should fix the .deb package so it has those dependencies.  I'm not going to do it though! :lolflag:  Oh well.   Android Development Kit here I come! :popcorn:

---

### Post by topsites on 2012-12-16
That's all fine and dandy but on my system there is no usr/lib/eclipse folder

Interestingly enough however, from within the software centre selecting eclipse, on the install screen there is an option to select version.

---

