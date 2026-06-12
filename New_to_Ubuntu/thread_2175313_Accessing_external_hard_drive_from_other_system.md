---
title: "Accessing external hard drive from other system"
date: 2013-09-18
forum: New to Ubuntu
---

### Post by qwerty3656 on 2013-09-18
The short version is I had a ubuntu server that has become inaccessable.  My plan is to wipe it out and start over.  I had some files backed-up to an external hard-drive (formated ext4).  Before I wipe out my server, I want to be able to confirm that I can get to these files on the external hard drive.  I've tempoaraliy installed ubuntu 12.04 desktop onto another computer and plugged that drive in.  The main folders show up, but when I try to acces them I get "The folder contents could not be displayed.  You do on have the permmissions necessary to view the contents".  When I click on permissions it says that the owner is "1002 - user #1002" (I have no idea what that is) and that since I am not the owner, I cannot change these permissions.

---

### Post by Bucky Ball on 2013-09-18
Give this a shot. What file manager are you using? Let's say nautilus. Open a terminal and:

```
gksudo nautilus
```

(Replace 'nautilus' with 'thunar' or 'pcmanfm' or whatever you are using.)

Now you have permission. Move what you want where you want then *close nautilus straight away*. Don't go fooling around in there and forget what you came for. **Just exit**. Reason: *you are running nautilus as root* and you can do some real damage. ;)

Good luck.

---

### Post by dankojoffrey on 2013-09-18
try accessing as root... I use gnome commander... [HTML]sudo gnome-commander[/HTML]

---

### Post by Bucky Ball on 2013-09-18
> **dankojoffrey said:**
> try accessing as root... I use gnome commander... [HTML]sudo gnome-commander[/HTML]

As I said, more or less. Open file manager as root, don't really need gnome-commander, but it looks interesting. Incidentally, you should run *any* GUI with gksudo if you are running it as root from a terminal, *not* sudo.

Also, 12.04 LTS uses Unity, not Gnome, so will gnome-commander work? Not sure, I don't use either. I suspect it will probably just drag in the gnome dependencies and make itself work. Unsure though. ;)

---

### Post by dankojoffrey on 2013-09-18
> **Bucky Ball said:**
> As I said, more or less. Open file manager as root, don't really need gnome-commander, but it looks interesting. Incidentally, you should run *any* GUI with gksudo if you are running it as root from a terminal, *not* sudo.

Also, 12.04 LTS uses Unity, not Gnome, so will gnome-commander work? Not sure, I don't use either. I suspect it will probably just drag in the gnome dependencies and make itself work. Unsure though. ;)

yeah, it's gonna work. I use gnome commander in Unity every day... you can even start it as normal user and then go to "File->Start GNOME Commander As Root" it is gonna ask you for root password and you've got root privileges... 

But if you don't wanna install gnome commander, just use Nautilus with gksudo like Bucky Ball suggested...

cheers...

---

### Post by whitesmith on 2013-09-18
Do as **Bucky Ball** suggested to get your files moved. Later you should do (from a terminal) ```
sudo chown -R your_username:your_username *.*
``` in whatever subdirectory the files reside, in order to gain ownership of your own files. Warning: close that gksudo window ASAP or you can destroy everything unintentionally.

---

### Post by qwerty3656 on 2013-09-18
On the main menu when I click on the "home" folder, there is a section at the top left titled "Devices" and one of the accessable devices is the usb drive.  However when I go into terminal and type "gksudo nautilus", there is no "Devices" option on the left.  I cannot find the usb drive within that window.

Found it under /media - I swear it was not there the first time I looked there.

---

### Post by Bucky Ball on 2013-09-18
> **qwerty3656 said:**
> Found it under /media - I swear it was not there the first time I looked there.

Excellent. Move what needs to be moved and close nautilus. ;)

---

