---
title: "Installation problem GRUB!!"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by link- on 2008-05-31
Hi,

obviously I'm a newbie here and I am having probably a not new problem but I haven't find out a solution to it yet.Here's the problem, I installed ubuntu(HH) on a wd usb external hdd (yes my bios support usb booting) I installed the grub in the external hdd (as i wanted to) so if the hdd is connected I could boot linux or vista, the problem is that when I connected the usb hdd it run the grub but when make my selection (ubuntu or vista) I get error 22 and error 17 depending on which os I select. The only way I could boot vista is by disconnecting the hdd.

There is a way to install the grub in the external hdd without having this problem?
Thanks,
link-

---

### Post by logos34 on 2008-05-31
I think you just need to fix menu.lst:

Select ubuntu on the grub menu and press 'e' to edit, 'e' again on the root line.  It should read **(hd[COLOR="Blue"]0[/COLOR],?)**.  Edit it if necessary, then 'b' to boot.  If that gets you into ubuntu make the change permanent:

gksudo gedit /boot/grub/menu.lst

-change **groot** and **root** lines.  

You might also want to edit /boot/grub/device.map to match

---

### Post by link- on 2008-05-31
> **logos34 said:**
> I think you just need to fix menu.lst:

Select ubuntu on the grub menu and press 'e' to edit, 'e' again on the root line.  It should read **(hd[COLOR="Blue"]0[/COLOR],?)**.  Edit it if necessary, then 'b' to boot.  If that gets you into ubuntu make the change permanent:

gksudo gedit /boot/grub/menu.lst

-change **groot** and **root** lines.  

You might also want to edit /boot/grub/device.map to match

I get me into ubuntu boot when I try to make change permanent I get 
chris@chris-laptop:~$ groot
bash: groot: command not found
chris@chris-laptop:~$ root
bash: root: command not found
chris@chris-laptop:~$ 

probably is because of me. Can you explain this part more explicitly?

Thanks
-link

---

### Post by Xiong Chiamiov on 2008-05-31
The easy way to deal with GRUB is using [SuperGrubDisk]("http://supergrubdisk.org").

---

### Post by link- on 2008-05-31
> **Xiong Chiamiov said:**
> The easy way to deal with GRUB is using [SuperGrubDisk]("http://supergrubdisk.org").

Why? Logos34 explanation seem simple.

---

### Post by Joeb454 on 2008-05-31
You can choose whichever method you want to use :) That's the nice thing about Linux :)

---

### Post by logos34 on 2008-05-31
> **link- said:**
> I get me into ubuntu boot when I try to make change permanent I get 
chris@chris-laptop:~$ groot
bash: groot: command not found
chris@chris-laptop:~$ root
bash: root: command not found
chris@chris-laptop:~$ 

probably is because of me. Can you explain this part more explicitly?

Thanks
-link

no, run

**gksudo gedit /boot/grub/menu.lst**

now you can edit it.

---

### Post by link- on 2008-05-31
> **logos34 said:**
> no, run

**gksudo gedit /boot/grub/menu.lst**

now you can edit it.

I wrote that on the terminal but it just asked me for the password and then nothing. Try to explain this procedure more explicitly for me.
Remember this is my first cup of ubuntu

-link

---

### Post by logos34 on 2008-05-31
gedit/text editor should have launched.

Alternatively try

sudo nano /boot/grub/menu.lst

---

### Post by link- on 2008-05-31
chris@chris-laptop:~$ sudo nano/boot/grub/menu.lst
sudo: nano/boot/grub/menu.lst: command not found

---

### Post by Maestro23 on 2008-05-31
> **link- said:**
> chris@chris-laptop:~$ sudo nano/boot/grub/menu.lst
sudo: nano/boot/grub/menu.lst: command not found

Linux is Case Sensitive:

> sudo nano /boot/grub/menu.lst (lowercase L)

---

### Post by sayakb on 2008-05-31
Give a space between nano and /boot..

---

### Post by Maestro23 on 2008-05-31
Double Post.

---

### Post by link- on 2008-05-31
> **LinuxIsInnovation said:**
> Give a space between nano and /boot..
You were right,

Now what?

---

### Post by logos34 on 2008-05-31
change the groot and root lines accordingly (use arrow keys to navigate, no mouse)

to save and exit press ctrl + x

---

### Post by link- on 2008-05-31
thanks a lot logos

---

