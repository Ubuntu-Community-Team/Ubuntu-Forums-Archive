---
title: "Multiple Kernels"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by Sub101 on 2008-05-04
I now have 3 kernels in my grub startup. Is it worth me keeping all these or should I get rid of one of them. If so how could I do this?

I do know that its best to keep the previous working kernel, i'm just concerned that to much space is being taken up.

---

### Post by Aurora@FleetBuzz on 2008-05-04
What version are you using?  Did you upgrade?  If so, it's normal to have the kernels from the previous distribution.  You can uninstall those if you like, or modify your menu.lst file so that they don't show when you boot.

---

### Post by Sub101 on 2008-05-04
I have .14 .16 and .17. I thought I should keep .16 in case I have problems with .17 but want to uninstall/delete .14. How do I do that? I can remove from grub, but it remains on my pc.

---

### Post by Sub101 on 2008-05-04
Sorry, just figured it out, I thought it would be something complicated.

```
 sudo apt-get autoremove 
```

Thanks for your help

---

### Post by Aurora@FleetBuzz on 2008-05-04
Open the synaptic manager and search for linux-image.  You should see it there after the search. Mark it for "uninstall" and hit "apply".

It might be a bit safer to just edit it out of your menu.lst with a # preceeding the entry.  Then re-boot.  That way, you won't see it when grub boots.

---

### Post by Aurora@FleetBuzz on 2008-05-04
> **Sub101 said:**
> Sorry, just figured it out, I thought it would be something complicated.


If it works, suggest marking this thread "Solved".

---

### Post by Sub101 on 2008-05-04
I don't actually know how? sorry

---

### Post by aheckler on 2008-05-04
I don't think you can yet, since the forums just went through an upgrade.

---

### Post by Malta paul on 2008-05-04
You can use ALT-F2 then type 'gksudo nautilus' (now be careful you are now in ROOT)
Go to Places>Home>Up>Up Open the boot folder>Grub Then open menu.lst.
Save a backup first. then edit the menu list to Kernel 2.6.24-17. Its not a bad idea to only edit the normal boot items first, so that if you mess it up you still have the recovery mode intact, then if all ok change that as well.

---

