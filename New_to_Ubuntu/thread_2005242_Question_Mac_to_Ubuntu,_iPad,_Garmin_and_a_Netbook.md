---
title: "Question: Mac to Ubuntu, iPad, Garmin and a Netbook."
date: 2012-06-17
forum: New to Ubuntu
---

### Post by psyclechick on 2012-06-17
Hi Everyone,
 
Basically I am looking to return to Ubuntu after a few years with a Macbook Pro (that has been given to my Mum and I, in turn have aquired her old Dell Inspiron Mini netbook running Windows 7...for now...)
 
I have some questions, firstly relating to the current LTS 12.04 of Ubuntu (as the laptop wiki seems to stop with 10.04 when discussing the Inspiron Mini). The netbook has a hard soldered (ie; non-upgradeable) 1 gig of memory so looking at running Xubuntu (as I actually like XFCE) or even Lubuntu (reading the threads about both)
My questions pertain to how stripped down either version is, and how much it will affect if any, the questions I have below.
 
Apologies to the mods if these are the same noob questions, although I have searched but many threads are out of date, or closed.
 
1) Syncing an iPad. Can it be done? And I am not talking just music, I am talking about being able to backup apps, photo's info the same as I would with iTunes. Or, my other option, just sync the iPad with iTunes initially and then install Ubuntu and just use iCloud for the iPad? (Keeping in mind I have yet to get an iPad as you will see further below - and no! its not negotiable...I am getting one, and no Android tablets lol)
 
1a) Will full blown Ubuntu run happily on a 1 gig netbook these days (no Compiz etc)? 
 
2) If it is possible to sync will having either Xubuntu or Lubuntu limit this? I do remember years ago when I first started using Ubuntu and its variants that Synaptic would end up asking you to install the entire Gnome (or Unity in this case I suppose) libs or the 'ubuntu desktop' package.....
 
3) I am an avid cyclist and I upload my data from a Garmin Edge 500 to Strava and it requires a browser plug in. Any other cyclists using Ubuntu and a Garmin Edge device and uploading to Garmin and Strava? (I have found this in my travels and wondered if anyone else is using it to much success? - [https://forums.garmin.com/showthread.php?t=4448&page=7](https://forums.garmin.com/showthread.php?t=4448&page=7) and this [http://www.andreas-diesner.de/garminplugin/doku.php](http://www.andreas-diesner.de/garminplugin/doku.php) ) This is VERY important...more so than the iPad ;-) and it is a deal breaker unfortunately if its buggy as I cannot obviously run a VM on a little tiny 1G netbook that struggled with XP and now Win 7!
 
The reason I am keen about the iPad is I have switched to an Android device (HTC One XL) but there are some iPhone apps I have paid for that I still wish to retain their usage of, as well as iMessage and Facetime (both I use a lot with overseas friends - and no there will be no converting to other methods etc etc :-P)
 
Sorry for the long winded post - but I figured to just group it all together rather than a whole heap of new thread - dunno how you mods would prefer it...but thanks in advance. I tend to jump on the forum when I am at work as its the only time I really get to spend in front of a computer so my responses may be sporadic in timing.
 
Cheers, and thanks again. :)

---

### Post by PhantomTurtle on 2012-06-17
> **psyclechick said:**
> Hi Everyone,
 
Basically I am looking to return to Ubuntu after a few years with a Macbook Pro (that has been given to my Mum and I, in turn have aquired her old Dell Inspiron Mini netbook running Windows 7...for now...)
 
I have some questions, firstly relating to the current LTS 12.04 of Ubuntu (as the laptop wiki seems to stop with 10.04 when discussing the Inspiron Mini). The netbook has a hard soldered (ie; non-upgradeable) 1 gig of memory so looking at running Xubuntu (as I actually like XFCE) or even Lubuntu (reading the threads about both)
My questions pertain to how stripped down either version is, and how much it will affect if any, the questions I have below.
 
Apologies to the mods if these are the same noob questions, although I have searched but many threads are out of date, or closed.
 
1) Syncing an iPad. Can it be done? And I am not talking just music, I am talking about being able to backup apps, photo's info the same as I would with iTunes. Or, my other option, just sync the iPad with iTunes initially and then install Ubuntu and just use iCloud for the iPad? (Keeping in mind I have yet to get an iPad as you will see further below - and no! its not negotiable...I am getting one, and no Android tablets lol)
 
1a) Will full blown Ubuntu run happily on a 1 gig netbook these days (no Compiz etc)? 
 
2) If it is possible to sync will having either Xubuntu or Lubuntu limit this? I do remember years ago when I first started using Ubuntu and its variants that Synaptic would end up asking you to install the entire Gnome (or Unity in this case I suppose) libs or the 'ubuntu desktop' package.....
 
3) I am an avid cyclist and I upload my data from a Garmin Edge 500 to Strava and it requires a browser plug in. Any other cyclists using Ubuntu and a Garmin Edge device and uploading to Garmin and Strava? (I have found this in my travels and wondered if anyone else is using it to much success? - [https://forums.garmin.com/showthread.php?t=4448&page=7](https://forums.garmin.com/showthread.php?t=4448&page=7) and this [http://www.andreas-diesner.de/garminplugin/doku.php](http://www.andreas-diesner.de/garminplugin/doku.php) ) This is VERY important...more so than the iPad ;-) and it is a deal breaker unfortunately if its buggy as I cannot obviously run a VM on a little tiny 1G netbook that struggled with XP and now Win 7!
 
The reason I am keen about the iPad is I have switched to an Android device (HTC One XL) but there are some iPhone apps I have paid for that I still wish to retain their usage of, as well as iMessage and Facetime (both I use a lot with overseas friends - and no there will be no converting to other methods etc etc :-P)
 
Sorry for the long winded post - but I figured to just group it all together rather than a whole heap of new thread - dunno how you mods would prefer it...but thanks in advance. I tend to jump on the forum when I am at work as its the only time I really get to spend in front of a computer so my responses may be sporadic in timing.
 
Cheers, and thanks again. :)

1. Syncing Apps is not possible without iTunes. iTunes does not run very well in Wine, so you are going to have to install that copy of Windows in a virtual machine after you overwrite it. Or you can use iCloud as you explained(not sure how that works, but looks like you know how to do it). I believe You can still sync music using a supported music player(read more about that [here]("https://help.ubuntu.com/community/PortableDevices/iPod")). 

1a. It should run fine. I used have an old desktop that ran ubuntu 11.10 with Gnome Classic and it ran fine. This desktop had a pentium 4 1.7GHz processor and 1GB of RAM. I think it will run really well with XFCE.

2. It shouldn't, unless you are installing a gnome app with gnome dependencies.

3. Not completely sure. It might work, it might not. You are just going to have to try it and see. Alternatively you can dual-boot with Windows and test it first. If you are satisfied then, delete the windows partition. If it doesn't work then keep the windows partition and use it for that.

EDIT: for the browser plugin, there is a Ubuntu ppa and it supports precise, so you should be fine.

---

### Post by blackbird34 on 2012-06-17
You might need to dual boot that netbook if the iPad is non negotiable ;-)

---

### Post by Autodave on 2012-06-17
[QUOTE=psyclechick;12034053]Hi Everyone,
 
  
1a) Will full blown Ubuntu run happily on a 1 gig netbook these days (no Compiz etc)? 
 
  
ASUS 900EEE running 12.04, Unity, on a 700mhz w/one gig: ran great: no probs at all.  I did finally change it to Xubuntu to free up some memory and also quicker booting.  It boots in 35 seconds with its solid state HD.

---

### Post by psyclechick on 2012-06-19
> **PhantomTurtle said:**
> ......
 
Thanks :) - going to wait until I have done the initial iPad sync (if I still get one...so far since picking up my Android phone I haven't really used any iOS only apps!!) then go full Ubuntu again as it will be easier - using iCloud is easy, but I have been a Mac and iOS user exclusively for the last 3-4 years now....
 
> **blackbird34 said:**
> You might need to dual boot that netbook if the iPad is non negotiable ;-)
 
Nah, just do as I said above, although I am considering my options as a few people have moved off iMessage to Kik since I picked up my Android handset lol
 
> **Autodave said:**
> .....
 
Thanks! Will give Unity a go definitely then. 
 
Thanks to everyone for the answers :D

---

