---
title: "Gnome-Shell (Oneiric) not working"
date: 2011-09-12
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by bdr529 on 2011-09-12
I upgraded to Oneiric a few days ago and unity works (after todays updates) fine, so far.

But if i start Oneiric with Gnome (package gnome-shell is instaled), i only see a nautilus menu:

[IMG]http://ubuntuone.com/41aUzkgyb7he23njgaWVGl[/IMG]

I can't see or activate anything of the shell.
Any idea why?

Michael

Edit: I tried it with and without ricotz/testing-ppa. The same result. I also installed gir1.2-accountsservice-1.0.

---

### Post by cmccauley on 2011-09-12
Gnome-shell was working fine for me until late last week. Now when I start it I get errors like this ..

JS ERROR: !!!     message = '"Requiring AccountsService, version none: Typelib file for namespace 'AccountsService' (any version) not found"'
Window manager warning: Log level 32: Execution of main.js threw exception: Error: Requiring AccountsService, version none: Typelib file for namespace 'AccountsService' (any version) not found



... and it crashes anyone know how to workaround it?

Thanks

Chris

---

### Post by awam66 on 2011-09-12
It is working fine here for me 64bit. Really looking good!
Sorry not much help!

---

### Post by bdr529 on 2011-09-12
> **cmccauley said:**
> Gnome-shell was working fine for me until late last week. Now when I start it I get errors like this ..

JS ERROR: !!!     message = '"Requiring AccountsService, version none: Typelib file for namespace 'AccountsService' (any version) not found"'
Window manager warning: Log level 32: Execution of main.js threw exception: Error: Requiring AccountsService, version none: Typelib file for namespace 'AccountsService' (any version) not found



... and it crashes anyone know how to workaround it?

Thanks

Chris

Did you install gir1.2-accountsservice-1.0?
I read, that some dependencies didn't work. 

Try this:

```
sudo apt-get install gir1.2-accountsservice-1.0

```

---

### Post by umbertoz on 2011-09-12
Sometime it could happen. You should restart gdm from console and log in again.

Rgds,

---

### Post by cmccauley on 2011-09-12
THANKS!

You were correct, the accounts service wasn't installed - I just assumed that it was part of the big update last week. Manually installing and running gnome-shell worked.

Thanks again,

Chris



> **bdr529 said:**
> Did you install gir1.2-accountsservice-1.0?
I read, that some dependencies didn't work. 

Try this:

```
sudo apt-get install gir1.2-accountsservice-1.0

```

---

### Post by bdr529 on 2011-09-13
After the latest upgrades my gnome-shell is still not working.

Any idea, what i can do?

---

### Post by rvchari on 2011-09-13
sorry to jump into this thread...
but my case is somewhat relevant..
i ve installed gnome shell successfully and it was functioning fine with the default adwaita theme. when i changed the theme (by old method of transfering the theme to /usr/share/gnome-shell and hitting Alt+F2 then r, i could change the theme... but then in the background of the top panel i see the nautilus menu... from where did that pop up ? any idea to make that go ?

---

### Post by tista on 2011-09-13
> **rvchari said:**
> sorry to jump into this thread...
but my case is somewhat relevant..
i ve installed gnome shell successfully and it was functioning fine with the default adwaita theme. when i changed the theme (by old method of transfering the theme to /usr/share/gnome-shell and hitting Alt+F2 then r, i could change the theme... but then in the background of the top panel i see the nautilus menu... from where did that pop up ? any idea to make that go ?

Hi rvchari. ;)

yeah that's the fact we've experienced ugly situation... :sad:
I suppose it caused Ubuntu_menuproxy patched gtk+-3.0 packages... yep, the ubuntu devs working for "Only Unity"!! XS that patch makes unity's global menu easy to handle, but on any other desktops, it only means the EVIL!! since I hate global menu. I had reverted gtk+-3.0 to dispatched version...

cheers.

---

### Post by ricotz on 2011-09-13
> **tista said:**
> I suppose it caused Ubuntu_menuproxy patched gtk+-3.0 packages... yep, the ubuntu devs working for &quot;Only Unity&quot;!! XS that patch makes unity's global menu easy to handle, but on any other desktops, it only means the EVIL!! since I hate global menu. I had reverted gtk+-3.0 to dispatched version... cheers.

Removing all *appmenu* packages should workaround this issue instead of having a unpatched gtk3.

---

### Post by bdr529 on 2011-09-13
> **tista said:**
> Hi rvchari. ;)
.. I had reverted gtk+-3.0 to dispatched version...

cheers.

How did you do that? I wonder, if this could solve my problem. 
I don't like global menu too, so this would be ok for me.

---

### Post by tista on 2011-09-13
> **ricotz said:**
> Removing all *appmenu* packages should workaround this issue instead of having a unpatched gtk3.

Hi ricotz.

If I remembered well, that removing didn't make any success... :sad:
actually from "3.1.10-0ubuntu3", I've experienced that issue. So I love 3.1.10-0ubuntu1's menuproxy!
since it didn't get my way to use gs and unity's global-menu as well.

or although we could stop that issue to disable nautilus's desktop handling via gnome-tweak-tool, it might be not cool...

regards.

---

### Post by lucazade on 2011-09-13
> **tista said:**
> Hi ricotz.

If I remembered well, that removing didn't make any success... :sad:
actually from "3.1.10-0ubuntu3", I've experienced that issue. So I love 3.1.10-0ubuntu1's menuproxy!
since it didn't get my way to use gs and unity's global-menu as well.

or although we could stop that issue to disable nautilus's desktop handling via gnome-tweak-tool, it might be not cool...

regards.

hey Tista
have you tried to see this scripts at session startup?

(from .xsession-errors)
Loading X session script /etc/X11/Xsession.d/80appmenu
Loading X session script /etc/X11/Xsession.d/80appmenu-gtk3

maybe disabling could help.. otherwise disabling nautilus to paint wallpaper from dconf

---

### Post by tista on 2011-09-13
> **lucazade said:**
> hey Tista
have you tried to see this scripts at session startup?

(from .xsession-errors)
Loading X session script /etc/X11/Xsession.d/80appmenu
Loading X session script /etc/X11/Xsession.d/80appmenu-gtk3

maybe disabling could help.. otherwise disabling nautilus to paint wallpaper from dconf

Hi Luca!! ;)

OK... I would see that scripts and re-revert to current gtk+-3.0...

Thanks!!

**EDIT**
Wow!! it could help! :P
Ohhh... I wonder why in Past I couldn't make any success... :sad: so sorry, you guys were correct.

---

### Post by tista on 2011-09-13
> **bdr529 said:**
> How did you do that? I wonder, if this could solve my problem. 
I don't like global menu too, so this would be ok for me.

Hi bdr529,

Yeah you may uninstall all of *appmenu stuff to kill the global menu... ;)
and then, if you still stack with ugly gs, please check the mutter version! because both gnome-shell and mutter depends in the deep of developments each other. it must be the same version.

cheers.

---

### Post by bdr529 on 2011-09-13
> **tista said:**
> Hi bdr529,

Yeah you may uninstall all of *appmenu stuff to kill the global menu... ;)
and then, if you still stack with ugly gs, please check the mutter version! because both gnome-shell and mutter depends in the deep of developments each other. it must be the same version.

cheers.

Hi tista,

i purged appmenu* an the global-menu is gone. Gnome-Shell still doesn't show up. I disabled ricotz-ppa to get the same versions for gs and mutter:

mutter_3.1.90.1
gnome-shell_3.1.90.1

The problem persists :-( Any other idea?

Michael

---

### Post by tista on 2011-09-13
> **bdr529 said:**
> Hi tista,

i purged appmenu* an the global-menu is gone. Gnome-Shell still doesn't show up. I disabled ricotz-ppa to get the same versions for gs and mutter:

mutter_3.1.90.1
gnome-shell_3.1.90.1

The problem persists :-( Any other idea?

Michael

OK... umm... so let's track the issue down.
once you login into gs, and then could you go back to VT console?
if could, please see your .xsession-errors? and hopefully paste yours on:
[http://paste.ubuntu.com/]("http://paste.ubuntu.com/")
then let us know the link. OK?

cheers.

tista

---

### Post by jbicha on 2011-09-13
> **bdr529 said:**
> Hi tista,

i purged appmenu* an the global-menu is gone. Gnome-Shell still doesn't show up. I disabled ricotz-ppa to get the same versions for gs and mutter:

mutter_3.1.90.1
gnome-shell_3.1.90.1

The problem persists :-( Any other idea?

Michael

Right, the appmenu doesn't have anything to do with GNOME Shell not starting. It just peeks through if Shell (or Unity) crashes. Appmenu has some subtle effects on gnome-terminal and such but it generally doesn't break the system.

---

### Post by rvchari on 2011-09-13
> **tista said:**
> Hi rvchari. ;)

yeah that's the fact we've experienced ugly situation... :sad:
I suppose it caused Ubuntu_menuproxy patched gtk+-3.0 packages... yep, the ubuntu devs working for "Only Unity"!! XS that patch makes unity's global menu easy to handle, but on any other desktops, it only means the EVIL!! since I hate global menu. I had reverted gtk+-3.0 to dispatched version...

cheers.

hi tista...
how to revert to dispatched version of gtk3 ? if i do that will things be stable ? today i face a new problem... the gnome shell that i reverted back to default adwaita theme... now Alt+F2 doesnt fire up the window !!!

if reverting back to dispatched version will help get back the shell in one piece ? i am unable to install extensions too ! just the shell without extensions is not handy !!!

---

### Post by tista on 2011-09-13
> **rvchari said:**
> hi tista...
how to revert to dispatched version of gtk3 ? if i do that will things be stable ? today i face a new problem... the gnome shell that i reverted back to default adwaita theme... now Alt+F2 doesnt fire up the window !!!

if reverting back to dispatched version will help get back the shell in one piece ? i am unable to install extensions too ! just the shell without extensions is not handy !!!

@rvchari ;)

If you already purged global menu stuff completely, you didn't have to revert libgtk3 to dispatched version! :P yeah its purpose leads 2 goals:
1. dispatched libgtk3 (especially version 3.1.10-0ubuntu1) works well on both gnome-shell and unity while keeping global menu alive... 
2. And that version had never avoided "show/hide menubar" option on individual apps setting like gnome-terminal, marlin and so... So I loved it. Since I'm addicted elementary apps, that apps has the useful option "hide menubar"!! ;) if luna had been released, I would move to elementary and say good-bye to Ubuntu.

Next, "run dialog" via Alt+F2 on gnome-shell, yep, it caused "pygobject" and "gobject-introspection" package. ricotz had both latest packages on his PPA, then we could use and fix it by upgrading such packages... 

Finally if you didn't have any harsh issues on gtk3's gtkmenubar, don't revert libgtk3!

regards.

---

### Post by bdr529 on 2011-09-14
> **tista said:**
> OK... umm... so let's track the issue down.
once you login into gs, and then could you go back to VT console?
if could, please see your .xsession-errors? and hopefully paste yours on:
[http://paste.ubuntu.com/]("http://paste.ubuntu.com/")
then let us know the link. OK?

cheers.

tista

Hi tista,

I cant start a terminal or use ALT-F2, but i could start nautilus with right-click on the desktop, so i saved my .xsession-errors.

.xsession-errors:
[http://paste.ubuntu.com/688901/]("http://paste.ubuntu.com/688901/")

Hope this is useful, cause some errors are in german, sorry!

Michael

---

### Post by tista on 2011-09-14
> **bdr529 said:**
> Hi tista,

I cant start a terminal or use ALT-F2, but i could start nautilus with right-click on the desktop, so i saved my .xsession-errors.

.xsession-errors:
[http://paste.ubuntu.com/688901/]("http://paste.ubuntu.com/688901/")

Hope this is useful, cause some errors are in german, sorry!

Michael

Hi Michael,

I'm afraid that why compiz initializer goes through the gnome3 session...? :confused:
so let me see your 2 files:
* /usr/share/gnome-session/sessions/gnome.session
* /usr/share/xsessions/gnome.desktop

Then if you login into gnome-fallback session, try to run "gnome-shell --replace" on gnome-terminal... if gs had been installed successfully, gs would come up...

cheers.

**EDIT**
```
gnome-session[2755]: WARNING: App 'gnome-shell.desktop' respawning too quickly
gnome-session[2755]: CRITICAL: We failed, but the fail whale is dead. Sorry....
```

as far as I know that gnome-sell.desktop file seems to be included too old package of "gnome-session"... anybody remembered that?

---

### Post by bdr529 on 2011-09-14
> **tista said:**
> Hi Michael,

I'm afraid that why compiz initializer goes through the gnome3 session...? :confused:
so let me see your 2 files:
* /usr/share/gnome-session/sessions/gnome.session
* /usr/share/xsessions/gnome.desktop

Then if you login into gnome-fallback session, try to run "gnome-shell --replace" on gnome-terminal... if gs had been installed successfully, gs would come up...



Hi tista,

i started ubuntu with Gnome-Classic and started "gnome-shell --replace":

[Terminal-Output]("http://paste.ubuntu.com/688980/")

The Shell started and seems to work fine! :D
(Except for ugly window-frames: [Screenshot]("http://ubuntuone.com/4lTuPrZ62dBea1ukp30rgJ")

But how can i start the gs directly? I tried it again from ligthdm with Gnome and it failed again.

My gnome.session: [Link]("http://paste.ubuntu.com/688978/")

I could not find /usr/share/xsessions/gnome.desktop

Michael

---

### Post by tista on 2011-09-14
> **bdr529 said:**
> Hi tista,

i started ubuntu with Gnome-Classic and started "gnome-shell --replace":

[Terminal-Output]("http://paste.ubuntu.com/688980/")

The Shell started and seems to work fine! :D
(Except for ugly window-frames: [Screenshot]("http://ubuntuone.com/4lTuPrZ62dBea1ukp30rgJ")

But how can i start the gs directly? I tried it again from ligthdm with Gnome and it failed again.

My gnome.session: [Link]("http://paste.ubuntu.com/688978/")

I could not find /usr/share/xsessions/gnome.desktop

Michael

Ahh... Stepping forward!! :P

So it means gs had been installed successfully. and the evil was the gnome-session environments.
well... try to run "sudo apt-get update && sudo apt-get install --reinstall gnome-session", and then check your /usr/share/xsessions/gnome.desktop out again...

cheers.

---

### Post by bdr529 on 2011-09-14
> **tista said:**
> Ahh... Stepping forward!! :P

So it means gs had been installed successfully. and the evil was the gnome-session environments.
well... try to run "sudo apt-get update && sudo apt-get install --reinstall gnome-session", and then check your /usr/share/xsessions/gnome.desktop out again...

cheers.

Hi tista,

i reinstalled gnome-session. I think i made a mistake, the gnome.desktop-file was there before, i think. It looks like this:

```
[Desktop Entry]
Name=Ubuntu
Comment=This session logs you into Ubuntu
Exec=gnome-session --session=ubuntu
TryExec=gnome-session
Icon=
Type=Application
Hidden=true
X-Ubuntu-Gettext-Domain=gnome-session-3.0
```

Edit: I still can't start gs from lightdm..

---

### Post by tista on 2011-09-14
> **bdr529 said:**
> Hi tista,

i reinstalled gnome-session. I think i made a mistake, the gnome.desktop-file was there before, i think. It looks like this:

```
[Desktop Entry]
Name=Ubuntu
Comment=This session logs you into Ubuntu
Exec=gnome-session --session=ubuntu
TryExec=gnome-session
Icon=
Type=Application
Hidden=true
X-Ubuntu-Gettext-Domain=gnome-session-3.0
```

Edit: I still can't start gs from lightdm..

@Michael

OK... Unity session seems to be OK. and then gnome-shell.desktop is how? mine is here:
```
[Desktop Entry]
Name=GNOME
Comment=This session logs you into GNOME
Exec=gnome-session --session=gnome
TryExec=gnome-shell
Icon=
Type=Application
X-Ubuntu-Gettext-Domain=gnome-session-3.0
```

please compare yours with mine! ;)

ciao.

---

### Post by bdr529 on 2011-09-14
Hi tista,

ok i posted gnome.desktop. My gnome-shell.desktop is equal to yours.

Michael

---

### Post by tista on 2011-09-14
> **bdr529 said:**
> Hi tista,

ok i posted gnome.desktop. My gnome-shell.desktop is equal to yours.

Michael

@Michael

OK... umm... if so, gs should come up via lightdm and/or gdm...:(
but your log said exactly compiz came up:
```
Backend     : gconf
Integration : true
Profile     : default
Adding plugins
Initializing core options...done
```
and soon gs had wiped out from your session:
```
gnome-session[2755]: WARNING: App 'gnome-shell.desktop' respawning too quickly
```

so haven't any clue now, then could you check the "auto-start apps" out? if we could trace the point where compiz came from, maybe we could solve (kill compiz)...

Best Regards.

tista

---

### Post by bdr529 on 2011-09-14
Hi tista,

maybe this has something to do with it:

If i start nautilus in /usr/share/xsessions, nautilus stops with this errors:

```
root@michael-laptop:/home/michael# cd /usr/share/xsessions
root@michael-laptop:/usr/share/xsessions# dir
gnome-classic.desktop  gnome-fallback.desktop  kde-plasma.desktop
gnome.desktop	       gnome-shell.desktop     ubuntu-2d.desktop
gnome.desktop~	       gnome-shell.desktop~    ubuntu.desktop
root@michael-laptop:/usr/share/xsessions# nautilus
** (nautilus:13284): DEBUG: Syncdaemon not running, waiting for it to start in NameOwnerChanged
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: »net usershare« gab den Fehler 255 zurück: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error Datei oder Verzeichnis nicht gefunden
Please ask your system administrator to enable user sharing.
```

---

### Post by ronacc on 2011-09-14
I am having the same problem (or was ) . I had set for automatic login and was ending up as in post #1 with just the global menu and a useless de ( couldn't do anything ) I found that if I alt>sysreq>k to kill the x-session I would go to the login screen and login then gnome-shell would start normally and fully functional . This did not persist through a reboot so I switched off auto login and can boot normally . Hope this helps .  I noticed that there is no option for a timed login with system settings>user accounts which is how I had enabled auto login perhaps this has something to do with it .

---

### Post by bdr529 on 2011-09-14
> **tista said:**
> @Michael

...so haven't any clue now, then could you check the "auto-start apps" out? if we could trace the point where compiz came from, maybe we could solve (kill compiz)...

Best Regards.

tista

Hi tista,

you were right! :P 

There was compiz in the auto-start apps (i don't know why). I deactivate it and it works! 

Thank you very much!

The only problem now ist, that my window frames look ugly (Shell and Themes are looking good). Anyway, i set this thread to solved!

Best regards 
Michael

---

### Post by tista on 2011-09-14
> **bdr529 said:**
> Hi tista,

you were right! :P 

There was compiz in the auto-start apps (i don't know why). I deactivate it and it works! 

Thank you very much!

The only problem now ist, that my window frames look ugly (Shell and Themes are looking good). Anyway, i set this thread to solved!

Best regards 
Michael

Hi Michael. ;)

Wow you did it!!

and ugly window frames might be changed via gnome-tweak-tool, you had some themes for mutter, so try one of them. if you didn't have unico gtk3 engine, run "sudo apt-get install gtk3-engines-unico". today we almost would be addicted to unico engined theming...

cheers.

---

### Post by bdr529 on 2011-09-14
Hi tista,

i had to use gconfig-tool to change the theme; now it works _and_ looks good.

Thanks to all!
Michael

---

### Post by Menti on 2011-09-14
Hello everyone. I had exactly the same problem as explained in the opening post, except that I could fire a terminal (I had AWN on autostart) and gnome-shell --replace would work. Even the ugly titlebars are there.

BUT I don't have Compiz on autostart!

I checked the gnome-shell.desktop and it is exactly the same as yours.

Any idea at all? Thanks.

---

### Post by ronacc on 2011-09-14
are you set for auto login ? if so see my post on the previous page ( last one )

---

### Post by Menti on 2011-09-14
> **ronacc said:**
> are you set for auto login ? if so see my post on the previous page ( last one )

If auto login means not selecting a user and entering password: no, I'm on manual login.

---

### Post by ronacc on 2011-09-14
yes that is what it means . so if you are on manual login the problem that I had is not the same as yours .

---

### Post by screaminj3sus on 2011-09-14
It works for me, but the shell randomly restarts, a lot. So I'm using unity for now.

---

### Post by tista on 2011-09-14
> **screaminj3sus said:**
> It works for me, but the shell randomly restarts, a lot. So I'm using unity for now.

Hi screaminj3sus,

Ohh god... :sad:
if you saw any crash on gs, then login into other session, please let me see your .xsession-errors.old hopefully...

and when you experienced that crashes, you had been forced to go back to lightdm? or system frozen?

cheers

---

### Post by screaminj3sus on 2011-09-15
> **tista said:**
> Hi screaminj3sus,

Ohh god... :sad:
if you saw any crash on gs, then login into other session, please let me see your .xsession-errors.old hopefully...

and when you experienced that crashes, you had been forced to go back to lightdm? or system frozen?

cheers

For me gnome-shell would just randomly restart and come back. It seems to have randomly stopped doing it now though.

---

### Post by tista on 2011-09-15
> **screaminj3sus said:**
> For me gnome-shell would just randomly restart and come back. It seems to have randomly stopped doing it now though.

OK... so what was LookingGlass saying ? any logs?

cheers.

---

