---
title: "System loads/shutsdown with Xubuntu splash / login screen"
date: 2012-03-01
forum: New to Ubuntu
---

### Post by matbluvenger on 2012-03-01
Okay so this isn't a terribly big deal but I just found it really strange.

I started using 11.10 with Unity... then I discovered how to use shells and I started using Gnome3 as my regular. But then I got curious and installed Lubuntu, Kubuntu, and Xubuntu wanting to try them out and explore a bit. 

I wasn't too crazy about them though they could be better than Gnome3 with some tweaking once I get used to them. So I went back to Gnome3.

But now when I shutdown or log off it takes me to the Xubuntu splash / login screen instead of the Ubuntu one with the default background.

Now this isn't a big deal... except that I've noticed it loads and shuts down slower and it bugs me that it askes for me to login on initial boot of the OS when it didn't before with the Ubuntu load.

---

### Post by Bucky Ball on 2012-03-01
You mean you installed xubuntu-desktop (and the rest -desktop etc) or you installed all the above mentioned on separate partitions? Please clarify ... ;)

You really only needed to install xfce4, kde, lxde *desktop environments,* _[COLOR=black]not[/COLOR]_ the entire 'whatever-desktop' which drags in a whole lot of other stuff; apps, packages, etc, related to kde, xubuntu, lubuntu (which uses lxde DE incidentally), etc. 

For instance, for a file manager you could probably now use Thunar (Xubuntu), PcManFM (Lubuntu), Nautilus (Ubuntu), and whatever the file manager is for KDE (never used, don't like). Open a terminal and type 'thunar' and you'll see what I mean. 

Iinstalling only the DE rather than the entire desktop package avoids this (and duplication of other things and sometimes total confusion and occasionally conflicts).

Loading and shutting down would be slower as you now effectively have Kubuntu, Lubuntu, Xubuntu, Ubuntu and whatever else installed! I would remove what you don't want and start again ('sudo apt-get remove xubuntu-desktop', etc) then just install the DE you like. (Xfce4 over Ubuntu is a good match, specially if you don't love Unity - a lot of folk are heading in that direction or changing to Xubuntu completely for 12.04 LTS).

---

### Post by Krytarik on 2012-03-01
For the login screen, just set it back to LightDM:
```
sudo dpkg-reconfigure lightdm
```To set the Plymouth boot splash to the default one, run:
```
sudo update-alternatives --config default.plymouth
```Then choose "ubuntu-logo.plymouth", followed by:
```
sudo update-initramfs -u
```Regards.

---

### Post by HeroOfCanton on 2012-03-01
It's a loooooooooong list, but this will remove xubuntu completely. The install of ubuntu-desktop at the end will reinstall the ones you need for gnome. There may be an easier way to kill just that feature so if this looks like more than you want to do just for a splash screen maybe someone will come by with an easier solution.

```
sudo apt-get remove abiword abiword-common abiword-plugin-grammar  abiword-plugin-mathview bison blueman brltty-x11 catfish  elementary-icon-theme exo-utils flex gigolo gimp gimp-data gmusicbrowser  gnome-icon-theme-full gnome-system-tools gnome-time-admin gnumeric  gnumeric-common gnumeric-doc gstreamer0.10-gnomevfs gthumb gthumb-data  gtk2-engines-pixbuf gtk2-engines-xfce indicator-application-gtk2  indicator-messages-gtk2 indicator-sound-gtk2  indicator-status-provider-pidgin leafpad libabiword-2.8  libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a  libao-common libao4 libaudio-scrobbler-perl libbabl-0.0-0  libclutter-1.0-0 libclutter-1.0-common libclutter-gtk-1.0-0  libcogl-common libcogl5 libconfig-inifiles-perl libencode-locale-perl  libept1 libexo-1-0 libexo-common libfile-listing-perl libfont-afm-perl  libgarcon-1-0 libgarcon-common libgdome2-0 libgdome2-cpp-smart0c2a  libgegl-0.0-0 libgimp2.0 libglade2-0 libgnomevfs2-extra libgoffice-0.8-8  libgoffice-0.8-8-common libgsf-1-114 libgsf-1-common libgstreamer-perl  libgtk2-notify-perl libgtk2-trayicon-perl libgtkmathview0c2a  libhtml-form-perl libhtml-format-perl libhtml-parser-perl  libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl  libhttp-daemon-perl libhttp-date-perl libhttp-message-perl  libhttp-negotiate-perl libid3tag0 libido-0.1-0 libilmbase6  libio-socket-ssl-perl libjpeg-progs libkeybinder0 liblink-grammar4  libloudmouth1-0 liblwp-mediatypes-perl liblwp-protocol-https-perl  libmad0 libmailtools-perl libnet-dbus-perl libnet-http-perl  libnet-ssleay-perl liboobs-1-5 libopenexr6 libotr2 libots0  libpolkit-gtk-1-0 libsexy2 libtagc0 libthunarx-2-0 libtie-ixhash-perl  libtimedate-perl libtumbler-1-0 liburi-perl libwv-1.2-3 libwww-perl  libwww-robotrules-perl libxfce4ui-1-0 libxfce4util-bin  libxfce4util-common libxfce4util4 libxfcegui4-4 libxfconf-0-2  libxml-parser-perl libxml-twig-perl libxml-xpath-perl libxss1  lightdm-gtk-greeter link-grammar-dictionaries-en m4 mpg321  murrine-themes orage parole pastebinit pidgin pidgin-data  pidgin-libnotify pidgin-microblog pidgin-otr plymouth-theme-xubuntu-logo  plymouth-theme-xubuntu-text python-configobj python-glade2 quadrapassel  ristretto screensaver-default-images synaptic system-tools-backends  tango-icon-theme tango-icon-theme-common tcl8.5 thunar  thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-volman  ttf-droid ttf-lyx tumbler tumbler-common xchat xchat-common xfburn  xfce-keyboard-shortcuts xfce4-appfinder xfce4-cpugraph-plugin xfce4-dict  xfce4-fsguard-plugin xfce4-indicator-plugin xfce4-mailwatch-plugin  xfce4-mixer xfce4-mount-plugin xfce4-netload-plugin xfce4-notes  xfce4-notes-plugin xfce4-notifyd xfce4-panel xfce4-places-plugin  xfce4-power-manager xfce4-power-manager-data xfce4-quicklauncher-plugin  xfce4-screenshooter xfce4-session xfce4-settings  xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-taskmanager  xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-volumed  xfce4-weather-plugin xfconf xfdesktop4 xfdesktop4-data xfwm4  xfwm4-themes xscreensaver xscreensaver-data xscreensaver-gl  xubuntu-artwork xubuntu-default-settings xubuntu-desktop xubuntu-docs  xubuntu-icon-theme xubuntu-wallpapers && sudo apt-get install ubuntu-desktop 
```

---

### Post by Bucky Ball on 2012-03-01
To poster #4, there is a lot more to remove than xubuntu-desktop and related packages to regain the original configuration and speed! Getting rid  of the resource hungry Kubuntu-desktop and related flotsam would be a good place to start. ;)

---

### Post by HeroOfCanton on 2012-03-01
> **Bucky Ball said:**
> To poster #4, there is a lot more to remove than xubuntu-desktop and related packages to regain the original configuration and speed! Getting rid  of the resource hungry Kubuntu-desktop and related flotsam would be a good place to start. ;)

Agree 100%, but that's not what he asked for. Personally, once I found the right desktop for me, I just reinstalled the full OS with the proper version (which happened to be xubuntu :D).

Note: Correct me if I'm wrong, but shouldn't any of the DE's ask for a login? That part sounded strange to me...

---

### Post by matbluvenger on 2012-03-01
AAAH! Good lord, I didn't realize there was a difference between xubuntu-desktop and xfce... I just did sudo apt-get install xubuntu-desktop because installing xcfe from Software Center didn't work (i.e. it wouldn't let me.)


So this code should work for each without damaging the main ubuntu system? 
```
sudo apt-get remove <blah>-desktop
```



EDIT: Okay, I tried that without waiting for a response because I'm dumb and impatient. :D    I tried removing lubuntu-desktop, it said it wasn't installed. Odd, but whatever. Then when I removed kubuntu and xubuntu the packages it removed were tiny, like ~47KB and ~54KB respectively. And I rebooted only to have xubuntu at shutdown and at startup, login screen and all.

...poop

---

### Post by HeroOfCanton on 2012-03-01
Yep. To install the desktop it installs all of the dependent programs (but doesn't uninstall them for some reason). It kind of has to since the desktops need them. [Click here]("http://www.psychocats.net/ubuntu/puregnome") for the info to uninstall each of them fully.

A reinstall would really be your best option if you're sure that's the one you want though. In the long run it's probably easier that way.

---

### Post by matbluvenger on 2012-03-01
Cool, just did a clean reinstall and I'm quite happy.

Also worth noting, I was really upset with the stupid default Chromium font that I couldn't change after I had installed all of those other desktops. Now it's back to normal. It's the little things that keep me happy :D

---

### Post by Bucky Ball on 2012-03-01
Cool! Now, if you want to try out xfce, install xfce4 from Synaptics, Software Centre or whatever or via a terminal with:

```
sudo apt-get install xfce4
```Log out, from the 'Sessions' pop up at the log-in screen, choose 'Xfce Session' then login. Done. 

This won't give you all the other stuff, ONLY the xfce4 desktop environment. You can go back to Unity or whatever the default is at any time by repeating these steps and choosing it from 'Sessions'. Have fun! ;)

PS: This won't slow your machine.

---

### Post by matbluvenger on 2012-03-01
> **Bucky Ball said:**
> Cool! Now, if you want to try out xfce, install xfce4 from Synaptics, Software Centre or whatever or via a terminal with:

```
sudo apt-get install xfce4
```Log out, from the 'Sessions' pop up at the log-in screen, choose 'Xfce Session' then login. Done. 

This won't give you all the other stuff, ONLY the xfce4 desktop environment. You can go back to Unity or whatever the default is at any time by repeating these steps and choosing it from 'Sessions'. Have fun! ;)

PS: This won't slow your machine.

AMAZING! Thank you so much. Does this work for KDE (that's kubuntu, right?) or LXDE (lubuntu?) as well?

---

### Post by Bucky Ball on 2012-03-01
Certainly does for lxde, not sure about KDE though. That is somewhat more of a complex beast and I think need to drag in a lot more stuff. You should probably research that with a search for something like 'install kde ubuntu'. For lxde, though;

```
sudo apt-get install lxde
```Also look here under 'Ubuntu and Debian based ...'

[http://wiki.lxde.org/en/Installation#Instal_LXDE_onto_an_existing_Linux_system](http://wiki.lxde.org/en/Installation#Instal_LXDE_onto_an_existing_Linux_system)

There's others; fluxbox, openbox, and the list goes on, from resource hungry to VERY lightweight, to extremely exotic (and difficult to configure but great when you get there). Good luck! ;)

** A further note: You can do all other neat stuff also like add artwork  from other *buntus. For instance, I really like the Edubuntu artwork so  always install that. Easy, just look for 'edubuntu-artwork' and  install. Now you will be able to select the artwork from Themes. You can  really customise this beast, one of the reasons I love it! (Ubuntu  Satanic Edition has some good stuff, too!). Artwork, obviously, is very  easy to uninstall. :wink:

---

### Post by matbluvenger on 2012-03-01
So far I'm enjoying xfce. Only thing is something odd happened: when I first loaded it it had a nice simple background that is nice and not bright. Then when I tried to go to my home folder it asked me what file manager I wanted to use. I chose nautilus and POW background changed to my previous one from unity and the desktop wallpaper manager changed to the one from unity and I couldn't find the nice simple xfce ones. Call me crazy but the simpler shell needs a simpler wallpaper :D

EDIT: But I already found out how to move the close, min, max buttons to the left... where they should be :D (Not a Mac guy... just love it from unity and gnome)

EDIT 2: Just noticed I can't raise, lower, or mute volume with my keyboard. Is there a way to fix that?

---

### Post by amhainen on 2012-04-08
> **Krytarik said:**
> For the login screen, just set it back to LightDM:
```
sudo dpkg-reconfigure lightdm
```To set the Plymouth boot splash to the default one, run:
```
sudo update-alternatives --config default.plymouth
```Then choose "ubuntu-logo.plymouth", followed by:
```
sudo update-initramfs -u
```Regards.

Krytarik, thanks so much again! You helped me with this same problem on 10.04 and I was so glad I found your post this evening after upgrading to 12.04. Thank you!

---

