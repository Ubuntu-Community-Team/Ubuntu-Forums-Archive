---
title: "choppy video, could it be graphics driver? (newbie)"
date: 2011-09-25
forum: New to Ubuntu
---

### Post by wedgec on 2011-09-25
Hi all

I'm a total newbie to Linux, after using windows, and I have to say I'm liking it so far.

I have noticed that my video on youtube isn't running well though. I'm using a HP Mini 110, which I guess only has onboard graphics, could this be the problem? I never had this problem on windows.

I'm using Ubuntu 11.04.

Any help that could be given would be greatly appreciated!

---

### Post by BeRoot ReBoot on 2011-09-25
According to google, that only has Intel's atom-based integrated graphics. The driver isn't the issue here, it simply can't do HD video in flash.

Do you also get stuttering on 480p and lower resolution videos?

---

### Post by wedgec on 2011-09-25
I have just found this handy bit of code which has got youtube working ok:

[B]sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release  -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo  apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated  install medibuntu-keyring; sudo apt-get -q update

[/B]I'm having the issue now with my .mts files from my camcorder though, which may be the HD problem you mentioned?! I have also tried converting these to .avi on winff, but it won't do it?!

Should this be possible, or am I better off doing this sort of thing on my desktop PC?

Thanks

---

