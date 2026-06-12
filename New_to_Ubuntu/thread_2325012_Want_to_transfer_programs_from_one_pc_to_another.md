---
title: "Want to transfer programs from one pc to another"
date: 2016-05-18
forum: New to Ubuntu
---

### Post by rdb3 on 2016-05-18
I have two desktops with Ubuntu 14.04.

I have a few programs customized on pc A that I would like to transfer to pc B  using a USB thumb drive.

Is this easily doable with Ubuntu?  Where would I start?

Thanks in advance.

---

### Post by howefield on 2016-05-18
Many applications config files wil be found in the /home folder, so it would simply be a matter of copying and pasting from pc A into pc B.

Which applications are you looking at ?

---

### Post by sudodus on 2016-05-18
If your Ubuntu operating system uses only built-in free drivers (no proprietary drivers, for example for graphics and wifi), the whole operating system is portable. It means that you can move the internal drive and it works in another computer (if that computer works without proprietary drivers). Some hardware needs installing/uninstalling proprietary drivers, but it is not too difficult.

So you can copy only the /home folder, as described by *howefield*, or you can copy or ***clone*** the whole system to another hard disk drive, solid state drive or USB pendrive (if the target drive is big enough).

If you intend to use both computers in the same local network, you should at least give them different names in the network, to make it easier to identify them.

---

### Post by rdb3 on 2016-05-18
One pc is showing .config  under home.
The other pc doesn't show .config under home. Is it hidden someplace?

I basically want to experiment doing this.  I have a couple of apps that I can try... Chromium, Kodi, Slimjet.

I'm limited to what I can do with a small usb drive (16 GB).

---

### Post by ajgreeny on 2016-05-18
On the machine that does not show the .config folder in home just hit Ctrl+H and it should appear; any file or folder with a name starting with a . is normally hidden.

You can the simply copy the folder from one machine to the other along with any other hidden folders that you want.  The chromium configuration info is contained in ~/.config/chromium but I do not know about slimjet or kodi; just search and I suspect you will find them somewhere in the home folder.

Not all configuration folders are subfolders of .config so look elsewhere as well.

---

### Post by rdb3 on 2016-05-18
> **ajgreeny said:**
> On the machine that does not show the .config folder in home just hit Ctrl+H and it should appear; any file or folder with a name starting with a . is normally hidden.

You can the simply copy the folder from one machine to the other along with any other hidden folders that you want.  The chromium configuration info is contained in ~/.config/chromium but I do not know about slimjet or kodi; just search and I suspect you will find them somewhere in the home folder.

Not all configuration folders are subfolders of .config so look elsewhere as well.

That worked.  Thanks!

---

### Post by ajgreeny on 2016-05-18
Great!

If this is now solved for you please mark as SOLVED from the Thread Tools menu up-top.

---

