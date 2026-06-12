---
title: "Plain white screen when I boot Ubuntu 12.04 from a DVD"
date: 2014-03-31
forum: New to Ubuntu
---

### Post by jack61 on 2014-03-31
Hi folks

I have a new 64 bit Packard Bell laptop running Windows 8. Processor: AMD A4-500 APU, 1.5 GHz; graphics: Radeon Graphics; RAM: 8 GB.

I am trying to get Ubuntu 12.04 to boot from a DVD, but all I get is a loading screen followed by a lot of writing, which is replaced by a completely blank, white screen before I can read it.

I've tried v13.10 also, with the same results.

I found out that people dealt with similar problems by specifying 'nomodeset' in the commands for loading. Trying this, I got Bash but no desktop.

I might be way off the mark here, but I then tried the 'startx' command. I got:

"[KMS] drm report modesetting isn't supported.
(EE)
Fatal-server error:
(EE) no screens found(EE)"

What can I do?

Thanks,
Jack

---

