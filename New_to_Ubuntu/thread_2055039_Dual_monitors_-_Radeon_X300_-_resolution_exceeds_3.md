---
title: "Dual monitors - Radeon X300 - resolution exceeds 3d limit"
date: 2012-09-08
forum: New to Ubuntu
---

### Post by Martwana on 2012-09-08
hi there me again, with the same problem haha.

got ubuntu 12.04.01 installed fine, all my hardware is working as it should except the graphics card. 

it currently has my 2 dell 17 inch monitors mirrored, but i want them extended, like in windows 7. 

when i go to displays, and untick mirrored displays and set the correct resolutions, i get this message:

GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._gnome_2drr_2derror_2dquark.Code3: Requested size (2560, 1024) exceeds 3D hardware limit (2048, 2048).
You must either rearrange the displays, so that they fit within a (2048, 2048) square,
or select the Ubuntu 2D session at login.

I have looked in additional drivers, but that window shows nothing. 

lspci -nn | grep VGA :

01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI RV370 5B60 [Radeon X300 (PCIE)] [1002:5b60]

xrandr -q :

Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 4096 x 4096
DVI-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
DVI-1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  


Hope that helps someone help me. AFAIK its just the builtin drivers running for the gfx card. after trying to play with xorg.conf, i had to reinstall ubuntu, so everythings stock just now.

Anyone have any ideas?

---

### Post by mips on 2012-09-08
Don't have ati but how about first dropping the resolution & applying it before unticking the mirror box and then change them afterwards again,

---

### Post by Martwana on 2012-09-08
> **mips said:**
> Don't have ati but how about first dropping the resolution & applying it before unticking the mirror box and then change them afterwards again,

I can reduce the resolution to 800x600, apply it, untick the mirror box, and it runs at 800x600, when i move up to 1280x1080 it either throws the same error i mentioned, or rotates one display 90 degrees and throws a very similar error but with a different resolution.

I really want to get this sorted, I was really excited about the move to linux lol but i cant use it for web design on a single screen.

Any other ideas? I appreciate them all, hopefully something will work, someone must of had the same problem at one point :|

---

### Post by Martwana on 2012-09-08
> **mips said:**
> Don't have ati but how about first dropping the resolution & applying it before unticking the mirror box and then change them afterwards again,

I can reduce the resolution to 800x600, apply it, untick the mirror box, and it runs at 800x600, when i move up to 1280x1080 it either throws the same error i mentioned, or rotates one display 90 degrees and throws a very similar error but with a different resolution.

I really want to get this sorted, I was really excited about the move to linux lol but i cant use it for web design on a single screen.

Any other ideas? I appreciate them all, hopefully something will work, someone must of had the same problem at one point :|

---

### Post by mips on 2012-09-08
1. Are you using LCD displays or old CRT displays?
2. Can you run these dual resolutions in windows?

---

### Post by mips on 2012-09-08
Ignore the above post. Looks like you have to change the maximum size for the virtual screen in your /etc/X11/xorg.conf file.

[http://ubuntuforums.org/showthread.php?t=1748037](http://ubuntuforums.org/showthread.php?t=1748037)
[http://askubuntu.com/questions/71457/how-can-i-set-up-dual-monitor-display-with-ati-driver](http://askubuntu.com/questions/71457/how-can-i-set-up-dual-monitor-display-with-ati-driver)

So change yours to read, (just add the bolded line to whatever is already in yours):

Section "Screen"
Identifier "Default Screen"
Device "Default Video Device"
SubSection "Display"
**Virtual 2560 1024**
EndSubSection
EndSection

---

### Post by Martwana on 2012-09-08
> **mips said:**
> 1. Are you using LCD displays or old CRT displays?
2. Can you run these dual resolutions in windows?

LCD's both exact same models. On windows 7 they run extended at 1280x1080 in harmony. The card itself is capable of 1920x1080 dual monitors, which I have tried and tested before.

So can't understand why it won't work on Ubuntu.

I read something about Xorg.conf, but I personally don't know anything about it, could someone maybe tell me how to do that?

---

### Post by mips on 2012-09-08
See post#6

Maybe post the contents of your /etc/X11/xorg.conf file here.

---

### Post by Martwana on 2012-09-08
> **mips said:**
> See post#6

Maybe post the contents of your /etc/X11/xorg.conf file here.

I also tried that earlier, it stopped Ubuntu booting. Can I enter multiple resolutions in xorg.conf?

---

### Post by mips on 2012-09-08
post your xorg.conf here

---

### Post by Martwana on 2012-09-08
> **mips said:**
> post your xorg.conf here

Sorry, I do not have one, this is a clean install, it doesn't have one

---

### Post by mips on 2012-09-08
Have you tried using the arandr utility?

I can't really help any further than this. I have a old AGP Radeon 9600 SE lying somewhere that I could try sticking into a old pc and testing with lubuntu 12.04 but that will take some time.

Hopefully someone else comes along with a answer in the mean time.

---

### Post by Martwana on 2012-09-08
> **mips said:**
> Have you tried using the arandr utility?

I can't really help any further than this. I have a old AGP Radeon 9600 SE lying somewhere that I could try sticking into a old pc and testing with lubuntu 12.04 but that will take some time.

Hopefully someone else comes along with a answer in the mean time.

I have not, I'm a complete NOOB with linux.

What can i do with that command?

---

### Post by mips on 2012-09-08
> **Martwana said:**
> I have not, I'm a complete NOOB with linux.

What can i do with that command?

it's a gui front end for xrandr used for setting up dual displays. Not saying it will work but maybe worth a shot.

sudo apt-get install arandr

I'm off to go watch some mindless tv now, I'll check back here later and maybe setup that pc tomorrow for testing.

---

### Post by Martwana on 2012-09-08
> **mips said:**
> it's a gui front end for xrandr used for setting up dual displays. Not saying it will work but maybe worth a shot.

sudo apt-get install arandr

I'm off to go watch some mindless tv now, I'll check back here later and maybe setup that pc tomorrow for testing.

arandr worked, fiddled with the display settings and arandr itself and thats me. for now lol, hopefully that works.

THANK YOU!!

---

### Post by mips on 2012-09-08
> **Martwana said:**
> arandr worked, fiddled with the display settings and arandr itself and thats me. for now lol, hopefully that works.

THANK YOU!!

Great! Now I don't have to go setup that old pc :biggrin:

---

### Post by Martwana on 2012-09-08
> **mips said:**
> Great! Now I don't have to go setup that old pc :biggrin:

Yep, it does work! but with issues

Every time i reboot, it rotates one display, and when they are aligned properly, the display has lots of lag, like when draggin windows and you tile your screen with it.

Any ideas on how to prevent that?

---

### Post by mips on 2012-09-08
Did you save the settings?

---

### Post by Martwana on 2012-09-08
> **mips said:**
> Did you save the settings?

I did, yes, it resolved itself after another reboot, but it still shows lots of lag, yet it did not show any when using a single monitor or dual screens in Win 7

---

### Post by mips on 2012-09-08
I have not used arandr (xrandr) so not familiar with it but from what I've read things seem to be laggy.

You can also try xinerama.

I still however think we should look into changing the virtual display size in the xorg.conf file. looks like I will have to fire up that pc after all.

---

### Post by Martwana on 2012-09-08
> **mips said:**
> I have not used arandr (xrandr) so not familiar with it but from what I've read things seem to be laggy.

You can also try xinerama.

I still however think we should look into changing the virtual display size in the xorg.conf file. looks like I will have to fire up that pc after all.

I'll try that one just now, but I agree with you, I seen a lot of people speaking about xorg.conf, but my computer doesnt seem to have one. 

I know this is an Ubuntu forum, and I want to stick with it, but could you reccommend another distro that is as sleek secure and fast as Ubuntu?

I'll only move if I can't sort this out. Cheers for helping, really appreciate it!!

---

### Post by mips on 2012-09-09
I'm about to get that PC with the radeon9600se ready for a lubuntu 12.04 install. Will get back to you a bit later.

EDIT: Unfortunately I don't have any RAM that works in this old PC, I just realised after struggling that the one working dimm I had for it I gave away some time ago.

Have you tried using the proprietary ATI/AMD drivers for it with catalyst control centre?
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Martwana on 2012-09-09
> **mips said:**
> I'm about to get that PC with the radeon9600se ready for a lubuntu 12.04 install. Will get back to you a bit later.

EDIT: Unfortunately I don't have any RAM that works in this old PC, I just realised after struggling that the one working dimm I had for it I gave away some time ago.

Have you tried using the proprietary ATI/AMD drivers for it with catalyst control centre?
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Ahh unfortunate. I have tried them, they install fine, amdcccle installs too, but when I open it, it says no supported adapters found. It's a Radeon x300, and it stated it works with the ATI drivers. 

I'll try again just now just to be sure.
----------------------------------------------------------------------------------------------------------------------

SO yea, just tried the proprietary drives using the guide you linked, and all goes fine untill step 5, 
sudo amdconfig --initial
AND
sudo aticonfig --initial

RETURN

amdconfig: No supported adapters detected
AND
aticonfig: No supported adapters detected

---

### Post by mips on 2012-09-09
> **Martwana said:**
> Ahh unfortunate. I have tried them, they install fine, amdcccle installs too, but when I open it, it says no supported adapters found. It's a Radeon x300, and it stated it works with the ATI drivers.

Apologies, I just read [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx) again and the X300 has been moved to 'legacy' and is not supported in the newer drivers found in the repos. 9.3 seems to be the last version for X300.

So purge those drivers [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:_Need_to_purge_-fglrx](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:_Need_to_purge_-fglrx)

Latest xorg & openource ati/radeon drivers are here [https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=precise](https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=precise)

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://wiki.archlinux.org/index.php/ATI](https://wiki.archlinux.org/index.php/ATI) some useful hints & tips in here.

---

### Post by Martwana on 2012-09-09
> **mips said:**
> Apologies, I just read [http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Legacy/Pages/radeon_linux.aspx) again and the X300 has been moved to 'legacy' and is not supported in the newer drivers found in the repos. 9.3 seems to be the last version for X300.

So purge those drivers [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:_Need_to_purge_-fglrx](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection?action=show&redirect=X%2FTroubleshooting%2FFglrxInteferesWithRadeonDriver#Problem:_Need_to_purge_-fglrx)

Latest xorg & openource ati/radeon drivers are here [https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=precise](https://launchpad.net/~xorg-edgers/+archive/ppa?field.series_filter=precise)

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://wiki.archlinux.org/index.php/ATI](https://wiki.archlinux.org/index.php/ATI) some useful hints & tips in here.

Ahh, brilliant, that should solve my problems! hopefully,

Could you just list the order to do things for me, with a little more detail. Ive reinstalled ubuntu about 12 times trying to sort this, so would rather not have to do that again. Beleive it or not im actually really good with computers, but im totally new to Linuz distro's.

If you could do that for me, i would be very gratefull.

Martin

---

### Post by mips on 2012-09-09
```

sudo apt-get remove --purge xorg-driver-fglrx fglrx*
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri fglrx-modaliases
sudo dpkg-reconfigure xserver-xorg
```

```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install xserver-xorg-core
```

REBOOT

---

### Post by Martwana on 2012-09-09
> **mips said:**
> ```

sudo apt-get remove --purge xorg-driver-fglrx fglrx*
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri fglrx-modaliases
sudo dpkg-reconfigure xserver-xorg
``````
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install xserver-xorg-core
```REBOOT

Thanks, will try that within the hour, will let you know how I get on.

Thanks again

---

### Post by Martwana on 2012-09-09
Tried, and still no joy, before trying i had just installed  Kubuntu, and it ran dual monitors fine straight out the box. Isn't  Kubuntu based on Ubuntu? 

When i got your message, i reinstalled ubuntu, then executed all those  lines of code, and it still shows the same message when trying to swap  from mirrored displays. 

I was tempted to stay with Kubuntu haha, but i like the UI of Ubuntu better. 

Thought i had it sorted there :sad:

---

### Post by mips on 2012-09-09
They are all based on the same platform but with their own unique differences/tweaks for the desktop.

Try joining IRC channle #ubuntu on the frenode server and ask for assistance with your radeon there.

I just remembered I have a old nx9910 laptop wit ATI R200 here which I'm gonna try get lubuntu onto. Lubuntu & Unity however is different but I'm gonna see if I can get that xorg settings going.

---

### Post by mips on 2012-09-09
You can also try this so long [http://www.tsolak.com/?p=130](http://www.tsolak.com/?p=130)

---

### Post by Martwana on 2012-09-09
I'VE SORTED IT FINALLY.

It was right infront of me the whole time, the error message actually told me what to do!

It said that the resolution was too big for the virtual desktop, to set the correct resolution or select 2d at login.

So, after your last post, I installed Kubuntu, SUSE, MINT, Fedora, Studio, and Kubuntu again, which I was about to settle for. 
I then installed Ubuntu desktop over that, so when I booted up, it technically booted kubuntu then unity, i thought that would help my problem, but due to me forgetting to tick the box when installing kubuntu to log in automatically, I was about to log in when i noticed the little button to change the desktop experiance.

Upon clicking that, I seen Ubuntu 2D, which rang a little bell haha. When I clicked it it loaded the 2d unity and mirrored the displays, my face dropped then. So I thought id give it one last go, clicked into displays, untucked the mirror box and hit apply, and VOILA!!

It bloody worked, all this time, it was that simple. I mean how much do I loose out on with it not being 3d.im going to write in code 80% of the time haha so i won't see anything special.

Problem solved, not need for any command lines at all.

Thought I'd share it!

Thanks mips, although I sorted it myself, your have been a great help. Praise to you. In my Scottish accent, cheers buddie!

---

### Post by mips on 2012-09-10
Glad you came right. Keep in mind that future versions (12.10+) of Ubuntu won't have Unity 2D from what I've read.

---

### Post by Martwana on 2012-09-10
Ahh, thats good to know. Maybe I'll stick with the LTS edition until I decide to get a new Graphics Card. WHat I've got does me just now, so no need to change.

---

### Post by AlistairH on 2012-09-26
Very interesting.

I've got exactly the same card driving two 23" Samsung monitors perfectly well in Ubuntu 10.04 using the open source driver - so there's no xorg.conf file.

This past weekend, I tried upgrading to Xbuntu 12.04 and monitors would not run in anything other than mirrored mode. Any attempt to extend the desktop across the monitors resulted in a complete system freeze and only a hard reboot would recover the situation.

I subsequently installed and tested the 12.04 based distributions of Ubuntu, Kunbuntu, Linux Mint MATE and Bodhi Linux. All crashed my system in some way.

Ubunutu - got the error message regarding 2D. Rebooted and went into a 2D session resulted in distorted screens and system freeze.

Kubuntu - Switching on mirroring casues one blank screen and a system freeze.

Linux Mint - Screen distortions and system freeze.

Bodhi - Results in a 'black screen of death' with loads of unintelligible error codes.

Only  Xubuntu came close in that it extended the desktop without distortions but caused a complete system freeze.

In all cases, I was using the open source driver. Given that dual monitors worked in version 10.04, I'm begining to wonder if the current open source driver is not compatible with this card - I'll be the first to admit it's a bit old hat and under powered. Having said that, I have no requirement for a high powered graphics card other than the ability to extend my desktop across two monitors.

So, I've got two questions:
1. Has anyone managed to get an ATI Radeon X300 working with an extended desktop across two monitors under 12.04 based distros?
2. Those of you who have a successful dual monitor setup under 12.04 based distro, what graphics card are using/would recommend?

---

### Post by sacaudill on 2012-09-28
I have the exact same issue with the exact same card... I'm curious about the 2D option, but what all would I lose? Would I still be able to play games and have compiz affects? This is such a stupid issue! I thought nVidia was bad for linux support, but this card has been around forever, I would have thought it would have been supported better out of the box.

---

