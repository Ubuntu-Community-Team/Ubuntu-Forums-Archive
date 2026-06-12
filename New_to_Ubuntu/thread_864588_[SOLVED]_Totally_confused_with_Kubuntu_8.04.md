---
title: "[SOLVED] Totally confused with Kubuntu 8.04"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by pablo27 on 2008-07-19
I have spent the last two weeks trying to get up and running but I am becoming so frustrated I am about to switch distros!! I am not totally new to Ubuntu I have an earlier version on my laptop and love it.  However Nothing in 8.04 seems to work or be easy. I really need some help please. I have a Celeron 2.66Gz processor with a hda-intel on board sound chip.  I have followed all the threads I have found to get my sound working ----no sound---- I've configured the alsamixer, added snd-hda-intel to my module file, REinstall the whole distro 7 times and nada.  Also when using k3b I cannot write to DVD-rw I just keep getting errors.  Did I hit my head or what?  Where do I start?  Thanks in advance for any and all help.

---

### Post by nothingspecial on 2008-07-19
The only advice I can give you is to do what I did. Go back to Gutsy. I just want my stuff to work.

---

### Post by petersk on 2008-07-19
I'm glad I'm not the only one to have my sound card not working.  I tried to modprobe snd-intel8x0 for my SiS onboard AC'97 and various other things.  
  Weird thing it that sound worked when I first installed Hardy from CD, but after one of the updates it stopped working.

I found this wiki, which I'm going to try out.
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)
Kurt

---

### Post by Sealbhach on 2008-07-19
This is good for troubleshooting sound problems:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

I found I had to add a line to /etc/modprobe.d/alsa-base

See the section: **Configuring default soundcards / stopping multiple soundcards from switching**

Hope it helps.

Just go through it step-by-step and it should solve the problems or at least show up what is wrong.



.

---

### Post by pablo27 on 2008-07-24
Well here I am about 30 hrs later. No sound, have downloaded latest alsa-libs,drivers,util and compiled and installed, driver name is in modprobe.d/alsa-base,
and all I have to show for it is----nada. ANYone have any more suggestions??  My card works just fine in XP and I get system beeps in Kubuntu but no sounds in Amarok.  Has anyone really solved this problem effectively? The last time I RE-installed Kubuntu 8.04 x64 and went through the whole process again and nothing.

---

### Post by hyper_ch on 2008-07-24
well, if hardy gives you such a headache I also recommend reverting back to gutsy or check out another distro. If you're brave you could see how it goes with Ibex, maybe you have more luck there.

I just think if you spend so much time and can't get it to run you might be better off to avoid this release and use something else and then maybe check back later...

It's not really technical help but you getting frustrated about Ubuntu Hardy doesn't help you much either.

---

### Post by pablo27 on 2008-09-28
After trying what seemed like hundreds of suggestions to no avail, I found that moving the speaker output plug to a different output jack solved the problem.  If you have more than output jack you might give this a try.  Thanks for all you efforts

---

