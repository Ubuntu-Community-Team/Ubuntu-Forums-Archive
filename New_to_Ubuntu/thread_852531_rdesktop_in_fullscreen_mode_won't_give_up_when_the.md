---
title: "rdesktop in fullscreen mode won't give up when the connection goes bad"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by ionFreeman on 2008-07-07
So, the wireless signal at work has been wonky today. And rdesktop freezes up whenever I lose my wireless signal; it won't respond to ctrl+alt+enter. The mouse will move around the screen, but of course the windows won't respond, as I'm disconnected. It does not fix itself when the wireless signal is restored. I don't think. I can't actually tell if the wireless signal is restored, as I'm in fullscreen mode with a remote Windows virtual machine, but I imagine it is.

I can't get out of it. I can't get to my other workspace. I've been killing X with ctrl+alt+backspace, which is the only thing that seems to work.

Is there a way to get rdesktop to give up without launching a remote shell into my desktop from another machine? I like having alt+tab and whatnot work inside of Windows -- I'm just wondering if I can use -f and make it killable when it freezes, or, even better, to get it to die instead of freezing.

I'm running rdesktop with these flags:

rdesktop -f -z -C -N -B -u <user> <machine>

---

### Post by toupeiro on 2008-07-10
> **ionFreeman said:**
> So, the wireless signal at work has been wonky today. And rdesktop freezes up whenever I lose my wireless signal; it won't respond to ctrl+alt+enter. The mouse will move around the screen, but of course the windows won't respond, as I'm disconnected. It does not fix itself when the wireless signal is restored. I don't think. I can't actually tell if the wireless signal is restored, as I'm in fullscreen mode with a remote Windows virtual machine, but I imagine it is.

I can't get out of it. I can't get to my other workspace. I've been killing X with ctrl+alt+backspace, which is the only thing that seems to work.

Is there a way to get rdesktop to give up without launching a remote shell into my desktop from another machine? I like having alt+tab and whatnot work inside of Windows -- I'm just wondering if I can use -f and make it killable when it freezes, or, even better, to get it to die instead of freezing.

I'm running rdesktop with these flags:

rdesktop -f -z -C -N -B -u <user> <machine>


I don't know of a said "flag" that will make it time out, but you should be able to jump down to CLI (ctrl-alt-F1) and do a 
> ps -ef | grep -i rdesktop ; then >  kill -TERM <PIDNumber> where the PIDNumber is the number of your rdesktop process, or issue a > pkill -9 rdesktop if you only have one session running, or don't care about killing all open ones.  to get back to your GUI, press ctrl-alt-F7 (sometimes its F6 or F8 for some reason, but traditionally its F7)

---

### Post by ionFreeman on 2008-07-11
Thanks! I'll report back as to whether this works.

---

### Post by bhaverkamp on 2011-07-14
I just had this happen as well. I was unable to get a alternate console via Ctrl-Alt-F1. I forgot about Ctrl-Alt-backspace. I will try that next time. I ended up doing a hard reboot. Nasty! One thing I have started doing on desktops is to never run full screen and just run in a window. On a notebook that is problematic due to limited screen real estate.

---

