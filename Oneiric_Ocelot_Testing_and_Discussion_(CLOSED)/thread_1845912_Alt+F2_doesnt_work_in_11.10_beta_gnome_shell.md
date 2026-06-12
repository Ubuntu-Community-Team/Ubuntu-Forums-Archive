---
title: "Alt+F2 doesnt work in 11.10 beta gnome shell"
date: 2011-09-18
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by rvchari on 2011-09-18
i ve installed gnome shell in 11.10 beta. i did it atleast 3 times but everytime Alt+F2 doesnt seem to function and fire up the window.

---

### Post by xxnishantxx on 2011-09-18
yeah, i noticed too. well, I guess it's still under development so some easy things have been left out to be added towards the end. up until yesterday, even suspend and resume wasn't working for me, but got fixed with an update, so I guess its just a matter of days before this gets fixed. probably be fixed by release of beta 2.

---

### Post by tista on 2011-09-18
Guys,

Which version did u use as these 2 packages?
* gobject-introspection
*pygobject

"runDialog" of gnome-shell didn't depend on so much system widely environments.
and today we almost might be able to load gnome-shell successfully with main repository I hope...

cheers.

---

### Post by xxnishantxx on 2011-09-18
gobject-introspection 1.29.17-0ubuntu1
there's no pygobject installed on my system. checked in synaptic.
Does it help?

---

### Post by Harry33 on 2011-09-18
> **xxnishantxx said:**
> gobject-introspection 1.29.17-0ubuntu1
there's no pygobject installed on my system. checked in synaptic.
Does it help?

Well, pygobject is python-gobject.
You do have it, because gnome-shell depends on it.

---

### Post by rbrick49 on 2011-09-18
working here

---

### Post by Harry33 on 2011-09-18
> **rbrick49 said:**
> working here
+1
Yes same here.

---

### Post by Quackers on 2011-09-18
Not here :-(  Hasn't worked for ages.

---

### Post by tista on 2011-09-18
> **Harry33 said:**
> Well, pygobject is python-gobject.
You do have it, because gnome-shell depends on it.

@Harry33,
Thanks for your following up... :)

> **rbrick49 said:**
> working here

@rbrick49,
Yeah me, too.. :sad:

> **Quackers said:**
> Not here  :sad: Hasn't worked for ages.

@Quackers.
Really? OMG...

does anybody know how to track this log down? .xsession-errors?
and I wanna ask you guys seemed to fail runDialog, 
1. the dialog showed up?
2. after the dialog appeared, ignores any typing to kick apps like "command not found"?

cheers.

---

### Post by karmila on 2011-09-18
Same here, Alt + F2 is not working.
GNOME Shell 3.1.90.1 :(

---

### Post by chakra_888 on 2011-09-18
It wasn't working for me by default, but I did the following to enable it.

In **System Settings** go to '**Keyboard**'
Open the second tab for **Shortcuts**.
Check in the **System **left Nav, there is **keybinding** for 'Show the run command prompt'.
If not double click it and press 'Alt + F2' to set it.

HTH

---

### Post by tista on 2011-09-18
> **chakra_888 said:**
> It wasn't working for me by default, but I did the following to enable it.

In **System Settings** go to '**Keyboard**'
Open the second tab for **Shortcuts**.
Check in the **System **left Nav, there is **keybinding** for 'Show the run command prompt'.
If not double click it and press 'Alt + F2' to set it.

HTH

@chakra_888,

Ahh... Nice finding!!

It must make sense to revive the keybindings for runDialog...
If I remembered well, in past (alpha2 or so) unity and/or compiz brought the ugly shortcuts on system global settings, then gs's one had been broken before... as far as I know, today it solved naturally... :/

Thanks for your experiencing! ;)

regards.

---

### Post by Quackers on 2011-09-18
> **chakra_888 said:**
> It wasn't working for me by default, but I did the following to enable it.

In **System Settings** go to '**Keyboard**'
Open the second tab for **Shortcuts**.
Check in the **System **left Nav, there is **keybinding** for 'Show the run command prompt'.
If not double click it and press 'Alt + F2' to set it.

HTH

I've tried these instructions a number of times but it still shows as "disabled" and will not change whatever I do.

---

### Post by mc4man on 2011-09-18
> **Quackers said:**
> I've tried these instructions a number of times but it still shows as "disabled" and will not change whatever I do.
Probably somethings borked in your install, on a fresh one wouldn't be any issue to enable

As of the latest O image
Alt+F2 is enabled in unity but is not in Gs

In Gs it must be enabled on a per user basis, if you set it to Alt+F2 as described then it's simply 'enabled' for that user (nothing written in that users ~/ as far as I can see
So it's really like 2 separate things, enabling the run dialog and setting the binding

If you set it to anything else other than Alt+F2 (the apparent default binding) then it is written to /apps/metacity/global_keybindings/panel_run_dialog and stored in ~/.gconf/apps/metacity/global_keybindings/%gconf.xml
If you were to set it to say Alt+F3, then remove the gconf file it will then revert back to Alt+F2 (the default) because it has previously been enabled

So what you could try with your current install is log into Gs, open gconf-editor and manually edit the key using <Alt>F2 - see screens

Or try setting it to something else in System Settings > keyboard > ..., see if it works, then delete the above mentioned file in ~/.gconf/apps/metacity/global_keybindings/%gconf.xml, do a logout/in & see.

---

### Post by Hakkatuka on 2011-09-18
> **Quackers said:**
> I've tried these instructions a number of times but it still shows as "disabled" and will not change whatever I do.

Try pressing SPACE after clicking on the shortcut you want to change, then the shortcut (ALT+f2).

---

### Post by karmila on 2011-09-19
> **chakra_888 said:**
> It wasn't working for me by default, but I did the following to enable it.

In **System Settings** go to '**Keyboard**'
Open the second tab for **Shortcuts**.
Check in the **System **left Nav, there is **keybinding** for 'Show the run command prompt'.
If not double click it and press 'Alt + F2' to set it.

HTH

thank you, this solve the problem.

---

### Post by Quackers on 2011-09-19
Thanks mc4man, the gconf-editor way has worked :-) (I thought gconf was being replaced by dconf.....?)
It was showing as disabled and I edited the key and now it's set. Logged out/in and now Alt+F2 brings up the run dialogue box. 
Very nice :-)

---

### Post by rbrick49 on 2011-09-19
mine works from alt-f2 I havent changed anything from the beta 1 release where I did a clean install 86x64 just updated everyday
by the way this is on gnome-shell from the main repository I just noticed someone said not working on unity will check
and it is also working on unity guys
regards ron

---

### Post by xxnishantxx on 2011-09-19
> **chakra_888 said:**
> It wasn't working for me by default, but I did the following to enable it.

In **System Settings** go to '**Keyboard**'
Open the second tab for **Shortcuts**.
Check in the **System **left Nav, there is **keybinding** for 'Show the run command prompt'.
If not double click it and press 'Alt + F2' to set it.

HTH

thanks, solved my problem. any idea why it wasn't default though?

---

### Post by jbicha on 2011-09-19
Those keyboard shortcuts have been set correctly for a long time, but something wasn't working right with gconf. I think it's working again now. If it's still broken, try moving .gconf/apps/metacity/ to another location. After verifying that it worked, I went ahead and removed that folder (you may want to check if you have any other settings in there that you want first). New installs shouldn't have this problem and hopefully it won't break again.

You may also need to run unity --reset especially if you've been messing around with CCSM too much but be aware that this will reset all of your Compiz settings to the defaults.

---

### Post by rvchari on 2011-09-20
> **chakra_888 said:**
> It wasn't working for me by default, but I did the following to enable it.

In **System Settings** go to '**Keyboard**'
Open the second tab for **Shortcuts**.
Check in the **System **left Nav, there is **keybinding** for 'Show the run command prompt'.
If not double click it and press 'Alt + F2' to set it.

HTH

thank you mate...
that did it !!!
wonder if the dumb nautilus menu that is visible in the back ground of top panel can be hidden with some tweaks like this !!!

---

