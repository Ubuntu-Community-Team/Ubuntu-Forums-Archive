---
title: "Firefox deleted deceitfully ~/.macromedia/Flash_Player/#SharedObjects"
date: 2011-08-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Sworddragon on 2011-08-09
I was wondering today why a savegame of a flashgame was missing. I figured out it was because I removed the history of Firefox with "Cache" selected. This option cleaned up the cache in ~/.mozilla/firefox/0.default/Cache and deleted the content in ~/.macromedia/Flash_Player/#SharedObjects.

But I want the to delete only the Firefox cache ans keep the Flash cache. It seems that Firefox doesn't provide such an option (or is there an option in about:config?). You can just delete all or nothing. I noticed this behaviour first with Firefox 6. But maybe it is only related to the Flash plugin (because I'm using a pre-release of Flash 11 from a ppa). Can somebody confirm this behaviour on Firefox?

---

### Post by jfernyhough on 2011-08-09
There's nothing deceitful about it - it's intended behaviour so as to delete Flash-based tracking cookies (LSOs). The upshot is that Flash game saves which are also in the same place are going to be deleted too.

You can revert to the old behaviour, and protect given objects, by using something like the BetterPrivacy addon (which deleted these ages before Mozilla decided to integrate it into Firefox). There's an option to disable the new Firefox behaviour in the BetterPrivacy options.

---

### Post by Sworddragon on 2011-08-09
In my opinion it is deceitful because Firefox never deleted the flash cookies before and there was not a warning that the cache-entry now deletes these cookies too. I tested better Privacy and it works good. It allows even to add an own entry for flash cookies in Firefox.

I will make a suggestion for Firefox to add such an official entry too.

---

