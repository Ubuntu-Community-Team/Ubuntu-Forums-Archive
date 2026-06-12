---
title: "GNOME Shell 3.1.90 Released &amp; Mutter 3.1.90"
date: 2011-08-29
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by dext on 2011-08-29
>  While there are many substantial features in this release, it's
particular worth pointing out the changes contributed by our
Summer of Code Students: Nohemi Fernandez's onscreen keyboard,
Morten Mjelva's contact search, and Neha Doijode's work on
getting cover art and other images to display in notifications.
       [More About GS3.1.90+ Here]("http://mail.gnome.org/archives/gnome-announce-list/2011-August/msg00038.html")

> There's several long-requested features in this release:
larger draggable borders on windows, antialiasing on rounded window
corners, and unredirection of full-screen 3D games for maximum
performance. Thanks to Jasper and Adel for this work!    

[More About Mutter 3.1.90+ Here]("http://mail.gnome.org/archives/gnome-announce-list/2011-August/msg00037.html")

---

### Post by pressureman on 2011-08-29
Still no official mention of world clock ([http://justinstories.wordpress.com/2011/05/26/ready-for-gnome-3-2-world-clock-comes-to-gnome-shell/](http://justinstories.wordpress.com/2011/05/26/ready-for-gnome-3-2-world-clock-comes-to-gnome-shell/)) or weather app ([http://justinstories.wordpress.com/2011/05/29/ready-for-gnome-3-2-welcome-back-the-weather-applet/](http://justinstories.wordpress.com/2011/05/29/ready-for-gnome-3-2-welcome-back-the-weather-applet/)) reappearing. Hopefully these features land in 3.2.

---

### Post by jbicha on 2011-08-30
> **pressureman said:**
> Still no official mention of world clock ([http://justinstories.wordpress.com/2011/05/26/ready-for-gnome-3-2-world-clock-comes-to-gnome-shell/](http://justinstories.wordpress.com/2011/05/26/ready-for-gnome-3-2-world-clock-comes-to-gnome-shell/)) or weather app ([http://justinstories.wordpress.com/2011/05/29/ready-for-gnome-3-2-welcome-back-the-weather-applet/](http://justinstories.wordpress.com/2011/05/29/ready-for-gnome-3-2-welcome-back-the-weather-applet/)) reappearing. Hopefully these features land in 3.2.

No, [GNOME 3.2 UI freeze]("https://live.gnome.org/ThreePointOne/") was yesterday. Perhaps in GNOME 3.4.

---

### Post by Harry33 on 2011-08-30
New Clutter (1.7.12-1) and Mutter (3.1.90) are available on the Ricotz Testing PPA.
I believe Gnome-shell 3.1.90 will be there soon.

---

### Post by pressureman on 2011-08-30
> **jbicha said:**
> No, [GNOME 3.2 UI freeze]("https://live.gnome.org/ThreePointOne/") was yesterday. Perhaps in GNOME 3.4.

D'oh... that's a shame. I'll have to install one of the third party plugins then. It baffles me that the gnome devs removed such fundamental features like that, which were in Gnome 2.x for years....

---

### Post by tista on 2011-08-30
Hi guys.

now I'm trying to run 3.1.90 gnome-shell, but no lock:
```
    JS ERROR: !!!   Exception was: Error: Requiring AccountsService, version none: Typelib file for namespace 'AccountsService' (any version) not found
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = '"gjs_throw"'
    JS ERROR: !!!     stack = '"("Requiring AccountsService, version none: Typelib file for namespace 'AccountsService' (any version) not found")@gjs_throw:0
@/usr/share/gnome-shell/js/ui/endSessionDialog.js:25
"'
    JS ERROR: !!!     message = '"Requiring AccountsService, version none: Typelib file for namespace 'AccountsService' (any version) not found"'
    JS ERROR: !!!   Exception was: Error: Requiring AccountsService, version none: Typelib file for namespace 'AccountsService' (any version) not found
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = '"gjs_throw"'
    JS ERROR: !!!     stack = '"("Requiring AccountsService, version none: Typelib file for namespace 'AccountsService' (any version) not found")@gjs_throw:0
@/usr/share/gnome-shell/js/ui/endSessionDialog.js:25
"'
    JS ERROR: !!!     message = '"Requiring AccountsService, version none: Typelib file for namespace 'AccountsService' (any version) not found"'
    JS ERROR: !!!   Exception was: Error: Requiring AccountsService, version none: Typelib file for namespace 'AccountsService' (any version) not found
    JS ERROR: !!!     lineNumber = '0'
    JS ERROR: !!!     fileName = '"gjs_throw"'
    JS ERROR: !!!     stack = '"("Requiring AccountsService, version none: Typelib file for namespace 'AccountsService' (any version) not found")@gjs_throw:0
@/usr/share/gnome-shell/js/ui/endSessionDialog.js:25
"'
    JS ERROR: !!!     message = '"Requiring AccountsService, version none: Typelib file for namespace 'AccountsService' (any version) not found"'
Window manager warning: Log level 32: Execution of main.js threw exception: Error: Requiring AccountsService, version none: Typelib file for namespace 'AccountsService' (any version) not found
```

today I couldn't upload 3.1.90 to PPA because of unresolved dependencies to build on Launchpad. but local build seems well... ;) pulling git to latest, updated any other gtk stuff, but the result was above.

so gnome-shell shows only mouse pointer and background without any shell stuff. :sad:
maybe we might have to update gjs package?

cheers.

**EDIT**
I've found the fix on mutter crash:
[http://git.gnome.org/browse/mutter/commit/?id=2f33d85a419df9755611113483e9e4431e583978]("http://git.gnome.org/browse/mutter/commit/?id=2f33d85a419df9755611113483e9e4431e583978")
now applying this patch and retrying...

**EDIT #2**
above patches got no luck...

and next is this:
[http://git.gnome.org/browse/gnome-shell/commit/?id=8f0c980d3cf1137ee64a0b76cc83c40fb4f4e143]("http://git.gnome.org/browse/gnome-shell/commit/?id=8f0c980d3cf1137ee64a0b76cc83c40fb4f4e143")

**EDIT #3**
no... didn't make any differences... :sad:
damned!

---

### Post by dino99 on 2011-08-30
dont remember where i've seen a changelog talking about " namespace 'AccountsService' (any version) not found " today.

but just get "pending publication":
gnome-shell (3.1.90+git20110830.c86f3b8d-0ubuntu1~11.10~ricotz2)

(Note: Some binary packages for this source are not yet published in the repository. )

Edit: now published, so into repo soon :)

---

### Post by tista on 2011-08-30
OK. now works!!

we need dependencies on gir1.2-accountservice-1.0 package to run.

cheers.

---

### Post by dino99 on 2011-08-30
> **tista said:**
> OK. now works!!

we need dependencies on gir1.2-accountservice-1.0 package to run.

cheers.

higher than 0.6.13-1ubuntu4 actually into Oneiric repo ?

---

### Post by paul_in_london on 2011-08-30
> **Harry33 said:**
> New Clutter (1.7.12-1) and Mutter (3.1.90) are available on the Ricotz Testing PPA.
I believe Gnome-shell 3.1.90 will be there soon.

I have the latest amd64 builds of **gnome-shell** and** mutter** from the Ricotz Testing ppa:

```
paul@oneiric-64:~$ apt-cache policy gnome-shell
gnome-shell:
  Installed: 3.1.90+git20110830.c86f3b8d-0ubuntu1~11.10~ricotz2
  Candidate: 3.1.90+git20110830.c86f3b8d-0ubuntu1~11.10~ricotz2
  Version table:
 *** 3.1.90+git20110830.c86f3b8d-0ubuntu1~11.10~ricotz2 0
        500 http://ppa.launchpad.net/ricotz/testing/ubuntu/ oneiric/main amd64 Packages
        100 /var/lib/dpkg/status
     3.1.4-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ oneiric/universe amd64 Packages
paul@oneiric-64:~$ apt-cache policy gnome-shell
gnome-shell:
  Installed: 3.1.90+git20110830.c86f3b8d-0ubuntu1~11.10~ricotz2
  Candidate: 3.1.90+git20110830.c86f3b8d-0ubuntu1~11.10~ricotz2
  Version table:
 *** 3.1.90+git20110830.c86f3b8d-0ubuntu1~11.10~ricotz2 0
        500 http://ppa.launchpad.net/ricotz/testing/ubuntu/ oneiric/main amd64 Packages
        100 /var/lib/dpkg/status
     3.1.4-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ oneiric/universe amd64 Packages
paul@oneiric-64:~$

paul@oneiric-64:~$ apt-cache policy mutter
mutter:
  Installed: 3.1.90+git20110830.2f33d85a-0ubuntu1~11.10~ricotz0
  Candidate: 3.1.90+git20110830.2f33d85a-0ubuntu1~11.10~ricotz0
  Version table:
 *** 3.1.90+git20110830.2f33d85a-0ubuntu1~11.10~ricotz0 0
        500 http://ppa.launchpad.net/ricotz/testing/ubuntu/ oneiric/main amd64 Packages
        100 /var/lib/dpkg/status
     3.1.4-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ oneiric/universe amd64 Packages
paul@oneiric-64:~$
```

but the amd64 build of **clutter-1.0** (1.7.12-1) doesn't seem to be available yet.

---

### Post by dino99 on 2011-08-30
GS 3.1.90 installed on i386: it works smootly :)

---

### Post by sgage on 2011-08-30
> **dino99 said:**
> GS 3.1.90 installed on i386: it works smootly :)

No go on 64-bit as of 18:30 UTC.

(referring to the version from ricotz/testing)

---

### Post by Harry33 on 2011-08-30
I have a well working 64-bit setup from the Testing PPA.
You just need to install the latest versions of all necessary packages from that PPA.
Gnome-shell has these new dependencies:
- gir1.2-accountsservice-1.0 (0.6.13-1ubuntu4)
- gir1.2-caribou-1.0 (0.3.5-0ubuntu1~11.10~ricotz1)
- gir1.2-folks-0.6 (0.6.1-0ubuntu2~oneiric1)
- gir1.2-gee-1.0 (0.6.1-2ubuntu1)
- libcaribou0 (0.3.5-0ubuntu1~11.10~ricotz1)
- libfolks25 (0.6.1-0ubuntu2~oneiric1)

As you can see, only gir1.2-accountsservice-1.0 and gir1.2-gee-1.0 are from Oneiric repos.

---

### Post by sgage on 2011-08-30
> **Harry33 said:**
> I have a well working 64-bit setup from the Testing PPA.
You just need to install the latest versions of all necessary packages from that PPA.
Gnome-shell has these new dependencies:
- gir1.2-accountsservice-1.0 (0.6.13-1ubuntu4)
- gir1.2-caribou-1.0 (0.3.5-0ubuntu1~11.10~ricotz1)
- gir1.2-folks-0.6 (0.6.1-0ubuntu2~oneiric1)
- gir1.2-gee-1.0 (0.6.1-2ubuntu1)
- libcaribou0 (0.3.5-0ubuntu1~11.10~ricotz1)
- libfolks25 (0.6.1-0ubuntu2~oneiric1)

As you can see, only gir1.2-accountsservice-1.0 and gir1.2-gee-1.0 are from Oneiric repos.

When I installed (upgraded) it from testing, it pulled in those dependencies. At login I got the desktop and what seemed to be a top panel that was the nautilus menu. Weird.

---

### Post by Harry33 on 2011-08-30
Indeed it is odd.
Did your setup run OK before the mutter/gnome-shell 3.1.90 installation?

---

### Post by sgage on 2011-08-30
> **Harry33 said:**
> Indeed it is odd.
Did your setup run OK before the mutter/gnome-shell 3.1.90 installation?

Yes, it was running fine under 3.1.4 from the repos, and it's running fine again (thank you ppa-purge!).

I used gnome-tweak-tool to set the theme to Adwaita - that's the only modification that I made.

---

### Post by paul_in_london on 2011-08-30
> **Harry33 said:**
> I have a well working 64-bit setup from the Testing PPA.
You just need to install the latest versions of all necessary packages from that PPA.
Gnome-shell has these new dependencies:
- gir1.2-accountsservice-1.0 (0.6.13-1ubuntu4)
- gir1.2-caribou-1.0 (0.3.5-0ubuntu1~11.10~ricotz1)
- gir1.2-folks-0.6 (0.6.1-0ubuntu2~oneiric1)
- gir1.2-gee-1.0 (0.6.1-2ubuntu1)
- libcaribou0 (0.3.5-0ubuntu1~11.10~ricotz1)
- libfolks25 (0.6.1-0ubuntu2~oneiric1)

As you can see, only gir1.2-accountsservice-1.0 and gir1.2-gee-1.0 are from Oneiric repos.

Thanks Harry - I have the same amd64 versions of those packages installed. All working ok, except that I installed and activated a couple of gnome-shell extensions yesterday, but after today's updates I'm no longer seeing them in gnome-tweak-tool.

---

### Post by Harry33 on 2011-08-30
> **paul_in_london said:**
> Thanks Harry - I have the same amd64 versions of those packages installed. All working ok, except that I installed and activated a couple of gnome-shell extensions yesterday, but after today's updates I'm no longer seeing them in gnome-tweak-tool.

I think the extensions ought to be of the version 3.1.90 too.
So we have to wait for them now.

---

### Post by paul_in_london on 2011-08-30
> **Harry33 said:**
> I think the extensions ought to be of the version 3.1.90 too.
So we have to wait for them now.

I can survive without them for the moment :)

---

### Post by sgage on 2011-08-30
> **sgage said:**
> Yes, it was running fine under 3.1.4 from the repos, and it's running fine again (thank you ppa-purge!).

I used gnome-tweak-tool to set the theme to Adwaita - that's the only modification that I made.

I tried again - it seemed there were some further upgrades available. 3.1.90 working beautifully here on my 64-bit system. :KS

---

### Post by tista on 2011-08-31
Hi guys.

I've already shifted to 3.1.90, but today experienced ugly issue...

when I type the words on search of overview, suddenly gs hang up!! :sad: only it's remained 2 chars on searchbar, all gs stuff completely crashed. so I had to return to vt and file the .xsession-errors:
```
(gnome-shell:3673): Clutter-CRITICAL **: clutter_text_get_editable: assertion `CLUTTER_IS_TEXT (self)' failed

(gnome-shell:3673): Clutter-CRITICAL **: clutter_text_get_text: assertion `CLUTTER_IS_TEXT (self)' failed

(gnome-shell:3673): Clutter-CRITICAL **: clutter_text_set_text: assertion `CLUTTER_IS_TEXT (self)' failed
```

any ideas?

P.S: I've used the latest mutter 3.1.90.1 pulled from git...

---

### Post by Sennaista on 2011-08-31
Been using 3.1.9 since yesterday, some minor issues but overall very usable.

I like the new session menu and full chat integration. The only thing that doesn't make much sense to me and therefore can be a bug (:P) is that if I set my status as "available", I can't toggle the "do not disturb" button to on position.

---

### Post by tista on 2011-08-31
> **Sennaista said:**
> Been using 3.1.9 since yesterday, some minor issues but overall very usable.

I like the new session menu and full chat integration. The only thing that doesn't make much sense to me and therefore can be a bug (:P) is that if I set my status as "available", I can't toggle the "do not disturb" button to on position.

Hi Sennaista.

yeah almost well!! ;)
for me, I could enable "do not disturb" while I set my status as "available"...
see my shot.

and now I'm uploading extensions for 3.1.90 to my PPA...

---

### Post by dino99 on 2011-08-31
> **Sennaista said:**
> Been using 3.1.9 since yesterday, some minor issues but overall very usable.

I like the new session menu and full chat integration. The only thing that doesn't make much sense to me and therefore can be a bug (:P) is that if I set my status as "available", I can't toggle the "do not disturb" button to on position.

Seems to be logic

---

### Post by Sennaista on 2011-08-31
> **tista said:**
> Hi Sennaista.

yeah almost well!! ;)
for me, I could enable "do not disturb" while I set my status as "available"...
see my shot.

and now I'm uploading extensions for 3.1.90 to my PPA...

It's weird, I tried it again and it work....then tried to do it again and it didn't. ;) Seems to be very moody.

---

### Post by Sennaista on 2011-08-31
> **dino99 said:**
> Seems to be logic

But where is the logic in only being able to say "do not disturb" when you are not online anyway?

---

### Post by xebian on 2011-08-31
Not sure but seems Ubuntu is like that.  The live CD of 8/30 for unity says 'keep' when it should be 'remove' for things already in launcher?

---

### Post by Sennaista on 2011-08-31
I don't think Ubuntu devs have anything to do with GS functionality.

---

### Post by skibler on 2011-09-02
I just did a fresh install of 11.10 beta 1 and installed gnome-shell/gdm.

Everything is working peachy, except for two small issues:

Nautilus keeps launching in "root window" mode, so it makes a menu bar across the very top of the screen. It is almost completely hidden by the gnome-shell UI, except for on the 2nd second monitor. There is now a grey bar across the top.

Why does nautilus think it needs to start in root window mode, and how do I stop it?

---

### Post by tista on 2011-09-07
Hi guys.

today upstream git had released 3.1.91! :P
[http://git.gnome.org/browse/gnome-shell]("http://git.gnome.org/browse/gnome-shell")
and now I'm testing it...
[https://launchpad.net/~tista/+archive/gtk3]("https://launchpad.net/~tista/+archive/gtk3")

then this rev could not handle Alt-Tab window switcher... :sad: this issue might exist the last updates of 3.1.90.1.

cheers.

---

### Post by jppr on 2011-09-07
it is soon repos [https://launchpad.net/ubuntu/oneiric/+source/gnome-shell/3.1.90.1-0ubuntu1](https://launchpad.net/ubuntu/oneiric/+source/gnome-shell/3.1.90.1-0ubuntu1)
and mutter [https://launchpad.net/ubuntu/oneiric/+source/mutter/3.1.90.1-0ubuntu1](https://launchpad.net/ubuntu/oneiric/+source/mutter/3.1.90.1-0ubuntu1)

Edit. [https://lists.ubuntu.com/archives/oneiric-changes/2011-September/thread.html ]("https://lists.ubuntu.com/archives/oneiric-changes/2011-September/thread.html")
[ From that found in any other system by the latest updates to come]("https://lists.ubuntu.com/archives/oneiric-changes/2011-September/thread.html")

---

### Post by paul_in_london on 2011-09-07
Following last night's updates, G-S loads and runs normally on both of my 32 bit installs.

Not so for me with 64 bit unfortunately. G-S fails to load automatically after login and I can't start it from the CLI either - even though I'm pretty sure I'm using the same set of G-S and other packages as on 32 bit (Ricotz ppa, xorg-edgers ppa etc).

Anyone else experiencing this?

Am at work now, but will check again tonight and post the output of:

```
gnome-shell --replace &
```

if it's still failing.

---

### Post by tista on 2011-09-07
> **paul_in_london said:**
> Following last night's updates, G-S loads and runs normally on both of my 32 bit installs.

Not so for me with 64 bit unfortunately. G-S fails to load automatically after login and I can't start it from the CLI either - even though I'm pretty sure I'm using the same set of G-S and other packages as on 32 bit (Ricotz ppa, xorg-edgers ppa etc).

Anyone else experiencing this?

Am at work now, but will check again tonight and post the output of:

```
gnome-shell --replace &
```

if it's still failing.

Hi paul. ;)

OMG... I've never experienced such pity... :sad:

and if you had .xsession-errors on kicking gs, let us see. or dmesg might record anything like segfaults or so...

cheers.

---

### Post by Harry33 on 2011-09-07
> **paul_in_london said:**
> Following last night's updates, G-S loads and runs normally on both of my 32 bit installs.

Not so for me with 64 bit unfortunately. G-S fails to load automatically after login and I can't start it from the CLI either - even though I'm pretty sure I'm using the same set of G-S and other packages as on 32 bit (Ricotz ppa, xorg-edgers ppa etc).

Anyone else experiencing this?

Am at work now, but will check again tonight and post the output of:

```
gnome-shell --replace &
```

if it's still failing.

I am using Ricotz Testing PPA in two different 64-bit setups and in one 32-bit setup.
All these work very well and fluently.

---

### Post by paul_in_london on 2011-09-07
> **tista said:**
> Hi paul. ;)

OMG... I've never experienced such pity... :sad:

and if you had .xsession-errors on kicking gs, let us see. or dmesg might record anything like segfaults or so...

cheers.

Hi Tista,

Thanks for the response. Will do. It was late last night when I ran into this so I only spent a little bit of time on it, but it's strange. One of the things I do remember checking is that it wasn't apparently caused by booting 3.1-rc4 on 64 bit as opposed to 3.0.0-10 on 32 bit (same box).

Maybe it'll resolve itself depending on which updates come through today.

Cheers,

Paul

---

### Post by paul_in_london on 2011-09-07
> **Harry33 said:**
> I am using Ricotz Testing PPA in two different 64-bit setups and in one 32-bit setup.
All these work very well and fluently.

Thanks very much for letting me know Harry - will investigate further this evening...

---

### Post by zacbarton on 2011-09-07
I'm loving the new anti-aliasing window decoration.
[IMG]http://zacbarton.com/screenshots/mutter_an_aa.png[/IMG]

---

### Post by tista on 2011-09-07
guys,

I've found the reason why I couldn't use Alt-Tab window switching...
yep, the evil was alternate-tab extension. maybe this issue would be appeared on 3.1.90.1 or 3.1.91...

I'm starting to fix...

regards.

---

### Post by sgage on 2011-09-07
Ricotz Testing now has 3.1.91 - working great here for me (64-bit, nvidia-current). I made a separate thread for 3.1.91.

---

### Post by jcphil on 2011-09-07
Any change on the issues with Gnome 3 and ATI video cards? With latest Oneiric, I still get panel weirdness and slanted, unusable pulldown menus in applications. I'm using the proprietary FGLRX driver from AMD.

---

### Post by tista on 2011-09-07
> **jcphil said:**
> Any change on the issues with Gnome 3 and ATI video cards? With latest Oneiric, I still get panel weirdness and slanted, unusable pulldown menus in applications. I'm using the proprietary FGLRX driver from AMD.

Hi jcphil. ;)

unfortunately it didn't yet...

see here:
[http://ati.cchtml.com/show_bug.cgi?id=99]("http://ati.cchtml.com/show_bug.cgi?id=99")

I'm using radeon with gallium3D instead of fglrx, works well!! :P

cheers.

---

### Post by jcphil on 2011-09-07
Thanks Tista! I'm going to wait a little bit. My card tends to overheat when I use another driver. It nearly ruined my laptop before I figured out what was happening.

> **tista said:**
> Hi jcphil. ;)

unfortunately it didn't yet...

see here:
[http://ati.cchtml.com/show_bug.cgi?id=99]("http://ati.cchtml.com/show_bug.cgi?id=99")

I'm using radeon with gallium3D instead of fglrx, works well!! :P

cheers.

---

### Post by jbicha on 2011-09-07
> **Sennaista said:**
> But where is the logic in only being able to say "do not disturb" when you are not online anyway?

From looking at the changelog, I believe that switch was changed in 3.1.91 to say "Notifications" instead of "Do Not Disturb".

---

### Post by paul_in_london on 2011-09-07
After today's updates, G-S was still working ok on 32 bit, but still failing on 64 bit (same box).

It wasn't immediately clear from the logs why this was happening, but looking for differences between the respective sets of installed packages that were related to gnome-shell, the first thing I realised was that I didn't have any gnome shell extensions installed on 32 bit.

So on the 64 bit I tried:

```
aptitude purge gnome-shell-extensions-{dock,alternative-status-menu,alternate-tab,workspace-indicator,user-theme,native-window-placement}
```

and after a reboot - problem solved! :)

---

### Post by bluebyt on 2011-09-07
Where is "suspend", now I have only the option to power off or restart?

---

### Post by tista on 2011-09-07
> **bluebyt said:**
> Where is "suspend", now I have only the option to power off or restart?

Hi bluebyt.

me, too...

if you run "gnome-power-statistics", could you see your power-state info? for me, it didn't, so this issue might cause oneiric system instead of gnome-shell...

cheers.

---

### Post by sammiev on 2011-09-07
In advance settings under shell, I set when lid close to suspend on AC.

---

### Post by bluebyt on 2011-09-07
> **tista said:**
> Hi bluebyt.

me, too...

if you run "gnome-power-statistics", could you see your power-state info? for me, it didn't, so this issue might cause oneiric system instead of gnome-shell...

cheers.

No, but I don't have a battery because this is not a laptop.

---

### Post by sammiev on 2011-09-07
You can also click on your computer name on the right top hand conner and select suspend.

---

### Post by Sennaista on 2011-09-08
It still says "Do Not Disturb" in the status menu. Suspend and Hibernate options have disappeared from the menu and the Alternative Status Menu Extension doesn't have any effect.

---

### Post by tista on 2011-09-08
> **Sennaista said:**
> It still says "Do Not Disturb" in the status menu. Suspend and Hibernate options have disappeared from the menu and the Alternative Status Menu Extension doesn't have any effect.

Hi Sennaista. ;)

that's right. today indicator-power almost disappeared from any other sessions, like unity, gnome-fallback, and so... :sad: so I suppose this issue caused oneiric system widely...

Gnome3 contributers had any ideas?

cheers.

P.S:
"Do Not Disturb"  must be fixed the name in 3.1.91.

**EDIT**
Just now I've updated these packages:
```
Upgraded the following packages:
gir1.2-clutter-1.0 (1.7.14-0ubuntu1~11.10~ricotz0) to 1.7.14-1~svn1
gir1.2-upowerglib-1.0 (0.9.12-1) to 0.9.13-1
gnome-settings-daemon (3.1.91-0ubuntu2) to 3.1.91-0ubuntu3
libclutter-1.0-0 (1.7.14-0ubuntu1~11.10~ricotz0) to 1.7.14-1~svn1
libclutter-1.0-common (1.7.14-0ubuntu1~11.10~ricotz0) to 1.7.14-1~svn1
libclutter-1.0-dev (1.7.14-0ubuntu1~11.10~ricotz0) to 1.7.14-1~svn1
libupower-glib-dev (0.9.12-1) to 0.9.13-1
libupower-glib1 (0.9.12-1) to 0.9.13-1
libzeitgeist-1.0-1 (0.3.10-0ubuntu1) to 0.3.12-0ubuntu1
libzeitgeist-dev (0.3.10-0ubuntu1) to 0.3.12-0ubuntu1
upower (0.9.12-1) to 0.9.13-1
zeitgeist-extension-fts (0.0.11-0ubuntu1) to 0.0.12-0ubuntu1
zeitgeist-fts-extension (0.0.11-0ubuntu1) to 0.0.12-0ubuntu1
```

then issue fixed!! Nice devs!! :P

---

### Post by sammiev on 2011-09-08
Different from mine. :confused:

---

### Post by tista on 2011-09-08
> **sammiev said:**
> Different from mine. :confused:

@sammiev,

which gs version did u use?
```
dpkg -l | grep gnome-shell
```

mine is 3.1.91 plus git latest sources... in both gs and gs-extensions... yours seems 3.1.90 or earlier, right?

cheers.

---

### Post by sammiev on 2011-09-08
> **tista said:**
> @sammiev,

which gs version did u use?
```
dpkg -l | grep gnome-shell
```

mine is 3.1.91 plus git latest sources... in both gs and gs-extensions... yours seems 3.1.90 or earlier, right?

cheers.

under system info it shows 3.1.91 but typing in your request shows 3.1.4-0.

Now why is that?

---

### Post by tista on 2011-09-08
> **sammiev said:**
> under system info it shows 3.1.91 but typing in your request shows 3.1.4-0.

Now why is that?

@sammiev,

Yeah it's quite normal. because gnome-shell is now only a piece of Gnome3 desktop environments. so "System Info" must show the version of "Gnome3" instead of "Gnome-Shell" I think. ;) as far as I know the future, at least today is so...

regards.

---

### Post by sammiev on 2011-09-08
Thanks tista :)

---

### Post by jbicha on 2011-09-08
The version number in System Info is just one piece of GNOME (gnome-desktop3 specifically). You need to use update-manager to get gnome-shell 3.1.90 which is the current Ubuntu 11.10 version. Not only is tista using gnome-shell 3.1.91 which isn't in the Ubuntu repositories yet but he's also using some extensions so yours won't look quite like his anyway.

By the way, 3.1.91 (which has only a week's worth of bugfixes/tweaks more than 3.1.90) requires caribou to make it into the repositories (even though it likely won't work yet since we use onboard as preferred screen keyboard) or someone to update my significant patch to build gnome-shell without caribou. Since gnome-shell 3.1.90 appears to run quite well, I'm content to wait a bit longer for caribou as updating that patch takes some time.

---

### Post by jbicha on 2011-09-08
Oops, I made a mistake in packaging 3.1.90 and it never built. Let me fix that...

---

### Post by tista on 2011-09-08
> **jbicha said:**
> Oops, I made a mistake in packaging 3.1.90 and it never built. Let me fix that...

Thanks a lot jbicha!! :P

today 3.1.91 seems quite well by applying a lot of minor fixes... and I also hope you devs knew the way to fix the issue "UBUNTU_MENUPROXY" patched gtk+3.0 had been breaking gtkmenubar on gnome-terminal, marlin and some more apps which has the option "show/hide menubar"... yeah that patch avoided such apps setting at all!! :sad:

cheers.

---

### Post by Sennaista on 2011-09-08
Does anyone know how to get the new GDM theme that's supposed to come with Gnome 3.2 working? Simply installing GDM doesn't work.

---

### Post by tista on 2011-09-08
> **Sennaista said:**
> Does anyone know how to get the new GDM theme that's supposed to come with Gnome 3.2 working? Simply installing GDM doesn't work.

Hi Sennaista. ;)

It might need some new gdm version:
[http://git.gnome.org/browse/gdm/log/]("http://git.gnome.org/browse/gdm/log/")

it now steps forward to 3.1.90, but our main repository sitll stacked too old one... I suppose ubuntu employed lightdm on oneiric release, so they might not be insterested in such newer gdm, isn't it?

cheers.

---

### Post by Sennaista on 2011-09-09
Thanks, I guess we have to wait and see. :)

---

### Post by jbicha on 2011-09-09
GDM is a bit complicated as we have a lot of patches that have to be rebased when new versions are released. I don't know whether GDM 3.2 will make it into Oneiric or not, but it is late in the release cycle.

---

### Post by sammiev on 2011-09-09
> **tista said:**
> @sammiev,

which gs version did u use?
```
dpkg -l | grep gnome-shell
```

mine is 3.1.91 plus git latest sources... in both gs and gs-extensions... yours seems 3.1.90 or earlier, right?

cheers.

Please see my update.
Thanks :)

---

### Post by tista on 2011-09-09
> **jbicha said:**
> GDM is a bit complicated as we have a lot of patches that have to be rebased when new versions are released. I don't know whether GDM 3.2 will make it into Oneiric or not, but it is late in the release cycle.

Hi jbicha!

Yep, I completely agree... many patches had to be re-composed in every release, and code bases had to be updated...

and I think gdm released until now had some ugly un-configurable options for themings, tweaks. :sad: now we got lightdm what has very good flexibility! :P light codes, easy configurations, and beauty...

cheers.

---

### Post by tista on 2011-09-09
> **sammiev said:**
> Please see my update.
Thanks :)

@sammiev,

OK.. GOOD! ;)

cheers.

---

### Post by screaminj3sus on 2011-09-12
I can't wait to finally have anti-aliased window borders without having to use emerald. I've switched full time to gnome-shell and love it besides the ugly borders!

---

### Post by zacbarton on 2011-09-12
> **screaminj3sus said:**
> I can't wait to finally have anti-aliased window borders without having to use emerald. I've switched full time to gnome-shell and love it besides the ugly borders!

AA borders are already done see [http://ubuntuforums.org/showpost.php?p=11226823&postcount=37](http://ubuntuforums.org/showpost.php?p=11226823&postcount=37)

---

### Post by screaminj3sus on 2011-09-12
> **zacbarton said:**
> AA borders are already done see [http://ubuntuforums.org/showpost.php?p=11226823&postcount=37](http://ubuntuforums.org/showpost.php?p=11226823&postcount=37)

Ah nice. I knew it had been done, but hadn't found a proper screen shot yet. Looks so much better. Suprised it took this long, with any rounded theme it makes a night and day difference between good looking and amateurish.

---

