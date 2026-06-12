---
title: "HELP! I can't play Flash videos anymore."
date: 2008-09-20
forum: New to Ubuntu
---

### Post by ahuman on 2008-09-20
What happened? I automatically upgraded to 8.04 today. I went to YouTube and all the sudden I'm being told I have to reinstall Flash to watch videos, after just watching another video before the update completed. How can I fix this?

---

### Post by ahuman on 2008-09-20
The problem is my upgrade to Ubuntu 8.04 aka Hardy Hardon. I have a 64-bit processor that's not working with Flash in Ubuntu. This stinks big time.

---

### Post by ahuman on 2008-09-21
Yeah - I found the solution. My Flash is working again. I downloaded the link for Gutsy-Hardy users (those who use Ubuntu 7.10 or 8.04) here: [http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

I also downgraded to Firefox 2 by going to System/Synaptic Package Manager and deleting anything found by searching Firefox-3. I went to Add/Remove programs, searched for Firefox-2 and installed it.

---

### Post by Tatty on 2008-09-21
All you needed to do was:

```
sudo apt-get install flashplugin-nonfree
```

That script is no longer needed for 64bit flash, as the npluginwrapper now comes with the flash package.

:)

---

### Post by gjoellee on 2008-09-21
download a .deb here: [http://www.kshoster.net/?c=downloads&h=deb](http://www.kshoster.net/?c=downloads&h=deb)

---

