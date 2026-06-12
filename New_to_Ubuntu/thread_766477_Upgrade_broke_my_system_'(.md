---
title: "Upgrade broke my system :'("
date: 2008-04-25
forum: New to Ubuntu
---

### Post by achelis on 2008-04-25
Hi
Just upgraded to 8.04 using the Update Manager, and now Ubuntu can only boot in recovery mode.

As I'm fairly new to Linux I don't really no where to start, and I suppose I should have just stayed away from upgrading.

---

### Post by PmDematagoda on 2008-04-25
Could you please state your problem a little more specifically? What problem do you get when trying to boot Ubuntu in normal mode?

---

### Post by steve-shinn on 2008-04-25
I suspect that it's not broken as such. Most likely IMO to be a problem with the monitor settings etc. within Xorg.
When I upgraded, I had to sort out the resolutions as they had defaulted to 1280 x 1024.


I'm not an expert on Xorg, but hopefully some will come along shortly, that is.

---

### Post by achelis on 2008-04-25
I guess you're right :) But having my computer not booting as the first thing in the morning made me panic.

I've re-enabled restricted drivers and am now able to boot when I remove the quiet splash --help from the "boot-line" or whatever it's called.

Only problem left is my screen is flickering worse than an electrocuted salmon on dry land.
For this I'm almost certain I solved it in 7.10 by running ```
sudo nvidia-settings 
``` but nvidia-settings doesn't seem to exist anymore??

Think I'll get some breakfast and then see if it works afterwards :)

@PmDematagoda: The splash screen froze (it still does when enabled) and disabling it I got a "Kernel Panic!".

---

### Post by PmDematagoda on 2008-04-25
So now are you able to boot Ubuntu in normal mode properly by disabling splash and installing the restricted drivers?

If so, what error do you get when trying to open Nvidia-Settings?

---

### Post by achelis on 2008-04-25
Heh - I get
```
 The program 'nvidia-settings' is currently not installed.  You can install it by typing:
sudo apt-get install nvidia-settings
bash: nvidia-settings: command not found

```

Teaches me to read the error message doesn't it.. :)

Sorry about that... installing it did the trick and I'm back to normal again.

Thanks a lot for pointing me in the right direction.

Is there a way to mark this as solved?

---

### Post by ace007 on 2008-04-25
You'll find error messages in Ubuntu, unlike windows actually provide some good advice

---

