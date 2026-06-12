---
title: "Safely removing hard drive?"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by catherineb23 on 2008-09-01
Hi,

It's probably obvious, but I can't see the button that allows me to safely remove my hard drive. Help!

---

### Post by porchrat on 2008-09-01
if you're talking about an external HDD then all you need is to right click on the icon for the drive (on your desktop or the one inside your "places") then click "unmount", the icon on your desktop should then disappear and you should then be able to remove it without a problem.

---

### Post by benerivo on 2008-09-01
If you mean a usb disk, then you should be able to open a file manager window and right click on its entry on the main panel (at the left) and choose unmount. I don't know why there is not a 'safely remove' option in the ubuntu system tray, as there is in windows -- it might be useful for many people.

---

### Post by porchrat on 2008-09-01
although "safely remove" is a just a more user-friendly word for "unmount" anyway.

---

### Post by catherineb23 on 2008-09-01
Thanks a lot. I found the unmount function easily. Though it has been unmounted the drive is still appearing in the places menu and the drive's light is still glowing - on other systems it turns off entirely when "safely removed". Is there perhaps an additional step which I am missing out on?

---

### Post by porchrat on 2008-09-01
Nope...you see it in "places" because ubuntu knows the drive exists and the light is on because the usb (or eSATA) is still supplying the drive with power, however the drive is not "mounted" so it isn't being read by ubuntu, and is therefore safe to remove

---

### Post by benerivo on 2008-09-01
porchrat is right. Also, you should see the name of the disk in the 'Places' panel change whenever it is mounted / unmounted.

---

### Post by catherineb23 on 2008-09-01
Great. Thanks!

---

### Post by porchrat on 2008-09-01
Glad to be of service...TO THE BATCAVE!!!!

---

