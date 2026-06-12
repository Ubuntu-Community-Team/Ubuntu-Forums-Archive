---
title: "Missing icons in gnome-shell applications screen"
date: 2011-07-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Quackers on 2011-07-12
I have just got OO back up and running and am using gnome-shell.
I have the gnome3team ppa and ricotz testing ppa eneabled.
Everything is fine except that lots of icons are missing from the Applications screen.
For instance I have no icon for synaptic package manager.
None for gparted - even though it is installed.

I have only 45 icons in the Applications screen and I remember having many more than this previously :confused:
I've looked at what is installed (Gnome packages) and nothing appears to be missing that I know should be there.
Any ideas people?
Thanks.

---

### Post by jfernyhough on 2011-07-12
This sounds similar to when I clean installed OO with GNOME3 and I had no applications at all. This was down to the session not being set to GNOME by lightdm so it was looking at the wrong applications list.

In **/etc/xdg/menus** there are several menu files. I reckon you will have one called **gnome-applications.menu**. Try symlinking this to applications.menu :

$ sudo ln -s /etc/xdg/menus/gnome-applications.menu /etc/xdg/menus/applications.menu

I think the reason why you have some applications but not all is due to having an applications-merged.menu. I'm not sure what created or uses this one.

---

### Post by Quackers on 2011-07-12
Thanks jfernyhough, I do indeed have a gnome-applications.menu and I tried what you suggest. The output was this
```
ocelot2@ocelot2-VGN-AR51SU:~$ sudo ln -s /etc/xdg/menus/gnome-applications.menu /etc/xdg/menus/applications.menu
ln: creating symbolic link `/etc/xdg/menus/applications.menu': File exists

``` Not sure whether that's good or bad :-)
I'll log out/in and see what happens.

Nothing, same as it was. Not surprising I suspect with the output :-)

---

### Post by Harry33 on 2011-07-12
> **Quackers said:**
> Thanks jfernyhough, I do indeed have a gnome-applications.menu and I tried what you suggest. The output was this
```
ocelot2@ocelot2-VGN-AR51SU:~$ sudo ln -s /etc/xdg/menus/gnome-applications.menu /etc/xdg/menus/applications.menu
ln: creating symbolic link `/etc/xdg/menus/applications.menu': File exists

``` Not sure whether that's good or bad :-)
I'll log out/in and see what happens.

Nothing, same as it was. Not surprising I suspect with the output :-)

Do you have gnome-icon-theme, gnome-icon-theme-full and gnome-icon-theme-symbolic installed?

---

### Post by Quackers on 2011-07-12
Yes sir :-)

---

### Post by Harry33 on 2011-07-12
> **Quackers said:**
> Yes sir :-)

Well OK.
I am also using Ricotz testing PPA (but not Gnome3 PPA).
What packages have you installed from Gnome3 PPA?
And do you use Natty or Oneiric part of Gnome3?

---

### Post by Quackers on 2011-07-12
As far as I'm aware nothing has come through from either Gnome3team or ricotz since I enabled them :-( (and I have apt-get updated the system :-) )
What's the difference between Natty and Oneiric Gnome3 and how do I tell which I'm using please?

---

### Post by mc4man on 2011-07-12
I've seen that the whole time - no exactly sure of the root cause but - 
If you were to open synaptic.desktop up in an editor you'll see this line
Categories=PackageManager;GTK;System;Settings;
Remove the Settings; and it will show.
Categories=PackageManager;GTK;System;

Another one is update manager, same thing - orig line
Categories=System;Settings;
Edited to this will allow it to show
Categories=System;

ect. ect.

Edit - once done they will show in the system sub menu - maybe gs only looks at last entry and there is no Settings category?, - easy to test,
(tried - it doesn't like Settings in the category line whatsoever

---

### Post by Quackers on 2011-07-12
Thanks mc4man I'll delve around. It doesn't explain things like gparted not appearing though. All these have appeared in previous OO/gnome-shell installations. Strange.

---

### Post by mc4man on 2011-07-12
> **Quackers said:**
> It doesn't explain things like gparted not appearing though. All these have appeared in previous OO/gnome-shell installations. Strange.
Well at least here this has been the case for some time - as far as parted same thing orig - 
Categories=GNOME;System;Filesystem;[COLOR="Red"]Settings;
[/COLOR]

---

### Post by Quackers on 2011-07-12
synaptic.desktop is an empty file it seems :-(

---

### Post by mc4man on 2011-07-12
> **Quackers said:**
> synaptic.desktop is an empty file it seems :-(
Are you sure?

```
gksudo gedit /usr/share/applications/synaptic.desktop
```

========================================================================
```
[Desktop Entry]
Name=Synaptic Package Manager
GenericName=Package Manager
Comment=Install, remove and upgrade software packages
Exec=gksu --description /usr/share/applications/synaptic.desktop /usr/sbin/synaptic
Icon=synaptic
Terminal=false
Type=Application
Categories=PackageManager;GTK;System;
NotShowIn=KDE;
X-Ubuntu-Gettext-Domain=synaptic
```

---

### Post by Quackers on 2011-07-12
Sorry, but this brings up another question.
Whenever I open a file in a text editor I get a second window (like in the screenshot - which I must have clicked on before it fully opened - entitled "untitled document" and has a spinning cursor thing.
Do you get that?
I've got the settings you describe :-)

---

### Post by Harry33 on 2011-07-12
> **Quackers said:**
> As far as I'm aware nothing has come through from either Gnome3team or ricotz since I enabled them :-( (and I have apt-get updated the system :-) )
What's the difference between Natty and Oneiric Gnome3 and how do I tell which I'm using please?

Go to this page (Natty), and you will see 127 packages:
[https://launchpad.net/~gnome3-team/+archive/gnome3/+packages?field.name_filter=&field.status_filter=published&field.series_filter=natty](https://launchpad.net/~gnome3-team/+archive/gnome3/+packages?field.name_filter=&field.status_filter=published&field.series_filter=natty)

Then go to this page (Oneiric), and you will see only 1 package:
[https://launchpad.net/~gnome3-team/+archive/gnome3/+packages?field.name_filter=&field.status_filter=published&field.series_filter=oneiric](https://launchpad.net/~gnome3-team/+archive/gnome3/+packages?field.name_filter=&field.status_filter=published&field.series_filter=oneiric)

See from /etc/apt/sources.list which one you have enabled.

---

### Post by Quackers on 2011-07-12
> **Harry33 said:**
> Go to this page (Natty), and you will see 127 packages:
[https://launchpad.net/~gnome3-team/+archive/gnome3/+packages?field.name_filter=&field.status_filter=published&field.series_filter=natty](https://launchpad.net/~gnome3-team/+archive/gnome3/+packages?field.name_filter=&field.status_filter=published&field.series_filter=natty)

Then go to this page (Oneiric), and you will see only 1 package:
[https://launchpad.net/~gnome3-team/+archive/gnome3/+packages?field.name_filter=&field.status_filter=published&field.series_filter=oneiric](https://launchpad.net/~gnome3-team/+archive/gnome3/+packages?field.name_filter=&field.status_filter=published&field.series_filter=oneiric)

See from /etc/apt/sources.list which one you have enabled.

I'm using Oneiric - maybe I should change to Natty :-)

---

### Post by mc4man on 2011-07-12
> Do you get that?
That's a known bug - a root gedit will also open (or attempt to open in unity) an 'untitled document'
[https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/796076](https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/796076)

A little fooling around - 
while the presence of Settings plays a part, at least here when logging out and then back in the .desktops tend to disappear again. The only sure way to kept them (again on this install) is to copy to ~/.local/share/applications/ and not have "Settings" on the line

(I may try a new install on a different machine - this one I'm on can only use O as an upgrade from 11.04 and the 2.6.38-X kernel - the 3.X kernel has a 100% fails to boot with the very nice message of " Bug: kernel not usable"

---

### Post by Quackers on 2011-07-12
Ok thanks again mc4man :-)

---

### Post by Harry33 on 2011-07-12
Hmm, I just noticed that in my 32-bit Oneiric setup the synaptic and gnome-tweak-tool icons were missing. In my 64-bit setups I do not have this bug.

I modified the .desktop files according to Mc4man instructions copying them to .local/share/applications and icons are now visible.

Thanks Mc4man.

---

### Post by Quackers on 2011-07-12
I changed oneiric gnome3team.ppa to natty and installed several packages, but the Applications menu is still the same :-)
I'll do some gediting then :-) and see what occurs!

---

### Post by mc4man on 2011-07-12
> copying them to .local/share/applications 
I don't quite get yet  why .desktops in /usr/.. can get 'lost' and those in ~/.. won't, also the 64 vs. 32 bit diff. is interesting.
Maybe this goes back to the initial issues with xdg/menus,  - 
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/798951](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/798951)

Anyway - couldn't find this reported so filed to see what transpires
[https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/809430](https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/809430)

---

### Post by Quackers on 2011-07-12
Workaround going well, thanks again mc4man. How do you know this stuff? :-)
Although it's a workaround as opposed to a fix I'll mark the thread as solved.

I've me too'd the bug.

---

### Post by mc4man on 2011-07-12
Just a bit of logical trial & error - in this case if one used alacarte to create a .desktop (launcher) for synaptic it would work.
The most obvious diff. between alacarte-made .desktops and the orig. is the lack of a Categories= line, then just T&E, ect.

---

### Post by mc4man on 2011-07-13
As a bit of comparison - on a new install, A2 updated (no ubuntu gs/panel available or ever installed), then the ppa gs - everything shows up fine, no need to edit .desktops ect.
(other than providing a /etc/xdg/menus/applications.menu

Just points to the relatively messy state atm..

---

### Post by Quackers on 2011-07-13
Indeed it does :-)

---

