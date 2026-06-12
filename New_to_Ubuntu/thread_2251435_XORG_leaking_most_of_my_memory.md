---
title: "XORG leaking most of my memory"
date: 2014-11-04
forum: New to Ubuntu
---

### Post by Gloris_Ian on 2014-11-04
Hello again! I am having an issue with xorg who is using insane amounts of my RAM and since my pc is not exactly bleeding edge, it's posing a serious problem. After start up, all processess togethet use about 600mb of memory. After a few hours of usage and with many apps open it's around 3gb. However, even if I close them all with no apps running in background xorg keeps eating about 1,5gb of memory, is that normal? My pc runs non-stop and even though I did not need to reboot it so far, I probably will eventually. I opened the system monitor to see other apps from system side to see which one uses most memory after xorg and it's like: compiz: 300mb, nautilus 150mb, all other proc. are under 50 mb,not sure what's the issue with xorg, should I be worried? Can this be fixed? I don't want to have to restart my pc everytime it starts to eat up all my RAM.

Other info: ubuntu 14,04, Intel G840 2,8Ghz, 3Gb Ram, HD6570 GPU; 500GB HDD, and if it has anything to do with this, HDD is encrypted using ubuntu built-in encryption.

---

### Post by philinux on 2014-11-04
Is there a difference in performance at all after a few hours, or does it run just the same?

---

### Post by sudodus on 2014-11-04
Please post the output of the command

```
free -m
```

1. Right after reboot

2. After the system has been running for some hour (or when you notice a big difference)

You can also install a good and light-weight tool to monitor the usage of memory and CPU: ***htop***

```
sudo apt-get install htop
```

and then run ```
htop
``` in a terminal window. Then you will notice which programs are using RAM and CPU.

It will be easier to discuss and if necessary, suggest what to do, when we know what those commands/tools show.

---

### Post by Gloris_Ian on 2014-11-04
Hey! Thanks for replies! :)  
 

 Philinux: Well it seems that if I do absolutely nothing with nothing running in the background the xorg stagnates at the amount of memory it has gotten (no drop). It continues to rise very slowly but surely if i use the pc.  
 

 Sudodus:  
 When I attempt to install htop through terminal I get the following message:  
 

 *"Err [http://hr.archive.ubuntu.com/ubuntu/](http://hr.archive.ubuntu.com/ubuntu/) trusty/universe htop amd64 1.0.2-3 * 
   *Something wicked happened resolving 'hr.archive.ubuntu.com:http' (-5 - No address associated with hostname) * 
 *E: Failed to fetch [http://hr.archive.ubuntu.com/ubuntu/pool/universe/h/htop/htop_1.0.2-3_amd64.deb](http://hr.archive.ubuntu.com/ubuntu/pool/universe/h/htop/htop_1.0.2-3_amd64.deb)  Something wicked happened resolving 'hr.archive.ubuntu.com:http' (-5 - No address associated with hostname) * 
 

 *E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?" * 
 

 I copy pasted your command the apt-get, so I did not misstype.  
 

 Anyways, here is the output of the other requested data:  
 

 free -m:  
 
Also note that at this time, when running the command no apps were open, none that I opened

 After is is running for few days:  
 

              ```
              total       used       free     shared    buffers     cached  
 Mem:          3936       3794        142         14         35       1197  
 -/+ buffers/cache:       [COLOR=#ff0000]2561[/COLOR]       1374  
 Swap:            0          0          0  
 
```

 After I just rebooted my pc:
 

              ```
              total       used       free     shared    buffers     cached
 Mem:          3936       1182       2754         10         70        605
 -/+ buffers/cache:        [COLOR=#ff0000]505[/COLOR]       3430
 Swap:            0          0          0

```

---

### Post by sudodus on 2014-11-04
1. In the output from ***free -m*** the [COLOR=#ff0000]red[/COLOR] numbers might be most relevant to watch.

2. The problem with the installer might be solved with the following commands (all of them or part of them). They were originally posted by *oldfred* (and you need sudo for all of them)

```
# This will reinstall if not current. (from my chroot procedure which does not have sudo on every line,
# so use the sudo -i first).
 
#if not chroot use: sudo -i

#houseclean
apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean

#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first

#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade

# fix Broken packages -f 
sudo apt-get -f install
dpkg --configure -a
```

---

### Post by Gloris_Ian on 2014-11-04
Installed htop through ubuntu software center, had to confirm that I want unathorized third party software something like that. Tried and it works, what now?

---

### Post by sudodus on 2014-11-04
Check which application programs that use most memory and CPU. Let us know your observations and we can discuss what is normal and what is not. (There are several people here, that know more about memory usage than I.)

---

### Post by Gloris_Ian on 2014-11-04
The output of "free -m" shows no colors other than white, did it several times it's always white font.

I first noticed this problem yesterday, I had like 30+ firefox tabs open so the system slowed quite a bit, then I noticed when I turned firefox off that xorg remains at his memory state. What I am trying to say that I suspect firefox has something to do with it even though I have no idea how to confirm it, seems normal in htop. 

There's also a lot of yellow lines in "mem" part of htop up. A lot of cache, is that normal?

---

### Post by sudodus on 2014-11-04
> **Gloris_Ian said:**
> The output of "free -m" shows no colors other than white, did it several times it's always white font.

I meant the red numbers in your previous post (post #4:[COLOR=#ff0000] 2561 [/COLOR]and[COLOR=#ff0000] 505[/COLOR])> 
I first noticed this problem yesterday, I had like 30+ firefox tabs open so the system slowed quite a bit, then I noticed when I turned firefox off that xorg remains at his memory state. What I am trying to say that I suspect firefox has something to do with it even though I have no idea how to confirm it, seems normal in htop. 

There's also a lot of yellow lines in "mem" part of htop up. A lot of cache, is that normal?

Cache is no problem, it is used when available, but the number at the position of those red numbers should be reduced (maybe not completely restored, but reduced) when you close an application program.

---

### Post by Gloris_Ian on 2014-11-04
Ok apology for that, wasn't sure what you were reffering to. Yeah, I  tried experimenting with firefox, I opened 20 tabs and then run free -m  and did it afterwards when I closed firefox (red numbers): before-1451 after-900. Everytime I do that, even though the numbers do go down, they never go down the old numbers, not completely, it adds up. SO if I open and then close 20 tabs 10 times, red numbers will go up by like 400mb and will remain at that and will continue to rise each time I do that, is there something wrong with firefox? Should I reinstall it?

I'll experiment with other apps and let you know. Is there a way to restart xorg without rebooting pc?

---

### Post by sudodus on 2014-11-04
You can start a text screen with the hotkey combination

***ctrl + alt + F2***

Then run

```
sudo service lightdm stop
```

to stop the graphical desktop, and 

```
sudo service lightdm start
```

to start it again. It will run at

***ctrl + alt + F7***

---

### Post by sudodus on 2014-11-04
> **Gloris_Ian said:**
> Ok apology for that, wasn't sure what you were reffering to. Yeah, I  tried experimenting with firefox, I opened 20 tabs and then run free -m  and did it afterwards when I closed firefox (red numbers): before-1451 after-900. Everytime I do that, even though the numbers do go down, they never go down the old numbers, not completely, it adds up. SO if I open and then close 20 tabs 10 times, red numbers will go up by like 400mb and will remain at that and will continue to rise each time I do that, *[COLOR=#ff0000]**is there something wrong with firefox?**[/COLOR]* Should I reinstall it?

I'll experiment with other apps and let you know. Is there a way to restart xorg without rebooting pc?

I'm not sure, if this is normal or if something is wrong with firefox. *[COLOR=#ff0000]To everybody[/COLOR]* reading this thread: If you think you can add something, please enter the discussion and tell us what you think or know :-)

---

### Post by Penguin360 on 2014-11-04
I opened about 20 tabs in FireFox, then closed them, then reopened them, and closed them. I don't see big change in memory usage.

Do you have Google Chrome installed? If yes, you can try the same thing with Google Chrome to see if the memory usage adds up.

Or you can try to kill the FireFox process after you closed all tabs to see if that makes any difference.

---

### Post by Gloris_Ian on 2014-11-05
Found a temporary solution: not use firefox   Not a real solution but oh well. Tried firefox with limiting its cache to 50 or less mb, that helped a little. Also disabled all addons and java and everything, that reduced the xorg memory leak but since it was still going up, albeit very slowly, I just moved to a different browser. THank you for your help it is appreciated!

---

