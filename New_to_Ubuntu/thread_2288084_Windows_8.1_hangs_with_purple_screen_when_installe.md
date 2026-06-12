---
title: "Windows 8.1 hangs with purple screen when installed with ubuntu 15.04"
date: 2015-07-24
forum: New to Ubuntu
---

### Post by sreeyeshns on 2015-07-24
I recently assembled a Desktop PC with intel i3 4th generation processor and intel MH87 motherboard.

I installed windows 8.1 first and it worked fine without any problems. The problems started when I installed ubuntu 15.04 along with the existing windows 8.1(dual boot).

After this, when I select windows from the grub menu a blank purple screen appears and stay for a few seconds. Then the screen goes full black for 2 seconds and again becomes purple as before and then stay as it is for ever. My ubuntu installation if working without any problem.

I tried too many things to solve this. One solution gave me a partial solution.

I just renamed '/etc/grub.d/30_os-prober' to '/etc/grub.d/06_os-prober' and run 'update-grub' command so that Windows becomes the first entry in the grub menu. This solution is partial because sometimes the windows login works fine but sometimes the purple screen problem come up as before.

Can someone tell me a permanent solution?

---

### Post by oldfred on 2015-07-24
Not really an Ubuntu or grub issue.
If you have fast startup on, then grub is not able to correctly boot Windows. It does some different in its reboot. Grub is set up to boot Windows in normal fashion from UEFI with a chain load.

       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

