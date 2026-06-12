---
title: "Roll back kernel?"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by TalioGladius on 2008-05-29
Fresh 8.04 install today and got it set up perfectly.  Then I finished installing updates, which included a kernel update that bumped me from 2.6.24-16 to 2.6.24-17.

After a reboot all apps keep hanging.  They would respond for about 5 seconds and then stop responding for 10-15 seconds, which makes this thing unusable.  Then it decided to make all my fonts freaking huge.

2.6.24-16 is still in the grub menu, and when booting to it everything is fine.  So how do I remove all the -17 stuff?

---

### Post by Ripfox on 2008-05-29
I *think* you can remove it through Synaptic Package Manager...

---

### Post by TalioGladius on 2008-05-29
> **Ripfox said:**
> I *think* you can remove it through Synaptic Package Manager...I did a search in there for 2.6.24-17 and it returned a bunch of stuff, but I don't want to go removing stuff when I have no clue what it's for.

---

### Post by drs305 on 2008-05-29
If you just want to use the previous kernel, you can change the default in menu.lst or change it via startupmanager. System, Administration, StartUp-Manager, Boot Options, and change the Default Operating system back to 16. 
If you don't see StartUp-Manager on the menu,
```
sudo aptitude install startupmanager
```

---

### Post by bumanie on 2008-05-29
You can remove it via synaptic or you can edit /boot/grub/menu.lst by placing # in front of the kernel entries you no longer want. This doesn't remove the kernel, but will stop it getting listed as an option at boot.

---

### Post by TalioGladius on 2008-05-29
> **drs305 said:**
> If you just want to use the previous kernel, you can change the default in menu.lst or change it via startupmanager. System, Administration, StartUp-Manager, Boot Options, and change the Default Operating system back to 16. 
If you don't see StartUp-Manager on the menu,
```
sudo aptitude install startupmanager
```Thanks, that's cool to have regardless.


I still think I want to get rid of it.  Fonts on some web sites in firefox are still huge.

---

### Post by TalioGladius on 2008-05-29
bump

---

### Post by drs305 on 2008-05-29
I'm not sure what you want to do next. If you change to 16 via the startup manager or editing menu list, you can verify which kernel you are running after boot with:
```
uname -a
```

You can go into synaptic, do a search for linux-image-2.6.24-17 and remove anything that is installed with that name. You can also do another search for 2.6.24-17 and remove those entries as well.

But if it concerns you, by changing the default boot into 16 you are not using any of the 17 resources, so you can just leave them on the machine if you want to until another kernel is published.

---

### Post by meierfra. on 2008-05-29
> I still think I want to get rid of it. Fonts on some web sites in firefox are still huge.

If you are booting  from the old kernel, the new kernel is not used at all. So  you can can just remove anything related to the new kernel.
But this will not make any difference in the performance of your computer.

The fonts on firefox must be due  to some other update.

---

### Post by TalioGladius on 2008-05-30
> **meierfra. said:**
> If you are booting  from the old kernel, the new kernel is not used at all. So  you can can just remove anything related to the new kernel.
But this will not make any difference in the performance of your computer.

The fonts on firefox must be due  to some other update.Sadly, I doubt there's a way to find it and remove it.

---

