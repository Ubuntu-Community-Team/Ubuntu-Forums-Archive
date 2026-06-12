---
title: "Terminal window blank, then &quot;Argument list too long&quot; then crashes"
date: 2012-03-16
forum: New to Ubuntu
---

### Post by ryang55 on 2012-03-16
Ubuntu 11.04

When I open a terminal window I get blank space.  I can type in it but  nothing happens.  After a few minutes it gives me an _"bash: /usr/bin/dirname:  Argument list too  long"_ message which it repeats a million times (continuously for a  couple of minutes) before crashing.The header of the terminal window says "/bin/bash"

I had just installed the ROS (Robot Operating System) software and the terminal was working fine then.
I'm new to linux and command line so any help would be greatly appreciated.

Update:  just checked my "bin" folder.  It has 1,880 items.  Is there a work around besides removing the items?

---

### Post by alquery on 2012-03-16
What happens when you open the application 'xterm?' It might start up correctly. If it doesn't, what happens if you press Ctrl+Alt+F1 and log in?

---

### Post by chipbuster on 2012-03-17
Your issue is definitely not in /usr/bin. Those files are the programs you use, don't get rid of them unless you particularly enjoy reinstalling your system from scratch. My /usr/bin has over 2700 and bash is working fine.

Try alquery's fix first. If that doesn't work, it's time to do some digging.

---

