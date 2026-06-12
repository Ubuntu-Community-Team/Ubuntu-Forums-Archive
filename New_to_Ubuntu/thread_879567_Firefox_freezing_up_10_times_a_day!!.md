---
title: "Firefox freezing up 10 times a day!!"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by t0p on 2008-08-04
Since the last firefox update, it has become buggy as all heck!!  Specifically, it freezes up very frequently: if I do something data-intensive, like watch streamed video, it gets very temperamental very quickly; but even if I'm just browsing basic websites like this one, it'll likely seize up on me after a couple of hours.

It's getting pretty frustrating. I'm force-quitting the browser several times a day.  It was okay until just recently.  Anyone got any ideas?

---

### Post by silkstone on 2008-08-04
It sounds like a Flash issue.

Look through this tutorial - especially the section near the end on Troubleshooting Adobe Flash Player - and see if that helps.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by t0p on 2008-08-04
> **silkstone said:**
> It sounds like a Flash issue.

Look through this tutorial - especially the section near the end on Troubleshooting Adobe Flash Player - and see if that helps.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Yesss, flash issue sounds about right.  Another pesky bit of bad behavior firefox has got up to is sometimes not playing flash.  For instance, earlier on this morning I watch the Nick Cave video at [www.youtube.com/watch?v=7kV5XkBQsKU]("http://www.youtube.com/watch?v=7kV5XkBQsKU").  I just went back there: and instead of getting the usual little black screen, it was just blank white.  Also, I watched Part1 of *Harry Potter and the Prisoner of Azkeban* at [www.surfthechannel.com/]("http://www.surfthechannel.com/") last night.  Now, the flash video picture won't appear, it's just blank white.

I'm going to read that tutorial you linked to.  But in the meantime, any other suggestions most welcome!

**EDIT:** Right, I have purged flashplugin-nonfree and a couple of other packages that may apparently have been interfering with it, and reinstalled flashplugin-nonfree, as per troubleshooting tip 1 in the linked tutorial.  Now I have to wait and see if this has improved the situation.

**RE-EDIT:** Oh nooo!! This has undone a fix I had to do to make sound work in flash vids!! Damn, now I gotta track down the tutorial I used before for the sound issue and do it all again.  Grrr!!

---

### Post by darrenn on 2008-08-04
I would switch to Opera until you find a solution to this problem.

---

### Post by t0p on 2008-08-04
> **darrenn said:**
> I would switch to Opera until you find a solution to this problem.

Hmmm... replacing firefox is something I've (briefly) considered, of course, but I am very wary of taking that route.  In the past I've tried Opera, Konqueror and Microsoft Explorer - and hated 'em all.  Firefox is the only browser I've tried that I like.

I realise you're only suggesting a temporary break from firefox.  And maybe I'll have to do that.  But I'm rather hoping I can sort this problem quickly, so I don't have to use another browser.

But, if I do have to use a different browser: anyone suggest a good one?  Something Free, preferably (note I wrote Free, not free).

---

### Post by sharks on 2008-08-04
open firefox from terminal using this command:
firefox

and when it freezes up, if there are any error in terminal post it up here.

---

### Post by t0p on 2008-08-04
> **sharks said:**
> open firefox from terminal using this command:
firefox

and when it freezes up, if there are any error in terminal post it up here.

Okay, I did like you said, and when firefox froze and I had to force-quit it, this is the error message I got in the terminal:

> t0p@ubunty:~$ firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

(npviewer.bin:14309): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:14309): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:14309): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:14309): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:14309): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:14309): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:14332): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:14332): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:14332): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:14332): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:14332): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:14332): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:14340): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:14340): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:14340): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:14340): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:14340): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:14340): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:14340): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:14340): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:14340): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:14340): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:14340): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:14340): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:14340): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:14340): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:14340): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:14340): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:14340): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:14340): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:14340): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:14340): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:14340): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed
*** NSPlugin Wrapper *** ERROR: NPP_Destroy() wait for reply: Message timeout
Killed


So... what's it mean?

---

### Post by sharks on 2008-08-04
dnt know about it. file a bug at launchpad.net and post the eroor quote.

---

### Post by silkstone on 2008-08-04
I don't know what's causing it, but npviewer is Firefox's Flash handler.

It may be that an add-on is causing the problem, so you could try running FF in safe mode.

firefox -safe-mode

[http://support.mozilla.com/en-US/kb/Safe+Mode](http://support.mozilla.com/en-US/kb/Safe+Mode)

---

### Post by sharks on 2008-08-04
> **silkstone said:**
> i don't know what's causing it, but npviewer is firefox's flash handler.

It may be that an add-on is causing the problem, so you could try running ff in safe mode.

Firefox -safe-mode

[http://support.mozilla.com/en-us/kb/safe+mode](http://support.mozilla.com/en-us/kb/safe+mode)


+1

---

### Post by t0p on 2008-08-04
Okay, so from reading the tutorial at [ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683") I have identified a *possible* reason for the problems I'm having.

It may be caused by **libflashsupport** and **nspluginwrapper ** interfering with the flash player.  If you look at the error message I quoted in an earlier post, you'll see the penultimate line mentions "NSPlugin Wrapper", which kind of backs up this theory.

Unfortunately, I installed libflashsupport and nspluginwrapper as part of [**this fix**]("http://ubuntuforums.org/showthread.php?p=4928900") for no audio when playing video files.  If I remove those packages, I lose the audio again.

What a perplexing predicament.... :confused:

> **silkstone said:**
> I don't know what's causing it, but npviewer is Firefox's Flash handler.

It may be that an add-on is causing the problem, so you could try running FF in safe mode.

firefox -safe-mode


I'll try it out.

---

### Post by mc4100 on 2008-08-04
You could try upgrading to the Flash 10 beta ... it fixes the sound issues (libflashsupport isn't needed).

---

### Post by philinux on 2008-08-04
> **mc4100 said:**
> You could try upgrading to the Flash 10 beta ... it fixes the sound issues (libflashsupport isn't needed).

Yes but some sites notably BBC check the version and reject the beta.

---

### Post by rhenium3 on 2008-08-06
I am having this problem too... interestingly enough, when I quit force firefox it will not start up again and I have to restart the computer. For some reason my shut down button does not work after firefox freezes and I have to shut it down manually.  Is this connected to the firefox problem or is something different?

---

