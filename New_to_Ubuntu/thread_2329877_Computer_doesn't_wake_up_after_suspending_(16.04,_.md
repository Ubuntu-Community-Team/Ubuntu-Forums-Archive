---
title: "Computer doesn't wake up after suspending (16.04,  Screen black but keyboard backlit)"
date: 2016-07-05
forum: New to Ubuntu
---

### Post by mishaal2 on 2016-07-05
I have been using Ubuntu 16.04 LTS on my Macbook Pro for the past few months and it seems to be working quite well. However, one issue I seem to run across at times is the following:

When I close my laptop lid, or if I leave my laptop unattended for a while, and return the computer fails to "wake up". The screen is totally black and there is no response from keyboard or trackpad/mouse input or even if I quickly press the power key. There is however light coming form the backlit keyboard. The only way to do anything is to hold-down the power button for a few seconds to force power off the laptop and then restart it, which is really quite inconvenient (and I imagine not great for my laptop).

When I looked up this issue, it said that the issue was resolved with Kernel 4.4.8; I installed and am running 4.4.8-040408-generic but the issue still persists.

I'm a) not sure if this means that its just the *screen* that isn't waking back up and b) regardless of it is a screen issue of not, not sure how to fix this.
So, does anyone know of some fix? Thank you!

---

### Post by mishaal2 on 2016-07-06
More information: looks like duration of time has something to do with it. I closed my laptop lid which should suspend my laptop. About 5 minutes later when I checked, opened it - it was fine. However, I think did this again but when I waited ~1 hr, it had the same issue described above. I also updated to kernel 4.5.0 and this is persisting...

---

### Post by Geoffrey_Arndt on 2016-07-06
So, the suspend (short sleep) is working fine, but "hibernation" (deep sleep) is not.    What are the "System Settings>Power" set on?   These can be changed for both battery operation or power-connected operation.   You can test if changing the settings to "Don't Suspend" . . . or change the time suspend starts and so on make a difference . . note there are trade-offs such as faster power drain, etc.

Another aspect of hibernation is how much (or little) swap space memory you have allocated.   How much RAM is on your system, and how big is the swap partition on your system?  I always like having 1 Gig more of swap space than my RAM (as that improves hibernation performance & system restore).

---

### Post by mishaal2 on 2016-07-07
> **Geoffrey_Arndt said:**
> So, the suspend (short sleep) is working fine, but "hibernation" (deep sleep) is not.    What are the "System Settings>Power" set on?   These can be changed for both battery operation or power-connected operation.   You can test if changing the settings to "Don't Suspend" . . . or change the time suspend starts and so on make a difference . . note there are trade-offs such as faster power drain, etc.

Another aspect of hibernation is how much (or little) swap space memory you have allocated.   How much RAM is on your system, and how big is the swap partition on your system?  I always like having 1 Gig more of swap space than my RAM (as that improves hibernation performance & system restore).

I'm not sure if its hibernate that is the issue; since it looks like none of my settings have hibernate (also doesn't the hibernate sort of "shut down" your computer? - I want to avoid this, since I have it dual booted, and would just prefer to have it suspend, regardless of lid close+time). Below is a picture of my Power settings. Not sure how to check the swap space.

[IMG]https://s31.postimg.org/u4csjz2sr/My_Power_Settings.png[/IMG]

---

### Post by mishaal2 on 2016-07-07
I do think I *may* have solved the issue by changing the settings in my logind.conf file:
HandleLidSwitchDocked=suspend
HandleLidSwitch=suspend

Not sure why but the Docked one also had to be changed.

**Edit: **Looks like I spoke too soon; this did not solve the problem... Left the computer lid down for a few hours and came back and had the same behavior.

---

### Post by Geoffrey_Arndt on 2016-07-13
Hibernate is not triggered by any user settings directly . . . but indirectly in that it's just a sequence of going from active (run) state = = > suspend state = = > hibernate state.    This happens automatically without user intervention.  A successful hibernation state results in a successful resume.   Hibernate is not the same as PC Halt/Shutdown.  The amount of ram allocated to swap is important because all process and system status data is written to swap before hibernation, and then retrieved from swap.   If inadequate swap is allocated, resume will fail and not result in a return to run-state.   So, check your swap, and change if necessary.   If that doesn't help, advise and we'll move on to the next item on the test list.

note:  one other config change you might want to consider . . when laptop is plugged in, change the 1 hour to suspend status to "Don't Suspend" . . . that may help the problem considerably.

---

### Post by mishaal2 on 2016-07-17
> **Geoffrey_Arndt said:**
> Hibernate is not triggered by any user settings directly . . . but indirectly in that it's just a sequence of going from active (run) state = = > suspend state = = > hibernate state.    This happens automatically without user intervention.  A successful hibernation state results in a successful resume.   Hibernate is not the same as PC Halt/Shutdown.  The amount of ram allocated to swap is important because all process and system status data is written to swap before hibernation, and then retrieved from swap.   If inadequate swap is allocated, resume will fail and not result in a return to run-state.   So, check your swap, and change if necessary.   If that doesn't help, advise and we'll move on to the next item on the test list.

note:  one other config change you might want to consider . . when laptop is plugged in, change the 1 hour to suspend status to "Don't Suspend" . . . that may help the problem considerably.


Ok! Thanks for the reply. 
Here is the output from terminal regarding swap info: 
```
mishaal@mishaal-MacBookPro:~$ sudo swapon -s
[sudo] password for mishaal: 
Filename                Type        Size    Used    Priority
/dev/sda4                                  partition    4097020    3100    -1
mishaal@mishaal-MacBookPro:~$ free -m
              total        used        free      shared  buff/cache   available
Mem:           3857        1221        1476         152        1159        2396
Swap:          4000           3        3997


```

I'm not sure if this is "inadequate" swap allocated. Can you advise? And if not, how could I change this? 

Thank you!

---

### Post by Geoffrey_Arndt on 2016-07-17
Looks like swap is not the issue . . your swap to ram ratio is OK.   So, if your machine is mostly connected to AC versus running off battery,  try changing your power settings to "Don't Suspend" for AC operation.    BTW, if you have to change your swap size - - it can be done via gparted (preferably from Live OS running on USB-Flashstick or DVD).

---

### Post by mishaal2 on 2016-07-18
I changed the settings to do not suspend, and it seems to work so far. Thank you!

---

### Post by donmorrison99 on 2016-07-18
I have been using Ubuntu 16.04 LTS on my HP Tower for the past month or so.  I am a Ubuntu beginner and I am experiencing the same problem -- on a desktop system rather a laptop.

If I leave my system unattended for a  while, and return the computer fails to "wake up". The screen is totally  black and there is no response from keyboard or trackpad/mouse input or  even if I quickly press the power key. There is however light coming from the mouse and keyboard. The only way to do anything is to hold-down  the power button for a few seconds to force power off the laptop and  then restart it, which is really quite inconvenient (and I imagine not  great for my system).

When I looked at this thread, I tried the same stuff.  I'm not sure how to interpret the numbers that look at the RAM and Swap space.  Mine look very similar.  I have 4GB of RAM.  I'm not sure how much Swap space I have.

I set the Power setting to Do Not Suspend.

I've made sure that my system is totally up to date.

It still keeps happening, but only if I leave system unattended for more than an hour or so.
  
So, does anyone know of some fix? Thank you!

---

### Post by Geoffrey_Arndt on 2016-07-23
donmorrison99,

Best to start a new thread on this as the Tower solution may be quite different (and I have nothing similar to test on).   Just put in a short descriptive title in the new to ubuntu section and more eyes can look at this and advise.   BTW, did you also set the additional option below the "Do not suspend"  . . to "Do Nothing"?  (even though you don't have a lid to close . . can't hurt to try.

---

### Post by Todd_Waddell on 2017-04-28
As Geoffrey_Arndt said, this is a separate issue.  Your tower almost certainly uses a USB keyboard.  Wake from sleep involves enabling wake for that USB device.  

I had the same problem and found the [solution here]("https://ubuntuforums.org/showthread.php?t=1968487").

---

