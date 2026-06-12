---
title: "ATI driver caused grafix problem"
date: 2014-03-16
forum: New to Ubuntu
---

### Post by mikee2 on 2014-03-16
I am a brand new user to UBUNTU, and dont know much about the system. I am running 12.04. Recently I installed the FGLRX driver and the fglrx-amdcccle driver for my Raedeon 9200 ATI card, and upon reboot got some error GUI saying i was in low graffixs mode. I could not resolve anything from the given choices in the menuy that was presented, and now can not even login. I am at a black screen that has my user root with TTYL listed which asks me for my login and PW, but upon entereing them it does not work. I dont know how to resolve this or even access UBUNTU now. I did try booting into recovery mode and then deleted teh FGLRX drivers via dpkg --purge fglrx-* but I am still getting the errors. Even now with those removed, I am still getting the low graffics erros and cane lof into my machine. Any help would be appreciated.

---

### Post by Yellow Pasque on 2014-03-16
Bad idea. fglrx/Catalyst dropped support for the Radeon 9200 several years ago.

Make sure you run the 7 commands presented here: [http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide#Removing_Catalyst.2Ffglrx)

> I am at a black screen that has my user root with TTYL listed which asks me for my login and PW
Ubuntu does not have a root user enabled by default. You use you regular username and password.

---

### Post by mikee2 on 2014-03-16
I am not sure if this is becuase i alraedy uninstalled some of this stuff, but i am getting errors like E: Command line option 'p' [for purge] is not known. I think the main drive is read only rightnow, need to mount and make RW witht he command mount -o remount,rw. Sitll there seems to be files that are lingering becuase I cant log into mymachine in TTYL. the graphics error is still here!

---

### Post by mikee2 on 2014-03-16
I am a new user to UBUNTU 12.04.. Recently I installed the FGLRX driver and the  fglrx-amdcccle  driver for my Raedeon 9200 ATI card,  and upon reboot  got some error GUI  saying i was in low graffixs mode. I could not  resolve anything from  the given choices in the menu that was  presented, and now can not even login. WHen i escape that it I am at a black page with TTYL that asks me for LOGIN and PASWWORD, and no matter what i type everything comes up INVALID. 

 I was able to boot into recovery mode and remove some packages (i think) with 
```
sudo apt-get remove --purge fglrx*
sudo sh /usr/share/ati/fglrx-uninstall.sh 
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*
```
I thought that after this I would be fine, but after a reboot, the graffix error came up again and I am now getting even more errors in the recovery console. I was given a link to this site for more instructions:

[FONT=century gothic]***[http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide#Removing_Catalyst.2Ffglrx)***[/FONT]

the first command i try get this error: 

"command line option p [from purge] is not known". 

after that I tired this command: 
sudo apt-get install xserver-xorg-video-atiI got these errors:
```

W: Not using locking for read only lock file /var/lib/dpkg/lock
E: Unable to write to /var/cache/apt/
```

I get similar errors when attempting to execute the other commands that follow. I do not know if these errors are attributable to the fact that I already ran some removal commands before hand.. At this point I am completely lost and do not know how to rescue my machine. HOw do I see what is installed and how do i make sure i completely remove it? I just want the machine to work the way it was before i installed FGLRX

---

### Post by slooksterpsv on 2014-03-16
To get back into a stable graphics environment try this (may not give all color depth available) - this will need to be done in a terminal with no windowing system on display 0 (so if X is running switch to a tty and kill it):

sudo Xorg -configure
sudo mv ./xorg.conf.new /etc/X11/xorg.conf

Restart

---

### Post by mikee2 on 2014-03-16
after typing that command i get the error message:

Fatal server error:
Could not create
 lock file in /tmp/.tx0-lock

?

---

### Post by tgalati4 on 2014-03-16
Remove the lock file:

```
sudo rm /tmp/.tx0-lock
```

Then restart.

I was under the impression that the fglrx driver supported Radeon 9600 and later cards.  I believe the 9200 is slightly earlier card and may not be supported by the proprietary driver.

---

### Post by mikee2 on 2014-03-16
thnak you for your reply but the error message now is no such directory?! it seems like this is VERY complicated jsut to remove a driver and get my computer working agian.

---

### Post by QIII on 2014-03-16
Hello!

ATI dropped Linux support for that card a loooong time ago.  Probably 2008-ish.  The difficulty you are having is due to ATI's decision.

Now they have dropped Linux support for anything earlier than HD 5000 cards.

You should uninstall whatever may have installed of the fglrx driver and use the default open source radeon driver that comes with the default installation of Ubuntu.

If you get the lock sorted out, 

```
sudo apt-get install --reinstall xserver-xorg-video-ati libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core mesa-utils
```

Best wishes!

---

### Post by mikee2 on 2014-03-16
Good to know! maybe you could read the rest of my post and help me figure out how to uninstall if i cant access anything?

---

### Post by QIII on 2014-03-16
I did, and I made changes.  And if you will be civil, I'll continue to help.

Also, please don't start multiple threads.  I have merged two.

---

### Post by sandyd on 2014-03-16
Please do the following

1. Reboot
2. Hit the arrow down key a few times after bios appears
3. Select 'additional options for ubuntu', or something similar
4. Choose the one ending in 'recovery mode' and press enter
5. Choose 'root'
6. 
```

mount -o remount,rw /
rm /tmp/.tx0-lock
```
7. Use instructions at [http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide#Removing_Catalyst.2Ffglrx)
8. Reboot

---

### Post by mikee2 on 2014-03-17
I was able to remove the lock somehow and remove all the files that were causing the bug. After doing this

sudo apt-get install xserver-xorg-video-ati mesa-utils

now my screen goes blue (no signal) and i can not see the log in screen.

---

### Post by mikee2 on 2014-03-17
ok so I got around the file lock my doing sudo **mount -o remount /dev/sda1**--------then i proceeded to uninstall all the drivers that were causing the system to go into low graphics mode by going to [http://wiki.cchtml.com/index.php/Ubu...talyst.2Ffglrx]("http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide#Removing_Catalyst.2Ffglrx") and follwoing the steps. and then scuccesfully boot back into the system. Thinking I was safe I proceed to take the advice of the post above and execute the suggested command 
sudo apt-get install --reinstall xserver-xorg-video-ati libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core mesa-utils

the result is now my system will boot fine until it gets to the login screen and my monitor turns off saying NO SIGNAL. 
I have tried tore-remove everything again, with no success.

---

### Post by slooksterpsv on 2014-03-17
Try this:
```

ps aux | grep lightdm | awk '{ print $2 }' > ./tokill && for f in `cat tokill`; do sudo kill $f; done && sudo Xorg -configure && sudo mv ./xorg.conf.new /etc/X11/xorg.conf

```
The ` is the tilde key not the ' apostrophe key. (Tilde is to the left of #1 on a US keyboard).

What this does is it takes your processes (ps aux) searches for lightdm (grep lightdm) prints the process number (awk) puts it in a file called to kill (> ./tokill) waits till that's done ( && ) gets every process from the tokill file (for f in ...); kills those processes (sudo kill) creates the configuration file (Xorg -configure) and moves it to the properlocation (sudo mv ./...)

---

### Post by QIII on 2014-03-17
Just to pop in quickly, even though I shouldn't...

xorg.conf is no longer needed and is not used by Ubuntu any longer by default.  If the failed fglrx install created one (it shouldn't have, since it failed, but proprietary drivers create on when installed) then simply renaming it to something like /etc/X11/xorg.conf.bak should be sufficient.  Ubuntu will run very happily with no xorg.conf.

After running the instructions indicated by sandyd and temujin, there was no need to go back to my post and run the commands -- which are just a rehash of what is in cchtml anyway with the addition of mesa-utils, which provides some diagnostic tools.

Edit:  Please understand, mikee2, that I am not disagreeing with slooksterpsv, but only adding a bit of info.  What sloosterpsv has said will work as advertised.  It's just a tidbit of information I know -- and none of us knows everything.  This is a team effort.

---

### Post by slooksterpsv on 2014-03-17
QIII is right and thank you for mentioning that. Myself, I had to use Xorg -configure to get an xorg file to get into the GUI area to even do the installation. Now I never did try nomodeset which may have worked. Overall QIII is correct.

---

### Post by Yellow Pasque on 2014-03-17
> **QIII said:**
> The difficulty you are having is due to ATI's decision.

Don't pin blame on ATI. About the only thing they are to blame for is not giving a more pronounced warning to those Linux users downloading legacy drivers from their site that those drivers will not work with later distro/X/kernel versions (but that's not even the case here).

If someone blindly installs a driver that doesn't support his/her card, that person is to blame for not doing his/her homework. As someone who actually used fglrx/Catalyst on an X300 back in 2007, I can tell you that the open source ati driver is leaps and bounds better nowadays.

---

