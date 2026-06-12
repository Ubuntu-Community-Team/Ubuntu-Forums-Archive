---
title: "Freezing from what?"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by ibrahim.safwat on 2008-05-19
I am an absolute beginner at linux, I'm like all of you guys out there just sick of windows and all the microsoft products. I asked around and heard that ubuntu 8.04 is an excellent OS. So I downloaded it and installed it on my laptop acer aspire 5520G, but now the laptop lags during the most random of times. It freezes when I'm using the battery or AC, it freezes when I'm surfing using firefox or downloading stuff with transmission. At first the wireless was not working, so I found a guide on ubuntuforums.org that explained to me how to install it. I asked a friend of mine why he thinks my laptop freezes up like this, he said that it might be the ndiswrapper. But I was wandering maybe it's just a bug in 8.04, if I downloaded an earlier version like 7.10 would that problem go away? Or what is it that you think I should do?

---

### Post by HotShotDJ on 2008-05-19
> **ibrahim.safwat said:**
> So I downloaded it and installed it on my laptop acer aspire 5520G, but now the laptop lags during the most random of times.Please verify... I believe that model uses an NVidia video card of some sort.  If this is the case, have you set up the drivers (System --> Administration --> Hardware Drivers)?

---

### Post by ibrahim.safwat on 2008-05-19
well that's true it does use NVIDIA. I opened the hardware drivers it had 3 things.
1- atheros hardware access layer (HAL)
2-NVDIA accelerated graphics driver (latest cards)
3-support for Atheros 802.11 wireless LAN cards.
They are all enabled and the status of 1 and 3 are not in use, while the second is in use. What should I do?

---

### Post by HotShotDJ on 2008-05-19
> **ibrahim.safwat said:**
> They are all enabled and the status of 1 and 3 are not in use, while the second is in use. What should I do?Hmmmmmmmm.  While I suspect the video card, I'm not 100% sure, and I have very little experience with NVidia cards.  Why don't you go ahead and post the specs for you laptop (CPU, RAM, Video Card (full model)) and then lets sit tight and see if somebody with more experience with NVidia cards can come in and offer assistance.

---

### Post by ibrahim.safwat on 2008-05-19
-It's an AMD Athlon 64 x2 Dual Core Processor 1.8GHz, 2 x 256 KB L2 cache
-NVIDIA GeForce 8400M G TurboCache
-2GB DDR2

Any help would be highly appreciated! Thanks

---

### Post by Tatty on 2008-05-19
My instinct is to suspect that its the nvidia / powernowd freezing bug.  Try disabling powernowd for a bit and see if the freezes stop

```
sudo /etc/init.d/powernowd stop
```

Add the cpu frequency monitor to your panel too.  Make sure that it is always 100% scaled up to be sure that powernowd is off.


If it is this bug then unfortunately there is no fix currntly, as it seems likely to be in the nvidia proprietry drivers, which are closed source and so relient on nvidia maintaining them.

The only workaround is to disable powernowd.  Trying to get the right balance between scaling and preventing freezes is something ive spent months trying to perfect, im getting closer though. lol.

---

### Post by ibrahim.safwat on 2008-05-19
well I did it. But could you please explain what is it that I must make sure is "100% scaled up" I have the system monitor added to the panel and open infront of me right now.

---

### Post by Tatty on 2008-05-19
its not the system monitor, its the cpu freqency scaler.  :)  basically it tells you what speed your process is currently working at.

Powernowd is responsible for scaling down your cpu when its not needed to save on power and cut heat.  But unfortunately it conflicts somehow with the nvidia proprietry driver and sometimes when it scales up it locks the whole system.  Its a real problem.

---

### Post by ibrahim.safwat on 2008-05-19
ok I did that. It's at 100%. So as long as powernowd is off it will remain at 100% right?

Doesn't turning off the powernowd affect the laptop? Or is it just a way to save battery or electricity?

---

### Post by Tatty on 2008-05-19
yes basically it just saves battery power and helps it keep cooler.  Preferably you want it on, but if it keeps locking up the machine then obviously you cant.

As i say, im still experimenting with this myself, trying various methods of trying to control cpu scaling a bit better but i havent found anything better than just disabling it yet.

note: when you reboot powernowd will come back on so you will need to disable it again.  If it turns out that it is powernowd causing the lockups then you can just uninstall it via synaptic.

---

### Post by ibrahim.safwat on 2008-05-20
thanks man! Till now it has not locked up. I would appreciate it very much if, when you do find another way than just disabling powernowd, that you let me know.

Thanks again.

---

### Post by ibrahim.safwat on 2008-05-20
it worked well for a while but now it started to lock up again!! if i download an older version of ubuntu, will that work? I really need to find a way to solve this problem because all my studies are on my laptop so it's practicaly my life!! Please help!

---

### Post by nick_h on 2008-05-20
Try disabling Visual Effects, it sometimes causes random freezes.

---

### Post by ibrahim.safwat on 2008-05-20
I did that but still it freezes. But I wanted to know if installing an older version of ubuntu will solve this problem?

---

### Post by tqprvn on 2008-05-22
at a guess, no, going back to 7.10 wont help.  I just started a similar thread and have similar issues with Acer notebooks on 7.10.

Watching with interest now....

---

### Post by tqprvn on 2008-06-04
Just curious about something...would this be a Ubuntu vs Nvidia issue or a Linux vs Nvidia issue?

If it is a Ubuntu powernowd issue, would switching to, say, Mepis (which loses Gnome, but has reputedly great hardware/driver support) solve the issue?

One of our machines in here much worse than the others....

---

