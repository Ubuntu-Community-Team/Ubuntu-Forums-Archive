---
title: "Laptop Crashed and stopped Booting"
date: 2022-11-01
forum: New to Ubuntu
---

### Post by thund3rmare on 2022-11-01
Hello, 

Although I'm running Ubuntu for 3 years now, my experience level with it is that of a beginner, so I've decided to ask for advice before I make my situation worse.

I was installing Python3 and OpenCV to explore Computer Vision a bit.
 After I installed the prerequisites, I noticed I suddenly didn't have internet anymore and couldn't finish installation.
 At first, I thought my network went down, but I quickly noticed all my other devices had internet.
It looked like Ubuntu didn't have access to the hardware, also the "power off" button disappeared. 

I force restarted the Laptop. It loaded up to the HP logo and then stopped booting. (I waited ~15 min)
I've tried this a couple more times. Then started GRUB and got a boot-diagnostic, where I noticed some errors.
(attached a picture of the terminal, maybe it's useful)

After Googling the Error and reading what others with similar problems have gone through, I've noticed a pattern of making a live USB version and running boot-repair.
(I could not remember at that time what my Ubuntu version was, so I downloaded Ubuntu 22.04 LTE for my USB)

This is my[ Boot-info Summary ]("https://paste.ubuntu.com/p/Wcv9NSFxcG/") 

Any Idea what happened? Should I go ahead with the repair?

Thank you for your Help and Time!

---

### Post by MAFoElffen on 2022-11-01
Yes. I would do the recommended repair for 'boot-repair'.

I don't see anything quarky about what 'boot-info' found, and it looks fairly straight forward in it's recommendations of repair.

---

### Post by thund3rmare on 2022-11-02
Thank you for the reply. 
I ran the recommended repair and the behavior did not change. 
It still does not boot.

[This is the paste generated at the end of the Boot-Repair.]("https://paste.ubuntu.com/p/wSgpyQX9Hy") 

At this point, I'm thinking I'll just try to save any important files I have and reinstall ubuntu.

---

