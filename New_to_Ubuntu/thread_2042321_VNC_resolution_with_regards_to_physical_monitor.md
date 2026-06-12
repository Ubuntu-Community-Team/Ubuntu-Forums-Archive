---
title: "VNC resolution with regards to physical monitor"
date: 2012-08-14
forum: New to Ubuntu
---

### Post by Headcase_Fargone on 2012-08-14
I'm running Ubuntu 11.04 on a machine that has an older monitor attached to it.  This monitor supports a maximum resolution of 1280x1024.  Though I'm rarely in front of this machine I do use the monitor from time to time.

The issue I'm running into is that using VNC (X11 I think?) the maximum resolution I get is that same 1280x1024.  Is it possible to have a resolution of, say, 1600x1200 when in VNC and 1280x1024 when using the physical monitor attached to the machine?

I've tried adding the "Display" subsection to xorg.conf but VNC won't even run after that change and I had to copy my backup back over.

Is this even possible?

---

### Post by lukeiamyourfather on 2012-08-14
As far as I know, no, that is not possible since VNC uses the framebuffer. What might work better is ssh with X tunneling. An example command is below, note the case of the "X" argument.

```
ssh -X luke@workstation4
```

Then if you run a command like "firefox" it will draw the GUI locally but the process will still be on the remote machine. Windows for processes running on the remote machine could then be maximized or whatever as if they were local windows.

---

### Post by Headcase_Fargone on 2012-08-14
I'll give that a try.  How do you set the resolution if you don't have a monitor though?  Is VNC limited to 1280x1024 in that case or can you set it to whatever you'd like?

---

### Post by lukeiamyourfather on 2012-08-14
> **Headcase_Fargone said:**
> I'll give that a try.  How do you set the resolution if you don't have a monitor though?  Is VNC limited to 1280x1024 in that case or can you set it to whatever you'd like?

VNC uses whatever the framebuffer resolution is. If there's no monitor it could be whatever, like 1600x1200. Though if you set the resolution to 1600x1200 you won't be able to use the physical monitor since that would exceed the specifications of the monitor. I'm not sure what you're trying to do but VNC is almost never the right answer to a problem.

---

### Post by Headcase_Fargone on 2012-08-14
> **lukeiamyourfather said:**
> VNC uses whatever the framebuffer resolution is. If there's no monitor it could be whatever, like 1600x1200. Though if you set the resolution to 1600x1200 you won't be able to use the physical monitor since that would exceed the specifications of the monitor. I'm not sure what you're trying to do but VNC is almost never the right answer to a problem.

I never really fooled around with ssh as the built-in VNC and telnet hosts have worked fine for my purposes until recently.  I'll do some reading on X11 forwarding, thanks.

---

