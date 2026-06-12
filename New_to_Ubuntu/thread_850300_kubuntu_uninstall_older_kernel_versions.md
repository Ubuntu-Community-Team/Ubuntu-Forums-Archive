---
title: "kubuntu uninstall older kernel versions"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by 77bridge on 2008-07-05
Hi,

I'm running kubuntu and I guess I've installed a couple updates to the kernel as I've got a bunch of versions to choose from in my grub menu file.  I've heard that you can uninstall the older versions of the kernel, but I can't find any such options in the adept installer.  Any suggestions?

thanks!  :)

---

### Post by wolfen69 on 2008-07-05
just go to /boot/grub/menu.lst and delete or put a # in front of each line you dont want.

---

### Post by mgranet on 2008-07-05
That will effectively remove the boot options from GRUB, but it won't get rid of the several hundred megs worth of kernel files still installed. Go into adept, and type in 'kernel' into the search box. Scroll down until you find the linux-headers and linux image files. If you are booted into the latest kernel, and everything works fine, go ahead and remove all the headers and images of the old kernels. This will by default remove them from the GRUB menu. Whatever you do, don't remove the installed image or header files for 2.6.24-19. Those are your current kernel, and if you remove them, you will be unable to boot.

---

### Post by 77bridge on 2008-07-06
great- the only problem is typing 'kernel' into the search box in adept gives me only 1 hit for some kernel for the game 'arkhart'.  :o(  I have selected to show unsupported software and proprietary software in the upper right hand corner.  any suggestions where i can find this in the adept gui?

---

### Post by kuja on 2008-07-06
Well, you could just scroll all the way down, or you could use "linux-image" to get the images and "linux-header" to get the headers and "linux-restricted" to get those ... yeah, and that should be all.

---

### Post by 77bridge on 2008-07-06
i entered these terms into the adept gui and got 0 hits each time.  i've scrolled through the "System" and "Utilities" sets of applications.  not sure where you intend me to scroll down- can you give me some more info?

---

### Post by Splappy on 2008-07-06
You have to use the Adept Manager, which you can find in the K Menu -> System -> Adept Manager.

---

### Post by 77bridge on 2008-07-10
Ahh... different package managers.  See this is why I posted in the newbies section.  Thanks!

---

