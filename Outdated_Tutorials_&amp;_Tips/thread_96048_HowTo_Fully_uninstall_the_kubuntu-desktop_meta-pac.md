---
title: "HowTo: Fully uninstall the kubuntu-desktop meta-package"
date: 2005-11-28
forum: Outdated Tutorials &amp; Tips
---

### Post by aysiu on 2005-11-28
This tutorial is extremely outdated.

For the latest Ubuntu version, go [here](http://www.psychocats.net/ubuntu/puregnome).

---

### Post by Xian on 2005-11-28
If the goal is as stated to "fully uninstall" the kubuntu-desktop kde affiliated packages then I would go ahead and use the purge prefix in the command.

$ sudo apt-get remove --purge

---

### Post by aysiu on 2005-11-28
Thanks for adding that.

It's really to address people's concerns (which I've seen in numerous threads) that a meta-package's installation dumps a bunch of apps in, but the meta-package's uninstall does not take those bunch of apps out.

Whether people want to fully uninstall each app is up to each user. I'm glad you presented that option as well.

---

### Post by Hopsonn on 2005-11-28
What I would really like to do is to be able to remove some of the other stuff without removing KDE.

---

### Post by aysiu on 2005-11-28
[QUOTE=Hopsonn]What I would really like to do is to be able to remove some of the other stuff without removing KDE.[/QUOTE] I'm not sure what you mean. What other stuff would you like to get rid of?

---

### Post by lcg on 2005-11-28
[QUOTE=aysiu]As you may or may not know, if you install the package called kubuntu-desktop, a lot of other packages will be installed so that you get the full KDE experience in addition to Gnome.

If, however, you *uninstall* kubuntu-desktop, none of the other "full KDE experience" packages will be uninstalled. You may have installed kubuntu-desktop to get the KDE experience but then found it cluttered things up too much.[/QUOTE]
For experiments like this, I like to use aptitude on the command line. Aptitude has this feature that it marks packages which are installed as dependencies as automatically installed. If you later remove all packages with a dependency on a package marked as auto, the auto package is removed as well.
So, with aptitude one can simply install and later remove kubuntu-desktop and there are no leftover packages.

HTH,
Lars

---

### Post by dabear on 2005-11-28
Shit! Just tried ```
sudo apt-get remove adept akode akregator amarok ark arts dbus gtk2-engines-gtk-qt gwenview ivman k3b kaddressbook kaffeine-gstreamer kamera karm katapult kate kaudiocreator kcontrol kcron kdeadmin-kfile-plugins kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kde-guidance kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards kdeprint kdesktop kde-systemsettings kdm kfind kghostview khelpcenter kicker kio-apt kio-locate klaptopdaemon klipper kmail kmenuedit kmilo kmix knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konserve konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb krita kscd kscreensaver ksmserver ksnapshot ksplash ksvg ksysguard ksystemlog kubuntu-artwork-usplash kubuntu-default-settings kubuntu-docs kubuntu-konqueror-shortcuts kuser kwalletmanager kwifimanager kwin openoffice.org2-kde pmount python-opengl qca-tls speedcrunch ttf-dejavu
``` without removing kubuntu-desktop.  Because of dependencies, it seems like much of the gnome desktop got uninstalled too. I luckily aborted the process before it was too late, but I had to do a «sudo dpkg-reconfigure -a && apt-get install gnome-desktop» afterwards

---

### Post by aysiu on 2005-11-28
[QUOTE=dabear]Shit! Just tried ```
sudo apt-get remove adept akode akregator amarok ark arts dbus gtk2-engines-gtk-qt gwenview ivman k3b kaddressbook kaffeine-gstreamer kamera karm katapult kate kaudiocreator kcontrol kcron kdeadmin-kfile-plugins kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kde-guidance kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards kdeprint kdesktop kde-systemsettings kdm kfind kghostview khelpcenter kicker kio-apt kio-locate klaptopdaemon klipper kmail kmenuedit kmilo kmix knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konserve konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb krita kscd kscreensaver ksmserver ksnapshot ksplash ksvg ksysguard ksystemlog kubuntu-artwork-usplash kubuntu-default-settings kubuntu-docs kubuntu-konqueror-shortcuts kuser kwalletmanager kwifimanager kwin openoffice.org2-kde pmount python-opengl qca-tls speedcrunch ttf-dejavu
``` without removing kubuntu-desktop.[/quote] *Without* removing kubuntu-desktop? What you're removing *is* kubuntu-desktop--that's what the whole point of this HowTo is.  

> Because of dependencies, it seems like much of the gnome desktop got uninstalled too. I luckily aborted the process before it was too late, but I had to do a &#171;sudo dpkg-reconfigure -a && apt-get install gnome-desktop&#187; afterwards Really? Because I cross-referenced ubuntu-desktop's packages with kubuntu-desktop's packages, and what you copied and pasted is what's left over (i.e., the ones specific to kubuntu-desktop). None of ubuntu-desktop's packages should be affected. Do you remember off the top of your head some packages that were affected?

Could it be that you have some KDE applications running in Gnome? The point of this HowTo is to get KDE out of there.

---

### Post by no1wantdthisname on 2005-11-28
A much easier way would be to use debfoster.
Install debfoster.
Create the basic file list with 
```
sudo debfoster -q
```
and then 
```
sudo gedit /var/lib/debfoster/keepers
```
erase entries that are unneeded.  In this case, kubuntu-desktop.
```
sudo debfoster
```
will ask about whether you want to keep something or not, and will automatically remove and purge those programs and their unneeded dependencies.  This is a much cleaner and easier way.

---

### Post by aysiu on 2005-11-28
I'm sure debfoster's a wonderful thing, but how is that easier than copying and pasting one command into a terminal? It may be "cleaner," but it's not easier.

---

### Post by mamo on 2005-12-06
[QUOTE=aysiu]

To uninstall all the other junk, open up a terminal (Applications > Accessories > Terminal) and copy and paste this into your terminal: ```
sudo apt-get remove adept akregator amarok amarok-gstreamer ark arts debtags enscript gtk2-engines-gtk-qt gwenview imagemagick ivman kaddressbook kaffeine  kaffeine-gstreamer kamera kappfinder karm katapult kate kaudiocreator kcron kde-guidance kde-style-lipstik kde-systemsettings kdeadmin-kfile-plugins  kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards kdeprint kdm kghostview khelpcenter kicker kio-apt kio-locate klaptopdaemon klipper kmail kmenuedit kmilo kmix knetworkconf knotes konq-plugins konqueror-nsplugins konserve konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb krita kscd kscreensaver ksmserver ksnapshot ksplash ksvg ksysguard ksysguardd ksystemlog kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kwalletmanager kwifimanager kwin libgadu3 libgpgme11 libjpeg-progs libkcal2a libkcddb1 libkdepim1 libkipi0 libkleopatra0a libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 libmimelib1a libopenobex-1.0-0 libpythonize0 libsensors3 libtdb1 openoffice.org2-kde poster psutils python-kde3 python-opengl python2.4-dev python2.4-kde3 python2.4-opengl python2.4-qt3 python2.4-sip4-qt3 qca-tls qobex sanekonsole speedcrunch ttf-dejavu xlibs
``` This will remove all the extra "junk" that was installed along with the kubuntu-desktop meta-package.

P.S. I haven't tested this yet. [/QUOTE]

I tested it and it works fine. It seems that kde is almost fully removed. Only konqueror is still installed (in fact it wasn't listed il the "remove" list)

I have a related question: kubuntu installation changed the boot splash (the one that is showed during boot, together with services startup list).
How can I remove kubuntu splash and have back the ubuntu one?

---

### Post by aysiu on 2005-12-07
[QUOTE=mamo]
I have a related question: kubuntu installation changed the boot splash (the one that is showed during boot, together with services startup list).
How can I remove kubuntu splash and have back the ubuntu one?[/QUOTE] ```
sudo apt-get remove kubuntu-artwork-usplash
```

---

### Post by mamo on 2005-12-07
I think this is not enough.
Now I'm not at home and I can't check, but I see "kubuntu-artwoks-usplash" was part of your list. So I removed it, but I still see the kubuntu splash.

By the way (I'm not an expert and maybe I didn't use the right term). By saying "splash" I don't mean the login window. I mean the bitmap that comes up during boot. It's a blue "kubuntu" at the center of the screen and under it the system lists all the startup activities.

---

### Post by aysiu on 2005-12-07
I know exactly what splash you're talking about.

Maybe in Synaptic mark for complete removal the package *usplash*, apply changes, then reinstall it? Complete removal removes not only the package but also the configuration file. My guess is that the config file is specifying the use of the Kubuntu usplash.

---

### Post by mamo on 2005-12-07
I solved my issue:

first of all I had to reinstall usplash (as you suggested) in order to have back  the default usplash-artwork.so

then, it's necessary to rebuild initramfs:

```
sudo dpkg-reconfigure linux-image-$(uname -r)
```

---

### Post by GreenHawkIA on 2005-12-07
This excellent [Howto thread]("http://www.ubuntuforums.org/showthread.php?t=82835") explains how to switch your splash to a customized color/image and revert it back to the original image as well.   Very well written, and worked like a dream for me - and should provide anyone with usplash questions some help.

---

### Post by shanghaipi on 2005-12-25
thanks for the code, worked perfectly for me.

---

### Post by angrykeyboarder on 2005-12-29
[quote=mamo]I solved my issue:

first of all I had to reinstall usplash (as you suggested) in order to have back  the default usplash-artwork.so

then, it's necessary to rebuild initramfs:

```
sudo dpkg-reconfigure linux-image-$(uname -r)
```[/quote]

What is *initramfs* ?

---

### Post by Adrian on 2006-01-15
A nice solution to this problem is to do this:
```
sudo aptitude remove kubuntu-desktop
```

That should uninstall kubuntu-desktop, given that you used **aptitude** when you installed it! 

**aptitude** works like **apt-get**, but one significant difference is that the former also handles meta packages. However, you should also do the INSTALL using **aptitude** to make it work properly.

I'm not sure of how it works when the installation was made with **apt-get**. I tried installing a meta-package with **apt-get**, and **aptitude** removed its components properly, but I don't know if that works in general. I've read that **aptitude** marks the packages it installs, as stated in post #6 of this thread.

After the uninstall, if your splash screen (during boot) still shows "Kubuntu", you might want to change that. First, type:

```
sudo update-alternatives --config usplash-artwork.so
```

This will not have any effect if you're just using Ubuntu, but if you for instance have Xubuntu installed too, you'll get a menu where you can chose the preferred splash.

The last step is to finalize the change of splash screen:
```
sudo dpkg-reconfigure linux-image-`uname -r`
```

(More about splash screens can be found here:
[http://www.ubuntuforums.org/showthread.php?t=113250](http://www.ubuntuforums.org/showthread.php?t=113250))

---

### Post by aysiu on 2006-01-15
Thanks for adding that, Adrian.

---

### Post by Galoot on 2006-01-16
I copy/pasted twice and got this message both times, so I aborted:

```
The following packages will be REMOVED:
  adept akregator amarok amarok-gstreamer ark arts debtags electricsheep
  enscript gkrellshoot gpa gqcam gtk2-engines-gtk-qt gwenview imagemagick
  ivman kaddressbook kaffeine kaffeine-gstreamer kamera kappfinder karm
  katapult kate kaudiocreator kcron kde-guidance kde-style-lipstik
  kde-systemsettings kdeadmin-kfile-plugins kdebluetooth
  kdegraphics-kfile-plugins kdemultimedia-kappfinder-data
  kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing
  kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards
  kdeprint kdm kghostview khelpcenter kicker kio-apt kio-locate klaptopdaemon
  klipper kmail kmenuedit kmilo kmix knetworkconf knotes konq-plugins
  konqueror-nsplugins konserve konsole kontact konversation kooka kopete
  korganizer kpdf kpf kppp krdc krfb krita kscd kscreensaver ksmserver
  ksnapshot ksplash ksvg ksysguard ksysguardd ksystemlog
  kubuntu-artwork-usplash kubuntu-default-settings kubuntu-docs
  kubuntu-konqueror-shortcuts kuser kwalletmanager kwifimanager kwin libgadu3
  libgpgme11 libjpeg-progs libkcal2a libkcddb1 libkdepim1 libkipi0
  libkleopatra0a libkpimexchange1 libkpimidentities1 libkscan1 libksieve0
  libktnef1 liblockdev1 libmimelib1a libopenobex-1.0-0 libpythonize0
  libsensors3 libtdb1 openoffice.org2-kde opera poster psutils python-kde3
  python-opengl python2.4-dev python2.4-kde3 python2.4-opengl python2.4-qt3
  python2.4-sip4-qt3 qca-tls qobex sanekonsole speedcrunch ttf-dejavu xlibs

```

Notice how it added electricsheep, gkrellshoot, gpa, gqcam, and opera?

You have ImageMagick in your list, which Gkrellshoot (a GKrellM screen capture util.) depends on. I'm not sure why the others were tagged for removal, though.

Here are the steps I followed right from the start:
[LIST=1]
[*]Installed kubuntu-desktop via Synaptic
[*]Tried KDE until all the shine gave me a headache (about 1 1/2 hours)
[*]sudo apt-get remove kubuntu-desktop
[*]Realized that now would be a good time to "sudo dpkg-reconfigure kdm" before I went any further
[*]Copy/pasted your instructions
[/LIST]
Because I aborted the command all the stuff is still on my hard drive. Should I maybe reinstall kubuntu-desktop the same way I removed it (via apt-get), then get rid of it through Synaptic and try your command again? Or should I just use your list for reference and go at them one at a time?

Or should I try AdAware? ;)

---

### Post by aysiu on 2006-01-16
My list was based on installing Ubuntu and seeing what packages get installed *on top of* that. I don't assume you have Opera installed, and I didn't know Opera depended on some of the KDE packages.

I think your best bet is to just remove all the crap it wants to remove and then reinstall electricsheep, gkrellshoot, gpa, gqcam, and opera. Your settings for those programs should still remain after you remove them, and when you reinstall them, only their dependencies (and not all the extra KDE crap) will be reinstalled with them.

---

### Post by Galoot on 2006-01-16
Did as you suggested.```
sudo apt-get install electricsheep gkrellshoot gpa gqcam
```gives the following message```
The following extra packages will be installed:
  imagemagick libgpgme11 libjpeg-progs xlibs
Suggested packages:
  html2ps
```

Added Opera to the reps (deb [http://deb.opera.com/opera/](http://deb.opera.com/opera/) stable non-free) and```
sudo apt-get install opera
```leads to
```
Recommended packages:
  libmotif
The following NEW packages will be installed:
  opera
```It doesn't look like Opera (installed through apt-get) depends on anything KDE related. I wonder why it gets uninstalled with your command. :confused:

Perhaps it has something to do with how I initially installed Opera by downloading the deb directly from the site (opera_8.51-20051114.6-shared-qt_en_etch_i386.deb) as opposed to using apt-get in the first place?

I don't really expect anyone to puzzle it out for me, though, I'm just documenting it here.

Thanks for your help, aysiu. All the shiny stuff has been removed.

---

### Post by aysiu on 2006-01-16
Well, I'm glad it all worked out in the end, though I'm just as confused as you are...

---

### Post by robotgeek on 2006-01-16
I have made a shell script for this purpose. You can use it to remove kubuntu-desktop, while keeping ubuntu-desktop installed, or remove ubuntu-desktop while keeping xubuntu-desktop installed. 

You can find it at [http://robotgeek.org/dotfiles/cleaner.sh](http://robotgeek.org/dotfiles/cleaner.sh) 

Download the file, and make changes regarding which one you want to keep, and which one you want to remove. For example:
```

wget http://robotgeek.org/dotfiles/cleaner.sh
PKG_REMOVE=ubuntu-desktop
PKG_KEEP=xubuntu-desktop

```

Then, run 
```

chmod +x cleaner.sh
./cleaner.sh 

```

All done, hopefully :)
It should remove the extra packages correctly.

---

### Post by confused57 on 2006-01-17
I uninstalled Kubuntu using copy and paste of Asyiu's instructions, did the trick, but have a question.  When I installed kubuntu-desktop, installation said 426 Mb of packages would be installed; but the uninstallation said 260 Mb would be removed.
No problems, it accomplished what I wanted;  but, I was just wondering...
I liked the look of Kubuntu, but kde used  90% of my memory resources(have 256 Mb) and there were various and sundry quirks in using the desktop.  Only been using Ubuntu for a week, definitely a fun learning experience.

---

### Post by cudmore on 2006-03-05
[QUOTE=Xian]If the goal is as stated to "fully uninstall" the kubuntu-desktop kde affiliated packages then I would go ahead and use the purge prefix in the command.

$ sudo apt-get remove --purge[/QUOTE]

Shoot, I just did the remove command and all went well ... except I forgot the --purge. Is there anyway now to purge what I just uninstalled?

For some reason the KDE software was really screwing up my video (NVIDIA 6600) and causing the system to hang?

---

### Post by cudmore on 2006-03-05
[QUOTE=confused57]I uninstalled Kubuntu using copy and paste of Asyiu's instructions, did the trick, but have a question.  When I installed kubuntu-desktop, installation said 426 Mb of packages would be installed; but the uninstallation said 260 Mb would be removed.
No problems, it accomplished what I wanted;  but, I was just wondering...
I liked the look of Kubuntu, but kde used  90% of my memory resources(have 256 Mb) and there were various and sundry quirks in using the desktop.  Only been using Ubuntu for a week, definitely a fun learning experience.[/QUOTE]

I had the same thing happen, like 400 MB on install and 300 MB on uninstall (approximate).

---

### Post by andrewski on 2006-03-19
I just tried this on Dapper and ran into a few problems:
```
andrew:~ sudo apt-get remove adept akregator amarok amarok-gstreamer ark arts debtags enscript gtk2-engines-gtk-qt gwenview imagemagick ivman kaddressbook kaffeine  kaffeine-gstreamer kamera kappfinder karm katapult kate kaudiocreator kcron kde-guidance kde-style-lipstik kde-systemsettings kdeadmin-kfile-plugins  kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards kdeprint kdm kghostview khelpcenter kicker kio-apt kio-locate klaptopdaemon klipper kmail kmenuedit kmilo kmix knetworkconf knotes konq-plugins konqueror-nsplugins konserve konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb krita kscd kscreensaver ksmserver ksnapshot ksplash ksvg ksysguard ksysguardd ksystemlog kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kwalletmanager kwifimanager kwin libgadu3 libgpgme11 libjpeg-progs libkcal2a libkcddb1 libkdepim1 libkipi0 libkleopatra0a libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 libmimelib1a libopenobex-1.0-0 libpythonize0 libsensors3 libtdb1 openoffice.org2-kde poster psutils python-kde3 python-opengl python2.4-dev python2.4-kde3 python2.4-opengl python2.4-qt3 python2.4-sip4-qt3 qca-tls qobex sanekonsole speedcrunch ttf-dejavu xlibs
Reading package lists... Done
Building dependency tree... Done
<SNIP some packages weren't installed>
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  openoffice.org-l10n-en-us: Depends: openoffice.org-common (> 2.0.2) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
                             Depends: openoffice.org-common (< 2.0.3) but it is not going to be installed or
                                      language-support-en but it is not going to be installed
E: Broken packages
``` So I thought, "Well, I'll just go ahead and break this dependency right now; I can reinstall openoffice afterwards."
```
andrew:~ sudo apt-get remove openoffice.org-l10n-en-us
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  kubuntu-desktop openoffice.org openoffice.org-base openoffice.org-calc
  openoffice.org-common openoffice.org-core openoffice.org-draw
  openoffice.org-evolution openoffice.org-gnome openoffice.org-impress
  openoffice.org-java-common openoffice.org-kde openoffice.org-l10n-en-us
  openoffice.org-math openoffice.org-writer python-uno
0 upgraded, 0 newly installed, 16 to remove and 1 not upgraded.
Need to get 0B of archives.
After unpacking 186MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 104284 files and directories currently installed.)
Removing kubuntu-desktop ...
Removing openoffice.org ...
Removing openoffice.org-evolution ...
Removing openoffice.org-base ...
Removing openoffice.org-calc ...
Removing openoffice.org-writer ...
Removing python-uno ...
Removing openoffice.org-math ...
Removing openoffice.org-kde ...
Removing openoffice.org-impress ...
Removing openoffice.org-gnome ...
Removing openoffice.org-draw ...
Removing openoffice.org-java-common ...
Removing openoffice.org-common ...
***
* Updating MIME database in /usr/share/mime...
Wrote 469 strings at 20 - 2714
Wrote aliases at 2714 - 28c8
Wrote parents at 28c8 - 2f1c
Wrote literal globs at 2f1c - 2f78
Wrote suffix globs at 2f78 - 62e0
Wrote full globs at 62e0 - 6304
Wrote magic at 6304 - bac8
Wrote namespace list at bac8 - bad8
***
Removing openoffice.org-core ...
Removing openoffice.org-l10n-en-us ...
andrew:~ sudo apt-get remove adept akregator amarok amarok-gstreamer ark arts debtags enscript gtk2-engines-gtk-qt gwenview imagemagick ivman kaddressbook kaffeine  kaffeine-gstreamer kamera kappfinder karm katapult kate kaudiocreator kcron kde-guidance kde-style-lipstik kde-systemsettings kdeadmin-kfile-plugins  kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards kdeprint kdm kghostview khelpcenter kicker kio-apt kio-locate klaptopdaemon klipper kmail kmenuedit kmilo kmix knetworkconf knotes konq-plugins konqueror-nsplugins konserve konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb krita kscd kscreensaver ksmserver ksnapshot ksplash ksvg ksysguard ksysguardd ksystemlog kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kwalletmanager kwifimanager kwin libgadu3 libgpgme11 libjpeg-progs libkcal2a libkcddb1 libkdepim1 libkipi0 libkleopatra0a libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 libmimelib1a libopenobex-1.0-0 libpythonize0 libsensors3 libtdb1 openoffice.org2-kde poster psutils python-kde3 python-opengl python2.4-dev python2.4-kde3 python2.4-opengl python2.4-qt3 python2.4-sip4-qt3 qca-tls qobex sanekonsole speedcrunch ttf-dejavu xlibs
Reading package lists... Done
Building dependency tree... Done
<SNIP those packages that weren't installed>
The following packages will be REMOVED:
  abiword abiword-common abiword-plugins abiword-plugins-gnome adept akregator
  alacarte amarok amarok-xine ark arts artsbuilder avifile-divx-plugin
  avifile-mad-plugin avifile-mjpeg-plugin avifile-vorbis-plugin
  avifile-win32-plugin avifile-xvid-plugin baobab beagle
  beagle-backend-evolution bluez-cups bluez-pin bug-buddy compiz-gnome
  contact-lookup-applet cupsys cupsys-driver-gimpprint
  cupsys-driver-gutenprint dbus-1-utils debtags deskbar-applet easytag ekiga
  enscript eog epiphany-browser epiphany-extensions evince evolution
  evolution-exchange evolution-plugins evolution-webcal f-spot file-roller
  firefox firefox-gnome-support fontconfig gaim gaim-themes gcalctool
  gconf-editor gdebi gdm gedit gftp gftp-gtk gimp gimp-helpbrowser gimp-python
  gksu glade-gnome glade-gnome-2 gmpc gmrun gnome-about gnome-app-install
  gnome-applets gnome-btdownload gnome-control-center gnome-cups-manager
  gnome-games gnome-icon-theme gnome-keyring gnome-media
  gnome-netstatus-applet gnome-nettool gnome-panel gnome-pilot
  gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session
  gnome-spell gnome-sudoku gnome-system-monitor gnome-system-tools
  gnome-terminal gnome-themes gnome-utils gnome-volume-manager gnomebaker
  gnumeric gramps grip gstreamer0.10-plugins-good gstreamer0.10-x gthumb
  gtk-gnutella gtk2-engines-clearlooks gtk2-engines-crux gtk2-engines-gtk-qt
  gtk2-engines-industrial gtk2-engines-lighthouseblue gtk2-engines-mist
  gtk2-engines-pixbuf gtk2-engines-redmond95 gtk2-engines-smooth
  gtk2-engines-thinice gtk2-engines-ubuntulooks gtkhtml3.8 gucharmap gwenview
  hal-device-manager hplip hplip-data hwdb-client imagemagick inkscape k3b
  kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kaudiocreator
  kcontrol kcron kde-guidance kde-style-lipstik kde-systemsettings
  kdeadmin-kfile-plugins kdebase-bin kdebase-kio-plugins kdebluetooth
  kdegraphics-kfile-plugins kdelibs-bin kdelibs4c2a
  kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing
  kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources
  kdepim-wizards kdeprint kdesktop kdm kdnssd keep kfind kghostview
  khelpcenter kicker kio-apt kio-locate klaptopdaemon klipper kmail kmenuedit
  kmilo kmix knetworkconf knotes koffice-data koffice-libs konq-plugins
  konqueror konqueror-nsplugins konsole kontact konversation kooka kopete
  korganizer kpdf kpf kppp krdc krfb krita kscd kscreensaver ksmserver
  ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog
  kubuntu-artwork-usplash kubuntu-default-settings kubuntu-docs
  kubuntu-konqueror-shortcuts kwalletmanager kwifimanager kwin
  kwin-style-crystal language-selector libaiksaurusgtk-1.2-0c2a libarts1-akode
  libarts1c2a libavahi-qt3-1 libavifile-0.7c2 libbonoboui2-0 libbtctl2
  libcairo2 libdbus-qt-1-1c2 libedataserverui1.2-6 libeel2-2 libevolution-cil
  libexchange-storage1.2-1 libexo-0.3-0 libfontconfig1 libgadu3 libgail-common
  libgail17 libgdl-1-0 libgdl-1-common libgecko2.0-cil libgimp2.0 libgksu1.2-1
  libgksuui1.0-1 libglade-cil libglade2-0 libglade2.0-cil libgnome-cil
  libgnome-desktop-2 libgnome-keyring0 libgnome2-canvas-perl libgnome2-perl
  libgnome2.0-cil libgnomecanvas2-0 libgnomecupsui1.0-1c2a libgnomeprint2.2-0
  libgnomeprintui2.2-0 libgnomeui-0 libgoffice-1-2 libgpgme11 libgtk-cil
  libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtk2.0-cil libgtk2.0-common
  libgtkglext1 libgtkhtml2-0 libgtkhtml3.8-15 libgtkmathview0c2a
  libgtkmm-2.4-1c2a libgtksourceview1.0-0 libgtkspell0 libgucharmap4
  libjpeg-progs libk3b2 libkcal2b libkcddb1 libkdepim1a libkipi0 libkleopatra1
  libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libkscan1 libksieve0
  libktnef1 liblaunchpad-integration0 liblockdev1 liblpint-bonobo0
  libmetacity0 libnautilus-burn3 libnautilus-extension1 libnotify1
  libopenobex-1.0-0 libpanel-applet2-0 libpango1.0-0 libpango1.0-common
  libpoppler1 libpoppler1-glib libpoppler1-qt libpythonize0 libqt3-mt
  librsvg2-2 librsvg2-common libscim8c2a libsensors3 libsexy1 libskim0
  libswfdec0.3 libtdb1 libthunar-vfs-1 libtotem-plparser1 libvte4 libwnck18
  libwxgtk2.6-0 libxfcegui4-4 libxft2 liferea liferea-gtkhtml metacity
  mozilla-firefox-locale-en-gb mplayer nautilus nautilus-cd-burner
  nautilus-sendto notification-daemon orage poppler-utils poster psutils pygmy
  python-glade2 python-gnome2 python-gnome2-desktop python-gnome2-extras
  python-gst python-gst0.10 python-gtk2 python-kde3
  python-launchpad-integration python-opengl python-vte python-wxgtk2.6
  python2.4-cairo python2.4-dev python2.4-glade2 python2.4-gnome2
  python2.4-gnome2-desktop python2.4-gnome2-extras python2.4-gtk2
  python2.4-kde3 python2.4-opengl python2.4-qt3 python2.4-sip4-qt3 qca-tls
  qobex rhythmbox rhythmbox-applet scim scim-gtk2-immodule scim-modules-socket
  scim-qtimm sensors-applet serpentine skim speedcrunch ssh-askpass-gnome
  straw synaptic teatime timer-applet tomboy totem-xine
  totem-xine-firefox-plugin tsclient ttf-dejavu ubuntu-artwork update-manager
  update-notifier vino x-window-system-core xbase-clients xchat-gnome xclock
  xfce4-battery-plugin xfce4-clipman-plugin xfce4-mcs-manager
  xfce4-mcs-plugins xfce4-minicmd-plugin xfce4-mixer xfce4-mixer-alsa
  xfce4-netload-plugin xfce4-panel xfce4-sensors-plugin xfce4-session
  xfce4-systemload-plugin xfce4-utils xfd xfdesktop4 xfprint4 xfwm4
  xfwm4-themes xlogo xorg-driver-fglrx xsane xscreensaver-data xscreensaver-gl
  xterm yelp zenity
0 upgraded, 0 newly installed, 395 to remove and 1 not upgraded.
Need to get 0B of archives.
After unpacking 986MB disk space will be freed.
Do you want to continue [Y/n]? n
``` 
Whoa whoa whoa... something ain't right.  I'll hold off for now, and it isn't much trouble to dig through it for me, but I wanted to bring it to your attention that your command will need to be updated.

---

### Post by Zombiac82 on 2006-04-03
perfect worked like a charm no problems now after I had to reset .ICEauthority
then I finally got this done and now it works again thanks for this info

---

### Post by Jose Catre-Vandis on 2006-04-04
This list took out my gnome desktop as well :-(  (dapper Flight 5)

And killed X server

Had to reinstall. Warning from the stupid to the wise :-)

---

### Post by aysiu on 2006-04-04
[QUOTE=Jose Catre-Vandis]This list took out my gnome desktop as well :-(  (dapper Flight 5)[/QUOTE] Um, it hasn't been tested on Dapper yet.

---

### Post by Jose Catre-Vandis on 2006-04-05
[QUOTE=aysiu]Um, it hasn't been tested on Dapper yet.[/QUOTE]

Has now, lol

---

### Post by .t. on 2006-05-01
[QUOTE=confused57]I uninstalled Kubuntu using copy and paste of Asyiu's instructions, did the trick, but have a question.  When I installed kubuntu-desktop, installation said 426 Mb of packages would be installed; but the uninstallation said 260 Mb would be removed.
No problems, it accomplished what I wanted;  but, I was just wondering...
I liked the look of Kubuntu, but kde used  90% of my memory resources(have 256 Mb) and there were various and sundry quirks in using the desktop.  Only been using Ubuntu for a week, definitely a fun learning experience.[/QUOTE]
Well, when the system installs packages, it keeps the debs in /var/cache/apt/archives, but when you remove those packages, it doesn't delete those cached files. If you were to do apt-get clean, then you'd free up a lot more space, but you'd have to re-download any if you wanted them in future.

---

### Post by .t. on 2006-05-01
Oh, and when I installed the kubuntu-desktop (and then uninstalled it), my GNOME terminal used KDE-style tabs. Weird. Can I get rid of that? I'm on Dapper.

EDIT: Don't worry, I killed and restarted X and all was fine!

---

### Post by aysiu on 2006-05-11
Thanks to [SergioA for finding out what KDE packages get installed on top of Gnome in Dapper](http://www.ubuntuforums.org/showpost.php?p=1006677&postcount=15). Here's Sergio's hard work paying off: ```
sudo apt-get remove adept akregator amarok amarok-xine ark arts artsbuilder bogofilter bogofilter-bdb bogofilter-common debtags enscript fortune-mod fortunes-min gtk2-engines-gtk-qt gwenview imagemagick k3b kaddressbook kamera karm katapult kate kaudiocreator kcontrol kcron kde-guidance kde-style-lipstik kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdm kdnssd keep kfind kghostview khelpcenter kicker kio-apt kio-locate klaptopdaemon klipper kmail kmailcvt kmenuedit kmilo kmix kmplayer-base kmplayer-konq-plugins knetworkconf knotes koffice-data koffice-libs konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb krita krita-data kscd kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwifimanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libdbus-qt-1-1c2 libgadu3 libgpgme11 libgsl0 libjpeg-progs libk3b2 libkcal2b libkcddb1 libkdepim1a libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 libmimelib1c2a libnss-mdns liboggflac3 libpoppler1-qt libpythonize0 librsync1 libruby1.8 libsamplerate0 libsensors3 libskim0 libtdb1 libtunepimp2c2a libxcomposite1 openoffice.org-kde perl-suid poster psutils pykdeextensions python-kde3 python2.4-dev python2.4-kde3 python2.4-qt3 python2.4-sip4-qt3 qca-tls qobex rdiff-backup scim-qtimm skim speedcrunch ttf-gentium vorbis-tools wlassistant
``` This will likely change between now and June 1, but we can update it as we go.

---

### Post by regeya on 2006-05-11
Excellent.  I looked, but didn't see such a thing; what's needed now is a guide for the opposite, meaning an easy way to remove all the GNOME junk.

---

### Post by aysiu on 2006-05-11
[QUOTE=regeya]Excellent.  I looked, but didn't see such a thing; what's needed now is a guide for the opposite, meaning an easy way to remove all the GNOME junk.[/QUOTE] [It already exists](http://www.ubuntuforums.org/showthread.php?t=96046), except that, like this guide until recently, it's missing how to do it in Dapper.

---

### Post by n00bWillingToLearn on 2006-05-15
**************WARNING TO BEGINNERS*************
If you have KDM set as your default Desktop Manger and you try to log out to restart your computer you will just get a grey screen with an X and seemingly no way out. Once you have restarted though the Gnome Desktop Manager will automatically be set back to the default so to restart you can open the terminal and type:
```
 sudo shutdown -r now
```
If you are already stuck at the grey screen you can restart by pressing ctrl + alt + F1 then logging in and typing:
```
 sudo shutdown -r now
```
(The command is the same whether or not you have already logged out)

---

### Post by ronb on 2006-06-19
Aysiu,

I used the command at psychocats for Dapper to remove Kubuntu. It took apache, PHP,  PHPMyAdmin and a few other extras. I got apache back through synaptic package manager. But I can't get PHP back. It says it's install, but phpinfo doesn't work.

Any ideas?
Ron

---

### Post by aysiu on 2006-06-19
ronb, unfortunately, it's not perfect, which is why I always urge people to install *kubuntu-desktop*, *xubuntu-desktop*, or *ubuntu-desktop* with *aptitude* instead of *apt-get* or Synaptic.

*aptitude* will remove the package and its dependencies--only if other packages don't depend on those dependencies.

The psychocats tutorial is based off a fresh Gnome install with a fresh Kubuntu installed on top of it, so it doesn't account for situations like yours.

I wish I knew something about PHP, but I don't even know what *phpinfo* is.

---

### Post by no1wantdthisname on 2006-06-19
And this is why it's a lot easier to just use debfoster.  The metapackages of the different DEs will keep changing, and so you have to keep changing which packages to remove.  And then there's a chance you forgot some packages or remove the dependencies of something important.  Why bother when you can just type 
```
sudo debfoster
```?

---

### Post by aysiu on 2006-06-19
From [http://www.fruit.je/debfoster/](http://www.fruit.je/debfoster/) : > As of 2006-01-01, debfoster is officially deprecated: aptitude does the same stuff as debfoster but integrated into the apt system. 

---

### Post by Raijin87 on 2007-05-28
I've tried out that really long command and also the pruge thing. I'm really new with Linux, so don't know what to do. I want to remove KDE and all it programs. To install it I used "sudo apt-get install kubuntu-desktop". After trying some of the things here, I can still change session to the KDE and all the apps are still here. Should I use the Synaptic Package manager?

Edit: Found my answer!

sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator amarok amarok-xine apport-qt ark arts bogofilter bogofilter-bdb bogofilter-common debtags digikam enscript fftw3 gtk-qt-engine gwenview hwdb-client-kde k3b kaddressbook kaffeine kaffeine-xine kamera karm katapult kate kbstate kcontrol kcron kde-guidance kde-guidance-powermanager kde-icons-mono kde-style-polyester kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-data kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdelibs-data kdelibs4c2a kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards kdeprint kdesktop kdm kdnssd keep kexi kfind kghostview khelpcenter kicker kio-apt kio-locate kipi-plugins klipper kmag kmail kmailcvt kmenuedit kmilo kmix kmousetool kmplayer-base kmplayer-konq-plugins knetworkconf knetworkmanager knotes koffice-data koffice-libs konq-plugins konqueror konqueror-nsplugins konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb kscreensaver ksmserver ksnapshot ksplash ksplash-engine-moodin ksvg ksysguard ksysguardd ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin kwin-style-crystal language-selector-qt libakode2 libarts1-akode libarts1c2a libartsc0 libavahi-compat-libdnssd1 libavahi-qt3-1 libcurl3-gnutls libdbus-qt-1-1c2 libexiv2-0.12 libflac++5c2 libgmp3c2 libgpgme11 libgsl0 libid3tag0 libifp4 libimlib2 libjasper-runtime libjpeg-progs libk3b2 libkcal2b libkcddb1 libkdepim1a libkexiv2-0 libkipi0 libkleopatra1 libkmime2 libkonq4 libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1 liblockdev1 liblua50 liblualib50 libmeanwhile1 libmimelib1c2a libmodplug0c2 libmpcdec3 libmtp5 libmysqlclient15off libnjb5 libofa0 liboggflac3 libopenexr2c2a libopenobex1 libpcre3 libpoppler1-qt libpq5 libpulse0 libpythonize0 libqt-perl libqt3-mt libqt4-core libqt4-gui libqt4-qt3support libqt4-sql librsync1 libruby1.8 libsamplerate0 libskim0 libsmokeqt1 libsqlite0 libtdb1 libtunepimp5 libxine1 libxvmc1 mysql-common networkstatus openoffice.org-kde openoffice.org-style-crystal perl-suid pmount poster psutils pykdeextensions python-kde3 python-qt3 python-qt4 python-sip4 python2.5-dev qca-tls qobex rdiff-backup ruby ruby1.8 scim-qtimm skim software-properties-kde speedcrunch vorbis-tools && sudo apt-get install ubuntu-desktop

---

### Post by firmit on 2008-03-25
Not tried the above line yet. But here's an answer to another question in the OP and other p's.

Packages in the meta-package:
```

tasksel --task-packages kubuntu-desktop

```

!!!USE WITH CAUTION!!! DANGEROUS CODE !!!
So... if you have the balls ( I am not sure if I do )....
```
sudo apt-get remove `tasksel --task-packages kubuntu-desktop`

```
!!!BE WARNED! THIS MAY BE DANGEROUS!!!

After this I guess 
```
sudo apt-get install ubundu-desktop
```
is in place.

---

### Post by s5GbJReJ on 2008-06-07
> **no1wantdthisname said:**
> A much easier way would be to use debfoster.
Install debfoster.
Create the basic file list with 
```
sudo debfoster -q
```
and then 
```
sudo gedit /var/lib/debfoster/keepers
```
erase entries that are unneeded.  In this case, kubuntu-desktop.
```
sudo debfoster
```
will ask about whether you want to keep something or not, and will automatically remove and purge those programs and their unneeded dependencies.  This is a much cleaner and easier way.

Thank you! This worked perfectly.

---

### Post by dagurb on 2008-11-11
Could someone update this for 8.04 and kubuntu-kde4-desktop? I used 
```
sudo apt-get install kubuntu-kde4-desktop
```
and then
```
sudo apt-get remove kubuntu-kde4-desktop
```
and now I'm stuck with a bunch of stuff that wasn't removed. If someone was to update the list from the first post I would be able to throw out the rest.

---

### Post by aysiu on 2008-11-11
```
sudo apt-get remove *nameofmetapackage*
``` will never remove the metapackage's dependencies.

Try this instead: ```
sudo apt-get remove adept adept-batch adept-common adept-installer adept-manager adept-notifier adept-updater akregator apport-qt ark-kde4 cryptsetup debtags dolphin-kde4 dragonplayer gnupg-agent gpgsm gwenview-kde4 hplip-gui jockey-kde juk-kde4 kaddressbook kamera-kde4 karm kate-kde4 kde-icons-oxygen kde4libs-bin kdebase-bin kdebase-bin-kde3 kdebase-bin-kde4 kdebase-data-kde4 kdebase-kio-plugins kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data kdelibs-data kdelibs4c2a kdelibs5 kdelibs5-data kdemultimedia-kio-plugins-kde4 kdepim-kio-plugins kdepim-kresources kdepim-wizards kdepimlibs-data kdepimlibs5 kdesktop kdesudo kdesudo-kde4 kdm-kde4 kfind-kde4 khelpcenter khelpcenter-kde4 klipper-kde4 kmail kmilo-kde4 kmix-kde4 knetworkconf-kde4 knotes konqueror-kde4 konqueror-nsplugins-kde4 konsole konsole-kde4 kontact kopete-kde4 korganizer kppp-kde4 krdc-kde4 krfb-kde4 kscd-kde4 ksnapshot-kde4 ksysguard-kde4 ksysguardd-kde4 kubuntu-artwork-usplash kubuntu-default-settings kubuntu-docs kubuntu-kde4-desktop kubuntu-konqueror-shortcuts kwalletmanager-kde4 kwin-kde4 language-selector-qt libarts1c2a libartsc0 libaudio2 libavahi-qt3-1 libavcodec1d libavutil1d libcapseo0 libcaptury0 libclucene0ldbl libdbus-qt-1-1c2 libept0 libexiv2-2 libfftw3-3 libgif4 libgmp3c2 libgsm1 libkcal2b libkcddb4-kde4 libkdepim1a libkleopatra1 libkmime2 libkonq4 libkonq5 libkonq5-templates libkpimexchange1 libkpimidentities1 libksba8 libksieve0 libktnef1 liblua50 liblualib50 libmad0 libmimelib1c2a libmodplug0c2 libmpcdec3 libmysqlclient15off libofa0 libokularcore1-kde4 libphonon4 libplasma1 libpoppler-qt4-2 libpostproc1d libpq5 libqca2 libqca2-plugin-ossl libqimageblitz4 libqt3-mt libqt4-core libqt4-gui libqt4-qt3support libqt4-sql libraptor1 librasqal0 librdf0 libskim0 libsoprano4 libstreamanalyzer0 libstreams0 libstrigiqtdbusclient0 libtunepimp5 libvncserver0 libxapian15 libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin libxine1-console libxine1-ffmpeg libxine1-misc-plugins libxine1-plugins libxine1-x libxvmc1 libzip1 mysql-common network-manager-kde networkstatus okular-kde4 openoffice.org-kde openoffice.org-style-crystal oxygen-cursor-theme pinentry-qt python-qt3 python-qt4 python-qt4-common python-qt4-dbus python-reportlab python-sip4 scim-bridge-client-qt scim-qtimm skim software-properties-kde speedcrunch strigi-daemon system-config-printer-kde systemsettings-kde4 ttf-arphic-ukai && sudo apt-get install ubuntu-desktop
```

---

### Post by marty_oc on 2009-01-02
For 8.10 Intrepid Ibex this worked fine:
> sudo apt-get remove adept akregator amarok amarok-common amarok-engine-xine apport-qt ark  dolphin dragonplayer exiv2 foomatic-db-gutenprint gdebi-kde  gnupg-agent gtk-qt-engine guidance-power-manager gwenview hpijs-ppds  hplip-gui ijsgutenprint imagemagick install-package jockey-kde k3b  k3b-data kaddressbook kamera kate kde-icons-oxygen kde-printer-applet  kde-window-manager kde-zeroconf kdebase-bin kdebase-data kdebase-plasma  kdebase-runtime kdebase-runtime-bin-kde4 kdebase-runtime-data  kdebase-runtime-data-common kdebase-workspace-bin kdebase-workspace-data  kdebase-workspace-libs4+5 kdebluetooth kdegraphics-strigi-plugins  kdelibs-bin kdelibs-data kdelibs4c2a kdelibs5 kdelibs5-data  kdemultimedia-kio-plugins kdepasswd kdepim-kresources  kdepim-strigi-plugins kdepim-wizards kdepimlibs-data kdepimlibs5  kdeplasma-addons kdeplasma-addons-data kdeplasma-addons-libs4 kdesudo  kdm kfind kgrubeditor khelpcenter4 klipper kmag kmail kmix  kmousetool knotes konqueror konqueror-nsplugins  konqueror-plugin-searchbar konsole kontact konversation kopete  korganizer krdc krfb ksnapshot ksysguard ksysguardd ksystemlog  ktimetracker ktorrent kubuntu-artwork-usplash kubuntu-default-settings  kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kvkbd  kwalletmanager language-selector-qt libakonadiprivate1 libarts1c2a  libartsc0 libaudio2 libavahi-qt3-1 libcapseo0 libcaptury0  libclucene0ldbl libdbus-1-qt3 libdbus-qt-1-1c2 libexiv2-4 libfftw3-3  libflac++6 libgeoip1 libifp4 libk3b3 libkcddb4 libkdecorations4  libkdepim4 libkholidays4 libkipi-common libkipi5 libkleo4 libkonq5  libkonq5-templates libkpgp4 libksieve4 libkwineffects1 liblua50  liblualib50 libmimelib4 libmodplug0c2 libmpcdec3 libmysqlclient15off  libnjb5 libofa0 libokularcore1 libphonon4 libplasma2 libpoppler-qt4-3  libpq5 libqca2 libqca2-plugin-ossl libqimageblitz4 libqt3-mt  libqt4-assistant libqt4-core libqt4-dbus libqt4-designer libqt4-help  libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql  libqt4-sql-mysql libqt4-svg libqt4-test libqt4-webkit libqt4-xml  libqt4-xmlpatterns libqtcore4 libqtgui4 libraptor1 librasqal0 librdf0  libruby1.8 libsearchclient0 libsoprano4 libstreamanalyzer0 libstreams0  libstrigihtmlgui0 libstrigiqtdbusclient0 libtunepimp5 libvncserver0  libxcb-shape0 libxcb-shm0 libxcb-xv0 libxine1 libxine1-bin  libxine1-console libxine1-misc-plugins libxine1-x libxvmc1 libzip1  mediamanager mysql-common network-manager-kde okular  okular-extra-backends openoffice.org-kde openoffice.org-style-crystal  oxygen-cursor-theme phonon phonon-backend-gstreamer phonon-backend-xine  pinentry-gtk2 pinentry-qt4 plasmoid-quickaccess python-kde4 python-qt3  python-qt4 python-qt4-common python-qt4-dbus python-reportlab  python-sip4 qt4-qtconfig raptor-utils redland-utils ruby ruby1.8  software-properties-kde soprano-daemon speedcrunch strigi-client  strigi-daemon system-config-printer-kde systemsettings ttf-dustin  update-manager-kde update-notifier-kde

---

### Post by Neostar2119 on 2009-01-03
If I uninstall the KDE, will KDE-based applications still work on my machine?

---

### Post by UniqueCrash5 on 2009-01-26
The marty-oc's 8.10 list seems to have done the trick for me just fine.

 Aysiu, it may be helpful edit your first post to make it clear which version your initial list is for, and to add a link to the list for 8.10 Intrepid. And thanks for all your awesome posts btw!

---

