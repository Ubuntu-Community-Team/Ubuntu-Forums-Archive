---
title: "HOWTO: GNOME - Remove Menu Icon Arrow"
date: 2008-03-24
forum: Outdated Tutorials &amp; Tips
---

### Post by andrek on 2008-03-24
Ok, I finally found a way to get rid of that ugly white/black arrow near the Ubuntu [ or custom ] icon of menu button in GNOME.
```

sudo apt-get install apt-build
*while configuring, choose your processor type* 
sudo apt-build source gnome-panel
sudo apt-get build-dep gnome-panel
cd /var/cache/apt-build/build/
sudo gedit gnome-panel-*/gnome-panel/panel-menu-button.c

```
now change the following part :
> button = g_object_new (PANEL_TYPE_MENU_BUTTON,
"menu-path", menu_path,
"custom-icon", custom_icon,
"tooltip", tooltip,
"use-menu-path", use_menu_path,
"use-custom-icon", use_custom_icon,
"has-arrow", **TRUE**,
NULL); 
into
> button = g_object_new (PANEL_TYPE_MENU_BUTTON,
"menu-path", menu_path,
"custom-icon", custom_icon,
"tooltip", tooltip,
"use-menu-path", use_menu_path,
"use-custom-icon", use_custom_icon,
"has-arrow", **FALSE**,
NULL); 
save & exit and
```
cd gnome-panel-*/
sudo ./configure
[i]in case there are still some missing dependencies (build-dep may miss something), install them manually [ most of them are the -dev packages, so use synaptic for that - **for example** when it shows **No package 'libgnomeui-2.0' found**
 , just search in Synaptic Package Manager for libgnomeui (**forget about -2.0 or any other number**) and install the **-dev** package, **libgnomeui-dev**.][/i]
sudo make
sudo make install
sudo killall gnome-panel

```

that's all.

---

### Post by light50 on 2008-03-25
Hi, thanks, do you have a screen shot of the result?

---

### Post by andrek on 2008-03-25
Here it is : [IMG]http://xs125.xs.to/xs125/08132/menu266.png[/IMG]

---

### Post by BOBSONATOR on 2008-03-27
awsome tutorial man, works flawlessly

---

### Post by andrek on 2008-03-27
Thanks, I appreciate your reply ;)

---

### Post by bigbrovar on 2008-04-04
Awesome ... Simpliy Wicked .. This Thing Worked Like A Charm .. Thanks Man

---

### Post by TheOneAlex on 2008-04-05
Hello folks,
I've been trying to remove that ugly arrow for some days with no luck.
The method described in "macmenu" thread didn't work for me(near the page  Andrek achieved to use compiz config to activate transparency on gnome-panel but keeping awn without transparency, i think its about page 105). There was an error when I got to the "debuild" step.

Now I tried this methode, but on ./configure, there are several package dependencies that aren't met by my sistem, and when I try to get them with synaptic, it only let me install lower versions that the ones that are needed.

I want to know if this method works only for Hardy Heron, cause I have Gusty on an AMD machine,

Regards!

---

### Post by serial00 on 2008-05-31
hello, thank you for this how-to, so good to get off this arrow. But I've noticed that the exit menu has changed, am I the only one? does anyone know how to fix it?

Regards

PS : TheOneAlex, I did it on Gutsy on a friend's computer and it worked properly

---

### Post by andrek on 2008-05-31
No, you're not the only one.
It seems that Ubuntu team adds some patches into the panel, which are missed when we compile it by ourselves. No big deal for me, but if somebody find any info on that - inform us please ;)

---

### Post by mistakenidentity on 2008-06-01
What if I have a Core2Duo machine? I'm not sure what processor choice to put in there. Can anyone help me?

---

### Post by andrek on 2008-06-01
Are you using a 64bit system? If so, use nocona. If 32bit - use presscot. *(as [http://jeffrasmussen.wordpress.com/2007/11/20/apt-build-for-intel-duo-core-2/](http://jeffrasmussen.wordpress.com/2007/11/20/apt-build-for-intel-duo-core-2/) says)*

---

### Post by mistakenidentity on 2008-06-01
Thank You.

---

### Post by endz on 2008-06-06
hey, do you have deb package?
because when i try to compile it, there are a lot of package i cant install manually

thx

---

### Post by andrek on 2008-06-07
Nope, sorry.
Try to search those dependencies by Synaptic ( remember to install also -dev packages )

---

### Post by endz on 2008-06-09
help, after i compile the panel
this thing gone weird
if i click top right icon(shutdown)
it only show "Switch user', "cancel", "log out"

to shutdown, i have to choose from menu

how to repair this thing?
like from original hardy menu

---

### Post by Bacardilvr on 2008-06-28
Yeah, I'm having the same issues. Hopefully a fix will be found.

---

### Post by serial00 on 2008-07-19
I think it's the same for everyone, but what's interresting is that when I push the power button on my pc, the usual exit menu appears, so it's still somewhere...

Btw, thanks to andreck ;)

---

### Post by andrek on 2008-07-19
Seriously, I have no clue what's wrong. I've tried adding ubuntu patches but it still doesn't look like just after ubuntu installation.

---

### Post by lumix700i on 2008-08-05
this method didnt work from me. i got this message

> agung@agung-laptop:~$ sudo apt-build source gnome-panel
Missing source package name for source_by_source().


anyone can help me?

---

### Post by andrek on 2008-08-05
> **lumix700i said:**
> this method didnt work from me. i got this message



anyone can help me?

Do you have deb-src repositories in your sources.list ?

---

### Post by InfinityCircuit on 2008-08-05
Am I missing something? Why are you using apt-build + make install?  Why not apt-get source + debuild which will create debs?

---

### Post by InfinityCircuit on 2008-08-10
I have built amd64 and i386 debs for this patch on my ppa.  Feel free to use them.  This will also overcome the issue of make install being non-reversible.

[https://launchpad.net/~dmoerner/+archive](https://launchpad.net/~dmoerner/+archive)

If you just want the patch:

```
dmr@skynet:~/Documents/Work/gnome-panel$ cat gnome-panel-2.22.2/debian/patches/91_no-arrow-fix.patch 
--- gnome-panel-2.22.2/gnome-panel/panel-menu-button.c	2008-08-10 18:13:55.000000000 -0700
+++ gnome-panel-2.22.2.new/gnome-panel/panel-menu-button.c	2008-08-10 18:13:39.000000000 -0700
@@ -643,7 +643,7 @@ panel_menu_button_load (const char  *men
 			       "tooltip", tooltip,
 			       "use-menu-path", use_menu_path,
 			       "use-custom-icon", use_custom_icon,
-			       "has-arrow", TRUE,
+			       "has-arrow", FALSE,
 			       NULL);
 
 	info = panel_applet_register (GTK_WIDGET (button), NULL, NULL,
```

---

### Post by sandpaperback on 2008-09-29
Thank you so much for the package!  It worked flawlessly and I'm FINALLY rid of that arrow!

---

### Post by ondope on 2008-10-08
thank you very much for this repo. Just what I was looking for :)

---

### Post by faraday on 2008-10-12
When I run:
> 
sudo gedit gnome-panel-*/gnome-panel/panel-menu-button.c

the file doesn't seem to exist?

---

### Post by andrek on 2008-10-12
> **faraday said:**
> When I run:


the file doesn't seem to exist?
Instead of manual editing files and building it up, use following repository :
```
deb http://ppa.launchpad.net/dmoerner/ubuntu hardy main
deb-src http://ppa.launchpad.net/dmoerner/ubuntu hardy main
```
- add it to your sources.list file and then install gnome-panel from it.

---

### Post by faraday on 2008-10-12
After adding the repositories I get:

gnome-panel:
  Depends: libebook1.2-9 (>=2.22.3) but 2.22.1-0ubuntu2 is to be installed
  Depends: libecal1.2-7 (>=2.22.3) but 2.22.1-0ubuntu2 is to be installed
  Depends: libedataserver1.2-9 (>=2.22.3) but 2.22.1-0ubuntu2 is to be installed
  Depends: libedataserverui1.2-8 (>=2.22.3) but 2.22.1-0ubuntu2 is to be installed
  Depends: libpango1.0-0 (>=1.20.5) but 1.20.1-1 is to be installed

---

### Post by andrek on 2008-10-12
Hm, I guess the repository's owner hasn't updated its files. I'll try to contact him.

---

### Post by faraday on 2008-10-13
Thanks.

I am currently stuck without any taskbar at all, and with that I appear to have lost the ability to run terminal. Oh dear!

---

### Post by andrek on 2008-10-21
Sorry for a long delay, but I've finally got a response from the repository's maintainer.

> Thanks for the heads up.  I will build a hardy chroot in the next
couple of days to test this out.

---

### Post by InfinityCircuit on 2008-10-21
Hi, sorry, I didn't watch this thread or my freenode account recently.  I cannot reproduce the reported problem with my packages.  If your taskbar, etc. have disappeared, then you probably have bigger problems than this.

---

### Post by evrkusd on 2008-10-22
sick. thanks for the modified install. very easy.

---

### Post by phynix on 2008-11-16
Intrepid support?

---

### Post by Yankee_Fan on 2008-12-15
> **phynix said:**
> Intrepid support?

Ditto!  BUMP!

---

### Post by phynix on 2008-12-16
I just followed the instructions on the first page to compile from source.

---

### Post by unique on 2009-01-10
> **phynix said:**
> Intrepid support?

For everyone running Intrepid 8.10 I justed wanted to let you all know that this guide does work!

---

### Post by Sugz on 2009-01-14
^ What about for Gutsy? - Dont worry i will switch to hardy sometime :p

---

### Post by HunterK on 2009-01-17
I'm confused.  Which arrow are you talking about?  The one next to every menu item that can expand to a new menu?

EDIT: never mind, I see there is a different type of menu button you can add via "Add To panel".  I see the arrow.

---

### Post by phandrew08 on 2009-02-09
after changing the value from true to false, im having trouble doing the rest in the code. when i input cd gnome-panel-*/ into terminal, it says it is not a directory

---

### Post by Alex6969 on 2009-03-06
Wow works great. It's an awful lot of work though just to get an arrow off the menu button, there should be an eaisier way to accomplish this.

---

### Post by Themaister on 2009-04-14
This is why I love free software =)

---

### Post by mishathegoat on 2009-05-15
Thought I'd let everyone know this works in Jaunty.. (Not the first method with the resources.. but the second manual method)

---

### Post by p!u$ on 2009-06-02
> **mishathegoat said:**
> Thought I'd let everyone know this works in Jaunty.. (Not the first method with the resources.. but the second manual method)

Yes, I follow this manual and it works in Jaunty.

---

### Post by gegadeath on 2009-06-30
Hi folks,

Thanx for this tuto I ,as well, have that ugly arrow on the panel's main button. I followed the instructions and everything went good. but I type 

```
sudo ./configure
```

I get this :

```
No package 'gnome-desktop-2.0' found
No package 'libgnome-menu' found
No package 'dbus-glib-1' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PANEL_CFLAGS
and PANEL_LIBS to avoid the 
the problem is that when I look for those packages in synaptic No package 'gnome-desktop-2.0' found
No package 'libgnome-menu' found
No package 'dbus-glib-1' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables PANEL_CFLAGS
and PANEL_LIBS to avoid the need to call pkg-confneed to call pkg-config.
See the pkg-config man page for more details.

```

the problem is that when I look for those packages in synaptic I can't find them. 

SOS !

---

### Post by andrek on 2009-06-30
Try using

```
sudo apt-get build-dep gnome-panel
```

I tried it on my Jaunty installation and it worked great, solved all the dependencies.

Otherwise, install :
```
libgnome-desktop-2-11 libgnome-desktop-dev libgnome-menu2 libgnome-menu-dev libdbus-glib-1-2 libdbus-glib-1-dev
```

---

### Post by gegadeath on 2009-06-30
Thanx andrek, I'll give that a try!

---

### Post by gegadeath on 2009-06-30
Greaaaaaaaat !

Andrek that worked like a charm, thanks a bunch ;)

---

### Post by basiix on 2009-07-02
Hey guys, I found a really easy way to get rid of that ugly menu arrow. All you have to do is navigate to this location: /usr/share/themes/THEME YOUR USING/gtk-2.0/Images/Arrows
Once in that folder just delete the two arrows pointing down.
they should be called arrow-down.png and arrow-down-dark.png i believe.
Good luck!

---

### Post by andrek on 2009-07-03
Well, your method depends on what GTK theme are you using.
First of all, ~/.themes is more commonly used for installing new themes, thus direction you have provided may be wrong.
Second, many of GTK themes do not consist of custom arrow icons ( I haven't seen any, to be honest ). There are lots of simple themes that contain only gtkrc file.

---

### Post by coldReactive on 2009-08-03
Bumping, subscribing.

Just wanting to know: I will have to do this all over again if I dist-upgrade, right?

---

### Post by fela on 2009-08-14
Great tutorial :)

But isn't there a less involved method than recompiling the whole gnome-panel? It should be an option really.

---

### Post by coldReactive on 2009-08-14
> **fela said:**
> Great tutorial :)

But isn't there a less involved method than recompiling the whole gnome-panel? It should be an option really.

The other option is theme-based, not system-wide.

---

### Post by p0cky84 on 2009-09-07
Ilu <33

---

### Post by hypertime179 on 2009-10-12
Great  5 stars! works perfectly on a gateway machine with a pentium 4 processor and 18 gb of hd space and around 400 mb of ram!
I am running karmic beta and have nvidia and a edited xorg.conf:popcorn:
:guitar:=P~

---

### Post by J-Buntu on 2009-11-11
Oh what joy that was - all to banish that little bloody arrow... totally worth it though. Looking at the date of the post i wasn't sure it would still work, but it's perfect. mmm look at my lovely arrow-less menu =) This really should be easier though, a lot of people wouldn't even try this... Done on the final release of Karmic - incase anyone is wondering =P

---

### Post by andrek on 2009-11-11
Thanks, great to hear it is still working.

---

### Post by Hellene Atheist on 2009-11-19
Success! Thank you! =D> \\:D/

---

### Post by Mattevt on 2009-12-21
> **andrek said:**
> Ok, I finally found a way to get rid of that ugly white/black arrow near the Ubuntu [ or custom ] icon of menu button in GNOME.
```

sudo apt-get install apt-build
*while configuring, choose your processor type* 
sudo apt-build source gnome-panel
sudo apt-get build-dep gnome-panel
cd /var/cache/apt-build/build/
sudo gedit gnome-panel-*/gnome-panel/panel-menu-button.c

```
now change the following part :

into

save & exit and
```
cd gnome-panel-*/
sudo ./configure
[i]in case there are still some missing dependencies (build-dep may miss something), install them manually [ most of them are the -dev packages, so use synaptic for that - **for example** when it shows **No package 'libgnomeui-2.0' found**
 , just search in Synaptic Package Manager for libgnomeui (**forget about -2.0 or any other number**) and install the **-dev** package, **libgnomeui-dev**.][/i]
sudo make
sudo make install
sudo killall gnome-panel

```

that's all.

That seemed like a lot of work for such a small accomplishment. Regardless, I'm happy. Thanks!!!

---

### Post by Sizzlintrumpet on 2010-03-09
Welcome to the year 2010, 4 years has passed, and this solution still helped me solve this problem.

How much longer until there will be an easier way to accomplish this?

Many thanks andrek!

---

### Post by x-shaney-x on 2010-04-15
I can't remember where I originally found this info but I have this in my ~/.gtkrc-2.0 file:
```
style "panel-arrow-remove"

#the following removes the arrows from the panel
{
engine "pixmap"
    {
    image
    {
        function    = ARROW
        recolorable    = TRUE
        overlay_file    = "arrows/arrow-blank.png"
        overlay_border    = {2,2,2,2}
        overlay_stretch    = FALSE
        arrow_direction    = UP
    }

    image
    {
        function    = ARROW
        recolorable    = TRUE
        overlay_file    = "arrows/arrow-blank.png"
        overlay_border    = {2,2,2,2}
        overlay_stretch    = FALSE
        arrow_direction    = DOWN
    }
    }
}

widget_class "*PanelToplevel*"             style "panel-arrow-remove"
```

Works fine for me and I am using it in linux Mint, karmic and lucid (with Ambiance).

---

### Post by ceelo on 2010-04-28
> **x-shaney-x said:**
> I can't remember where I originally found this info but I have this in my ~/.gtkrc-2.0 file:
```
style "panel-arrow-remove"

#the following removes the arrows from the panel
{
engine "pixmap"
    {
    image
    {
        function    = ARROW
        recolorable    = TRUE
        overlay_file    = "arrows/arrow-blank.png"
        overlay_border    = {2,2,2,2}
        overlay_stretch    = FALSE
        arrow_direction    = UP
    }

    image
    {
        function    = ARROW
        recolorable    = TRUE
        overlay_file    = "arrows/arrow-blank.png"
        overlay_border    = {2,2,2,2}
        overlay_stretch    = FALSE
        arrow_direction    = DOWN
    }
    }
}

widget_class "*PanelToplevel*"             style "panel-arrow-remove"
```

Works fine for me and I am using it in linux Mint, karmic and lucid (with Ambiance).

Perfect!

andrek's method still works as well as of 2.30 but this is so much simpler and a fix for other distros.

---

### Post by jacksonpollack on 2010-05-03
The problem with the simpler method above is that yes, it gets rid of that pesky black arrow, but it also changes/deletes the icon that separates the notification area from the rest of the panel (also the one to the left of the window list).

---

### Post by donkihote on 2010-05-10
i wish this task will be added to Ubuntu-tweak to make more easy for other newbie...like me :D

---

### Post by x-shaney-x on 2010-05-11
> **jacksonpollack said:**
> The problem with the simpler method above is that yes, it gets rid of that pesky black arrow, but it also changes/deletes the icon that separates the notification area from the rest of the panel (also the one to the left of the window list).
I only just noticed that.  You are quite right, though with some themes I would consider that a bonus.
Although it removes the appearance, you are still able to drag them as if it was there.

---

### Post by Johonunu on 2010-06-06
**@andrek**

Thank you so much ;) Your HOWTO works great on Ubuntu Lucid 10.04 x64 !

---

### Post by onethirtythreeseven on 2010-10-01
This worked the last time I tried it using 10.04, however on a fresh install of the 10.10 release candidate, it no longer works.  Suggestions?

---

### Post by OliverN on 2010-10-01
getting problems in 10.10 too. for some reason make crashes?

```
make[4]: *** [gnome-panel] Error 1
make[4]: Leaving directory `/home/me/gnome-panel-2.30.2/gnome-panel'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/me/gnome-panel-2.30.2/gnome-panel'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/me/gnome-panel-2.30.2/gnome-panel'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/me/gnome-panel-2.30.2'
make: *** [all] Error 2

```

Does this mean anything to anyone?

---

### Post by onethirtythreeseven on 2010-10-01
It doesn't crash when I do it, it just doesn't remove the arrow.  I decompiled it again and checked, and the change went through, it just didn't have the desired effect, even though I restarted gnome-panel and even rebooted.

---

### Post by OliverN on 2010-10-03
> **OliverN said:**
> getting problems in 10.10 too. for some reason make crashes?

```
make[4]: *** [gnome-panel] Error 1
make[4]: Leaving directory `/home/me/gnome-panel-2.30.2/gnome-panel'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/me/gnome-panel-2.30.2/gnome-panel'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/me/gnome-panel-2.30.2/gnome-panel'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/me/gnome-panel-2.30.2'
make: *** [all] Error 2

```

Does this mean anything to anyone?

ok, well I found out what my problem was. The gnome-panel-* folder I had to use was packed in a .tar.gz file called **gnome-panel_2.30.2.orig.tar.gz**. After unpacking and using that the installation worked, and my panel is now arrow-less :)

---

### Post by onethirtythreeseven on 2010-10-03
> **OliverN said:**
> ok, well I found out what my problem was. The gnome-panel-* folder I had to use was packed in a .tar.gz file called **gnome-panel_2.30.2.orig.tar.gz**. After unpacking and using that the installation worked, and my panel is now arrow-less :)

I'm not sure I follow. Was this after you went through the decompiling process? Could you break down exactly what you did? I'm still trying to learn how to do things like this in Ubuntu.

---

### Post by OliverN on 2010-10-04
> **onethirtythreeseven said:**
> I'm not sure I follow. Was this after you went through the decompiling process? Could you break down exactly what you did? I'm still trying to learn how to do things like this in Ubuntu.

Alright, to do what I did here's what you do.

assuming you've still got the files in your /var/cache/apt-build/build/ -folder try doing

```
tar -xzvf /var/cache/apt-build/build/gnome-panel_2.30.2.orig.tar.gz -C ~/
```

to extract the contents of the file I mentioned to your home dir. -If this fails for some reason you could just navigate there via. the file browser (nautilus) and copy the gnome-panel_2.30.2.orig.tar.gz -file to your home dir, then extract it. Then do 

```
cd ~/gnome-panel-2.30.2/
sudo gedit gnome-panel/panel-menu-button.c
```
and do the needed changes to the file (what andrek posted)

then run the final commands```

sudo ./configure
sudo make
sudo make install
sudo killall gnome-panel
```

after that you can remove the **gnome-panel-2.30.2** folder from your home dir.

Hope it works for you too...

---

### Post by onethirtythreeseven on 2010-10-04
Perfect!  Thanks.

---

### Post by Hellene Atheist on 2010-11-01
thanks oliver, it worked for my maverick, too

---

### Post by QXY7 on 2011-01-10
> **jacksonpollack said:**
> The problem with the simpler method above is that yes, it gets rid of that pesky black arrow, but it also changes/deletes the icon that separates the notification area from the rest of the panel (also the one to the left of the window list).
Took me a while to figure out (this will make the handles blank as well):
```
style "panel-arrow-remove"
#the following removes the arrows from the panel
{
engine "pixmap"
    {
    image
    {
        function    = ARROW
        recolorable    = TRUE
        overlay_file    = "arrows/arrow-blank.png"
        overlay_border    = {2,2,2,2}
        overlay_stretch    = FALSE
        arrow_direction    = UP
    }
    image
    {
        function    = ARROW
        recolorable    = TRUE
        overlay_file    = "arrows/arrow-blank.png"
        overlay_border    = {2,2,2,2}
        overlay_stretch    = FALSE
        arrow_direction    = DOWN
    }
    image
    {
      function			= HANDLE
      recolorable		= TRUE
      overlay_file		= "arrows/arrow-blank.png"
      overlay_stretch	= FALSE
      orientation		= VERTICAL
    }
    image
    {
      function			= HANDLE
      overlay_file		= "arrows/arrow-blank.png"
      overlay_stretch 	= FALSE
      orientation		= HORIZONTAL
    }
    }
}

widget_class "*PanelToplevel*" 			style "panel-arrow-remove"
```

---

