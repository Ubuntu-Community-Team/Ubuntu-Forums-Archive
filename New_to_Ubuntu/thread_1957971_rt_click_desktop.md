---
title: "rt click desktop"
date: 2012-04-13
forum: New to Ubuntu
---

### Post by cmcanulty on 2012-04-13
I installed Ubuntu on an old laptop and then rt clicked desktop to check the various options. I picked something wrong and now all the customize desktop options are gone.Can't screenshot as laptop is somewhere else currently.

---

### Post by 2F4U on 2012-04-13
Your post is a bit vague. There is not much customization available by right clicking on the desktop and I am wondering what you did. Maybe its best to wait until you have access to the machine and then make screenshots.

---

### Post by ankspo71 on 2012-04-13
This is a question about Lubuntu, correct? If this is, Do you remember if you right clicked on the desktop, then chose desktop preferences, then chose advanced, then clicked on "Show menus provided by window managers when desktop is clicked"?

That option switches LXDE's desktop menus with Openbox's desktop menus.

If you have, then right click on the desktop then go to System > Desktop Settings and undo the changes.

If you don't have that option in your desktop menu, then the configuration file is kept at ~/.config/pcmanfm/lubuntu/pcmanfm.conf

So open the file in leafpad:
```
leafpad ~/.config/pcmanfm/lubuntu/pcmanfm.conf
```

Then change the line that says:
show_wm_menu=1
to
show_wm_menu=0

then save the file and log out and back in (or restart).

---

### Post by cmcanulty on 2012-04-13
yes that is what I did thanks

---

### Post by cmcanulty on 2012-04-16
well I did that and even after saving file nothing changed. Then I changed it with sudo nautilus and I got the rt click change desktop background back but an empty blue desktop and can't change it when I select change desktop background nothing happens. Also no matter how many times I save the config file the value goes back to 1 after logout.

---

