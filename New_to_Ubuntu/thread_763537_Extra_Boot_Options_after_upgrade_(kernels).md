---
title: "Extra Boot Options after upgrade (kernels?)"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by kam.samji on 2008-04-23
Hi. I have just upgraded to 8.04 and everything is working perfectly. The only gripe i have is that on the boot up screen (I have dual boot) I now have 4 sets (2 options in each set) of Ubuntu boot options and one set of windows.

Out of the 2 sets of ubuntu, the number for one of the ends in "..22-14" and the other one ends in "..26-16" or somethin like that. How can i get rid of (clean up) the set i don't use any more. Each one has a corresponding Recovery Mode too.

They are both connected to 8.04 but one of them clearly looks like the 'old' 7.10.

I hope this make sense to someone...

Thanks,

Kam

---

### Post by joshrobinson on 2008-04-23
you can remove your old kernels, the one that ends in 16 is the newest, so you can remove any others by using synaptic, or you can edit

/boot/grub/menu.lst

and remove the portions you dont need

---

### Post by kam.samji on 2008-04-23
Sorry to sound stoopid, but when you say 'using Synaptic', what do I look for?

Or if I go for the other option, does that mean browse for that'those folders? Then, what do i exactly delete?

Thanks

---

### Post by Michael.Godawski on 2008-04-23
To change your menu.lst run this in terminal.

```
gksudo gedit /boot/grub/menu.lst
```
You can also post the content of the menu.lst so that we can say what to delete and what not.

```
cat /boot/grub/menu.lst
```

---

### Post by joshrobinson on 2008-04-23
> **kam.samji said:**
> Sorry to sound stoopid, but when you say 'using Synaptic', what do I look for?

Or if I go for the other option, does that mean browse for that'those folders? Then, what do i exactly delete?

Thanks

you know how to use synaptic package manager right?
system > administration > synaptic package manager

click search and type linux-image
you will see a bunch of results, the ones with the green boxes are the intalled ones, you want to keep the one ending in 16, the others you can click the green box and click mark for removal, when your done click apply

---

### Post by kam.samji on 2008-04-23
sweet. Thanks guys. Will try those this evening.

Cheers.

(ps - 8.04 rocks!! My advanced visuals work now, which never did before, and it's so pleasing to the eye!)

---

