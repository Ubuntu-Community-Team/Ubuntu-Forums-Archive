---
title: "Using CLI Without X"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by tdrusk on 2008-06-12
I am running a computer that is 100% commandline. The console leaves about 3 inches all around it of black. I would like to have a full screen. Is there something that I need to do this?

---

### Post by wolfen69 on 2008-06-12
using the buttons on the monitor, you can adjust the horiz. and vert. size and placement.

---

### Post by tdrusk on 2008-06-12
This stupid monitor doesn't have them. Any other suggestions?

---

### Post by Prefader on 2008-06-12
Some laptops have a setting that enables "stretching" of the display when the resolution your OS is running at is lower than the native resolution of the LCD panel - this is likely the problem (are we talking about the laptop in your sig?).  Poke around in the laptops BIOS, you'll probably find something like that.

You may also want to look into modifying the boot line in /boot/grub/menu.lst to include vga=[whatever].  Look [here]("http://en.wikipedia.org/wiki/VESA_BIOS_Extensions") for a list of vga modes.

---

### Post by decoherence on 2008-06-12
> **Prefader said:**
> You may also want to look into modifying the boot line in /boot/grub/menu.lst to include vga=[whatever].  Look [here]("http://en.wikipedia.org/wiki/VESA_BIOS_Extensions") for a list of vga modes.

You can test this out by appending vga=[whatever] to the kernel line.

When you start the computer, press escape when it says "GRUB Loading". Press the 'e' key to edit the default boot options (assuming your computer boots in to Ubuntu by default and not windows or something)

Use the arrow keys to go down to the "kernel" line and press the 'e' key again.
Type a space, then type ```
vga=791
``` (for instance.) vga=791 should give you full screen on a 1024x768 monitor. If you don't have a 1024x768 monitor, you'll need a different number. Don't worry about messing things up -- changes here are temporary until the next reboot.

Press enter, then type the 'b' key to boot with that kernel line. If it works, use that line in /boot/grub/menu.lst to make the change permanent.

---

### Post by tdrusk on 2008-06-12
> **Prefader said:**
> Some laptops have a setting that enables "stretching" of the display when the resolution your OS is running at is lower than the native resolution of the LCD panel - this is likely the problem (are we talking about the laptop in your sig?).  Poke around in the laptops BIOS, you'll probably find something like that.

You may also want to look into modifying the boot line in /boot/grub/menu.lst to include vga=[whatever].  Look [here]("http://en.wikipedia.org/wiki/VESA_BIOS_Extensions") for a list of vga modes.
Sorry. It's actually a Pentium 4 Gateway Desktop.

Thanks.

---

### Post by Prefader on 2008-06-12
:) Do try the vga mode setting - if it's an older LCD, or just a really crappy CRT, it's possible that it just isn't scaling smaller resolutions for you.

Good luck!

---

### Post by tdrusk on 2008-06-12
Okay. I am reinstalling right now because I want to start fresh. I will tell ya how it works.

---

### Post by wootah on 2008-06-12
> **tdrusk said:**
> Okay. I am reinstalling right now because I want to start fresh. I will tell ya how it works.

VGA modes are probably what you are looking for (unless the monitor is not correctly stretching the input). Unfortunately, in 7.10, the framebuffer wasn't included as a kernel module (for whatever freakin' reason) so if you included the vga=xxx as a kernel option (in the grub menu.lst) you wuold always get a blank screen.

I don't know if they changed this in 8.04? Either way, you could try appending **vga=ask** into the line that specifies your kernel in the menu.lst:

```

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=df1efe7b-4feb-4dc9-bf44-4bb294cffc18 ro splash **vga=ask**
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

```

Try that and let us know if one of the options works. You can find more information in the linux kernel documentation at: */usr/share/doc/linux-doc-2.6.22/Documentation/fb/* and the file is ***vesafb.txt.gz***. 2.6.22 is the kernal version you have without the minor number (ie: uname -r using the first 3 numbers) You will need to gunzip this file to read it of course :) If you don't have the documentation, you may need to install it:
```
sudo apt-get install linux-doc
```
and if you forget where it is installed, or you are not sure:
```
dpkg -L linux-doc
```

Lot's of information that might not even apply to you. Regardless, good luck :)

---

### Post by tdrusk on 2008-06-12
Hmm. Still having troubles.

I realized that my bios is exactly the same resolution. vga=ask isn't working for me either. It's not giving me any modes that work, even after I scan. I have had Ubuntu installed on this computer and it worked correctly. Hmm...

---

### Post by wootah on 2008-06-12
> **tdrusk said:**
> Hmm. Still having troubles.

I realized that my bios is exactly the same resolution. vga=ask isn't working for me either. It's not giving me any modes that work, even after I scan. I have had Ubuntu installed on this computer and it worked correctly. Hmm...

Yeah, I'm thinking the fb module isn't included in the new version either. Don't take my word for it though :) I'm still working out how to fix this as well. Perhaps try doing a search for *frame buffer +Ubuntu* if you still want to change your resolution. I think you might need to do a kernel recompile IF this is the actually cause of your problem.

PS: Does anyone find it kind of funny when some one thanks you for something, but hasn't said anything anywhere in the thread? :)

---

### Post by tdrusk on 2008-06-12
> **wootah said:**
> Yeah, I'm thinking the fb module isn't included in the new version either. Don't take my word for it though :) I'm still working out how to fix this as well. Perhaps try doing a search for *frame buffer +Ubuntu* if you still want to change your resolution. I think you might need to do a kernel recompile IF this is the actually cause of your problem.

PS: Does anyone find it kind of funny when some one thanks you for something, but hasn't said anything anywhere in the thread? :)
I do it sometimes. It saves a post.

---

### Post by gr4nf on 2008-06-12
Gah! this is so simple!

just use a VT. Try CTRL+ALT+F1. This will give you a _true_ CLI. When you want X back, use CTRL+ALT+F7.

---

### Post by tdrusk on 2008-06-12
> **gr4nf said:**
> Gah! this is so simple!

just use a VT. Try CTRL+ALT+F1. This will give you a _true_ CLI. When you want X back, use CTRL+ALT+F7.
Nice job reading the thread.

---

