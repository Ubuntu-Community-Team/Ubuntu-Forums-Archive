---
title: "lxde vs icewm vs xfce"
date: 2009-09-07
forum: Recurring Discussions
---

### Post by pythonscript on 2009-09-07
I'm looking to rework my lightweight ubuntu installation (currently command line only ubuntu with icewm stacked on top) and I'm wondering about people's experience with the three states desktop environments. I'm mainly looking for ease of configuration, stuff like that. I've been using icewm for almost a year now and loved it, because you can't really beat writing text files when it comes to ease of configuration. Any opinions on these three would be greatly appreciated. I'm done with gnome, kde, and fluxbox :) so these three are my options now. Thanks!

---

### Post by Brandon Williams on 2009-09-07
If you're looking for text file configuration, you probably want to stick with lxde and/or icewm. IIRC, xfce appears to be moving in the direction of gnome in terms of how configuration settings are stored, with setting stored very much the same way that gconf setting are stored. Yes, they are text files ... but the settings' keys also use directory structure to represent the variable's "path" within the settings hierarchy. There are simple graphical settings to manage all of the settings, but editing with a console editor would be a pain.

Also, xfce does not currently have a functional menu editor. You have to edit/create a whole bunch of different files if you want to change the menu. Hopefully, this will be easier in Karmic, but for now, I don't think menu editing in xfce meets the description of what you're looking for.

---

### Post by theZoid on 2009-09-07
LXDE IMO.....or just plain Openbox....Xfce I love, but it's entering the 'heavyweight' category almost.

---

### Post by earthpigg on 2009-09-07
> **theZoid said:**
> LXDE IMO.....or just plain Openbox....Xfce I love, but it's entering the 'heavyweight' category almost.

at first, i read that as:

> *[I]_LXDE_* I love, but it's entering the 'heavyweight' category almost.[/I]

my brain was about to explode.



<3 LXDE.

---

### Post by XubuRoxMySox on 2009-09-07
I too am an LXDE fan. It's still undergoing very active development, so I think we can expect more great things from the LXDE developers. It is *definitely* more lightweight than Xfce and very easy to configure.

Barebones Openbox is wonderful (LXDE relies on Openbox as well). The Ubuntu-based [Crunchbang]("http://crunchbanglinux.org") distro uses just Openbox, and with Conky added, it has a stark beauty that belies it's power and versatility. 

I'm using minimal Ubuntu + LXDE with great results in both speed and customizability.

-Robin

---

### Post by Warpnow on 2009-09-07
Openbox wins for customization in my opinion.

LXDE is a great initial setup and a few applications for openbox.

---

### Post by #11u-max on 2009-09-07
if you are ever looking for a super lightweight IceWM OS, look no further than Spri Linux!

---

### Post by kk0sse54 on 2009-09-07
Debian Lxde using only 44 MB Ram = Win! As a matter of personal opinion, I'm not too big of a fan of icewm. I do love Xfce, but as already pointed out it's moving into a more heavier direction. As such, personally I'd go with  ubuntu minimal + lxde but depending on how minimal you want to get don't forget about the other window managers i.e. Tiling WMs and floating WMs like evilwm.

---

### Post by tropicofvector on 2009-09-10
> **#11u-max said:**
> if you are ever looking for a super lightweight IceWM OS, look no further than [VectorLinux]("http://www.vectorlinux.com%22")!


---
[TROPIC OF VECTOR Blog]("http://www.uluga.ubuntuforums.org/tropicofvector.wordpress.com"): Running Linux on an old PIII laptop

---

### Post by afroman10496 on 2010-07-02
I think its pretty good to bump now cause of Lubuntu 10.04- Id chose LXDE over any of them. icewm is too unixy ;)

---

### Post by theZoid on 2010-07-02
> **Afroman10496 said:**
> I think its pretty good to bump now cause of Lubuntu 10.04- Id chose LXDE over any of them. icewm is too unixy ;)

If you like LXDE I'd recommend what I'm using now, Peppermint OS.  It's a fork of Mint LXDE based on 10.04.  Stable and fast.  Same developer of Mint LXDE.

---

### Post by iluii on 2010-10-30
I'm liking opensuse lxde, even the live version was pretty fast

havent gotten around to customizing as I just donwloaded it but it seems flexible

---

### Post by Spice Weasel on 2010-10-31
Window managers and desktop environment are an opinion. Personally, I use FVWM, Openbox, Enlightenment E16 (Yep. That's right. E16.) and AwesomeWM with some tools from Xfce and LXDE.

Xfce vs LXDE (in my opinion)

Thunar > PCManFM (PCMan may have tabs, but it does't run very smoothly here)
Squeeze > Xarchiver (Xarchiver always seems to be frozen or crashing.)
???? Xfce < LXAppearance (LXAppearance is THE GTK configuration tool.)
xfce-taskmanager < LXTask (More features.)

It's nice to mix things up a bit some times. Find what works for you.

---

### Post by handy on 2010-10-31
On Arch (not that it matters really what distro you are on) I use Openbox (mostly text based configuration) with xfce4-panel running 4 plugins.

I liked Xfce when I used it, but it is far more system than I need. As my system I don't use icons & windows, I use the Openbox menu rarely, & Worker & Sakura all the time. Worker mostly.

For anyone who does choose to use Openbox, you essentially need to install OBMenu, LXappearance & Openbox Config Manager.  A couple of which may be part of the installation these days, I don't really know, I installed a very long time ago now.

Setting up the Openbox menu's using the OBMenu isn't too tough, if you do have a problem you can just go to the ~/.config/openbox/menu.xml & play there.

---

### Post by runny6play on 2011-11-20
I love openbox. Its ultra configurable while being light. With Debian menu you get an updating menu.
personally im a fan of openbox +extras. 
I love the tint2 panel. It is really lightweight while being one of the most configurable panels available. I use feh to set the background image. once feh is done it exits so it really doesn't take any system resources up. Its very visually appealing too. 
I am in the process of setting up idesk for some desktop icons (just a few). And depending on resources maybe conky. unforchanitly
I have some gnome apps that like to start the gnome key-ring and other gnome extentions that waste memory. Killing them also inhibit the correct use of such apps. But once started they run as daemons and its annoying.

---

### Post by leclerc65 on 2011-11-30
I have Xubuntu on my Samsung NF210, because it's the only way to make the backlight working properly (with Voiria PPA), but given choice I'd rather have Ubuntu or Lubuntu on it. I don't know why but sometimes, back from the Internet Cafes, it looses the cursor (becomes a cross); desktop icons missing; menus lose minimize, maximize, close buttons.:confused:

---

