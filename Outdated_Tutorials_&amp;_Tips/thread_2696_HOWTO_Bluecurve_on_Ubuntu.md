---
title: "HOWTO: Bluecurve on Ubuntu"
date: 2004-10-30
forum: Outdated Tutorials &amp; Tips
---

### Post by JConnell on 2004-10-30
Do you love Ubuntu but just can't live without your redhat/fedora bluecurve theme? Well here are some simple steps to bring back the blue! :D


**1)** Download the [bluecurvedebian](http://themes.freshmeat.net/projects/bluecurvedebian/) tarball:

[http://themes.freshmeat.net/redir/bluecurvedebian/51489/url_tgz/bluecurvedebian-padrao.tar.gz](http://themes.freshmeat.net/redir/bluecurvedebian/51489/url_tgz/bluecurvedebian-padrao.tar.gz)

**2)** Unpack the tarball:

Right-click -> Extract Here

**3)** Install libgdk-pixbuf2:
```

yourname@ubuntu:~ $ sudo apt-get install libgdk-pixbuf2

```
**4)** Install the redhat-artwork .deb:
```

yourname@ubuntu:~ $ sudo dpkg -i redhat-artwork_0.96-2_i386.deb

```
**5)** Change your theme selection:

Computer->Desktop Preferences->Theme

---

### Post by fjleal on 2004-10-31
You should fight bad habits, you know?... :)

Thanks for the link. ;)

---

### Post by dishkuvek on 2004-12-13
Here is just another way of doing the same thing...

add these lines to /etc/apt/sources.list:
```

deb http://home.planet.nl/~autar022/ ./
deb-src http://home.planet.nl/~autar022/ ./

```

and then at the prompt:
```

$ sudo apt-get update && sudo apt-get install redhat-artwork

```

Note that "redhat-artwork" is a meta-package, if you do not want to install gtk1 packages, you can install the packages individually...

```

$ sudo apt-get install gtk2-engines-bluecurve gdm-bluecurve  icons-bluecurve  metacity-bluecurve

```

---

### Post by khad on 2004-12-16
The easiest way to get Bluecurve in my opinion is directly from the Fedora project Web site. You also get the latest version of it.

Download the "redhat-artwork" RPM from:

[http://download.fedora.redhat.com/pub/fedora/linux/core/development/i386/Fedora/RPMS/](http://download.fedora.redhat.com/pub/fedora/linux/core/development/i386/Fedora/RPMS/)

As of this writing, the current RPM is 0.120-1.2:

[http://download.fedora.redhat.com/pub/fedora/linux/core/development/i386/Fedora/RPMS/redhat-artwork-0.120-1.2.i386.rpm](http://download.fedora.redhat.com/pub/fedora/linux/core/development/i386/Fedora/RPMS/redhat-artwork-0.120-1.2.i386.rpm)

In the directory you downloaded the RPM, run this command:

```
sudo alien -i redhat-artwork*
```

That's all there is to it. Run one command and a single file you download, and it is the latest version directly from the Fedora project.

---

### Post by LongTooth on 2004-12-18
By God! I did it. Easy as pie. Looks like my FC2. But not to worry. I'm sticking with Ubuntu.

---

### Post by cllow on 2005-01-01
hi khad (and anyone who can help),

I try your method. Everything OK, till i rebooted. My system hangs(stops at the screen with a X mouse cursor) when it tries to startup the X-server. And when I moved my mouse of tried to change to any session using Ctrl-Alt-F2, this message appears:

There already appears to be an X server running on display :0.
Should I try another display number? If you answer no, I will
attempt to start the server on :0 again. (You can change
console by pressing Ctrl-Alt plus a function key, such as Ctrl-Alt-F7
to go to console 7. X servers usually run on console 7 and higher.)

Anyway to fix this? Thanks.

---

### Post by cllow on 2005-01-02
Think it's not the Bluecurve thingy that messed up my system. It might be the Firefox installation that I apt-get from the hoary repository

---

### Post by Deusiah on 2005-02-17
Khad thank you ever so much! Your method worked flawlessly and I am now admiring my new Bluecurve themed Ubuntu box  \\:D/

---

### Post by jdong on 2005-02-17
[QUOTE=cllow]Think it's not the Bluecurve thingy that messed up my system. It might be the Firefox installation that I apt-get from the hoary repository[/QUOTE]


If you're talking about installing Hoary packages on Warty, that's a **big** no-no!
Check out [http://backports.ubuntuforums.org](http://backports.ubuntuforums.org) for a sensible solution.

---

### Post by mirtux on 2005-03-02
[QUOTE=khad]The easiest way to get Bluecurve in my opinion is directly from the Fedora project Web site. You also get the latest version of it.

Download the "redhat-artwork" RPM from:

[http://download.fedora.redhat.com/pub/fedora/linux/core/development/i386/Fedora/RPMS/]("http://download.fedora.redhat.com/pub/fedora/linux/core/development/i386/Fedora/RPMS/")

As of this writing, the current RPM is 0.120-1.2:

[http://download.fedora.redhat.com/pub/fedora/linux/core/development/i386/Fedora/RPMS/redhat-artwork-0.120-1.2.i386.rpm]("http://download.fedora.redhat.com/pub/fedora/linux/core/development/i386/Fedora/RPMS/redhat-artwork-0.120-1.2.i386.rpm")

In the directory you downloaded the RPM, run this command:

```
sudo alien -i redhat-artwork*
```

That's all there is to it. Run one command and a single file you download, and it is the latest version directly from the Fedora project.[/QUOTE]

Hi,
  i've tried the way i've said and it's ok with GNOME, but it's not working with KDE i.d. it does not give me any Bluecurve style neither Window Decoration. The only thing available is color palette. I've tried with different versions of redhat-artwork but nothing changes.

Any ideas, thanks,
MC

---

### Post by jerome bettis on 2005-03-22
can someone post a screen shot of this?  i've never seen it & it sounds like it's pretty nice

---

### Post by andbert on 2005-03-23
Heres a [SNAPSHOT!](http://www.arstadrekrutt.com/snapshot1.png) 
Im in KDE though, guess it fits better in Gnome.....

---

### Post by fjleal on 2005-03-23
[QUOTE=andbert]Im in KDE though, guess it fits better in Gnome.....[/QUOTE]
I honestly hope it does... ;)

---

### Post by bored2k on 2005-03-23
[QUOTE=fjleal]I honestly hope it does... ;)[/QUOTE]
 here is a better one
[bored2k bluecurve](http://img225.exs.cx/img225/4562/shot8rq.jpg)

---

### Post by mirtux on 2005-03-24
[QUOTE=andbert]Heres a [SNAPSHOT!]("http://www.arstadrekrutt.com/snapshot1.png") 
Im in KDE though, guess it fits better in Gnome.....[/QUOTE]
I don't know why there is the strange things on the upper left of the opened windows, i have the same of you  in KDE but it does not appear in GNOME... strange..

Regards,
MC

---

### Post by basse1989 on 2005-04-05
AFAIK the bluecurve theme is a GNOME theme, and you need some kind of gtk theme to qt theme package for it to be available in kde.
I dont know tough, it might be a kde theme in that package too.

---

### Post by Nano on 2005-04-05
Indeed, it is a very nice theme and I used it till a bit ago, now the human theme has improved enough and I don't need it anymore.

---

### Post by poofyhairguy on 2005-04-05
Clearlooks makes bluecurve irrelevent. It was nice for Redhat to finally give it away.

---

### Post by primeirocrime on 2005-04-05
bluecurve? that was one depressive theme I will not miss. That shade of blue really reminds me of baaaaaad stormy weather.

---

### Post by mirtux on 2005-04-06
[QUOTE=poofyhairguy]Clearlooks makes bluecurve irrelevent. It was nice for Redhat to finally give it away.[/QUOTE]
Hi,
   is Clearlooks a theme only for GNOME? I'm using KDE....

Regards,
MC

---

### Post by 23meg on 2005-04-07
does anyone have (the url to) the Bluecurve XMMS skin? i just can't find it but i know there is one..

---

### Post by bgrant75 on 2005-04-07
Go over to gnome-look.org and have alook there. If not do a search on the web for XMMS+bluecurve+theme...

If not have a look athis site: [http://www.mithril-linux.org/~henrich/debian/package/Packages.gz](http://www.mithril-linux.org/~henrich/debian/package/Packages.gz)

But I got to ask the question...Why?

---

### Post by mirtux on 2005-04-08
[QUOTE=23meg]does anyone have (the url to) the Bluecurve XMMS skin? i just can't find it but i know there is one..[/QUOTE]
You can find it here [http://themes.freshmeat.net/projects/lighthouseblue-xmms/](http://themes.freshmeat.net/projects/lighthouseblue-xmms/)

Regards,
MC

---

### Post by 23meg on 2005-04-12
thanks mirtux, much appreciated.

---

### Post by mirtux on 2005-04-12
Hi,
  hope to enjoy it!

Regards,
MC

---

### Post by Silvio Moioli on 2005-04-17
KDE users: just "ln -s /usr/lib/qt-3.3/plugins/styles/bluecurve.* /usr/lib/kde3/plugins/styles/" and BC will work on KDE. Can't figure out how to do that in the most recent version, though.

---

### Post by adam.b on 2005-04-30
I installed the theme from the 'redhat-artwork' rpm.

How can I get back the gnome foot as the launcher button? I have a frickin' Fedora! I like the theme... hate the hat.

btw === I tried doing this on my own and moved around some icons in: /usr/share/icons/Bluecurve/

That was a major mistake. I couldn't get ubuntu to load into X!

It was easy to fix but scared me to death because I have my system about 99.5% how I want it... after three weeks of tweaks!

---

### Post by wirjo on 2005-05-31
[QUOTE=mirtux]Hi,
  i've tried the way i've said and it's ok with GNOME, but it's not working with KDE i.d. it does not give me any Bluecurve style neither Window Decoration. The only thing available is color palette. I've tried with different versions of redhat-artwork but nothing changes.

Any ideas, thanks,
MC[/QUOTE]
 Works perfectly for me! Thanks.

---

### Post by mach_zero on 2005-06-05
[QUOTE=adam.b]I installed the theme from the 'redhat-artwork' rpm.

How can I get back the gnome foot as the launcher button? I have a frickin' Fedora! I like the theme... hate the hat.

btw === I tried doing this on my own and moved around some icons in: /usr/share/icons/Bluecurve/

That was a major mistake. I couldn't get ubuntu to load into X!

It was easy to fix but scared me to death because I have my system about 99.5% how I want it... after three weeks of tweaks![/QUOTE]

You've may already figured this out by now, but for anyone who hasn't, this is the icon you need to replace. Launch Nautilus (File Browser) and go to "View>Show Hidden Files" in your Home Folder to enable you to see the ".icons" folder:

.icons/Bluecurve/16x16/apps/icon-panel-menu.png

You'll need to replace the same icon in 24x24, 32x32 and 48x48 as well.

Just rename the original icon to something like "icon-panel-menu-back.png" (in the unlikely event you'd ever want to change it back). Rename the custom icon you'd like to use instead to "icon-panel-menu.png" and add it to the folder . Refresh your theme and the new icon should show up in the Applications menu.

Worked for me, anyway. However, I installed Bluecurve by unpacking the RPM and moving all the theme elements to their appropriate locations by hand. As always you're mileage may vary.......

---

### Post by pdk001 on 2005-06-06
that was used when i used fedora core3

---

### Post by angrykeyboarder on 2005-06-07
[QUOTE=Nano]Indeed, it is a very nice theme and I used it till a bit ago, now the human theme has improved enough and I don't need it anymore.[/QUOTE]

It's *still* **brown**.  I don't see any improvement. :-)

---

### Post by felix.rommel on 2005-06-08
[QUOTE=mirtux]Hi,
  i've tried the way i've said and it's ok with GNOME, but it's not working with KDE i.d. it does not give me any Bluecurve style neither Window Decoration. The only thing available is color palette. I've tried with different versions of redhat-artwork but nothing changes.

Any ideas, thanks,
MC[/QUOTE]

Hello,

I have Debian Sarge - I think it's quite the same as Ubuntu Warty with Gnome 2.8 etc.

I had the same proplems when I tried Bluecurve for KDE with the package from Fedora Core4RC3

1. Then I downloaded

redhat-artwork-0.96-1.i386.rpm

2. from Fedora Core 2 converted it with

fakeroot alien redhat-artwork-0.96-1.i386.rpm

3. installed it with

dpkg --install redhat-artwork_0.96-2_i386.deb

4. Set the links as described in the upper post from qt to kde directory:

ln -s /usr/lib/qt-3.3/plugins/styles/bluecurve.* /usr/lib/kde3/plugins/styles/

5. After that you can set the style for QT with 

qtconfig

6. and for KDE with the control center

kcontrol

If you use Hoary you should try the redhat-artwork from Fedora Core 4 which is out next week. Hope it works for you.

I tried millions of themes but I must say bluecurve is the best for me. It is easy, simple and does not distract me while working like other 3D bloated themes.

Greetings

Felix

---

### Post by bpilgrim1979 on 2005-06-30
Go to [http://art.gnome.org/](http://art.gnome.org/) and download Clearlooks.

---

### Post by angrykeyboarder on 2005-07-06
[QUOTE=Nano]Indeed, it is a very nice theme and I used it till a bit ago, now the human theme has improved enough and I don't need it anymore.[/QUOTE]

How has Human "improved"?

It's still brown.....

---

### Post by Ken.Lank on 2005-07-22
[QUOTE=mach_zero]
You've may already figured this out by now, but for anyone who hasn't, this is the icon you need to replace. Launch Nautilus (File Browser) and go to "View>Show Hidden Files" in your Home Folder to enable you to see the ".icons" folder:

.icons/Bluecurve/16x16/apps/icon-panel-menu.png
[/QUOTE]

OK, I browsed to the .icons directory and do not have any Bluecurve directory under it.

I'd like to get rid of the dang "Red Hat" icon ... How can I get the foot back?

---

### Post by Indigo2 on 2005-09-19
I ran into this problem installing the latest one:

yourname@yourmachine: alien -i redhat-artwork*
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
        xargs -0 -r -i cp -a {} debian/redhat-artwork
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dh_gencontrol
dpkg-gencontrol: error: current build architecture i386 does not appear in package's list (amd64)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: redhat-artwork-0.128: No such file or directory

Any suggestions?

---

### Post by Fearan on 2005-11-29
Does anyone know where to get a really huge pack of bluecurve icons? (i.e. ones that cover a lot of apps?)

---

### Post by Xian on 2005-11-29
[QUOTE=Fearan]Does anyone know where to get a really huge pack of bluecurve icons? (i.e. ones that cover a lot of apps?)[/QUOTE]

Sure, here you go: [Bluecurve Complete Icons](http://download.fedora.redhat.com/pub/fedora/linux/core/development/i386/Fedora/RPMS/redhat-artwork-0.131-1.i386.rpm)
Then just use the alien command to convert to a .deb file.

---

### Post by angrykeyboarder on 2005-11-30
[quote=Xian]Sure, here you go: [Bluecurve Complete Icons]("http://download.fedora.redhat.com/pub/fedora/linux/core/development/i386/Fedora/RPMS/redhat-artwork-0.131-1.i386.rpm")
Then just use the alien command to convert to a .deb file.[/quote] 
That's more than just icons and I'm not entirely sure that's what the poster wanted.  I gathered more than the standard ones were desired.

---

### Post by Xian on 2005-11-30
They need only remove the additional bluecurve themes from /usr/share/themes if so desired. I am not aware of a more comprehensive set of bluecurve icons other than those in the linked package, but would certainly be interested if a member is aware of one.

---

### Post by angrykeyboarder on 2005-11-30
[quote=Xian]They need only remove the additional bluecurve themes from /usr/share/themes if so desired. I am not aware of a more comprehensive set of bluecurve icons other than those in the linked package, but would certainly be interested if a member is aware of one.[/quote] 
I'm not aware of a more comprehensive set of icons either. However, you might want to take a closer look at that package. It installs far more than you think.

Here's just ***some ***of what you didn't mention.:

/usr/lib/gtk/themes/engines/libbluecurve.so
 /usr/lib/[gtk-2.0/2.4.0/engines/libbluecurve.la]("http://gtk-2.0/2.4.0/engines/libbluecurve.la")
 /usr/lib/[gtk-2.0/2.4.0/engines/libbluecurve.so]("http://gtk-2.0/2.4.0/engines/libbluecurve.so")
/usr/lib/kde3/kwin3_bluecurve.la
/usr/lib/kde3/kwin3_bluecurve.so
/usr/lib/kde3/kwin3_bluecurve.so.0
/usr/lib/kde3/kwin3_bluecurve.so.0.0.0

I have no idea why those files are even necessary in RedHat/Fedora, but anyhow...

---

