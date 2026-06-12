---
title: "[SOLVED] A Different Question re Dual Booting"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by john wagner on 2008-07-20
Hey all!  I got a different question about dual booting for ya...  I am running Dapper (LOVE it) on a 160 gig HD laptop.  I recently installed Feisty (to play with it etc...), and my question is thus...
When I fire it all up initially, I get a screen asking what to boot up.  Several versions of Dapper or Feisty.  The default is Feisty and I got 7 seconds to decide.  I would like to make the default Dapper and give me more time.  If I happen to blink, or zone a little, I end up in Feisty.  My usual system is Dapper, I likes it the most!
If I install other OS of linux, will I have to do this all over again?

Thanks, in advance!
john

---

### Post by schauerlich on 2008-07-20
Open up your grub settings:
```

gksudo gedit /boot/grub/menu.list

```
Then find a section that looks like this:
```

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        7

```

Then change that 7 to whatever you want.

---

### Post by cdtech on 2008-07-20
You can also set the default OS by changing:
# default 0 (which is the first OS in the list
to # default "whatever list number" (1 being the second in the list).

**P.S.**
If you change anything that starts with a "#" sign you have to do the "sudo update-grub" thing. If you change any line that has no "#" sign you don't need to update-grub.

---

### Post by munkyeetr on 2008-07-20
The changes you want to make are in /boot/grub/menu.lst

```

gksudo gedit /boot/grub/menu.lst

```

edit the **timeout** option to alter how many seconds you have to decide which OS to boot
```

timeout <seconds>

```

edit the **default** option to alter which OS boot if you let the timer run out. **NOTE: the number you use here corresponds to the list of boot choices at the end of this file. So scroll down and look, you will see a list in the same order as you see when you are booting. The default value starts at 0, so if you want to boot the first OS in the list, set default to 0, if you want to boot the second in the list, set it to 1, etc...
```

default <os selection>

```

Hope this makes sense to you.

---

### Post by john wagner on 2008-07-22
Tried em all, none did the trick.  I log into the terminal, give myself admin rights, call up the .lst and make the changes recomended.  Save it, reboot and nada.  Same time and same default.  Doing something wrong I guess, just don't know what. Thanks for all the input tho.

john

---

### Post by munkyeetr on 2008-07-23
> **john wagner said:**
> Tried em all, none did the trick.  I log into the terminal, give myself admin rights, call up the .lst and make the changes recomended.  Save it, reboot and nada.  Same time and same default.  Doing something wrong I guess, just don't know what. Thanks for all the input tho.

john

EDIT: Now I'm second guessing this, but what the hell, I'll leave it in...

I just thought of what it may be:

Make sure you make the changes to the proper grub installation. You are running both Dapper and Feisty, Feisty being the newest installation would have taken over the grub instance. Make sure you are booted into Feisty when you change the timeout and boot default.

I could be wrong, but thought I'd throw that out there.

---

### Post by kansasnoob on 2008-07-23
I don't know if it's available in Feisty or not but go to synaptic and look for > startupmanager then if it's in the repos you'll see something like this in System > Administration > Startup-Manager:

[ATTACH]78645[/ATTACH]

[ATTACH]78646[/ATTACH]

Choose your default boot from the list.

---

### Post by kansasnoob on 2008-07-23
> **munkyeetr said:**
> EDIT: Now I'm second guessing this, but what the hell, I'll leave it in...

I just thought of what it may be:

Make sure you make the changes to the proper grub installation. You are running both Dapper and Feisty, Feisty being the newest installation would have taken over the grub instance. Make sure you are booted into Feisty when you change the timeout and boot default.

I could be wrong, but thought I'd throw that out there.

Totally correct-a-mundo! I recently installed Linux Mint Elyssa as a third OS with Hardy and Win XP. Mint has control now as far as GRUB, although the stage 1, 1.5, 2, etc. all have me a bit boggled.

I did once follow Herman's guide to create a separate GRUB partition and it worked, but I don't really understand the ins and outs yet.

[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_)

---

### Post by john wagner on 2008-07-23
A-ha!!!!  I be off to try that now!  Will fill you in after I do it.  Thanks all!

john

---

### Post by john wagner on 2008-07-23
> **munkyeetr said:**
> EDIT: Now I'm second guessing this, but what the hell, I'll leave it in...

I just thought of what it may be:

Make sure you make the changes to the proper grub installation. You are running both Dapper and Feisty, Feisty being the newest installation would have taken over the grub instance. Make sure you are booted into Feisty when you change the timeout and boot default.

I could be wrong, but thought I'd throw that out there.



That was the problem!  I kept making the changes to grub for Dapper!  Once I booted into feisty and did the changes to .lst.....  a quick reboot into dapper and voila!  Perfect!  Thanks a bunch guys, I really love this forum!

john

---

