---
title: "How to edit program start code in Unity?"
date: 2015-07-03
forum: New to Ubuntu
---

### Post by Geoffrey_Arndt on 2015-07-03
Unlike KDE there is no gui editor to modify program startup commands (aka menu editor).   

I have kgpg installed . . . gpg actually runs fine, does the job, but to get the gui to display I enter the following via cli:   "kgpg %u -k" (less quotes).

I'd like to add that string to the gui command launcher, but am not seeing an intuitive way to do it in Unity (running 15.04).

Appreciate any tips.

Here's a thumbnail of current setup:

[IMG]http://i.imgur.com/oSYYcPMl.png[/IMG]

note:  if needed acct small pic, use "ctrl+" to enlarge enough to read . .

---

### Post by monkeybrain20122 on 2015-07-03
You can create a bash script with whatever command and run it at log in by adding the script to  startup applications

---

### Post by ajgreeny on 2015-07-03
I suspect you may be able to edit as root, the **kgpg.desktop** (or whatever it is called) file in /usr/share/applications.

You can also install **alacarte** which will edit your menu items, but as I do not use unity, I don't honestly know if that also edits the dash launcher items in the same way that it does old style menu items.

---

### Post by monkeybrain20122 on 2015-07-03
Are you asking how to edit .desktop file or make commands autostart? Maybe I misunderstood. But to edit .desktop you just open it with a text editor and change the exec line.

---

### Post by Geoffrey_Arndt on 2015-07-03
What I'd like to do is similar to editing the properties dialog in a typical menu editor (kde & alacarte, etc.).   I'm not intending to have kgpg to be auto started at login - - but when I do start the app via clicking the kgpg icon via the dash or via the launcher, I prefer to have the gui launch and not run in a non-existent Unity panel (the app wants to minimize to kde panel by default).

Here is a pic of the properties dialog window for kgpg . . found in /usr/share/applications/kde4/KGpg

[img]http://i.imgur.com/GDoOpSal.png[/img]

I'd like to edit that dialog window via root and have the changes stick (I want the startup command to be:  kgpg %u -k (the -k is missing and without it, the gui can only be opened via CLI)

Using sudo gedit /usr/share/applications/kde4/KGpg will bring up a blank config file (so I don't really know what actual file contains the startup code as listed above.

---

### Post by monkeybrain20122 on 2015-07-03
The desktop file should be /usr/share/applications/kde4/KGpg.desktop or something like that (end with .desktop)

---

### Post by sandyd on 2015-07-03
Can be done with
```

sudo dpkg-divert --add --rename --divert /usr/share/applications/kde4/kgpg.desktop.orig /usr/share/applications/kde4/kgpg.desktop
sudo cp /usr/share/applications/kde4/kgpg.desktop.orig /usr/share/applications/kde4/kgpg.desktop
sudo -H gedit /usr/share/applications/kde4/kgpg.desktop
```

Explanation:
The dpkg-divert command allows me to rename a file created using dpkg so that when apt-get upgrades the package, your customized desktop file is not replaced. Instead, it is simply installed to kgpg.desktop.orig


Additional:
I don't have Unity, so I cannot test, but copying /usr/share/applications/kde4/kgpg.desktop to ~/.local/share/applications/kgpg.desktop and editing it there may work as well. Mainly, that avoids fiddling with the default kgpg launcher, and prevents you from editing every single user's kgpg launch shortcut. Also allows you to edit the file without sudo since it is owned by you.

Updated: Jul/4/2015:
```

mkdir -p ~/local/share/applications
cp /usr/share/applications/kde4/kgpg.desktop ~/.local/share/applications/kgpg.desktop
gedit ~/.local/share/applications/kgpg.desktop
```

---

### Post by Geoffrey_Arndt on 2015-07-04
Ok, thanks - this PC has too many users and sensitive projects underway,  . . so, I'll add kgpg to a test laptop and try out a couple things including sandyd's interesting idea  - - one minor issue is I still don't see a file resembling "kgpg.desktop".   The desktop extension is missing but I think it's the same file as kgpgrc (found in /home/.kde/share/config/kgpgrc).   Maybe I need to edit that file in /usr as I think the kgpgrc in home is just a link).  

Anyway, I'm out most of next week but will try above after I get caught up.   For now - "thank the Maker" for the CLI!

Thanks again guys! . . I really appreciate the help.

---

