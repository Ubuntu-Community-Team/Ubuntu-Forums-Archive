---
title: "Updated per Software Center and now I can't boot..."
date: 2013-05-24
forum: New to Ubuntu
---

### Post by uhhhnoakes on 2013-05-24
[COLOR=#000000]Well, I just did an update and now when I boot up it says disconnected from Plymouth and [/COLOR][FONT=Ubuntu Mono]/run/shm not mounted [/FONT][COLOR=#000000]then goes to a black screen. I tried hitting "shift" at boot, then "e" to edit, and placing "nomodeset" + "f10" but it takes me to the same place.... What happened when I updated?[/COLOR]
[COLOR=#000000]
"ctrl+shift+f1" will bring me here from the black screen but i can't do anything... 

[/COLOR][IMG]http://ubuntuforums.org/attachment.php?attachmentid=242960&d=1369387847[/IMG]

---

### Post by lethall1 on 2013-05-24
[COLOR=#000000]Plymouth is a boot loader.
Use documentation [https://wiki.ubuntu.com/Plymouth](https://wiki.ubuntu.com/Plymouth) or [http://forums.linuxmint.com/viewtopic.php?f=189&t=69300](http://forums.linuxmint.com/viewtopic.php?f=189&t=69300) try to reinstall it (may be from recovery mode)[/COLOR]

---

### Post by uhhhnoakes on 2013-05-24
[ATTACH=CONFIG]242971[/ATTACH]

I attempted that process and this is what I see... It worked just fine until I performed that update, was it corrupt, maybe?

> **lethall1 said:**
> [COLOR=#000000]Plymouth is a boot loader.
Use documentation [https://wiki.ubuntu.com/Plymouth](https://wiki.ubuntu.com/Plymouth) or [http://forums.linuxmint.com/viewtopic.php?f=189&t=69300](http://forums.linuxmint.com/viewtopic.php?f=189&t=69300) try to reinstall it (may be from recovery mode)[/COLOR]

---

### Post by uhhhnoakes on 2013-05-24
[ATTACH=CONFIG]242972[/ATTACH]

> sudo apt-add-repository ppa:mefrio-g/plymouthmanagersudo apt-get update
sudo apt-get install plymouth-manager

this did not work since I couldn't connect to the Internet.... I broke ubuntu :/

---

### Post by garaujo on 2013-05-29
you could try to download the package .deb file ( from another machine ) and install via
dpkg -i /path-to-package/package-name.deb
to repair it, unless you've already tried a clean install.

---

