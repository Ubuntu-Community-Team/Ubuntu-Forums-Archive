---
title: "Acer Aspire One wireless card not recognised"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by Teh N00binator on 2008-10-16
Hi all, i'm completely new to all of this, and i have encountered a problem.

I had installed ubuntu 8.4 onto my laptop, and i have had it running fine for a few weeks now, but last night i updated it, and have since not been able to use my wireless card. I have no idea what's happened to it and any help would be greatly appreciated.

Thanks all.

P.S, my Acer is the basic specced 512 mb RAM linux version, not too sure of specifics.

---

### Post by az on 2008-10-16
The kernel was update recently.  If you had to compile a driver by hand to get your wireless working, you will have to do it again (for the new kernel you are running).

In the meantime, you can boot into the old kernel and your wireless should work while you are running that kernel.

---

### Post by Teh N00binator on 2008-10-16
> **az said:**
> The kernel was update recently.  If you had to compile a driver by hand to get your wireless working, you will have to do it again (for the new kernel you are running).

In the meantime, you can boot into the old kernel and your wireless should work while you are running that kernel.

I didn't update the entire kernel, i just installed what the update manager said i should install, and i did, and now the wireless isn't recognised

I'm still on the same computer and everything seems to be running normally, except the wireless.... Originally, the wireless just worked straight out of the box.

This is so confuddling for me xD

---

### Post by Ryadt on 2008-10-16
Try to find if your wireless card is in System > Administration > Hardware Drivers. If it's in there, enable it.

---

### Post by Teh N00binator on 2008-10-16
Yeah it says it's enabled but not in use.... ::confused:

---

### Post by Ryadt on 2008-10-16
Disable it and then try doing an update```
sudo apt-get update && sudo apt-get upgrade
``` 

Retry to enable it after the update

---

### Post by Teh N00binator on 2008-10-16
> **Ryadt said:**
> Disable it and then try doing an update```
sudo apt-get update && sudo apt-get upgrade
``` 

Retry to enable it after the update

Done, and still no luck... aah well, thanks for all the help guys, looks like i'll have to re-install a stable kernel.

---

### Post by Ryadt on 2008-10-16
> **Teh N00binator said:**
> Done, and still no luck... aah well, thanks for all the help guys, looks like i'll have to re-install a stable kernel.
First try to disable it.. reboot and then re-enable it.. and then reboot again.

---

### Post by Teh N00binator on 2008-10-16
> **Ryadt said:**
> First try to disable it.. reboot and then re-enable it.. and then reboot again.

yep, figures no luck either... i really don't know why there's no roll-back button on the update manager

---

### Post by Teh N00binator on 2008-10-16
Just noticed something else aswell, the fan is on constantly...(the fan only used to come on when the processor was overheating) gah, why aren't these things tested before release?

---

### Post by Ryadt on 2008-10-16
Try to boot in the kernel that you were using previously.

---

### Post by Teh N00binator on 2008-10-16
But I haven't changed the kernel!

---

### Post by Ryadt on 2008-10-16
What kernel are you using?
```
uname -r
```will give you the answer.

---

### Post by Teh N00binator on 2008-10-16
2.6.24-21-generic ... no idea what that means :P

*edit* i meant the generic bit btw :P

---

### Post by Ryadt on 2008-10-16
> **Teh N00binator said:**
> 2.6.24-21-generic ... no idea what that means :P

*edit* i meant the generic bit btw :P
neither do I 

When you boot you should get the option to choose the kernel version you want to use. If not, press escape just after the bios finishes to load and the choose kernel 2.6.24-19-generic.

---

### Post by Teh N00binator on 2008-10-16
awesome! thanks a lot man, just one more question, will i have to keep on choosing to boot up this version of Ubuntu?

---

### Post by Ayuthia on 2008-10-16
Out of curiosity, when you are in 2.6.24-21-generic, did you check lshw -C network?  I am curious if you are missing the module for your wireless.  Sometimes on upgrades the linux-restricted-modules is held up for one reason or another.  If lshw -C network shows your card as disabled, I am guessing that the module is missing.

---

### Post by Teh N00binator on 2008-10-16
err, no  I didn't , but i will get round to doing it when i can be bothered, but for the meantime, i'm happy enough that it works 
:p but god help me if an update breaks it again :/

---

### Post by Jakey_TheSnake on 2008-12-28
Download this wireless driver: [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3879-20081204.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3879-20081204.tar.gz) 

Move it to your Documents folder and extract. 

Open up a Terminal (Applications > Accessories > Terminal)

Type:

```
cd /home/username/Documents/madwifi-hal-0.10.5.6-r3879-20081204
```

Press enter. Then type:

```
make
```

Will take a couple of minutes, wait until you get the correct prompt again. 

Then type:

```
sudo make install
```

Let it do it's stuff, then:

```
modprobe ath_pci
```

Restart laptop, then when you click your networks icon you should get that beautiful list of wireless networks to connect to. 

Sorry for late reply *shrugs*

---

### Post by melicious on 2009-05-29
Wow, you rock... Seriously. I installed VMware and it somehow broke my Wireless (Acer One). Your instructions fixed the problem. Many thanks.

---

