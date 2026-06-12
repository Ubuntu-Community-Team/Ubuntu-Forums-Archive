---
title: "Help! After upgrade only text based login"
date: 2012-07-25
forum: New to Ubuntu
---

### Post by redsprite on 2012-07-25
Hey everyone! 
I recently upgraded to Ubuntu 12.04 on it. It worked fine for many two weeks but after installing updates and rebooting, I was greeted with a text based login screen. 

I tried to get console mode the by  ctrl+alt +f1 but the screen turned black and it froze (in the upper left corner there is a dash).

Is there any way to find out what the problem is? Like an error log that I can take a look at?  The boot-loader works fine. I only get this text : 

"** (plymouthd:234): WARNING **: Command line 'dbus-launch --autolaunch=08ddf3fcf038ec-----008 --binary-syntax --close-stderr' exited witn non-zero exit status 1: Autolaunch error: X11 initialization failed.\n" 

Any help is much appreciated!

---

### Post by angry_johnnie on 2012-07-25
if you're able to get to a text login, try logging in with your username an password, and then type "startx."  that should bring up your destop.

---

### Post by redsprite on 2012-07-25
> **angry_johnnie said:**
> if you're able to get to a text login, try logging in with your username an password, and then type "startx."  that should bring up your destop.
it's impossible to log in  when i try ctrl+alt+ f1 and f2 to get console mode the screen turned black and it froze (in the upper left corner there is a dash)

---

### Post by angry_johnnie on 2012-07-25
:) well, from your first post, i gathered you did get to a text based login.

have you tried booting to recovery mode?

---

### Post by redsprite on 2012-07-25
> **angry_johnnie said:**
> :) well, from your first post, i gathered you did get to a text based login.

have you tried booting to recovery mode?
thank u a lot ,
same thing in safe mode too

---

### Post by redsprite on 2012-07-25
on the recovery mode system still booting 
the screen turned black and it froze

---

### Post by angry_johnnie on 2012-07-25
well, that's really rotten :o

do you have any other available kernels in your grub menu?  if so, try booting with an older kernel.

if there are no older kernels to boot with, try editing grub's boot options to try to make some sense out of this.

on your grub menu, select the line you would boot from and press "e" to edit.  it will display the menu entry as it is in /boot/grub/grub.cfg.

look for the line that starts with "linux".  it should be something like: "linux	/boot/vmlinuz-......"  move the cursor with the navigation arrows until you get to the end of that line.  usually, it'll say something like "ro quiet splash"  delete "quiet" and "splash".  then, press ctrl + x to boot.

it will give you a verbose, text only, boot, with no plymouth.  if it fails, at least it will show you what it's getting stuck on.

good luck :)

---

### Post by redsprite on 2012-07-25
> **angry_johnnie said:**
> well, that's really rotten :o

do you have any other available kernels in your grub menu?  if so, try booting with an older kernel.

if there are no older kernels to boot with, try editing grub's boot options to try to make some sense out of this.

on your grub menu, select the line you would boot from and press "e" to edit.  it will display the menu entry as it is in /boot/grub/grub.cfg.

look for the line that starts with "linux".  it should be something like: "linux	/boot/vmlinuz-......"  move the cursor with the navigation arrows until you get to the end of that line.  usually, it'll say something like "ro quiet splash"  delete "quiet" and "splash".  then, press ctrl + x to boot.

it will give you a verbose, text only, boot, with no plymouth.  if it fails, at least it will show you what it's getting stuck on.

good luck :)
thank u
 i'll do it  now

---

### Post by redsprite on 2012-07-25
sorry but no changes apart from many new lines on the boot screen:
satrting mDNS/DNS-SD daemon                             ok
satrting uncomplicated firewall                              ok
satrting configure virtuel network devices             ok
satrting configure virtuel network devices             ok
satrting cups printing spooler/erver                        ok
-
 and still a long time on this  froze screen

---

### Post by redsprite on 2012-07-25
i have an other linux 3.2.6 on the same hdd , i don't know if that can help us ?

---

### Post by redsprite on 2012-07-25
any solution  :confused:

---

### Post by angry_johnnie on 2012-07-25
so what happens if you boot from that other linux you mentioned?  does it do anything different? can you still boot from a live cd?

---

### Post by redsprite on 2012-07-27
yes certainly sir

---

### Post by redsprite on 2012-07-27
thnx, i did  it by the live cd

---

