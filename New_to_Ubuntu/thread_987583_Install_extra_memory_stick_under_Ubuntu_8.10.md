---
title: "Install extra memory stick under Ubuntu 8.10?"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by bettyhills on 2008-11-19
I installed Intrepid onto an older PC that has specifications described in the "signature line" below.  (The former Win98 OS is totally gone.)  Ubuntu is working well.

I own an extra "stick" of 512mb memory for this machine that Win98 (in the PC's former life) would not recognize due to limitations in Win98.  The memory is perfect.  There is a vacant slot available.  If installed it would bring the memory in the box up to 1gb.  

Can anyone familiar with Intrepid tell me whether Ubuntu 8.10 would be able to recognize and use the extra memory if I install it?

If so, is there anything I need to do to get the new memory stick recognized by Linux, other than install it and turn on the PC?

Thanks in advance.

---

### Post by taurus on 2008-11-19
If the BIOS is happy with it, Ubuntu should be too.  So, unplug the power cord and open the box.  Put in the extra stick.  Power it back on and go into the BIOS to see if it even detects the additional RAM.  If everything is fine in there, boot up Ubuntu and see what's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
free
```

---

### Post by Therion on 2008-11-19
> **bettyhills said:**
> Can anyone familiar with Intrepid tell me whether Ubuntu 8.10 would be able to recognize and use the extra memory if I install it?
Yes, it would.

> **bettyhills said:**
> If so, is there anything I need to do to get the new memory stick recognized by Linux, other than install it and turn on the PC?
No, there's isn't.

---

