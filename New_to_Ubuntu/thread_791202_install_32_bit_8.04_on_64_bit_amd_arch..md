---
title: "install 32 bit 8.04 on 64 bit amd arch."
date: 2008-05-12
forum: New to Ubuntu
---

### Post by infoanalysis on 2008-05-12
After finally getting the 64 bit 8.04 to boot up, I come to learn that it is loaded with media problems. 

SO now after all that I am going to attempt to build a 32 bit kernel running on 64 bit arch. The standard 32 bit iso download failed to boot up after several attempts I resorted to the 64 bit version which worked ok.  How can I get 32 bit to run on a 64 bit platform? IS there a choice in the 64 bit cd boot that permits me to partiton the drive for 32 bit and run the 64 amd as 32 bit?

---

### Post by tjwoosta on 2008-05-12
i have had both 32 bit and 64 bit installed before on my computer (usually the 32bit cd should boot)

but i have been using hte 64bit version lately

what media problems have you been having?  i seem to have none

---

### Post by nathansoz on 2008-05-12
I agree with tjwoosta, the 32 bit cd should boot. Try buring the cd image again at a lower speed. Or perhaps you have a corrupt cd image. I know that on one of my computers cd burners, quality of the burn degrades quickly as speed increases. One of my ubuntu burns at high speeds refused to boot. When I burned it around the 12x area however, it worked just fine.

---

### Post by sdennie on 2008-05-12
I don't think you will be able to drop in a 32bit kernel on a 64bit install.

If you can't sort out your media problems on 64bit, you may want to re-download the 32bit iso and make sure that the download is correct (use the torrent download).  It's possible that your first 32bit download was corrupt and that's why it didn't install.

---

### Post by Inxsible on 2008-05-12
what speed did you burn the 32 bit version at?

Recommended speeds are 4X or less, although I have burnt at 24X and it has still worked. also did you download it off of ubuntu.com or some other mirror?

---

### Post by infoanalysis on 2008-05-13
I can not install flashplayer 9

---

### Post by Xiong Chiamiov on 2008-05-13
Using a 32-bit kernel on 64-bit install, I do not think will work.

I have an Athlon X2 (64-bit), but I've never used a 64-bit OS because I didn't want to deal with getting things working.  You just won't have the advantage of having a 64-bit processor.

---

### Post by infoanalysis on 2008-05-13
I reburned a cd i386.iso at 4x, the same thing happened: mouse pointer works, bronze screen with a 3/8 white line at the top and the botton- but no usuable desktop with bird and mozilla icon - just a blank screen. It seems like it is having video card problems? I am running a ge force 6200 NVIDIA. The install did work fine with 64x86 remember- it was just that it is too burdensome to get the media flashplayer up and running, but the 64x86 install recognizes the card. What can I do now?

---

### Post by Xiong Chiamiov on 2008-05-13
What about if you don't use the proprietary drivers?

Press alt+f2 when booting, then try this:
```

sudo dpkg-reconfigure -phigh xserver-xorg
startx

```

This is assuming that you've installed it, not running off the CD.  If you are, have you tried the safe graphics option?

---

### Post by dstin1 on 2008-05-13
> **infoanalysis said:**
> I can not install flashplayer 9

Here is a guide for flash and 64 bit.  I'm not sure how it works as I have a 32 bit machine.

[http://ubuntuforums.org/showthread.php?p=4822974#post4822974]("http://ubuntuforums.org/showthread.php?p=4822974#post4822974")

---

### Post by tjwoosta on 2008-05-13
> I can not install flashplayer 9

i have flashplugin-nonfree with 64bit and it works great

---

### Post by infoanalysis on 2008-05-13
some how I got to the commandline, it asked for my login and password, then it gave me a terminal like prompt xxxx@xxxx $, I then put in the code sent to me. The screen came up this time with a black and white mesh instead but no icons or graphics. Still at A loss

---

### Post by infoanalysis on 2008-05-13
I installed the nsXXXXXwrapper but that did not work - but now Iam back to32 bits and having trouble getting the desktop to comeup anyway

---

### Post by infoanalysis on 2008-05-13
> **dstin1 said:**
> Here is a guide for flash and 64 bit.  I'm not sure how it works as I have a 32 bit machine.

[http://ubuntuforums.org/showthread.php?p=4822974#post4822974]("http://ubuntuforums.org/showthread.php?p=4822974#post4822974")
I tried that install and it still did not take, so I am back to 32 bit install- I really think as an ABT novice I should KIS and stay with 32 bits according what I have read on this board.

---

### Post by Enternald on 2008-05-13
You would better use 64-bit edition, but normally 32 bit boot cd should run. For me that hapenned once with orginal Cd. Fun thing is that cd started and stoped when ubuntu was nearly load. My processor is amd 64. And moreover it worked fine with vmware. So I thing that is somekind bugh

---

### Post by tjwoosta on 2008-05-13
> I tried that install and it still did not take, so I am back to 32 bit install- I really think as an ABT novice I should KIS and stay with 32 bits according what I have read on this board

i dont understand what the hell they are talking about removing nspluginwrapper (because i still have it and i have never done things they say to do, i simply installed flash and it works)

what i did to get flash9 working was much much simpler

first you have to remove all other flash players you may have installed
 so go to Synaptic and search for theese flash players and uncheck them if you see them (gnash , swfdec , and flashplugin-nonfree) then click apply to remove them

then in synaptic search for nspluginwrapper and put a check nexxt to it and hit apply (sinse they had you remove it)

next simply install the working flashplugin-nonfree for linux
```
sudo apt-get install flashplugin-nonfree
```

and flash shoud be working

i have no idea why they would tell you to use remove nspluginwrapper in the first place (or why they would have you make the symbolick links you made)  

from a clean install the only thing you would ever have to do to get flash working right from the start is this
```
sudo apt-get install flashplugin-nonfree
```

NOTHING ELSE    it works great with64bit

---

### Post by infoanalysis on 2008-05-13
ok, So I will go back to 64 bit install - how do you bring up synaptic?
I also had to put in all_generic_ide in the boot line to get the 64 install to work ( and then later in the menu.lst to makeit permanent)

---

### Post by tjwoosta on 2008-05-13
> ok, So I will go back to 64 bit install - how do you bring up synaptic?

System-Administration-Synaptic Package Manager

> I also had to put in all_generic_ide in the boot line to get the 64 install to work ( and then later in the menu.lst to makeit permanent)

??? i have no idea about that (ive never heard of such a thing, maybe this has something to do with why they told you remove the nspluginprapper ?)

all i know for sure is that to make flash work in 64 bit all i did was install flashplugin-nonfree like i showed you, and nothing else (it simply worked)

---

### Post by SunnyRabbiera on 2008-05-13
The thing is though its not impossible to run the 32bit kernel in a 64bit environment, I have seen it done many times...

---

### Post by infoanalysis on 2008-05-13
> **tjwoosta said:**
> System-Administration-Synaptic Package Manager



??? i have no idea about that (ive never heard of such a thing, maybe this has something to do with why they told you remove the nspluginprapper ?)

all i know for sure is that to make flash work in 64 bit all i did was install flashplugin-nonfree like i showed you, and nothing else (it simply worked)
free at last... at least for the short term from the opression of xp! Needless to say your help with the flash plugin did the trick. I can't say how grateful I am for your help after five days of pulling my hair out, I am on my way.

John

---

### Post by tjwoosta on 2008-05-14
glad to help :)

---

