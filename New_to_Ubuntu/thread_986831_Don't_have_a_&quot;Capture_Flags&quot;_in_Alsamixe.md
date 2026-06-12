---
title: "Don't have a &quot;Capture Flags&quot; in Alsamixer - why?"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by kgolyaev on 2008-11-18
There is a topic in which I discuss a similar question, but I hope creating a new one will attract some extra attention.

I have a problem with my microphone. It's on a Toshiba Satellite laptop, model U405D-S2848. My sound card (as given by lspci command) is: 00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA).

I just installed the latest version of alsa drivers, utils and lib. The sound works quite fine, but I cannot get anything recorded, so I believe the problem is with the microphone.

After reading various sources, it looks like I have to launch alsamixer, go to the "Capture" tab, and use spacebar to toggle the "capture" flags on. Well, I don't have any signs of such flags, and hitting spacebar any (odd) number of times does not seem to help. (I attach a screenshot of my alsamixer capture tab.)

Have anyone seen anything like this?

---

### Post by fooman on 2008-11-19
install the gnome-alsamixer from synaptic,  or in a terminal, run:

```
sudo apt-get install gnome-alsamixer
```

---

### Post by kgolyaev on 2008-11-19
I have it installed. I don't think I am able to find these capture flags there either. Maybe I am doing something wrong?

---

### Post by kansasnoob on 2008-11-19
I've found gnome-alsamixer to be much superior!

It's in the repos:

```
sudo apt-get install gnome-alsamixer
```

Oops, Fooman beat me!

---

### Post by kgolyaev on 2008-11-20
To kansasnoob and fooman:

I do have gnome-alsamixer installed. My question initially was not about the program per se but rather about the fact I cannot find the needed switch in it.

Here is my screenshot for gnome-alsamixer. I can't help noticing there are no Capture flags (or similar buttons) there as well. Maybe you guys know what is wrong with it - I know there is a mic on my laptop, it just does not work!

Thanks!

---

### Post by fooman on 2008-11-20
in the toolbar, click edit > sound card properties

there should be more options in there to choose from. just put a check next to any that you want to show in the mixer.

---

