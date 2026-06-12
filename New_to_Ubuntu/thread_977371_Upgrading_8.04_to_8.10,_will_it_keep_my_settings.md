---
title: "Upgrading 8.04 to 8.10, will it keep my settings?"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by legolas_w on 2008-11-10
Hi
Thank you for reading my post.
I am just wondering whether upgrading 8.04 to 8.10 keep following settings preserved?

- Firefox history, bookmark, and extensions : I have firefox 2.* in 8.10
- Thunderbird settings, emails, ....
- VPN connections, I am using network applet
- look and feel, I customized my ubuntu look and feel and want it preserved.


Thanks

---

### Post by mapes12 on 2008-11-10
You will need to make sure you have /home on a separate partition. Then everything will be preserved. See this HowTo: [http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

---

### Post by methodmarvel on 2008-11-10
> **mapes12 said:**
> You will need to make sure you have /home on a separate partition. Then everything will be preserved. See this HowTo: [http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)
Couldn't he just save his home (including hidden folders) to an external drive then copy them to the new distro install?

---

### Post by mapes12 on 2008-11-10
> Couldn't he just save his home (including hidden folders) to an external drive then copy them to the new distro install?

I wouldn't recommend this because the changes required to the etc/fstab mentioned in the HowTo will not take place and the system will not know where to find the new place for /home.

---

### Post by legolas_w on 2008-11-10
Thank you for your reply.
Does software like crossover,pidgin,.... which I installed will get removed?

Thanks.

---

### Post by philinux on 2008-11-10
I followed this guide and it worked ok. [Psychocats]("http://www.psychocats.net/ubuntu/separatehome")

I think the only trouble I had was caused by me.

---

### Post by Paqman on 2008-11-10
If you do an upgrade through Update Manager, then yes all your settings will be preserved. This is the main advantage of upgrading.

If you reinstall using a disk, then you'll need to either back up your /home, or have a seperate /home partition.

As for software, an upgrade will leave it intact. In fact anything that's in the repos will be have it's version updated. It's a good idea to disable any extra repos before starting the upgrade.

---

### Post by mapes12 on 2008-11-10
If you do a fresh install then to save having to install all your packages you can back them up using aptoncd: System>Applications> Synaptic Package Manager then search for it.

It also might be a good idea to back up your system files in case you want to restore your current system: [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

If you have home on a separate partition then exclude it from the backup. Include this in the tar command

```
--exclude=/home
```

---

### Post by muteXe on 2008-11-10
> **Paqman said:**
> If you do an upgrade through Update Manager, then yes all your settings will be preserved. This is the main advantage of upgrading.


With the main disadvantage being that you're "upgrade" might stall halfway through, not work, and completely ruin your OS.  This happened to me when going from Feisty to Gutsy.  I had to reinstall from fresh.  Since then i've put my home folder on a CD, and reinstalled from fresh, then copied my old folder back.

Maybe my upgrading problems are a one-off, but i thought you might like to know.

Tom

---

### Post by ichi@YUKI on 2008-11-10
i've been planning to upgrade from 7.10 to 8.04 and then to 8.10 but i'm the one stalling since i'm worried i have to start from scratch.

what might have caused that halfway stall? interrupted internet connection?

---

### Post by ichi@YUKI on 2008-11-10
i've been planning to upgrade from 7.10 to 8.04 and then to 8.10 but i'm the one stalling since i'm worried i have to start from scratch.

what might have caused that halfway stall? interrupted internet connection?

(sorry for the double post.. i don't know how it happened but it did.)

---

### Post by muteXe on 2008-11-10
Someone said it had something to do the proprietry (sorry if spelt incorrectly) graphics card driver, but i disabled this before "upgrading", so i still dont have an idea why it went bad I'm afraid.

---

### Post by legolas_w on 2008-11-10
Thank you everyone for your comments.
I used ubuntu 8.10 DVD and I upgrade my current ubuntu and it went very well.

---

