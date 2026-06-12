---
title: "Firefox &amp; Flash"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by nrpgeek on 2008-05-07
How do I enable Flash with Firefox?

I've looked in all the categories in Tools|Add-ons and it's not listed.

I've been to the Adobe website, downloaded the tar, rpm and yum files, followed the instructions for each of them and nothing happens!

Whats happening (except nothing!).

I didn't have any problems in Gutsy, I dont even remember having to install it!

---

### Post by perlluver on 2008-05-07
> **nrpgeek said:**
> How do I enable Flash with Firefox?

I've looked in all the categories in Tools|Add-ons and it's not listed.

I've been to the Adobe website, downloaded the tar, rpm and yum files, followed the instructions for each of them and nothing happens!

Whats happening (except nothing!).

I didn't have any problems in Gutsy, I dont even remember having to install it!

It's not installed by default, type in the terminal, sudo apt-get install flashplugin-nonfree.

Make sure your restricted repos are enabled.

---

### Post by Joeb454 on 2008-05-07
The instructions for the .tar file from the Adobe site should work.

I've used it many times before :confused:

---

### Post by nrpgeek on 2008-05-07
Thanks Guys, problem solved. Help really appreciated!

---

### Post by shifty_powers on 2008-05-07
> **Joeb454 said:**
> The instructions for the .tar file from the Adobe site should work.

I've used it many times before :confused:

easy, go onto youtube, wait for the bar at the top to pop up asking you to install the missing plugin and use one. I generally use the gnuflash, or whatever it is called, but the adobe one is fine. Just that adobe is non-free.

otherwise check in the add/remove section of your applications menu ;)

---

