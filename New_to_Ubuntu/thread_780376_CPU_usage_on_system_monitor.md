---
title: "CPU usage on system monitor"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by mikebravo on 2008-05-03
I have a good 2GHz Intel Core 2 Duo CPU in my computer. When I bring up the system monitor to look at my CPU usage under minimum load, they seem to go berserk. One core will be flat on zero and the other will have peaks and valleys that average around 60 percent, and then the useage will flip flop. They keep doing this indefinitely, staying 180 out of phase. Why? While searching these forums for an answer, I learned of the terminal "top" command. When I used that, it confirmed something I already suspected: the CPU's do not demonstrate that behavior until you open system monitor to the system resources tab. Before, top would be root using 2% CPU and after, top would be Xorg using 70 % CPU. My questions are 1) is this normal?  2)Why does it happen? and 3) If using the GUI to observe CPU load has this effect during light load, how can one expect to have any valid measurement during heavy loads?

What tools can I use to get a more realistic view of CPU usage?
MikeBravo

---

### Post by cubeist on 2008-05-03
I can confirm that my amd system does this also.  However, I found a simple fix.  Change the update interval in preferences to 10 seconds and the cpu load from system monitor drops right off.  Something related to "pinging" the cpu load every second causes it to spike.

---

