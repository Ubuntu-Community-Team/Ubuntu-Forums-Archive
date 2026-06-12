---
title: "Issue: Programs not fully uninstalling?"
date: 2018-10-27
forum: New to Ubuntu
---

### Post by iMba@$o72+L on 2018-10-27
Hi all, I recently switched from Windows to Linux for the first time ever, and I ran into what looks like a problem with uninstalling programs.

I installed the Dolphin file manager and then later uninstalled it. I believe I uninstalled it from within Ubuntu Software itself. However, the icon for Dolphin still remains in the "Show Applications" overlay (see screenshot), despite Dolphin appearing to be uninstalled and no longer visible in my list of programs (also see screenshot).

Any help or explanation on this? Thank you.

[I am using Ubuntu 18.10 on a freshly-built desktop using a Ryzen 3 2200g CPU].

---

### Post by oldrocker99 on 2018-10-27
You can try this:
```
sudo apt purge dolphin
```

---

### Post by iMba@$o72+L on 2018-10-28
> **oldrocker99 said:**
> You can try this:
sudo apt purge dolphin

Unfortunately, that didn't seem to work. I receive the following message:

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package Dolphin"

The Dolphin icon is still present the "Show Applications" overlay... really weird.

---

### Post by deadflowr on 2018-10-28
There's a snap version so see if that's it with
```
snap list
```
if it is run
```
sudo snap remove dolphin
```

see: 
```
snap help
```
for more on snap commands.

And then to fully clean it out without any leftover cruft in Files go to the snap folder, and remove (right click delete or move to trash) the dolphin folder.

---

### Post by iMba@$o72+L on 2018-10-29
> **deadflowr said:**
> There's a snap version so see if that's it with
```
snap list
```
if it is run
```
sudo snap remove dolphin
```

see: 
```
snap help
```
for more on snap commands.

And then to fully clean it out without any leftover cruft in Files go to the snap folder, and remove (right click delete or move to trash) the dolphin folder.

Nope, it does not appear in the snap list. Can I submit this as a bug report?

---

### Post by oldos2er on 2018-10-29
> **gateless-gate said:**
> Unfortunately, that didn't seem to work. I receive the following message:

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package Dolphin"

The Dolphin icon is still present the "Show Applications" overlay... really weird.

Please try a lower case "d" as```
sudo apt purge dolphin
```

---

### Post by iMba@$o72+L on 2018-10-29
> **oldos2er said:**
> Please try a lower case "d" as```
sudo apt purge dolphin
```

Nope, doesn't work either (see attached screenshot). "Dolphin" still appearing in the Show Applications overlay.

---

### Post by deadflowr on 2018-10-29
You already uninstalled it through Ubuntu Software, so it's understandable that it would not show in the snap list.
But always worth a look anyway...
Did you look in the snap folder for a dolphin entry, just in case?

Also look in the hidden folder (ctrl + h to toggle viewing hidden files/folders) .local > share > applications.

The ~/.local/share/applications folder is where user set launchers are, typically.

---

### Post by mc4man on 2018-10-29
You certainly installed the snap version of Dolphin (1st listed in Ubuntu software

So while you removed it a .desktop file was not removed, maybe a bug in the dolphin or kde snaps.
The file is /var/lib/snapd/desktop/applications/dolphin_org.kde.dolphin.desktop

To remove and no longer see in the app overview run this command in a terminal, strongly suggest you copy & paste..
```
sudo rm  /var/lib/snapd/desktop/applications/dolphin_org.kde.dolphin.desktop
```

Edit: seems to affect all KDE snaps..

---

### Post by iMba@$o72+L on 2018-10-30
> **mc4man said:**
> You certainly installed the snap version of Dolphin (1st listed in Ubuntu software

So while you removed it a .desktop file was not removed, maybe a bug in the dolphin or kde snaps.
The file is /var/lib/snapd/desktop/applications/dolphin_org.kde.dolphin.desktop

To remove and no longer see in the app overview run this command in a terminal, strongly suggest you copy & paste..
```
sudo rm  /var/lib/snapd/desktop/applications/dolphin_org.kde.dolphin.desktop
```

Edit: seems to affect all KDE snaps..

Seems to work!! Thank you mc4man. I copy/pasted that line into the terminal and voila, the icon is now removed from Show Applications.

---

### Post by iMba@$o72+L on 2018-10-30
> **deadflowr said:**
> You already uninstalled it through Ubuntu Software, so it's understandable that it would not show in the snap list.
But always worth a look anyway...
Did you look in the snap folder for a dolphin entry, just in case?

Also look in the hidden folder (ctrl + h to toggle viewing hidden files/folders) .local > share > applications.

The ~/.local/share/applications folder is where user set launchers are, typically.

Before I tried mc4man's command, I also tried this to no avail. Didn't see anything named dolphin in the hidden applications folder. Thank you though, as I wasn't previously aware of the ctrl+h toggle!

---

