---
title: "cannot mount psp since i changed mount point"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by antisocialist on 2008-04-27
it was mounting as '2.0GB storage device' and since i have a couple things like that i decided i would change them so i dont get confused, so i right clicked the icon on my desktop and click preferences and then under one of the tabs and changed the mount point to /media/sony PSP and now whenever i mount a psp it gives me an error 'mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /)'
and i cannot mount my psp. how can i fix this because i cant right click the icon for preferences on my desktop anymore >< and cant think of what cmd to use for this

---

### Post by janmartin on 2008-04-27
Hi,

I can think of a few things to try:

1) Check the media directory if there is a "sony PSP" folder. If not, create it. You can mount only to existing folders.
Then try to mount. Restart Ubuntu, try again.

2) However if there already is a "sony PSP" folder in media, delete it. Try to change the mount point again. Just to be sure, avoid "space" in the mount points name. E.g. use sony_PSP instead.

3) If nothing worked, post your /etc/fstab file which might have useful info to help you.

Let us know what worked.

Good Luck!

---

### Post by antisocialist on 2008-04-27
i got it mounting at /media/sony_PSP but i dont have perm to rw it. need a uuid for it

---

### Post by dhaj1964 on 2008-04-30
hi...i have the same problem with my psp not mounting ....yes...did the same too of changing mount point....i hope too that this problem can be solve too...coz my video converter can't detect my psp and so is ubuntu 8.04 hardy.

---

### Post by antisocialist on 2008-04-30
> **dhaj1964 said:**
> hi...i have the same problem with my psp not mounting ....yes...did the same too of changing mount point....i hope too that this problem can be solve too...coz my video converter can't detect my psp and so is ubuntu 8.04 hardy.

i can help you if you want, right now my only problem is my card reader, not rigt this instant i gtg to school in a min but when im back ill help

---

### Post by antisocialist on 2008-04-30
ok first you need to find out its location
with it disconnected type
```
ls /dev/sd
``` and then hit the tab button

plug in your psp with it in usb mode, wait 10 seconds, then do the same thing again
copy+paste the results of both to me

---

### Post by mosibfu on 2008-11-04
ok first off.. the error came because there was a space in the folder name.. since fstab and most of linux commands use space as a seperator, you get a conflict (check out /etc/fstab and then u know why its confused with the space)

how to get read+write on it??```

sudo chmod 777 /media/sony_PSP

```
  read write execute for all..


to find out wich device is your psp easily ill have to quote antisocialist

antisocialist  	
Re: cannot mount psp since i changed mount point
ok first you need to find out its location
with it disconnected type

```

ls /dev/sd

```
and then hit the tab button

plug in your psp with it in usb mode, wait 10 seconds, then do the same thing again

THE NEW SD IS THE PSP!!! no copy pasting needed.. (so the sd thats NOT on the first list but IS on the 2nd list will be your psp)

this basically goes for all supported external drives/cardreaders/mobile phones

well i just hope that covers it all, ty antisocialist for that nice way to find the new device.. never thought of that, beats looking up and down for sd´s.. :guitar:

---

