---
title: "Error 15"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by Viola99 on 2008-07-16
Hullo Experts

I'm very new to Ubuntu - and indeed forums - only been using it a couple of weeks (Gutsy Gibbon code 7.10). This morning I automatically installed some recommended updates (unfortunately I didn't note what) and now when I try to boot I get "Error 15: file is not found". (Same thing with memtest or recovery mode etc.) Have searched the forum but no-one else seems to have had this problem? No idea what I need to do to be able to boot up - any suggestions very welcome

Thanks

---

### Post by aquavitae on 2008-07-16
I think that error is related to a missing kernel file. If you look at the grub command line (press 'e' in the boot loader I think), you'll see a file mentioned there. I can't remember what its usually called in ubuntu, but I think its either something like vmlinuz or linux-2.26.??. Then, if you boot of a live cd, have a look in the folder on your hard drive: /boot/grub. You should see a file of the same name. On the assumption that you won't, you can change it to the correct filename by editing /boot/grub/menu.lst.

Since you're in absolute beginner I assume you have no idea what I'm talking about ;), so boot off your live cd, and post a list of the files in /boot/grub (on your hard drive). Then also post the contents of /boot/grub/menu.lst.

---

### Post by dracayr on 2008-07-16
It's the file that grub needs to mount the filesystem. it's /boot/grub/stage1 or one of it's variants like /boot/grub/e2fs.stage1 etc. Often if this error occurs, it's because grub tries to boot the wrong partition (out of mysterious reasons). For the grub prompt, press c (not e, thats editing). then, execute the grub command

```
find /boot/grub/stage1
``` if the file exists, the correct partition will be shown. write down that partition (it should be sth. of the form (hdX,X) ) and press esc. then press e. you can now edit your boot command. select the line where it sais sth. about (hdY,Y) and change the (hdY,Y) to the previously noted (hdX,X)

hope it helps,

dracayr

---

### Post by bobpur on 2008-07-16
Sometimes, for whatever reason, usually when I'm switching flash drives or External drives, my BIOS will screw up the boot priority. I'll have to go in and return it to the proper boot drive. If the computer is not directed to the right hdd it'll give me an "error 15" because it can't find the OS.
I use AMD cpu's and Asus motherboards in my machines.
I don't know if this helps you or not, just something to check.

Good luck.

---

### Post by Viola99 on 2008-07-16
Thanks all - sadly away now, won't get chance to try any of these suggestion for another 24 hours!

---

