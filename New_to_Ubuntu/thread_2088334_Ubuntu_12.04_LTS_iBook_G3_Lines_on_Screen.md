---
title: "Ubuntu 12.04 LTS iBook G3 Lines on Screen"
date: 2012-11-26
forum: New to Ubuntu
---

### Post by nugent1998 on 2012-11-26
I'm having problems with graphics, I have Ubuntu 12.04 LTS on my iBook G3 Al005, 800MHz processor, 384MB PC133 SDRAM SODIMM. I can't explain what it looks like so I attached a picture.

---

### Post by newb85 on 2012-11-26
Did you install via Live CD/USB?  Did you experience any graphics issues during installation?

---

### Post by nugent1998 on 2012-11-26
I already installed it, during yaboot i have to press "tab" then type "old" for it to work properly, the Linux option which is the default option is when it does it. It didn't start until I shut it down to move it.

---

### Post by nugent1998 on 2012-11-30
Now it does it all the time after the kernel update

---

### Post by venividivici24 on 2013-03-01
I'm sorry for "bumping" this thread, but I have the solution (I think) to your problem. When your computer boots into the yaboot prompt, type in:   video=radeonfb: off (without the space, if I don't put the space in, the forums insert an emoticon)

 You will loose the ability to suspend and change the screen brightness, but at least it is usable. If you want 3D acceleration, go to the "No userspace mode setting 3d hardware acceleration" section and follow the instructions. PowerPc Known Issues page: [https://wiki.ubuntu.com/PowerPCKnownIssues](https://wiki.ubuntu.com/PowerPCKnownIssues)

I hope this helps you,

venividivici24

---

