---
title: "boot problem- blank screen"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by andy128 on 2008-04-28
IBM Laptop T22 900mhz 256 ram  
Ubuntu 6.06 install

Having problem with boot-up.  Only happens on first boot after sitting all night.  Goes through drivers loading and files loading and then starts to boots and then blank screen with blinking cursor.  I hear the sound signaling enter user name and password- but the screen is blank.  I shut off the computer and re-boot and it comes up fine.  I can then shut it down a hundred times and it is fine booting up.  Leave it over night and the first boot does the same thing.  Have to shut off and re-boot and alls well. 

If, at the blank screen with the blinking cursor, I type in my user name, -hit enter-,  and then type in my password, the start up music starts and then hangs like a skipping record.  Have to shut down.

Any suggestions for me to check?

Tried sudo gedit /etc/usplash.conf 
and nothing comes up

Thanks in advance
Andy

---

### Post by schauerlich on 2008-04-29
You might try reconfiguring your xorg.conf file, although it is odd that it only happens when the computer sits for a few hours... Anyways, here's the command:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Also, there is a new, much more up to date version of Ubuntu that you might want to upgrade to. Given your computer's specs, I would recommend Xubuntu, although the decision is ultimately up to you which desktop environment you prefer.

---

### Post by erginemr on 2008-04-29
Since it occurs at the first boot only, presumably this is related to some hardware resisting to initialize properly at a cold start. It is hard to pinpoint which one, though. 

The system logs might tell more about what is really happening. So please examine the various system logs (esp. boot related ones) via "Main Menu -> Admin -> System Log" for a clue.

---

### Post by alienexplorers on 2008-04-29
What type of video card are you running?  Do you have the correct drivers running for it?  Almost sounds like you have a bad chip somewhere that only works when the system is warmed up.

---

### Post by andy128 on 2008-04-29
In the log is says :  piix4_smbus: probe of 0000:00:07.3 Failed with error-1

When reboot it says:
PIIX4: Chipset revision 1
PIIx4: not 100%% native mode: will probe irqs

Mean anything to anyone?

Andy

---

### Post by hermes0710 on 2008-04-29
I think there is a setting in bios about irq configuration (in a specific choice it is going to rearrange irqs in every boot (cold)). This is not probably the case but you can try checking this value and change it

---

### Post by andy128 on 2008-04-29
EDavidBurg,

Did as you suggested- will try it when I return from work in pm. Thanks.

Andy


hermes,

Didn't see anything to change.  Maybe elaborate a little because I am not exactly sure where I should find it and/or change it.

Andy

---

### Post by andy128 on 2008-04-29
Alien,

I will look that up tonight and post back.

Andy

---

