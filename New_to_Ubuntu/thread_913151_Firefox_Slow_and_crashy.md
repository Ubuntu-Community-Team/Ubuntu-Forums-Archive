---
title: "Firefox: Slow and crashy"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by SalsaShark on 2008-09-07
I've been having some trouble with Firefox 3.0.1 lately.  It seems to be a lot slower when loading pages and it seems to just close randomly when loading pages from time to time.  I've been using Firefox for about 3 or 4 years now and I never had this problem on either XP, Vista, or when I was using Firefox 2.5.x in Ubuntu 7.10.  I run a Vista/Ubuntu 8.04 and Firefox on Vista works totally fine.  Does anyone have any idea what the problem could be, and if so, how to fix it?

---

### Post by kjohansen on 2008-09-07
Have you installed any plugins lately?  Upgraded flash?

---

### Post by SalsaShark on 2008-09-07
I have, but it has acted this way before I added anything.

---

### Post by billgoldberg on 2008-09-07
> **SalsaShark said:**
> I've been having some trouble with Firefox 3.0.1 lately.  It seems to be a lot slower when loading pages and it seems to just close randomly when loading pages from time to time.  I've been using Firefox for about 3 or 4 years now and I never had this problem on either XP, Vista, or when I was using Firefox 2.5.x in Ubuntu 7.10.  I run a Vista/Ubuntu 8.04 and Firefox on Vista works totally fine.  Does anyone have any idea what the problem could be, and if so, how to fix it?

Most likely it's the Flash plugin.

I would suggest you upgrade to flash player 10 RC, that should fix the problem.

[http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/](http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/)

--

Note: you can always use another browser.

I suggest you take a look at "epiphany". Make sure to install the extension packages from the Ubuntu repos (this includes adblock plus, ...).

Or try Opera. A .deb file can be downloaded from their website. A .deb file is installed by double clicking it.

---

### Post by kaibob on 2008-09-07
If not Flash, it could be another plug-in or extension. The best way to check this is to create a new profile. To do this, enter "firefox -ProfileManager" in a terminal window.

If Firefox runs properly with the new profile, you can copy over your bookmark and any other user files and, after a test period, delete the old profile. If this doesn't help, you'll know to look elsewhere.

REFERENCE
[http://support.mozilla.com/en-US/kb/Managing+profiles](http://support.mozilla.com/en-US/kb/Managing+profiles)

---

### Post by SalsaShark on 2008-09-08
> **billgoldberg said:**
> Most likely it's the Flash plugin.

I would suggest you upgrade to flash player 10 RC, that should fix the problem.

[http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/](http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/)

--

Note: you can always use another browser.

I suggest you take a look at "epiphany". Make sure to install the extension packages from the Ubuntu repos (this includes adblock plus, ...).

Or try Opera. A .deb file can be downloaded from their website. A .deb file is installed by double clicking it.

I tried installing the flash player 10 plugin, but it doesn't come up under my installed plugins.  These are the plugins I have installed:
Default Plugin
Demo Print Plugin for unix/linux
DivX Web Player version 1.4.0.233
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible;Totem)
iTunes Application Detector (Disabled)
Java(TM) Plugin 1.6.0_06-b02
QuickTime Plug-in 7.2.0
Shockwave Flash 9.0 r124
Totem Web Browser Plugin 2.22.1
VLC Multimedia Plugin (compatible; Totem 2.22.1)
Windows Media Player Plug-in (compatible; Totem)
I imagine some of these are redundant, I assume I don't need all of these media plugins but I really don't know.  Also, how do you remove the plugins from your system and not just disable them?
The only extensions I have are StumbleUpon, AdBlock Plus, and Download Statusbar.  But I don't know that I could live without StubleUpon and thus switching would kind of suck.

I also think one problem (it being slow) may be my wireless connection.  When I'm in my bedroom (which is a short ways from my living room, where my router is) I only get two bars, but in my living room I get 4 - about 90% when I'm literally 7 feet away from the router.  But it's only 40% in my bedroom.  It's not nearly that small under vista (around 80%) so I assume it's a driver issue.  It's a atheros ar5007G and I had to do some funky thing to get it working

---

### Post by gjoellee on 2008-09-08
what ever this may be, it is fixed in Intrepid Alpha 5, and also in the next upcoming version of Firefox (either 3.0.2 or 3.1)

---

### Post by gjoellee on 2008-09-08
what ever this may be, it is fixed in Intrepid Alpha 5, and also in the next upcoming version of Firefox (either 3.0.2 or 3.1)

Oh, by the way I have a flash-plugin .deb (flash 10) on my website: [http://www.kshoster.net/?c=downloads&h=deb](http://www.kshoster.net/?c=downloads&h=deb)

---

