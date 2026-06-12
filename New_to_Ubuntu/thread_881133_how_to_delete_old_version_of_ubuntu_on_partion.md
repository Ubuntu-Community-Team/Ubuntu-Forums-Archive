---
title: "how to delete old version of ubuntu on partion"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by brandon.sifford on 2008-08-05
i just did a fresh install with a cd from 6.10 to 7.10. i do have the hdd partitioned with windows xp. after the install was complete and was at the boot option window it still had the old 6.10 as a option to boot from. i had to do a fresh install cause 6.10 had alot of bugs and would lock up on me. now i need to know how to delete the old 6.10 from the boot option window. i tried the startup manager in 7.10 but didnt work for me. can anyone help me out. im also new to this so please give detailed info. thanks.

---

### Post by Ru$$i@N on 2008-08-05
If you're using Grub as your boot manager, all you need to do is edit the menu.lst

In terminal
```
gksudo gedit /boot/grub/menu.lst
```
I would advise to save a backup file in the same folder, in case something goes wrong and you need the old list.

On the bottom of the file, there'll be entries of systems, just edit out the entries that you don't need. Or post the menu.lst here, if you're not sure which ones to delete 

Once again, that's assuming you're using Grub

---

### Post by brandon.sifford on 2008-08-05
perfect. work out. thanks. now will that automaticly resize my partions for either ubuntu or windows?

---

### Post by loboc on 2008-08-05
No look into gpartd to reclaim your partion space

---

### Post by brandon.sifford on 2008-08-07
great thanks. all worked perfectly.

---

