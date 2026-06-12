---
title: "Is it Ubuntu or is it Firefox ?"
date: 2023-03-04
forum: New to Ubuntu
---

### Post by Innernet on 2023-03-04
Hello.
Happened again :  After the forced updating of something Firefox, now the top and the bottom in the list of favorites in a subfolder do no work.  Clicking on them does nothing.
Example : 'Show your bookmarks' star tray ---> forums folder ---> list shows, but top and bottom links do not work.
Third time that flaws surface after the forced updating happens.  I always delay the updates as much as possible but at some point am caught. :(

---

### Post by DuckHook on 2023-03-04
Since FF became a snap app you are right, it's now a forced upgrade and there is nothing you can do about it except delay.

The snap nature of FF has many people thoroughly spooked. Your problem may not necessarily have anything to do with snap though. Try the following, in order:

[LIST=1]
[*]Clear the cache in FF
[*]After backing up your bookmarks and other data, reset FF to its default state. Lots of walkthroughs with a websearch. Make sure your bookmarks are safe and accessible before resetting.
[*]If all else fails, consider removing snap FF and installing .deb version. Instructions for installing .deb: [https://ubuntuforums.org/showthread.php?t=2438709&p=13939386#post13939386](https://ubuntuforums.org/showthread.php?t=2438709&p=13939386#post13939386)
Ignore the LXD stuff unless you are in the mood for a wild ride. You must first uninstall snap version or else you will have two possibly conflicting versions at once. This means that you can only restore bookmarks/history/etc if you previously did a proper export of this data.
[/LIST]

---

### Post by ian-weisser on 2023-03-04
Hmmm. All my bookmarks on Firefox (snap) seem to be working properly.

What is a "'Show your bookmarks' star tray?" That option is not found is a stock Firefox without any extensions. There are several bookmark-related options, but none with that name.

I want to be able to duplicate the issue in a test environment, and so far I cannot. Please help me to do so.

---

### Post by DuckHook on 2023-03-04
> **ian-weisser said:**
> &#8230;What is a "'Show your bookmarks' star tray?" That option is not found is a stock Firefox without any extensions. There are several bookmark-related options, but none with that name.
OP is referring to the standard bookmarks button. In a default FF, it is hidden but can be revealed and moved to FF tray using the "More Tools" >> button on the far right side of FF tray. It is a star icon with "Show your bookmarks" popout.

---

### Post by ian-weisser on 2023-03-05
Aha, thanks.

Creating folders, adding bookmarks. Trying to get those bookmarks to not work. (So far, working). 

Further tips in how to reproduce the issue are welcome.

---

### Post by Innernet on 2023-03-05
Thanks.  
Ian-weisser : Exactly as properly described on post #4.   
As an attempt to reproduce the issue, perhaps try to populate a favorites folder with a list that contains more links than the vertical 'room' can display.  In my case, it is about 30 entries with need to scroll to show them all.

---

### Post by mIk3_08 on 2023-03-06
> **Innernet said:**
> Hello.
Happened again :  After the forced updating of something Firefox, now the top and the bottom in the list of favorites in a subfolder do no work.  Clicking on them does nothing.
Example : 'Show your bookmarks' star tray ---> forums folder ---> list shows, but top and bottom links do not work.
Third time that flaws surface after the forced updating happens.  I always delay the updates as much as possible but at some point am caught. :( It's probably Firefox not Ubuntu. Applications has noting to do with the Operating System. Its usually Firefox that always encounter errors with the end user. I always use this Firefox browser and I haven't encounter this error so far since I have installed 22.04 LTS in my machine. Regards and cheers.

---

### Post by ian-weisser on 2023-03-06
Hmm. Still not able to reproduce.

The issue might match a previously reported bug at [https://bugzilla.mozilla.org/buglist.cgi?product=Firefox&component=Bookmarks%20%26%20History&bug_status=__open__](https://bugzilla.mozilla.org/buglist.cgi?product=Firefox&component=Bookmarks%20%26%20History&bug_status=__open__)

---

### Post by DuckHook on 2023-03-06
@Innernet

If you are working the problem as an intellectual/curiosity exercise, then by all means go for it. But if looking for a solution, then try the steps outlined in my post #2 above. Especially resetting FF.

Have you tried that?

---

### Post by Innernet on 2023-03-12
Thanks.   I see there is reset, restart, refresh, reload,  and for preferences, for customizations, for add-ons, for extensions, for everything ?

At the 3 horizontal lines at right,  In 'Settings' did not see the option;  In  'More tools', did not see the option to do what you suggest.  Should I first get a report of the current installed/tweaked customizations before attempting anything ?
At top left FF icon; with left click or right click cannot find how-to either.

---

### Post by DuckHook on 2023-03-12
[https://support.mozilla.org/en-US/kb/refresh-firefox-reset-add-ons-and-settings#firefox:linux:fx102](https://support.mozilla.org/en-US/kb/refresh-firefox-reset-add-ons-and-settings#firefox:linux:fx102)
[https://support.mozilla.org/en-US/kb/reset-preferences-fix-problems](https://support.mozilla.org/en-US/kb/reset-preferences-fix-problems)

---

### Post by mIk3_08 on 2023-03-12
> **Innernet said:**
> Thanks.   I see there is reset, restart, refresh, reload,  and for preferences, for customizations, for add-ons, for extensions, for everything ?

At the 3 horizontal lines at right,  In 'Settings' did not see the option;  In  'More tools', did not see the option to do what you suggest.  Should I first get a report of the current installed/tweaked customizations before attempting anything ?
At top left FF icon; with left click or right click cannot find how-to either.
Have you tried the .deb version of Firefox, as what DuckHook suggested in post #2 or just use the tar.bz version of Firefox. 
[Click Here]("https://www.mozilla.org/en-US/"). Regards and cheers.

---

