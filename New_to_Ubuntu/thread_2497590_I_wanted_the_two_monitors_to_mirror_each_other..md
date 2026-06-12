---
title: "I wanted the two monitors to mirror each other."
date: 2024-05-11
forum: New to Ubuntu
---

### Post by louie77777 on 2024-05-11
Hi, I'm new to linux. My development environment is ubuntu20.04, the graphics card is 4070ti, and I have configured the driver. After I closed the desktop graphics program and started my application directly at boot time, I found that I couldn't configure the monitors properly when I connected the two monitors. I wanted the two monitors to mirror each other. When I want to use xrandr, I can't set it up because the x service has been turned off. Excuse me, how can I solve this problem?

---

### Post by TheFu on 2024-05-11
**lxrandr** has a simple GUI with a check box that will mirror displays
if
a) the card supports it (and the connections are made/working)
b) if X/Windows is the display server (I don't know about Wayland)

For Wayland (a new, different display server), you'll need to check the _Ubuntu Desktop Guide_ for how to accomplish this. Google finds it easily.

You can always choose to use X/Windows as your display server instead of Wayland.  There are slight performance and security issues doing this, but X/Windows functionality has been available since before Linux even existed, so it is very mature.  

Perhaps in another 10 yrs, Wayland will provide all the same capabilities.  IDK.  Perhaps Wayland already provides this capability.  IDK, since it currently breaks a few of my automated workflows, so I try Wayland about once a year for 15 minutes to see if it meets my needs. So far, nope.  I have needs that most people don't, it seems. Though what I do was common in the 1990s and pretty much everyone worked in a similar way.

Oh, lxrandr is the app used by Lubuntu to control the display, so if you aren't running that DE, expect to install it. It is a small package and doesn't care which DE is being used.

---

