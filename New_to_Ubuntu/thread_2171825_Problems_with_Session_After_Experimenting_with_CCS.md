---
title: "Problems with Session After Experimenting with CCSM"
date: 2013-09-01
forum: New to Ubuntu
---

### Post by BlacklightHalo on 2013-09-01
I'm having trouble with my Unity session after having installed/experimented with CCSM.

A little background information - I'm using Ubuntu Unity 13.04 on an HP E2 Vision Desktop.

I was trying to enable multiple desktop backgrounds so I could use a different picture with each of three desktops. This was something I liked about KDE (which I wasn't feeling brave enough to install on this computer) and wanted to do with my current installation. I followed the instructions on [this]("http://askubuntu.com/questions/75998/is-it-possible-to-have-a-different-background-for-each-workspace/334224#334224") webpage to do so. It didn't happen. What *did* happen, however, was that my session is 'tweaky' and things are misbehaving. For instance, when I log in to my desktop, the login screen seems to "hang on" even once I'm signed in.

[ATTACH=CONFIG]245906[/ATTACH]

You can see here, where it still appears (but cannot be interacted with) to the immediate right of the panel. Also, Firefox is acting weird. It won't minimize properly - just seems to almost completely minimize/shrink back into its icon in the panel, but there's still a small "ghost" of an image sticking out. After that point, almost everything becomes unresponsive, although the cursor will still move around the page. I managed to get around this by using Fn+f2 (sleep mode) which seems to jar it out of its unresponsive state as it goes to sleep, and then waking the computer back up. Then I can interact with the panel again, but Firefox won't come back properly and tells me it's unresponsive if I right-click and tell it to quit.

I tried resetting compiz icons with

```
reset --unity-icons
```

as described [here]("http://www.liberiangeek.net/2013/04/how-to-restart-unity-and-compiz-in-ubuntu-13-04-raring-ringtail/"), where dconf was already installed. That didn't work. Having decided that further screwing around with compiz and CCSM wasn't a good idea (I'm giving up on CCSM entirely) I uninstalled CCSM with Software Center, as well as the plugins package that I installed with it (not the default ones.) The problem hasn't gone away, even with several reboots.

Will someone please tell me what I can do to reset my session to elimintate these problems, or whatever would be the more practical approach?

Thank you for your time,

-Val

---

### Post by Jonathan Precise on 2013-09-01
> **BlacklightHalo said:**
> I'm having trouble with my Unity session after having installed/experimented with CCSM.

A little background information - I'm using Ubuntu Unity 13.04 on an HP E2 Vision Desktop.

I was trying to enable multiple desktop backgrounds so I could use a different picture with each of three desktops. This was something I liked about KDE (which I wasn't feeling brave enough to install on this computer) and wanted to do with my current installation. I followed the instructions on [this]("http://askubuntu.com/questions/75998/is-it-possible-to-have-a-different-background-for-each-workspace/334224#334224") webpage to do so. It didn't happen. What *did* happen, however, was that my session is 'tweaky' and things are misbehaving. For instance, when I log in to my desktop, the login screen seems to "hang on" even once I'm signed in.

[ATTACH=CONFIG]245906[/ATTACH]

You can see here, where it still appears (but cannot be interacted with) to the immediate right of the panel. Also, Firefox is acting weird. It won't minimize properly - just seems to almost completely minimize/shrink back into its icon in the panel, but there's still a small "ghost" of an image sticking out. After that point, almost everything becomes unresponsive, although the cursor will still move around the page. I managed to get around this by using Fn+f2 (sleep mode) which seems to jar it out of its unresponsive state as it goes to sleep, and then waking the computer back up. Then I can interact with the panel again, but Firefox won't come back properly and tells me it's unresponsive if I right-click and tell it to quit.

I tried resetting compiz icons with

```
reset --unity-icons
```

as described [here]("http://www.liberiangeek.net/2013/04/how-to-restart-unity-and-compiz-in-ubuntu-13-04-raring-ringtail/"), where dconf was already installed. That didn't work. Having decided that further screwing around with compiz and CCSM wasn't a good idea (I'm giving up on CCSM entirely) I uninstalled CCSM with Software Center, as well as the plugins package that I installed with it (not the default ones.) The problem hasn't gone away, even with several reboots.

Will someone please tell me what I can do to reset my session to elimintate these problems, or whatever would be the more practical approach?

Thank you for your time,

-Val

Install the programs again, disable wallpaper, uninstall, untick "show icons", and then run "Files"every time the system starts by typing this into a terminal:

```
gnome-session-properties
```

Add an entry:

> Background
```
nautilus -n
```
Nautilus background.

To enable the different backgrounds, you should install kde (kubuntu):

```
sudo apt-get install kubuntu-desktop
```

That should fix the background and install kde (kubuntu).

---

### Post by BlacklightHalo on 2013-09-01
A question comes to mind - should I have used another (perhaps more general or broad) reset command, instead of "reset --unity-icons"? I'm not going to go typing things into the terminal unless I have some indication of whether or not it's a good idea, here, but resetting things to their defaults would seem to be the logical way to go, here. Anyone?

---

### Post by BlacklightHalo on 2013-09-01
Sorry, just noticed your comment. Should have hit "refresh" first. You say I should run "files" every time the system starts with gnome-session-properties and adding the nautilus -n entry, but doesn't that mean the problem isn't being solved, just sort of "medicated"? I didn't have to go to all that trouble before I did this to start my system correctly. If the problem were being fixed, then shouldn't it go back to the same way it was?

Other question - what about,

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

[This page]("http://askubuntu.com/questions/56313/how-do-i-reset-gnome-to-the-defaults") says that's the way to reset gnome settings to default, as though one had never logged-in. If I were without another permanent solution, could I (safely) use this to put everything back in place (even if it meant setting everything back up all over again)?

*Update - Somehow now the login-screen imagery is gone and things seem to have gone back to minimizing and otherwise behaving themselves correctly. If this continues on and I don't get any more replies, I'm going to close this thread as the earlier stages of Jonathan's solution seem to have worked. If anyone sees this and thinks of something else I need to do or know, please do say something.

---

### Post by wildmanne39 on 2013-09-01
This command ```
rm -rf
```in its present form is very dangerous and should be avoided when possible because if you make one typo and change the path to something that you did not intend you could wipe out your system or lose important files.

---

### Post by BlacklightHalo on 2013-09-02
I see. Well it looks as though everything's back to normal with my computer so I shouldn't need to use it, but I'll remember that for future reference. Thank you.

Where you say "in its present form," do you mean as I have it typed, or as is its current nature/behavior when used?

---

### Post by wildmanne39 on 2013-09-02
Yes as you have typed it, like this it is not so dangerous. ```
rm
```

---

### Post by Jonathan Precise on 2013-09-02
> **BlacklightHalo said:**
> I see. Well it looks as though everything's back to normal with my computer so I shouldn't need to use it, but I'll remember that for future reference. Thank you.

Where you say "in its present form," do you mean as I have it typed, or as is its current nature/behavior when used?

He means as you typed it. However if you run:

```
rm
```

it is (still dangerous, but) not as dangerous as rm -rf.

There is no way to recover that, so I say to:

```
mv *filename* *filename*-old
```

or:

```
mv _folder-name_ _folder-name_-old
```

replacing *filename/*_folder-name_ with the name of the *file* or _folder_.
Both need to be one file/folder at a time.

To restore (if you did it my way,) use:

```
mv **item-name**-old **item-name**
```

replacing **item-name** with the name of the file/folder. Once again, one by one.

---

