---
title: "Can't extract .zip files now"
date: 2011-08-28
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Quackers on 2011-08-28
After running the last 2 days updates (one was ubuntu-restricted-extras) I cannot now extract .zip files.
It reports as in screenshot below.
Anybody else seeing this?

---

### Post by bash on 2011-08-28
Have been seeing this since a while (think about a 1-2 weeks). From what I can it's only with .zip. And using unzip from the terminal still works normally. 

Since I saw no other report on here, figured it for some quirk I get from time to time if I just keep running an updated alpha version for an extended period. Wanted to update to a fresh image anyways and guessed it would go away then.

---

### Post by Quackers on 2011-08-28
Very odd, as I extracted a .zip file two days ago, if I remember correctly.
Thanks bash :-)

---

### Post by Bowmore on 2011-08-28
Here's the bug on this issue:
[https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/829169](https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/829169)

A workaround is to install p7zip & p7zip-full to make file-roller work for zip-file too.

---

### Post by bash on 2011-08-28
> **Bowmore said:**
> Here's the bug on this issue:
[https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/829169](https://bugs.launchpad.net/ubuntu/+source/file-roller/+bug/829169)

A workaround is to install p7zip & p7zip-full to make file-roller work for zip-file too.

Thanks for the tip. Just tried it and now I can extract zips again.

---

### Post by Quackers on 2011-08-28
Thanks Bowmore - happy again :-)

---

