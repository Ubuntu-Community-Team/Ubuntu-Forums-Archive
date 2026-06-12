---
title: "Ubuntu 10.04 Desktop access vanished"
date: 2012-02-07
forum: New to Ubuntu
---

### Post by janisgeiger on 2012-02-07
Hi. After so many times googling around when a problem happened or checking to my knowledge how to resolve some problems, I'm getting a bit tired.

I'm using gnome 2.30.2

After boot-up, everything works correctly, panels, menus
but there are no icons on the desktop anymore, nor can I click / right-click on the desktop.

When i start running nautilus as root, the desktop loads correctly, showing the content of the root desktop folder.

So I guess it's not a graphic driver issue, but how to change the default user desktop back to actually showing up?
anyone knows what could be done, and how it could've happened?

PS: the default desktop folder still exists, can be accessed normally via file browsing

Thanks, J

---

### Post by wolfen69 on 2012-02-07
Try [this]("http://www.liberiangeek.net/2010/11/restorereset-desktop-ubuntu-10-0410-10-maverick-meerkat/").

---

### Post by Krytarik on 2012-02-08
> **wolfen69 said:**
> Try [this]("http://www.liberiangeek.net/2010/11/restorereset-desktop-ubuntu-10-0410-10-maverick-meerkat/").
OMG, please don't! (Sorry, wolfen69, but that is extreme overkill for trying to solve *any* issue.)

The more sensible approach:
[LIST]
[*]First, make sure Nautilus is set to handle the desktop:
```
gconftool-2 /apps/nautilus/preferences/show_desktop --type bool --set true
```
[*]Second, make sure the file "~/.config/user-dirs.dirs" has an entry looking exactly like this:
```
XDG_DESKTOP_DIR="$HOME/Desktop"
```
If you need to modify it, relogin thereafter.
[/LIST]
Regards.

---

### Post by janisgeiger on 2012-02-10
Hey, thanks for the replies.

About Nautilus, I've already done that via the config editor.

apps>Nautilus>prefererences>Show Desktop.

The thing is, it's always marked on, as 'True', even after boot up. Still, no icons / desktop.
BUT, I found a strange workaround.

when I load up / look at the desktop folder in nautilus *first* and then 'recheck' the apparent option again, the desktop + icons appear. Stating your cmd line has the same effect. is this a clue to something?

The XDG_Desktop_Dir... in user-dirs.dirs exists, letter for letter.

I  could try out the solution by wolfen69, though I think it's a pretty strange behaviour of my desktop, I assume it could be corrected more directly/independently. I guess this would reset everything back to normal again, meaning, take a screenshot, reset, set the icons on the panels again.

I'll eventually see, look further, if I have more time.

Cheers / thanks, J

---

### Post by Krytarik on 2012-02-10
> **janisgeiger said:**
> when I load up / look at the desktop folder in nautilus *first* and then 'recheck' the apparent option again, the desktop + icons appear. Stating your cmd line has the same effect. is this a clue to something?
Do you have your home directory on an external partition/drive?

> **janisgeiger said:**
> I  could try out the solution by wolfen69, ... I guess this would reset everything back to normal again, meaning, take a screenshot, reset, set the icons on the panels again.
Actually, that would reset the *entire desktop environment* back to defaults, plus a great deal of apps! So I'd better not do that, plus I don't think that it would actually help.

---

### Post by janisgeiger on 2012-02-11
> **Krytarik said:**
> Do you have your home directory on an external partition/drive?

No, it's installed right on the first startup partition. But, why not, actually the desktop reappeared even after only looking into the home folder first and then rechecking the "show desktop" option. So I guessed it must have been something about nautilus not loading at boot.

So, I've found some kind of workaround. By booting normally, starting nautilus, going to 'System, Preferences, Startup Applications' and checking "Remember currently running application". The desktop at boot is back again.

Not really satisfied though, didn't have time to look into some system things, I'm worried if some "system internal message system" is now referring from unnecessary points to other unnecessary points at boot without making it a clean healthy boot. (as if, my solution above did just override some wrong lines prioritywise but not replace them.)

But who cares, for NOW

(if I'll notice my boot will be slower gee will I be ... !) ;) Cheers.

---

