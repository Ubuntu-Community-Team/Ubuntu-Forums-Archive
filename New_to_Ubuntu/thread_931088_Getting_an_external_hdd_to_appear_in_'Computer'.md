---
title: "Getting an external hdd to appear in 'Computer'"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by m_ad on 2008-09-26
Does anyone have a quick tutorial on how to get mounted disks in 'Computer'? 

And for some reason, when I apply a new icon theme, the icons for the devices in Computer don't change (only the DVD-RW drive and hard drive), they remain at gnomes default grey icons. Is there a fix for this without editing the icons manually?

---

### Post by nightcrawler27 on 2008-09-26
If you type "mount" at the console, does your external drive show up as mounted under a path that starts with "/media"? Is this an external USB drive? Even though the usb drive may be a hard disk, it is considered removable media and may not appear in the file browser if not mounted in the right location.

As for your icons, not every theme will replace all your icons. If you know a theme contains replacements for all the icons, then maybe there is an issue. Try one of them manually first to ensure that you can actually change them, and then change it back again.

Nightcrawler27

---

### Post by m_ad on 2008-09-26
It's actually a networked drive that I'm sharing from another computer on the same network (smbfs).. I wonder if this is going to be a difficult task. :confused:

```
//192.168.0.11/WD My Book on /mnt/wd-mybook type cifs (rw,mand)
```

That's the drive, I knew it was in /mnt, but I don't know how to change this stuff to put it in Computer. It would just be easier for me to navigate to it through Computer rather than /mnt. Any suggestions would be appreciated.

---

### Post by m_ad on 2008-09-27
Anyone have a solution?

---

### Post by nightcrawler27 on 2008-09-30
How about this:

When you click "Computer", there is a button on the left side under the "Back" arrow...it changes between button and text-based location bar. Click it so you get the text-based bar. Now type /mnt/wd-mybook in the bar, and you will get your drive. Now click "Bookmarks->Add Bookmark" and a folder icon with the name of the drive should show up under your bookmarks on the left hand side of the file browser. Anytime you need access to that drive just click on the bookmark.

Is this what you are looking for?

Nightcrawler27


> **m_ad said:**
> It's actually a networked drive that I'm sharing from another computer on the same network (smbfs).. I wonder if this is going to be a difficult task. :confused:

```
//192.168.0.11/WD My Book on /mnt/wd-mybook type cifs (rw,mand)
```

That's the drive, I knew it was in /mnt, but I don't know how to change this stuff to put it in Computer. It would just be easier for me to navigate to it through Computer rather than /mnt. Any suggestions would be appreciated.

---

