---
title: "Gnome-shell and mutter 3.1.4"
date: 2011-07-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-07-30
I just installed gnome-shell 3.1.4 and mutter 3.1.4 along with clutter 1.7.6.
These are new releases with several fixes and better properties.
They seem to run more fluently.

Gnome-shell 3.1.4
> * Take over inserted media handling and autorun from gnome-session [Cosimo]
* Message Tray
  - Display a count of unread notifications on icons
    [Jasper, Guillaume; #649356, #654139]
  - Only remove icons when the sender quits from D-Bus, not when it
    closes its last window [Neha, Marina; #645764]
  - Solve problems switching chats between shell and Empathy
    [Guillaume; #654237]
  - Fix handling of bad GMarkup in messages [Dan; #650298]
  - Never show notifications when the screensaver is active [Dan; #654550]
* Telepathy integrationpp
  - Implement Telepathy Debug interface to enable empathy-debugger
    [Guillaume; #652816]
  - Allow approving room invitations, and audio/video calls
    [Guillaume; #653740 #653939]
  - Send typing notifications [Jonny; #650196]
* Fix selection highlighting for light-on-dark entries [Jasper; #643768]
* Make control-Return in the overview open a new window [Maxim]
* Delay showing the alt-Tab switcher to reduce visual noise when
  flipping betweeen windows [Dan; #652346]
* When we have vertically stacked monitors, put the message tray
  on the bottom one [Dan; #636963]
* Fix various problems with keynav and the Activities button
  [Dan; #641253 #645759]
* Ensure screensaver is locked when switching users [Colin; #654565]
* Improve extension creation tool [Jasper; #653206]
* Fix compatibility with latest GJS [Giovanni; #654349]
* Code cleanups [Adel, Dan, Jasper; #645759 #654577 #654791 #654987]
* Misc bug fixes [Richard, Dan, Florian, Giovanni, Jasper, Marc-Antoine, Rui;
  #647175 #649513 #650452 #651082 #653700 #653989 #654105 #654791 #654267
  #654269 #654527 #655446]
* Build fixes [Florian, Siegfried; #654300]

Mutter 3.1.4
> * Use better, much more subtle shadow definitions [Jakub; #649374]
* Add the ability to use named GTK+ colors in theme files as
  gtk:custom(name,fallback) [Florian; #648709]
* Port from GdkColor to GdkRGBA and from GtkStyle to GtkStyleContext
  [Florian; #650586]
* Try to fix window bindings using the Super key [Owen; #624869]
* Update to using more modern Cogl and Clutter APIs
  [Adel, Emmanuele, Neil; #654551 #654729 #654730 #655064]
* Fix for srcdir != builddir builds [Thierry; #624910]
* Make handling of focus appearance for attached dialogs more robust
  [Dan; #647712]
* Misc bug fixes
  [Dan, Florian, Jasper, Owen, Rui; #642957 #649374 #650661 #654489 #654539]

These are available from ricotz staging PPA, however be careful with that.
It is always good to have root console skills. :D

---

### Post by sgage on 2011-07-30
Not working here - I get a blank desktop (with my wallpaper), but no panel or launcher. The upgrade seemed to go smoothly with no errors - any idea how I might proceed?

[edit - I tried another login, and this time just got stuck at the blank lightdm background with a cursor. PPA-purged staging: same thing. Maybe I need to start from scratch.]

---

### Post by Harry33 on 2011-07-30
> **sgage said:**
> Not working here - I get a blank desktop (with my wallpaper), but no panel or launcher. The upgrade seemed to go smoothly with no errors - any idea how I might proceed?

[edit - I tried another login, and this time just got stuck at the blank lightdm background with a cursor. PPA-purged staging: same thing. Maybe I need to start from scratch.]

It seems the issue is not in the staging PPA itself.

People seem to have a lot of issues due to nvidia-current vs nouveau.
One need to reinstall nvidia-current after each mesa and kernel update.

Other issues may be due to lightDM upgrade to the new API (0.9.2).
It is best to uninstall the previous version completely and then install the new version.

---

### Post by tista on 2011-08-26
Hi Harry33. ;)

I've also experienced 3.1.4.... that's nice!! expecially latest mutter solved darkest transparency on gnome-terminal...

but one thing.
this 3.1.4 seems to break my activities extension to replace the label to icon, gnome-tweak-tool says this extension is disabled... :sad: that's the reason devs polished activities button?

cheers.

---

### Post by jbicha on 2011-08-26
tista, are you using a late enough version of the extension? You can try the git repository.

---

### Post by tista on 2011-08-26
> **jbicha said:**
> tista, are you using a late enough version of the extension? You can try the git repository.

Hi jbicha.

Thanks!!
I would see git tree soon! ;)

regards.

**EDIT**
I've tried Ricotz PPA... and the current release had to handle extensions ON/OFF via docnf-editor manually instead of gnome-tweak-tool... :sad: when I pressed ON/OFF switch on it, soon crashed!! still I didn't trace this error, seems Glib-GIO error...

cheers.

---

### Post by tista on 2011-08-28
Hi guys. ;)

today I've tried Rico's latest:
gnome-shell 3.1.4+git20110827.4e9e6e75-0ubuntu1~11.10~ricotz0

then I've experienced "vanished window"... shell's stuff were normal, but all of gkt windows were hidden... :sad: so once  I've rollbacked to 3.1.4+git20110825.a64e0e1f-0ubuntu1~11.10~ricotz0, it works well again.

caused this patch?
[http://git.gnome.org/browse/gnome-shell/diff/?id=a13af7fbccc91c71a390e7dbe8db267e755557a5]("http://git.gnome.org/browse/gnome-shell/diff/?id=a13af7fbccc91c71a390e7dbe8db267e755557a5")

cheers.

---

### Post by Harry33 on 2011-08-28
> **tista said:**
> Hi guys. ;)

today I've tried Rico's latest:
gnome-shell 3.1.4+git20110827.4e9e6e75-0ubuntu1~11.10~ricotz0

then I've experienced "vanished window"... shell's stuff were normal, but all of gkt windows were hidden... :sad: so once  I've rollbacked to 3.1.4+git20110825.a64e0e1f-0ubuntu1~11.10~ricotz0, it works well again.

caused this patch?
[http://git.gnome.org/browse/gnome-shell/diff/?id=a13af7fbccc91c71a390e7dbe8db267e755557a5]("http://git.gnome.org/browse/gnome-shell/diff/?id=a13af7fbccc91c71a390e7dbe8db267e755557a5")

cheers.

Todays git version works well in my 64-bit setup.

---

### Post by tista on 2011-08-28
> **Harry33 said:**
> Todays git version works well in my 64-bit setup.

Thanks Harry33. ;)

I had no luck... :sad:
here is the log when kicking gtk apps on gnome-shell:
```
** (process:1381): DEBUG: zeitgeist-datahub.vala:174: Inserting 1 events
    JS ERROR: !!!   Exception was: TypeError: actor.meta_window.is_attached_dialog is not a function
    JS ERROR: !!!     lineNumber = '312'
    JS ERROR: !!!     fileName = '"/usr/share/gnome-shell/js/ui/windowManager.js"'
    JS ERROR: !!!     stack = '"([object _private_Shell_WM],[object _private_Meta_WindowActor])@/usr/share/gnome-shell/js/ui/windowManager.js:312
"'
    JS ERROR: !!!     message = '"actor.meta_window.is_attached_dialog is not a function"'
** (gnome-fallback-mount-helper:1382): DEBUG: ConsoleKit session is active 0
```

cheers.

---

### Post by jbicha on 2011-08-28
> **tista said:**
> 
I've tried Ricotz PPA... and the current release had to handle extensions ON/OFF via docnf-editor manually instead of gnome-tweak-tool... :sad: when I pressed ON/OFF switch on it, soon crashed!! still I didn't trace this error, seems Glib-GIO error...

cheers.

I believe this was fixed in gnome-tweak-tool trunk. It's easy to run the git version of tweak-tool. Because it's Python, you don't need to compile anything yourself.

```
git clone git://git.gnome.org/gnome-tweak-tool
cd gnome-tweak-tool
./gnome-tweak-tool
```

---

### Post by tista on 2011-08-28
> **jbicha said:**
> I believe this was fixed in gnome-tweak-tool trunk. It's easy to run the git version of tweak-tool. Because it's Python, you don't need to compile anything yourself.

```
git clone git://git.gnome.org/gnome-tweak-tool
cd gnome-tweak-tool
./gnome-tweak-tool
```

Hi jbicha. ;)

Yeah the latest 3.1.1~git20110821.66e9c1ca-0ubuntu1~11.10~ricotz1 were OK. fixed it! ;)
but still gnome-shell's "vanished window" existed on the latest master branch... :sad:

Should I track this issue down via LookingGlass?

regards.

---

### Post by jbicha on 2011-08-28
It's probably worth asking about it in #gnome-shell on irc.gnome.org since GNOME 3.2's beta release is imminent.

---

### Post by tista on 2011-08-28
> **jbicha said:**
> It's probably worth asking about it in #gnome-shell on irc.gnome.org since GNOME 3.2's beta release is imminent.

Thanks.

I've found the latest mutter had been added such "attached dialogs" on master barnch related to gnome-shell 3.1.4 master barnch... ;)
[http://git.gnome.org/browse/mutter/commit/?id=2be1574e5504094848a75cb00d59a49d944edffc]("http://git.gnome.org/browse/mutter/commit/?id=2be1574e5504094848a75cb00d59a49d944edffc")

So trying to sync mutter to latest on my PPA...

Regards.

---

### Post by jbicha on 2011-08-28
> **tista said:**
> Thanks.

I've found the latest mutter had been added such "attached dialogs" on master barnch related to gnome-shell 3.1.4 master barnch... ;)
[http://git.gnome.org/browse/mutter/commit/?id=2be1574e5504094848a75cb00d59a49d944edffc](http://git.gnome.org/browse/mutter/commit/?id=2be1574e5504094848a75cb00d59a49d944edffc)

So trying to sync mutter to latest on my PPA...

Regards.

Yes, that makes sense. Mutter intentionally does not keep ABI compatibility but is basically only used by gnome-shell.

---

### Post by pelle.k on 2011-08-28
Hey, can mutter do anything other that cascading window placing yet? I much, much prefer the smart window managment of compiz and kwin. If i remember correctly, even metacity did "smart" window managment.

---

### Post by tista on 2011-08-28
> **jbicha said:**
> Yes, that makes sense. Mutter intentionally does not keep ABI compatibility but is basically only used by gnome-shell.

Thanks a lot jbicha!

Yep, Bingo!! :P
now it works well...

Best Regards.

---

### Post by tista on 2011-08-29
Hi guys.

today git upstream released 3.1.90 on both mutter/gnome-shell!! :P
but unfortunately our folks package on main repository couldn't provide 2 important files needed by them:
```
usr/lib/girepository-1.0/Folks-0.6.typelib
usr/share/gir-1.0/Folks-0.6.gir
```

and already upstream released folks-0.6.1 as well, so I really hope devs could update folks package soon!!

cheers.

---

### Post by jbicha on 2011-08-30
> **tista said:**
> Hi guys.

today git upstream released 3.1.90 on both mutter/gnome-shell!! :P
but unfortunately our folks package on main repository couldn't provide 2 important files needed by them:
```
usr/lib/girepository-1.0/Folks-0.6.typelib
usr/share/gir-1.0/Folks-0.6.gir
```and already upstream released folks-0.6.1 as well, so I really hope devs could update folks package soon!!

cheers.

We're in beta freeze so the official repositories are temporarily closed for most updates. I think we'll see some updates on Friday though after Ubuntu 11.10 Beta 1 is released.

---

### Post by Harry33 on 2011-08-30
New Clutter (1.7.12-1) and Mutter (3.1.90) are now available on the Ricotz Testing PPA.
I believe Gnome-shell 3.1.90 will be there soon.

---

