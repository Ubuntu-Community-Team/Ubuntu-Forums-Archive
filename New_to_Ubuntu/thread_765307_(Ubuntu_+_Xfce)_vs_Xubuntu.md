---
title: "(Ubuntu + Xfce) vs Xubuntu"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by mar\/in on 2008-04-24
A couple of rookie questions...

1) After playing with Ubuntu 8.04rc for a couple of days on my creaky old laptop (see .sig), I'm wondering if using Xfce instead of Gnome would provide a better user experience.  The question is: is there a practical difference in usage & management between using Xfce installed from the package manager on top of vanilla Ubuntu, on the one hand, and using an Xubuntu system installed from scratch, on the other?  (Aside from the lingering option to log into Gnome, I mean.)

2) In a [previous thread]("http://ubuntuforums.org/showthread.php?t=763443") the very kind Overdrank advised me to use ```
sudo dpkg-reconfigure xserver-xorg
``` in order to improve the performance of my video driver in Gnome.  (It allowed me to turn off frame buffering by the kernel.)  Does that command affect Xfce too, or would a different command be in order?

---

### Post by swoll1980 on 2008-04-24
theres no diference between ubuntu+xfce and xubuntu

---

### Post by y-lee on 2008-04-24
I'm no Xfce expert but my thoughts anyway

> is there a practical difference in usage & management between using Xfce installed from the package manager on top of vanilla Ubuntu, on the one hand, and using an Xubuntu system installed from scratch, on the other?

I would say no difference, the gnome stuff will remain installed of course.

> Does that command affect Xfce too, or would a different command be in order?

I would think that would still work as it effects X windows and xfce is built on top of X windows :)

---

### Post by kansasnoob on 2008-04-24
If you have a "creaky old system" Xubuntu will be better for you.

Yes you can add X to your ubuntu and then spend hours dumping all of the Gnome stuff, but just download X! X uses less resources by default.

I put Xubuntu on an old Micron Clientpro circa 1998 w/a 333 mhz cpu & 128 mg ram and it worked! The only problem was getting an ethernet card to work. I was using ethernet cards from my left-overs pile and I'm an idiot when it comes to marking parts and pieces for later use :^/

---

### Post by mar\/in on 2008-04-24
> **swoll1980 said:**
> theres no diference between ubuntu+xfce and xubuntu

Groovy.

> **y-lee said:**
> I would think that would still work as it effects X windows and xfce is built on top of X windows :)

Excellent!  I guess I was wondering if each instance of a different desktop would have its own set of X windows configuration files or not, and if that would mean that the video drivers might act differently for different desktops.

> **kansasnoob said:**
> If you have a "creaky old system" Xubuntu will be better for you.

Yes you can add X to your ubuntu and then spend hours dumping all of the Gnome stuff, but just download X! X uses less resources by default.

I put Xubuntu on an old Micron Clientpro circa 1998 w/a 333 mhz cpu & 128 mg ram and it worked! The only problem was getting an ethernet card to work. I was using ethernet cards from my left-overs pile and I'm an idiot when it comes to marking parts and pieces for later use :^/

Good news.  :guitar:

I probably wouldn't uninstall Gnome, though, unless it proves to be completely redundant.  Aren't there some software packages that only work in a given desktop?

---

### Post by mar\/in on 2008-04-25
Ok, I've reinstalled with the final 8.04 release and added Xfce to the mix.  And I've given up on flash for the time being.  But I really like this Xubuntu feel.  Sweet. :)

---

### Post by hyper_ch on 2008-04-25
> **swoll1980 said:**
> theres no diference between ubuntu+xfce and xubuntu

There is... xubuntu comes with a set of preconfigured applications that gets installed which are not there with a pure xfce installation.

---

### Post by ugm6hr on 2008-04-25
> **hyper_ch said:**
> There is... xubuntu comes with a set of preconfigured applications that gets installed which are not there with a pure xfce installation.

But the difference in apps is much less than it used to be in 6.06/7.04.

The choice of media / office apps is a personal preference in any case.

If you really want all the Xubuntu default apps - just install the xubuntu-desktop package.

---

### Post by zvacet on 2008-04-25
> I probably wouldn't uninstall Gnome, though, unless it proves to be completely redundant.

If you decide to use Xubuntu then Gnome is redundant.To remove Gnome

```
sudo apt-get remove alacarte aspell bittorrent bluez-cups bluez-gnome bluez-utils bogofilter bogofilter-bdb bogofilter-common brltty brltty-x11 bsh bug-buddy capplets-data cdrdao cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins consolekit contact-lookup-applet dcraw deskbar-applet dictionaries-common diveintopython ekiga eog espeak evince evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal f-spot fast-user-switch-applet firefox-gnome-support fping gcj-4.2-base gconf-editor gedit gedit-common gij gij-4.2 gimp-python gnome-about gnome-applets gnome-applets-data gnome-btdownload gnome-control-center gnome-desktop-data gnome-doc-utils gnome-keyring-manager gnome-media gnome-menus gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-session gnome-spell gnome-terminal gnome-terminal-data gnome-user-guide gnome-utils gnome-volume-manager gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-tools gstreamer0.10-x gthumb gtkhtml3.14 hal-device-manager hwdb-client-common hwdb-client-gnome libalut0 libao2 libart2.0-cil libavc1394-0 libbeagle0 libbluetooth2 libcaca0 libcamel1.2-10 libcdio6 libcompizconfig-backend-gconf libcompizconfig0 libcucul0 libdecoration0 libdeskbar-tracker libdv4 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 libexchange-storage1.2-3 libgcj-bc libgcj-common libgcj8-1 libgconf2.0-cil libgda3-3 libgda3-common libgdl-1-0 libgdl-1-common libgdl-gnome-1-0 libgksu1.2-1 libgksuui1.0-1 libgl1-mesa-dri libglade2.0-cil libglew1.4 libglib2.0-cil libgmime-2.0-2 libgmime2.2-cil libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2.0-cil libgnomevfs2-bin libgnomevfs2-extra libgpod2 libgsl0 libgtk2.0-cil libgtkhtml2.0-cil libgtkhtml3.14-19 libgtkhtml3.8-15 libgtksourceview2.0-0 libgtksourceview2.0-common libhsqldb-java libicu36 libiec61883-0 libjaxp1.3-java libjline-java liblpint-bonobo0 libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono2.0-cil libmtp6 libmusicbrainz4c2a libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon26 liboil0.3 libopal-2.2 libopenal0a libpam-gnome-keyring libpisock9 libpisync0 libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 librarian0 libraw1394-8 librsvg2.0-cil libservlet2.4-java libshout3 libsndfile1 libsoup2.2-8 libsvg1 libtracker-gtk0 libtrackerclient0 libvisual-0.4-0 libvorbisenc2 libvorbisfile3 libwavpack1 libwpg-0.1-1 libwps-0.1-1 libxalan2-java libxerces2-java libxml2-utils mono-common mono-gac mono-jit mono-runtime nautilus nautilus-cd-burner nautilus-data nautilus-sendto o3read openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk openoffice.org-hyphenation openoffice.org-impress openoffice.org-java-common openoffice.org-math openoffice.org-style-human openoffice.org-writer pkg-config python-bittorrent python-gmenu python-gnome2-extras python-pygtksourceview python-uno rdesktop rhythmbox rss-glx serpentine sound-juicer ssh-askpass-gnome tangerine-icon-theme tomboy totem-mozilla tracker tracker-search-tool tsclient ttf-opensymbol ubuntu-desktop ubuntu-docs ubuntu-sounds usplash-theme-ubuntu vino whois xdg-user-dirs xdg-user-dirs-gtk xsane xsane-common xsltproc yelp
```

---

### Post by A$h X on 2008-04-25
I was thinking of doing the same thing, but if the only difference between Xubuntu and Ubuntu is the desktop environment/window manager and pre-installed apps, then I might as well add XFCE to my existing hardy installation.

So just to confirm: Installing XFCE on top of ubuntu hardy = Xubuntu hardy minus a few pre-installed programs?

---

### Post by stchman on 2008-04-25
> **mar\/in said:**
> A couple of rookie questions...

1) After playing with Ubuntu 8.04rc for a couple of days on my creaky old laptop (see .sig), I'm wondering if using Xfce instead of Gnome would provide a better user experience.  The question is: is there a practical difference in usage & management between using Xfce installed from the package manager on top of vanilla Ubuntu, on the one hand, and using an Xubuntu system installed from scratch, on the other?  (Aside from the lingering option to log into Gnome, I mean.)

2) In a [previous thread]("http://ubuntuforums.org/showthread.php?t=763443") the very kind Overdrank advised me to use ```
sudo dpkg-reconfigure xserver-xorg
``` in order to improve the performance of my video driver in Gnome.  (It allowed me to turn off frame buffering by the kernel.)  Does that command affect Xfce too, or would a different command be in order?

YOur laptop has a 2.4GHz proc and 512MB RAM.  That should more than sufficient to run Gnome very well.

If you want get another 512MB RAM.

If you are looking for the fastest possible Linux use Puppy.  It flies.

---

### Post by A$h X on 2008-04-25
I've been doing a bit of reading, and it looks like Xubuntu 8.04 will use the same kernel as ubuntu 8.04, so all the boot/shutdown times will be the same? The ONLY difference performance-wise will be while using XFCE itself, everything else is identical, is that correct? 

And could someone please confirm that BOTH desktop environments are loaded into RAM at bootup, and you choose one at the login screen; OR are they loaded when you pick one from the login screen, and thus only the one you are using is loaded into memory?

---

### Post by Paqman on 2008-04-25
> **zvacet said:**
> If you decide to use Xubuntu then Gnome is redundant.

I dunno about that. Some of the components are quite good. XFCE is using Gnomes system monitor these days, and I like to use Nautilus instead of Thunar on my Xubuntu laptop. I like to have Gnome installed in case I want to use some of it's nice features. It's only a bit of space on the hard drive, after all.

---

### Post by Paqman on 2008-04-25
> **A$h X said:**
> 
And could someone please confirm that BOTH desktop environments are loaded into RAM at bootup, and you choose one at the login screen; OR are they loaded when you pick one from the login screen, and thus only the one you are using is loaded into memory?

You can pick which desktop to use at login.

[Screenshot](http://www.ridinglinux.org/wp-content/uploads/2007/04/ubuntu-kde-install9.png)

When you pick your desktop, you can specify whether to make it the default, or just use it for that session. To switch again you'd need to log out.

---

### Post by mar\/in on 2008-04-25
> **ugm6hr said:**
> 
If you really want all the Xubuntu default apps - just install the xubuntu-desktop package.

This is what I'm doing for now.

---

### Post by mar\/in on 2008-04-25
> **stchman said:**
> YOur laptop has a 2.4GHz proc and 512MB RAM.  That should more than sufficient to run Gnome very well.

If you want get another 512MB RAM.

If you are looking for the fastest possible Linux use Puppy.  It flies.

Yes, the more I look around these forums the more I realize I've set the bar too low for "old and creaky." :rolleyes:

Puppy looks kind of neat...hmmmm!

---

