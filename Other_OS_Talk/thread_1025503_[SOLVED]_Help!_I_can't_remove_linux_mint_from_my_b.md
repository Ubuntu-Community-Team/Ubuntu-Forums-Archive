---
title: "[SOLVED] Help! I can't remove linux mint from my bootloader!"
date: 2008-12-30
forum: Other OS Talk
---

### Post by Fzang on 2008-12-30
I tried installing mint4win, the linux mint equivalent of wubi. Unfortunatly, this thing didn't want to boot after install so I uninstalled it and then removed all the files...

...But, linux mint still stands as an entry in my vista bootloader, even after I've done
```
bootrec.exe /fixboot
bootrec.exe /fixmbr
```

Windows boots just fine but having to wait another 5 seconds just to see the "linux mint" boot entry is pretty annoying

How can I remove it completely?

---

### Post by gettinoriginal on 2008-12-30
You may want to wait for another response, but if you hit escape during boot splash, you should have the option to "e" edit.  Not sure, as I am running ubuntu, so do not know what your boot splash looks like.  :P

---

### Post by Fzang on 2008-12-30
I don't think there's an "e" option. Wubi installs the boot entry into vista's bootloader instead of installing GRUB

I can check it though

---

### Post by Fzang on 2008-12-30
Alright! Fixed it by looking around on google, finding some various commands and chaining them together with some logic and simple commands,

Turned out like this:
[IMG]http://i42.tinypic.com/2uhnuqd.png[/IMG]

---

### Post by gettinoriginal on 2008-12-30
Congrats, glad you found the answer, please go to tools and mark this as solved :P

---

