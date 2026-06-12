---
title: "Helpful programs"
date: 2016-05-30
forum: New to Ubuntu
---

### Post by JoAnn_Donaldson on 2016-05-30
I am new to Ubuntu 16.04 and have MousePad installed. How or where can I get a list of commands?

---

### Post by JoAnn_Donaldson on 2016-05-30
GEdit is already installed, so where does it reside? I want to make an Desktop link or .desk file.

---

### Post by DuckHook on 2016-05-31
Hi JoAnn,

I link to many excellent guides and tutorials in my signature, esp *Resources for Newcomers*. There are a lot of resources there, so if you feel a little dazed by the extent and the variety, please feel free to ask again back on this thread.

---

### Post by Bill Vincenti on 2016-05-31
> **JoAnn_Donaldson said:**
> GEdit is already installed, so where does it reside? I want to make an Desktop link or .desk file.

The executable resides in:  /usr/bin 
however, you can open a terminal and type gedit at the prompt ```
$ gedit
``` it will open the Gedit text editor (same as/with mousepad) then navigate to the file you want to edit. 
You can also create files with gedit and mousepad (*bash scripts <filename.sh> etc and so on...*).
While in terminal type in ```
$ man gedit
``` to open the gedit instruction manual, same with mousepad, also ```
$ gedit --help
```

---

### Post by vasa1 on 2016-05-31
@Bill, please don't advise users to run 
```
sudo gedit
```

Care needs to be taken when running graphical programs with elevated privileges. New users, in particular, can damage their systems by accidental misuse of elevated privileges.

I think the use of *pkexec* is recommended in Ubuntu. Some other flavors allow the use of *gksudo*.

---

### Post by Bill Vincenti on 2016-05-31
Thank you vasa1, understood.

---

### Post by DuckHook on 2016-05-31
> **JoAnn_Donaldson said:**
> GEdit is already installed, so where does it reside? I want to make an Desktop link or .desk file.You can find any application in Ubuntu from the dash. Instructions as follows:

[https://help.ubuntu.com/lts/ubuntu-help/unity-dash-intro.html](https://help.ubuntu.com/lts/ubuntu-help/unity-dash-intro.html)

Once running, you can lock any application to the Launcher by right clicking its thumbnail in the Launcher and choosing "Lock to Launcher". Instructions as follows:

[https://help.ubuntu.com/16.04/ubuntu-help/unity-launcher-intro.html](https://help.ubuntu.com/16.04/ubuntu-help/unity-launcher-intro.html)

By locking an application to the Launcher, it is always available, and this is meant to do away with keeping apps on the desktop. However, if you still would like desktop links to apps, the instructions are as follows:

[https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles](https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles)

The process can be quite involved and intimidating for new users. Apparently, the developers expected users to prefer squeaky clean desktops with the introduction of Unity, so the process for creating desktop links to programs is pretty arcane. Directories and documents are easy to create, but not so for apps.

---

### Post by JoAnn_Donaldson on 2016-05-31
The Gedit that came with Ubuntu 16.04 does not look the Gedit that is in the tutorials.

---

### Post by DuckHook on 2016-05-31
> **JoAnn_Donaldson said:**
> The Gedit that came with Ubuntu 16.04 does not look the Gedit that is in the tutorials.True.

The tutorials are written for older versions of Gedit. Ubuntu 16.04 is using a newer version and tutorial writers have not had time to change their tutorials to reflect the new version yet. Some will never get around to doing so. This is an ongoing issue throughout the Linux-sphere because apps continue to change and documentation always lags behind. However, I have found that tutorials are often close enough that I can learn most of the functionality. I learn the rest through exploration and experimentation.

---

### Post by CantankRus on 2016-05-31
Some applications will show a generic name in the dash rather than the application name.
eg
gedit shows as **Text Editor**

You can drag and drop applications from the dash into a text editor window to view the x-desktop launcher
where you can see the actual start command on the "**Exec=**" line.

---

### Post by JoAnn_Donaldson on 2016-06-01
OK...I now have a GEdit.desktop file in the Desktop folder and an link on the Desktop and it fires up GEdit. Is there a folder that contains different icons that one can use to jazz up these links?

---

### Post by CantankRus on 2016-06-01
> **JoAnn_Donaldson said:**
> OK...I now have a GEdit.desktop file in the Desktop folder and an link on the Desktop and it fires up GEdit. Is there a folder that contains different icons that one can use to jazz up these links?
If it's a .desktop file, right click on it **Properties > Permissions** and make executable.
Should now show the default icon.

You should really get out of the habit of using your desktop for shortcuts.
Shortcuts on the unity launcher are always visible even when the desktop is not.

---

### Post by DuckHook on 2016-06-02
> **CantankRus said:**
> ...You should really get out of the habit of using your desktop for shortcuts.
Shortcuts on the unity launcher are always visible even when the desktop is not.+1

I suspect OP is asking for location of icon files in general:

```
/usr/share/icons/
```

---

### Post by vasa1 on 2016-06-02
And some are in /usr/share/pixmaps

---

