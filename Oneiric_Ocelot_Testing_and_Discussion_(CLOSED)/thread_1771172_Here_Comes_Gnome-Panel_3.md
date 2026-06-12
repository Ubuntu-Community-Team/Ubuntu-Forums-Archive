---
title: "Here Comes Gnome-Panel 3"
date: 2011-05-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Vrroom on 2011-05-30
gnome-panel 3 is now available in Oneiric. Should be mirrored in all servers in few hours :P

[https://launchpad.net/ubuntu/oneiric/+source/gnome-panel/1:3.0.2-0ubuntu1](https://launchpad.net/ubuntu/oneiric/+source/gnome-panel/1:3.0.2-0ubuntu1)

---

### Post by ubername on 2011-05-30
What am I looking for? I just refreshed from the main server and I still have gnome-panel 1:2.32.1-0ubuntu6.5

---

### Post by Vrroom on 2011-05-30
It will take time to build. Only source is available ATM.

---

### Post by dino99 on 2011-05-30
why such post ?

Missing build dependencies: libwnck-3-dev

so its not ready at all.

---

### Post by Vrroom on 2011-05-30
> **dino99 said:**
> why such post ?

Missing build dependencies: libwnck-3-dev

so its not ready at all.

Oh, totally missed it.

---

### Post by JMB74 on 2011-05-30
New version seems to be building.

[https://launchpad.net/ubuntu/+source/gnome-panel/1:3.0.2-0ubuntu2](https://launchpad.net/ubuntu/+source/gnome-panel/1:3.0.2-0ubuntu2)

---

### Post by Harry33 on 2011-05-30
Newer version (3.0.2-0ubuntu2) is ready now.
But, also the previous version (3.0.2-0ubuntu1) was OK (the state is new, so it is ready to be downloaded).
Here is the older version (3.0.2-0ubuntu1):
[https://launchpad.net/ubuntu/oneiric/+source/gnome-panel/1:3.0.2-0ubuntu1](https://launchpad.net/ubuntu/oneiric/+source/gnome-panel/1:3.0.2-0ubuntu1)

And the newer version (3.0.2-0ubuntu2) is here:
[https://launchpad.net/ubuntu/oneiric/+source/gnome-panel/1:3.0.2-0ubuntu2](https://launchpad.net/ubuntu/oneiric/+source/gnome-panel/1:3.0.2-0ubuntu2)

So now we have Gnome-panel GTK+3, which is the default fallback session to Gnome-shell.
The Gnome-shell is not yet ready (dependency wait),
but you can get it from Ricotz Testing PPA.
Here:
[https://launchpad.net/~ricotz/+archive/testing](https://launchpad.net/~ricotz/+archive/testing)

---

### Post by Harry33 on 2011-05-30
I have now tested the new gnome-panel_3.0.2-0ubuntu2 (the GTK+3 version).
It looks very nice and works well.
It needs to have gnome-session-fallback installed.
:guitar:

BTW
It is a good, fine looking pair with gnome-shell.

---

### Post by lucazade on 2011-05-30
> **Harry33 said:**
> I have now tested the new gnome-panel_3.0.2-0ubuntu2 (the GTK+3 version).
It looks very nice and works well.
It needs to have gnome-session-fallback installed.
:guitar:

BTW
It is a good, fine looking pair with gnome-shell.

Yep, panel works nicely.. unfortunately installing it ATM it wipes out ubuntu-desktop and indicator-* :)
How to remove launchers from panel once added?

---

### Post by dino99 on 2011-05-30
sadly "system prefs appearance" is gone, so how to tweak themes ?

---

### Post by Hanmac on 2011-05-30
hm on my system ubuntu-desktop and the indicator-* are installed but ubuntustudio-desktop is gone because the new panel breaks gnome-applets (version to old)

some packages to update:
[s]gnome-applets[/s]
and the “meta-gnome2” packages

hm the gnome-icon-theme-extras have a very wrong depence:
gnome-icon-theme >=3.0 AND gnome-icon-theme <2.9

---

### Post by lucazade on 2011-05-30
> **dino99 said:**
> sadly "system prefs appearance" is gone, so how to tweak themes ?

via dconf-editor

---

### Post by dino99 on 2011-05-30
> **lucazade said:**
> via dconf-editor

Thanks, but i cant see how to get "System" menu back into top-panel, thats weird :(

---

### Post by 3vi1 on 2011-05-30
> **dino99 said:**
> Thanks, but i cant see how to get "System" menu back into top-panel, thats weird :(

Same problem here.  I thought maybe I removed a package I shouldn't have removed.  gnome-applets, perhaps?

---

### Post by donniezazen on 2011-05-30
E: /var/cache/apt/archives/gnome-panel_1%3a3.0.2-0ubuntu2_i386.deb: trying to overwrite '/usr/share/applications/gnome-panel.desktop', which is also in package gnome-panel-data 1:2.32.1-0ubuntu6.5

---

### Post by Hanmac on 2011-05-30
soham_1207: this can solved if you make gnome-panel and gnome-panel-data as to reinstall

---

### Post by novatillasku on 2011-05-30
After updates (gnome-panel..etc..) i can't login with Classical Desktop, give me login error.Unity is ok, but windows buttons (close, max, min) there isn't, jeje..
(terrible my english ;-)

---

### Post by Harry33 on 2011-05-30
> **lucazade said:**
> Yep, panel works nicely.. unfortunately installing it ATM it wipes out ubuntu-desktop and indicator-* :)
How to remove launchers from panel once added?

You mean the gnome-panel (GTK+2) launchers?
They are in your home folder, here:
.gconf/apps/panel/
Just delete the whole panel folder (not the new panel3-applets folder).

---

### Post by Harry33 on 2011-05-30
> **novatillasku said:**
> After updates (gnome-panel..etc..) i can't login with Classical Desktop, give me login error.Unity is ok, but windows buttons (close, max, min) there isn't, jeje..
(terrible my english ;-)

Do you have gnome-session-fallback installed?

You may have to reinstall the new package gnome-panel, because it tends to be left unconfigured at first attempt.

---

### Post by donniezazen on 2011-05-30
> **Hanmac said:**
> soham_1207: this can solved if you make gnome-panel and gnome-panel-data as to reinstall

Thanks fixed it.

---

### Post by Harry33 on 2011-05-30
> **3vi1 said:**
> Same problem here.  I thought maybe I removed a package I shouldn't have removed.  gnome-applets, perhaps?

The new gnome-applets package (2.91.4) is in repos, here:
[https://launchpad.net/ubuntu/oneiric/+source/gnome-applets/2.91.4~20110321-1ubuntu1](https://launchpad.net/ubuntu/oneiric/+source/gnome-applets/2.91.4~20110321-1ubuntu1)

---

### Post by MacUntu on 2011-05-30
Do I understand this right: the gnome panel is themed via CSS? If so, where would I find the files to play around? Don't like depressing black...

Edit: Ah, it's gtk-3.0/gtk-widgets.css

Update: I altered the Adwaita file, but that didn't change anything.

---

### Post by 3vi1 on 2011-05-30
> **Harry33 said:**
> The new gnome-applets package (2.91.4) is in repos, here:
[https://launchpad.net/ubuntu/oneiric/+source/gnome-applets/2.91.4~20110321-1ubuntu1](https://launchpad.net/ubuntu/oneiric/+source/gnome-applets/2.91.4~20110321-1ubuntu1)

Yeah, I installed it a little bit ago, but I still don't see the system menu icon on my titlebars.  :\

---

### Post by lucazade on 2011-05-30
> **Harry33 said:**
> You mean the gnome-panel (GTK+2) launchers?
They are in your home folder, here:
.gconf/apps/panel/
Just delete the whole panel folder (not the new panel3-applets folder).

I meant some application launchers I've added to new gnome-panel gtk3 and in contextual menu there is not "Delete Item" (like in old panel)!
I made a drag-and-drop from main-menu to panel.

Edit: gnome-panel gtk3 switched from gconf to gsettings/dconf
in org/gnome/gnome-panel/layout/objects.. there are my custom lauchers.. now i've to find some gsettings commandline to purge them.. is it possible a simple "delete item" is not available??!

---

### Post by MacUntu on 2011-05-30
It's in ~/.config/gnome-panel/launchers/

---

### Post by lucazade on 2011-05-30
> **MacUntu said:**
> It's in ~/.config/gnome-panel/launchers/

those are the old for gnome-panel gtk2.. check my post before, i've added some notes

---

### Post by MacUntu on 2011-05-30
Well, I removed my custom launcher by deleting the .desktop file in that directory and restarting gnome-panel. :)

But yeah, that leaves the entry in org.gnome... intact. :-(

If you find a way to remove dconf entries, let Ask Ubuntu know: [http://askubuntu.com/questions/45535/how-do-i-clean-up-my-dconf-database](http://askubuntu.com/questions/45535/how-do-i-clean-up-my-dconf-database) ;)

---

### Post by lucazade on 2011-05-30
you're right, those .desktop are for gtk3 version.. anyway also the gsetting entry should be removed alongside .desktop files

---

### Post by MacUntu on 2011-05-30
Btw, with your Ambiance from trunk, the Applications menu doesn't open from the first pixel column.

---

### Post by lucazade on 2011-05-30
> **MacUntu said:**
> Btw, with your Ambiance from trunk, the Applications menu doesn't open from the first pixel column.

true.. i'm working on the panel now, i'm going to fix that odd behavior!

there is an object in top panel called "user-menu"  or "PanelInternalFactory::UserMenu" that eats tons of pixel... i'm getting crazy to find out its css widget name to tweak it... ugh!

---

### Post by kansasnoob on 2011-06-02
Gnome-panel 3 convinced me to focus on Lubuntu :)

IMHO everything Gnome related ATM is just heading from stable to fubar, I can use Unity a little bit but for everyday use Lubuntu is now better for me.

---

### Post by jfernyhough on 2011-06-02
Just for information, I finally found out from [here]("https://bbs.archlinux.org/viewtopic.php?id=118378") that you can alter gnome-panel 3 (i.e. the fallback panel) the same as gnome-panel 2 - but by using ALT-Right click instead of just right-click. Moving can be done with ALT-middle click.

Nicely hidden, GNOME-devs. :D

---

### Post by lucazade on 2011-06-02
> **jfernyhough said:**
> Just for information, I finally found out from [here]("https://bbs.archlinux.org/viewtopic.php?id=118378") that you can alter gnome-panel 3 (i.e. the fallback panel) the same as gnome-panel 2 - but by using ALT-Right click instead of just right-click. Moving can be done with ALT-middle click.

Nicely hidden, GNOME-devs. :D

I wonder why I've to use ALT+left click+right click instead to get the contextual menu on panel.. it looks like I'm the only one :D

---

### Post by kansasnoob on 2011-06-02
> **lucazade said:**
> I wonder why I've to use ALT+left click+right click instead to get the contextual menu on panel.. it looks like I'm the only one :D

The next great idea is to require two mice :lolflag:

Left mouse -> right click, right mouse -> middle click, stand on head, rub belly and press return.

---

### Post by lucazade on 2011-06-02
> **kansasnoob said:**
> The next great idea is to require two mice :lolflag:

Left mouse -> right click, right mouse -> middle click, stand on head, rub belly and press return.

Ahahah.. the impossible combination!!

Looking at [Vuntz blog]("http://www.vuntz.net/journal/post/2011/04/13/gnome-panel-is-dead%2C-long-live-gnome-panel%21") about new gnome-panel I've found:
"Still editable, but not by accident: this all sounds cool, but you tried to add an applet, or to even just move one, but without success? There's a *secret* trick here: press alt (or the modifier configured for metacity, if you changed it) and right-click"

So secret that I need also the left-click.. woohoo!!

---

### Post by kansasnoob on 2011-06-03
> **lucazade said:**
> Ahahah.. the impossible combination!!

Looking at [Vuntz blog]("http://www.vuntz.net/journal/post/2011/04/13/gnome-panel-is-dead%2C-long-live-gnome-panel%21") about new gnome-panel I've found:
"Still editable, but not by accident: this all sounds cool, but you tried to add an applet, or to even just move one, but without success? There's a *secret* trick here: press alt (or the modifier configured for metacity, if you changed it) and right-click"

So secret that I need also the left-click.. woohoo!!

Thanks for that link, pretty good info there.

I LOL'ed at this:

> Port to GSettings: since we wanted to be cool, there was no way we would still use the venerable gconf to store settings. Porting to GSettings was quite fun, especially as gnome-panel was probably one of the heaviest user of gconf (and it was certainly using it in interesting ways). We now use GSettings in interesting ways too since some API is still missing in GSettings. Oh, and we're also using dconf (which is what GSettings uses as a backend by default) directly, **[COLOR="Red"]which is completely insane and crazy. But we love insane and crazy![/COLOR]**

IMHO they took "insane and crazy" to a whole new level :D

I know opinions differ greatly regarding gnome3, gnome-shell, and unity but for this old man it's just too much change for my old noggen to handle.

I wish someone would comment about the change to gnome2 in about 2002. I'll bet it took a long time to get things sorted as well as they were when I started with Gnome in Ubuntu's Gutsy.

I loved Gnome2 so it's very hard to give up the simplicity of customizing it to just make it work for nearly anyone :cry:

---

