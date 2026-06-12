---
title: "Customized options in /boot/grub/menu.lst disappear after updates"
date: 2006-07-29
forum: Programming Talk
---

### Post by jcc on 2006-07-29
Following myriad online docs to the letter, I've lovingly researched and added kernel options to the boot menu -- vga for actually usable ttys, power management options so I can actually use standby, etc. -- only to have them silently disappear in the wake of an automatic security update (... from all entries, not just shuffled down to make room for a new kernel entry).

Um, how do I prevent this?

---

### Post by Ares Drake on 2006-07-29
move your customized boot / kernel options above the following lines in grubs menu.lst: ;) 


# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

---

