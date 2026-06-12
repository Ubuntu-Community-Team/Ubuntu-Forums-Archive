---
title: "[SOLVED] Citadel mail server question"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by greavette on 2008-09-03
Hello,

I've been looking for the requirements to run the Citadel mail server, but I can't seem to find it at their website...I also couldn't find a forum either so I thought I would ask here.

I'm looking to run an easy to setup mail server and Citadel seems to fit the bill for my small office.  I have a small fanless computer (512 MB of Ram, 433 MHz processor) and wanted to see if a mail server could run on this small box.  The fanless PC is a Koolu and comes preloaded with Ubuntu on it.

Can anyone point me to where I can find if Citadel will work on this small PC?

Thanks,

Charles.

---

### Post by jonabyte on 2008-09-04
The site mentions prerequisites for Debian/Ubuntu here:

[http://www.citadel.org/doku.php/installation:easyinstall:prereq-debian.html](http://www.citadel.org/doku.php/installation:easyinstall:prereq-debian.html)

The install page:

[http://www.citadel.org/doku.php/installation:easyinstall:easyinstall](http://www.citadel.org/doku.php/installation:easyinstall:easyinstall)

I can't comment on whether this will work on your hardware or not.

---

### Post by schmidtbag on 2008-09-04
i would say from now on, since you can admit yourself the computer is not all that impressive, you should just try installing the program anyway.  the chances of it performing well is fairly slim but its not like you have much to lose

---

### Post by halitech on 2008-09-04
Memory: [http://www.citadel.org/doku.php/faq:generalquestions:what_are_the_memory_requirements#what.are.the.memory.requirements](http://www.citadel.org/doku.php/faq:generalquestions:what_are_the_memory_requirements#what.are.the.memory.requirements)

Can't find anything on CPU requirements but I had it running (briefly) on My P4 1.8 and it seemed okay (uninstalled it as I didn't like the layout and really don't need to run a mail server) so you may find it sluggish on a 433 unless that is all it is doing.

---

### Post by greavette on 2008-09-08
Hello,

Just thought I should close this post by replying back with my results.

I've successfully installed Citadel on this little fanless PC without issue.  Runs like a champ.  So far I've only tested it with 3 people logged in but no issues with performance so far.  I'll be using this in a small office with 3 people anyway so my test isn't far off from production for me anyway.

I've noticed that the CPU gets maxed at times but there is still lots of Ram left over. 

I've also got Nagios running at the same time, but I'm not sure I'll keep it and leave the Koolu just for the mail server.

I like Citadel so far, although getting used to the rooms is a little weird and I can't say I like the web interface, but it was very easy to install and runs great.

Thanks!

Charles.

---

### Post by jonabyte on 2008-09-09
Thanks for the update.

---

