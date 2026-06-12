---
title: "I think Nautilus is broken."
date: 2008-09-14
forum: New to Ubuntu
---

### Post by elise1030 on 2008-09-14
A couple of days ago my Ubuntu drive messed up and told me on boot there were corrupted segments and so on. I went thru the fix procedure which allowed me to get back into Ubuntu. Now programs won't open up and Nautilus tell me it can't read the file and some stuff is in read only permission and I can't change it back to read/write permissions. 
When I open up a "place", down the sidebar there is like jumbled icons that look like should be words but when I click on it Nautilus says it can't read it or something.

Thanks for the help and sorry if my wording is a bit vague.

---

### Post by doctorbighands on 2008-09-14
If it were me, I'd boot into a Live CD environment and try a file system check.

More info here: [http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem](http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem)

---

### Post by elise1030 on 2008-09-14
I'm currently posting this from Ubuntu. It says Nautilus cannot handle this kind of locations. What does this mean? Can I repair Nautilus?

---

### Post by doctorbighands on 2008-09-14
> **elise1030 said:**
> I'm currently posting this from Ubuntu. It says Nautilus cannot handle this kind of locations. What does this mean? Can I repair Nautilus?

You can't (and shouldn't) run a file system check on a mounted drive (in other words, from "inside" Ubuntu). You need to pop an Ubuntu CD into your drive, and reboot your computer using the CD instead of the hard drive. Once that's finished booting up, you can proceed with the file system check.

---

### Post by elise1030 on 2008-09-14
Thanks I'll do that. Will I have an option to check the filesystem when I boot from the Live CD?

---

### Post by doctorbighands on 2008-09-14
> **elise1030 said:**
> Thanks I'll do that. Will I have an option to check the filesystem when I boot from the Live CD?

There won't be anything you can "just click on," if that's what you're asking. You'll need to enter a command into the terminal (Applications > Accessories > Terminal) in order to run the check. If you take a look at the link provided above, it should give you everything you need to get the job done. If you need more explained, ask away! :)

---

