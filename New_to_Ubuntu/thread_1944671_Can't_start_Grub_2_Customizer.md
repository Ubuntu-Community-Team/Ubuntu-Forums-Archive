---
title: "Can't start Grub 2 Customizer"
date: 2012-03-21
forum: New to Ubuntu
---

### Post by Bumpalot on 2012-03-21
Installed Grub Customizer. On running it,  - I get the popup msg "No Bootloader found
Do you want to select another root partition?"
Selected NO. What is causing Grub2 customizerto NOT find a bootloader when I am able to previously rebot sucessfully?

---

### Post by Rex Bouwense on 2012-03-21
That doesn't make any sense.  How did you install Grub Customizer (Software Center, Synaptic, apt-get)?  What I would do is completely uninstall it and then re-install.

---

### Post by Bumpalot on 2012-03-22
I apt-get installed. Have now uninstalled, rebooted & reinstalled. Same result "No Bootloader found!

---

### Post by plucky on 2012-03-22
> **Bumpalot said:**
> I apt-get installed. Have now uninstalled, rebooted & reinstalled. Same result "No Bootloader found!

Try from a terminal ```
grub-customizer
``` and post output.

What does your /boot partition look like ```
ls -l /boot
```

---

### Post by Bumpalot on 2012-03-22
[EMAIL="bump@bumpyputer:~$"]bump@bumpyputer:~$[/EMAIL] grub-customizer
 *** initializing (w/o specified bootloader type)&#8230;
   * reading partition info&#8230;
   * Loading Framebuffer resolutions (background process)
   * Finding out if this is a live CD
     [running on an installed system]
     [checking the burg-mkconfig command&#8230; ]
     [not found]
     [using custom Grub2 configuration]
     [checking the  command&#8230; ]
     [not found]
[EMAIL="bump@bumpyputer:~$"]bump@bumpyputer:~$[/EMAIL] 
[EMAIL="bump@bumpyputer:~$"]bump@bumpyputer:~$[/EMAIL] ls -l /boot
total 45212
-rw-r--r-- 1 root root  646144 2011-01-10 16:27 abi-2.6.32-28-generic
-rw-r--r-- 1 root root  646806 2012-01-25 06:42 abi-2.6.32-38-generic
-rw-r--r-- 1 root root  646913 2012-02-13 18:10 abi-2.6.32-39-generic
-rw-r--r-- 1 root root  110590 2011-01-10 16:27 config-2.6.32-28-generic
-rw-r--r-- 1 root root  110567 2012-01-25 06:42 config-2.6.32-38-generic
-rw-r--r-- 1 root root  110567 2012-02-13 18:10 config-2.6.32-39-generic
drwxr-xr-x 3 root root    4096 2012-03-19 18:03 grub
-rw-r--r-- 1 root root 8340224 2012-03-02 15:39 initrd.img-2.6.32-28-generic
-rw-r--r-- 1 root root 8371939 2012-03-03 09:21 initrd.img-2.6.32-38-generic
-rw-r--r-- 1 root root 8371565 2012-03-07 08:15 initrd.img-2.6.32-39-generic
-rw-r--r-- 1 root root  160280 2010-03-23 02:40 memtest86+.bin
-rw-r--r-- 1 root root 2157108 2011-01-10 16:27 System.map-2.6.32-28-generic
-rw-r--r-- 1 root root 2159402 2012-01-25 06:42 System.map-2.6.32-38-generic
-rw-r--r-- 1 root root 2159832 2012-02-13 18:10 System.map-2.6.32-39-generic
-rw-r--r-- 1 root root    1336 2011-01-10 16:28 vmcoreinfo-2.6.32-28-generic
-rw-r--r-- 1 root root    1336 2012-01-25 06:43 vmcoreinfo-2.6.32-38-generic
-rw-r--r-- 1 root root    1336 2012-02-13 18:15 vmcoreinfo-2.6.32-39-generic
-rw-r--r-- 1 root root 4052512 2011-01-10 16:27 vmlinuz-2.6.32-28-generic
-rw-r--r-- 1 root root 4061376 2012-01-25 06:42 vmlinuz-2.6.32-38-generic
-rw-r--r-- 1 root root 4061152 2012-02-13 18:10 vmlinuz-2.6.32-39-generic
[EMAIL="bump@bumpyputer:~$"]bump@bumpyputer:~$[/EMAIL]

---

### Post by Bumpalot on 2012-03-23
Closing this & starting a new thread: Reason a question was asked & I pasted the reply  -- Plucky did not reply.

---

### Post by Bumpalot on 2012-03-23
Installed Grub Customizer. On running it, - I get the popup msg "No Bootloader found
Do you want to select another root partition?"
Selected NO. What is causing Grub2 customizer to NOT find a bootloader when I am able to previously reboot sucessfully?
Here is the output for grub-customizer & ls -l /boot
[EMAIL="bump@bumpyputer:~$"]bump@bumpyputer:~$[/EMAIL] grub-customizer
*** initializing (w/o specified bootloader type)…
* reading partition info…
* Loading Framebuffer resolutions (background process)
* Finding out if this is a live CD
[running on an installed system]
[checking the burg-mkconfig command… ]
[not found]
[using custom Grub2 configuration]
[checking the command… ]
[not found]
[EMAIL="bump@bumpyputer:~$"]bump@bumpyputer:~$[/EMAIL] 
[EMAIL="bump@bumpyputer:~$"]bump@bumpyputer:~$[/EMAIL] ls -l /boot
total 45212
-rw-r--r-- 1 root root 646144 2011-01-10 16:27 abi-2.6.32-28-generic
-rw-r--r-- 1 root root 646806 2012-01-25 06:42 abi-2.6.32-38-generic
-rw-r--r-- 1 root root 646913 2012-02-13 18:10 abi-2.6.32-39-generic
-rw-r--r-- 1 root root 110590 2011-01-10 16:27 config-2.6.32-28-generic
-rw-r--r-- 1 root root 110567 2012-01-25 06:42 config-2.6.32-38-generic
-rw-r--r-- 1 root root 110567 2012-02-13 18:10 config-2.6.32-39-generic
drwxr-xr-x 3 root root 4096 2012-03-19 18:03 grub
-rw-r--r-- 1 root root 8340224 2012-03-02 15:39 initrd.img-2.6.32-28-generic
-rw-r--r-- 1 root root 8371939 2012-03-03 09:21 initrd.img-2.6.32-38-generic
-rw-r--r-- 1 root root 8371565 2012-03-07 08:15 initrd.img-2.6.32-39-generic
-rw-r--r-- 1 root root 160280 2010-03-23 02:40 memtest86+.bin
-rw-r--r-- 1 root root 2157108 2011-01-10 16:27 System.map-2.6.32-28-generic
-rw-r--r-- 1 root root 2159402 2012-01-25 06:42 System.map-2.6.32-38-generic
-rw-r--r-- 1 root root 2159832 2012-02-13 18:10 System.map-2.6.32-39-generic
-rw-r--r-- 1 root root 1336 2011-01-10 16:28 vmcoreinfo-2.6.32-28-generic
-rw-r--r-- 1 root root 1336 2012-01-25 06:43 vmcoreinfo-2.6.32-38-generic
-rw-r--r-- 1 root root 1336 2012-02-13 18:15 vmcoreinfo-2.6.32-39-generic
-rw-r--r-- 1 root root 4052512 2011-01-10 16:27 vmlinuz-2.6.32-28-generic
-rw-r--r-- 1 root root 4061376 2012-01-25 06:42 vmlinuz-2.6.32-38-generic
-rw-r--r-- 1 root root 4061152 2012-02-13 18:10 vmlinuz-2.6.32-39-generic
[EMAIL="bump@bumpyputer:~$"]bump@bumpyputer:~$[/EMAIL]

---

### Post by plucky on 2012-03-24
> Closing this & starting a new thread: Reason a question was asked & I pasted the reply -- Plucky did not reply. 

Sorry about that,but life intervened.

This is what I get when I run grub-customizer from a terminal in 12.04
```
 *** initializing (w/o specified bootloader type)…
   * reading partition info…
   * Loading Framebuffer resolutions (background process)
   * Finding out if this is a live CD
     [running on an installed system]
     [checking the burg-mkconfig command… ]
     [not found]
     [checking the grub-mkconfig command… ]
     [found at: /usr/sbin/grub-mkconfig]
     [checking the update-grub command… ]
     [found at: /usr/sbin/update-grub]
     [checking the grub-install command… ]
     [found at: /usr/sbin/grub-install]
 *** initializing (w/ specified bootloader type)…
     [checking the grub-mkconfig command… ]
     [found at: /usr/sbin/grub-mkconfig]
     [checking the update-grub command… ]
     [found at: /usr/sbin/update-grub]
     [checking the grub-install command… ]
     [found at: /usr/sbin/grub-install]
process 6295: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
   * Checking if the config directory is clean
 *** loading configuration
 *** loading - preserveConfig: no
   * unsetting saved config
 *** loading settings
 *** loading grub list
   * loading scripts…
   * loading proxies…
   * creating proxifiedScript links & chmodding other files…
   * running grub-mkconfig
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [mkconfig successfull completed]
     [using /usr/share/desktop-base/grub_background.sh to configure colors and the background image]
   * restoring grub configuration
   * loading completed
 *** grub list completely loaded
 *** loading saved grub list
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]
     [running GrubCustomizer::syncListView_load]
     [GrubCustomizer::syncListView_load completed]

```


It seems to be failing the checks on your system.

Do the files exist in your /usr/sbin directory?

Are you running Lucid 10.04.4?

Has it ever run correctly?

You could try running ```
sudo update-grub
``` to see if that runs correctly.

Good Luck

p.s. I cannot open your new thread.

---

### Post by critin on 2012-03-24
Bumpalot, I've followed all your threads with fascination.  What are you wanting or expecting Grub Customizer to do?   

Maybe if you asked from that point of view, you could accomplish it another way or from another app.   Fooling around too much with grub will leave the machine unable to boot at all at some point.
Hope you get it the way you want, good luck.

---

