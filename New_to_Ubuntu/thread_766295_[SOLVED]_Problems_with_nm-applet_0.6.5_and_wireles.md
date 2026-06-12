---
title: "[SOLVED] Problems with nm-applet 0.6.5 and wireless"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by NeuB27 on 2008-04-25
First thank you to everyone who helped me earlier in installing my wireless drivers and ndiswrapper over [Here]("http://ubuntuforums.org/showthread.php?t=764638"). 
I am now having trouble with my wireless card in other ways. It is recognized by the system (Gutsy 7.10 amd64) and under the network manager I have a wireless option... However, I cannot connect to my router, and after an attempt or two the system has problems, namely that the nm-applet which is in the upper right hand corner disappears, or stops responding correctly. It will have no options, for wired or wireless, only manual and a grayed out (no network devices have been found) option. But I can still find the wireless/wired/dialup options in the network settings window (System > administrator > network) but opening that window takes a very long time now, several minutes of frozen opening time (and I am sure it is not hardware related from slow machine). 
I am at a total loss as to what I should do. Do I need to completely reinstall 7.10 and just try it all over again? Does anyone know of a really good idiots guide to ubuntu/linux that might help in that case?

---

### Post by twright on 2008-04-25
could you type sudo ndiswrapper -l into terminal and post the output

---

### Post by NeuB27 on 2008-04-27
Ok, so it broke the OS, whatever this problem was. I shut the comp off after my first post, and when I turned it back on today, it would not start correctly( ubuntu ) so I went through the grub loader and tried the recovery option and it stopped progressing after stalling on the network settings section. So I'm just going to reinstall and try to move the computer and use the wired connection. Hopefully it will work, and then after I update some, I'll try to get the wireless working again.

---

