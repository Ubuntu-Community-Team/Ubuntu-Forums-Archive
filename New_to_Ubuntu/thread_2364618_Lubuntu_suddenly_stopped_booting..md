---
title: "Lubuntu suddenly stopped booting."
date: 2017-06-25
forum: New to Ubuntu
---

### Post by francisco.marin on 2017-06-25
Hi everyone. A couple of months ago I decided to try a Linux OS with an old computer. Since the computer is around ten years old, I tried only lightweight distributions. The first I tried was xubuntu, but I got a lot of trouble with the wi-fi connection, I had to verify the password every five minutes or so, and after that sometimes the OS did not boot properly. Because of that, I uninstalled it. 

My second attempt on a linux lightweight distribution was lubuntu. It was exactly what I needed: a fast and easy to use distribution to surf the web, the possibility to install an office suite, and little more. I can say that this distribution ran perfectly for nearly a month, but overnight my computer started to have troubles to boot the OS. At first, I just had to reboot a couple of times the computer and everything worked fine. But now it is really an ordeal to get lubuntu running, it gets stuck after the grub (for I have windows xp installed in another partition of the HDD, and with windows xp I have absolutely no booting problems). 

Sometimes appears a message that reads "/dev/sda5: recovering journal" and then the usual partition and blocks information "/dev/sda5: clean xxx/xxx, xxxx/xxx blocks". After that, the screen goes black, the computer starts loading and nothing else happens. 

I have also seen this message: 
[drm:drm_atomic_helper_commit_cleanup_done [drm_kms_helper]] **ERROR** [*CRTC*:*26*:*pipe A] flip_done timed out*. Then, again the information about the partition and blocks, and again the black screen and the computer gets stuck. 

Sometimes, if I let the computer to keep loading for a while after the scenario of my first example, I got the information of the picture. 
[CENTER]                         [ATTACH=CONFIG]275773[/ATTACH] 
[/CENTER]


I have looked a lot for a solution to this issue, but I have only come across vague answers, and a lot of "this could help"; I have tried a lot of things as well (for example updating the grub, fsck related stuff, editing commands) without any success. 

I hope some one can help me because I really do not want to reinstall lubuntu because of this. Especially since something similar happened when I tried xubuntu (that makes me think that it is something specific that I have to adjust). 

Thanks in advance. 

Computer specs: 

Acer Aspire ICL50
Ram: 1GB
CPU: Intel Celeron CPU 560 @ 2.128GHz 
GPU: Mesa DRI Intel(R) 965GM x86/MMX/SSE2

---

### Post by eluandar on 2017-08-15
Install Rescatux on a thumb drive and boot from it. Choose the Boot Fix Option (GRUB). Reboot after that.

---

