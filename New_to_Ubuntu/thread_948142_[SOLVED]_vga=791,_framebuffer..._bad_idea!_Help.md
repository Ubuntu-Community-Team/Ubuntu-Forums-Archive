---
title: "[SOLVED] vga=791, framebuffer... bad idea! Help?"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by mrowth on 2008-10-14
I'm afraid I messed something up. I wanted a higher screen resolution on the ttys. Not quite knowing what I was doing, I followed instructions found elsewhere:

1) Commented out "blacklist vesafb" and "blacklist vga16fb" in /etc/modprobe.d/blacklist-framebuffer.

2) Added "vga16fb", "fbcon" and "vesafb" to /etc/initramfs-tools/modules.

3) Ran sudo update-initramfs -u.

Voila! vga=791 worked again. 

But waking from Suspend-to-RAM gave me garbled screens -- full of pixel-noise. 

So I undid the changes to the blacklist-framebuffer and modules files and ran sudo update-initramfs -u again, hoping this would revert everything back to the defaults. 

Everything seems fine again after waking from suspend -- but then X spontaneously restarts, bringing back the pixel junk too. That's even worse, since it obviously kills every app/file I had run/opened until then. 

Also: I forgot to remove the vga=791 the first time I rebooted, and that still worked.

So... how can I clean up my mess? 

:oops:

PS: Kubuntu 8.04.1 with Nvidia drivers from the repositories.

---

### Post by mrowth on 2008-10-14
There are differences between the faulty behaviour in the -generic and -rt kernels.

**generic:**

X restarts after waking from suspend or when trying to switch to a console (it's as though I'd pressed Ctrl-Alt-Backspace instead of Ctrl-Alt-F1). 

lsmod lists this:

```
fbcon                  42912  0
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
```

**rt:**

Can switch between consoles, but X still restarts after waking from suspend.

lsmod doesn't list the above entries. 

The pixel noise is gone (for some reason).

---

### Post by mrowth on 2008-10-15
Okay, I reinstalled both kernels + nvidia drivers. I wish I'd thought of a better solution than simply wiping the slate clean, and I'm still wondering about the fbcon/softcursor/bitblit/tileblit discrepancy between generic/rt kernels, because that's still there. But at least it seems to have worked.

(Knowing my Suspend-to-RAM it'll become flaky again soon enough for no discernible reason.)

Will mark this "solved" if it doesn't explode until tomorrow...

---

### Post by mrowth on 2008-10-15
It seems that kompmgr was or is the reason or *another* reason for the X restarts. Although I can't say it's always done that as predictably as right now. That's a different topic, though.

---

