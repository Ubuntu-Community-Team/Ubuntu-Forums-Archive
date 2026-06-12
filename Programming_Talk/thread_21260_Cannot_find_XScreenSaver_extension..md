---
title: "Cannot find XScreenSaver extension."
date: 2005-03-21
forum: Programming Talk
---

### Post by dcraven on 2005-03-21
Hello,

I just switched from a source based distrobution to try Ubuntu. The transition was excellent. The only issue I'm having with binary based distrobutions is that none of the -dev packages get installed which makes things difficult to compile yourself. Normally this is relatively easy to overcome, but I think I need assistance this time.

I'm trying to build Gossip manually so that I can apply my personal patches to it (this is why I'm not using apt for it). Now I've never had issues before compiling Gossip, but now on Hoary, I get a configure error, the relevent snippet is below:
```

... lots of successful checks etc ...
checking for XScreenSaverRegister in -lXext... no
checking for XScreenSaverRegister in -lXss... yes
configure: error: Couldn't find XScreenSaver extension.
make: *** [config.status] Error 1
```

Then obviously it dies. My riddle to the forum crowd is, what package to I need to install to fill the XScreenSaver extension requirement? I'm at a loss...

Thanks,
~djc

---

### Post by daniels on 2005-03-21
libxss-dev

---

### Post by dcraven on 2005-03-21
[QUOTE=daniels]libxss-dev[/QUOTE]

I thought the same, but it does not satisfy the requirement. Your reply, however, confirms that I'm not going crazy, and that there must be an error in the Gossip configure.in script. I'll have a look there.

Thanks for the help!
~djc

---

