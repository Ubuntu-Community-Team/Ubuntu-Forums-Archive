---
title: "HOWTO: electricsheep screensaver with gnome-screensaver! (Dapper)"
date: 2007-02-07
forum: Outdated Tutorials &amp; Tips
---

### Post by EReckase on 2007-02-07
**Introduction**

My name is Erik Reckase, and I'm the current bellybutton for the flam3 rendering engine for the Electric Sheep screensaver, conceptualized and written by Scott Draves.  We're in the process of getting a new client out to the masses with a lot of new features, and it struck me that I've been unable to get the old client running on my Dapper laptop.
 
After trying for a few weeks, I was finally able to gather enough information about gnome-screensaver to understand exactly how to get the Electric Sheep screensaver working on Dapper *without* using xscreensaver.  The voting keys do not currently work, but downloading and rendering work fine.  Since the package in the universe is quite old, this HOWTO will compile the client from the source files.  I will not detail the compilation process, but I will help with specific questions.  I assume a moderate capability with respect to compiling and installing software.

**Getting Ready:**
You will need the following packages to compile the electricsheep client :
[LIST]
[*]libc6-dev
[*]libexpat1-dev
[*]libice6-dev
[*]libjpeg62-dev
[*]libpng12-dev
[*]libsm6 (not sure)
[*]libx11-dev
[*]libxext-dev
[*]libxv-dev
[*]libxml2-dev
[*]zlib1g-dev
[*]curl
[*]xloadimage
[*]libjpeg-progs
[/LIST]

**Step 1:**
Grab the latest sources from electricsheep.org (currently 2.6.8):
[http://electricsheep.org/index.cgi?&menu=code]("http://electricsheep.org/index.cgi?&menu=code")
Click the source tarball link, and extract the folder to your home directory.

**Step 2:**
In the electricsheep-2.6.8 directory, perform
```
./configure
make clean all

```

**Step 3:**
Edit the Makefile with a text editor.  You need to remove these lines from the end of the file:
```

	test -e $(SCREENSAVER_DATADIR) && $(INSTALL) electricsheep.xml $(SCREENSAVER_DATADIR)
	$(INSTALL) -d $(pkgdatadir)

```
Delete these lines from the file and save it.  These lines referred installing the xscreensaver xml file that no longer works for the gnome-screensaver.  The test failed, so the install will fail unless these lines are removed.

**Step 4:**
```
sudo checkinstall -D make install
```
Answer all questions as per standard checkinstall procedures.

**Step 5:**
Create a folder that will hold your Sheep.  Many folks use ~/.sheep for this, but it can be anything in your local area.

**Step 6:**
This is the secret sauce.  As root, or using sudo, create a text file in the /usr/lib/xscreensaver directory called esheep.sh, and paste the following text into the file:
```
#!/bin/sh
exec electricsheep --nick xxxx --root 1 --max-megabytes 2000 --zoom 1 --display-anim 1 --show-errors 0 --nrepeats 2 --frame-rate 30 --save-dir yyyy

```
Replace xxxx with the nickname you would like to be known by on the server.
Replace yyyy with the full path to the directory created in Step 5.

**Step 7:**
```
sudo chmod 755 esheep.sh
```

**Step 8:**
As root, or using sudo, create a text file in the /usr/share/gnome-screensaver/themes directory called electricsheep.desktop, and past the following text into the file:
```
[Desktop Entry]
Encoding=UTF-8
Name=ElectricSheep
Comment=Electric Sheep is a distributed screen-saver that harnesses idle computers into a render farm with the purpose of animating and evolving artificial life-forms. This module requires a high-bandwidth, always-on connection to the internet such as DSL or cable-modem. The first time you run it, it normally takes 5 to 10 minutes before the first sheep is downloaded and displayed. After that, it should come up immediately. If you have installed the hacked xscreensaver that supports passing key-presses onto the graphics hack and this feature is enabled, then pressing the up arrow-key transmits a vote for the currently displayed sheep to the server. The votes are the basis of a fitness function for an evolutionary algorithm on the sheep genomes. Vote for the sheep you like, and they will mate, reproduce, and evolve! See http://electricsheep.org for more information. This is version 2.6.8.
TryExec=esheep.sh
Exec="esheep.sh"
StartupNotify=false
Terminal=false
Type=Application
Categories=Screensaver
```

**Step 9:**
gnome-screensaver resets every 10 minutes as part of the random selection - even if random isn't chosen.  We need to change that to a larger number, otherwise nothing will render or download properly.
```
gconftool-2 --type int --set /apps/gnome-screensaver/cycle-delay 10000
```

**Step 10:**
System->Preferences->Power Management: Change the setting to put the display to sleep when inactive to 'Never' by dragging the bar all the way to the right.  Alternatively, 
```
gconftool-2 --type int --set /apps/gnome-power-manager/ac_sleep_display 0
```

**Step 11:**
Open the gnome-screensaver selection dialog, pick electricsheep, and enjoy.  It might take some time to get a sheep, so be patient.  If you want to test it, you can download individual sheep from the electricsheep website and place them in your sheep storage directory.

Let me know how this works!

---

### Post by frodon on 2007-02-08
There's another guide on this topic there for those who wish a repository to install it :
[http://ubuntuforums.org/showthread.php?t=350089](http://ubuntuforums.org/showthread.php?t=350089)

---

### Post by sciurus on 2007-02-09
If you're running Edgy the electricsheep package is at 2.6.8-2, so there is no need to build from source. Just create the esheep.sh and electricsheep.desktop files.

[https://bugs.launchpad.net/ubuntu/+source/electricsheep/+bug/5823](https://bugs.launchpad.net/ubuntu/+source/electricsheep/+bug/5823)

---

### Post by pensador82 on 2007-02-10
Hi, I'm getting the following error:

```
/electricsheep-2.6.8$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
/electricsheep-2.6.8$ make clean all
make: *** No rule to make target `clean'.  Stop.

```

How can I fix this?
As you see, I'm new to Linux.

---

### Post by Jojo12a on 2007-02-10
I suppose that you haven't satisfied all build depencies from the first post ;)... I think that the deps from above, plus build-essential, checkinstall and gcc should be enough to build it... if they are all there, please post the contents of config.log.

---

### Post by EReckase on 2007-02-10
According to this, you might need the binutils package:

[http://www.geektimes.com/linux/troubleshooting/c-cant-create-executables.html]("http://www.geektimes.com/linux/troubleshooting/c-cant-create-executables.html")

---

### Post by Triorph on 2007-02-13
Hey, firstly i absolutely love this screensaver, but sadly i haven't been able to get it working in a screensaver state, when run as it is (no options) i get this error

```
 
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  106
  Current serial number in output stream:  106
Terminated

```

so i have been using the --mplayer 1 tag in initialising it for things like xwinwrap etc.. however i was quite interested in getting this to work for your guide, however i have tried following this guide to the letter (using source tarball, commenting out makefile lines, etc..) but in the end "ElectricSheep" still doesn't show up in gnome-screensaver. Any idea why this would be?

---

### Post by EReckase on 2007-02-13
These instructions are only for Dapper - Edgy has a different set of rules.  I'll see if I can drum up a solution for Edgy.

Erik

---

### Post by EReckase on 2007-02-20
> **Triorph said:**
> 
so i have been using the --mplayer 1 tag in initialising it for things like xwinwrap etc.. however i was quite interested in getting this to work for your guide, however i have tried following this guide to the letter (using source tarball, commenting out makefile lines, etc..) but in the end "ElectricSheep" still doesn't show up in gnome-screensaver. Any idea why this would be?

Try putting the file from step 6 into /usr/share/applications/screensavers.

---

### Post by EReckase on 2007-02-20
I added a gconftool-2 call and a slightly different script to make this work better and not spawn multiple instances of the screensaver every 10 minutes...hope this helps.

Erik

---

### Post by steeef on 2007-03-18
I can't seem to get Electric Sheep working in Edgy. I've followed the instructions in this link:
[https://bugs.launchpad.net/ubuntu/+source/electricsheep/+bug/5823](https://bugs.launchpad.net/ubuntu/+source/electricsheep/+bug/5823)

Manually running electricsheep with the arguments used in esheep.sh works if I leave out "--root 1", but I can't get anything but a blank screen when the screensaver runs. If I leave out "--root 1" in the script, I still get a blank screen, but after typing in my password to unlock the screen, I can see the sheep playing.

Here's my esheep.sh currently:
#!/bin/sh
electricsheep --root 1 --nick <mynick> --max-megabytes 500 --zoom 1 --display-anim 1 --show-errors 0 --nrepeats 2 --frame-rate 30 --mplayer 1

---

### Post by steeef on 2007-03-25
I gave up trying to get gnome-screensaver to run this and switched to xscreensaver, as Electric Sheep is the only screensaver I really care about running anyway.

---

### Post by blithe on 2007-03-28
> **steeef said:**
> I can't seem to get Electric Sheep working in Edgy. I've followed the instructions in this link:
[https://bugs.launchpad.net/ubuntu/+source/electricsheep/+bug/5823](https://bugs.launchpad.net/ubuntu/+source/electricsheep/+bug/5823)

Manually running electricsheep with the arguments used in esheep.sh works if I leave out "--root 1", but I can't get anything but a blank screen when the screensaver runs. If I leave out "--root 1" in the script, I still get a blank screen, but after typing in my password to unlock the screen, I can see the sheep playing.

Here's my esheep.sh currently:
#!/bin/sh
electricsheep --root 1 --nick <mynick> --max-megabytes 500 --zoom 1 --display-anim 1 --show-errors 0 --nrepeats 2 --frame-rate 30 --mplayer 1

I've been having this problem too. I googled high and low and it appears to be an Ubuntu specific package. ElectricSheep seems to run fine until I run mplayer or VLC or some other video player, then it gives me the black screen everytime ElectricSheep starts.

Very strange indeed, I kind of gave up on fixing it for the moment. :(

---

### Post by muguwmp67 on 2007-03-28
Try taking off the -mplayer 1 portion, I think it was buggy for me too.

After stripping off  the stuff that I didn't need, my xscreensaver settings look like this:

```
electricsheep --root 1 --nick mugwump67 --zoom 1 --max-megabytes 5000.
```

---

### Post by andydude on 2007-05-18
Hi, I found the above tutorial very helpful in general, but it was very bad with respect to the installation of the script. I eventually found that this /usr/lib/xscreensaver did not exist on Debian-7.04, but I did find that the other screensavers are usually found in /usr/lib/gnome-screensaver/gnome-screensaver so I eventually installed my esheep.sh script in /usr/lib/gnome-screensaver/gnome-screensaver/esheep.sh and that is what finally made it work, I also customized the command-line options, but realized the most important one is "--root 1", just to let you know!

---

### Post by olavjunior on 2007-08-18
This didn't work out at all for me. First of all I didn't have any themes-folder, so I created one. 
Second, I tried the tip above to move it to gnome-screenserver folder instead (though I had the xscreenserver folder). That didn't help eighter. The sheep didn't show up in gnome sreensavers. But suddently my system hung completely, and I had to make a total system power kill. First thing I did afterwards was to remove everything from esheep!.. It sounds like a resource-killer anyway

---

### Post by fatlotus on 2007-10-18
You know, in Fiesty and up, electricsheep is an APT package: you can just do:```

sudo apt-get install electricsheep
```

---

### Post by steeef on 2007-10-21
Yup, once it's downloaded sheep, the Electric Sheep package from Synaptic works like a charm. I was skeptical at first, but as I was running Xubuntu, I first needed to add gnome-screensaver to my autostarted applications.

It's nice to finally have a trouble-free installation of this screensaver.

---

### Post by nageekdoog on 2008-04-19
Hey all

I followed this process and all I get is a black screen as if esheep can't find its sheep. I downloaded a pack of Sheep from the esheep site and placed them into the folder that I designated for them. Does the sheep-holding folder have to be in a specific place? I have mine on the desktop. I also went back and checked through the files esheep.sh and electricsheep.desktop and they were fine, according to this walkthrough.

thanks in advance.

---

### Post by Mr. Svinlesha on 2008-05-16
Add my name to the list of people who 1) love electric sheep (not in the carnal sense, of course) and 2) can't get it to work with my installation of Hardy Heron.

Can anyone out there help us out?

---

### Post by EReckase on 2008-05-16
By work, do you mean as a screensaver, or interactively?  That is, can you run the electricsheep program and get a smaller window?

---

### Post by Mr. Svinlesha on 2008-05-16
I meant as a screensave.  I used *sudo apt get* to retreive the program, and it's listed among my screensavers, but when I select it, I get nothing but a black screen.

---

### Post by EReckase on 2008-05-16
We're working on the new version of the screensaver right now - that package has not really been tested with Hardy (from what I understand.)

I'll try to get that package and see what's going on with it.  It might be worth creating a new thread since this one is for Dapper...

---

### Post by Mr. Svinlesha on 2008-05-16
Really? Cool!

Who's "we?"

---

### Post by EReckase on 2008-05-16
I work with Scott Draves on the flame code and the screensaver (I'm the current flam3 render code maintainer).  If you'd like to try the beta version of the screensaver to help us do debugging and such, and feel comfortable compiling it yourself, have a look [here]("http://draves.org/blog/archives/000526.html") for instructions on installing it.

---

### Post by Mr. Svinlesha on 2008-05-16
You guys are great.  I have a dual boot system and have been using electric sheep in Windows for years now, and it's absolutely fantastic.  I'm one of your biggest fans!

:)


Anyway, I'd really be glad to help, but I've never compiled in my life.  I'm just a beginner, especially with Linux.  But I'll take a look, and if there's anything a layman can do to help -- documentation or what not -- I'd be glad to lend a hand.

---

### Post by spotspot on 2008-05-16
the tarball on that blog post is old, you should use the latest from cvs.  there will be a new beta release shortly with a new tarball.

---

### Post by spotspot on 2008-05-16
> **Mr. Svinlesha said:**
> You guys are great.  I have a dual boot system and have been using electric sheep in Windows for years now, and it's absolutely fantastic.  I'm one of your biggest fans!

:)


Anyway, I'd really be glad to help, but I've never compiled in my life.  I'm just a beginner, especially with Linux.  But I'll take a look, and if there's anything a layman can do to help -- documentation or what not -- I'd be glad to lend a hand.

Thank you Mr Svinlesha, that's great to hear :)  When I write the blog post I'll be really clear so you should be able to try it out, and if you have any problems we can go over it here or on the electric sheep forum.

---

### Post by Mr. Svinlesha on 2008-05-16
Okay.  Just let us know when you're ready...PM me or post to this thread.  I'll try to keep an eye out.

Tim

---

### Post by spotspot on 2008-05-16
ok try this: [http://community.electricsheep.org/node/237](http://community.electricsheep.org/node/237)

---

### Post by EReckase on 2008-06-27
Note that there is now a Launchpad repository with binaries for the flam3 and electricsheep packages.  Simply add this line to sources.list (or to the repository list in synaptic)

deb [http://ppa.launchpad.net/flam3/ubuntu](http://ppa.launchpad.net/flam3/ubuntu) hardy main

--Erik

---

### Post by nerd2.0 on 2008-08-09
pensador82, I had the same error. I fixed it by typing both the commands in the same line. Try this:

$ ./configure make clean all

---

### Post by ario on 2009-06-12
Hi
I installed this by adding its repositories to my synaptic. and then running the script provided in its website. then signed up in [www.electricsheep.org](www.electricsheep.org) and choosed a username and password. entered my username and password in preferences windows of this screen saver by running **electricsheep-preferences** command. Then entered **electricsheep** wait about 5 minute by a 128kb dsl line and then it worked like a charm:p
But I don't know how much it will download from internet. cause  internet traffic is too expensive here.:(
Is there a way to set it to offline downloading mode? So then I can manage it when to download and when not.

---

### Post by jakswa on 2009-07-06
ario:  In the man page ("man electricsheep"), it says you can set the "standalone" option when you start, and it won't connect to the internet at all, just play what you have downloaded:  *electricsheep --standalone 1*

Count me in as unsuccessful at getting electricsheep to start or work...
started with this error and then a 404:  "could not scan gen"
tried downloading a few sheep manually and putting them in ~/.sheep

No success :(  just a blank screen on screensaver.

---

### Post by EReckase on 2009-07-06
Note that there are no Jaunty packages yet...are you using the version from the PPA?  Can you post what it says when you add --debug 1 to the command-line options?

Erik

---

### Post by spotspot on 2009-09-10
Now in Debian Sid:

[http://packages.debian.org/sid/electricsheep](http://packages.debian.org/sid/electricsheep)

How do we get these into Ubuntu?

---

### Post by kabeza on 2010-01-06
hi people
Can any1 tell me why I can only see this screen in my screensaver properties?
I also see this screen when screensaver activates... 

[http://img693.imageshack.us/img693/282/screenshot004n.png](http://img693.imageshack.us/img693/282/screenshot004n.png)

TIA

---

### Post by ario on 2010-01-07
> **kabeza said:**
> hi people
Can any1 tell me why I can only see this screen in my screensaver properties?
I also see this screen when screensaver activates... 

[http://img693.imageshack.us/img693/282/screenshot004n.png](http://img693.imageshack.us/img693/282/screenshot004n.png)

TIA

I think you must only follow the the message prompted in screensaver window. First register at the site linked and then enter you username and password in configuration window of this screen saver.

---

### Post by kabeza on 2010-01-07
> **ario said:**
> I think you must only follow the the message prompted in screensaver window. First register at the site linked and then enter you username and password in configuration window of this screen saver.

I'm registered already.
What I don't see is the configuration window of the screensaver. How should I access it?

---

### Post by DJ_Peng on 2010-01-07
There is an Electricsheep Preferences dialog that you can access by running this in a terminal
```
electricsheep-preferences
```
It will get you this screen, although I'm not sure if it's what you're looking for.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=142775&stc=1&d=1262876342[/IMG]

---

### Post by kabeza on 2010-01-08
@DJ_Peng
Yes, that's what I was looking. I could configure the preferences. They were blank, but anyway. I can't see anything yet.
I don't know why the preview doesn't show anything, it only shows that black screen with logo & message that suggests registering, etc.

[IMG]http://img218.imageshack.us/img218/1439/screenshot005h.png[/IMG]

---

### Post by DJ_Peng on 2010-01-08
That's odd because I definitely have a preview in my Screensaver window. I never saw anything about registering it though. Where did you install it from?

---

### Post by kabeza on 2010-01-08
> **DJ_Peng said:**
> ...Where did you install it from?

wow, that's a good question. I guess I've installed from Ubuntu software center, it didn't work. Then I think I got some .sh file, don't remember from where, and then I guess that thing make it to install...

What would you recommend me to do? Maybe uninstalling everything and reinstalling again correctly can solve this...?

---

### Post by spotspot on 2010-01-10
Currently the best way to get it is by following the instructions on the home page: [http://community.electricsheep.org/node/51](http://community.electricsheep.org/node/51)

You should remove any package you have installed, and then follow the above instructions.

You don't have to register, but sometimes it does take a long time to load.  you can either be patient (try letting it run overnight), or use a sheep pack to kick-start it.

See our forum for more info, I don't read here very often.

---

### Post by kabeza on 2010-01-12
I've executed the makesheep.sh but seems there's a trouble with the latest steps... I get this output...

[http://justpaste.it/xp](http://justpaste.it/xp)

However, I can access and browse the urls... I don't know why terminal throws these errors
I guess I've to try to install these two things manually, right?

---

### Post by finlost on 2010-01-30
This app looks neat.  Keyword is "looks".  It doesn't work in 9.10 and I am not going to spend a week scouring the Internet looking for a solution.  The link spotspot provided to install via terminal results in an error during the installation.

---

### Post by Stason on 2010-02-21
How do I limit the time electricsheep runs for? It seems to disable power savings settings on my machine somehow. I have a plasma and I need it to turn off in 20 minutes or so.

---

