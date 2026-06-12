---
title: "Firefox toolbars empty after upgrade to 8.10"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by freesitebuilder on 2008-10-30
I've upgraded from 8.04 to 8.10, apparently with no problems. But my Firefox toolbars are mainly empty.

The bookmarks are all there, if I choose Bookmarks > Bookmarks toolbar folder everything is there but they aren't displaying on the toolbar.

The throbber appears in the middle of the bar rather than at the right-hand side, and none of the extension icons show - although they're all there. Oddly the extensions that put their icons on the status bar at the bottom are displaying OK.

I've tried to attach a screenshot - if it works!

I've looked at the preferences, and about:config but I haven't made any changes to the config. Haven't seen any other reports of this problem here - so shall I just take the well-trodden route of removing all extensions to see if one of them is the culprit?

I know my video driver has been replaced for this update, as the release notes mention it (Nvidia GeForce) so I don't know if that's a factor.

TIA

---

### Post by cairnzi on 2008-10-30
this probably wont be of any useful help but i have just upgraded today to 8.10 and had no firefox problems,but i have an integrated intel graphics chip,so possibly it could be your graphics card driver... but cannot see why it would wipe your toolbar, hopefully someone will be able to sort it but you could also just go to the sites again and put them in your toolbar. :popcorn:

---

### Post by kneewax on 2008-10-30
is it similar to this problem?  [http://ubuntuforums.org/showthread.php?p=6067505#post6067505](http://ubuntuforums.org/showthread.php?p=6067505#post6067505)

---

### Post by stormtrooprdave on 2008-10-30
I had the same problem after I upgraded. read this thread:

[http://ubuntuforums.org/showthread.php?t=960230]("http://ubuntuforums.org/showthread.php?t=960230")

Basically the Ubuntu Firefox Modifications add on was screwing things up, even though it was fine in Hardy.  Disable it to fix it, I don't know why it happens though.

---

### Post by illepic on 2008-10-31
I'm having the same problem with the del.icio.us toolbar, screenshot attached.  I tried the post that stormtrooprdave suggested, but it did not work.

---

### Post by illepic on 2008-10-31
> **illepic said:**
> I'm having the same problem with the del.icio.us toolbar, screenshot attached.  I tried the post that stormtrooprdave suggested, but it did not work.

Ok, I fixed this.  Here is how I did it.

Close all instances of firefox down and then run

```
firefox -safe-mode
```

in a terminal. Use the checkboxes to disable all addons and reset toolbar positions.  Re-enable your addons but DO NOT re-enable the Ubuntu Firefox addon.

---

### Post by lariosa42 on 2008-11-01
Thanks!  That worked for me.  My google search bar is back in the toolbar, and my modifications to the buttons stays fixed each time.

---

### Post by mejpark on 2009-03-26
Thanks for sharing your solution illepic; this solved the problem for me. The toolbar vanished after automatic update to Delicious Bookmarks addon. 

I should point out that users who utilise multiple Firefox profiles (like myself) can 'repair' a specific profile using the -P option with safe mode:

```
firefox -P **ProfileName** -safe-mode
```

Hope this helps!

---

### Post by natrik on 2009-04-16
My bookmarks toolbar was still there, and working, but I wound up missing my ad-block-plus icon (in the not-default location menubar-toolbar) as well as my forecastbar, and my web developer toolbar, and my text formatting toolbar (all are extensions).  Additionally, in the Customize box (right click on menubar, choose "customize") all the icons from add-ons / extensions were missing.  NoScript, AdBlock Plus, Greasemonkey, Download Helper, etc.

**[size=3][color=#00aa00]I disabled the Ubuntu Firefox Modifications 0.6 add-on, and I got everything back.[/color][/size]** 

Safe mode did not do it for me.  It just disabled everything I was already missing.   Even restoring defaults did not work.  I only tried disabling all plugins, and resetting toolbar defaults.  That did nothing until I disabled the Ubuntu Firefox Modifications 0.6.

-- Nate

---

