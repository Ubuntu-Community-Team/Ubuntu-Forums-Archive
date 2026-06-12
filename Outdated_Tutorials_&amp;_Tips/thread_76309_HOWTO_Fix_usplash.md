---
title: "HOWTO: Fix usplash"
date: 2005-10-14
forum: Outdated Tutorials &amp; Tips
---

### Post by Curufir on 2005-10-14
The timeout is set pretty low on usplash. Because of this people with slower computers will get kicked from the "pretty" usplash loading screen into the text style boot. The fix is pretty simple, but is made slightly more complicated by having to deal with the initrd image.

First make sure you have installed whichever kernel is suitable for your processor. I use an athlon-xp processor, so I use the "linux-image-2.6.12-9-k7" package.

Before we do anything we're making a backup of the initrd image.
```
sudo cp /boot/initrd.img-`uname -r` /boot/initrd.img-`uname -r`.bak
```

Now there are two way to fix this problem. The first method (which was pointed out by b34r in this thread) is very simple and feels a lot more "Ubuntu". The second method involves some direct manipulation of the initrd image and is a little more involved. If you can then use the first method.

**_The First Method_**

Edit the initramfs init file with your favourite text editor(If, for some reason, you don't have this file then run 'sudo apt-get install initramfs-tools').
```
sudo vim /usr/share/initramfs-tools/init
```

Replace this section:
```

. /scripts/${BOOT}

log_begin_msg "Loading modules"

```

With this:
```

. /scripts/${BOOT}

/sbin/usplash_write "TIMEOUT 120"

log_begin_msg "Loading modules"

```

Build a new initrd image.
```
sudo dpkg-reconfigure linux-image-`uname -r`
```

***

**_The Second Method_**

We'll work in a temporary dir, so make one.
```
mkdir ~/temp
cd ~/temp
```

Now we'll decompress the contents of the current initrd image in this directory.
```
gunzip -c /boot/initrd.img-`uname -r` | cpio -i
```

Now edit the init file with your favourite text editor.
```
vim init
```

Replace this section:
```

. /scripts/${BOOT}

log_begin_msg "Loading modules"

```

With this:
```

. /scripts/${BOOT}

/sbin/usplash_write "TIMEOUT 120"

log_begin_msg "Loading modules"

```

Now we'll rebuild the initrd image.
```
find * | cpio -o -H newc | gzip -9 -c > initrd.img-`uname -r`
sudo mv initrd.img-`uname -r` /boot/initrd.img-`uname -r`
```

***

Reboot and you should have the usplash screen working properly.

NOTE: If something goes horribly wrong then use GRUB to edit the entry for booting Ubuntu (Press 'e' on the boot screen). Add .bak to the end of the 'initrd= ...' part of the GRUB entry then press 'b' to boot. Once ubuntu has booted you can overwrite the broken initrd with the backup initrd for a permanent fix.

NOTE2: I just noticed that tildes don't show up well on the forum code sections. It's ~/temp **NOT** -/temp. Copy/paste would show up the difference, but it's best to be clear about it.

CREDIT: Thanks to b34r for pointing out a more elegant way to edit the initrd image.

---

### Post by gmc on 2005-10-15
After following you're instructions. I've run into little problem. I get a message saying "/sbin/usplash_write" not found. However usplash_write does exist in the /sbin directory.

```

# Don't do log messages here to avoid confusing usplash
run_scripts /scripts/init-top

. /scripts/${BOOT}

/sbin/usplash_write "TIMEOUT 120"

log_begin_msg "Loading modules"
load_modules
log_end_msg

```

```
ls -l /sbin/usplash
-rwxr-xr-x  1 root root 35764 2005-10-07 16:39 /sbin/usplash
-rwxr-xr-x  1 root root  3032 2005-10-07 16:39 /sbin/usplash_write

```

---

### Post by b34r on 2005-10-15
It is a bit easier to edit /usr/share/initramfs-tools/init
and the do a :
dpkg-reconfigure linux-image-$(uname -r)

---

### Post by gmc on 2005-10-15
[QUOTE=b34r]It is a bit easier to edit /usr/share/initramfs-tools/init
and the do a :
dpkg-reconfigure linux-image-$(uname -r)[/QUOTE]

This worked like a charm. I don't know why the previous method didn't but at least it's working now. Thanks.

G.

---

### Post by Curufir on 2005-10-15
[QUOTE=b34r]It is a bit easier to edit /usr/share/initramfs-tools/init
and the do a :
dpkg-reconfigure linux-image-$(uname -r)[/QUOTE]

Much nicer, I've updated the HOWTO to show that method.

[QUOTE=gmc]This worked like a charm. I don't know why the previous method didn't but at least it's working now. Thanks.

G.
[/QUOTE]

Weird error you had. My only thought is that usplash_write might not have been in the current initrd image. Glad you got it fixed.

---

### Post by Rxke on 2005-10-15
Disclaimer: running on a Mac, but ith same timeout problem.
i followed the 'complex' approach because there seems to be no  initramsf-tools for PPC in the repositories... (EDIT: Scrap that, there is... Must've been very confused... So disregard rest of post :oops: first method seems to work fine)(Edit #2: no it doesn't, seems to change nothing...)

But when I do ```
sudo find * | cpio -o -H newc | gzip -9 -c > /boot/initrd.img-`uname -r`
``` I got > bash: /boot/initrd.img-2.6.12-9-powerpc: access denied

So this is a case of privileges?

---

### Post by jdong on 2005-10-15
rxke: that is a permissions issue. "sudo" does not help you in the case of escalating permissions to redirections. In other words:

echo "hello" > /root-only
-and-
sudo echo "hello" > /root-only

Work in the exact same way. echo is what's affected by the "sudo", so echo will be running as root (which is pointless because you don't need root to print hello on the screen :) ). The redirection part of the command is actually handled by the currently running shell, which is running under your username regardless of how many sudo's you use inside of it.


You need to start a sudo shell:

sudo sh


then issue your commands.



But then again, I don't own a Mac. I don't know if PPC uses initramfs or initrd. Is initrd-tools present?

---

### Post by jdong on 2005-10-15
Note that you should be editing /usr/share/initramfs-tools/init and dpkg-reconfiguring. The other method of blasting apart an initrd has the annoying side-effect that kernel updates (i.e. security patches) will revert the changes, while the first method is permanent.

---

### Post by Rxke on 2005-10-15
thank you, jdong for the explanation. turned out I was barking up the wrong tree anyways (see edit in original post) but now at least I know why sudo in non-root doesn't works heehee!

---

### Post by Curufir on 2005-10-15
Fixed the sudo issue in the second method and the "initramsf-tools" typo, but I strongly advise people to use the first method not the second if at all possible.

That's what you get for posting at 4am :D .

---

### Post by CbrPad on 2005-10-15
Great stuff, I've finally gotten it going after having to set the timeout all the way up to 200.  Much appreciated !!

---

### Post by pardasaniman on 2005-10-17
I thought I'd mention that it is worth trying to boot without splash and quiet in the kernel boot parameters to see why it is taking soo long to boot.

---

### Post by skoal on 2005-10-17
Great Howto.  I couldn't figure out what the dealio was the splash screen with no progress meter bar.  This fixes it, but breaks something else...

** *When I log out of a KDE session, and try to log back in I lose all keyboard response.  Nothing.  Nada.  Adios keymigos! ***

Causes?

1. I believe recreating the initram disk has something to do with it.  I don't know who maintains the kernel package tree containing the ramdisk, but the ramdisk may have been built with some other options.  Not gonna download that kernel package source to probe any further either. Maybe later...

2. A lot of framebuffer device aware "drivers" do not play nice nice with Nvidia binary drivers.  It's quite apparent when I try to shutdown my box too.  When it's hitting runlevel 6, you can see some graphical garbledygook mixed in on the the framebuffer.

In the meantime, I just disabled the usplash altogether by removing the kernel grub parameters and restored my original ramdisk.

Thanks for the fix though.  I just don't need all that perty stuff when I can't log back into a KDE session.  Maybe someone else can figure this one out and post back...

\\//_

---

### Post by hunteramor on 2005-10-18
ok, I've set a high timeout and reinstalled the usplash package, and this is the error I'm still getting when usplash should be starting:

/init:70: /sbin/usplash_write:not found

that file *does* exist.  what's going on and how can i fix it?

---

### Post by erikf154 on 2005-10-24
I recompiled the kernel and am not using initramfs. Is it still possible to use usplash? In that case how...?

---

### Post by Tobi Vollebregt on 2005-11-13
If you set the usplash timeout to something high and it still times out (for me it times out while checking internal reiserfs tree), you may want to check if the script is run after module-init-tools or networking, because those scripts temporarily set the timeout to 120 and reset it to 15 afterwards.

I fixed my usplash with the first solution here and commenting out the lines changing the timeout in module-init-tools and networking.

---

### Post by quaestor on 2006-01-17
[QUOTE=erikf154]I recompiled the kernel and am not using initramfs. Is it still possible to use usplash? In that case how...?[/QUOTE]

I'd like to know the answer to this too, out of curiousity, mostly; I'm not using initrd so as to cut down on boot time (I made a custom kernel with only the necessary modules compiled in). The splash screen is kind of cool to "impress the rubes" ("Hey, what's THAT?" "Oh, thats linux... Kubuntu, actually"). I'd like to get it working again, just for fun. What would a minimal initrd image contain? How can you build it as part of the kernel build process?

q

---

### Post by kleeman on 2006-01-18
Another basic question:

How does one switch between the Kubuntu and Ubuntu splash screens? I prefer the latter, it's browner ;-)

---

### Post by rykel on 2006-01-19
[QUOTE=kleeman]Another basic question:

How does one switch between the Kubuntu and Ubuntu splash screens? I prefer the latter, it's browner ;-)[/QUOTE]

yes, someone please teach us how to switch between the ubuntu and kubuntu splashes... i installed kde, and now my splash shows kubuntu ~   :(

---

### Post by byen on 2006-01-19
> How does one switch between the Kubuntu and Ubuntu splash screens?
ok..to switch between Ubuntu and Kubuntu Uspash screens here is a how-to:
[http://www.ubuntuforums.org/showthread.php?t=113250](http://www.ubuntuforums.org/showthread.php?t=113250)
Let me know if it worked. Goodluck.

---

### Post by kleeman on 2006-01-19
[QUOTE=byen]ok..to switch between Ubuntu and Kubuntu Uspash screens here is a how-to:
[http://www.ubuntuforums.org/showthread.php?t=113250](http://www.ubuntuforums.org/showthread.php?t=113250)
Let me know if it worked. Goodluck.[/QUOTE]

Did the trick. Thanks!

---

### Post by rraghur on 2008-01-10
Tried *almost *everything and nothing worked (didnt try the time out though).

Also setting vga=791 in /boot/grub/menu.lst and I'd get a 

"Invalid mode value passed" error at boot.

Went to BIOS and increased framebuffer memory from 1MB to 8 MB - and that did the trick - get my usplash boot screen now.

HTH.

---

### Post by ubuntu-freak on 2008-01-10
My how-to may be useful to those who still have windows on their system. 
 
[http://ubuntuforums.org/showthread.php?t=663214](http://ubuntuforums.org/showthread.php?t=663214)
 
Nathan

---

