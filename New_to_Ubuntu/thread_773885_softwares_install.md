---
title: "softwares install"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by irshan on 2008-04-29
1 pls help me that the locations of all software which are downloaded.if i downloaded the software i dont know where it is store. 

2. I install ubuntu after windows xp but now it is defaultly showing ununtu first and then windows so pls giv idea how make first default as windows in OS menu

---

### Post by tompickles on 2008-04-29
[change order of booting]("https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS")

if you download the software from firefox, it may still show you in the downloads window, cant remember where exactly... if your using the repositories, then i dont really know, but you shouldnt really have to worry?

---

### Post by tliotis on 2008-04-29
i think that default of firefox is on desktop.If it is not , then go to firefox tools and see the path of downloads that is save them

---

### Post by may15100 on 2008-04-29
I just installed Ubuntu yesterday in WinXP and it works well now.
I have the same problem with you that the default OS is not WinXP , but I don't care~~~  I like Ubuntu , what is first and what is second do nothing to me. So be calm about the order and have fun~~~

---

### Post by davidgypsy on 2008-04-29
> **irshan said:**
> 
2. I install ubuntu after windows xp but now it is defaultly showing ununtu first and then windows so pls giv idea how make first default as windows in OS menu

It's possible to change this, but involves editing the grub menu.list file, which always comes with a risk and may leave you unable to boot at all... might be better to just hit the down arrow button when you want to boot windows. If you want to do it anyway, just search it on this forum, it is explained in a few places.

---

### Post by pro003 on 2008-04-29
you have to edit this file and set default OS

```
sudo gedit /boot/grub/menu.lst
```

---

### Post by tompickles on 2008-04-29
> **davidgypsy said:**
> It's possible to change this, but involves editing the grub menu.list file, which always comes with a risk and may leave you unable to boot at all... might be better to just hit the down arrow button when you want to boot windows. If you want to do it anyway, just search it on this forum, it is explained in a few places.

the wiki link in my post above walks you through it - as long as your carefull, all you have to do is hange 1 number - (0 to 4) from my remembering.

---

