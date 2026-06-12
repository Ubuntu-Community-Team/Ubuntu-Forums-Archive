---
title: "Uninstalling VirtualBox -&gt; Broken Kernel?"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by Eltern on 2008-08-28
I was messing around with installing VirtualBox yesterday, and it didn't work out. While I'm interested in figuring out the problems with that, I'm currently more concerned with the problems that arose when I uninstalled: my wireless and sound cards no longer work.

Since the various VirtualBox packages I was installing/uninstalling dealt with the kernel, I think something must have been pulled out that shouldn't have been. Since all my drivers have "just worked" during my Ubuntu experience, I have no idea how to go about fixing this. 

Any suggestions on what I should install to regain my previous functionality? My hunch is that this will be a single package, since that was how it was broken, but I'm no expert.

Thanks!

---

### Post by tuxxy on 2008-08-28
Search for virtualbox in synaptic and remvoe any packages you have installed

---

### Post by Eltern on 2008-08-28
Yes, did that. 

I don't think it's necessary to solving the problem, but here's a bit of a timeline of what I did:
- Install virtualbox
- Try out virtualbox
- A necessary packages is missing, but it's not sure which ones
- Install some packages
- Try it, doesn't work
- Install some packages
- Try it, doesn't work
- Install some packages
- Oh, my wireless and volume aren't working. Crud
- Hey, it works now! Oh well
- Remove all the virtualbox packages

The packages I was trying were the various virtualbox-ose-guest-modules and the virtualbox-ose-modules.

---

### Post by Eltern on 2008-08-28
Fixed: I was running off the linux-image-generic, instead of linux-image-386

---

### Post by tuxxy on 2008-08-28
Good stuff, mark the thread solved then now :)

---

