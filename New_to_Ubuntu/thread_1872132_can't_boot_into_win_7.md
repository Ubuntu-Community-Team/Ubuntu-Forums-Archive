---
title: "can't boot into win 7"
date: 2011-10-30
forum: New to Ubuntu
---

### Post by zabergan on 2011-10-30
I'm dual-booting Win 7 and Ubuntu 11.10 on an acer 5742. Before I upgraded from Ubuntu 11.04 to 11.10 I had no problems loading Win 7 but since the upgrade I've had nothing but problems. First when I restarted ,the computer booted straight into ubuntu with no option of choosing an OS so I had to switch off then switch on again to get the menu with a list of OS systems. Now it goes straight into ubuntu all time. I know I haven't accidently deleted win 7 because I checked with gparted and it's on /dev/sda3.

---

### Post by pierreyy on 2011-10-30
hey.... maybe you should update your grub...


   ```
 sudo update-grub 
```

---

### Post by Mark Phelps on 2011-10-31
When you updated, it overwrote the old GRUB config file -- removing any entries to any other OSs.  You have to do the "sudo update-grub" command mentioned in the previous post to generate a new menu with those entries.

---

