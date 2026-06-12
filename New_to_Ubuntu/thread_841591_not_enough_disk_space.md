---
title: "not enough disk space?"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by lolumadclan on 2008-06-26
Hello, I am dual booting Windows Vista and Ubuntu Linux. I am trying to install a game but it is telling me that I only have 700MB left and the game requires about 1 GB...but I have a 190GB hard Drive with 126GB free space...how should I go about fixing this?

---

### Post by Dutch70 on 2008-06-26
Install gparted, and look at your partitions. there's another way to do it, but sounds like you may be needing it anyway

---

### Post by drs305 on 2008-06-26
This command may provide some insight:
```
df -Th
```

---

### Post by lolumadclan on 2008-06-26
> /dev/sda5     ext3     12G   11G  651M  95% /


lol so when I tried using the Gparted Live CD I set it up and i guess when it was trying to run the program the screen became really fuzzy and unresponsive...anyway I should fix this?

---

### Post by drs305 on 2008-06-26
> **lolumadclan said:**
> lol so when I tried using the Gparted Live CD I set it up and i guess when it was trying to run the program the screen became really fuzzy and unresponsive...anyway I should fix this?

12GB is large enough for a root ( / ) partition although I prefer it a little larger. Depending on what the rest of the disk looks like, you could keep root on this partition and make and move /home to its own partition. The advantage of doing what's suggested in this paragraph is that you won't have to do a complete reinstallation and are less likely to wipe out something important. There will undoubtedly be other suggestions.

Here is a link on how to move home to it's own partition:
[ Create a separate home partition in Ubuntu]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by Dutch70 on 2008-06-26
> **lolumadclan said:**
> ...anyway I should fix this?

That really sounds like statement, then I finally noticed the ? afterward...lol. 

 So, how much RAM do you have? maybe that will help drs305 or someone else to be of more assistance!

---

