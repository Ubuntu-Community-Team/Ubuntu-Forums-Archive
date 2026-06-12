---
title: "[SOLVED] Installing WoW (CD Mount Issue)"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by Bonzzai on 2008-06-25
I've been trying to figure out how to install World of Warcraft on my computer. I've downloaded Wine, but when copying over the files to my harddrive, I noticed there's not a 'install.exe'. Only a Mac folder, and 'Installer Tome 1.mpq', all the way to six or so. I've read that I should type in the following command to 'unhide' the file.

```
 sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/cdrom0/
```
Unfortunately, I get this error.

```
 mount: special device /dev/cdrom does not exist 
```

I've tried simply going into the CD directory and pressing ctrl+h to 'unhide', but the install.exe file does not show up.

---

### Post by hyper_ch on 2008-06-25
did you have windows before?

---

### Post by Bonzzai on 2008-06-25
> **hyper_ch said:**
> did you have windows before?

Quite a while ago, yes. Back in January, I believe.

---

### Post by hyper_ch on 2008-06-25
so you have no running windows anymore?

Easiest way (at least was for me) was to install wow in windows (maybe even in a virtual machine) and then just copy the whole WoW folder over to linux using this guide here: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) (alternative 1)

---

### Post by Bonzzai on 2008-06-25
> **hyper_ch said:**
> so you have no running windows anymore?

Easiest way (at least was for me) was to install wow in windows (maybe even in a virtual machine) and then just copy the whole WoW folder over to linux using this guide here: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) (alternative 1)

Unfortunately I don't have Windows installed on the machine at all, sorry. >.<
I would re-install it, I just don't have a disc, hehe.

**Edit**

I might just download the entire game. That should work, right? I'd just rather use the DVD since I have it in front of me, hahah.

---

### Post by B61zz13 on 2008-06-25
Wait, are you trying to install WoW through an ISO file?

---

### Post by Bonzzai on 2008-06-25
> **B61zz13 said:**
> Wait, are you trying to install WoW through an ISO file?

No, I'm following [this](https://help.ubuntu.com/community/WorldofWarcraft) guide. The 'installer.exe' file doesn't show up for me, so I tried following the command I typed earlier. My main problem is I don't know what to type for my CDrom drive :S

---

### Post by B61zz13 on 2008-06-25
Oh ok, so you're installing from a DVD.  Well, why don't you first try to mount the DVD and if the directory to the WoW installer shows up, then search for Installer.exe and go to your terminal and type:
wine "/location/of/Installer.exe" (without quotation marks).  See if that works.

---

### Post by Bonzzai on 2008-06-25
I can actually install *from* the DVD? I was getting the impression I needed to copy my files to a folder on my harddrive.

P.S. - [This is all I see](http://i29.tinypic.com/2yphwsj.jpg) without doing a search in the folder for 'install'. When I do that, two other locked files show up. 'InstallerLauncher.pef' and 'InstallerLauncher.rsrc'.

---

### Post by B61zz13 on 2008-06-25
Now that you know where your WoW DVD installer directory is, try this in the terminal:

sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/WoW DVD/

But just wondering: is this DVD for installing WoW on a Mac?

---

### Post by Bonzzai on 2008-06-25
> **B61zz13 said:**
> Now that you know where your WoW DVD installer directory is, try this in the terminal:

sudo mount -t iso9660 -o ro,unhide /dev/cdrom /media/WoW DVD/

But just wondering: is this DVD for installing WoW on a Mac?

It's for both Windows *and* Mac. I'm just getting a message saying I'm doing it wrong. I tried to unmount the drive to type in the command again, but I'm getting nothing. Just downloading the game is sounding like a great plan, hahah.

---

### Post by B61zz13 on 2008-06-25
Wait, wait! Before you go download it, just do this little stunt:
Press Ctrl + H on your WoW DVD installer directory and see if the hidden files show up! :)

---

### Post by Bonzzai on 2008-06-25
> **B61zz13 said:**
> Wait, wait! Before you go download it, just do this little stunt:
Press Ctrl + H on your WoW DVD installer directory and see if the hidden files show up! :)

I did that, but unfortunately I only got a '.Trashes' directory and .VolumeIcons.icns. :(

But thanks so much for sticking with me through it. n.n
xD

---

