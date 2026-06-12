---
title: "HOWTO: Improve NVidia Laptop Graphics Performance"
date: 2008-06-13
forum: Outdated Tutorials &amp; Tips
---

### Post by sdennie on 2008-06-13
**Overview**
NVidia laptop cards come with a feature called PowerMizer that dynamically underclocks the GPU when it's not being used much.  This is great for battery power but horrible for performance when using Desktop Effects (compiz).  Unfortunately, NVidia does not provide a way to configure PowerMizer on Linux however, it's not difficult to create a script that will give you maximum speed while on AC power and maximum power savings while on battery.

This HOWTO is aimed primarily at users of NVidia 8 and 9 series laptop graphics cards (though, it may be useful for 7 series users as well).  This HOWTO assumes you are running compiz and have already properly configured the NVidia proprietary drivers.  If you are not using compiz, this guide will not be useful for you.

**Implementation**
The first thing we will need is a utility called nvidia-settings.  If you've installed the NVidia drivers directly from the NVidia website or using envyng, you can skip this step:

```

sudo apt-get install nvidia-settings

```

The nvidia-settings has a unique property that, with essentially no CPU/GPU activity, when you ask the card to print all of its information, it causes the card to go to maximum power.  The nvidia card only drops a power level every 30 seconds so, we are going to take advantage these two facts to keep the card at maximum power if we are on AC power.

If you have no custom scripts, follow these instructions first:

```

mkdir -p ~/bin

```

Then, open up gedit and paste the following script:

```

#!/bin/bash

while true; do
    if on_ac_power; then
        nice /usr/bin/nvidia-settings -q all > /dev/null
    fi
    sleep 25;
done

```

Save the script as ~/bin/nvidia-power.sh.  Then, start a terminal and type the following:

```

chmod +x ~/bin/nvidia-power.sh
~/bin/nvidia-power.sh &
disown
exit

```

If you are on AC power, the card should now be locked at its maximum power but, if you are on battery power, you should see no difference at all (until you next plug your laptop in).

Next, we will need to add this script to run when you login.  On gnome, go to System->Preferences->Sessions, click Add.  Add a descriptive name for the startup program (maybe, "NVidia Power") and for Command use, "/home/your_username/bin/nvidia-power.sh" (replace your_username with your username).  Now the command should run whenever you login.

**Testing**
Testing is fairly straightforward.  Start a terminal and type:

```

nvidia-settings

```

Scroll down to the bottom of the window this command brings up and look on the left side for the PowerMizer option.  If your laptop is plugged in, you should see that your graphics card is running at full power.  Watch it for a minute (the time it takes for the card to normally drop to lowest power) and make sure it stays at the highest power level.  Now, unplug your laptop and wait for another minute.  After less than a minute, your card should drop down to minimum power (as long as you keep it idle).  Now, plug the cable back in and, in less than 30 seconds, the card should come back to full power and stay there.  

The one caveat of this approach is that it can take up to 25 seconds for the card to come back up to full power.  There are more complex ways to make the card instantly go to full power when plugged in but, on average, it will be at full power within 12 seconds so, it's probably more hassle than it's worth to use more complex methods.

Questions/Comments/Suggestions welcome.

---

### Post by markinf on 2008-06-17
Thanks =D
This script improved my card perfomance so much =D, now I'm 100% here =D

---

### Post by chocoboyz on 2008-06-18
Thank you for the helpful tutorial, i'll try it and give feedback soon.

---

### Post by steveneddy on 2008-06-23
Works great!

Thank you.

Great work..

:D


EDIT:

When I ran your script, most of the animations in Compiz-Fusion were blocky and ugly, not smooth and pretty.

The card ran well but crashed my setup.

I currently don't use this script.

---

### Post by sdennie on 2008-06-24
> **steveneddy said:**
> 
When I ran your script, most of the animations in Compiz-Fusion were blocky and ugly, not smooth and pretty.

The card ran well but crashed my setup.

I currently don't use this script.

What do you mean by "crashed my setup"?  Did the computer actually crash?

To fix the "blocky and ugly", try this:

```

sudo apt-get install compizconfig-settings-manager

```

Go to System->Preferences->Advanced Desktop Effects->General Options->Display Settings.  Uncheck "Detect Refresh Rate" and manually move the "Refresh Rate" slider from "50" to "60".  Optionally, you may also want to check "Sync to VBlank".

---

### Post by steveneddy on 2008-06-24
> **vor said:**
> What do you mean by "crashed my setup"?  Did the computer actually crash?

To fix the "blocky and ugly", try this:

```

sudo apt-get install compizconfig-settings-manager

```

Go to System->Preferences->Advanced Desktop Effects->General Options->Display Settings.  Uncheck "Detect Refresh Rate" and manually move the "Refresh Rate" slider from "50" to "60".  Optionally, you may also want to check "Sync to VBlank".

I had to totally reinstall Compiz for some reason. I thought it did look better with the card turned up, but for some reason I lost all of my settings and had to reinstall all of Compiz just to fix it.

weird.

---

### Post by sdennie on 2008-06-24
You had to re-install compiz or re-install your nvidia drivers?  There was an xserver-xorg-core update recently and, if you've manually installed the nvidia drivers, it probably clobbered a few of the files that compiz needs to function.  The script as posted above is fairly innocuous and doesn't change any existing files on the system whatsoever (with the exception of the users startup programs).

---

### Post by steveneddy on 2008-06-24
> **vor said:**
> You had to re-install compiz or re-install your nvidia drivers?  There was an xserver-xorg-core update recently and, if you've manually installed the nvidia drivers, it probably clobbered a few of the files that compiz needs to function.  The script as posted above is fairly innocuous and doesn't change any existing files on the system whatsoever (with the exception of the users startup programs).

Yeah - I know. nVidida drivers OK. compiz became odd after installing your script. Not blaming your script, but I occasionally open the nvidia-settings and when the card needs to be turned up, it does so automatically. When idling, it goes back to the lowest settings.

I think I'm happy with the stock model.

Cool script though!

---

### Post by subru77 on 2008-07-02
Is this in any way bad for the graphics card?

---

### Post by sdennie on 2008-07-02
> **subru77 said:**
> Is this in any way bad for the graphics card?

It will probably make the card run slightly hotter than it would with the default settings but, Windows users have had the ability to do this for years (or so I've heard) and I would imagine that if forcing the card to maximum power was in any way dangerous, NVidia would not make it an option on their Windows drivers.  In fact, they have stated that they are going to add a more formal way to control PowerMizer in an upcoming linux driver.  They didn't state when that would be though (so, it could be years).

---

### Post by subru77 on 2008-07-02
Thanks for the quick reply. I will go ahead and try !

Edit: Awesome --- I was so sad that the GUI was slow. This made my day. 

Thanks VOR (Y)

---

### Post by xcesarfrancox on 2008-08-09
I've been using your script since I got my Dell 1420n Laptop, but I've noticed there's an issue involving GPU's temperature under some NVidia Cards (Including mine)

I went to nvidia-settings and checked in the Thermal Monitor and it shows up 62°C with NVidia-Power script enabled

Is this normal? What's the top on the GPU's core's temperature? Which is the optimal temperature?

EDIT: After installing sensors-applet I can see both my CPU and GPU temperatures, and the icon of the GPU is showing red and full... I guess this is a bad thing...

---

### Post by sdennie on 2008-08-09
> **xcesarfrancox said:**
> I've been using your script since I got my Dell 1420n Laptop, but I've noticed there's an issue involving GPU's temperature under some NVidia Cards (Including mine)

I went to nvidia-settings and checked in the Thermal Monitor and it shows up 62°C with NVidia-Power script enabled

Is this normal? What's the top on the GPU's core's temperature? Which is the optimal temperature?

EDIT: After installing sensors-applet I can see both my CPU and GPU temperatures, and the icon of the GPU is showing red and full... I guess this is a bad thing...

Depending on the ambient temperature of the room, 62C is perfectly reasonable if you are using compiz.  The card is made to prevent itself from overheating and, in extreme cases (like over 100C), I believe that it will underclock itself to prevent damage.  To ease your worries, I recommending grabbing a 3D game, playing for a while and, keeping in mind that the card is meant to play games, note the difference in temperature.  The card will run incredibly hot but, still not hot enough to worry.

---

### Post by plamen_todoroff on 2008-08-10
I just tested your script and it's doing it's job absolutely perfect. I've read that Nvidia's 8 series had some problems with Powermizer working correctly, but waiting for nvidia to release a driver update that would fix this. Finally everything is working for me as it should. Thank you!

For all of you guys who notice how choppy some effects are till you repeat them several times (and you have nvidia series 8 card of course), this script is for you!

For all of you who need some temperature data: my card is Nvidia Geforce 8600M GT 512MB, and I'm running 169.12 driver from the repos. The card's temperature before the script was average 57 to 62 degrees. Afer installing the script and running Ubuntu for an hour the temperature is 67 degrees. I think this is perfectly normal. In Vista the default nvidia driver settings keep the card at max performance when on battery, and the temperature in Vista is constantly around 65-70 degrees. So you don't have to worry a bit about appling the script.

Thank you once again for this superb piece of code. My system feels so much snappier and responsive, the whole experience with Ubuntu has changed dramatically!

I don't know whether the following is in some way connected to the changes your script made, but now it seems that firefox loads pages quickly than before (or should I say just renders them quickly?).

Perfect!

---

### Post by sdennie on 2008-08-10
I'm glad it worked.  And, yes, it does make some operations in Firefox much faster (I mostly notice it while scrolling).

---

### Post by xcesarfrancox on 2008-08-11
> **vor said:**
> Depending on the ambient temperature of the room, 62C is perfectly reasonable if you are using compiz.  The card is made to prevent itself from overheating and, in extreme cases (like over 100C), I believe that it will underclock itself to prevent damage.  To ease your worries, I recommending grabbing a 3D game, playing for a while and, keeping in mind that the card is meant to play games, note the difference in temperature.  The card will run incredibly hot but, still not hot enough to worry.

So you're telling me that my card will not burn up unless it goes over 100ºC? I'd like to know from what temperature I should begin to worry

Thank you very much, this script is really great

---

### Post by sdennie on 2008-08-11
> **xcesarfrancox said:**
> So you're telling me that my card will not burn up unless it goes over 100ºC? I'd like to know from what temperature I should begin to worry


Well, 100ºC was really just an example.  The point is that at 62ºC, you still have a lot of temperature room before damage to your card becomes a possibility.  One thing that I find useful to keep my machine cool is to clean all the vents with compressed air at least once a month.  It makes a surprising difference in how cool the machine stays.

---

### Post by x001 on 2008-08-11
Haven't implemented the script yet but wanted to check the temperature with the default setting in nvidia-settings. It shows Core Temperature at 62C and the Slowdown Threshold is set to 110C. So I am assuming that it is ok to run the script and the GPU gets too hot it will auto slow down.

---

### Post by sdennie on 2008-08-11
> **x001 said:**
> Haven't implemented the script yet but wanted to check the temperature with the default setting in nvidia-settings. It shows Core Temperature at 62C and the Slowdown Threshold is set to 110C. So I am assuming that it is ok to run the script and the GPU gets too hot it will auto slow down.

That's correct.  If your laptop can use this script, you will probably notice a slightly increase in heat but, on the order of a few degrees and nothing that will push the card anywhere near the slowdown threshold.

---

### Post by x001 on 2008-08-11
Just implemented this script on my XPS1530 and it works very well, looking at the nvidia-settings Thermal Monitor the GPU core temperature is on avg of 66/67C while the PowerMizer Performance Level always displays level 2. Thank you for a great solution.

---

### Post by rlanham on 2008-09-03
Running this on my M4300 with a Quadro FX 360M and its working great.

---

### Post by The Noble on 2008-09-04
> **xcesarfrancox said:**
> So you're telling me that my card will not burn up unless it goes over 100ºC? I'd like to know from what temperature I should begin to worry

Thank you very much, this script is really great

GPUs are tested at very high temperatures. I know ATI cards are spec'd at 120* Celsius, so you should worry at 80* or so. My Nvidia 8400GS m is rated to 125* and runs at 94* in windows (I OC'd it by ~50%).  The 4 series from ATI is breaking the 70* barrier while idle, so you have nothing to worry about.

---

### Post by markinf on 2008-09-14
Guys it's running about 80-82 C IDLE, should I worry?

---

### Post by Buzzdee on 2008-09-24
My Nvidia 570M card has 3 levels, 

performance level 0
NV clock 169 MHz, Memory Clock 100 MHz

performance level 1
NV clock 275 MHz, Memory Clock 301 MHz

performance level 2
NV clock 475 MHz, Memory Clock 702 MHz

Now when running your script, it says 'performance mode: maximum performance' in the powermizer tab, but level 0 and 2 are greyed out, so I guess I'm on level 1. Is level 2 an overclocked mode, which isn't to be used normally, or is something not working?

Best regards, 

Bastian

---

### Post by Guspaz on 2008-09-25
Sweet monkey unicycles, this made a HUGE difference for me!

I've got an Inspiron 9400 (E1705 in the US) with a GeForce Go 7900gs (Kubuntu 8.04). I'm *not* running XGL/Compiz/etc.

Previously on battery, my system performance was absolutely horrible. Drawing a page in Firefox took 3-5 seconds instead of nearly instant on AC power. We're talking more than an order of magnitude of performance difference.

It seems the culprit was xorg; when the GPU was clocked down, whenever anything happened on-screen, the xorg process would max out one of my cores (Core 2 Duo 2.16GHz).

Running the nvidia-settings -q all within a while loop (removing the ac check), my GPU is forced to full, and I'm getting NORMAL performance! My laptop is usable on battery again.

Noting the increase in wattage reported by the battery gauge in the systray indicates that the power drain is actually roughly the same as with the GPU clocked down, probably due to the huge reduction in CPU load. There is possibly a ~2-3 watt increase in drain (I'm currently at 28w), which is almost inconsequential considering the performance increase. So this isn't really affecting my battery life.

For reference, min GPU speed is 100/100, and normal is 375/507.

Seriously, this is huge! Thanks a ton for figuring this out.

---

### Post by evergreen_p on 2008-09-29
awesome tutorial man! thanks

---

### Post by Jen5en on 2008-11-05
The script works flawlessly, however, the changes are undone when the system is rebooted. Is there a way to make the changes permanent?

---

### Post by Funnnny on 2008-11-05
Add nvidia-power.sh into starup (System->Preferences->Sessions) and each time you reboot it'll run again

---

### Post by AndrewZorn on 2008-11-05
After I did this and a bunch of other power savers, my laptop (M1330 with 8400gs and Intrepid 64) would start to do something strange.  After maybe 1min of being logged in, the taskbar wouldn't respond (the Applications, Places, System will light up but not expand), couldn't alt-tab, basically nothing except mouse movement.

I took the Nvidia script out of startup and I have not had it since.

EDIT okay, so it's not the cause.  Awesome.  I'll probably just clean install, I'm getting sick of screwing stuff up from playing around.

---

### Post by Jen5en on 2008-11-06
> **Funnnny said:**
> Add nvidia-power.sh into starup (System->Preferences->Sessions) and each time you reboot it'll run again

Hehe, I actually did this earlier and it didn't work. However, I found out that I shouldn't place it in the root directory. :D It's in my home folder now, and it works like a charm. Thanks a lot.

---

### Post by macabro22 on 2009-03-17
Is it possible to modify the script and have the GPU clocks at full speed even when on batteries?

I would like to have it that way.

---

### Post by sdennie on 2009-03-17
> **macabro22 said:**
> Is it possible to modify the script and have the GPU clocks at full speed even when on batteries?

I would like to have it that way.

Yes.  Just remove the the "if..." and "fi..." lines.  Then it will always be at full speed.  It will also drain your battery much, much faster.

---

### Post by abhiroopb on 2009-03-19
This script worked wonders! Just one concern. When I run it in my terminal I get the following error:

```

NVIDIA: could not open the device file /dev/nvidiactl (Permission denied).
NVIDIA: Direct rendering failed; attempting indirect rendering.

```

And this keeps repeating over and over again. However, the script itself seems to be functioning as it is kept at the highest level!

---

### Post by loomsen on 2009-03-19
Thats obv due to the restrictive permissions the nvidia driver ships with by default.

Add a Section to your xorg.conf to define access for other users than root.

```

Section "DRI"
   Group         "video"
   Mode           0660
EndSection

```

If you dont mit other users accessing you DRI(=direct rendering infrastructure) of your video device you may replace 0660 with 0666.

See link in my sig for more detailed explanation.

---

### Post by macabro22 on 2009-03-19
Nope, that didn't do. The clock is still slowing down as revealed by nvidia X-server settings.

---

### Post by abhiroopb on 2009-03-20
That worked...thanks!k

---

### Post by SketchyClown on 2009-03-20
Thank you for this. I have a Asus M50VM with the GeForce 9600M with 1GB of VRAM.

The first thing I noticed upon reboot was how fast the entire Gnome desktop & Compiz launched.

It was virtually instantaneous. Panel and all. Usually it would take a couple seconds to draw it all, now it just 'appears'. Very quick.

Graphics performance has definitely increased by a lot. Performance using Google Earth is very impressive. It was fast before, just because of the card, but now it renders even faster using maximum settings across the board.

Great little haxie indeed.

---

### Post by moutou on 2009-04-04
cool as ice!
lets try now the "HOWTO: XPS m1330 power savings" post :D

cheers!

---

### Post by dcstar on 2009-05-01
> **loomsen said:**
> Thats obv due to the restrictive permissions the nvidia driver ships with by default.

Add a Section to your xorg.conf to define access for other users than root.

```

Section "DRI"
   Group         "video"
   Mode           0660
EndSection

```

If you dont mit other users accessing you DRI(=direct rendering infrastructure) of your video device you may replace 0660 with 0666.

See link in my sig for more detailed explanation.

[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/370249](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-180/+bug/370249)

---

### Post by CoreyCavalera on 2009-05-06
Hi. I've got problem with this script, it's rise performance level when laptop plugged in, but when is unplugged, power source will stay et AC and performance level not bellow. How I can solve this? Sorry about my english.
(HP pavilion, nvidia geforce 8400M GS.) Thank you for help.

---

### Post by falen_pl on 2009-08-14
Hey,

First of all I wanted to thank you for this tip. I can honestly say it saved my sanity. I'm not exaggerating - the flickering was driving me crazy.It was like that Chinese water torture, I could never be at ease while using my laptop because the anticipation for the next flick was too great.

The bottom line is: your solution works flawlessly and the flickering is gone. Thanks again.

I've read some people here have concern about running their card at full speed. If my laptop wasn't 4 years old I would probably be too, but I've been using the fix for over a month and I've yet experience something worrying. Besides, as long as you're running you card within the official capabilities, why worry? If you tweaked it to run at, let's say, 110% then you would a legitimate reason to worry. Otherwise, it's cool. 

ps. I'm using GeForce G0 7600

---

### Post by alvin1472 on 2010-04-14
Hello there, 

The script is sound so good after I see its function.

I am a newbie to those staff things, I don't even know where and how to  key in the code..

Can anyone please show me some steps to do it?

Your help will appreciated..

---

### Post by Red_Steve on 2011-01-09
2 things

1st: Your card would get that hot anyway if using programs forcing it to run at that speed thus only the average temperature is raised.

2nd: It seems like the script starts multiple times for me if I log off and into the same user again.
I've put the script into .bin instead of bin (to get it hidden) and chmoded to the other location so my version of the terminal command would look like: 

```
chmod +x ~/.bin/nvidia-power.sh
~/.bin/nvidia-power.sh &
disown
exit
```

Or is it normal that there are multiple instances for this script?

I also run the script to improve desktop performance -> [http://www.webupd8.org/2010/11/script-to-automatically-apply-200-lines.html](http://www.webupd8.org/2010/11/script-to-automatically-apply-200-lines.html)

could it be related to this? I don't experience any issues I'm just confused to see several instances of this script in system diagnostics (each with a vastly different ID thus hinting to this script I run to improve desktop performance)

Maybe you could look into this and add a function to kill this script on log off?

Edit: a possible solution for anyone using gnome and GDM would be adding the following line before ```
exit 0
``` in /etc/gdm/PostSession/Default :
```
killall nvidia-power.sh && killall sleep
```

Every time you log out those two processes would be killed and correctly called again if logging back into this user.

---

### Post by LuisGMarine on 2011-05-03
I'm not sure if this script is now rendered useless since the new nvidia-settings allow you to choose between "Adaptive" and "Prefer Maximum Performance" under the PowerMizer.

I'm just curious so I'm not running this script for no purpose.  

For example without the script running.  Plugged in to AC "Prefer Maximum Performance" selected, full power from GPU.  Unplug AC, same thing.

When I set it to "Adaptive", AC plugged in, full power from GPU.  Unplug AC and it starts to drop down.  

Just wondering, either way this script did wonders for me back in the day.  I never got around to thanking you, so here it is, almost 3 years late =) :guitar:

---

### Post by sdennie on 2011-05-03
> **LuisGMarine said:**
> I'm not sure if this script is now rendered useless since the new nvidia-settings allow you to choose between "Adaptive" and "Prefer Maximum Performance" under the PowerMizer.


It's not very useful these days but, there is still scripting to be had.  You can use the following two commands to toggle the max performance vs. adaptive on and off:

Performance:
nvidia-settings -a [gpu:0]/GPUPowerMizerMode=1

Power save:
nvidia-settings -a [gpu:0]/GPUPowerMizerMode=0

For Natty, I've got this and various other power saving/performance options bundled into a panel indicator that lets you select performance mode or power savings mode with a little dropdown.  Maybe I'll retire this HOWTO (and my other laptop HOWTOs) and do a new, more relevant one.

---

### Post by Markino76 on 2011-06-10
Hi guys,
I'm new in ubuntu and I've got a problem with my netbook (Asus 1015PN) equipped with nvidia ION2:
I'm running Ubuntu 11.04 and I've installed the restricted drivers including the nvidia driver but when I choose in nvidia settings the option "Prefer Maximum Performance" the level goes in the 1 level not in the 2 level that seems to be the highest freq.
If I close the nvidia settings and reopen it I can see the level still in 1 option but the power mizer is now in Adaptive mode... any idea in order to use the maximum level (2) from my ION2?
The script in the first post will be nice for me?

P.S: I saw that in the official nvidia web site there is a new version of the driver for linux but ubuntu doesn't install me the last version... why?

---

