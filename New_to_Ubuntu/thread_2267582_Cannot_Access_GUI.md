---
title: "Cannot Access GUI"
date: 2015-03-02
forum: New to Ubuntu
---

### Post by daniel252 on 2015-03-02
Hi all,
I'm very new to Ubuntu (as to be expected) and I really could use some help. So before I get into the issue I'll tell you my exact specs. I am running an Asus n56vz laptop with an i7, GT650m 2gb, with a 1TB drive partitioned 3 ways (but I'll get into that in a moment). I'm running Ubuntu 14.04 LTS 64 bit along side windows 7 64 bit. I gave up 25gbs for ubuntu, just so I could mess around with it and the other two partitions are for windows. Now that I got that out of the way I can describe my issue. IU began running Ubuntu and everything worked fine I was learning some of the basics such as how to conduct sudo update commands and things of that nature. I began reading about this extension called GNOME eager to try anything i installed it. After installing a shell extension and rebooting my system my entire UI was gone, I have the lock screen and can get to tty1 though but beyond that I can do almost nothing. I can no longer preform downloads updates or most basic functions. they all come up with an error when retrieving from the site. I was unable to uninstall the GNOME shell but still am stuck with no UI or the ability to download anything. Any help would be greatly appreciated 
Thanks 
Dan


Also I'm pretty familiar with the terminology from rooting and roming android but I'm not too advanced so if i sound like an idiot that's why, again thanks.

---

### Post by pfeiffep on 2015-03-02
If you reboot do you first see the Grub menu? if so try recovery

---

### Post by daniel252 on 2015-03-02
yeah I do see the Grub menu and can still boot into the log in screen but after I type my password in I get nothing just a blank wallpaper. Thanks for the quick response

---

### Post by Bucky Ball on 2015-03-03
Welcome. When you get to the login screen hit the Sessions menu. Can you choose Unity (Ubuntu session)? That should get you back to the original desktop and hopefully a workable system.

---

### Post by daniel252 on 2015-03-03
No all I can see is the guest session login and the one for my name (both lead me to the same outcome). I also can see the top bar there (I believe that's part of the gui)


*edit* I just noticed my initial little loading screen pre log in is still the gnome one (the foot logo). Sorry I know this all must sound very dumb I see these types of questions on XDA and I always feel bad for them.

---

### Post by Bucky Ball on 2015-03-03
I don't use Ubuntu, but on the login screen somewhere (maybe on the top tool bar?) there is a drop-down menu 'Sessions', or something like it. NOT guest session or anything like that on the actual login GUI. Have a further look round. 

* Update: where you have the GUI to login with your user and at the bottom 'Guest session', there is a Ubuntu logo in the top righthand corner of the actual login Window. Click that. That is where the desktop session selection is made.

---

### Post by daniel252 on 2015-03-03
sadly that isnt their either I read some previous posts and that seemed to be the answer but not with mine.

---

### Post by mastablasta on 2015-03-04
> **daniel252 said:**
> . I gave up 25gbs for ubuntu, just so I could mess around with it... .
easiest solution - reinstall (can choose to reformat or just rewrite the partition).

note that sudo command or as soon as you type in admin password it means you will do some major changes to the system. if you are unsure do not type it ;) as a side note you might have installed the wrong package as gnome desktop should work just fine. well at least other deskotps and WM's do (KDE, LXDE, XFCE... about 18 of them). I am not so certain about gnome as Unity is basically a modified Gnome.

next time you want to mess around safely and with that kind of machine do this instead: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
you can take a snapshot and then mess up the virtual system totally, then all you need to do is restore the snapshot (takes a couple of seconds, maybe a minute) and you are back when you started.

---

### Post by daniel252 on 2015-03-04
thanks man, that's what I was thinking but if I reformat the partition will it break my windows boot manager? I read that online somewhere and was hesitant to do it because I'm at college and don't have my windows repair disk.

---

### Post by mastablasta on 2015-03-04
it shouldn't, but i never did it myself to be able to confirm this first hand.

then try to add a light desktop - for example since you already have gnome and it's stuff maybe XFCE, then maybe reinstall gdm manager or is it light-dm by default (if it will be necessary). its the one that at the start that loads different desktops.

at leats all this should get you to a working desktop where you could maybe more easily see what went wrong. you don't have to add the whole desktop just the basics.

to install xfce:

```
sudo apt-get install xfce4
```

to install light-dm it is preety similar:
```
sudo apt-get install lightdm
```

if you want gdm instead then:
```
sudo apt-get install gdm

sudo dpkg-reconfigure gdm
```

and select gdm from the menu that appears.

otherwise we can't see what is on your screen and what is not working. if you have some smartphone or camera you could make some screens or video.

here is how the os loads (basically):
BIOS->Grub->OS  --  the OS loads drivers and daemons and stuff it needs or might need, then it loads the desktop manager (lightdm in Ubutnu's case). you then select the desktop you plan to use and type in your password to login. then it loads the desktop things - windows manager, various desktop stuff (e.g. network manager, clipboard manager, menues...) and then finally the desktop appears where you load your programs. 

you problem is that you messed up some files that are supposed to load in order for the desktop manager to load the desktop. and while you were installing you might have messed up the desktop manager itself since the suggestions by other users did not work. so one way to repair it would be to reinstall the *ubuntu-desktop* metapackage, so you could try that first. and temoporary solution that would make it easier for you to asses the damage would be to install another desktop and reinstall the desktop manager ort just use another one. by the way, there are a few even lighter ones, but I think gdm should be safest with gnome and xfce.

you can also wait - perhaps some expert has a better solution.

---

### Post by Bucky Ball on 2015-03-04
I agree with mastablasta, with the caveat that you install lightdm or gdm and try that first prior to installing a desktop environment. If you are missing a 'Sessions' menu, and if you can fix that problem with a dm install then you should be able to select whatever session you like and all should be right with the world. ;)

I think Gnome uses gdm and that mave have screwed things up, so perhaps reinstall lightdm - which is what you would have been using with Ubuntu previous to the Gnome install - reboot, and see what happens. Look for that 'Sessions' list in Lightdm login, if you get there.

---

