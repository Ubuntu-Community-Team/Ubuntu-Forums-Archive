---
title: "linux -rt? Should I?"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by |{urse on 2008-05-28
Just wondering if anyone could enlighten me as to whether i should bother going with one of those fancy low latency kernels? So far I've heard they rock and I've also heard that overall performance degrades too. I recently installed quake wars enemy territory, VERY VERY SWEET GAME! But performance could be a bit smoother. I've tweaked all the settings to hell and back and found a nice balance. SO I'm reading the install guide (waaay after i've already installed lol) And it's telling me I should probably roll my own low latency kernel, which is all well and good but wont that adversely affect my overall system performance when I'm running several apps at a time? I google "low latency gutsy" sans quotes and i see that the lowlatency kernel was actually available from the repos "sweet!" i said (sans quotes) And then saw it had been obsoleted by linux-rt which is also in the repos. So 

1. Is this a good idea for an asus sk8n w/ an athlon fx 52 and an ati x1650 512 with 1gb of low latency corsair a raid 0 and gutsy?

2. What are the differences between the low latency kernel and linux-rt (im supposing that means real-time (I'll believe that when i see it lol))

---

### Post by sdennie on 2008-05-29
Looking at the config for the Gutsy -rt kernel, it looks like it's compiled with the -rt patches (It has CONFIG_PREEMPT_RT set) and set to a 1000Hz timer so, you shouldn't need to compile your own.  There is no real harm in trying it out:

```

sudo apt-get install linux-image-rt linux-headers-rt

```

Then reboot and select the -rt kernel.

---

### Post by |{urse on 2008-05-29
Well.. I installed the real time kernel, I suppose im going to need a diff gfx drver for it? Compiz gives me white screen of doom but e17 runs like it's on steroids. Glx is a no go. I'm gonna stick with the default kernel.

---

### Post by sdennie on 2008-05-29
You may need a manually install the graphics driver for the -rt kernel.  If you can't find the -rt kernel modules (restricted modules?) for it in synaptic, it should be pretty straightforward to install them using envy.  I don't think that's in the Gutsy repos but you can grab it here: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html).  Of course, this may cause problems if you switch back to the -generic kernel and you'd probably have to use envy again for the generic kernel.

---

### Post by bornagainpenguin on 2008-05-29
> **|{urse said:**
> Well.. I installed the real time kernel, I suppose im going to need a diff gfx drver for it? Compiz gives me white screen of doom but e17 runs like it's on steroids. Glx is a no go. I'm gonna stick with the default kernel.

I'm using -rt on my laptop and was using it on my desktop (currently without a desktop due to non-related monitor issues) on my laptop, which uses the default open source drivers there were no issues in the switch.  On my desktop I completely lost the sky when it came time to load the gfx drivers.  When I booted back in with the default kernel everything was fine.  I discovered that for some strange reason selecting the -rt kernel (and I thought all the recommended add ons for it) **doesn't** automatically add the restricted modules for the -rt series like you'd think.

If you've still got the -rt kernel installed, it'd be worth checking synaptic and seeing if the -rt restricted modules are installed also.  That fixed my problems with my nVidia card and I was really enjoying the speed and smoothness until my monitor went out.... (again monitor issues not related) so you should really give it another chance!

--bornagainpenguin

---

### Post by |{urse on 2008-05-29
Sounds good ^^ I'm at work so I'll def try that at home tonight.

---

### Post by das letzte einhorn on 2008-05-29
I installed the RT kernel by Ubuntu Studio; First ubuntu, then I installed Studio through the terminal. Works wonders for me, for sound, video, etc. I do have the choice between -RT and generic version 17 kernels when I boot, do you have that option as well?If you do, you might want to test them and see which one works best for you.

---

### Post by |{urse on 2008-05-30
to person with germanish name, lol. Yes I have both options in my grub.conf. thanks for your reply. To everyone else above I couldn't get it working with the new ati catalyst (x1650) and -rt but i'll keep an ear out on this thread. I'd use the fglrx in the repos but it wreaks havoc on my system. Mesa direct rendering won't go away etc.

---

