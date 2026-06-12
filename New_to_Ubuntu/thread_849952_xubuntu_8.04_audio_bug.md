---
title: "xubuntu 8.04 audio bug"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by pcrussell50 on 2008-07-05
hi, i run xubuntu for my mother on her older desktop, p4, 1gb ram, 7.10.  it's great, just what she needs. so a few days ago, i'm over for a visit, and i install 8.04 for her. it's a beautiful visual upgrade...but...no sound.  also, the only screen resolution is 800x600 and she has a 19" monitor that easily runs 1024x768...in 7.10, anyway.  i was short on time, and did a little searching, and it appears there's a bug folks are talking about in 8.04, but i didn't have time to try the "workarounds" to get sound back for her, so i just formatted and reinstalled 7.10.

any insights into this from anyone?  also, if it is a bug, it's obviously a big one.  as such, i am relatively new enough to ubuntu/xubuntu to ask, "do the developers usually fix bugs?"  and do they fix it within the same version, or will we have to wait until 8.10?

regards,
peter

---

### Post by Bodsda on 2008-07-05
This is a workaround for sound, it is by no means a decent fix, but it usually clears up sound problems

first try

```
killall pulseaudio
```
then open/close-reopen a media player and try playing something, if you get sound the workaround is

```
sudo apt-get remove pulseaudio
```

The problem (according to the pulseaudio devs) is that Ubuntu doesnt configure PA properly so it doesnt work out of the box for all applications, you can reconfigure it but its much easier to revert to the default alsa.

For the resolution, make sure, if you have a graphics card that the restricted drivers are installed, and maybe try rebooting, at grub select 'recovery mode' then choose the 'fix x' option.

Hope this helps ;~)

Bodsda.

---

