---
title: "Recovering a broken system"
date: 2014-01-28
forum: New to Ubuntu
---

### Post by cigtoxdoc on 2014-01-28
Please give me step-by-step keystrokes to do the following:

To access rescue mode, type rescue at the boot: prompt, or boot with the rescue/enable=true boot parameter. You'll be shown the first few screens of the installer, with a note in the corner of the display to indicate that this is rescue mode, not a full installation.

I cannot get my system started.  I can get to the Recovery Menu, but when I go to the root prompt, typing rescue does not do anything.  I need to recover files I made in the few hours before the system failed.

John

---

### Post by justleen on 2014-01-28
The steps outlined above are for booting from a live image. If you already have a system installed you have to use the rescue/enable=true boot parameter, which will drop you to a root prompt. Typing rescue there will not do anything indeed, you're already in rescue mode.
from there you can mount your disks and recover your data.

---

