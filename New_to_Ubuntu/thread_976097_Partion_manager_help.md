---
title: "Partion manager help?"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by joec369 on 2008-11-09
Hello,

Super Newb.  Super being not good.  I installed 8.10 dual boot with XP.  Worked great, not a glitch so far.  I am finding myself use Ubuntu more and more, so I need more space.  I shrank my windows partition and I now have a bunch of unallocated space that I want to add to my Unbuntu partition.  I tried to use Gparted which came with my distro, but it doesn't seem to want to resize the Unbuntu partition(or any of them for that matter).

Is there another tool to use? Can I do this while running the Unbuntu GUI? Or do I have to do it from the CLI?  If I do have to do it from the CLI how do I boot into it?  If there are any other posts/threads please feel free to point me there.

Thanks for the help in advance.
Thanks Joe

---

### Post by mojoman on 2008-11-09
> **joec369 said:**
> Hello,

Super Newb.  Super being not good.  I installed 8.10 dual boot with XP.  Worked great, not a glitch so far.  I am finding myself use Ubuntu more and more, so I need more space.  I shrank my windows partition and I now have a bunch of unallocated space that I want to add to my Unbuntu partition.  I tried to use Gparted which came with my distro, but it doesn't seem to want to resize the Unbuntu partition(or any of them for that matter).

Is there another tool to use? Can I do this while running the Unbuntu GUI? Or do I have to do it from the CLI?  If I do have to do it from the CLI how do I boot into it?  If there are any other posts/threads please feel free to point me there.

Thanks for the help in advance.
Thanks Joe

You can't resize the root partition when you use it. This means you have to unmount it. Boot the computer with a live CD (ubuntu installation CD fits the bill) and fire up gparted and give it another go. That way, your root partition will not be mounted and you can expand it to cover the free space.

/mojoman

---

### Post by joec369 on 2008-11-09
Thank you

---

### Post by mapes12 on 2008-11-09
Or, if you can't find GParted on your Ubuntu installation CD then burn yourself a GParted Live CD from here:  [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Always a good tool to have in your kit bag.

---

