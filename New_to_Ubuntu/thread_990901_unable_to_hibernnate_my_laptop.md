---
title: "unable to hibernnate my laptop"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by shreyanshjain8 on 2008-11-23
hi friends...

i m using ubuntu 8.04...

and i had seen that i am unable to hibernate my laptop... 
whenever i press that hibernate button ... some message comes like this

"cannot find swap on device"

and some more error message comes along with it ...
and the main screen again shows me the log on screen...
and it ask me for my password again..

plzz help me out....

i need hibernation...
and i have to face many problem as i can't hibernate my laptop....

---

### Post by -Zeus- on 2008-11-23
did you make a swapfile when you installed ubuntu?

please post the results of the command ```
free
```

---

### Post by shreyanshjain8 on 2008-11-23
no.. i think i didn't made any swap partition....


can u plzz help me out...

now what to do.... :-(

---

### Post by shreyanshjain8 on 2008-11-23
this is the outcome .....    that do not show any swap partition....

:-(   :-( 




             total       used       free     shared    buffers     cached
Mem:       3106372     708340    2398032          0      25308     327696
-/+ buffers/cache:     355336    2751036
Swap:            0          0          0

---

### Post by -Zeus- on 2008-11-23
try this link: [https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?](https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?).  It needs to be at least as big as your physical RAM, 3GB in this case.

---

### Post by shreyanshjain8 on 2008-11-23
okk after following all the instructions given in the link which u gave in the above post,,,

i hav created a swap file 

and now i can suspend my system but...

suddenly hibernation button has disappeared from the logout MENU....

i can see 

suspend 
shutdown
switchuser
lock screen
restart


but there is no hibernation button....
:-(

---

### Post by shreyanshjain8 on 2008-11-23
i need a help friends ...

please techies and gr88 computer users .. help me out with your super knowledge...


thanks

---

### Post by shreyanshjain8 on 2008-11-23
any help ....?????

---

### Post by Paqman on 2008-11-23
> **shreyanshjain8 said:**
> okk after following all the instructions given in the link which u gave in the above post,,,

i hav created a swap file 

and now i can suspend my system but...

suddenly hibernation button has disappeared from the logout MENU....


How big did you make the swap partition? How big is your RAM?

---

### Post by shreyanshjain8 on 2008-11-23
it is 3 GB ram...
 and i made a swap file of 512 mb

i know the rule is     
n < swap partition< 2*n  
(n= RAM of the system)

but on my friends systems it work on lesser swap space also..
so i also made it only 512 MB

but i don think that due to it the hibernation button directly disappeared from the logout menu..

---

### Post by Paqman on 2008-11-23
> **shreyanshjain8 said:**
> it is 3 GB ram...
 and i made a swap file of 512 mb


That's why. Swap needs to equal RAM for hibernation.

During hibernation, the whole contents of the RAM memory is copied into the Swap partition and stored. When coming out of hibernation the system reloads it's memory from the swap. That's how you can completely power off during hibernation, but still keep the state the machine was in.

---

### Post by shtripok on 2008-12-27
I have 8.10 and asus eeepc 901. 1 GB ram, 2GB swap partition.
No hibernate buttons nowhere. All linux partitions runs on SD card in internal card reader.

How can I enable hibernation?

---

