---
title: "Can I access Linux Swap partition via window? Please help!"
date: 2018-05-10
forum: New to Ubuntu
---

### Post by bunsuke on 2018-05-10
I'm a new rookie in ubuntu and new to linux partition. Now I have the linux harddisk that contains all of my website data!. And I'm going to move the whole data to a new harddisk. I acces the linux partition via Window by DiskInternals Linux Reader program, I can access the /home partition but canntot acces the /sda2 partition(it is a linnnux swap partition ). Are there anyway to access it? Thank you! (sorry for my english)

---

### Post by QIII on 2018-05-10
Hello!

There should be nothing of value in the swap partition when the system is not running.  And it is a partition type that is foreign to Windows.  Even in Linux, you can't just navigate to your swap partition and view what's there in any simple, meaningful way.

Swap is somewhat similar to the PageFile (virtual memory) in Windows, except that where Windows attempts to keep a copy of everything in RAM in the PageFile, Linux uses swap to "supplement" RAM when usage is high.

Whatever you have stored on your Linux drive won't be in swap.  I don't even have a swap partition and haven't for years.  It was pointless when I went over 8GB of memory and is senseless with 128GB.  Ubuntu uses a swap file in its recent releases, so a swap partition is really unnecessary.

---

### Post by bunsuke on 2018-05-10
> **QIII said:**
> Hello!

There should be nothing of value in the swap partition when the system is not running.  And it is a partition type that is foreign to Windows.

Swap is somewhat similar to the PageFile (virtual memory) in Windows, except that where Windows attempts to keep a copy of everything in RAM in the PageFile, Linux uses swap to "supplement" RAM when usage is high.

Whatever you have stored on your Linux drive won't be in swap.  I don't even have a swap partition and haven't for years.  It was pointless when I went over 8GB of memory and is senseless with 128GB.  Ubuntu uses a swap file in its recent releases, so a swap partition is really unnecessary.

[COLOR=#000000]Thank you so much QIII now it's all clear for me.[/COLOR]

---

