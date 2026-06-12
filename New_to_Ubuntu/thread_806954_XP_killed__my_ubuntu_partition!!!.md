---
title: "XP killed  my ubuntu partition!!!"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by destructaball on 2008-05-25
I recently [grudgingly] installed XP on my computer because I need one of the programs for work. Now I've installed it the GRUB menu doesn't come up, how am I supposed to boot ubuntu?

Second question, why is my computer so slow and virus filled already.... oh wait I can answer that its M$

---

### Post by PriceChild on 2008-05-25
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

(found with search for 'recover grub' on wiki.ubuntu.com)

---

### Post by Inxsible on 2008-05-25
XP, by default writes the loader to mbr. So your grub has been overwritten. You can get Supergrub disk and restore your Grub again

---

### Post by lswest on 2008-05-25
answer to question 1: third line of my sig, it's a link to a how-to i wrote on re-installing bootloaders (including GRUB).  That will allow you to boot Ubuntu again.

2: It's not Linux ;)

*EDIT* wow...four replies in the same minute :P

---

### Post by Joeb454 on 2008-05-25
That's what Windows does - it'll overwrite the MBR when you install it :)

You may want to check this wiki page: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Sunfist on 2008-05-25
The XP install probably overwrote GRUB, you will need to reinstall Grub. I am kind new at this LInux stuff myself, but I know you can do it using the SuperGrub software. There is also a way using the Live CD also, I am sure someone can tell you how to do that. If you do a search for 'reinstalling grub' it should come up with something.

---

### Post by destructaball on 2008-05-25
Wow thanks six answers in a minute. I was tempted to ring XP support be put on hold for fourty minutes, cut off twice then told that it wasn't their fault they fuc...errr...messed up my computer but this way works too lol.

Ubuntu has a sweet comunity.

---

### Post by Joeb454 on 2008-05-25
> **destructaball said:**
> Wow thanks six answers in a minute...<rest of post>...Ubuntu has a sweet comunity.

No problem :) That page came in handy for me ;) And thanks

---

