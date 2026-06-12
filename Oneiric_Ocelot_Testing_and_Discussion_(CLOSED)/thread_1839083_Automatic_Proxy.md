---
title: "Automatic Proxy?"
date: 2011-09-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by BrownieBoy on 2011-09-04
Hoorah!  The 11.10 beta now has an Automatic Proxy option in the Network settings.  This allows me to enter a config URL for our proxy at work.  (I don't know which one, but the config URL points to a .PAC file.)

The goods news is that Firefox picks this up just fine.  I checked Firefox Preferences, just to check that it wasn't doing its own thing, but it was set to "Use system proxy settings" there.

The bad news is that nothing else seems to picking these settings up.  I can get nothing out of the command line (e.g. sudo apt-get update) or from the likes of the Ubuntu Software Centre.  They are unable to resolve any internet addresses that they're given.

And there seems to no way of putting in the manual proxy authentication settings - our proxy requires authentication - like you can do on 11.04.

I should add that I'm running the 11.10 Beta as a VirtualBox guest, under a Windows XP host.

---

