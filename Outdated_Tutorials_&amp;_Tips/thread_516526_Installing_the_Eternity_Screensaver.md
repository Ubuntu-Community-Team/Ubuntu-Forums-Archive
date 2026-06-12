---
title: "Installing the Eternity Screensaver"
date: 2007-08-03
forum: Outdated Tutorials &amp; Tips
---

### Post by parker13 on 2007-08-03
The Eternity Screensaver Project ([http://launchpad.net/eternity](http://launchpad.net/eternity)) is a new screensaver which displays animations of raytraced scenes. There are a number of plugins including an Eternal Ubuntu animation featuring a spinning Ubuntu logo. Packages are available either from an online APT repository or by installing the .deb files directly. The packages have been tested under both Gnome and KDE. They also work if you're running Beryl/Compiz.

[img]http://parker1.co.uk/eternity/screenshots/_thb_eternalubuntu.png[/img]

Here's a video showing the Eternal Ubuntu plugin:
[http://video.google.com/videoplay?docid=3522833444734552124](http://video.google.com/videoplay?docid=3522833444734552124)

[img]http://parker1.co.uk/eternity/screenshots/_thb_pentagram.png[/img]
There's also an Ubuntu Satanic Edition plugin featuring 3 animations:
[http://video.google.com/videoplay?docid=-5223711495134257826](http://video.google.com/videoplay?docid=-5223711495134257826)

Full installation instructions are available at:
[http://parker1.co.uk/eternity/download.php](http://parker1.co.uk/eternity/download.php)

...but here's a quick HOWTO:


Using APT
1. Add the repository:
Edit your APT sources file:
```
sudo gedit /etc/apt/sources.list
```

Add the following lines to the end:
```

# Eternity Screensaver
deb http://ppa.launchpad.net/eternity/ubuntu feisty main
deb-src http://ppa.launchpad.net/eternity/ubuntu feisty main

```
Note: change feisty to gutsy if you're using Ubuntu 7.10

2. Install the packages
To install the screensavers:
```

sudo apt-get update
sudo apt-get install eternal-ubuntu

```

Note that you will get the following error during the installation:
```

WARNING: The following packages cannot be authenticated!
  eternity-screensaver
Install these packages without verification [y/N]? y

```
This is because Launchpad's PPA service does not currently support package signing (see [https://bugs.edge.launchpad.net/soyuz/+bug/125103](https://bugs.edge.launchpad.net/soyuz/+bug/125103)).

For the Ubuntu Studio plugin, use:
```

sudo apt-get install eternal-studio

```

For the Ubuntu Satanic Edition plugin, use:
```

sudo apt-get install eternal-damnation

```

3. Select the screensaver
Run the Screensaver selection tool:
  * Gnome: System->Preferences->Screensaver
  * KDE: Right-click the desktop and select "Configure Desktop..." 

The screensavers are called Eternity, Eternal Ubuntu, Eternal Ubuntu Studio and Eternal Damnation.


Installing from Packages
If you don't want to use the APT repository, you can just download the individual packages. See [http://parker1.co.uk/eternity/download.php](http://parker1.co.uk/eternity/download.php) for links to these.


Any questions or problems, please let me know.

Also, if you have any animations to contribute I'd be glad to hear from you.

Thanks,
Garry.

---

### Post by parker13 on 2007-08-05
Just to be clear, I'm the author of the screensaver and the Ubuntu packages, so I'll be happy to give support you require. Thanks!

---

### Post by fooman on 2007-08-05
i like 'em both!  :)

thanks!

---

### Post by virtualcourtney on 2007-08-06
Will these work with xscreensaver?

---

### Post by parker13 on 2007-08-06
In theory, yes. All the config is there for xscreensaver.

However, I've never tested it myself. If you'd like to give it a try I'd appreciate the feedback.

---

### Post by virtualcourtney on 2007-08-06
Well, it doesn't show up in xscreensaver by default (though it's there in gnome-screensaver).  I don't know too much about getting it to appear, but I'll play around a bit and see what I can dig up.

---

### Post by johnl on 2007-08-06
I installed the amd64 version on my system, but there are no graphics -- the screen just goes black (both in the preview and when the screen saver actually triggers) .

This happens with both the eternity and eternal-ubuntu screensavers.

I'm using the nvidia-glx-new driver, and the black screen happens both with beryl running and without.

---

### Post by parker13 on 2007-08-06
> **virtualcourtney said:**
> Well, it doesn't show up in xscreensaver by default (though it's there in gnome-screensaver).  I don't know too much about getting it to appear, but I'll play around a bit and see what I can dig up.

OK, thanks for trying. Looks like I'll have to bite the bullet and install xscreensaver to get it working.

---

### Post by parker13 on 2007-08-06
> **johnl said:**
> I installed the amd64 version on my system, but there are no graphics -- the screen just goes black (both in the preview and when the screen saver actually triggers) .

This happens with both the eternity and eternal-ubuntu screensavers.

I'm using the nvidia-glx-new driver, and the black screen happens both with beryl running and without.

Thanks for giving it a try. I'm really sorry that you've had problems - this is pretty new software and Ubuntu just has so many variants! I wonder if this is an amd64 specific problem. 

By the way, the projects are registered on launchpad. I'll raise these bugs there. If anyone else wants to raise bugs against the screensaver, the URL is:

[https://launchpad.net/eternity/+filebug](https://launchpad.net/eternity/+filebug)

The project pages are:
[https://launchpad.net/eternity](https://launchpad.net/eternity)
[https://launchpad.net/eternal-ubuntu](https://launchpad.net/eternal-ubuntu)
[https://launchpad.net/eternal-damnation](https://launchpad.net/eternal-damnation)

---

### Post by parker13 on 2007-08-06
OK, the bugs have been raised. 

[https://bugs.launchpad.net/eternity/](https://bugs.launchpad.net/eternity/)

Thanks again for your participation!

---

### Post by johnl on 2007-08-06
> **parker13 said:**
> OK, the bugs have been raised. 

[https://bugs.launchpad.net/eternity/](https://bugs.launchpad.net/eternity/)

Thanks again for your participation!


I did a little exploring and solved the problem.

The bash scripts in /usr/lib/gnome-screensaver/gnome-screensaver/ were looking for eternity-mpeg2 in /usr/bin when eternity-mpeg2 had been installed in /usr/local/bin.

fixing this causes the screensaver to work correctly.

---

### Post by parker13 on 2007-08-07
> **johnl said:**
> I did a little exploring and solved the problem.

The bash scripts in /usr/lib/gnome-screensaver/gnome-screensaver/ were looking for eternity-mpeg2 in /usr/bin when eternity-mpeg2 had been installed in /usr/local/bin.

fixing this causes the screensaver to work correctly.

Fantastic! Thanks for that.

It must be to do with the chroot environment I'm using to compile for amd64. I'll get a fixed package out soon.

---

### Post by fooman on 2007-08-07
i *really* like the beginning of the eternity-damnation saver (the red part).  kinda wish they were 3 different screensavers from that one.

oh well,  i jgrabbed the 3 mpg files from [_here_]("http://parker1.co.uk/eternity/eternal-damnation.php"), then used the media screensaver plugin for kscreensaver and that works great!  :)

nice work...thanks again

---

### Post by raijinsetsu on 2007-08-07
Not to be a nitpicker, but, do you think it's ok to have a static image(the background) on a screensaver? I'm talking about the Eternity version in particular.
Modern CRTs still have burn-in, and I think LCDs do to(although it takes a very long time). *shrugs* Personally, it wouldn't affect me because my screensaver kicks in after 5 mins, and the screen goes to standby after 15 mins...

---

### Post by hikaricore on 2007-08-07
Very nice.  ^_^

---

### Post by parker13 on 2007-08-07
> **raijinsetsu said:**
> Not to be a nitpicker, but, do you think it's ok to have a static image(the background) on a screensaver? I'm talking about the Eternity version in particular.
Modern CRTs still have burn-in, and I think LCDs do to(although it takes a very long time). *shrugs* Personally, it wouldn't affect me because my screensaver kicks in after 5 mins, and the screen goes to standby after 15 mins...

It is a good point, but the intention is to add other animations to each plugin, so the background will change periodically.

Anyway, this is art, man!

---

### Post by parker13 on 2007-08-07
> **johnl said:**
> I did a little exploring and solved the problem.

The bash scripts in /usr/lib/gnome-screensaver/gnome-screensaver/ were looking for eternity-mpeg2 in /usr/bin when eternity-mpeg2 had been installed in /usr/local/bin.

fixing this causes the screensaver to work correctly.

Version 0.2 of the screensaver and plugins are now available on the site:

[http://parker1.co.uk/eternity/download.php](http://parker1.co.uk/eternity/download.php)

It should now work correctly for amd64 and also under Xscreensaver.

---

### Post by Skrypt on 2007-08-07
Great screensavers (minus the burning pentagram, :)) but I cannot get them to properly display across 2 monitors using TwinView. Any ideas / suggestions?

---

### Post by parker13 on 2007-08-08
> **Skrypt said:**
> Great screensavers (minus the burning pentagram, :)) but I cannot get them to properly display across 2 monitors using TwinView. Any ideas / suggestions?

Hi Skrypt,

First of all, if you don't like the pentagram, you can edit the following config file and remove the pentagram line:

```
/usr/share/eternity-screensaver/damnation/eternity.cfg
```

...same goes for other tweaks such as how many times each animation repeats and the number of frames per seconds etc. There's one config file per plugin.

Regarding twinview, this screensaver's media player is based on the one shipped with  electricsheep. I've had a look and there's a twinview patch available, so I'll take a look at incorporating it. Bit tricky for me to test, though...

---

### Post by Pheodax on 2007-08-08
I really really like the screensavers. You did a fantastic job. Installing was extremely easy and the screensavers are just amazingly good looking.

Thanks a lot and keep up the good work!!! :D

---

### Post by owenll on 2007-08-08
Thank you for the screensaver - fantastic workand easy to install (x64). :)

---

### Post by Skrypt on 2007-08-08
> **parker13 said:**
> Hi Skrypt,

First of all, if you don't like the pentagram, you can edit the following config file and remove the pentagram line:

```
/usr/share/eternity-screensaver/damnation/eternity.cfg
```

...same goes for other tweaks such as how many times each animation repeats and the number of frames per seconds etc. There's one config file per plugin.

Sweet! Thanks!
> 
Regarding twinview, this screensaver's media player is based on the one shipped with  electricsheep. I've had a look and there's a twinview patch available, so I'll take a look at incorporating it. Bit tricky for me to test, though...
If you want, you can e-mail them to me and I'll test it and work with you to get it up and running on TwinView.

---

### Post by parker13 on 2007-08-08
> **Skrypt said:**
> Sweet! Thanks!

If you want, you can e-mail them to me and I'll test it and work with you to get it up and running on TwinView.

Great. I'll work on the patch and send you a beta package.

...and thanks to everybody for the great feedback!

---

### Post by Pheodax on 2007-08-12
> **parker13 said:**
> Great. I'll work on the patch and send you a beta package.

...and thanks to everybody for the great feedback!
I use TwinView all the time, so if you need a second tester feel free to PM me. I'll be happy to help.

---

### Post by krandun on 2007-09-12
I'm running Feisty 7.04. I have installed Eternity, Eternal Damnation, and Eternal Ubuntu packages, then completely removed and re-installed them and I'm still having the same problem.
When the screensaver becomes active, it blanks the entire screen, but only shows the moving video in the upper left corner, about 1/4 of the screen. I don't think that it's scaling at all, I can see more than in the preview in Gnome Screensaver, but it's not full screen.
Am I missing a required package somewhere or something? These look really cool, and I would like to get it working.

---

### Post by parker13 on 2007-09-14
> **krandun said:**
> I'm running Feisty 7.04. I have installed Eternity, Eternal Damnation, and Eternal Ubuntu packages, then completely removed and re-installed them and I'm still having the same problem.
When the screensaver becomes active, it blanks the entire screen, but only shows the moving video in the upper left corner, about 1/4 of the screen. I don't think that it's scaling at all, I can see more than in the preview in Gnome Screensaver, but it's not full screen.
Am I missing a required package somewhere or something? These look really cool, and I would like to get it working.

Hi Krandun,

First of all - do you have dual monitors? This is known to cause a problem. If not, what graphics card, monitor and xorg driver are you using? Posting your /etc/X11/xorg.conf may be useful.

Thanks!

---

### Post by Ripfox on 2007-09-14
Kick A** screensavers my friend...thanks!

---

### Post by zen_buddah on 2007-09-14
hullo im running the ubuntu-ultimate live cd...  followed your instuctions...  and they all installed/worked perfectly!!! :)
lovley screen savers !!! bloody marvelous !!

---

### Post by hikaricore on 2007-09-14
Are these always going to be premade animations or do you plan to move to an actual opengl screensaver eventually?

Just curious.

---

### Post by parker13 on 2007-09-14
> **hikaricore said:**
> Are these always going to be premade animations or do you plan to move to an actual opengl screensaver eventually?

Just curious.

First of all, thanks for all the positive feedback, guys.

Regarding the question "do I plan an actual OpenGL screensaver", the answer is a definite "no". My view is that it should be possible to get better effects using raytracing than OpenGL. I'm currently rendering some new Ubuntu POV Ray animations and they're taking 4 days on an Athlon64 X2 6000+ for a 30 second clip... even with accelerated graphics hardware you're not going to be able to render anything like it on-the-fly.

The plan is to continue adding new raytraced animations. If anybody would like to submit any I'd be very grateful. Other than that, it might be interesting to create some kind of distributed screensaver to render the images - much like electricsheep.

I'm on holiday for a week, but when I get back I'll be releasing some new packages with more animations. Plus I'll hopefully be moving the repository to Lauchpad PPA.

Thanks again.

---

### Post by krandun on 2007-09-14
> **parker13 said:**
> Hi Krandun,

First of all - do you have dual monitors? This is known to cause a problem. If not, what graphics card, monitor and xorg driver are you using? Posting your /etc/X11/xorg.conf may be useful.

Thanks!
Single monitor. Laptop, in fact. Sorry I forgot to mention that.

Section "Device"
        Identifier      "ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
        Driver          "fglrx"
        Option "Capabilities" "0x00000800"
        Option "UseFastTLS" "2"
        Option "KernelModuleParm" "locked-userpages=0"
        Busid           "PCI:1:0:0"
EndSection

---

### Post by parker13 on 2007-09-15
> **krandun said:**
> Single monitor. Laptop, in fact. Sorry I forgot to mention that.

Section "Device"
        Identifier      "ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]"
        Driver          "fglrx"
        Option "Capabilities" "0x00000800"
        Option "UseFastTLS" "2"
        Option "KernelModuleParm" "locked-userpages=0"
        Busid           "PCI:1:0:0"
EndSection

Hi Krandun,

Weird... I'm writing this on a laptop with the exact same graphics card as you, and also running the fglrx driver, and it works fine! What resolution are you running at? Mine only does 1024x768.

---

### Post by krandun on 2007-09-15
I'm running at 1280x800, but I just switched to 1024x768 and tried the screensaver again. Same problem.

---

### Post by Jawsman on 2007-09-15
Very clear tutorial and great screensavers!
thanksss

---

### Post by jr.gotti on 2007-09-19
Just would like to point out the fact that these won't work while Compiz/Beryl is running. At least not for me. Other than that, excellent man! You used POV-Ray for them? I used to be big on that...stopped a long time ago tho.

---

### Post by i M@N on 2007-09-21
Hello.

w00t w00t w00t ! that roxX !!

Many thnxX 4 this very nice screensaver (the Ubuntu one).
Respect.

@+...

---

### Post by parker13 on 2007-09-22
> **jr.gotti said:**
> Just would like to point out the fact that these won't work while Compiz/Beryl is running. At least not for me. Other than that, excellent man! You used POV-Ray for them? I used to be big on that...stopped a long time ago tho.

Hi jr.gotti,

I've tested them using both Beryl and Compiz Fusion and on a number of machines and they work fine, so I'm a bit concerned by the problems your having...

I did use POV-Ray, with a bit of help from KpovModeler in some areas.

---

### Post by g14 on 2007-09-22
Very nice. Great job!

Edit:
On my Lenovo Thinkpad T60, I run compiz-fusion on gutsy and just installed the eternity-ubuntu screensaver. When previewing it from the gnome-screensaver dialog, it works perfect. When locking the screen (which I set to call gnome-screensaver-command --lock), it just fades to black and doesn't show up. On my desktop with an Nvidia geforce 5200  running compiz-fusion + gutsy this works perfectly in both areas.

Thoughts?

---

### Post by nuclearj on 2007-09-22
Those are awesome screensavers, Parker13.  These should be default ones for the next Ubuntu release!  Great job and we look further to more.

---

### Post by parker13 on 2007-09-24
> **g14 said:**
> Very nice. Great job!

Edit:
On my Lenovo Thinkpad T60, I run compiz-fusion on gutsy and just installed the eternity-ubuntu screensaver. When previewing it from the gnome-screensaver dialog, it works perfect. When locking the screen (which I set to call gnome-screensaver-command --lock), it just fades to black and doesn't show up. On my desktop with an Nvidia geforce 5200  running compiz-fusion + gutsy this works perfectly in both areas.

Thoughts?

Thanks for that. It seems that a few people are having issues running Eternity with certain laptops and compiz/beryl. It's maybe a problem with the ATI driver, but some laptops with ATI cards work fine.

The player which Eternity uses is based on the one in electricsheep, and as far as I can tell, these problems affect electricsheep, also.

I've raised a bug on Launchpad:

[https://bugs.edge.launchpad.net/eternity/+bug/144405](https://bugs.edge.launchpad.net/eternity/+bug/144405)

---

### Post by parker13 on 2007-10-02
This tutorial has been edited to reflect the fact that the repositories have been moved to Launchpad PPA. The old repo is still available, but to get the updates, including the new Ubuntu Logo animations and Ubuntu Studio plugin, you'll need to use the new Launchpad repository.

Full details at [http://parker1.co.uk/eternity/](http://parker1.co.uk/eternity/)

---

### Post by dante00001 on 2007-11-03
Great work man! Worked perfect on my Gutsy box (compiz-fusion). Thank you so much making these.

---

### Post by ezramorris on 2008-05-28
Hi, I'm running it on a desktop with an ATI graphics card, running compiz. When I click preview, I also get a blank screen.

Thanks.

---

### Post by ranger_cole on 2008-05-28
> **parker13 said:**
> This tutorial has been edited to reflect the fact that the repositories have been moved to Launchpad PPA. The old repo is still available, but to get the updates, including the new Ubuntu Logo animations and Ubuntu Studio plugin, you'll need to use the new Launchpad repository.

Full details at [http://parker1.co.uk/eternity/](http://parker1.co.uk/eternity/)
I am using dell optiplex 755 uses ati card.  I tried this [http://parker1.co.uk/eternity/](http://parker1.co.uk/eternity/) and get nothing on the previews on any of the eternity screensavers.  Any ideas?

---

### Post by parker13 on 2008-05-30
The solution described in the following bug report is known to fix issues with ATi graphics cards:

[https://bugs.edge.launchpad.net/eternity/+bug/148437](https://bugs.edge.launchpad.net/eternity/+bug/148437)

I'd be interested to know if it works for you.

---

### Post by ezramorris on 2008-05-30
> **parker13 said:**
> The solution described in the following bug report is known to fix issues with ATi graphics cards:

[https://bugs.edge.launchpad.net/eternity/+bug/148437](https://bugs.edge.launchpad.net/eternity/+bug/148437)

I'd be interested to know if it works for you.

Thanks very much. This worked great!

---

### Post by parker13 on 2008-05-31
Thanks for the feedback.

I've added a new page on the site to help others who encounter this problem:

[http://parker1.co.uk/eternity/troubleshooting.php](http://parker1.co.uk/eternity/troubleshooting.php)

---

### Post by ezramorris on 2008-05-31
> **parker13 said:**
> Thanks for the feedback.

I've added a new page on the site to help others who encounter this problem:

[http://parker1.co.uk/eternity/troubleshooting.php](http://parker1.co.uk/eternity/troubleshooting.php)

Any idea why this happens/why the fix works? It worked without the fix on my laptop with ATI graphics, but on my desktop with ATI, I had to apply the fix.

Also, is turning OpenGLOverlay off likely to prevent anything else from working?

---

### Post by alexsabree on 2008-05-31
How do I get this to work for fiesty (where is the repo)?

---

### Post by themuddler on 2008-06-01
Really like it, thanks very much!

A couple of questions to satisfy my curiosity if you don't mind.

1. Do the mpegs require some special codec as I can't seem to play them with vlc or totem?

2. Are there any high-definition versions available (for our HDTV which acts as my second monitor) or were they raytraced at this resolution?

Once again, well done on a cool screensaver.:)

---

### Post by ezramorris on 2008-06-01
> **themuddler said:**
> 1. Do the mpegs require some special codec as I can't seem to play them with vlc or totem?


I couldn't get it to play with either of these, but I could get it to play with mplayer, and hence encode it to something else.

Interestingly, it picks up the video codec as '¬', which seems rather odd.

---

### Post by ezramorris on 2008-06-01
> **alexsabree said:**
> How do I get this to work for fiesty (where is the repo)?

Don't know about repos, but if you want you can download the debs manually at [http://parker1.co.uk/apt/dists/feisty/main/binary-i386/](http://parker1.co.uk/apt/dists/feisty/main/binary-i386/) (you want the .deb files - eternity-screensaver first.

---

### Post by parker13 on 2008-06-02
> **ezramorris said:**
> Any idea why this happens/why the fix works? It worked without the fix on my laptop with ATI graphics, but on my desktop with ATI, I had to apply the fix.

Also, is turning OpenGLOverlay off likely to prevent anything else from working?

Not sure why it works - it was posted on the Electric sheep forum and as Eternity uses a similar player the fix works for both.

As for whether it breaks anything, nobody has complained. I guess bear it in mind and you can always remove it if you find any problems.

---

### Post by parker13 on 2008-06-02
> **alexsabree said:**
> How do I get this to work for fiesty (where is the repo)?

The repo is in the same place - see here for instructions

[http://parker1.co.uk/eternity/download.php](http://parker1.co.uk/eternity/download.php)

Just change hardy for feisty.

Sorry, I should make than more clear.

---

### Post by parker13 on 2008-06-02
> **themuddler said:**
> Really like it, thanks very much!

A couple of questions to satisfy my curiosity if you don't mind.

1. Do the mpegs require some special codec as I can't seem to play them with vlc or totem?

2. Are there any high-definition versions available (for our HDTV which acts as my second monitor) or were they raytraced at this resolution?

Once again, well done on a cool screensaver.:)

The codec is MPEG2 PS. This is the same as used by Electric sheep (I modified their player as the basis for the screensaver). It's true that only mplayer will play them in this format.

The animations can be raytraced at any resolution. I've been working on a bespoke player which plays OGG Theora format files, allowing larger HD quality animations. It's a toss up between file size (for downloading), amount of CPU used during playback and the quality of the animation.

I'll post a link to the new code once it's finished if anybody would like to help beta-test.

Cheers,
Garry.

---

### Post by themuddler on 2008-06-02
> The codec is MPEG2 PS. This is the same as used by Electric sheep (I modified their player as the basis for the screensaver). It's true that only mplayer will play them in this format.

Aha, didn't try mplayer!

> The animations can be raytraced at any resolution. I've been working on a bespoke player which plays OGG Theora format files, allowing larger HD quality animations. It's a toss up between file size (for downloading), amount of CPU used during playback and the quality of the animation.

Sounds good and I understand it's a compromise. I am less concerned about size/cpu than some. Perhaps there's a market for a Lite version and an HD version but I appreciate it's some work. Seems like it could really catch on though!

> I'll post a link to the new code once it's finished if anybody would like to help beta-test.

I'll gladly help test.

---

### Post by jobbesat on 2008-09-07
I'm on an ati card (Radeon) and obviously it doesn't work, I tried adding those 2 lines on xorg.conf, but nothing. In case you have another possble solution, pleqse write it down here. Thanks a lot in advance

---

### Post by parker13 on 2008-09-08
> **jobbesat said:**
> I'm on an ati card (Radeon) and obviously it doesn't work, I tried adding those 2 lines on xorg.conf, but nothing. In case you have another possble solution, pleqse write it down here. Thanks a lot in advance

Actually, it usually works on Radeon cards without problems. It's only certain ones which require the two lines. Anyway, just to be clear, are you running the restricted drivers for your ATi card (System->Administration->Hardware Drivers)?

---

### Post by ellalan on 2008-09-08
Hi
I am having problem installing this "eternal-ubuntu". When I tried to install the package I get the message in the terminal "E:couldn't find the package eternal-ubuntu". I have attached the screen shot. Could someone please help me.
I am running Hardy Heron.
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) hardy-proposed/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Fetched 2B in 2s (1B/s)  
Reading package lists... Done
vignes@vignes-desktop:~$ sudo apt-get install eternal-ubuntu eternal-damnation eternal-studio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package eternal-ubuntu

---

### Post by parker13 on 2008-09-09
Hi,

The eternity screensaver isn't in the official Ubuntu repos. Please follow the instructions on the following page to add the repository and install:

[http://parker1.co.uk/eternity/download.php](http://parker1.co.uk/eternity/download.php)

Hope this helps,
Garry.

---

### Post by ellalan on 2008-09-09
Hi parker13
Thanks for the link and I have got them installed. Ubuntu eternal very nice.
Well done. Thanks again.

---

### Post by Berean on 2010-05-03
Fantastic!  Thanks for this, especially as it looks so good.

---

