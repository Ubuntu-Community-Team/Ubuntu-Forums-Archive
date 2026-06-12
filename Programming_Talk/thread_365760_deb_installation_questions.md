---
title: "deb installation questions"
date: 2007-02-20
forum: Programming Talk
---

### Post by j_g on 2007-02-20
Ok, so I finally have this .deb package of my binaries. Now, when I want to install it upon some Ubuntu (or Debian-based) system, do I have to open a terminal window, cd to the directory with the .deb file, and then type:

sudo dpkg -i my_package_name.deb

Now I know that the .deb package is supposed to contain information about dependencies. And it appears that when I do an "apt-get install" on some package, it also downloads and installs the dependencies. But will this dpkg utility also check for, and ensure that, all dependency packages are also installed (going to one of those repositories to find the dependent packages if need be)?

Or is there some graphical utility I can use to install the .deb file from disk (or am I limited to dpkg)? For example, can I run Synaptic, and somehow point it to this file on disk? Or is there some other such utlity (ie, "Applications -> System Tools -> Gnome Apt Software Manager") that can install a file from disk? Or are these graphical frontends limited only to viewing/installing files that reside upon some web "repository"?

---

### Post by SunnyRabbiera on 2007-02-20
well what are you using here, practically all ubuntu varients have a package installer.

---

### Post by WW on 2007-02-20
If you use the File Browser Nautilus and right-click on a .deb file, you can open the file with 'GDebi Package Installer'.  This is a GUI installer for a single package. (I think the actual program is gdebi-gtk.)

---

### Post by j_g on 2007-02-20
> Practically all ubuntu varients have a package installer.

I did a default install of Ubuntu, and I see that it appears to have come with apt-get, synaptic, and dpkg.

But my question wasn't "Is one of these installed upon Ubuntu?". I know that they are. My questions concern the differences/capabilities of these choices. Are they all essentially the same thing, or does one offer me...

1) A way of installing a deb file on disk..
2) ...using a GUI (ie, I don't have to open a terminal and type a command to invoke the software on my particular file)...
_and_
3) ...also ensures that any dependency packages are downloaded and installed from a repository?

Is there such an option out there?

> use the File Browser Nautilus

I didn't see that installed with the default Ubuntu setup.

Here's the deal: I'm currently writing up a User's Manual (PDF) for my software that I'm about to release, and I want to provide endusers with the easiest possible instructions for installation. Some of these users may be Windows folks just migrating to Linux. My package doesn't depend upon Nautilus, so if it's a situation where I have to tell an enduser "download and install nautilus, and then you can easily install my package", I'd rather not even venture down that road. I was hoping that a deb file, even if I limit the choices of which particular distros it can be used upon, could achieve the same kind of ease-of-installation we get on Windows. No?

---

### Post by WW on 2007-02-20
"Nautilus" is  the name of the program that is the default file browser in Ubuntu.  I have gotten used to calling it Nautilus, so I forgot that you never actually see that name unless you choose the menu item Help->About in the File Browser.

If your user is using Ubuntu, they have Nautilus.  Just call it the "File Browser", not Nautilus, to avoid confusion.

For installation instructions, you can tell your users to "Double-click on the file my_package_name.deb to start the Package Installer". (The "Package Installer" is actually a program called gdebi, but again, your user won't know that unless he or she happens to look at Help->About in the "Package Installer" window.)  I think if you try this yourself, you'll have the best idea for how to write your instructions.

---

### Post by WW on 2007-02-20
Some more thoughts:

The "double-click" instructions that I mentioned in my previous post will work in Ubuntu.  Ubuntu uses Gnome, and the default file browser in Gnome is Nautilus.  I am not running Kubuntu or Xubuntu, so I don't know if the default file browsers in those flavors of Ubuntu work the same way.  These are just the Ubuntu variations.  There are many other flavors of debian, with a wide variety of desktop environments.

The "safest" (i.e. guaranteed to work) instructions for a debian-based system will almost certainly involve using dpkg in the command line. Maybe something like:
> If you are unable to install the package from your file browser,  you can do it from the command line.  In the following, I will assume that you have saved my_package_name.deb to the Desktop directory in your home directory.  In a terminal, enter the commands
[quote]$ cd ~/Desktop
$ sudo dpkg -i my_package_name.deb

[/quote]

---

### Post by j_g on 2007-02-20
Thanks for the info.

Yes, I do intend to provide various "backup instructions" (ie, "If this simple approach doesn't work, try this more complicated approach..."). But I do want to offer endusers, first and foremost, the easiest method.

So this "debi" will take care of downloading/installing all the dependencies? I've already installed them on my own system, and I really don't want to remove them just to check that debi does what I hope it does when it installs my deb package.

---

### Post by WW on 2007-02-20
I haven't had a chance to check if gdebi does dependencies.  I don't know why you don't want to remove a dependency or two just to check.  The beauty of apt is how easy it is to do. Just find a dependency of your app that is not a dependency of something else, remove it (with synaptic, or just 'apt-get remove package'), and then see if the dependency gets reinstalled by gdebi when you use it to install your package.

Or see if there are any docs that answer the question.

Or wait to see if someone else responds here.

---

### Post by j_g on 2007-02-20
I did a test. The "File Browser" method you alluded to doesn't appear to work. I did:

1). Selected "Places -> Home Folder" menu item, and navigated to where my .deb file is located.
2) Right-clicked on the .deb file's icon. This presented a pop-up menu.
3). There was no "Open with File Browser" item in the pop-up menu, but there was an "Open with other application" so I selected that.
4) This presented a dialog box listing numerous utilities. Sure enough, "File Browser" was in the list, so I selected that.
5) An error box popped up saying "Can't open <mydebfilename>. The location is not a folder.".

That sort of makes sense. This .deb file is not a folder, and if "File Browser" assumes that you've always right-clicked on a folder, then that explains the error message.

Any other approaches?

---

### Post by dannyboy79 on 2007-02-20
> **WW said:**
>  The "safest" (i.e. guaranteed to work) instructions for a debian-based system will almost certainly involve using dpkg in the command line. Maybe something like:

Well, I would have to disagree due to a greatly know Debain package named: gdeb 

Versions: 0.4.9-1.1+b1 [hppa], 0.4.9-1.1 [alpha, amd64, arm, i386, ia64, kfreebsd-i386, m68k, mips, mipsel, powerpc, s390, sparc]

As you can see this Gui Program for installing .deb packages is supported on many different platforms and will work for ANY distro that is built upon Debian, which Ubuntu, Kubuntu, Xubuntu, the newest I believe is now Linux Mint and ALL these:

Adamantix 
APLINUX 
BenHur 
Corel Linux 
Debian JP 
DemoLinux 
Demudi, [http://www.demudi.org/](http://www.demudi.org/), a multimedia distribution. 
Embedded Debian, [http://www.emdebian.org/](http://www.emdebian.org/) 
ESware Linux 
Euronode, [http://euronode.org/](http://euronode.org/) 
Floppix, [http://floppix.ccai.com/](http://floppix.ccai.com/) 
Gibraltar 
GNUstep LIVE CD, [http://livecd.gnustep.org/](http://livecd.gnustep.org/) 
Impi Linux 
Kanotix, [http://www.kanotix.com/](http://www.kanotix.com/) 
KNOPPIX, [http://www.knopper.net/knoppix/](http://www.knopper.net/knoppix/) 
Libranet, [http://www.libranet.com/](http://www.libranet.com/) 
Linspire, [http://www.linspire.com/](http://www.linspire.com/) 
Linex 
Linuxin 
Linux-YeS, [http://eugene.mplik.ru/doc/lys/](http://eugene.mplik.ru/doc/lys/) 
Linux Router Project, [http://www.linuxrouter.org/](http://www.linuxrouter.org/) 
MEPIS, [http://www.mepis.org/](http://www.mepis.org/) 
M.N.I.S. Linux, [http://www.mnis.fr/](http://www.mnis.fr/) 
Morphix 
PingOO, [http://www.linuxedu.org/](http://www.linuxedu.org/) 
Progeny Linux, [http://www.progeny.com/](http://www.progeny.com/) 
Prosa, [http://www.prosa.it/](http://www.prosa.it/) 
RAYS LX 
Stonegate 
Stormix Technologies' Storm Linux. 
TelemetryBox, [http://telemetrybox.org/](http://telemetrybox.org/) 
Ubuntu 
Xandros. 

The obvious downfall to this program is that if it's not installed by default within these listed distros, they'll have to use dpkg  after downloading the deb to install it and then it'll work. Good luck on your pdf for your software. Here is a link to all the dependencys of gdeb. [http://packages.debian.org/unstable/utils/gdeb](http://packages.debian.org/unstable/utils/gdeb)

---

### Post by dannyboy79 on 2007-02-20
> **j_g said:**
> I did a test. The "File Browser" method you alluded to doesn't appear to work. I did:

1). Selected "Places -> Home Folder" menu item, and navigated to where my .deb file is located.
2) Right-clicked on the .deb file's icon. This presented a pop-up menu.
3). There was no "Open with File Browser" item in the pop-up menu, but there was an "Open with other application" so I selected that.
4) This presented a dialog box listing numerous utilities. Sure enough, "File Browser" was in the list, so I selected that.
5) An error box popped up saying "Can't open <mydebfilename>. The location is not a folder.".

That sort of makes sense. This .deb file is not a folder, and if "File Browser" assumes that you've always right-clicked on a folder, then that explains the error message.

Any other approaches?


you were suppose to double click it, not right click it. I know some1 said to right click it but I don't think they knew really what they were saying. If you have gdeb installed, you can double click it because all .deb files will be associated to this gdebi program.

OOPS, I accidentally stated the wrong program in my last thread although, gdeb is similar to gdebi, it doesn't install the deb by default but allows you the option to install it. here's the link for gdebi.  [http://packages.debian.org/unstable/admin/gdebi](http://packages.debian.org/unstable/admin/gdebi)

---

### Post by j_g on 2007-02-20
Ok, I got it figured out. Ubuntu's default setup doesn't install gdebi. But all one has to do is use Synaptic (or I suppose apt-get) to install gdebi from Ubuntu's repository.

Then, _after_ gdebi is installed on Ubuntu, you can right-click on a .deb file, and you'll see an "Open with "GDebi Package installer" item in the pop-up menu. (Don't know if it does the same under a KDE, rather than Gnome, desktop. Knowing the state of Linux "interoperability", probably not).

The docs claim that it will resolve dependencies, and download/install needed stuff.

Simple enough. Now hopefully, the other debian distros do the same thing. (Probably not. Sigh.)

---

### Post by j_g on 2007-02-20
Aha! Even easier. Install "debi" and double-click on the .deb file.

Great. Do the other Debian packages (ie, besides Ubuntu) exhibit the same behavior? Does this work just as easily under KDE as it does under Gnome?

---

### Post by dannyboy79 on 2007-02-20
> **j_g said:**
> Ok, I got it figured out. Ubuntu's default setup doesn't install gdebi. But all one has to do is use Synaptic (or I suppose apt-get) to install gdebi from Ubuntu's repository.

Then, _after_ gdebi is installed on Ubuntu, you can right-click on a .deb file, and you'll see an "Open with "GDebi Package installer" item in the pop-up menu. (Don't know if it does the same under a KDE, rather than Gnome, desktop. Knowing the state of Linux "interoperability", probably not).

The docs claim that it will resolve dependencies, and download/install needed stuff.

Simple enough. Now hopefully, the other debian distros do the same thing. (Probably not. Sigh.)

it's a lot easier to simply double click instead of click, hold, find what you want, scroll down to it, blah blah blah.
Anyway, I am sure ALL Debian based distros will be the same once gdebi is installed. that's the way the gdebi installer is I imagine. That's another reason I am telling you to out double click (which will always work after they install gdebi) instead of hoping that gdebi put a choice within the right click menu.

---

### Post by j_g on 2007-02-20
Right. My enduser instructions will be:

Assuming you've downloaded <myfilename.deb> to your desktop:

1) Make sure that gdebi is installed upon your Debian distro. If not, use Synaptic Package Manager to search/locate and install it.
2) Double-click on <myfilename.deb>. (ie, Move the mouse pointer over the icon labeled <myfilename.deb> and quickly press the left mouse button twice.)
3) This presents the "Package Install" window. Click on the "Install package" button.

Does this cover it? Actually works under all Debian distros??? (Gasp!) No interoperability problems between Gnome or KDE desktops??? (Double gasp!!)

---

### Post by dannyboy79 on 2007-02-20
Well I can't say for sure but I know it works in both Xubuntu, Debian, and Ubuntu. I don't see why it wouldn't work on Kubuntu let alone all Debian based distros since we're are talking about deb's here. Do you understand what .deb extension stands for??? It's short for debian package and Kubuntu is Debain based.

---

### Post by j_g on 2007-02-20
Believe me, I know what Debian Package means. (I wish I didn't, but that's a story for another time).

Anyway, if it at least works under Gnome-based debian distros (but not KDE-based ones), then that's good enough for me. I was just asking so I'd know what to say to an enduser if he encounters a problem. (ie, "If you want to use this software, but you're having trouble installing it under KDE, then dump KUbuntu and install Ubuntu instead").

---

### Post by WW on 2007-02-20
In an earlier post, I suggested using right-click.  This is, after all, what **gdebi** says to do:
> $ gdebi -h
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
Usage: /usr/bin/gdebi [package.deb]

To use the graphical user interface, right-click
on a '.deb' software package in the file browser
and select: Open with 'GDebi Package Installer'.

(The initial warning may be a bug in Ubuntu's version of gdebi?)  I later suggested double-clicking, since that worked automatically.

---

