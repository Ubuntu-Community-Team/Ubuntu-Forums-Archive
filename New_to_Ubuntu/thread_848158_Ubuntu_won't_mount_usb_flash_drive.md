---
title: "Ubuntu won't mount usb flash drive"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by Jackfrost123 on 2008-07-03
On my laptop computer (although it mounts the same usb flash drive on my desktop computer booted with the live cd). It outputs: "cannot mount volume" "invalid mount option when attempting to mount the volume". Is there a way around this you guys?

---

### Post by copperco2 on 2008-07-03
the problem usually is because, was faced by me too, of faulty dismounting at an earlier time.
if you have a dual boot then try using it on xp (if that is what you have) then un install it properly. then try mounting it on ubuntu.

If it does not work then there is an option to force mount too.. but i dont have tech expertise to.. let me check this out.

---

### Post by Jackfrost123 on 2008-07-03
hey copper, thanks a lot buddy, I have dual boot and it works on xp but I am not sure I understand what you are saying about removing it properly from xp, I dont think that bears any influence on linux.

---

### Post by copperco2 on 2008-07-03
[http://ubuntuforums.org/showthread.php?t=842993&highlight=mount+usb+drive](http://ubuntuforums.org/showthread.php?t=842993&highlight=mount+usb+drive)

check the above thread. it works just like that.

to dismount, windows allows you to just take it out of the usb plug. but in linux that is not the right way.
either right click on the drive icon and dismount it (in xp). if it shows the message' its okay to take the dongle out' then take it out and when you want to use it in ubuntu..then it wont have any problems.

try it once and let me know.

---

### Post by Jackfrost123 on 2008-07-03
hey coper, will do so, in the next couple of hours, many thanks bro!

---

### Post by Jackfrost123 on 2008-07-04
FAILURE.

Tried but failed with the win xp trick. Read extensively the linked thread to no avail.

HEEELLPPP!

---

### Post by silkstone on 2008-07-04
You could try this, assuming that the drive is recognised in XP and you can transfer whatever is on it in XP.

1. Insert the drive into your XP machine and copy everything on it to a temporary folder.

2. Reformat the drive as FAT32 in XP.

3. For good measure, give it a new volume label.

4. Copy everything back onto it.

5. Try it again in your Ubuntu machine.

EDIT/ Before doing any of that, do other external drives mount OK? Is it just this USB stick that's a problem?

---

### Post by Jackfrost123 on 2008-07-04
Good question the last one. Ok, bro, other media load ok, another 1 gb usb flash I tried, so that means I better try what you said with xp, reformating and all. Or btw, why don't I reformat it in ubuntu, isn't that possible?

---

### Post by Jackfrost123 on 2008-07-04
Hey SOME success, i reformated in ubuntu ( i d already copied the content via xp) and it said it couldn't mount, again. Mounted it through partition editor and it worked.

///EDIT

THANKS SILKSTONE, GOOD TURNAROUND.

---

### Post by silkstone on 2008-07-04
Cheers - glad you're having some luck! :)

---

### Post by Jackfrost123 on 2008-07-04
Hey, like I said, many thanks. Btw, I read yorkshire in your location, I am coming to study in University of Leeds, how abou that?

---

### Post by silkstone on 2008-07-04
Leeds is about 20 miles from where I live - plenty going on there - hope you enjoy it and good luck! :)

---

### Post by Jackfrost123 on 2008-07-04
Thanks. D'you live in Bradford?

---

### Post by silkstone on 2008-07-05
West of Barnsley - Silkstone Common - hence the forum name!

---

