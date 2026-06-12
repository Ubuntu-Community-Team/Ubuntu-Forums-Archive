---
title: "HowTo: Fully Uninstall the ubuntu-desktop meta-package"
date: 2005-11-28
forum: Outdated Tutorials &amp; Tips
---

### Post by aysiu on 2005-11-28
As you may or may not know, if you install the package called ubuntu-desktop, a lot of other packages will be installed so that you get the full Gnome experience in addition to KDE. If, however, you *uninstall* ubuntu-desktop, none of the other "full Gnome experience" packages will be uninstalled. You may have installed ubuntu-desktop to get the Gnome experience but then found it cluttered things up too much. To uninstall all the other junk, open up a terminal (Applications > Accessories > Terminal) and copy and paste this into your terminal: ```
sudo apt-get remove bittorrent bluez-pin bug-buddy capplets-data contact-lookup-applet dbus-1-utils desktop-file-utils eog esound evince evolution evolution-data-server evolution-exchange evolution-plugins evolution-webcal file-roller firefox firefox-gnome-support fping gaim gaim-data gcalctool gconf-editor gdb gdm gedit gedit-common gimp gimp-data gimp-python gksu gnome-about gnome-app-install gnome-applets gnome-applets-data gnome-btdownload gnome-control-center gnome-cups-manager gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-icon-theme gnome-keyring gnome-media gnome-menus gnome-mime-data gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-session gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes gnome-utils gnome-volume-manager gnome2-user-guide gnomemeeting gstreamer0.8-esd gstreamer0.8-gnomevfs gthumb gtk2-engines-clearlooks gtk2-engines-crux gtk2-engines-industrial gtk2-engines-lighthouseblue gtk2-engines-mist gtk2-engines-pixbuf gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-thinice gtkhtml3.8 gucharmap guile-1.6-libs hal-device-manager hwdb-client language-selector launchpad-integration libaa1 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libcamel1.2-6 libcompfaceg1 libcroco3 libdjvulibre15 libebook1.2-5 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1 libedataserver1.2-4 libedataserverui1.2-6 libeel2-2 libeel2-data libegroupwise1.2-8 libesd-alsa0 libexchange-storage1.2-0 libgail-common libgail17 libgda2-3 libgda2-common libgimp2.0 libgksu1.2-0 libgksuui1.0-0 libglade2-0 libgle3 libglib-perl libglib2.0-data libgnome-desktop-2 libgnome-keyring0 libgnome-menu2 libgnome-pilot2 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomecupsui1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgsf-1 libgtk2-perl libgtkhtml2-0 libgtkhtml3.8-15 libgtksourceview-common libgtksourceview1.0-0 libgtkspell0 libgtop2-5 libgucharmap4 libguile-ltdl-1 libkpathsea3 liblaunchpad-integration0 liblircclient0 liblpint-bonobo0 libmetacity0 libnautilus-burn2 libnautilus-extension1 libnotify0 libopenal0 libopenh323-1.15.3c2 libpanel-applet2-0 libpisync0 libpoppler0c2-glib libpt-1.8.3c2 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libqthreads-12 librsvg2-2 librsvg2-common libsmpeg0c2 libsoup2.2-8 libtotem-plparser0 libvte-common libvte4 libwmf0.2-7 libwnck-common libwnck18 libxklavier10 libxml2-utils libxres1 metacity nautilus nautilus-cd-burner nautilus-data nautilus-sendto notification-daemon openoffice.org2-evolution openoffice.org2-gnome python-glade2 python-gmenu python-gnome2 python-gnome2-extras python-gst python-gtk2 python-launchpad-integration python2.4-cairo python2.4-glade2 python2.4-gnome2 python2.4-gnome2-extras python2.4-gtk2 rdesktop rhythmbox rss-glx serpentine shared-mime-info smeg sound-juicer ssh-askpass-gnome synaptic system-tools-backends totem totem-gstreamer tsclient ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-sounds update-manager update-notifier vino vnc-common whois xchat xchat-common xsane xsane-common xscreensaver xscreensaver-data xscreensaver-gl xsltproc xvncviewer yelp zenity
``` This will remove all the extra "junk" that was installed along with the ubuntu-desktop meta-package. P.S. I haven't tested this yet. I just know it should work in theory. If anyone is brave enough to test it, could she or he post a reply in this thread so others won't have to worry.

**Edit**: This definitely works. I've tested it out on a fresh Kubuntu installation.

For Dapper, go [here](http://www.psychocats.net/ubuntu/purekde).

---

### Post by N8K99 on 2005-11-29
I did something rather similiar, although not as exact as you. I have an older machine with memory issues, so both KDE and GNOME are way too sluggish (tried them both) so I installed enlightenment from the repositories ( tried out the howto for e17 but like 16 much better) so I hd to basically remove all the large amounts of junk from my system. Basically, I opened synaptic and scrolled down and removed anything that said Gnome or looked like it related to gnome and KDE, although I left kicker on just for giggles. You single line apt-get remove looks like it will pretty much do the trick when it comes to removing unnecessary programs.

---

### Post by aysiu on 2005-11-29
I just revised it, too--as I wasn't absolutely sure it would work.
I did a clean installation of Kubuntu and found out which packages were marked for installation after typing ```
sudo apt-get install ubuntu-desktop
```

---

### Post by GoldBuggie on 2005-12-06
*original post removed by ME so not to get ppl confused*

---

### Post by aysiu on 2005-12-06
See, that's how I did it originally, too. It made logical sense--you take a look at the two sets of packages, eliminate what they have in common, and see what's left.

Theoretically, it should work, but it didn't.

So I changed it to be what really gets installed when you install ubuntu-desktop (I did it with a fresh reinstall of Kubuntu).

---

### Post by mint on 2005-12-07
I've found that liberal applications of deborphan (apt-get install deborphan).  Will help you clean up all of the libraries and such that get left hanging after a big uninstall operation like that.

e.g.

To get a list of orphaned library packages:
$ deborphan

To get a list of all orphans:
$ deborphan -a

To remove orphaned libraries:
# apt-get --purge remove $(deborphan)

To remove python orphans (lots on a default install):
# apt-get --purge remove $(deborphan -a | awk {'print $2'} | grep ^py)

---

### Post by geearf on 2005-12-09
Thanks for this how to, I installed ubuntu-desktop but I never really used it, so it might be good to remove it for a while.

---

### Post by N8K99 on 2005-12-10
[QUOTE=mint]
To remove orphaned libraries:
# apt-get --purge remove $(deborphan)
[/QUOTE] I tried this out, and well it didn't help me at all. Mostly this was because I had already removed all the Gnome stuff from my machine and was running Enlightenment as my Desktop Shell. When I ran the above command, it removed some libraries that enabled apt-get install to work. :???: Oh well, it's not a weekend if I am not completely re-vamping my Linux box yet again!! i'm going to have to learn to be happy with what I've got going on. Fortunately, this time all my data was backed up!:cool:

---

### Post by starscalling on 2005-12-10
[QUOTE=N8K99]I tried this out, and well it didn't help me at all. Mostly this was because I had already removed all the Gnome stuff from my machine and was running Enlightenment as my Desktop Shell. When I ran the above command, it removed some libraries that enabled apt-get install to work. :???: Oh well, it's not a weekend if I am not completely re-vamping my Linux box yet again!! i'm going to have to learn to be happy with what I've got going on. Fortunately, this time all my data was backed up!:cool:[/QUOTE]

lol im with ya.... thinking of doing the dapper install >_> my audio hates me right now anyway :P
though ive got to ask the thread wtf are ya thinkin sortof ~_^ [not meant meanly i swear..] i just mean why not do the server install and then install ONLY what you need?

---

### Post by N8K99 on 2005-12-10
[QUOTE=starscalling]lol im with ya.... thinking of doing the dapper install >_> my audio hates me right now anyway :P
though ive got to ask the thread wtf are ya thinkin sortof ~_^ [not meant meanly i swear..] i just mean why not do the server install and then install ONLY what you need?[/QUOTE]I have done the server install- at least three times for every time I have done a full install. Each time I get things nice and working and go straight with enlightenment (as an aside, I'm not certain if it's really the way the environment acts or if I just enjoy constantingly striving for 'enlightenment') and things work, except that I have great difficulty getting the xorg.conf to play nicely and give me a screen with anything but 400x600 resolution. So I do the full install and strip in order to get multiple resolutions resolved automagically. I know kinda weak but it's how I  have beeen rolling. Still it's an educational process for me none the less. {'^_^'}

---

### Post by higgins on 2005-12-14
I have followed the method in this thread and it has worked perfectly. Thanks


:D :D :D

---

### Post by aysiu on 2005-12-14
[QUOTE=higgins]I have followed the method in this thread and it has worked perfectly. Thanks


:D :D :D[/QUOTE] Good to know.

---

### Post by pmj on 2005-12-14
[QUOTE=GoldBuggie]and for uninstalling kubuntu
```
sudo apt-get remove adept akode akregator amarok ark arts dbus gtk2-engines-gtk-qt gwenview ivman k3b kaddressbook kaffeine-gstreamer kamera karm katapult kate kaudiocreator kcontrol kcron kde-guidance kde-systemsettings kdeadmin-kfile-plugins kdebase-kio-plugins kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-wizards kdeprint kdesktop kdm kfind kghostview khelpcenter kicker kio-apt kio-locate klaptopdaemon klipper kmail kmenuedit kmilo kmix knetworkconf knotes konq-plugins konqueror konqueror-nsplugins konserve konsole kontact konversation kooka kopete korganizer kpdf kpf kppp krfb krita kscd ksmserver ksnapshot ksplash ksvg ksysguard ksystemlog kubuntu-default-settings kubuntu-konqueror-shortcuts kuser kwalletmanager kwifimanager kwin pmount python-opengl python2.3-opengl python2.4-opengl qca-tls ttf-dejavu vorbis-tools
``` [/QUOTE]

I tried this one to completely get rid of KDE and like half of Gnome went along with it. Somehow the system stayed up though and Gnome was fully fixed by an apt-get install ubuntu-desktop, which was a 249MB download.

And for some reason Java, Azureus and totem-xine disappeared at the same time.

---

### Post by aysiu on 2005-12-14
[QUOTE=pmj]I tried this one to completely get rid of KDE and like half of Gnome went along with it. Somehow the system stayed up though and Gnome was fully fixed by an apt-get install ubuntu-desktop, which was a 249MB download.

And for some reason Java, Azureus and totem-xine disappeared at the same time.[/QUOTE] To uninstall Kubuntu, follow [this HowTo](http://www.ubuntuforums.org/showthread.php?t=96048). GoldBuggie's post was speculating--it wasn't a real HowTo.

---

### Post by GoldBuggie on 2005-12-14
IIIiiiihhh:confused: I thought that was clear...sorry about the trouble.

---

### Post by aysiu on 2005-12-14
[QUOTE=GoldBuggie]IIIiiiihhh:confused: I thought that was clear...sorry about the trouble.[/QUOTE] It was clear to me when you posted it, but it may not have been to someone else who stumbled upon the thread later.

---

### Post by pmj on 2005-12-15
Nah, I was just browsing the forum and stumbled on this thread and thought to myself, why not get rid of the KDE stuff I never use?

I was just letting you know how it went so that nobody else tries it. :)

---

### Post by aysiu on 2005-12-15
[QUOTE=pmj]Nah, I was just browsing the forum and stumbled on this thread and thought to myself, why not get rid of the KDE stuff I never use?[/quote] Can you try the **real** HowTo (i.e., the first post in the thread) and let me know if it doesn't work? If so, please post the entire output of the command and its outcome in the thread--don't just say, "it doesn't work."

> 
I was just letting you know how it went so that nobody else tries it. :) And I'm telling you to use the command in the original post (one which I tried out on a fresh Kubuntu installation), not the one that you quoted from Goldbuggie.

Please read **the entire thread** and the context of the post you quoted and tried out.

If you're not going to read the entire thread, don't just pick a random post to try out something--go to the first post with **the real HowTo instructions**.

If you try the instructions **from the first post** and have problems, let me know.

---

### Post by GoldBuggie on 2005-12-15
/me has used his undo button

---

### Post by kairu0 on 2005-12-15
This was a really good idea for a HOWTO, aysiu!

How many readers have found it helpful?

---

### Post by aysiu on 2005-12-15
[QUOTE=kairu0]This was a really good idea for a HOWTO, aysiu!

How many readers have found it helpful?[/QUOTE] I don't know. Actually, I usually point people to my "uninstall kubuntu" thread because most Ubuntu users are using Gnome and want to try KDE, not vice versa.

---

### Post by pmj on 2005-12-15
Thanks, but as I believe I already told you, I already installed everything that went missing. It only took a few minutes. My computer works perfectly and KDE is gone. I don't need to use another tutorial.

I *did* read the whole thread and I *was* aware that the command I ran was not part of the howto. And I know I should have been more careful. I'm just telling you how it went so that anyone else reading knows and won't do the same.

---

### Post by aysiu on 2005-12-15
Cool.

---

### Post by desiboston on 2006-03-06
This also resoled the issue described here. It happened to me.

[http://kubuntuforums.net/forums/index.php?topic=2357.msg9044#msg9044](http://kubuntuforums.net/forums/index.php?topic=2357.msg9044#msg9044)

---

### Post by aysiu on 2006-03-06
[QUOTE=desiboston]This also resoled the issue described here. It happened to me.

[http://kubuntuforums.net/forums/index.php?topic=2357.msg9044#msg9044](http://kubuntuforums.net/forums/index.php?topic=2357.msg9044#msg9044)[/QUOTE] If you follow that link to this page:
[http://doc.gwos.org/index.php/Uninstall_kubuntu-desktop](http://doc.gwos.org/index.php/Uninstall_kubuntu-desktop)

...you'll see it's just the same tutorial mirrored on another website.

---

### Post by Tapatio on 2006-05-05
It didn't work for me. I copy-pasted the command and apt-get wanted to remove a lot of my KDE packages too!! Any idea why? By the way, I installed Ubuntu 5.10 first and later installed the kubuntu-desktop package. I don't know if this has anything to do with it. 
This is what I got:

Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  adept akode akregator amarok amarok-gstreamer amarok-xine apollon ark arts artsbuilder bittorrent bluez-pin bug-buddy capplets-data
  contact-lookup-applet dbus-1-utils desktop-file-utils eog esound evince evolution evolution-data-server evolution-exchange
  evolution-plugins evolution-webcal file-roller firefox firefox-gnome-support fping gaim gaim-data galternatives gcalctool gconf-editor
  gdb gdm gedit gedit-common gimp gimp-data gimp-python gksu gnome-about gnome-alsamixer gnome-app-install gnome-applets gnome-applets-data
  gnome-btdownload gnome-control-center gnome-cups-manager gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-icon-theme
  gnome-keyring gnome-media gnome-menus gnome-mime-data gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot
  gnome-pilot-conduits gnome-session gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes
  gnome-utils gnome-volume-manager gnome2-user-guide gnomemeeting gparted gstreamer0.8-esd gstreamer0.8-gnomevfs gthumb
  gtk2-engines-clearlooks gtk2-engines-crux gtk2-engines-gtk-qt gtk2-engines-industrial gtk2-engines-lighthouseblue gtk2-engines-mist
  gtk2-engines-pixbuf gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-thinice gtkhtml3.8 gucharmap guile-1.6-libs gwc gwenview
  hal-device-manager hwdb-client k3b k3b-mp3 k3blibs kaddressbook kaffeine kaffeine-gstreamer kamera kappfinder karm katapult kate
  kaudiocreator kcontrol kcron kde-guidance kde-style-lipstik kde-systemsettings kdeadmin-kfile-plugins kdebase-bin kdebase-kio-plugins
  kdebluetooth kdegraphics-kfile-plugins kdelibs kdelibs-bin kdelibs4c2 kdemultimedia-kappfinder-data kdemultimedia-kfile-plugins
  kdemultimedia-kio-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepasswd kdepim-kio-plugins kdepim-kresources kdepim-wizards
  kdeprint kdesktop kdm kfind kghostview khelpcenter kicker kio-apt kio-locate klaptopdaemon klipper kmail kmenuedit kmilo kmix
  knetworkconf knotes koffice-libs konq-plugins konqueror konqueror-nsplugins konserve konsole kontact konversation kooka kopete korganizer
  kpdf kpf kppp krdc krfb krita kscd kscreensaver ksmserver ksnapshot ksplash ksvg ksysguard ksystemlog kubuntu-default-settings
  kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kuser kwalletmanager kwifimanager kwin language-selector launchpad-integration
  libaa1 libarts1c2 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libcamel1.2-6 libcompfaceg1 libcroco3
  libdbus-qt-1-1c2 libdjvulibre15 libebook1.2-5 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1 libedataserver1.2-4 libedataserverui1.2-6
  libeel2-2 libeel2-data libegroupwise1.2-8 libesd-alsa0 libexchange-storage1.2-0 libgail-common libgail17 libgda2-3 libgda2-common
  libgimp2.0 libgksu1.2-0 libgksuui1.0-0 libglade2-0 libgle3 libglib-perl libglib2.0-data libgnome-desktop-2 libgnome-keyring0
  libgnome-menu2 libgnome-pilot2 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnomecanvas2-0
  libgnomecanvas2-common libgnomecups1.0-1 libgnomecupsui1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0
  libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgsf-1 libgtk2-perl libgtkhtml2-0
  libgtkhtml3.8-15 libgtksourceview-common libgtksourceview1.0-0 libgtkspell0 libgtop2-5 libgucharmap4 libguile-ltdl-1 libkcal2b libkcddb1
  libkdepim1a libkipi0 libkleopatra1 libkmime2 libkonq4 libkpathsea3 libkpimexchange1 libkpimidentities1 libkscan1 libksieve0 libktnef1
  liblaunchpad-integration0 liblircclient0 liblpint-bonobo0 libmetacity0 libnautilus-burn2 libnautilus-extension1 libnotify0 libopenal0
  libopenh323-1.15.3c2 libpanel-applet2-0 libpisync0 libpoppler0c2-glib libpt-1.8.3c2 libpt-plugins-alsa libpt-plugins-v4l
  libpt-plugins-v4l2 libqthreads-12 librsvg2-2 librsvg2-common libsmpeg0c2 libsoup2.2-8 libtotem-plparser0 libvte-common libvte4
  libwmf0.2-7 libwnck-common libwnck18 libxklavier10 libxml2-utils libxres1 metacity nautilus nautilus-cd-burner nautilus-data
  nautilus-open-terminal nautilus-sendto notification-daemon openoffice.org2-evolution openoffice.org2-gnome openoffice.org2-kde
  python-glade2 python-gmenu python-gnome2 python-gnome2-extras python-gst python-gtk2 python-kde3 python-launchpad-integration python-vte
  python2.4-cairo python2.4-glade2 python2.4-gnome2 python2.4-gnome2-extras python2.4-gtk2 python2.4-kde3 rdesktop rhythmbox rss-glx
  sanekonsole serpentine shared-mime-info smeg sound-juicer ssh-askpass-gnome synaptic system-tools-backends totem totem-gstreamer tsclient
  ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-sounds update-manager update-notifier vino vnc-common whois xchat xchat-common xsane
  xsane-common xscreensaver xscreensaver-data xscreensaver-gl xsltproc xvncviewer yelp zenity
0 upgraded, 0 newly installed, 349 to remove and 70 not upgraded.
Need to get 0B of archives.
After unpacking 909MB disk space will be freed.
Do you want to continue [Y/n]? n

---

### Post by aysiu on 2006-05-05
I did it on a fresh Kubuntu install--totally fresh. I hadn't installed anything else on top of it.

> By the way, I installed Ubuntu 5.10 first and later installed the kubuntu-desktop package. I don't know if this has anything to do with it. So, yes, I think that may have something to do with it.

What I would do is look at all the stuff it's planning to remove, copy and paste that to a Kate document and then delete from that document all the stuff you want to keep. Then paste it back in after the command ```
sudo apt-get remove
```

**Or**... just go ahead and remove it all--the configuration files will still be there, as will the .debs. After that, do ```
sudo apt-get install kubuntu-desktop
``` and everything you need to have come back will be reinstalled.

---

### Post by Tapatio on 2006-05-06
Thanks for your answer aysiu. I just did it as N8K99. I opened synaptic and removed anything that was gnome related. Well, almost everything, 'cause there were some programs I wanted to keep. Thanks anyway. Good HOWTO.

---

### Post by markp1989 on 2009-11-09
have you got a uptodate version of this how to?
 
thanks markp1989

---

### Post by Tibuda on 2009-11-11
> **markp1989 said:**
> have you got a uptodate version of this how to?
 
thanks markp1989
[http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)
Bookmark this psychocats site.

---

### Post by markp1989 on 2009-11-12
> **danielrmt said:**
> [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)
Bookmark this psychocats site.

thanks :D

---

### Post by Kubischbuntu on 2010-05-04
I originally installed Ubuntu Jaunty - and then decided to try the KDE desktop so installed that. I have not used gnome since and actually ran the update to Lucid in KDE. 

 I have now decided that I like KDE better so want to get rid of all the gnomes. Given this history - Can I use the method mentioned above for that - or do I need to do a clean Kubuntu install??

---

### Post by aysiu on 2010-05-04
> **Kubischbuntu said:**
> I originally installed Ubuntu Jaunty - and then decided to try the KDE desktop so installed that. I have not used gnome since and actually ran the update to Lucid in KDE. 

 I have now decided that I like KDE better so want to get rid of all the gnomes. Given this history - Can I use the method mentioned above for that - or do I need to do a clean Kubuntu install??
You can use this method here:
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---

### Post by Kubischbuntu on 2010-05-05
Hi,

wow that is a lot of stuff for one command line command

One more question - i noticed that at the end it does an apt-get install kubuntu - why is that? Given that I am already running Kubuntu (see history in prev post) If I run it again will it just ignore the things that are already installed?

---

### Post by aysiu on 2010-05-05
It's tacked on just off on the off-chance that something gets removed. If nothing gets removed, the last command will do nothing.

---

### Post by Kubischbuntu on 2010-05-05
OK here is what I get back:

[sudo] password for kubisch: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package compiz is not installed, so not removed
Package compiz-core is not installed, so not removed
Package compiz-fusion-plugins-main is not installed, so not removed
Package compiz-gnome is not installed, so not removed
Package compiz-plugins is not installed, so not removed
Package compizconfig-backend-gconf is not installed, so not removed
Package evolution is not installed, so not removed
Package evolution-couchdb is not installed, so not removed
Package evolution-exchange is not installed, so not removed
Package evolution-indicator is not installed, so not removed
Package evolution-plugins is not installed, so not removed
Package libcompizconfig0 is not installed, so not removed
Package notification-daemon is not installed, so not removed
Package scrollkeeper is not installed, so not removed
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libxine1: Depends: libxine1-x (= 1.1.17-1ubuntu3) but it is not going to be installed
E: Broken packages
kubisch@squarebear:~$ 


Any ideas?

---

### Post by Kubischbuntu on 2010-05-06
Hi, 

sorry my question may have been a bit short in the last post.;)

Basically while I verbally understand what the response is saying - I am a bit too new to this to comprehend what this means and what I should be doing about it. 

Could anybody give me a hint please?

Thanx a lot

---

### Post by aysiu on 2010-05-06
Usually that kind of error message indicates you have conflicting software sources (otherwise known as software repositories--basically online servers Ubuntu uses to fetch software you want to install).

Can you post the output of these commands? ```
sudo apt-get update
cat /etc/apt/sources.list
```

---

### Post by Kubischbuntu on 2010-05-07
Sorry for the delay - I posted the question from work 

OK here it goes:

For the first one I get:

kubisch@squarebear:~$ sudo apt-get update
[sudo] password for kubisch: 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_NZ
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_NZ
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_NZ
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_NZ
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg [189B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_NZ
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_NZ
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_NZ
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_NZ
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release.gpg [189B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/main Translation-en_NZ                                    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_NZ                              
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_NZ                                
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_NZ                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release                                                                    
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release [38.5kB]                                                 
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security Release [32.5kB]                                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages                                                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages                                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources                                                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources                                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages                                                          
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources                                                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages                                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources                                                         
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages [115kB]                                            
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages [14B]                                        
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources [49.9kB]                                            
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources [14B]                                         
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages [8,371B]                                       
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Sources [2,392B]                                       
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages [14B]                                       
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Sources [14B]                                        
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Packages [2,067B]                                         
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Packages [14B]                                      
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/main Sources [1,300B]                                          
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/restricted Sources [14B]                                       
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Packages [815B]                                       
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/universe Sources [780B]                                        
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Packages [14B]                                      
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-security/multiverse Sources [14B]                                       
Fetched 252kB in 16s (15.4kB/s)                                                                                
Reading package lists... Done


For the second one I get: 
kubisch@squarebear:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
# deb-src [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-security multiverse
# deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) karmic free non-free

By the way how do you make those scrollable text boxes in your posts?

---

### Post by Kubischbuntu on 2010-05-11
Bump! 

Psychocat - where are you?

---

### Post by Kubischbuntu on 2010-05-14
Bumpetybumpbump!!!

---

### Post by thecursedfly on 2010-06-12
> **danielrmt said:**
> [http://www.psychocats.net/ubuntu/purexfce](http://www.psychocats.net/ubuntu/purexfce)
Bookmark this psychocats site.
Hello all,
my purpose is to revert a full ubuntu desktop installation into a ubuntu minimal one (_[link]("https://help.ubuntu.com/community/Installation/MinimalCD")_), and then reinstall only the stuff I want. Either this or find a way to install ubuntu mini through wubi (not possible afaik). (Please don't propose alternative solutions like partitioning and so on, I'm interested in this specifical way of installing ubuntu.)

Is it so that using the instructions in the quoted link I get my purpose (apart from the last instruction, "apt-get install xubuntu-desktop")?
```
sudo apt-get remove adium-theme-ubuntu alacarte  app-install-data-partner binfmt-support  binutils bluez-gstreamer branding-ubuntu brltty brltty-x11  capplets-data  checkbox checkbox-gtk cli-common compiz compiz-core  compiz-fusion-plugins-main compiz-gnome compiz-plugins  compizconfig-backend-gconf computer-janitor computer-janitor-gtk  couchdb-bin dcraw desktopcouch empathy empathy-common eog erlang-base  erlang-crypto erlang-inets erlang-mnesia erlang-public-key  erlang-runtime-tools erlang-ssl erlang-syntax-tools erlang-xmerl  evolution evolution-common evolution-couchdb evolution-data-server  evolution-data-server-common evolution-exchange evolution-indicator  evolution-plugins evolution-webcal example-content f-spot gbrainy gcc  gcc-4.4 gconf-defaults-service gconf-editor gdm-guest-session gedit  gedit-common gnome-about gnome-applets gnome-applets-data  gnome-bluetooth  gnome-control-center gnome-disk-utility gnome-media gnome-media-common  gnome-nettool gnome-panel gnome-panel-data gnome-power-manager  gnome-screensaver gnome-session gnome-session-canberra gnome-terminal  gnome-terminal-data gnome-themes-selected gnome-themes-ubuntu  gnome-user-share gnome-utils gstreamer0.10-gnonlin  gstreamer0.10-plugins-base-apps gstreamer0.10-tools gvfs-fuse gwibber  gwibber-service humanity-icon-theme ibus ibus-gtk ibus-m17n ibus-table  indicator-applet indicator-applet-session indicator-me  indicator-messages  indicator-session indicator-sound libanthy0 libart2.0-cil libc-dev-bin  libc6-dev libcamel1.2-14 libcanberra-pulse libcompizconfig0  libcouchdb-glib-1.0-2 libcryptui0 libdecoration0  libdesktopcouch-glib-1.0-2 libebackend1.2-0 libebook1.2-9 libecal1.2-7  libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-11  libedataserverui1.2-8 libegroupwise1.2-13 libexchange-storage1.2-3  libexempi3 libflickrnet2.2-cil libgail-gnome-module libgconf2.0-cil  libgd2-xpm libgdata-google1.2-1 libgdata1.2-1 libgdict-1.0-6 libgdiplus  libgdu-gtk0 libgif4 libglade2.0-cil libglib2.0-cil libglitz-glx1  libglitz1 libgmime2.4-cil libgnome-keyring1.0-cil libgnome-media0  libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1  libgnome2.24-cil libgnomepanel2.24-cil libgoocanvas-common  libgoocanvas3  libgpgme11 libgpod-common libgpod4 libgraphite3 libgtk2.0-cil  libgtkhtml-editor-common libgtkhtml-editor0 libgtkhtml3.14-19  libgtksourceview2.0-0 libgtksourceview2.0-common libgweather-common  libgweather1 libhyphen0 libibus1 libical0 libido-0.1-0  liblaunchpad-integration1.0-cil liblpint-bonobo0 libm17n-0  libmetacity-private0 libmono-addins-gui0.2-cil libmono-addins0.2-cil  libmono-cairo2.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil  libmono-i18n-west2.0-cil libmono-posix2.0-cil libmono-security2.0-cil  libmono-sharpzip2.84-cil libmono-sqlite2.0-cil  libmono-system-data2.0-cil  libmono-system-runtime2.0-cil libmono-system-web2.0-cil  libmono-system2.0-cil libmono2.0-cil libmtp8 libmusicbrainz4c2a  libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon27-gnutls  libnunit2.4-cil libotf0 libpisock9 libpisync1 libprotobuf5 libprotoc5  libpst4 libpth20 libraptor1 librasqal2 librdf0 libsctp1  libsdl1.2debian-pulseaudio libsqlite0 libstlport4.6ldbl  libtelepathy-farsight0 libubuntuone-1.0-1 libupower-glib1  libwmf0.2-7-gtk  light-themes linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic  linux-headers-generic linux-libc-dev lksctp-tools m17n-contrib m17n-db  manpages-dev media-player-info metacity metacity-common mono-2.0-gac  mono-gac mono-runtime mousetweaks nautilus nautilus-data  nautilus-sendto  nautilus-sendto-empathy nautilus-share obexd-client  openoffice.org-base-core openoffice.org-calc openoffice.org-common  openoffice.org-core openoffice.org-draw openoffice.org-emailmerge  openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us  openoffice.org-impress openoffice.org-math openoffice.org-style-galaxy  openoffice.org-style-human openoffice.org-writer pitivi pkg-config  plymouth-theme-ubuntu-logo protobuf-compiler  pulseaudio-module-bluetooth  pulseaudio-module-gconf python-avahi python-configglue python-couchdb  python-crypto python-desktopcouch python-desktopcouch-records  python-egenix-mxdatetime python-egenix-mxtools python-farsight  python-fstab python-gnomekeyring python-gtksourceview2 python-gtkspell  python-ibus python-indicate python-mako python-openssl python-pam  python-papyon python-protobuf python-pycurl python-pygoocanvas  python-pyinotify python-serial python-telepathy python-twisted-bin  python-twisted-core python-twisted-names python-twisted-web  python-ubuntuone python-ubuntuone-client  python-ubuntuone-storageprotocol  python-uno python-wnck rdesktop rhythmbox rhythmbox-plugin-cdrecorder  rhythmbox-plugins rhythmbox-ubuntuone-music-store  screen-resolution-extra  seahorse ssh-askpass-gnome telepathy-butterfly telepathy-gabble  telepathy-haze telepathy-idle telepathy-mission-control-5  telepathy-salut  tomboy tsclient ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-mono  ubuntu-sounds ubuntu-system-service ubuntu-wallpapers ubuntuone-client  ubuntuone-client-gnome uno-libs3 upower ure vino whois  xdg-user-dirs-gtk  xfonts-mathml[COLOR=Silver]* && sudo apt-get install xubuntu-desktop   *[/COLOR]

 
```Thanks in advance for helping. ;-)

Ps. Ubuntu 10.04

---

### Post by pseudo_nz on 2010-08-01
> **aysiu said:**
> Usually that kind of error message indicates you have conflicting software sources (otherwise known as software repositories--basically online servers Ubuntu uses to fetch software you want to install).

Can you post the output of these commands? ```
sudo apt-get update
cat /etc/apt/sources.list
```

I'm having the same problem, with the same libxine entry, on 64bit Lucid.  Here's the output from the two commands:

> Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release.gpg                                     
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release.gpg                                  
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg [197B]                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg                           
Hit [http://debian.scribus.net](http://debian.scribus.net) lucid Release.gpg                                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                      
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_NZ                     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/main Translation-en_NZ                  
Ign [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) lucid/partner Translation-en_NZ            
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_NZ        
Ign [http://debian.scribus.net/debian/](http://debian.scribus.net/debian/) lucid/main Translation-en_NZ                  
Ign [http://ppa.launchpad.net/apachelogger/ubuntuone-kde/ubuntu/](http://ppa.launchpad.net/apachelogger/ubuntuone-kde/ubuntu/) lucid/main Translation-en_NZ
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_NZ                 
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_NZ            
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid Release                                      
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_NZ  
Ign [http://debian.scribus.net/debian/](http://debian.scribus.net/debian/) lucid/non-free Translation-en_NZ              
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                      
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_NZ              
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release [6,854B]                          
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Packages                             
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_NZ    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_NZ            
Ign [http://ppa.launchpad.net/bisigi/ppa/ubuntu/](http://ppa.launchpad.net/bisigi/ppa/ubuntu/) lucid/main Translation-en_NZ        
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_NZ  
Hit [http://archive.canonical.com](http://archive.canonical.com) lucid/partner Sources                              
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release.gpg                             
Hit [http://debian.scribus.net](http://debian.scribus.net) lucid Release                                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release                               
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_NZ          
Ign [http://ppa.launchpad.net/docky-core/ppa/ubuntu/](http://ppa.launchpad.net/docky-core/ppa/ubuntu/) lucid/main Translation-en_NZ    
Hit [http://debian.scribus.net](http://debian.scribus.net) lucid/main Packages                                   
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages                           
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_NZ    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg                                      
Hit [http://debian.scribus.net](http://debian.scribus.net) lucid/non-free Packages                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages                         
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_NZ      
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) lucid/main Translation-en_NZ     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Sources                                
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_NZ    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-backports Release.gpg                           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Sources                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages                     
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-backports/main Translation-en_NZ        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages                   
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-backports/restricted Translation-en_NZ  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release                           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources                          
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release.gpg                              
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-backports/universe Translation-en_NZ    
Ign [http://archive.getdeb.net/ubuntu/](http://archive.getdeb.net/ubuntu/) lucid-getdeb/apps Translation-en_NZ           
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                                    
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) lucid-backports/multiverse Translation-en_NZ  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid Release                                         
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb Release                                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources                      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates Release                                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-backports Release                               
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/apps Packages                            
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages                                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Packages                                   
Hit [http://archive.getdeb.net](http://archive.getdeb.net) lucid-getdeb/apps Sources                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Packages                               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Packages                             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/main Sources                                    
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/restricted Sources                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/universe Sources                                
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid/multiverse Sources                              
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Packages                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Packages                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) lucid-backports/multiverse Sources
Fetched 7,051B in 22s (312B/s)                       
Reading package lists... Done

and

> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) lucid-backports main restricted universe multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted universe multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid free non-free
deb [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) lucid-getdeb apps
deb-src [http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu) lucid-getdeb apps
deb [http://debian.scribus.net/debian/](http://debian.scribus.net/debian/) lucid main non-free

Any advice appreciated :)

---

### Post by vangop on 2010-08-04
same problem. I installed kubuntu-desktop 1st, then was trying to remove gnome (so I removed && install cmd at the end).
This can be the cause.. Any solution?

---

