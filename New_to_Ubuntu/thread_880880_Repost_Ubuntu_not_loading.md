---
title: "Repost: Ubuntu not loading"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by Polish Rifle on 2008-08-05
I helped C-man install Ubuntu on his computer the other day.  One times out of ten it will actually load, but all the other times it gets to the Ubuntu load bar screen and it feezes when it has loaded 1/8 of the way.

I'm reposting because I don't think he got much help on his previous post.  He titled it "help!" haha.

He really wants to give it a try but Ubuntu won't even load.

---

### Post by Ru$$i@N on 2008-08-05
I assume you're using a live CD to try ubuntu. I think, most of the time, the problem is with RAM, to be precise - small amount of it :)
Could you tell me how much RAM does your buddy's computer have?

---

### Post by gjoellee on 2008-08-05
if he have under 384MB of RAM the live CD won't work, you should use Xubuntu instead then the minimum RAM for Xubuntu is 192 if you want to install it form live CD and 128MB if you just want to run live CD

---

### Post by Polish Rifle on 2008-08-05
Ubuntu is already INSTALLED on a 256 MB machine.

---

### Post by Ru$$i@N on 2008-08-05
oh oops, misunderstood.
Then when Grub loads, press Esc (if it's in that quick mode, where you don't choose the system to load), and edit the entry with the system. Press "e", and at the end of the second line (the longest line) there should be something like "quiet splash", change "splash" to "nosplash". Read the instructions on the bottom how to get back and boot ( i think you just need to press "b")
"nosplash" is exactly what it sounds like. Instead of the splash you'll see what processes get loaded. This will help you see what might be the problem at the boot.

oh and yeah, this edit is just a one-time thing, it will reset back to previous settings after you reboot.

---

### Post by Polish Rifle on 2008-08-07
He installed it on  his laptop and it works fine.  So...maybe we just need to reinstall on the desktop?  Frustrating nonetheless.

---

