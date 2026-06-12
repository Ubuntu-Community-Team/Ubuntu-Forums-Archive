---
title: "Desktop Virtualization"
date: 2011-10-05
forum: New to Ubuntu
---

### Post by DiegoTc on 2011-10-05
Hi
I am trying to build a computer lab for a small school.
I read about the Linux Terminal Project, but I had some doubts.

First of all.
The School doesn't count with money, so they are not planning in buying a lot of computers.

I read about the LTS project, and I though I can use this.
My idea is the fallowing. Have one CPU, and with this have 4 or 5 monitors connected to it. But I have my doubts about this. How do I connect the mouse, keyboard, speakers? 

So searching on Internet I found NComputing [http://www.ncomputing.com/classroom-in-a-box](http://www.ncomputing.com/classroom-in-a-box)

This is a great idea, but it seems they don't give support to the new versions of Ubuntu.

If you have a better idea, I would like to know

Thanks

---

### Post by Lars Noodén on 2011-10-05
> **DiegoTc said:**
> My idea is the fallowing. Have one CPU, and with this have 4 or 5 monitors connected to it. But I have my doubts about this. How do I connect the mouse, keyboard, speakers? 


It's doable, but requires hacking the X server's configuration.

It's called [multiseat](http://www.google.com/search?sclient=psy-ab&hl=en&q=multiseat+-microsoft).  You can get it if you have multiple graphics cards (or the right kind of graphics cards) in the one computer and then edit your X server's configuration accordingly.  The company Userful specializes in it.

---

### Post by thomasw_lrd on 2011-10-05
I assume they have some money to spend on this project?  I would check on ebay for older used pcs.  You should be able to find a copy of Ubuntu that will run on them.  We just picked up two for 150, that both had some small harddrives, 2 gb of ram, and dual-core processors.  Might be worth looking into depending on your budget.  You could also call any local community colleges and see if they have any older pcs they are getting away.

---

