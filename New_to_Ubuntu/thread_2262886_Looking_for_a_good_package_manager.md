---
title: "Looking for a good package manager"
date: 2015-01-28
forum: New to Ubuntu
---

### Post by garycheng12 on 2015-01-28
I am looking for a good package manager for Kubuntu. Base on what I've googled briefly, Synaptic Package Manager is a very powerful tool for Ubuntu. On Kubuntu, I checked out Muon but I can't find any options to manage packages other than uninstall and install--I can't view/fix dependencies, do upgrades, etc. Since "every package manager does not do the same thing," is Synaptic Package Manager still the most powerful package manager available for debian-based distros? I am new to Linux and there are so many Linux commands just to install/uninstall packages (clean, purge, remove, upgrade, etc.)--I just want a powerful GUI equivalent so I can visualize the process of it all. Also, I was wondering if package managers are used by even the most experienced of Linux users (for example, a package manager may not accomplish something that a command can). Do experienced Linux users avoid everything GUI because they can use the terminal efficiently?

---

### Post by Bucky Ball on 2015-01-28
Best way to find out is install Synaptics. If you don't like, uninstall. It's all I use (I run a mini install with only the apps I want so haven't used Software Centre in ages). Good luck. ;)

---

### Post by SeijiSensei on 2015-01-28
I just use apt and dpkg from the command line for upgrades and similar tasks.  I do use Synaptic on occasion (in KDE), but usually only to browse for new software.

---

### Post by vasa1 on 2015-01-28
> **SeijiSensei said:**
> I just use apt and dpkg from the command line for upgrades and similar tasks.  I do use Synaptic on occasion (in KDE), but usually only to browse for new software.

Can you explain how to use Synaptic to browse for new software? I Just looked through the menu options and didn't see anything obvious.

---

### Post by Bucky Ball on 2015-01-28
There is a search box. Just type in what you want to find. There are also categories (many) you can search through specifically.

---

### Post by newb85 on 2015-01-28
If I want to browse descriptions of available packages, I often use Software Center.  Otherwise, I usually stick to command-line.  It's been a couple years since I had Synaptic installed, but when I did, it was indeed a powerful tool.  I simply haven't needed it of late.  Still, I think it would be quite useful for most new users who want to go deeper than an app-store-style installation interface.

---

### Post by mastablasta on 2015-01-28
muon has two version. one is muon the other one is muon package manager. or at least it used to be like that.

---

### Post by kc1di on 2015-01-28
I use synaptic a lot and infact it's one of the first programs I install after a fresh install of any Ubuntu. 
if you want more package information go to settings >General tab and check the box next to "Show package properties in main window."
this : This will give you tabs with Description, Common, Dependencies and Installed files and Versions. 

Good Luck :)

---

### Post by ajgreeny on 2015-01-28
I also use synaptic all the time with the exception of occasional command line apt-get commands.

I started using Ubuntu in 2005 when synaptic was the default so I am very used to the way it is used; it is very powerful, and in my opinion is so much better than the software-center, which I have never ever used in those ten years of Ubuntu.  When I started using ubuntu I always installed the standard gnome 2 version and added kubuntu-desktop package to it, which I used quite a lot, but it was still always synaptic that I used for package management, even with the KDE desktop.

It is still the first package that I add to any install of any of the OSs that are derived from Ubuntu, including my current Xubuntu 14.04, and that is one situation where I have to use apt-get, ie, to install synaptic.  I also in synaptic preferences set it to carry out changes in terminal window as you can then see what is actually happening if you do that.

---

### Post by mikodo on 2015-01-28
Knowledgeable package management  is an integral part of administering an OS. Since you asked about experienced Linux users/admins, I am going to give you a link to read about it in Debian, for you to begin to learn more about it for Debian/Ubuntu. 

You should also search Ubuntu for more documentation.

[Debian package management]("https://www.debian.org/doc/manuals/debian-reference/ch02.en.html")

(An important question. I hope you continue in this vane, to learn more.)

---

### Post by Rob Sayer on 2015-01-28
I stopped using software center pretty quickly.  It's too slow and the user reviews aren't that helpful.

Synaptic is also what I'd recommend.  I use that or the terminal.

If I want to find a decent app I search here or askubuntu.  Blogs aren't necessarily useful either.  Some are good, others not.

If you look at one and a lot of the stuff they recommend for ubuntu involves adding a 3rd party ppa I'd definitely think that was a warning sign.  That stuff isn't beta tested by ubuntu and it can cause problems when updating.  Plus I know of very few instances where I couldn't find something as good or better in the tested repos.

---

### Post by SeijiSensei on 2015-01-28
I added a [Mozilla PPA]("https://launchpad.net/~mozillateam/+archive/ubuntu/firefox-next") today so I could try out Firefox beta with its support for [HTML5 video from YouTube]("http://news.slashdot.org/story/15/01/27/2217258/youtube-ditches-flash-for-html5-video-by-default").  I use a few other PPAs either from organizations like [LibreOffice]("https://launchpad.net/~libreoffice/+archive/ubuntu/ppa") or [VirtualBox](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions), or from individuals I've come to trust like [John Stebbins]("https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-snapshots").

---

### Post by ofnuts on 2015-01-28
> **mikodo said:**
> Knowledgeable package management  is an integral part of administering an OS. 

Me, I am very happy that there are package managers to handle that for me. This is one big selling point of modern distros over Windows IMHO.

---

### Post by ajgreeny on 2015-01-28
> **SeijiSensei said:**
> I added a [Mozilla PPA]("https://launchpad.net/~mozillateam/+archive/ubuntu/firefox-next") today so I could try out Firefox beta with its support for [HTML5 video from YouTube]("http://news.slashdot.org/story/15/01/27/2217258/youtube-ditches-flash-for-html5-video-by-default").  I use a few other PPAs either from organizations like [LibreOffice]("https://launchpad.net/~libreoffice/+archive/ubuntu/ppa") or [VirtualBox]("https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions"), or from individuals I've come to trust like [John Stebbins]("https://launchpad.net/~stebbins/+archive/ubuntu/handbrake-snapshots").
I also use several PPAs, and whilst I take everything that Rob says as a warning, I am pretty careful about adding PPAs and always look carefully into possible malware intrusions that a PPA could install.

Just for info, here's a list of those that I have enabled without any problems of any sort:-

[http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu](http://ppa.launchpad.net/mjblenner/ppa-hal/ubuntu)  #essential for Channel 4 TV catchup service here in UK.
[http://ppa.launchpad.net/osmoma/audio-recorder/ubuntu](http://ppa.launchpad.net/osmoma/audio-recorder/ubuntu)  #a super but simple audio recorder needing fewer resources than audacity.
[http://ppa.launchpad.net/jon-hedgerows/get-iplayer/ubuntu](http://ppa.launchpad.net/jon-hedgerows/get-iplayer/ubuntu)  #essential for BBC iPlayer recordings in UK.
[http://ppa.launchpad.net/tsbarnes/indicator-keylock/ubuntu](http://ppa.launchpad.net/tsbarnes/indicator-keylock/ubuntu)  #needed to show Caps-Lock status on laptop with no hardware indicator.
[http://plex.r.worldssl.net/PlexMediaServer/ubuntu-repo](http://plex.r.worldssl.net/PlexMediaServer/ubuntu-repo)  #added automatically when plex installed.
[http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu](http://ppa.launchpad.net/maarten-baert/simplescreenrecorder/ubuntu)  #a super but simple screenrecorder, like audio-recorder above.
[http://ppa.launchpad.net/libreoffice/ppa/ubuntu](http://ppa.launchpad.net/libreoffice/ppa/ubuntu)  #for the latest stable LO version.

---

### Post by mikodo on 2015-01-28
> **SeijiSensei said:**
> I added a [Mozilla PPA]("https://launchpad.net/~mozillateam/+archive/ubuntu/firefox-next") today so I could try out Firefox beta with its support for [HTML5 video from YouTube]("http://news.slashdot.org/story/15/01/27/2217258/youtube-ditches-flash-for-html5-video-by-default").So nice, to see flash starting to go the way of the Dodo.

---

### Post by garycheng12 on 2015-01-29
Appreciate all the comments, will check out Synaptic, read more on Debian package management, and see if the recommended PPAs are for me.

---

