---
title: "Will an upgrade from 7.10 to 8.04 work properly?"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by RichTJ99 on 2008-10-02
Hi,

I have 7.10 Ubuntu & I enjoy using it but I dont use it often due to the lack of MS exchange support (crossover works OK).  Anyway I have not really updated it in a few months & I have either 120 updates or I can install 8.04.  

I was curious which is a better solution for me.  

Everything works just fine but I am guessing the updates are probably important. 

Thanks,
Rich

---

### Post by H.Callahan on 2008-10-02
If it were me, I would probably update the 7.10 to current before I tried an upgrade anyway -- unless you are going to nuke and pave, in which case, I would go with 8.04 (or wait a couple of weeks for 8.10).

---

### Post by kansasnoob on 2008-10-02
Always make sure you're updated before doing a distribution upgrade. Then the answer about upgrading is still **maybe**!

I've had about a 50% success rate with dist-upgrades. Half the time all goes well, the other half I end up having to do a clean install, so always backup all your info!

BTW Gutsy (aka 7.10) will receive updates until next April. You can stop the Update Manager from notifying you of Dist-Upgrades by enabling Configuration Editor - just go to System > Administration > Preferences > Main Menu and click on System Tools, then make sure Confiuration Editor is "ticked".

It'll then show up in Applications > System Tools > Configuration Editor. In config editor expand the "apps" folder and scroll down to "update manager", click on it and to the right you'll see "check_dist_upgrades", just "untick" it, and you won't be bothered with that again.

If you should ever want to do a distribution upgrade just go to terminal and:

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

```
sudo apt-get dist-upgrade
```

---

