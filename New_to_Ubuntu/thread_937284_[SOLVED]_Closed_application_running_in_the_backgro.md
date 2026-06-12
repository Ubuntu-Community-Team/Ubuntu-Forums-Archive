---
title: "[SOLVED] Closed application running in the background and overloading CPU"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by lovinglinux on 2008-10-03
This is weird for me and I don't know if I'm doing something wrong.

Sometimes when I run applications in the terminal, like ipstate or iptraf for example, and I close the terminal window after a while, the application stays running in the background and overload the CPU like 99%. I don't know if this is "normal" and I can't close the application unless I reboot.

---

### Post by mikewhatever on 2008-10-03
It's probably not normal, but you can at least use <killall process-name>.

---

### Post by lovinglinux on 2008-10-03
> **mikewhatever said:**
> It's probably not normal, but you can at least use <killall process-name>.

Already tried that, but it doesn't work. What if I use the application PID? I'm trying to reproduce the issue to test this.

---

### Post by nowshining on 2008-10-03
> **lovinglinux said:**
> This is weird for me and I don't know if I'm doing something wrong.

Sometimes when I run applications in the terminal, like ipstate or iptraf for example, and I close the terminal window after a while, the application stays running in the background and overload the CPU like 99%. I don't know if this is "normal" and I can't close the application unless I reboot.

i've had the same problem with a few programs esp. sometimes top/htop run as sudo and sysv-rc-conf :/ - just kill the programs thru the terminal/tty, etc.. and all should be fine.. - to avoid these cpu overloads make sure u exit the program gracefully and the right way, example using Q to quit, etc.. instead of ctrl+c and just shutting down the terminal if can...

---

### Post by lovinglinux on 2008-10-03
> **nowshining said:**
> i've had the same problem with a few programs esp. sometimes top/htop run as sudo and sysv-rc-conf :/ - just kill the programs thru the terminal/tty, etc.. and all should be fine.. - to avoid these cpu overloads make sure u exit the program gracefully and the right way, example using Q to quit, etc.. instead of ctrl+c and just shutting down the terminal if can...

I guess using Q to quiet will solve this issue. I was just closing the terminal, so I guess this was the culprit. Thanks.

---

