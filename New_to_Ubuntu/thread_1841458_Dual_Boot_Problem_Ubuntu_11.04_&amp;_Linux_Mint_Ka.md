---
title: "Dual Boot Problem: Ubuntu 11.04 &amp; Linux Mint Katya (11)"
date: 2011-09-09
forum: New to Ubuntu
---

### Post by tlcmd on 2011-09-09
I'm a relative noobie to the world of Linux Distros and am learning on an older PC (3.4 Celeron, 512 RAM, 40 G HDD). 
I have 1st installed linux Mint 11 (Katya) and then Ubuntu 11.04 along side it.. Now Linus Mint does not boot. Yes it's there. I'm certain that there is a Mickey Mouse solution I have overlooked. I'd appreciate a solution. 

Although I have a doctorate degree, I am still 70 years old so please keep it simple for old "stupid" here and if you give me a command line to put in the terminal, please give the whole thing from "sudo.....til the end.
One of the biggest problems wwe noobies have is the expectation that we know more than we do and the solutions given frequently are more complex than we can understand. 

Thanks,
tlcmd (aka ****)

---

### Post by Nickjpost on 2011-09-09
You could try boot repair....the doc is for windows, but it basically repairs grub so you can boot both systems.

Here's the link: 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub)

---

### Post by oldfred on 2011-09-09
I often recommend boot-repair as it can do a lot of repairs, but you just may need this to rerun the os-prober from a terminal:

```
sudo update-grub
```

---

