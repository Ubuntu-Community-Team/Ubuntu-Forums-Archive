---
title: "Gnome3 packages in Oneiric repos"
date: 2011-05-17
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-05-17
There are new Gnome3 packages in official Oneiric repos now.
ATM these GTK+2 versions have been upgraded to GTK+3 versions:

- zenity (2.32.1-0ubuntu1) to 3.0.0-1
   and zenity-common (3.0.0-1)
- policykit-1-gnome (0.99-1ubuntu4) to 0.101-2ubuntu2
- gconf-editor (2.32.0-0ubuntu2) to 3.0.0-0ubuntu1
   and liblaunchpad-integration-3.0-1 (0.1.51)
- avahi (0.6.30-3-ubuntu1)

---

### Post by portis on 2011-05-17
nautilus 1:3.0.1.1-0ubuntu1
gnome-disk-utility  3.0.0-1ubuntu1

---

### Post by 23dornot23d on 2011-05-17
Fully updated now re-booted and working.

---

### Post by lucazade on 2011-05-17
I still don't see all this new updates.. I got only baobab, screenshot-tool and search-tool updated to v3.
C'mon servers! :)

edit: I should have waited some other mins.. arrived!

---

### Post by terry_gardener on 2011-05-17
just updated and rebooted and it now looks horrible.

also the picture of all windows etc are staying on the screen after closing the app.

---

### Post by lucazade on 2011-05-17
> **terry_gardener said:**
> just updated and rebooted and it now looks horrible.

Gtk murrine engine has not been ported yet to gtk3.. so it is normal.

Probably we'll see a new engine (called Unico if I remember correctly) during OO dev cycle and a new Ambiance theme.

---

### Post by terry_gardener on 2011-05-17
> **lucazade said:**
> Gtk murrine engine has not been ported yet to gtk3.. so it is normal.

Probably we'll see a new engine (called Unico if I remember correctly) during OO dev cycle and a new Ambiance theme.

thanks for the info

---

### Post by MacUntu on 2011-05-17
Sounds like we'll have some high crash potential during the next few weeks. Going into selective update mode... :D

---

### Post by lucazade on 2011-05-17
> **terry_gardener said:**
> thanks for the info

To be more precise there is another issue at the moment that blocks gnome-settings-deamon to start:


```
$ gnome-settings-daemon 

** (gnome-settings-daemon:1728): WARNING **: Ignoring unknown module 'org.gnome.settings-daemon.plugins.gconf'

** (gnome-settings-daemon:1728): WARNING **: You can only run one xsettings manager at a time; exiting

** (gnome-settings-daemon:1728): WARNING **: Unable to start xsettings manager: Could not initialize xsettings manager.

** (gnome-settings-daemon:1728): WARNING **: Name taken or bus went away - shutting down
Segmentation fault
```

So also gtk2 apps atm doesn't follow theme and user settings.

This is the blueprint of the migration to Gtk3 stack: [https://blueprints.launchpad.net/ubuntu/+spec/desktop-o-gtk3-gnome3](https://blueprints.launchpad.net/ubuntu/+spec/desktop-o-gtk3-gnome3)

---

### Post by JMB74 on 2011-05-17
> **lucazade said:**
> To be more precise there is another issue at the moment that blocks gnome-settings-deamon to start:[]("https://blueprints.launchpad.net/ubuntu/+spec/desktop-o-gtk3-gnome3")

I get something different to that.

[COLOR=DarkGreen][I]jmb@ubuntu:~$ killall gnome-settings-daemon 
jmb@ubuntu:~$ gnome-settings-daemon &
[2] 19148
[1]   Segmentation fault      gnome-settings-daemon
jmb@ubuntu:~$ 
** (gnome-settings-daemon:19148): WARNING **: Ignoring unknown module 'org.gnome.settings-daemon.plugins.gconf'
jmb@ubuntu:~$ [1305644196,000,xklavier.c:xkl_engine_start_listen/]     The backend does not require manual layout management - but it is provided by the application[/I][/COLOR]

---

### Post by portis on 2011-05-17
Which version of gnome-settings-daemon are you talking about?
There's a new version 3.0.1-1ubuntu1 just uploaded.

---

### Post by JMB74 on 2011-05-17
Seems to be looking better now?

---

### Post by Harry33 on 2011-05-17
I get that terrible theme named "Simple" too, and yes it is due to the fact that gnome-settings-daemon does not start properly.

Then, I do not hear login sound nor any other event sounds any more.
That was after I upgraded gnome-desktop-settings, it pulled in libcanberra-gtk3.
Gnome-session-canberra does not work with that.

---

### Post by cecilpierce on 2011-05-17
Thats funny, I installed gNatty and it has Gnome3, Ubuntu Classic and Unity (Ubuntu) and No system sounds on all three but has sound in games and in Firefox ???

---

### Post by Framli on 2011-05-17
[https://launchpadlibrarian.net/68342600/gnome-themes-standard_3.0.0.orig.tar.gz](https://launchpadlibrarian.net/68342600/gnome-themes-standard_3.0.0.orig.tar.gz)

For those who need a decent desktop during our gtk transition, here is a link to Adwaita, the g-shell default theme. Just drag the Adwaita folder to the gnome-appareance-properties window.

---

### Post by MacUntu on 2011-05-17
I'm getting this when trying to install that theme: 

> "gnome-themes-standard-3.0.0" does not appear to be a valid theme. It may be a theme engine which you need to compile.

---

### Post by afv on 2011-05-17
Thanks Framli.

> **MacUntu said:**
> I'm getting this when trying to install that theme:

It's just the Adwaita folder, not the full .tar.gz, but I'm getting this:

"This theme will not look as intended because the required window manager theme 'Adwaita' is not installed.", even after installing gnome-themes-standard (3.0.0-2) through synaptic…

---

### Post by Framli on 2011-05-17
Yes, same message for me, but session is still getting themed.

---

### Post by MacUntu on 2011-05-17
Oh thanks, now it says "Correctly installed". *facepalm*

---

### Post by afv on 2011-05-17
> **Framli said:**
> Yes, same message for me, but session is still getting themed.

Hmm, okay then, I get something like that (my window buttons are on the right instead of being on the left side :-?).

How is your desktop? I'm getting this when everything is minimized:

---

### Post by terry_gardener on 2011-05-17
> **afv said:**
> How is your desktop? I'm getting this when everything is minimized:

yes i am getting the same thing

---

### Post by MacUntu on 2011-05-17
Ditto. Maybe because desktop drawing is disabled by default (maybe I'm mixing something up, but I remember reading something like that)?

Unfortunately there's no dconf-editor without uninstalling dconf atm. :D

---

### Post by Vrroom on 2011-05-17
> **MacUntu said:**
> Ditto. Maybe because desktop drawing is disabled by default (maybe I'm mixing something up, but I remember reading something like that)?

Unfortunately there's no dconf-editor without uninstalling dconf atm. :D

Go the same problem too. Maybe with Intel cards only?????

---

### Post by Framli on 2011-05-18
I had the same problem a few hours ago, but...

Since I have installed gnome-themes and gnome-themes-standard => my desktop is now the nice blue g-shell wallpaper. :o

---

### Post by MacUntu on 2011-05-18
> **Vrroom said:**
> Go the same problem too. Maybe with Intel cards only?????


Looks like that. I'm not getting a desktop with Intel, but it works fine with Nouveau on the same machine.

> **Framli said:**
> I had the same problem a few hours ago, but...

Since I have installed gnome-themes and gnome-themes-standard => my desktop is now the nice blue g-shell wallpaper. :o

Confirmed (but not the 'nice' part :P).

---

### Post by JMB74 on 2011-05-18
> **Framli said:**
> Since I have installed gnome-themes and gnome-themes-standard => my desktop is now the nice blue g-shell wallpaper. :o

I changed mine with:

GSETTINGS_BACKEND=dconf gsettings set org.gnome.desktop.background picture-uri "file:///usr/share/backgrounds/gnome/FootFall.png"

---

### Post by Vrroom on 2011-05-18
> **Framli said:**
> I had the same problem a few hours ago, but...

Since I have installed gnome-themes and gnome-themes-standard => my desktop is now the nice blue g-shell wallpaper. :o

I installed both the packages and my desktop is still messed up. I can select Adwaita theme from System Settings but there are rendering glitches and window trails on my desktop :(

---

### Post by afv on 2011-05-18
My desktop is now OK (without icons). Just went to dconf-editor, org/gnome/desktop/background and clicked "Set to Default" on all the options. The picture-uri changed from something like /usr/share/themes/.. to file:///usr/share/themes/Adwaita/backgrounds/stripes.jpg :)

---

### Post by Johnsie on 2011-05-18
My gnome2 panel seems to have lost its colouring/bloat/theme. It appears to run alot faster now. 'About Gnome' says that it's version 2.32.1.

I'm wondering if everything will be done in a 6 month period, because there are such massive changes going on over the next few months. Gnome3 integration and a new Unity.

---

### Post by novatillasku on 2011-05-18
My desktop is wonderful today ;-)

[IMG]http://novatillasku.com/wp-content/uploads/2011/05/Pantallazo-41.png[/IMG]

---

### Post by cecilpierce on 2011-05-18
> **novatillasku said:**
> My desktop is wonderful today ;-)

[IMG]http://novatillasku.com/wp-content/uploads/2011/05/Pantallazo-41.png[/IMG]

Yea RIGHT !!!   :(

Looks just like mine, it WILL get better, I hope :)

---

### Post by Harry33 on 2011-05-18
> **cecilpierce said:**
> Yea RIGHT !!!   :(

Looks just like mine, it WILL get better, I hope :)

It will at least change, if you install gnome-themes-standard.
I got the gnome3 default background that way.
Then again, I'm still using gnome-panel session.

---

### Post by Amaranth on 2011-05-18
You need to enable nautilus drawing the desktop again to get rid of the weird ghost drawing happening on the desktop now.```
gsettings set org.gnome.desktop.background show-desktop-icons true
```

---

### Post by Johnsie on 2011-05-19
My desktop (classic mode) is alot less glamorous:

---

### Post by JMB74 on 2011-05-19
By installing the Atolm GTK3 theme, I can get the classic desktop looking half decent. Sort of.....

[IMG]http://img846.imageshack.us/img846/5659/0519001.png[/IMG]

---

### Post by hugmenot on 2011-05-19
I upgraded by, ahem, accident. 

The best combination to get a decent looking desktop is to combine Adwaita gtk-3.0 dark variant from git with Ambiance gtk-2.0. Just get Adwaita from git, and copy Ambiance gtk-2.0 folder into Adwaita gtk-2.0 dir.

Also, they have new blue icons which look nice.

---

### Post by Bowmore on 2011-05-19
The easy way around for now is to change the theme in dconf from Adwaita to the one you prefer.

For Ambiance just change Adwaita to Ambiance with
```
gsettings set org.gnome.desktop.interface gtk-theme 'Ambiance'
```
Nautilus though and its right-click menu is depending on gtk-themes-standard settings.

---

### Post by Starks on 2011-05-19
works nicely enough

---

### Post by Hanmac on 2011-05-20
your desktop is nicely ... on mine, i have no desktop icons (its only blue stripes)
it thinks that genview is the default Folder opener (it should be nautilus)
and after i deleted it, it opens with konqueror
my progamms only in kde-bluewhite j can not change the appirance
in process i have a kded4, but on service it says that gdm is runnng and not kdm .. 
i must do something very wrong right? :(

---

### Post by Vrroom on 2011-05-20
The most close you can get to Ambiance by having this GTK3 theme --> [http://gnome-look.org/content/show.php/Adwance-gtk3?content=141925](http://gnome-look.org/content/show.php/Adwance-gtk3?content=141925)

---

### Post by Framli on 2011-05-20
[B]- Unity
- GTK3
- Ambiance[/B] 
:)

[http://imagebin.org/154232](http://imagebin.org/154232)

---

### Post by MacUntu on 2011-05-20
Heh, how did you change the theme for the controls?

Also, neither does that look like my notebook screen nor like my CRT monitor! :D

[[img]http://img.xrmb2.net/166788.jpg[/img]](http://img.xrmb2.net/images/166788.png)

---

### Post by JMB74 on 2011-05-20
> **MacUntu said:**
> Heh, how did you change the theme for the controls?

Does this work?

```
gsettings set org.gnome.desktop.interface gtk-theme 'Adwaita'
```You would need [COLOR=DarkGreen]*gnome-themes-standard*[/COLOR] installed.

I did some hackery to get the gnome-tweak-tool working, but that may be a bit excessive. It should work by default once a build of gnome shell and it's dependancies hits the repo's anyway.

---

### Post by MacUntu on 2011-05-20
Adwaita works, but not Ambiance/Radiance (like in Framli's screenshot).

---

### Post by JMB74 on 2011-05-20
Did you install this theme and try switching to that?

> **Vrroom said:**
> The most close you can get to Ambiance by having this GTK3 theme --> [http://gnome-look.org/content/show.php/Adwance-gtk3?content=141925](http://gnome-look.org/content/show.php/Adwance-gtk3?content=141925)

---

### Post by Framli on 2011-05-20
Ambiance GTK3 is a work in progress, here is a quick tutorial to test it. [http://imagebin.org/154232](http://imagebin.org/154232)
[B]The Unico theme engine, the one Oneiric is going to have by default, is not finished at all. 
It breaks some stuff, like opening panels in gnome-control-center.[/B]

* First, you need the Unico theme engine:
[https://launchpad.net/ubuntu/oneiric/+source/gtk3-engines-unico](https://launchpad.net/ubuntu/oneiric/+source/gtk3-engines-unico)
or [https://launchpad.net/unico](https://launchpad.net/unico) (you can try the trunk bzr branch, it builds without problems)

* Then you need Ambiance-gtk3 by Lucazade:
bzr branch lp:~lucazade/+junk/ambiance-gtk3
The contained gtk-3.0 dir needs to go in /usr/share/themes/Ambiance/

* You can then use dconf-editor (from the dconf-tools package) to set the theme:
org>gnome>desktop>interface>gtk-theme>"Ambiance"

---

### Post by MacUntu on 2011-05-20
Awesome, thanks! :-)

---

### Post by shuttleworthwannabe on 2011-05-20
Hi Guys, just to clarify--Ubuntu OO will have Gnome 3 with Shell in its repo, and as an alternative to Unity desktop? This is great news...or did I miss the announcement?

---

### Post by screaminj3sus on 2011-05-20
> **shuttleworthwannabe said:**
> Hi Guys, just to clarify--Ubuntu OO will have Gnome 3 with Shell in its repo, and as an alternative to Unity desktop? This is great news...or did I miss the announcement?

Most likely. It will be based on gnome 3 so having the shell installable in the repo will be rather trivial.

---

### Post by lucazade on 2011-05-21
> **Framli said:**
> Ambiance GTK3 is a work in progress, here is a quick tutorial to test it. [http://imagebin.org/154232](http://imagebin.org/154232)
[B]The Unico theme engine, the one Oneiric is going to have by default, is not finished at all. 
It breaks some stuff, like opening panels in gnome-control-center.[/B]

* First, you need the Unico theme engine:
[https://launchpad.net/ubuntu/oneiric/+source/gtk3-engines-unico](https://launchpad.net/ubuntu/oneiric/+source/gtk3-engines-unico)
or [https://launchpad.net/unico](https://launchpad.net/unico) (you can try the trunk bzr branch, it builds without problems)

* Then you need Ambiance-gtk3 by Lucazade:
bzr branch lp:~lucazade/+junk/ambiance-gtk3
The contained gtk-3.0 dir needs to go in /usr/share/themes/Ambiance/

* You can then use dconf-editor (from the dconf-tools package) to set the theme:
org>gnome>desktop>interface>gtk-theme>"Ambiance"

:) I'm wondering who is this lucazade!
I'd like to point out that theme is in a early stage of development and porting (read 2 days of work),
so I'd expect in a few time to be at least pixel-perfect with Ambiance gtk2 based and if possible better ;)

---

### Post by Hanmac on 2011-05-21
hm ok, but i found no reason why my gnome looks like kde -.-

---

### Post by dino99 on 2011-05-21
hm, dont have adwaita nor ambiance installed, only light-themes, and i get the same choices seen in #42 above, everything is working fine.

---

### Post by MacUntu on 2011-05-21
I noticed that the appmenu no longer works. Is this due to installing the Unico theme engine?

> **lucazade said:**
> :) I'm wondering who is this lucazade!
I'd like to point out that theme is in a early stage of development and porting (read 2 days of work),
so I'd expect in a few time to be at least pixel-perfect with Ambiance gtk2 based and if possible better ;)

\\:D/

Do you know if someone is working on porting Radiance as well?

---

### Post by jbicha on 2011-05-21
MacUntu, the status menus and app menu (indicators) haven't been ported to GTK 3 yet so you won't see the appmenu working with GTK3 apps. That's one example of how the Gnome 3 PPA breaks Ubuntu's look and feel. Of course, it's being worked on and it will be fixed soon.

---

### Post by MacUntu on 2011-05-21
Thanks, wasn't sure what exactly broke them as I did so many updates at once.

---

### Post by lucazade on 2011-05-21
> **MacUntu said:**
> 
Do you know if someone is working on porting Radiance as well?

No, I don't think anyone is working on it.. maybe it is better to ask to Cimi in #murrine channel, I don't know what are the plans.

---

### Post by Hanmac on 2011-05-22
i have many problems and i does not know why:

i can not change the desktop background, and there are no icons on the  desktop, and i cant even open the context menu of the deskop

other question: why cant i open the nautilus from menu? the  LocationsFolder opens gwenview and if i deinstall it it prever Konqueror  ... and this on GDM!!

---

### Post by TerminX on 2011-05-22
> **Hanmac said:**
> i have many problems and i does not know why:

i can not change the desktop background, and there are no icons on the  desktop, and i cant even open the context menu of the deskop

other question: why cant i open the nautilus from menu? the  LocationsFolder opens gwenview and if i deinstall it it prever Konqueror  ... and this on GDM!!
Install gnome-tweak-tool and enable the option for having the file manager handle the desktop.

---

### Post by Hanmac on 2011-05-22
hm it is installed buf failed to start with:
GLib-GIO-ERROR **: Settings schema 'org.gnome.shell.clock' is not installed

---

### Post by TerminX on 2011-05-22
Oh, right... I had to add that GNOME 3 PPA for Natty and use those versions of the various packages that haven't made it into Oneiric yet.  Forgot about that.

---

### Post by Hanmac on 2011-05-22
hm i get the gnome-shell from the ppa and aktivate the option
now the icons are back, but the background is not changeable

---

### Post by novatillasku on 2011-05-22
I install "Adwaita-drakefire" and try my prefer wallpaper, but icons don't work.


[IMG]http://i223.photobucket.com/albums/dd295/sku5/ONEIRIC/Pantallazo-1.png[/IMG]

---

### Post by afv on 2011-05-23
> **novatillasku said:**
> 
I install "Adwaita-drakefire" and try my prefer wallpaper, but icons don't work.


[http://i223.photobucket.com/albums/dd295/sku5/ONEIRIC/Pantallazo-1.png](http://i223.photobucket.com/albums/dd295/sku5/ONEIRIC/Pantallazo-1.png)



Try:
```

$ gsettings set org.gnome.desktop.background show-desktop-icons true

```

---

### Post by novatillasku on 2011-05-23
Thank's!

---

### Post by Hanmac on 2011-05-23
HM!! i can not change the background with the menu and appierance
but it work with gstettings ... *i am confused*
ok problem solved ... i forget to update gnome-control-center, i does not do it before, bacause it deletes a package names capplet-data .. i did not know it was part of gnome-control-center

---

### Post by afv on 2011-05-23
Was **gnome-appearance-properties** removed/deprecated?

> 
$ **gnome-appearance-properties**
The program '**gnome-appearance-properties**' is currently not installed.  You can install it by typing:
sudo apt-get install **gnome-control-center**

$ apt-cache policy **gnome-control-center**
**gnome-control-center**:
  Installed: 1:3.0.1.1-1ubuntu1


I can't find anything about it on the changelogs:

- [https://launchpad.net/ubuntu/oneiric/+source/gnome-control-center/+changelog](https://launchpad.net/ubuntu/oneiric/+source/gnome-control-center/+changelog)
- [http://packages.debian.org/changelogs/pool/main/g/gnome-control-center/gnome-control-center_3.0.1.1-1/changelog](http://packages.debian.org/changelogs/pool/main/g/gnome-control-center/gnome-control-center_3.0.1.1-1/changelog)

---

### Post by TerminX on 2011-05-23
Yeah, gnome-control-center is pretty much a single unified binary now with most of the functionality of the GNOME 2 version gone.

---

### Post by hugmenot on 2011-05-24
Gnome 3 is one bitter pill after the other.

---

### Post by CreativeReach on 2011-05-26
> **hugmenot said:**
> Gnome 3 is one bitter pill after the other.

Gnome 3.2 will be the water.

---

### Post by ronacc on 2011-05-26
to wash the bitter pill down ? or drown in ?

---

### Post by seeker5528 on 2011-05-26
> **CreativeReach said:**
> Gnome 3.2 will be the water.

Salt water? :P

Later, Seeker

---

### Post by CreativeReach on 2011-05-26
> **seeker5528 said:**
> Salt water? :P

Later, Seeker

No just to help those pills go down.

---

### Post by Harry33 on 2011-05-27
We have a lot of Gnome3 packages in Oneiric official repos now.
These are still missing:
- gdm
- gnome-media
- gnome-menus
- gnome-panel (GTK+3)
- gnome-shell

---

### Post by Harry33 on 2011-05-27
Those, who want to have gnome-panel3 now (not yet in Oneiric repos),
may go and download it from here (experimental):

[https://launchpad.net/~jbicha/+archive/ppa](https://launchpad.net/~jbicha/+archive/ppa)

Just be sure to install gnome-session-fallback too.

---

### Post by JMB74 on 2011-05-27
> **Harry33 said:**
> Those, who want to have gnome-panel3 now (not yet in Oneiric repos),
may go and download it from here (experimental):

[https://launchpad.net/~jbicha/+archive/ppa]("https://launchpad.net/%7Ejbicha/+archive/ppa")

Just be sure to install gnome-session-fallback too.

Does that work usably in the fallback or any other session?

---

### Post by Harry33 on 2011-05-27
> **JMB74 said:**
> Does that work usably in the fallback or any other session?

It works only with gnome-session-fallback.

---

### Post by TerminX on 2011-05-27
That PPA is horribly broken... you'd have much better luck just pulling it from git yourself and installing it to /usr/local.

---

### Post by JMB74 on 2011-05-27
> **TerminX said:**
> That PPA is horribly broken... you'd have much better luck just pulling it from git yourself and installing it to /usr/local.

That's the sort of thing I was concerned about.

At the moment I have the old gtk2 panel working fine with at least one session, so I don't want to lose that until there is a reliable panel to replace it.

---

### Post by Squonk07 on 2011-05-27
> **TerminX said:**
> Yeah, gnome-control-center is pretty much a single unified binary now **with most of the functionality of the GNOME 2 version gone.**

No kidding. I would hope that functionality will creep back in over time, but seeing that the Control Center in Fedora 15 pretty much resembles this "new and improved" version in OO, I'd say that such hope would be foolish.

Definitely a bitter pill, this Gnome 3.

---

### Post by Harry33 on 2011-05-27
> **TerminX said:**
> That PPA is horribly broken... you'd have much better luck just pulling it from git yourself and installing it to /usr/local.

Have you installed the package gnome-panel (3.0.0.1-2ubuntu1) into Oneiric setup with Gnome3 PPA fully integrated?
What issues did you find?

---

### Post by TerminX on 2011-05-27
Yeah, I have to admit I'd be pretty unimpressed and quite possibly even upset over GNOME 3 if I was some kind of hardcore GNOME 2 user.  The past few months I've been using AWN with the Cardapio and Dockbar X applets instead of the panel so I haven't been terribly affected by the massive changes, but that didn't stop me from noticing how the control center has been completely raped.

Considering they removed such basic options as changing the fonts and GTK theme (yes, I'm aware of gnome-tweak-tool but it's not an official part of the control center) I'm surprised they didn't go a step further obliterate the preferences that control that kind of stuff under the hood altogether. 

The fact that so many options are now hidden away from the typical end user yet still perfectly functional behind the scenes seems to indicate a disconnect between the people actually programming the stuff and the people making the UI design decisions.  If a bunch of preferences are clearly still useful enough to maintain all of the supporting code, why aren't they important enough to present to the end user anymore?


> **Harry33 said:**
> Have you installed the package gnome-panel (3.0.0.1-2ubuntu1) into Oneiric setup with Gnome3 PPA fully integrated?
What issues did you find?
The panel segfaulted like mad for me.  No such issues when I pulled it from git and built it myself.

---

### Post by Quadunit404 on 2011-05-27
I got Ubuntu looking normal through the Adwance theme. Unity seems to be as theme-able as the version in Natty (as in, the window buttons don't change to reflect your current theme) but I'm expecting that to change later on, as the shift to G3 shouldn't be as big as the Compiz rewrite.

---

### Post by Harry33 on 2011-05-28
> **TerminX said:**
> 
The panel segfaulted like mad for me.  No such issues when I pulled it from git and built it myself.

Right, that means I am going to wait until the Gnome-panel3 finds its way into Oneiric repos.
Thanks.

---

### Post by Starks on 2011-06-12
lucazade, any chance at an Ambiance for the GNOME-Shell?

I'd like to be able to use Unity and GNOME-Shell on the same machine without having to switch my themes (gtk, window manager, etc) each time I switch my DE.

---

### Post by lucazade on 2011-06-13
> **Starks said:**
> lucazade, any chance at an Ambiance for the GNOME-Shell?

I'd like to be able to use Unity and GNOME-Shell on the same machine without having to switch my themes (gtk, window manager, etc) each time I switch my DE.

Starks don't know at the moment..
Unfortunately gnome-shell doesn't start here in virtualbox (haven't investigated too much about this so maybe my fault) so had no chanche to try it on OO.

In the meanwhile this theme for the shell could be good:
[http://half-left.deviantart.com/art/GNOME-Shell-Ubuntu-Ambience-210264151](http://half-left.deviantart.com/art/GNOME-Shell-Ubuntu-Ambience-210264151)
give it a try

---

### Post by wgarcia on 2011-06-13
Starks: Ubuntu Ambiance Gnome Shell theme:

[http://www.webupd8.org/2011/05/ubuntu-ambiance-gnome-shell-theme.html](http://www.webupd8.org/2011/05/ubuntu-ambiance-gnome-shell-theme.html)

---

### Post by Starks on 2011-06-13
i have that. doesn't really cooperate well with everything else even if i set everything to ambiance.

there's no ambiance window manager theme aside from adwance.

---

### Post by IanW on 2011-06-13
> **lucazade said:**
> Starks don't know at the moment..
Unfortunately gnome-shell doesn't start here in virtualbox (haven't investigated too much about this so maybe my fault) so had no chanche to try it on OO.

In the meanwhile this theme for the shell could be good:
[http://half-left.deviantart.com/art/GNOME-Shell-Ubuntu-Ambience-210264151](http://half-left.deviantart.com/art/GNOME-Shell-Ubuntu-Ambience-210264151)
give it a try

VirtualBox needs to be at version 4.0.8 _with Guest Additions installed_ to run GS.

---

### Post by lucazade on 2011-06-13
> **IanW said:**
> VirtualBox needs to be at version 4.0.8 _with Guest Additions installed_ to run GS.

i'm using both additions 4.0.8 and 3d enabled but i'm stuck with a blank gnome-shell session. :/

---

### Post by Quadunit404 on 2011-06-13
Maybe GS hates your VirtualBox. Under Fedora 15 I could only get the GNOME "Classic" session (with only one panel) even after installing the guest additions and enabling 3D acceleration (no, forced fallback mode wasn't on,) but under Oneiric it works just fine :|

---

### Post by lucazade on 2011-06-13
> **Quadunit404 said:**
> Maybe GS hates your VirtualBox
Aahah.. yes, it probably hates my vbox..
anyway not a great issue, i'm not in a hurry to try it :)

---

### Post by screaminj3sus on 2011-06-14
> **TerminX said:**
> Yeah, I have to admit I'd be pretty unimpressed and quite possibly even upset over GNOME 3 if I was some kind of hardcore GNOME 2 user.  The past few months I've been using AWN with the Cardapio and Dockbar X applets instead of the panel so I haven't been terribly affected by the massive changes, but that didn't stop me from noticing how the control center has been completely raped.

Considering they removed such basic options as changing the fonts and GTK theme (yes, I'm aware of gnome-tweak-tool but it's not an official part of the control center) I'm surprised they didn't go a step further obliterate the preferences that control that kind of stuff under the hood altogether. 

The fact that so many options are now hidden away from the typical end user yet still perfectly functional behind the scenes seems to indicate a disconnect between the people actually programming the stuff and the people making the UI design decisions.  If a bunch of preferences are clearly still useful enough to maintain all of the supporting code, why aren't they important enough to present to the end user anymore?



The panel segfaulted like mad for me.  No such issues when I pulled it from git and built it myself.

Gnome tweak isn't an "official part of the control center" but it is an officially maintained program. I expect we'll start to see most gnome 3 distros include it by default. Perhaps they should have kept the font settings in the control center, but I have no problem with them moving advanced settings to the tweak tool. Its just as easy for me to change fonts and such as it was before.

---

