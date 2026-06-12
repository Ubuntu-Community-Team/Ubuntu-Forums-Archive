---
title: "Firefox &quot;lost&quot; bookmarks. Why?"
date: 2017-12-26
forum: New to Ubuntu
---

### Post by sterator on 2017-12-26
This morning, when I launched FF, the 6 or so bookmarks I'd placed in the bookmarks bar were gone.

FF showed some kind of error saying it couldn't show bookmarks until a security software was fixed. I have no clue what this means or why FF would simply "lose" bookmarks.

Is this a known issue?

Thank you!

---

### Post by #&amp;thj^% on 2017-12-26
Without knowing the specific error.(in the future please note/quote the exact error seen)
The Reset/Refresh Firefox feature can fix many issues by restoring Firefox to its factory default state while saving your essential information. 
**Note: This will cause you to lose any Extensions, Open websites, and some Preferences.**

To Reset Firefox do the following:

    1.Go to Firefox > Help > Troubleshooting Information.
    2.Click the "Refresh Firefox" button.
    Firefox will close and reset. After Firefox is done, it will show a window with the information that is imported. Click Finish.
    Firefox will open with all factory defaults applied. 
[U]Your bookmarks and other personal data are stored in the Firefox profile folder and won't be affected by an uninstall and (re)install, but make sure that "remove personal data" is NOT selected when you uninstall Firefox.
[/U]
If you keep having problems then try also creating a new profile.

More on resetting Firefox: [https://support.mozilla.org/en-US/kb/refresh-firefox-reset-add-ons-and-settings](https://support.mozilla.org/en-US/kb/refresh-firefox-reset-add-ons-and-settings)

---

### Post by vasa1 on 2017-12-26
> **1fallen said:**
> Without knowing the specific error.(in the future please note/quote the exact error seen) ...
+1
> **sterator said:**
> ...
Is this a known issue?
...
I haven't seen similar complaints.

---

### Post by QIII on 2017-12-26
I haven't seen that either, but the "security update" thing may be a clue.  Was your version of FF updated recently?

I'm on my cell, so I can't drill down to be sure of the path, but would you please look for /home/<your username>/.mozilla/firefox (I think that's right) and see if you find a directory with some random character string and open that up?  We can see if you favorites are still there.

---

### Post by sterator on 2017-12-26
OK..Here is the error - I quit FF (just got home) and started it again.

It appears immediately beneath the top chrome (where the bookmarks bar would be) and is a band of red with a "Learn More" button to the right.

The error text says:

```
the bookmarks and history system will not be functional because one of Firefox's files is in use by another application. Some security software can cause this problem.
```

Note: I have no 'security software,' unless the 16.04 installer and Ubuntu updates put it there.

When the "Learn More" button is clicked, you're taken to [this page]("https://support.mozilla.org/en-US/kb/fix-bookmarks-and-history-will-not-be-functional?redirectlocale=en-US&as=u&redirectslug=The+bookmarks+and+history+system+will+not+be+functional&utm_source=inproduct").

I think I'll try these instructions first. I don't get why the places.sqlite file suddenly couldn't be found.

Thank you!

---

### Post by sterator on 2017-12-27
OK..in dealing with another issue I'd been having - rsync copying my backup to the boot volume - I seemed to have fixed the bookmarks issue.

I deleted the backup which had filled my boot volume, restarted the machine and the next time I launched FF, the bookmarks were back.

Thank you for your help!

:)

---

