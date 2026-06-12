---
title: "Having problem with suspend &amp; hibernate"
date: 2012-01-22
forum: New to Ubuntu
---

### Post by tkabir11 on 2012-01-22
I hardly ever put my laptop on suspend/hibernate, so I don't know how long I've had this issue for. I'm on Ubuntu 11.10. When I turn my laptop back on again from suspend- a blank screen shows up and none of the keyboard buttons/touch-pad respond; only way to recover is holding down the power button to restart. Same goes for waking up from hibernate- but this time there's a blinking cursor on top left side of screen. 
I did a quick search on Google and most problems are related to suspend/hibernate options not working at all.  
Anyone know how to fix this problem?

---

### Post by davethewave83 on 2012-01-22
> **tkabir11 said:**
> I hardly ever put my laptop on suspend/hibernate, so I don't know how long I've had this issue for. I'm on Ubuntu 11.10. When I turn my laptop back on again from suspend- a blank screen shows up and none of the keyboard buttons/touch-pad respond; only way to recover is holding down the power button to restart. Same goes for waking up from hibernate- but this time there's a blinking cursor on top left side of screen. 
I did a quick search on Google and most problems are related to suspend/hibernate options not working at all.  
Anyone know how to fix this problem?

how long do you wait for it to respond? When mine hibernates, if I turn it back on it boots to a blank screen for a bit as it restores the hibernation file. If you're waiting 5minutes+ and nothing happens then something is probably wrong but I wouldn't know what.

---

### Post by tkabir11 on 2012-01-22
Yea I did wait a bit longer than I usually do- still the same.

---

### Post by Mihon on 2012-01-22
Hy, I am having the same problem...

I have just installed Ubuntu 11.10 on Toshiba Satellite A200-10W and noticed that every time I put computer to sleep or hibernate it wont start again. It is the same when I close the lid. It only comes to light grey screen and nothin more happens. Than I have to push the hard reset button for couple of secounds to shut it down and than I have to restart computer again.

Does anyone have the solution to the problem? It is realy anoing to shut the comp down every time you do not need it and than to start it again... 

Thanks

---

### Post by nipunshakya on 2012-01-22
some have the problem fixed and some haven't fixed it when i read it [here]("http://www.omgubuntu.co.uk/2011/05/how-to-fix-suspendhibernate-in-ubuntu-10-10/")

Hope works for u guys...

Regards,WinuxUser

---

### Post by tkabir11 on 2012-01-22
> **WinuxUser said:**
> some have the problem fixed and some haven't fixed it when i read it [here]("http://www.omgubuntu.co.uk/2011/05/how-to-fix-suspendhibernate-in-ubuntu-10-10/")

Hope works for u guys...

Regards,WinuxUser

I've tried that solution already- but no luck. I tried many others too- all involving creating and writing codes into scripts like that one- but none of them have made any difference at all. This is really starting to bug me now :(

---

### Post by nipunshakya on 2012-01-22
Its sad to hear that. But like i said in my previous comment, the link i advised u showed that some succeeded while some didn't. So i wasn't sure of myself whether it would work for u too....Maybe u should wait for someone to help you out...Goodluck

Regards,WInuxUser

---

### Post by bogan on 2012-01-22
Hi!, **tkabir11**,

I had lots of problems with recovering from Suspend in versions prior to 11.04, but much less with 11.10.

I found that though it does not respond to Mouse movement nor Clicks and most keystrokes, it nearly always responds to 'Enter'; without having to press the power button..

The system light on my desktop computer flashes continuously in Ubuntu 'Suspend', or in Windows 'Sleep', and pressing 'Enter' the light changes to on all the time, so I know it has awakened even though the black screen stays unchanged. [ I just checked it, and the 'Long' delay was actually 18 seconds!! ].

However, I have to admit that recently it has started to refuse to reconnect the WiFi, so if I need to go on the Net, I have to do a Restart, which defeats the whole purpose.

Chao!, **bogan**.

---

### Post by bogan on 2012-01-24
Hi!, **tkabir11**,

I Posted:>  However, I have to admit that recently it [ - recovering from Suspend - ] has started to refuse to  reconnect the WiFi, so if I need to go on the Net, I have to do a  Restart, which defeats the whole purpose.

I have found a trick to overcome this:

I insert a Wlan USB dongle that I know works with the installed drivers and it triggers the NetworkManager to rescan and connect successfully.

Chao!,** bogan**.

---

### Post by gordintoronto on 2012-01-24
"When I turn my laptop back on again from suspend..." My laptop suspends when I close the lid. When I open the lid, it fires up perfectly. HP G62 laptop.

What brand and (exact!) model do you have? If you Google (model) suspend solved, you might get some useful information.

---

### Post by tkabir11 on 2012-01-25
> **gordintoronto said:**
> "When I turn my laptop back on again from suspend..." My laptop suspends when I close the lid. When I open the lid, it fires up perfectly. HP G62 laptop.

What brand and (exact!) model do you have? If you Google (model) suspend solved, you might get some useful information.

Ok- I've got an HP G60- pretty close to yours I guess. I found a few solutions on Google- but none of them worked. Although- at one place I read that this problem is due to a module that cannot be reloaded on wake. I checked my pm-powersave log as suggested- but I just couldn't figure out what exactly is going wrong during suspend-resume. This is by far the biggest problem I've faced in Ubuntu.

---

### Post by krespim on 2012-02-18
> **tkabir11 said:**
> I hardly ever put my laptop on suspend/hibernate, so I don't know how long I've had this issue for. I'm on Ubuntu 11.10. When I turn my laptop back on again from suspend- a blank screen shows up and none of the keyboard buttons/touch-pad respond; only way to recover is holding down the power button to restart. Same goes for waking up from hibernate- but this time there's a blinking cursor on top left side of screen. 
I did a quick search on Google and most problems are related to suspend/hibernate options not working at all.  
Anyone know how to fix this problem?

I'm having precisely the same problem. When recovering from hibernation it rarely works (I get he blank screen of death staring at me) and from suspension it is a hit and miss. I have to shutdown the computer in the on/off button and restart. 

This is actually very annoying and frustrating because it means that when I am working on something important, I will have to save all work and shut down (or keep the computer running for days) and then restart. This is IMO not a minor bug and it would be nice to have a working solution for it.

Another issue is that whenever I remove the power cable Ubutu returns the message that the "battery is running low" regardless of how full it is. This means that the option to "hibernate when battery is critically low" has to be disabled to avoid the problem above: hibernation -> force reboot.

I am running Ubuntu 10.10 on a Toshiba T230-10J with extra 4GB RAM.  

Any help will be appreciated.

---

