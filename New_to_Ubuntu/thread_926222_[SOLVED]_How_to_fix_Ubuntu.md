---
title: "[SOLVED] How to fix Ubuntu"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by jon555 on 2008-09-21
I installed Xp on my second partition, after that Ubuntu on first partition doesn't boots up any more.  Any sugestions? Ubuntu partition is intact.

I tried
sudo grub
   find /boot/grub/stage1
and got 
 (hd0,5)
then 
grub> root (hd0,1)   and got  Error 27: Unrecognized command
also tried
 grub> root (hd0,5)  and got the same Error 27: Unrecognized command

---

### Post by Tatty on 2008-09-21
This should sort you out

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by OutOfReach on 2008-09-21
Hmm Windows most likely overwrote the MBR you'll need to re-setup GRUB.

EDIT: Tatty beat me to it.

---

### Post by jon555 on 2008-09-21
First two steps worked
but then came error 
sudo grub
find /boot/grub/stage1
(hd0,5)
grub> root (hd0,1) and got Error 27: Unrecognized command
also tried
grub> root (hd0,5) and got the same Error 27: Unrecognized command

---

### Post by Tatty on 2008-09-21
Thats odd, try again but be very careful to make sure that you type it exactly correct:

```
root (hd0,5)
```

---

### Post by MasterNetra on 2008-09-21
Windows absolutely overrided grub. Thats why you install Windows first then Ubuntu. You will have to re-setup grub. If you aren't able to then that obviously leaves ya with one choice.

---

### Post by jon555 on 2008-09-22
```
root (hd0,5)
```[/QUOTE]
After that nothing happens, just empty line.

---

### Post by Tatty on 2008-09-22
That should have worked, I dont think it is supposed to give any output.

Now just continue with the final command of the guide:
```
setup (hd0)
```

---

### Post by jon555 on 2008-09-22
[QUOTE=]That obviously leaves ya with one choice.[/QUOTE]
But can I somehow reinstall Ubuntu without replacing home folder. It would be nice to see repair option on live cd in future. Ok, so [COLOR="DarkGreen"]**Thnx**[/COLOR] for help

---

### Post by Tatty on 2008-09-22
> **jon555 said:**
> But can I somehow reinstall Ubuntu without replacing home folder. It would be nice to see repair option on live cd in future. Ok, so [COLOR="DarkGreen"]**Thnx**[/COLOR] for help

You can if you have /home on a separate partition.  I recall hearing plans to allow you to re-install ubuntu whilst preserving /home even on the same partition, I dont know if they have been implemented yet though.

---

### Post by jon555 on 2008-09-22
Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 12: Invalid device requested

---

### Post by kansasnoob on 2008-09-22
Just one more time, from your live CD:
In the desktop, open terminal (Applications -> Accessories -> Terminal).

```
sudo grub
```

```
root (hd0,5)
```

```
setup (hd0)
```

```
quit
```

Please use "copy-n-paste" so you're sure to get it right.

---

### Post by jon555 on 2008-09-22
[QUOTE=]

```
setup (hd0)
```
Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 12: Invalid device requested

---

### Post by kansasnoob on 2008-09-22
I'm stumped:confused:

I wish either Meierfra or Caljohnsmith would see this, they can both run circles around me with boot problems!

Could you rename this thread to include "grub" in the title, or repost something like How to fix Ubuntu Grub, can't boot!

I'll bet they're stumbling right past this post.

---

### Post by bumanie on 2008-09-22
Post the output of > sudo fdisk -l from live cd. It is possible that windows, having been installed after ubuntu has ended up in a logical partition and thus won't boot.

---

### Post by jon555 on 2008-09-22
Time is up and I need working comp now. I'm reinstalling.Thanks to all!

---

### Post by jon555 on 2008-09-23
> **kansasnoob said:**
> Just one more time, from your live CD:
In the desktop, open terminal (Applications -> Accessories -> Terminal).

```
sudo grub
```

```
root (hd0,5)
```

```
setup (hd0)
```

```
quit
```

Please use "copy-n-paste" so you're sure to get it right.

   
I did it again. This time it worked. Thnx

---

