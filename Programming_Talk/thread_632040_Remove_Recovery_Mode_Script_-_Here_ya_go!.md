---
title: "Remove Recovery Mode Script - Here ya go!"
date: 2007-12-05
forum: Programming Talk
---

### Post by thenetduck on 2007-12-05
Hi 

I noticed that there was a need for a script to remove recovery mode on a machine (some people don't like the idea of having root access via recovery mode and for schools etc.) So I hacked up this script. Please be away it's one of my first scripts besides hello world so check the source before running to make sure it's not something you think is going to break your system. I tested it on my computer Gusty Gibbon 7.10 and so far things work just fine. It should get past kernel updates but we shall see. 

P.S. I didn't put the GNU PL on it but I intend to. If someone wants to cp on there or something, I have no idea which one I should put on there. Also, make sure to run this command to make it work. Thanks!

```

sudo sh RemoveRecovery.sh

```
The Net Duck

=======================
Update Posted new and imporved program. 

Use RecoveryAndPass.py because it puts a password on your menu.lst and removes recovery mode. 

to run....

```

sudo python RecoveryAndPass.py

```

======================================
UPDATE : DEC 8 2007
Ok I created a lunchpad.net page .[https://blueprints.launchpad.net/ege](https://blueprints.launchpad.net/ege)

I will start off making this in python and OOP based so it should get pretty fun! If anyone wants to get involved, I hope to get the base system done this week and maybe the menu, unless someone else wants to do it. I actually amd finding this project really fun. 

The Net Duck

---

### Post by geirha on 2007-12-05
This script will only remove the grub menu options for the recovery mode. Anyone with a little knowledge of grub will easily be able to boot into a root shell without them.

---

### Post by ZipoTe on 2007-12-05
A good idea would be setting a grub password so the boot loader. Combine that with removing the recovery entry from the menu :)

---

### Post by thenetduck on 2007-12-05
Thanks that is great feedback. I think I will start work on a grub script that creates the password... question.. could I just set grub bootime = 0? or can you still get into grub this way?  Also if I set a pass for grub they have to put that pass in to edit grub right? not use it every time it boots up?

The Net Duck

---

### Post by psusi on 2007-12-05
Just set a password on the root account and they will have to enter it if they choose the recovery option.  Also you will need to disable the ability to edit the grub menu interactively or they can just pass the right parameters and get a root shell anyhow.

---

### Post by thenetduck on 2007-12-05
> **psusi said:**
> Just set a password on the root account and they will have to enter it if they choose the recovery option.  Also you will need to disable the ability to edit the grub menu interactively or they can just pass the right parameters and get a root shell anyhow.

So I changed my GRUB to have a password (just to test things out) and once grub has a password, you need to enter the password before you can press 'e' to edit grub. ... Sorry if I didn't understand but what did you mean about the setting the password on the root account? Do you mean if i set a password, I don't have to worry about removing recovery mode? It it smart enough to realize that if you are using recovery mode you need a pass? 

Thanks

The Net Duck

---

### Post by psusi on 2007-12-05
Yes, normally recovery mode prompts you for the root password to login,  but by default, there isn't one.

---

### Post by thenetduck on 2007-12-06
Ok I added new new created Python script that does it all in one. Should I remove the old script?

P.S. I know if I used shell instead of Python I could have done it in 5 lines but I don't really know how to work with variables with shell. 

The Net Duck

---

### Post by ZipoTe on 2007-12-07
I know this is a little offtopic but, if you are interested in, you can have a look at this: [Securing Debian Manual]("http://www.debian.org/doc/manuals/securing-debian-howto/index.en.html") It teaches you how to portect your PC (including GRUB protection, wich is what you are doing :))

**EDIT**

There is also a pdf so you can print it as i have done ;)

---

### Post by SeanHodges on 2007-12-07
Good idea this. 

I don't think it needs to be a complete script for securing Grub against attacks (although you could make it do this if you want). It could simply be a script for easily setting options such as the recovery automagic options.

If someone is securing their computer they should read up on it (such as the Securing Debian Manual), but this script could assist them in getting the modifications in place without editing menu.lst directly.

Anyway, good job.

---

### Post by thenetduck on 2007-12-08
The current python script will look for key words that automagic set's up and change them to what it needs to be. This might not work if you have all ready edited your grub. 

I am going to update this script however. I have an idea how I can make it work even if you have edited your grub but starting with a fresh grub, snagging your boot menu locations (or whatever they are called that direct to the right spot on your boot) and making a new grub. Humm.....I hope that makes sense. 

Is there a place I can get a fresh automagic GRUB menu.lst? I mean one that would be a freshly created one without modifications? If anyone has that can they please post. I have messed my menu.lst formating up (I play) so want to have a clean version. 

The Net Duck

---

### Post by linuxsux on 2008-02-12
i accidentally disabled recovery mode a different way and i don't know how to get it back. Can someone help me get it back? Is there a way i can get it back by using a boot cd and how?

---

### Post by geirha on 2008-02-13
> **linuxsux said:**
> i accidentally disabled recovery mode a different way and i don't know how to get it back. Can someone help me get it back? Is there a way i can get it back by using a boot cd and how?

Yes, post the content of /boot/grub/menu.lst here. (put it inside [code]-tags please)

Are you able to boot regularly?

---

