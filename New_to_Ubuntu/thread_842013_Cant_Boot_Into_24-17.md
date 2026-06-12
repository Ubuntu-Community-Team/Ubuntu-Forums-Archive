---
title: "Cant Boot Into 24-17"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by Spoken on 2008-06-26
i cant boot into the latest kernel for some reason, if i just turn on my computer and let it try to boot normally, when it gets to the Ubuntu logo loading screen, the loading bar just continuously goes back and forth with no attempt to load.  in order to get my computer to work i have to hit esc when its loading grub and pick a previous kernel that worked.  

what do i need to do in order to get my latest kernel to work?

---

### Post by Dylock on 2008-06-26
When your booting, hit ESC to get into the GRUB menu. Select the entry for the kernel you want to get working and press 'e' to edit the entry. Go do the kernel line and press 'e' again. You should see the word splash. Delete this and press enter, then press b to boot. (I'm doing this off memory so be sure to read the screen for instructions)

Essentially what this is doing is not passing in the splash boot flag so we can see what's going on during your boot. There is another flag called quiet that you can remove as well to have additional information display. 

These changes to your GRUB entry will not be permanent but only apply for this boot. Hopefully we might see something that is going wrong. Let us know how it goes.

---

### Post by Spoken on 2008-06-27
k give me a few mins and i will let you know what happens.

---

