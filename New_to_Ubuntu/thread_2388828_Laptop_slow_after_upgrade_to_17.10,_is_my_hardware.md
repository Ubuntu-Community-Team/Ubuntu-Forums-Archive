---
title: "Laptop slow after upgrade to 17.10, is my hardware too old?"
date: 2018-04-07
forum: New to Ubuntu
---

### Post by jml3473 on 2018-04-07
Hi! I've upgraded to 17.10 yesterday because I feared I'd eventually run into security problems. My laptop is now much slower however.

Main use is Firefox, pokemon game ptcgo over wine, and gvim. Game to firefox now needs at least 10s instead of a few seconds. Swap used to be 300–600 Mo or at most 1 Go with 17.04, it's now 1.6 Go (says system monitor), so I suspect this may be the problem.

Memory 3.7 GiB DDR3, Intel Core i3-3130M CPU@2.60GHz x 4, Graphics Intel Ivybridge Mobile, Gnome 3.26.2 64-bit
L3 3 MiB, L2 512 KiB, L1 128 KiB
ATA Disk Western Digital WDC WD5000BPKX-7 7200 RPM

Should I go for a lighter version of ubuntu? :confused:

---

### Post by iscollin on 2018-04-07
maybe get an SSD they can help with slow application launches depending on your setup if you can afford a larger SSD it depends on your preference I'm ordering a crucial BX300 128gb which is reliable and fast it's 49.99 on Amazon it could make bootups and application launches *much* faster that's what I recommend anyway maybe upgrade ram to 4-8 gigabytes.

---

### Post by QIII on 2018-04-07
That does not offer a clue or solution to a slower experience after the update.  Please do not suggest that the OP spend money on hardware when there is likely a software issue here.

---

### Post by gordintoronto on 2018-04-07
+1. The i3 is plenty fast enough to run current applications well. You should run top or htop to figure out what is consuming so much memory.

---

### Post by monkeybrain20122 on 2018-04-08
Are you on wayland or xorg, is that a clean install or an "upgrade"?

---

### Post by dave1956 on 2018-04-08
I have to confirm that my computer also is running slower than it did when I had ver12 of Ubuntu on it... I am going to do a clean install of ver 18LTS in May

Dave

---

### Post by jml3473 on 2018-04-08
Thanks a lot for your help everybody! So my hardware should be enough, great news!

Firefox  may be the culprit. Yesterday it crashed hard (it would crash again on  restart, problem solved after a reboot). Now I have fewer opened tabs  and speed was okay when switching from the game, swap was lower too.
Perhaps my choices are 1. don't leave 1&#8211;2 youtube vids on pause in their tab 2. do a fresh install.

I guess I'm on wayland since I have Xwayland and gdm-wayland-session processes :p
I've never done a fresh install, I've just been upgrading from the factory install 4 years ago.

I noted down the System Monitor values while playing: Mem 3.1 GiB / 3.7GiB Swap 1.2 GiB
Sorting the processes by memory usage (in System Monitor):
gnome-shell 1.0GiB
Pokémon [...].exe (the game) 586 MiB
firefox 359MiB
Web Content, 4 times: 142 / 130 / 123 / 41 MiB
The next processes go down in size very quickly so I don't understand how this could add up to 3.1 GiB, much less 3.1 + 1.2 GiB.
I  thought maybe only the user processes are shown, so I "sudo apt install  htop" (which mostly froze everything for 20&#8211;30s). Sorting by memory  shows many duplicates in htop, I didn't spot anything new, I'll try  harder if necessary.
Wow, the game is closed as I'm writing this and  gnome-shell went up to 1.4 GiB! I guess when gnome-shell and the game  and firefox all go up a few hundred MiB the RAM limit is hit and things  go very slow.

---

### Post by &amp;wP*!) on 2018-04-08
[LIST=1]
[*] Try to install much lighter Ubuntu distros: Xubuntu or Lubuntu. At Lubuntu Desktop Environment is much lighter. Lighter distro will consume less RAM, reduce probability to use the swap. Swap activity will reduce life time of your SSD.
[*] For SSD, use noatime option in /etc/fstab to increase life time of your memory, because at each IO access (read/write) timestamp of the files will be updated. This causes lots of IO activity. A very nice page about this is [here]("https://sites.google.com/site/easylinuxtipsproject/ssd").
[*] Uninstall unnecessary programs, which run in the background. Example: postfix (local email service). For more information, see [here]("https://ubuntuforums.org/showthread.php?t=2388708").
[*] Your memory is limited so probably no chance to get rid of swap. I have 8 GB RAM machine, where firefox etc take about 2.4 GB (Lubuntu).
[/LIST]

---

### Post by monkeybrain20122 on 2018-04-08
> **jml3473 said:**
> I guess I'm on wayland since I have Xwayland and gdm-wayland-session processes :p
I've never done a fresh install, I've just been upgrading from the factory install 4 years ago.
.

So logout, in the login screen press the Ubuntu button and choose xorg session and see if it improves.

Also, there are many changes from 4 years ago, upgrade has probably broken something or some leftover configurations might interfere with the new os. It is a lot cleaner, safer, a much much faster to a clean install, if switching to xorg doesn't fix it a clean install should be next.

---

### Post by monkeybrain20122 on 2018-04-08
> **pencuse said:**
> 
[LIST=1]
[*] Try to install much lighter Ubuntu distros: Xubuntu or Lubuntu. At Lubuntu Desktop Environment is much lighter. Lighter distro will consume less RAM, reduce probability to use the swap. Swap activity will reduce life time of your SSD. 
[*] For SSD, use noatime option in /etc/fstab to increase life time of your memory, because at each IO access (read/write) timestamp of the files will be updated. This causes lots of IO activity. A very nice page about this is [here]("https://sites.google.com/site/easylinuxtipsproject/ssd"). 
[*] Uninstall unnecessary programs, which run in the background. Example: postfix (local email service). For more information, see [here]("https://ubuntuforums.org/showthread.php?t=2388708"). 
[*] Your memory is limited so probably no chance to get rid of swap. I have 8 GB RAM machine, where firefox etc take about 2.4 GB (Lubuntu). 
[/LIST]


His specs are pretty adequate to run FF and doesn't need a "light desktop" unless it is his aesthetic preferences.Clearly something else is amiss.

---

### Post by &amp;wP*!) on 2018-04-08
> **monkeybrain20122 said:**
> His specs are pretty adequate to run FF and doesn't need a "light desktop" unless it is his aesthetic preferences.Clearly something else is amiss.

His RAM is 3 GB, and swap usage is continuously and it is ~ 1 GB (that's what he says above). With Lubuntu I can see it eats ~2,5GB RAM and no swap is used at all (even though my computer is much better than his, I have 8 GB RAM and 8 GB swap). With continuously swapping in/out, the product life of his SSD will be much shorter. This is my argument why he needs a lightweight distro.

---

### Post by monkeybrain20122 on 2018-04-08
> **pencuse said:**
> His RAM is 3 GB, and swap usage is continuously and it is ~ 1 GB (that's what he says above). With Lubuntu I can see it eats ~2,5GB RAM and no swap is used at all (even though my computer is much better than his, I have 8 GB RAM and 8 GB swap). With continuously swapping in/out, the product life of his SSD will be much shorter. This is my argument why he needs a lightweight distro.

I don't know what is eating up his ram but I doubt that it is the DE alone if everything else is running properly.It is conceivable that gnome-shell may have a memory leak but that would be a bug rather than because it is not "light".

 He has almost 4Gs of Ram and pretty powerful cpu, it can run any **properly supported and configured **Linux DE with no problem on resources. Any modern Linux DE is much lighter than Win8 or 10 that the machine comes with. I think this idea of magically fixing problem with a "light DE" came from a time when  <= 2G of ram was normal and members of the Geek community who take great pride in running antique hardware, with reasonably modern hardware (say in the last 6-7 years) "light DE" is more of a preference than a necessity IMO.


**EDITED**: He can reduce swapping by setting vm.swappiness, the default 60 maybe a bit conservative, but my hunch is that high memory consumption is just a symptom, something is messed up with his configuration somewhere due to "upgrade", or it is Wayland, or both.

---

### Post by sp40140 on 2018-04-08
There is a known issue with 17.10 Gnome version of memory leak.

Try to install xfce (or any other DM) and see if you experience any changes in performance.


Edit: link to the memory leak article. 
[https://www.omgubuntu.co.uk/2018/03/gnome-shell-memory-leak-is-being-fixed](https://www.omgubuntu.co.uk/2018/03/gnome-shell-memory-leak-is-being-fixed)

---

### Post by jml3473 on 2018-04-09
I'm really thankful for the help you guys gave me.

After more monitoring it's clear the problem stems from a full memory. The system monitor's values are htop's RES minus SHR, which is why values didn't add up to the total memory usage (all shared memory was missing&#8212;er, not that I really understand what I'm talking about).
Gnome shell is a good suspect. Indeed it seems it's growing in size over time, on average. sp14140's linked article implies normal size should be ~250M, not 1+G.

I tried monkeybrain20122's advice to try ubuntu on Xorg. It seems to work! gnome-shell's size is under 500M after I watched some youtube and played pokémon and stuff. It's smaller and/or grows more slowly. No slowdown at all. I don't know what Wayland and Gnome do to each other, I guess it could be that whatever makes gnome-shell big hasn't triggered yet.

If I must log out daily to bring gnome-shell down until the leak is patched, that's no big deal. Or I have a range of alternatives in this thread. Thanks again.

I don't have an SSD, but I just "sudo sysctl -w vm.swappiness=30" for fun :)

---

### Post by monkeybrain20122 on 2018-04-09
> **jml3473 said:**
> I'm really thankful for the help you guys gave me.


If I must log out daily to bring gnome-shell down until the leak is patched, that's no big deal. Or I have a range of alternatives in this thread. Thanks again.


No need, it remembers your last login, so if it is xorg it will be xorg in the future, unless you choose wayland again.

---

