---
title: "HOWTO: Captive-NTFS on 2.6.10-4"
date: 2005-03-20
forum: Outdated Tutorials &amp; Tips
---

### Post by beefsprocket on 2005-03-20
Right... Here it is (at least for me anyways). 

Step 1: Install gcc and kernel source for whichever version you so choose (I went with 2.6.10-4)

Step 2: Patch your kernel source with the following (taken from mail archive on captive [site](http://www.jankratochvil.net/pipermail/captive-list/2004-December/000645.html) )

diff -Naur kernel/signal.c.orig kernel/signal.c
--- kernel/signal.c.orig        2004-12-28 13:23:06.000000000 +0100
+++ kernel/signal.c     2004-12-28 13:24:59.000000000 +0100
@@ -1939,6 +1939,7 @@
 EXPORT_SYMBOL(sigprocmask);
 EXPORT_SYMBOL(block_all_signals);
 EXPORT_SYMBOL(unblock_all_signals);
+EXPORT_SYMBOL(kill_proc_info);  /* hcz */


 /*

To patch you should copy and paste the above into a new file and save.
Execute the following from within your /usr/src/linux directory:

patch -p0 < /path-to-previously-created-patch-goes-here

Step 3: Download captive-ntfs .deb from [here](http://www.kruyt.org/?sub_item=46) and install it.

Step 4: Compile your kernel and modules and reboot.

Step 5: Run captive-install-acquire and then try mounting your drive with mount -t captive-ntfs

Step 6: Write a reply telling me that I'm an idiot if this doesn't work for you  ](*,)

---

### Post by vvu on 2005-03-23
This feature should be an option to install via apt-get or be integrated into the distro.

---

### Post by ember on 2005-03-23
Anyway I like to tick that Captive NTFS is really, really slow compared to the NTFS-driver in the Linux-Kernel, so if you don't depend on NTFS-write access stay with the open source driver.

---

### Post by kahping on 2005-03-24
[QUOTE=vvu]This feature should be an option to install via apt-get or be integrated into the distro.[/QUOTE]

in hoary, just add a new custom repository with [FONT=System]deb [http://www.kruyt.org/debian](http://www.kruyt.org/debian) /[/FONT]

kahping

edit:

o yeah, and reload after adding it so it'll be listed for selection at your leisure :-P

edit2:

btw, i get stuck at the patching step, or at least it seems like it's stuck there. how long does it take to patch a file, normally? since it's just one file, i think it shouldn't be more than a few seconds(if at all)  :confused:

---

### Post by cerbie on 2005-05-27
newbie at step 6  :) 

```
root@cerbuntu:~ # patch -p0 < /home/cerbie/patchy.txt
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -Naur kernel/signal.c.orig kernel/signal.c
|--- kernel/signal.c.orig 2004-12-28 13:23:06.000000000 +0100
|+++ kernel/signal.c 2004-12-28 13:24:59.000000000 +0100
--------------------------
File to patch:
```

This occurs with 2.6.10-5-386 and 2.6.10-5-k7 (the only kernels I have installed). I have the GCC (gcc-3.3, gcc-3.3-base), AFAIK, and the headers and sources for the kernels.

Now, I wasn't sure about the <, and that is probably wrong, but trying it as such:```
root@cerbuntu:~ # patch -p0 < /home/cerbie/patchy.txt
```causes the terminal to just sit there and not give the prompt back. No messages , no crazy CPU use or HDD access...nada. Unless it should take more than a couple hours to apply the patch, somethin' ain't right, there.

 ](*,)

---

