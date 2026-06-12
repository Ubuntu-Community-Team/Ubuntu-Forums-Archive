---
title: "What is the best kernel for me?"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by amit.la on 2008-11-01
Hey all.

I've recently upgraded to Ubuntu 8.10, and noticed that my CPU usage is pretty high on simple tasks (playing music and video, showing web pages that have flash, and so on)

I've did some digging, and found out that I'm using the 386 generic kernel. Being new to Ubuntu, I'm asking your help with choosing the right kernel for my configuration:

- Ubuntu 8.10
- AMD Athlon64 3000+
- ATI Radeon 9800 pro
- 1 GB of RAM


Thanks in advance,
Amit

---

### Post by Tom--d on 2008-11-01
Flash is CPU intensive. Always is, even in Windows.

You have an 64bit processor. Try the 64bit verison of Ubuntu.

---

### Post by amit.la on 2008-11-01
Ok, Can i upgrade from my existing installation, Or must I reinstall?

---

### Post by Tom--d on 2008-11-01
You must reinstall because 32bit (which is i386, i686) is different from 64bit. But you can run 32bit software in a 64bit installation but not 32bit running 64bit.

---

### Post by Tom--d on 2008-11-01
Please read this: [http://ubuntuforums.org/forumdisplay.php?f=343](http://ubuntuforums.org/forumdisplay.php?f=343)

Its all about 64bit. There are advantages and disavantages.

---

### Post by ethoxyethaan on 2008-11-01
a 64 bit version will not help for flash, since this way you will have to emulate a 32 bit environment for flash to run in (remember there is no 64 bit version of flash yet). it will take up allot more cpu to run flash.

---

### Post by amit.la on 2008-11-01
OK, Tom, Thanks for that. Lets say I want to stick with the 32bit version, isn't there a better kernel for my than the generic 386?

---

### Post by Tom--d on 2008-11-01
> **amit.la said:**
> OK, Tom, Thanks for that. Lets say I want to stick with the 32bit version, isn't there a better kernel for my than the generic 386?

You say you have high CPU load with Flash and music playing? Could not be a kernel problem. Are you getting freezings?

Also. Use Htop to check your CPU load. The system Monitor can be read false readings due to its self is using the CPU as well.

Htop is a terminal, and VERY light system monitor.
```
sudo apt-get install htop
```
Its in Add/Remove as well.

then in terminal, htop.

Then find out what is using CPU.

---

### Post by amit.la on 2008-11-02
Hey Tom.

First, Thanks for your time. I've done as you adviced, and installed htop. The results are not much different from the results i got when i monitored the CPU usage with system-monitor. I'm begining to think that it might be a problem with the flash plugin for firefox. Are there alternatives for the default plugin?

---

### Post by amit.la on 2008-11-02
Hey Tom.

First, Thanks for your time. I've done as you adviced, and installed htop. The results are not much different from the results i got when i monitored the CPU usage with system-monitor. I'm begining to think that it might be a problem with the flash plugin for firefox. Are there alternatives for the default plugin?

---

### Post by amit.la on 2008-11-02
Hey Tom.

First, Thanks for your time. I've done as you advised, and installed htop. The results are not much different from the results i got when i monitored the CPU usage with system-monitor. I'm beginning to think that it might be a problem with the flash plug-in for Firefox. Are there alternatives for the default plug-in?

---

### Post by bep on 2008-11-02
If you updated to 8.10, check what kernel you are using.

I did that too, was running the 386-kernel and the upgrade manager did not find a newer one so stayed with the old one. Unstable and slow system.

Installed the latest generic kernel, everything ok.

See [http://ubuntuforums.org/showthread.php?t=966999](http://ubuntuforums.org/showthread.php?t=966999)

---

