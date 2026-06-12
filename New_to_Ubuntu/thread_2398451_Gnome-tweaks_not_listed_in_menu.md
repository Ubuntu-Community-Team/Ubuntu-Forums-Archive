---
title: "Gnome-tweaks not listed in menu"
date: 2018-08-12
forum: New to Ubuntu
---

### Post by Norm24 on 2018-08-12
After installing gnome-tweaks its nowhere to be found in the menu,the only way to launch is through terminal which is a PIA.Would love to have a desktop icon and/or launcher in the panel.

---

### Post by Frogs Hair on 2018-08-12
If you are using Ubuntu Mate you would install mate-tweak.

```
sudo apt install mate-tweak
```

---

### Post by deadflowr on 2018-08-12
Find the .desktop file in /usr/share/applications and remove the line that says OnlyShowIn.
Then it should show everywhere.
Though if you're using mate(I'm guessing) I doubt it offers anything that mate does not already do, (and what mate would already do better for mate)

This would be the file ftr: /usr/share/applications/org.gnome.tweaks.desktop

ninja'd

---

### Post by ubantunovice2 on 2018-08-12
> **deadflowr said:**
> Find the desktop file in /usr/share/applications and remove the line that says OnlyShowIn.
Then it should show everywhere.

I'm not the OP. I hope it is OK to join the thread.
I'm a newbie and trying to learn by reading threads. I am using (in virtual box) Ubuntu 18.04.1 which comes with gnome.

following your above instructions, I went to /usr/share/applications (both in "files" and in "Double Commander") and there is no "desktop" file to modify. Would that file have another name or be located elsewhere?

---

### Post by deadflowr on 2018-08-12
> **ubantunovice2 said:**
> I'm not the OP. I hope it is OK to join the thread.
I'm a newbie and trying to learn by reading threads. I am using (in virtual box) Ubuntu 18.04.1 which comes with gnome.

following your above instructions, I went to /usr/share/applications (both in "files" and in "Double Commander") and there is no "desktop" file to modify. Would that file have another name or be located elsewhere?

It's not a default app so you need to install it yourself.

---

### Post by ubantunovice2 on 2018-08-12
You mean 'desktop' is a separate app?
Edit: OK I get it.

---

### Post by deadflowr on 2018-08-12
> **ubantunovice2 said:**
> You mean 'desktop' is a separate app?

No, I mean gnome tweaks is not installed by default.
.desktop refers to the file type:
[https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles]("https://help.ubuntu.com/community/UnityLaunchersAndDesktopFiles")
(The link says unity launchers but can be apply to launchers and desktop files in general)

Opps, I meant .desktop in the original post.
Fixed

---

### Post by Dennis N on 2018-08-12
If you have Ubuntu and you want the Tweaks tool, just open the "Activities" screen, type "Tweak Tool" (just "Tweak" is probably enough) in the search box at the top, and in the "Ubuntu Software" section below that, you should see Gnome Tweak Tool among the suggested packages. Just click on that to install from Ubuntu Software. Job done.

---

