---
title: "Forgive me if this sounds like a rant...."
date: 2008-08-03
forum: New to Ubuntu
---

### Post by Jimmy9pints on 2008-08-03
because it's not intended that way at all.

However, I am getting really impatient with Ubuntu these days. I am not here to criticise anyone, I just want it fixed!!! 

I would like to ask the community to help if they can because I have multiple computer-crippling problems on my machine. 

I REALLY want to use Ubuntu as my only OS and a total work and personal computing solution. I realise that I have to put in the time to learn so I hope you can do that. Please bear with me and I promise that I will try to use what I learn to give back to the community. I am keen to teach others what I learn. 

Here are my problems I would like help with:

Firstly I cannot type at certain times in certain applications. Sometimes it's Open Office Writer, sometimes its Firefox...today it's Nautilus. I posted about this [here,]("http://ubuntuforums.org/showthread.php?t=864139") but never got it solved. 

Then, another surprise comes along. Text in title bars becomes tiny. Not always but it is a recurring problem. Now I have noticed that today text in Open office menu bars has gone small too and the icons in the tool bars have disappeared. 

Also, a problem which may be related is that my desktop screen resolution often (but not always) reverts to 800X640. The login screen is permanently like that. I wrote about that [here]("http://ubuntuforums.org/showthread.php?t=864139") but have had no luck with a solution. I am sure I didn't change any settings concerning this.

Another problem is my firefox has become very slow to load pages and hangs (grays out) on loading almost every page. I have tried creating a new profile and uninstalling add-ons and plugins and clearing old data - NONE OF IT WORKED. :(

Finally, another problem I have is that when using the power management (standard part of Ubuntu) to turn the computer off it will not reboot properly. It stalls and the screen turns off so I have to hard reset the computer. As a result I leave my computer on all night which I HATE doing because I am concerned about green issues. Again, I [posted]("http://ubuntuforums.org/showthread.php?t=836904") but had no luck getting it solved.

I know I am asking for a lot... but it's because I am still in an early learning phase and I just seem to have a LOT of problems since changing OS. My friends (even the geeky ones) thought I was mad to ditch Windows and despite all the problems I want to prove them wrong. I want to make Ubuntu and open source software my one and only and do my bit to convert others. 

I am already thinking about starting a non-profit NGO here in China to promote opensource....so please help if you can.

EDIT:Since posting this (about a minute ago) I suddenly cannot type in Firefox! This is copy-pasted from gedit. My machine is almost totally crippled. Should I just reinstall Ubuntu or what???

---

### Post by northern lights on 2008-08-03
Not too much of a rant, I'd say.

As for the reverting to 800x600 - run ```
nvidia-xconfig
```if it happened. (Shouldn't be the case often though)

When firefox freezes, what else are you doing? Can you post the output of ```
top
```at such a time?

---

### Post by ugm6hr on 2008-08-03
What hardware are you using?

What version of Ubuntu?

How did you install?

Have you updated?

These may all be relevant, but I am uncertain.  I have never heard of any of these problems before, and wonder whether your initial installation CD was corrupted.  Or perhaps a hardware issue?

Did Ubuntu run flawlessly from the LiveCD?

---

### Post by chuckyp on 2008-08-03
A lot of your problems sound like they are video related. What type of video card do you have is it the one in your signature? What have you done as far as drivers are concerned for the card?  Will you post the output of lspci so others can see all your hardware to help troubleshoot.

---

### Post by northern lights on 2008-08-03
> **chuckyp said:**
> Will you post the output of lspci so others can see all your hardware to help troubleshoot.Thought the signature would do, plus if it isn't happening right now, I am uncertain that info will be needed. Still you're right the more the better and it's in the nature of "uncertain" to not be sure what's relevant.

However, on this issue, I'd rather see ```
sudo lshw -C display
```

---

### Post by chuckyp on 2008-08-03
In reading your other posts it sounds like you are using the binary drivers from nvidia?  Is there any reason you are using those instead of the ones packaged in the repos such as nvidia-glx-new?  Also if the kernel changes as suggested in the other post and you were using the binary drivers from nvidia.com you need to reinstall them again.

With the nvidia drivers a kernel module is needed for every kernel installed on your system.  When you install the drivers it compiles this module for you.  The alternative is to use the driver in the repos which would install the kernel module automatically with every kernel change.  Keep in mind if you plan on switching drivers you need to completely remove the binary ones including the kernel module.

---

### Post by Jimmy9pints on 2008-08-03
Firstly: THANK YOU EVERYONE for your replies!

I will reply to each of you separately otherwise it's going to be a super lengthy reply!

**northern lights.**

I ran 

```
 nvidia-xconfig 
```

But I got this:

```
james@james-desktop:~$ nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

ERROR: Unable to write to directory '/etc/X11'.
```

Then the output of ```
top
``` is

```
top - 20:13:06 up  1:21,  2 users,  load average: 0.09, 0.14, 0.16
Tasks: 128 total,   1 running, 126 sleeping,   0 stopped,   1 zombie
Cpu(s):  0.3%us,  0.3%sy,  0.0%ni, 99.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1028336k total,   960848k used,    67488k free,    25512k buffers
Swap:  3012148k total,        0k used,  3012148k free,   446780k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
   33 root      10  -5     0    0    0 S    0  0.0   0:04.01 kacpi_notify       
 6509 root      15   0  171m  75m 9.9m S    0  7.5   2:19.30 Xorg               
 6721 james     15   0  144m 3356 1872 S    0  0.3   0:11.39 gnome-screensav    
 6729 james     15   0  234m  29m  12m S    0  3.0   1:14.14 compiz.real        
 7233 james     15   0  266m  24m  12m S    0  2.5   0:00.34 gnome-terminal     
    1 root      18   0  3960  836  572 S    0  0.1   0:01.82 init               
    2 root      11  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/0           
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1           
   11 root      10  -5     0    0    0 S    0  0.0   0:00.01 khelper            
   30 root      10  -5     0    0    0 S    0  0.0   0:00.00 kblockd/0  
```

Thanks, James.

---

### Post by northern lights on 2008-08-03
> **Jimmy9pints said:**
> 
But I got this:

```
james@james-desktop:~$ nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

ERROR: Unable to write to directory '/etc/X11'.
```
Run it as root - ```
gksu nvidia-xconfig
```my bad. Are you having resolution issues right now? Otherwise you might not want to run it anyways.

---

### Post by northern lights on 2008-08-03
> **Jimmy9pints said:**
> 
But I got this:

```
james@james-desktop:~$ nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

ERROR: Unable to write to directory '/etc/X11'.
```
Run it as root - ```
gksu nvidia-xconfig
```my bad. Are you having resolution issues right now? Otherwise you might not want to run it anyways.

When firefox freezes, what else are you doing? Can you post the output of ```
top
```at such a time?
Had firefox indeed just locked up? No other processes? If so, it's not load.

[EDIT]I was certain I edited in the first place...[/EDIT]

---

### Post by Jimmy9pints on 2008-08-03
To ugm6hr, again thanks for your reply.


> What hardware are you using?

I think all that info is in my signature. Is there anything else I have missed?

> What version of Ubuntu?

I am sure I installed Gusty - 7.04. But the output of ```
cat /etc/issue
``` is ```
Ubuntu 7.10 \n \l

``` so I guess it updated. By the way, the kernal was recently updated on my machine, it's now 2.6.22-15-generic.


> How did you install?

Let me think... from a live CD. I (gladly) totally overwrote Windows in the process.

> Have you updated?

Yes, everyday. To be honest the number of updates seems a bit over the top, especially for AWN dock (which is not working either by the way - but that's another story). 

EDIT: Oh and in answer to your question > Did Ubuntu run flawlessly from the LiveCD?, as far as I know it was running almost perfectly. I think the resolution was not correct and the sound wasn't smooth (a few clicks and gaps). But yes, it did work. 

Thanks,

james.

---

### Post by Bodsda on 2008-08-03
Some interesting problems you have there. 

As much as you wont these issues resolved sometimes Ubuntu is just so much quicker to reinstall then faff about, but if you want to keep the install troubleshooting each problem seperately will get more results.

When you posted your 'top' output it looks pretty stable to me, the only thing i would suggest is try without compiz, as your graphics card isn't that pokey it may not be running properly. 

Do you have the nvidia restricted drivers installed and in use?

Have you tried reinstalling firefox from the repo's?

7.04 is Fiesty, 7.10 is Gutsy. Maybe try a dist-upgrade to 8.04 Hardy

p.s
AWN not working properly is most likely due to compiz issues

---

### Post by Jimmy9pints on 2008-08-03
To chuckyp  	

> A lot of your problems sound like they are video related. What type of video card do you have is it the one in your signature? What have you done as far as drivers are concerned for the card? Will you post the output of lspci so others can see all your hardware to help troubleshoot.

I agree with you here, I've done a lot of searching for answers and graphics cards come up again and again as a source of these sorts of problems. 

Yes, my graphics card is the one in the signature. First of all I used the driver Ubuntu automatically chose for me. However, I had some problems with the WHOLE system freezing up!!! People at the time suggested that it was video card related, and suggested I try the proprietary drivers. I couldn't get them installed properly myself and a glx-gears test showed that my frame rate was super low. So I used Envy to get it installed. It pretty much totally cured the problems I had initially and my system hardly ever totally freezes now...just individual programs.

So in summary, proprietary Nvdia drivers installed via Envy (and yes I have reinstalled them several times recently). 

The output of > lspci is

```
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a2)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)

```


Thanks!

james.

---

### Post by Jimmy9pints on 2008-08-03
Another reply to northern lights:

the output of ```
sudo lshw -C display
``` is
```
*-display               
       description: VGA compatible controller
       product: G72 [GeForce 7300 LE]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia

```

Does that mean anything to you?

Cheers,

james

---

### Post by Bodsda on 2008-08-03
Do things get better after you run this command?

```
metacity --replace
```

run that in a terminal

if they do then it could well be a problem with your card and compiz

---

### Post by Jimmy9pints on 2008-08-03
To chuckyp again,

> ...sounds like you are using the binary drivers from nvidia? Is there any reason you are using those instead of the ones packaged in the repos such as nvidia-glx-new?

Yes, because originally at least, they caused my whole system to freeze. Maybe I should try them again.

> Also if the kernel changes as suggested in the other post and you were using the binary drivers from nvidia.com you need to reinstall them again. 

I have reinstalled them (two or three times) using Envy after getting these resolution problems. However, when I go into sysinfo, the I click on the NVidia icon, at the bottom it says
 "NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008"
I am not sure what that means, but Feb was when I first installed Ubuntu. Does that mean despite reinstalling the Nvidia drivers, the kernel module has not updated?

Cheers,

james.

---

### Post by northern lights on 2008-08-03
Sure enough everything can be tried and as such might as well try metacity. Nonetheless, compiz was not at all hogging resources.

Are these issues the case **right now**?

Have you run 'nvidia-xconfig' as root? (Only if resolution is screwed right now)

Did you install the drivers from source or from a .deb? If the latter is the case, they will still get updated.

---

### Post by Jimmy9pints on 2008-08-03
Another reply to northern lights:

> my bad. Are you having resolution issues right now? Otherwise you might not want to run it anyways.

No, I have corrected the resolution. I have to correct it most times I log in ... then log out and back in again to get the right settings. 

I ran ```
gksu nvidia-xconfig
``` so does that mean it will stay like it is? Hope so!

Cheers,

James./

---

### Post by eldragon on 2008-08-03
i may have missed something, but have you tried Hardy Heron? aka 8.04?

why not download the livecd and try it out?

i found many issues fixed under HH...

---

### Post by Jimmy9pints on 2008-08-03
Again to n lights

> When firefox freezes, what else are you doing? Can you post the output of

Well, always just trying to use my computer to full advantage. Right now, I have 8 windows open, inc 2 firefox (about 10 tabs in total), exaile, 2 terminals, sysinfo....and compiz running. Is there a code and output that gives an easy answer to this?

---

### Post by northern lights on 2008-08-03
> **Jimmy9pints said:**
> Again to n lights



Well, always just trying to use my computer to full advantage. Right now, I have 8 windows open, inc 2 firefox (about 10 tabs in total), exaile, 2 terminals, sysinfo....and compiz running. Is there a code and output that gives an easy answer to this?
Yes. 'top' and you posted it. But if that was not right after a freeze/lockup the info is pretty useless. If it was, it proves that CPU load and or memory lacks are not the culprit.

---

### Post by Jimmy9pints on 2008-08-03
Hi Bodsda, thanks for your reply

> 
As much as you wont these issues resolved sometimes Ubuntu is just so much quicker to reinstall then faff about, but if you want to keep the install troubleshooting each problem seperately will get more results. 

Although it's a lot more trouble, I'd prefer to faff around to try to get it sorted so I can learn something. I used to reinstall Windows every 6 months or so - now I am using Linux, I'd rather learn to maintain the system instead of regularly wiping it clean just to keep it running.

> your graphics card isn't that pokey it may not be running properly. 
Should I get a new graphics card?

> 
Do you have the nvidia restricted drivers installed and in use?
Yes. Installed via Envy.

> Have you tried reinstalling firefox from the repo's?
 
No. Do you recommend this? Would I loose all my data?

Cheers,

james.

---

### Post by Jimmy9pints on 2008-08-03
> Do things get better after you run this command?

```


metacity --replace
```


I have run that command...well it doesn't look as good... but we can see. To answer that question I would have to use the computer for a day or two to see if the problems crop up again. I don't have all the problems at once.

> 
if they do then it could well be a problem with your card and compiz
Even before answering your original question, I suspect you are right here.

Cheers,

james.

---

### Post by northern lights on 2008-08-03
> **Jimmy9pints said:**
> Should I get a new graphics card?
Not necessary.

> **Jimmy9pints said:**
> [question: do you have the restricted drivers installed?] Yes. Installed via Envy.You do not need Envy for a GeForce7XXX XX...

---

### Post by Jimmy9pints on 2008-08-03
> Sure enough everything can be tried and as such might as well try metacity. Nonetheless, compiz was not at all hogging resources.

Generally I have found in the past that I have less problems with compiz disabled. I will try again now to see if this solves the problems. 

> 
Are these issues the case right now?

These problems are very intermittent. It's like the cough that cures itself the moment you walk into see the doctor and reemerges in the middle of the night. 

Of my original problems I reported:
[LIST=1]
[*]Sometimes cannot type in certain apps
[*]Tiny text in title bars and menus
[*]Wrong resolution (Desktop)
[*]Wrong resolution (login screen) 
[*]Firefox freezing 
[*]Power management (not rebooting properly)
[/LIST]

Apart from 5, none are affecting me...but that DOES NOT mean they are necessarily fixed. Firefox is still freezing up. I'll have to set the power management to auto-off to test 2, 3, and 5. 

> 
Have you run 'nvidia-xconfig' as root? (Only if resolution is screwed right now)

Yes. Hope that fixes it.

> Did you install the drivers from source or from a .deb? If the latter is the case, they will still get updated.

Neither. Too much of a noob. Did it through Envy. 

Cheers,

james.

---

### Post by chuckyp on 2008-08-03
There is a reason Envy was not supported in gutsy. It is not the recomended way to install your drivers for your card.  I would suggest removing the drivers its installed and using the System > Administration > Restricted Drivers Manager to install the glx drivers from the repos.

It should be noted Envy-ng is now supported I guess. At least from what i've seen in IRC. IMO this is all video related and by that I mean driver related.

Like others have mentioned Hardy is now out and that is the current LTS version of ubuntu.  You may want to consider installing it or upgrading. Either way try the drivers in the repos out first. They are easier to install then Envy was.

---

### Post by Jimmy9pints on 2008-08-03
to Eldragon

> why not download the livecd and try it out?

i found many issues fixed under HH...

You're the second person to suggest this so I might try it. Just thought that there should be no reason that Gutsy should work properly really. 

cheers,

james.

---

### Post by Bodsda on 2008-08-03
When i said 'have you got the restricted drivers' i meant using the method mentioned above

System--> Admin--> Hardware drivers--> Enable

new graphics card is not needed unless you are planning on doing heavy media/graphic work 

When posting the output of 'top' we need the command to be executed at the moment it starts lagging, your previous post showed no signs of anything really.

Faffing around is FUN!!! and learning is all part of the experience, but if my machine started to get to the severity of unstableness i would be inclined to back up any important data

If you install firefox from the repos, as long as you dont use -purge you will still have all your settings i believe.

---

### Post by Jimmy9pints on 2008-08-03
chuckyp, ok I will try to get rid of the proprietary drivers and install the opensource ones. 

By the way, is there a tutorial out there to tell me how to remove the original drivers AND the kernel module?

Later I will install Hardy, but first I have to partition my drive so I don't delete all my docs. 

Thank you everyone. I will try to apply the fixes you suggest and use my computer for a while to test it out. If there are problems remaining, I'll post them tomorrow. 

James.

---

### Post by wpshooter on 2008-08-03
Jimmy:

I think that though you are relucant to WIPE your computer and start all over, I think that eventually that you are going to get flustrated with trying to fix this piece-meal.

I suggest that you save any thing of importance that you might have on the computer and then get [www.killdisk.com](www.killdisk.com) to WIPE the drive completely clean and then re-install Gutsy from a copy of the ALTERNATE (text based) CD version of Ubuntu on which you have verified the integrity of the CD by running the verification function that is found on the initial Ubuntu boot screen menu.

I suggest that you use the manual partitioning method to partition your drive.  You should have 3 partitions /=root (make bootable), /home= home, /swap = swap.

Then once you get the O/S installed the ONLY thing that I would initialy change would be to go to system/preferences/appearance/visual effect and make sure that NONE is chosen.

Do not install any drivers other than what the O/S has installed and see if everything works correctly for a while.  Then and only then if things are not working correctly, should you consider installing either restricted drivers or drivers from any other source.

REMEMBER THIS, IF YOU INSTALL ANYTHING ON YOUR SYSTEM THAT IS NOT FROM AN OFFICIAL UBUNTU SOURCE, YOU ARE TAKING **SOME** CHANCE ON YOUR SYSTEM ON WORKING PROPERLY, I.E. STICK WITH WHAT THE O/S HAS INSTALLED OR GET IT FROM SYNAPTIC.

Good luck.

---

### Post by ugm6hr on 2008-08-03
> **Jimmy9pints said:**
> Later I will install Hardy, but first I have to partition my drive so I don't delete all my docs. 

I would suggest you create a separate /home partition.  That way, reinstallations will not jeopardise your data at all, and only take about 30mins each time.

I've found that it is quicker to just reinstall every 6 months with the new upgraded version rather than using Update Manager / dist-upgrade to do it.  Keeps things running smoothly for me...

---

### Post by Jimmy9pints on 2008-08-04
Again for those people who asked me if I am having the problems **right now** (norther lights)

I have used the system for 24 hours now to see if the fixes have had an effect. 

_**The fixes**_ 

1.```
gksu nvidia-xconfig
```
and 
2.```
metacity --replace
```
3. Removed all add-ons from firefox.

**_The result_**

1.Basically I ran the first code to keep the current (correct) resolution. But when I rebooted, it was back to the old 800X640. 

2. Running the second one turned off compiz and activated metacity. It changed the settings until I rebooted... now compiz is back (which may be the source of my problems). It seemed to run a little better with metacity but still had Firefox freezing up on me. 

3. Removing all the add-ons from Firefox hasn't made the blind bit of difference. 

So it seems, I am still stuck with ALL the original problems.

   1. Sometimes cannot type in certain apps
   2. Tiny text in title bars and menus
   3. Wrong resolution (Desktop)
   4. Wrong resolution (login screen)
   5. Firefox freezing
   6. Power management (not rebooting properly)

**_N.B_**

No I still haven't tried the opensource drivers (partly because they were totally screwy in the fist place - hence me using the proprietary ones). Instead, I am going to reinstall before I go mad. Thank you for your help anyway.

Someone please point me in the direction of a good set up.

---

