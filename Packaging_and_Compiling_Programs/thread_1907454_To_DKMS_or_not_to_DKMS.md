---
title: "To DKMS or not to DKMS?"
date: 2012-01-11
forum: Packaging and Compiling Programs
---

### Post by djsephiroth on 2012-01-11
This is mostly to bounce some thoughts off of persons presumably more knowledgeable than myself, rather than a specific technical inquiry. I hope this is the right venue.

I have built a kernel module. I need to put it on several identical systems. 

The systems will of course receive upgrades to the kernel over time, thus the kernel module will need to be rebuilt against the apropos kernel(s) as they are released. 

The systems in question need to be as free of cruft as possible, and have limited (practically nonexistent) direct Internet connectivity. (Updates come from a local apt cache server.)

Would DKMS be my best option for ensuring that the systems have the kernel module they need?

Would DKMS require the systems to all have development tools that might cruft things up? And would the extra tools not require more strain in terms of adding to the amount and size of updates needed on a regular basis?

What are some other options?

I have considered creating a server that will build the module for each kernel as it is released, then add the debs to a local repo. However, this strikes me as potentially more complicated and less supported than using DKMS. Thoughts?

---

