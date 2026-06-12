---
title: "[SOLVED] Folders open in package installer instead of nautilus"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by zorblek on 2008-11-02
I just upgraded to Intrepid, and I'm having a bizarre problem. For some reason, when I try to open a folder from the Places menu or using Launchy, it opens in gdebi-gtk instead of nautilus (which naturally produces an error message). If I attempt to open a folder from the desktop, it opens normally in nautilus.

Also archive files now open in the package installer instead of the archive manager. This happens regardless of where they are opened from.

Any idea of what might be causing this and how I could fix it?

Thanks!

---

### Post by brandoncolorado on 2008-11-02
> **zorblek said:**
> I just upgraded to Intrepid, and I'm having a bizarre problem. For some reason, when I try to open a folder from the Places menu or using Launchy, it opens in gdebi-gtk instead of nautilus (which naturally produces an error message). If I attempt to open a folder from the desktop, it opens normally in nautilus.

Also archive files now open in the package installer instead of the archive manager. This happens regardless of where they are opened from.

Any idea of what might be causing this and how I could fix it?

Thanks!

That is strange.  Lets see if you have the same entry here:

Hit the key-combo of ALT-F2 and enter in gksudo nautilus--this will open nautilus with root permissions.

Go to the /usr/share/applications directory, right-click the file called 'Home Folder' and go to Properties.

Click the Launcher tab and on the line where the command ---what does it say?

---

### Post by brandoncolorado on 2008-11-02
Nevermind, see this bug:

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/260492](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/260492)



Simple workaround

Right click -> Open with -> custom command -> nautilus

repeat for all folders

now should open folders from Places in Nautilus

---

### Post by zorblek on 2008-11-03
That bug does sound like what I am experiencing, but the workaround does not work for me. When I use the "open with application" option it works that time, but the next time I try to open it, it uses the package installer.

(BTW, the command listed for Home Folder in /usr/share/applications is "nautilus --no-desktop".)

---

### Post by Sand Lee on 2008-11-03
The fix for this is to right click on a folder->Properties->Open With-> then Remove Synaptic and select "Open Folder" (or Nautilus)

---

### Post by zorblek on 2008-11-03
> **Sand Lee said:**
> The fix for this is to right click on a folder->Properties->Open With-> then Remove Synaptic and select "Open Folder" (or Nautilus)

I'm not sure what you mean by Remove Synaptic...

---

### Post by zorblek on 2008-11-03
Wait, never mind. I figured it out. It worked!

Thank you!

---

