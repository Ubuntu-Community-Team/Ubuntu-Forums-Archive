---
title: "Grub gray screen"
date: 2015-04-11
forum: New to Ubuntu
---

### Post by static7 on 2015-04-11
I recently installed Ubuntu Gnome and all is well except for grub displaying a gray screen instead of the usual boot options. I want to dual boot with Windows but without seeing the boot options there's no way to know what I'm booting into. I have looked at etc/default/grub and changed "quiet splash" to "nomodeset" but it did not solve the problem. This has solved graphical issues for me in the past. From what I've read this is a problem with nvidia cards but so far I haven't found a post with this exact problem. Currently using GTX580 with proprietary driver 331.113 installed. 

Thoughts?

---

### Post by tjiagoM on 2015-04-12
I don't know if I quite understood your problem. But basically you want your dual boot screen and you don't have it? (just go directly to ubuntu?)

Have you tried this? [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by UltimateCat on 2015-04-13
If your not seeing your Windows os in your Grub Menu all you need to do is run a few simple commands.

```
sudo os-prober
sudo update-grub

```

When you reboot you should have the choice of using your arrow keys and choose which os you want.

That should fix the issue your having unless your also having a graphic's issue.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by dino99 on 2015-04-13
purge your actual nvidia installation:  sudo apt-get purge nvidia* 
  (from the recovery mode, you should get it, even blindly, if you select the 2nd line: hit 'arrow down' one time, then hit 'enter'). 
Then open the terminal to be able to purge it.
This will activate 'nouveau' as the graphic driver. When done, reboot, this should solve that grey issue.
Your card support newer nvidia driver than that oldish 331, use the 349 one (xorg-edgers ppa if you are not using 'vivid')

---

### Post by static7 on 2015-04-16
Thanks for the replies.

9d9:
I have tried blindly booting to recovery by pressing down and enter but the system will boot up into ubuntu.
Thanks for noticing my nvidia drivers were out of date. I did not realize there is a more up to date repository. Updated to 349 but the issue persists.

tjiagoM:
Good to know about Boot-Repair. I'll give it a try next (waiting on it to download...) Even if it doesn't help now it will be useful in the future.

To clarify, I do not have windows installed right now. Just Ubuntu Gnome.

This is what I'm seeing

[[IMG]http://i.imgur.com/npiHBnSl.jpg[/IMG]]("http://imgur.com/npiHBnS")

---

### Post by Krillo on 2015-04-16
I'm having a similar issue on Ubuntu Mate. :-/

---

### Post by phidia on 2015-06-03
Using Ubuntu Mate 15.04 I have the same symptom-grey grub screen as seen in this thread. Still searching for a solution.

---

