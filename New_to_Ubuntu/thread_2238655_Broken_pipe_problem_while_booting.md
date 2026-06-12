---
title: "Broken pipe problem while booting"
date: 2014-08-09
forum: New to Ubuntu
---

### Post by alma2 on 2014-08-09
Hello guys! OK, I have installed ubuntu 12.04 alongside windows 7. It was all working regularly until last few days. I'm getting the "cannot write bytes broken pipe" while booting. I've read other threads about this problem, but the difference is, I can still boot ubuntu. Another problem I have, is when I go to the Additional drivers section I get " No proprietary drivers are in use on this system". Since I'm a nooby i don't know what does this actually means. If it is a problem, could it be that the problems are related? I appreciate any help or sugestion I get.

---

### Post by verymadpip on 2014-08-09
Hi there.
I get the same message when booting my MSI U180 netbook, which functions perfectly well.
I think, in my case, it's related to an odball graphics chip. (GMA3600, PowerVR).
As I say the machine does everything I want it to do without any problems, so I tend not to worry about it.

Hopefully someone may be able to give you more information on what the message actually means.

---

### Post by Jonathan Precise on 2014-08-09
Yes, If you can still boot ubuntu, there should be no problem.

About the "Install proprietary drivers", if there are none, there shouldn't be any problem either.

---

### Post by Rob Sayer on 2014-08-10
One thing I've learned the hard way is not to go into Additional Drivers and install anything without looking it up first.  it doesn't always work properly because sometimes the drivers ... which are provided by the peripheral manufacturer ... haven't been updated properly.

The broken pipe message the OP got may very well be video related.  Open a terminal and paste this into it:

```
sudo lshw -C video
```

enter password and wait for it.  Copy and paste that back here, wrapped in code tags.

I'm familiar with the system described in post #2 because this netbook uses the GMA3600 too.  The reason for it is that Intel outsourced the video adapter and they won't release the source code.  So it works well enough for me as a netbook but it wouldn't lay big HD video files very well.  It doesn't support 3D hardware acceleration and this is where that piping message comes from.

There's not enough info by the OP to tell there though.

---

