---
title: "Remove icons from Desktop"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by PT.Linn.A on 2008-08-20
Last night my kids asked me to load some pictures on my computer from the SD Memory cards out of their cameras. Being Dad, I of course complied.  :)

However, I am now left with two icons on my Desktop which I cannot remove.

The icons are in the shape of the SD Memory cards and when I try and drag them to the Trash it tells me "Cannot move items to Trash, do you want to delete them immediately?" I click "Delete" and nothing changes.

When I right click on the icons the option to Move to Trash is not available.

Any ideas as to how I can delete these icons from my Desktop?

I have already transfered the pics into the appropriate folder and no longer require the icons.

Phoenix

---

### Post by linuxguymarshall on 2008-08-20
type 
```
cd ~/Desktop
```

then 

> dir  

If you dont see the files then they are not there. This is a bug I encounter. Just reboot and they shall begone

---

### Post by perlluver on 2008-08-20
If the above does not work, press alt+f2, then type in gconf-editor, go to the nautilus tab, and click on, desktop, then click on show media, or drives.  That should get rid of them too.

---

### Post by lswest on 2008-08-20
right-click the icon, and choose "unmount", else find out the path to the SD cards (I assume that it IS still there? otherwise insert the SD card again, or try without first, up to you), and do ```
sudo umount /media/*path to sd card*/
```changing "path to sd card" with the actual path.  If I misunderstood something, could you please post a screenshot?

---

### Post by PT.Linn.A on 2008-08-20
Great tips and information people!  :D  I appreciate the knowledge, and the quick responses.

**linuxguymarshall** I used your tip and it worked. Checked the dir and they were not there. So, I rebooted. And, they were gone. Wonderful!

Thanks to all who took the time to teach this Noob some tips.

---

### Post by SakJur on 2008-08-20
> **linuxguymarshall said:**
> type 
```
cd ~/Desktop
```

then 

  

If you dont see the files then they are not there. This is a bug I encounter. Just reboot and they shall begone

I would recommend you to write **ls** instead of dir, Dir is colourless, ls lists with colours... **ls -la** shows hidden files in a smart list...

---

### Post by PT.Linn.A on 2008-08-20
Wow. OK, so I tried the ls -la and wound up finding:

total 8
drwxr-xr-x  2 phoenix phoenix 4096 2008-08-18 11:11 .
drwxr-xr-x 49 phoenix phoenix 4096 2008-08-20 10:30 ..

Does this mean that I am still sporting the stuff I don't want? If so, how do I get rid of it completely? Especially since I no longer see the icons on the Desktop, I assumed they were gone.

Confused here.

---

