---
title: "Update manager lost packages?"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by chimera007 on 2008-11-19
Hello, and thank you for reading my thread. 

I have run into an inconvenience lately while upgrading some packages. I had selected all new updates to be applied and clicked on the update button, the started downloading. Electricity went out and ups would keep the pc on for long, so I decided to cancel the downloading of the updates. While rushing around, I accidentally clicked on a button that now I don't remember exactly the string it had but was more or less "Don't inform me about these updates again."

When I turned on the pc again, and tried to update, didn't find them. In those new updates, the new kernel was included, this was 3 days ago for today (19/11/09). 

Is there a way to re-enable the upgrading of those packages? I tried completely removing update-manager-core and similar files and installing it again, but it didn't help.

IMO, that option shouldn't be there ^^

---

### Post by jenkinbr on 2008-11-19
Try removing update-manager-core with the purge option.
```
sudo apt-get purge update-manager-core
``` and then reinstall update-manager-core. (If apt-get spits out a huge list of packages to remove, cancel the operation and remove it using synaptic.)

Alternatively, as a temporary workaround, use ```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by snova on 2008-11-19
Reinstallation rarely helps anything on Ubuntu, no matter what it is (although purging configuration files might).

For now, run this in the terminal:

```
sudo apt-get update
sudo apt-get upgrade
```

This will update everything the manual way (I happen to prefer this method).

In theory, this will solve your problem permanently, or at least until you use that button again. But I don't use it, so I don't know for sure...

---

### Post by wolfen69 on 2008-11-19
> **snova said:**
> Reinstallation rarely helps anything on Ubuntu, no matter what it is (although purging configuration files might).



not true. the reason it does not work alot of times is because people do not clear their cache and wind up reinstalling the same package.

sudo apt-get clean

sudo apt-get autoremove

takes care of this. i have fixed many problems by reinstalling.

---

### Post by chimera007 on 2008-11-19
None of the methods posted previously work. Argg, maybe reinstalling the whole system works? XD Kidding, though i thought about it. 

By the way, when the kernel is updated, isn't the older one supposed to be include in the grub boot list? And in intrepid tab doesn't complete commands in the console, that seriously annoys me.

Synaptic says that I have linux-image-2.6.27-7.16 install, is that the latest one?

---

### Post by kansasnoob on 2008-11-19
Did you see any errors displayed when you ran:

```
sudo apt-get update
```

or:

```
sudo apt-get upgrade
```

If yes post the output of the terminal. If no try this command:

```
sudo apt-get -f install
```

Also post the output of:

```
cat /etc/issue
```

---

### Post by kansasnoob on 2008-11-19
> **chimera007 said:**
> None of the methods posted previously work. Argg, maybe reinstalling the whole system works? XD Kidding, though i thought about it. 

By the way, when the kernel is updated, isn't the older one supposed to be include in the grub boot list? And in intrepid tab doesn't complete commands in the console, that seriously annoys me.

Synaptic says that I have linux-image-2.6.27-7.16 install, is that the latest one?

I'm up to date:

> lance@lance-desktop:~$ cat /etc/issue
Ubuntu 8.10 \n \l

lance@lance-desktop:~$ uname -a
Linux lance-desktop 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:20 UTC 2008 i686 GNU/Linux


---

### Post by chimera007 on 2008-11-20
I don't see errors. There were no errors to begin with. Let me see if I can detail or explain properly what has happened. 

I received notification of new updates, opened update manager and clicked on download. electricity went out, and pc was working on temporary UPS, gives me about 3 minutes to turn of pc. So quickly I tried to cancel the downloading of packages, and I was presented with a message box which I don't remember the exact wording but basically meant not to show me these updates I canceled again.

Never got errors, it was only downloading packages, but now I am not sure if they have been applied. Since it was 150 MB and I was only at 3 package of probably 20. When I started the pc again, those updates were not presented again. I only saw a few newer ones regarding firefox and gnome.

---

