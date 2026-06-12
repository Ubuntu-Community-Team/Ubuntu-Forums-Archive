---
title: "Other Users"
date: 2023-04-26
forum: New to Ubuntu
---

### Post by daveyb415 on 2023-04-26
Usinge: Dell Inspiron 5537 / memory 8GB / Intel® Core™ i7-4500U CPU @ 1.80GHz × 4 / Mesa Intel® HD Graphics 4400 (HSW GT2) / Harddrive 1TB / OS: Ubuntu 22.04.2 LTS / 64-bit / GNOME ver. 42.5

When I restart or power off, the dialog box shows "other users currently logged in " and list my u/name.  This is a new phenom and does not happen on my other machine.  Thoughts?

Thx

---

### Post by chris0nlinux on 2023-04-26
This usually happens to me when I switch desktop environments without logging out, but by switching users. Make sure you are using the GDM Login Manager and you logout properly.

---

### Post by daveyb415 on 2023-04-26
To be sure I understand, Instead of lightdm make  gdm3 the default manager?

---

### Post by chris0nlinux on 2023-04-26
You can make gdm3 the default login manager by:

If you have already installed it:```
sudo dpkg-reconfigure gdm
```

If you have not installed it:```
sudo apt install gdm
```

Let me know if this helps.

---

### Post by daveyb415 on 2023-04-26
Yes in deed.  Those damn other users are gone...
THx for the assistance - peAce

---

### Post by mIk3_08 on 2023-04-26
> **daveyb415 said:**
> Yes in deed.  Those damn other users are gone...
THx for the assistance - peAce

On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

