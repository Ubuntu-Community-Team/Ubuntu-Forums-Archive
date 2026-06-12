---
title: "Dolphin won't open folder in place"
date: 2012-11-02
forum: New to Ubuntu
---

### Post by Ralph L on 2012-11-02
I am trying out kubuntu in this case oneiric.  When I try to open a folder by double clicking it, nothing happens.  If I right click the folder it asks me whether I want to open in a tab or a new window.  What I want to do is open the folder in the current window.  That is the way nautilus works.  Is there any way to configure dolphin so a simple double click will open the folder in place--like nautilus?

---

### Post by dniMretsaM on 2012-11-02
Check the settings in Settings -> Configure Dolphin... -> Navigation -> Single/Double-click to open files and folders. Try changing it, restart Dolphin, and see if it works correctly. Also, what version of Dolphin and the KDE SC are you using?

---

### Post by Ralph L on 2012-11-02
Thanks for responding.
I tried resetting the single/double click setting.  I can't get dolphin to open a folder in place with either setting.

Dolphin is version 1.7

---

### Post by Kevin McCready on 2012-11-02
You might want to reboot the system after you apply the change and see if that works.

---

### Post by whatthefunk on 2012-11-02
It sounds like there may be something wrong with your Dolphin.  Just to check, when you double click on a folder, nothing happens?  And when you right click, you only get two menu options, opening in a new tab or opening in a new window?  Definitely not standard.  Open the Dolphin settings and click the Defaults button.  Does that do anything?

---

### Post by Ralph L on 2012-11-02
1.  I tried restarting from scratch.  Double click still did nothing.
2.  I opened the "Settings" and clicked defaults.  Still nothing.
3.  Regarding right-clicking on a folder, I didn't mean to imply that there were only two items in the pull down.  There several.  However, using the right-click and opening the folder in a new tab, or in a new window, were the only ways I could open a folder.
4.  Usion muon package manager I reinstalled dolphin.  However, I did not reinstall all its dependencies.  Still didn't work.

I haven't installed updates for a while.  I will try that.

---

### Post by Kevin McCready on 2012-11-02
or you could uninstall dolphin (could be a problem is dolphin is default file manager) and reinstall.

---

### Post by Zorael on 2012-11-09
It may be that something else has registered itself as the default handler for the 'directory' file association ("mimetype"), so when you're double-clicking a folder it tries to start that program instead. Did you at any point install some other file manager? And perhaps uninstalled it afterwards?

If you open up System Settings and head into Default Applications -> File Manager; is Dolphin the selected choice?

Elsewise there is a file you could open up in a text editor and manually remove any such file association; **~/.local/share/applications/mimeapps.list**. It defines all file associations that you have changed (from the defaults) for your user. Try commenting out any entries there that start with '**inode/directory**', by prepending an octhorpe (**#**) to the very beginning of the line. That should make it fall back to the default settings.

---

### Post by Ralph L on 2012-11-09
I did an upgrade to 12.10 and everything worked.

---

