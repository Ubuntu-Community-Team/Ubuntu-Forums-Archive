---
title: "[SOLVED] wont boot after power went out"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-07-03
So i just installed hardy 64 bit on my sisters computer the other day.
I had just finished setup and customization and was about to give it back to her when..

well first i should say that the computer was off at the time so i dont know if losing power is really the problem or what (and it was on a surge protector)

but anyway we lost power (it flickered on and off a few times)

now i cant boot, i can get as far as the ubuntu loading screen and the bar goes about 1/16th of the way and stops and just does nothing 
no errors or anything
(the light on my box that indicates if the harddisc is reading also stops)

i also tried booting recovery mode but that also freezes and does nothing

i even tried booting the old kernal and that wouldnt work

i can acess my filesystem with the live cd and all appears normal


what can i do, aside from a full reinstall? (it took me too long to set everything up, and i really dont want to do it all over)

---

### Post by defrex on 2008-07-03
If I were you I'd boot the cd, make a tarball of /home, reinstall, and restore /home. It's annoying, but if it's a newly set up system it shouldn't be to bad.

If it's still no good I'd say you got a serious hard drive issue. Then it's probably time for [Spinrite]("http://www.grc.com/sr/spinrite.htm"). It's not free or open source, unfortunately, but it sure does work. Does anyone know of a free alternative?

---

### Post by chrisccoulson on 2008-07-03
When you boot in recovery mode, what messages are display before it freezes? It might be useful for you to photograph your screen and post it here.

I would also try running a check of your discs (fsck) from the live CD. If you want help doing that, then please ask.

Thanks

---

### Post by tjwoosta on 2008-07-03
> When you boot in recovery mode, what messages are display before it freezes? It might be useful for you to photograph your screen and post it here.

I would also try running a check of your discs (fsck) from the live CD. If you want help doing that, then please ask.

Thanks 


id love to be able to take picture but i dont have a camera on hand

(i will reboot now and write it down by hand the last few things it says)


i tired fsck from the live cd but i dont know if i did it right cuz it only took about a half a second and it said clean

this is what i did after reading the man 

sudo fsck /dev/sda1

is that right?


> If I were you I'd boot the cd, make a tarball of /home, reinstall, and restore /home. It's annoying, but if it's a newly set up system it shouldn't be to bad.


i suppose i could do this but is there anyway i can unmount my dvd burner when the live cd is running?  (maybey run ubuntu from ram?)
so i can burn the tarball

it says its not mounted in the first place but i know it must be because i cant open the disc drie

---

### Post by logos34 on 2008-07-03
> **tjwoosta said:**
> i suppose i could do this but is there anyway i can unmount my dvd burner when the live cd is running?  (maybey run ubuntu from ram?)
so i can burn the tarball

it says its not mounted in the first place but i know it must be because i cant open the disc drie

I use Parted Magic rescue cd...runs from the ram...but it only has a CD burner app, no dvd (although if you gzip the tarball it might fit on a cd...then again nothing against using more that one cd)

---

### Post by tjwoosta on 2008-07-03
ok this is everything displayed on the screen when it freezes

```

0x30
[  57.147482]  [<ffffffff80466fe9>] mutex_lock+0x9/0x20
[  57.147640]  [<ffffffff8823b448>] :ndiswrapper:kdpc_worker+0xa8/0x140
[  57.147697]  [<ffffffff8823b3a0>] :ndiswrapper:kdpc_worker+0x0/0x140
[  57.147738]  [<ffffffff8024f2bc>] run_workqueue+0xcc/0x170
[  57.147778]  [<ffffffff8024fe40>] worker_thread+0x0/0x11
[  57.147818]  [<ffffffff8024fe40>] worker_thread+0x0/0x110
[  57.147858]  [<ffffffff80253a00>] worker_thread+0xa3/0x110
[  57.147899]  [<ffffffff80253a00>] autoremove_wake_function+0x0/0x30
[  57.147940]  [<ffffffff8024fe40>] worker_thread+0x0/0x110
[  57.147980]  [<ffffffff8025363b>] worker_thread+0x0/0x110
[  57.148019]  [<ffffffff8020d198>] kthread+0x4b/0x80
[  57.148060]  [<ffffffff8020d198>] child_rip+0xa/0x12
[  57.148103]  [<ffffffff802535f0>] kthread+0x0/0x80
[  57.148142]  [<ffffffff8020d18e>] child_rip+0x0/0x12
[  57.148181]
[  57.148215]
[  57.148216] Code: 66 0f 7f b4 24 a0 01 00 00 0f 84 5d 04 00 00 66 66 90 66 66

[  57.148871] RIP  [<ffffc200005bbb8a>]
[  57.148936]  RSP <ffff81003da39be8>
[  57.148982] ---[ end trace 005baac14fdb6f5b ]---
                                                               [fail]
*Setting the system clock
*Loading Kernal modules...
*Loading manual drivers...


```

after seening this is reminds me of a couple things that i did the last time i was logged on, that may be related
1. i compiled ndiswrapper, but failed to get the driver loaded correctly
2. i set the system clock to auto sync with the new york server

---

### Post by tjwoosta on 2008-07-03
> I use Parted Magic rescue cd...runs from the ram...but it only has a CD burner app, no dvd (although if you gzip the tarball it might fit on a cd...then again nothing against using more that one cd)

awesome thanks, 
but first off does anybody have any ideas about my last post?

---

### Post by annda on 2008-07-03
in case it is a problem with ndiswrapper drivers, please try hitting CTRL-c as soon as you see "Loading manual drivers" to stop the loading process.

if you can boot after that, go back a few steps and get rid of the offending driver.

---

### Post by annda on 2008-07-03
double post, deleted

---

### Post by dodle on 2008-07-03
If you have to do a complete reinstall:  When you get to the partition editor choose to configure manually.  Mount your main partition to "/" without formatting.  At about step 5 or 6 (can't remember which) it should ask you if you want to import users.  Select the users you want to keep; this should save all your settings.  You may have to reinstall a few of your applications though.

---

### Post by chrisccoulson on 2008-07-03
tjwoosta - what you've posted looks like part of the dump from a kernel panic, related to ndiswrapper. You need to disable / fix / uninstall ndiswrapper to rectify it. I've got to call it a night now, but I'll try and help you out tomorrow if you haven't got it sorted.

---

### Post by tjwoosta on 2008-07-03
> tjwoosta - what you've posted looks like part of the dump from a kernel panic, related to ndiswrapper. You need to disable / fix / uninstall ndiswrapper to rectify it. I've got to call it a night now, but I'll try and help you out tomorrow if you haven't got it sorted.
ok, awesome, im getting somewhere

so what can i do to remove ndiswrapper?

can i just delete the bin files using the livecd, or will that probably be bad?

---

### Post by annda on 2008-07-03
> so what can i do to remove ndiswrapper?

can i just delete the bin files using the livecd, or will that probably be bad?

it won't hurt because those are only install files, but i'm afraid it won't help much either, since the kernel module is placed/installed elsewhere. look for it in /lib/modules/**your_kernel_version**

you can blacklist the module until you have figured everything out. using the livecd mount the ubuntu partition and once you are there:

```
sudo gedit **path_to_ubuntu_partition**/etc/modprobe.d/blacklist
```

and add this line:
```
blacklist ndiswrapper
```

save and reboot to your installation. i hope it will work.

BTW: be careful about the 32bit/64bit compatibility issues. unless you actually compile stuff on your own, i believe it is safest to install from official repositories, not third-party binaries.

---

### Post by tjwoosta on 2008-07-04
> BTW: be careful about the 32bit/64bit compatibility issues. unless you actually compile stuff on your own, i believe it is safest to install from official repositories, not third-party binaries.

yea i actuall compiled from source because it was a newer version than is available in the repository
(was going on advice from another thread)

i guess there are no bin files i just assumed there were (i dont actually know how that stuff works)

Edit:
anyway thank you everyone i used the blacklist ndiswrapper and it worked great

it booted right up, then i just ran make uninstall to remove ndiswrapper, then i undid the blacklist ndiswrapper and rebooted

all is great now

---

### Post by chrisccoulson on 2008-07-04
I'm glad you've got it sorted:)

---

