---
title: "How do I access my c: drive"
date: 2012-02-17
forum: New to Ubuntu
---

### Post by Roody4U on 2012-02-17
Hello, All! I want to know if there is anyway I can access folders on my c: drive (windows 7) in ubuntu. I am using Ubuntu 11.10 and have just installed it. The installation was done using the wubi installer. I was wondering if there's a simple way I can access my c: from the home folder to bring over things such as pictures, music, etc... Without having to boot into windows and use a usb stick.


Thanks

---

### Post by forrestcupp on 2012-02-17
I don't have any experience with WUBI, but if you open up Nautilus, your C: drive should appear under the Devices section on the left side. It won't be called C: drive; it will be named whatever that drive is named. Mine is called Gateway because I have a Gateway computer, and that's what they named my C: drive. It may not be mounted, but as soon as you click it, it will automatically mount and you can access it.

But I don't know what things are like with WUBI. It may not show up the same way.

---

### Post by 3rdalbum on 2012-02-17
> **forrestcupp said:**
> I don't have any experience with WUBI, but if you open up Nautilus, your C: drive should appear under the Devices section on the left side. It won't be called C: drive; it will be named whatever that drive is named. Mine is called Gateway because I have a Gateway computer, and that's what they named my C: drive. It may not be mounted, but as soon as you click it, it will automatically mount and you can access it.

But I don't know what things are like with WUBI. It may not show up the same way.

No, for Wubi the Windows drive is at /host - that's the "host" folder in "Filesystem".

---

### Post by Roody4U on 2012-02-17
Thanks. That's the info I was looking for. I found all of the files I was looking for in the "host folder"


Thanks for the help

Christian

---

