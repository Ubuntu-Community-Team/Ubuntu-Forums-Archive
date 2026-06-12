---
title: "sudo shutdown -h now doesn't work"
date: 2008-09-11
forum: New to Ubuntu
---

### Post by CryptiniteDemon on 2008-09-11
I try this command and ubuntu turns off, but leaves my hardware on still.

sudo shutdown -r now works fine however for restarts.

Any ideas?

---

### Post by handydan918 on 2008-09-11
> **CryptiniteDemon said:**
> I try this command and ubuntu turns off, but leaves my hardware on still.

sudo shutdown -r now works fine however for restarts.

Any ideas?


What is your hardware?

---

### Post by Locutus_of_Borg on 2008-09-11
thats what the command is supposed to do

if you want to power off your machine as well, insert a -P in there

---

### Post by ad_267 on 2008-09-11
Try using "sudo shutdown -P"

For a full list of options enter "man shutdown"

---

### Post by anders_c_ on 2008-09-11
-h                          halt or power off after shutdown
  -H                          halt after shutdown (implies -h)
  -P                          power off after shutdown (implies -h)

-P and -h is supposed to do the same thing so it should work...

---

### Post by Locutus_of_Borg on 2008-09-11
i dont know, but -h never turned off the power for me

i just use 'telinit 0' as it is a shorter command and encompasses halting and powering off in one

---

### Post by Tatty on 2008-09-11
As mentioned before, you need to specify -P to make it power off the hardware.

There is an easier method of doing this:

```
sudo halt
```

which basically just executes shutdown -h -P for you.

---

### Post by Iowan on 2008-09-11
> **Tatty said:**
> 
```
sudo halt
```
 Being intrinsically lazy, that's my favorite way to shutdown.

---

### Post by xebian on 2008-09-11
I simply pull the plug.  It's immediate, no if's or but's, or 'are you sure..' stuff.

---

### Post by Iowan on 2008-09-11
> **xebian said:**
> I simply pull the plug.  It's immediate, no if's or but's, or 'are you sure..' stuff.My flight instructor described a "good landing" as any you can walk away from - a GREAT landing is one in which the airplane can be used afterwards. That would certainly be a "good" way to power down...

---

### Post by Ntweat on 2008-09-11
m with u... i leave my comp on... if anytime the light goes thats the only time my comp goes down

---

