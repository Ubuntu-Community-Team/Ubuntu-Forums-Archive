---
title: "Issues with dual monitors"
date: 2014-03-11
forum: New to Ubuntu
---

### Post by yehowraah on 2014-03-11
Hi, everyone

I've been running a dual display setup with two cheap monitors for the past couple of weeks. Everything worked fine, at first. Nvidia-settings recognized both displays perfectly, and setup was straightforward. The first monitor is an Acer-P191W, and the secondary is a Hanns-G HW173D.

Today, I stupidly unplugged the Hanns-G from the wall without completely disabling it in Ubuntu first, or even shutting it off. After doing so, my Acer stopped working as well. Now, my system only ever recognizes the Hanns-G. My GPU(9800GTX) has two DVI ports, DVI-1-2 and DVI-1-3. Regardless of which one the monitors are plugged into, the Hanns is the only one that works - my Acer isn't even detected at all.

If I boot to the login screen with the Hanns-G, unplug it, and then plug the Acer into that same port, it is semi-detected, but it immediately loses signal again after I attempt to login. When I switch from Nvidia's drivers to Nouveou, however, I'm able to log in fine, and it only loses signal upon restarting.

Now I switched out the DVI cable on my Asus with a VGA cable + VGA to DVI adapter, and it's perfectly detected as DVI-1-1. Unfortunately the Hanns-G isn't recognized with this setup, but if I unplug the Acer, it's detected again. It's a somewhat functional workaround for now, as I can at least use the superior Acer but I really want to get my system functioning the way it was before, so any help would be much appreciated.

Thanks in advance!

---

### Post by TheFu on 2014-03-12
Have you rerun the nvidia-settings app again to reset the configuration in /etc/X11/xorg.conf?
Since that file is protected, sudo is needed.
**sudo nvidia-settings**

This assumes you have replaced the Nouveou drivers with proprietary nvidia drivers again.  I'm sorta shocked that unplugging a monitor would alter the xorg.conf file - did that actually get updated last time or has the machine been running since you made the original changes?

---

### Post by yehowraah on 2014-03-14
Sorry for not replying earlier. These past couple of days have been hectic.

It doesn't make any sense, but none of this happened until the moment I unplugged the Hanns. Actually, I haven't even installed anything in the past several days. I rebooted a few times shortly after it started having this problem. I even tried hooking up one other monitor - they both have the same issue, except for that stupid Hanns-G! I didn't remember to root before trying to reset Xorg.conf, so I tried that now, but no luck. 

I even removed my Nvidia GPU entirely and switched to onboard graphics, but flabbergastingly, the problem remained. Switching the Acer to a VGA cable worked with onboard, though, so that's why I tried that same cable with my dedicated card with a VGA to DVI adapter. Running xrandr -q in the terminal actually got both monitors recognized flawlessly, too. 

Thinking that whatever had gone awry had been fixed, I tried reconnecting the Acer using the DVI again, but it still isn't recognized. xrandr -q shows whatever port I plug it into as "disconnected." I haven't had a chance to try the third monitor again, but I get the feeling nothing has really changed. :( I also have the Acer set up as Primary once again, but it seems like that setting isn't recognized during startup, as the boot screen still defaults to the Hanns-g.

---

