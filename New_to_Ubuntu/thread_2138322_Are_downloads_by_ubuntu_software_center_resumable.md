---
title: "Are downloads by ubuntu software center resumable?"
date: 2013-04-23
forum: New to Ubuntu
---

### Post by sherby on 2013-04-23
I'm on a slow connection, wondering will i be able to resume large downloads?

---

### Post by Cheesemill on 2013-04-23
I believe so, yes.

I don't have any experience of the Software Centre myself as I prefer to use the terminal to install programs, but when using the 'apt-get' command to install software if I cancel it in the middle of a download it will resume from where it was when I next run the command.

As the Software Centre is simply a graphical front-end to the exact same apt-get command that I use in the terminal then I would presume that exactly the same thing happens.

---

### Post by pqwoerituytrueiwoq on 2013-04-23
packages are saved to [FONT=courier new]/var/cache/apt/archives/[/FONT]
you can copy the contents to another system to save it download time

---

### Post by Buntu Bunny on 2013-04-23
> **pqwoerituytrueiwoq said:**
> packages are saved to [FONT=courier new]/var/cache/apt/archives/[/FONT]
you can copy the contents to another system to save it download time

Good tip, thanks.

---

### Post by Paqman on 2013-04-24
Individual packages aren't resumable, but you can stop a download part way through and any packages that have already downloaded will still be sitting in the APT cache.

---

### Post by B45op on 2013-04-24
very handy to know as my router keeps dying on me.

---

