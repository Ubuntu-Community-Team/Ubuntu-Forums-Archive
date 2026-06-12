---
title: "How do I set VLC as my default player in both Ubuntu and Firefox?"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by andrewwg94 on 2008-09-27
ubuntu doesn't give me an option for vlc when i right click on a file. and any ideas with videos in firefox?

---

### Post by Zieg30CT on 2008-09-27
Did you right click on a video or music file, click properties, switch to the Open With tab, and add VLC?

If it still doesn't come up do a quick reboot and see if it does then.

As for videos with firefox, did you install mozilla-plugin-vlc from the repositories?

---

### Post by alienexplorers on 2008-09-27
Go into system --> prefered applications and under the multimedia tab select VLC.  For Mozilla go to synaptic and select the mozilla-plugin-vlc file and load it,

---

### Post by drs305 on 2008-09-27
> **andrewwg94 said:**
> ubuntu doesn't give me an option for vlc when i right click on a file. and any ideas with videos in firefox?

In nautilus, to set a file association you may have to take an extra step. Right click, then select Properties. From there you should be able to select the Open With tab and choose VLC. If you don't see it, you can select "Add", custom command. The command is simply: vlc  (assuming the run command is installed in the default location of /usr/bin )

---

### Post by andrewwg94 on 2008-09-27
thanks for all the replies, everything worked, except every time i click the back button in ff from a page that had quicklime content, Firefox would just suddenly crash and shut down. help please

---

### Post by PierreDeKat on 2008-09-28
I wasn't terribly keen on the VLC plugin, as it lacked all of the controls of the full VLC GUI. Also, I, like you, was having problems with the plugin causing Firefox to crash.

So if you want the full VLC GUI player to handle media links, instead of the plugin, first, uninstall the plugin via Synaptic or command line.

Then open Firefox and go to Edit -> Preferences -> Applications, select a filetype, scroll down to "Use other...". 

This will pull up a file browser dialog.

Select "File System" on the left panel, and browse to /usr/bin/vlc

Go on to the next filetype you want the full VLC GUI player to handle in Firefox, only this time, the file browser dialog should still be cued up in the /usr/bin folder, and you just have to scroll down to "vlc" and select it.

Go on to the next filetype, next, next, next, and then close your Firefox preferences.

From then on, you'll have the full VLC GUI handling your media links in Firefox. And your crashing problem should clear up, as well.

Oh yeah, I highly recommend moving up to VLC version 0.9.2. There's several tutorials on how to do it in Ubuntu, and most include uninstalling whatever version you're currently using and adding

```
deb http://ppa.launchpad.net/c-korn/ubuntu hardy main
```

to your "Third-Party Software" sources. Then you can install 0.9.2, either from command line or from Synaptic.

---

