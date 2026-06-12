---
title: "How to safely remove old kernels?"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by legolas_w on 2008-05-15
Hi
Thank you for reading my post
I have ubuntu 8.04 and In update manager I select to get all updates (post hardy, and back ports...) now It installs one other kernel into my system.

When I boot the computer I have 2 "safe recovery?" option and two normal boot kernels one number ends with 16 and the other ends with 17.

Does having more than one kernel impose resource consumption or there is no problem with it?

I should somehow be able to remove old kernels, can you let me know how?

Thanks

---

### Post by AbredPeytr on 2008-05-15
There should be no problem with resources since only one kernal will be running when you start up linux. You can choose which one to use.

I know there is a program that will remove older kernals and leave just one, but I will have to get back to you with it's name, if I can find it again.

---

### Post by FreewheelinFrank on 2008-05-15
Do a search with Synaptic for linux-image and remove older ones, but there's no hurry: test out a new kernel for a few weeks to make sure there're no problems before removing the old one.

---

### Post by Oldsoldier2003 on 2008-05-15
> **legolas_w said:**
> Hi
Thank you for reading my post
I have ubuntu 8.04 and In update manager I select to get all updates (post hardy, and back ports...) now It installs one other kernel into my system.

When I boot the computer I have 2 "safe recovery?" option and two normal boot kernels one number ends with 16 and the other ends with 17.

Does having more than one kernel impose resource consumption or there is no problem with it?

I should somehow be able to remove old kernels, can you let me know how?

Thanks

I usually leave the second oldest kernel as a backup in case things go south, but if you want to remove and older kernel just go into synaptic and search for "linux-image". Find the old image(s) and mark them for complete removal. Synaptic will remove the old images and update grub for you.

---

### Post by Ayuthia on 2008-05-15
> **legolas_w said:**
> Hi
Thank you for reading my post
I have ubuntu 8.04 and In update manager I select to get all updates (post hardy, and back ports...) now It installs one other kernel into my system.

When I boot the computer I have 2 "safe recovery?" option and two normal boot kernels one number ends with 16 and the other ends with 17.

Does having more than one kernel impose resource consumption or there is no problem with it?

I should somehow be able to remove old kernels, can you let me know how?

Thanks

If you just don't like seeing them, you can remove them by editing /boot/grub/menu.lst:
```
gksu gedit /boot/grub/menu.lst
```Just look for something like this:
```
title           Ubuntu 8.04, kernel 2.6.24-17-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.24-17-generic root=UUID=34243212-ds38e-5k43-f3ae3-42f16f88e95e ro quiet splash
initrd          /boot/initrd.img-2.6.24-17-generic

```
and add a # in front of each line:
```
#title           Ubuntu 8.04, kernel 2.6.24-17-generic
root            (hd0,5)
#kernel          /boot/vmlinuz-2.6.24-17-generic root=UUID=34243212-ds38e-5k43-f3ae3-42f16f88e95e ro quiet splash
#initrd          /boot/initrd.img-2.6.24-17-generic
```

That will remove them from the display, but not make them disappear.

Generally, you want to have a backup kernel available because if something does go wrong, you can always go to the other kernel to try to fix what broke.

---

### Post by drs305 on 2008-05-15
There is also a menu in System, Admin, Startup Manager, Advanced tab so you can limit the number of kernels you see in the grub boot menu. Each time a new kernel is added the grub boot menu by default will show all the old ones. If you don't want to see all of them, edit this entry. It doesn't actually remove the kernels - it just removes them from the boot menu.

If you don't see this menu option, install startupmanager:
```
sudo aptitude install startupmanager
```

You can also do this manually by editing the grub menu (/boot/grub/menu.lst) and commenting out the old kernels, but the above method is easier for newbies.

---

### Post by Oldsoldier2003 on 2008-05-15
> **drs305 said:**
> There is also a menu in System, Admin, Startup Manager, Advanced tab so you can limit the number of kernels you see in the grub boot menu. Each time a new kernel is added the grub boot menu by default will show all the old ones. If you don't want to see all of them, edit this entry. It doesn't actually remove the kernels - it just removes them from the boot menu.

If you don't see this menu option, install startupmanager:
```
sudo aptitude install startupmanager
```

You can also do this manually by editing the grub menu (/boot/grub/menu.lst) and commenting out the old kernels, but the above method is easier for newbies.
I agree that startup manager is a nice utility, but honestly it really is a good idea for newbies to learn a little about grub. I know its a bit advanced but having a basic knowledge of grub will pay off in the long run :)

---

### Post by drs305 on 2008-05-15
> **Oldsoldier2003 said:**
> I agree that startup manager is a nice utility, but honestly it really is a good idea for newbies to learn a little about grub. I know its a bit advanced but having a basic knowledge of grub will pay off in the long run :)

I agree completely  -  if they want to.

---

### Post by celticbhoy on 2008-05-15
I agree also, but giving them the utilities to make things easier can only help them to spread the word of linux to friends.

---

### Post by Oldsoldier2003 on 2008-05-15
> **celticbhoy said:**
> I agree also, but giving them the utilities to make things easier can only help them to spread the word of linux to friends.

I'm kinda on the fence though I tend to agree with the part that it helps spread the gospel :) Unfortunately when one of the utilities is misused or flat out fails often we have a new user that is likely to reach for his windows cd because he hasn't the patience to work through it :/

---

### Post by stchman on 2008-05-15
> **legolas_w said:**
> Hi
Thank you for reading my post
I have ubuntu 8.04 and In update manager I select to get all updates (post hardy, and back ports...) now It installs one other kernel into my system.

When I boot the computer I have 2 "safe recovery?" option and two normal boot kernels one number ends with 16 and the other ends with 17.

Does having more than one kernel impose resource consumption or there is no problem with it?

I should somehow be able to remove old kernels, can you let me know how?

Thanks

You can remove them via Synaptic.  This will also cause your menu.lst file to be modified.

---

### Post by legolas_w on 2008-05-17
Thank you all for your replys.
New kernel works fine and I just tried to load the system with the older kernel and it does not load the X window correctly. 
So I think the new kernel has changed other packages when it get installed and made the old kernel not to work.

Thanks again.

---

### Post by lolo67 on 2008-06-18
> **Oldsoldier2003 said:**
> I usually leave the second oldest kernel as a backup in case things go south, but if you want to remove and older kernel just go into synaptic and search for "linux-image". Find the old image(s) and mark them for complete removal. Synaptic will remove the old images and update grub for you.

:)Thanks removed 2 older kernals from Hardy using Synaptic, works great:lolflag:

---

### Post by gulmer on 2008-07-02
I have a question about adding new kernels to the boot menu. In synaptic it shows the latest kernel installed as linux-image 2.6.24-19 generic, but in the boot menu it only shows -17 and not the latest kernel that's installed.How do I get the latest kernel to show up in the boot menu?:confused:

---

