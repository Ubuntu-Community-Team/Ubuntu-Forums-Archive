---
title: "enable apt automatic: 10periodic as in Server Guide, or 02periodic as in crop script?"
date: 2012-03-13
forum: New to Ubuntu
---

### Post by theoneness on 2012-03-13
Hi community,

I'm installing Ubuntu 11.04 server on an office computer to try and setup a staging server for our websites. I'm checking out the Ubuntu Server Guide and get to the section on Automatic updates using Apt, which i'm interested in activating so as to save me time running routine updates and upgrades.

I've run into a bit of a standstill because I followed the directions of the Server Guide on this page:
[https://help.ubuntu.com/11.04/serverguide/C/automatic-updates.html]("https://help.ubuntu.com/11.04/serverguide/C/automatic-updates.html")

and I quote:

> To configure unattended-upgrades, edit /etc/apt/apt.conf.d/50unattended-upgrades and adjust the following to fit your needs.

Which I do.

Then, I read this further down the page:

> You can read more about apt Periodic configuration options in the /etc/cron.daily/apt script header.

Which I also do; wherein, the /etc/cron.daily/apt script states, in the aforementioned header:

> Create /etc/apt/apt.conf.d/02periodic file to set your preference.

and it goes on with more details.

So there is an unexplained difference in file names to edit. is it **10periodic** as the *Ubuntu Server Guide* states, or **02periodic** as the *cron.daily/apt* script states?

Thank you, folks!

---

### Post by theoneness on 2012-03-13
Hmm, wish i had noticed that title typo. Obviously should read "cron" script, not "crop".

---

