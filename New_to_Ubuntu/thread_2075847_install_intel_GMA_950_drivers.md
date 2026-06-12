---
title: "install intel GMA 950 drivers?"
date: 2012-10-24
forum: New to Ubuntu
---

### Post by kidd4200 on 2012-10-24
im using backtrack r3 10.04 LTS (lucid), ubuntu basically.

anywho, its dual boot. i fire up windows and my external moniter works fine under 1600x1200. on backtrack, it only works under 1024x768. there IS an option under display settings to enable the higher resolution, but after logging out and in again, im still at 1024x768 - whats up with that?

is there a way to force the external to be under 1600x1200? OR do i have to install an updated, open source driver?
i found a website that hosts intel open source drivers, from the intel website. the issue is im not sure if i want to mess around with my kernel, which is 3.2.6
besides that, their are multiple downloads availible - the "kernel" file, 2d file, 3d file, and mesa (i beleive thats the 3d version).

soooooo, how do i get my friggin external to be 1600x1200?
thanks!! whoop whoop!

---

### Post by snowpine on 2012-10-24
Welcome to the forums!

Ubuntu installs Intel video drivers by default. There is no extra step necessary on your part to get them.

You can get support for Backtrack here: [www.backtrack-linux.org/forums/forum.php](www.backtrack-linux.org/forums/forum.php)

As you point out, there is a Display Settings option that allows you to set your resolution.

---

### Post by kidd4200 on 2012-10-24
well yes, but as i said, display settings only reverts back to 1024x768 on my monitor which should be 1600x1200.
not sure why?

---

### Post by snowpine on 2012-10-24
I think BackTrack is designed to be used as a "Live" environment for security/penetration testing, and therefore it does not save settings from session to session like Ubuntu does. But I don't know that for a fact; you can confirm it by visiting their site at the link above. Ubuntu certainly has the capability to remember screen resolution (once it is installed to hard drive, not as live CD/USB).

---

### Post by kidd4200 on 2012-10-24
well i have BT installed on the system, its not live. but i do have the capability of running it as a live version, and saving settings via a usb device.
but thats getting off track.

my BT does save settings, for sure. my xorg.conf virtual display IS setup correctly (though both displays arent listed, doubt that matters).
the virtual resolution is saved as 2624x1200 which, is 1024 (main monitor) plus 1600. and obviously, 1200 becuase thats the height of my larger monitor, which is right of, the main monitor.

is it possible i can just edit xorg.conf do setup both displays manually?
ive seen the tutorial on wiki-ubuntu, but i feel hesitant to start popping in code which might jank up my X displays. obviously i could save a backup and restore it if X didnt work on a reboot\log off.
anybody wanna help me with editing xorg? that would be great!

PS - im also gonna post this on BT forum also

---

### Post by snowpine on 2012-10-24
Ubuntu doesn't use xorg.conf any more, it is auto-configured on the fly.
Since I don't know much about BackTrack I'm afraid I'm out of suggestions, sorry. :(

---

### Post by kidd4200 on 2012-10-24
rough biz yo

maybe somebody else can be of assistance?

im having trouble finding the "new thread" button on BT forum. and YES i registered, and im logged in. im not that much of a dippy.

but yeah, help!

OH also, the main reason im using BT is because windows SUCKS. only reason i use wincrap is bc of itunes. naturally apple dont want ubuntu to use itunes. although, i do use yoolo or something, to edit crap on my older ipod (the proggy dont work for iphones, unfortunately - yet)

and, my pc is a asus eee pc, 1005HAB. its a little dated, but it runs BT GREAT. windows, runs like garbage (whats new there?)

---

### Post by snowpine on 2012-10-24
Honestly your negativity about Windows makes me less inclined to help you, you might want to consider how you present yourself in the future as a member of this community.

My Asus EEE has identical graphics chip to yours, and I've never had any problem with external displays detecting the correct resolution on the various Linux distros I've installed on it. But again, I've never used BackTrack--that would be a question for their forum I think. :)

---

