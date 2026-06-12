---
title: "Firefox lost settings"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by Matt26 on 2008-07-25
i just installed the meta package update for Firefox 1.0.3 and have also been having difficulties getting the new adobe flash player 10 beta 2 to work correctly in Firefox (keeps crashing the brwoser everytime i have it installed) but just after i removed the flash player most recently and tried to open Firefox again, all of my tabs from my previos session are gone!  when Firefox opens now all i get is a blank tab, and if i click the Home button all i get is a Google/Firefox start page- which isn't even my homepage- and i checked the homepage setting in Firefox and it hasn't changed. plus, if i look at the Bookmarks menu in Firefox, all of my bookmarks are gone- and the Bookmarks menu looks cut off- like it is missing some of the standard entries that the menu has by default..

i tried reinstalling Firefox, plus removing then installing Firefox again via Synaptic but no success- i am still having the same issues..

does anyone know what could be causing this and how i might go about fixing it?

any help would be greatly appreciated.

thanks.

---

### Post by silkstone on 2008-07-25
You have to completely uninstall FF and also delete the folder .mozilla/firefox/xxx.default (xxx can be anything!), then reinstall FF.

Unfortunately you'll lose all your bookmarks, add-ons and settings, so you have to configure everything again, unless you use Foxmarks in which case you can reimport the bookmarks.

---

### Post by Matt26 on 2008-07-25
> **silkstone said:**
> You have to completely uninstall FF and also delete the folder .mozilla/firefox/xxx.default (xxx can be anything!), then reinstall FF.

Unfortunately you'll lose all your bookmarks, add-ons and settings, so you have to configure everything again, unless you use Foxmarks in which case you can reimport the bookmarks.

just to be clear- i only need to delete the folder under ~/.mozilla/firefox that has .default in the filename?

also, this might seem like a silly question, but can i still backup everything under my ~/.mozilla directory in order to save all of my Firefox settings in order to restore them once i have reinstalled Firefox?

thanks.

---

### Post by Matt26 on 2008-07-30
> **silkstone said:**
> You have to completely uninstall FF and also delete the folder .mozilla/firefox/xxx.default (xxx can be anything!), then reinstall FF.

Unfortunately you'll lose all your bookmarks, add-ons and settings, so you have to configure everything again, unless you use Foxmarks in which case you can reimport the bookmarks.

i did this and now i get the following error message even after rebooting my system- as it suggests:

**Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system.**

any suggestions anyone?

---

### Post by Matt26 on 2008-08-01
> **Matt26 said:**
> i did this and now i get the following error message even after rebooting my system- as it suggests:

**Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system.**

any suggestions anyone?

i discovered that this error message is related to the Firefox profile folder (xxx.default) being removed from the ~/.mozilla/firefox directory

once i created a new Firefox profile using **firefox -profilemanager** via the command console and then copied all of my files from the old xxx.default directory to the newly created one (i saved a backup) i was able to get Firefox running again and restore all of my Firefox settings as well.

:)

---

