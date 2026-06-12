---
title: "Quick fixes for brightness and CPU ?"
date: 2014-11-21
forum: New to Ubuntu
---

### Post by hebdave on 2014-11-21
High my hardware appears to work fine with my 14.04LTS on my laptop. I have heard though if you use a laptop and even a desktop that the CPU for any normal tasks uses more than windows does. If this is so is there a way to trim down the usage a bit in the code or settings. Also I find myself constantly having to turn down the brightness to half and wondered if you could help me turn down the default permanently ? Perhaps there is an easy number I can reduce in the code. 

I have not idea about codes and programming by the way which is why I'm posting in the beginners section. I do not that the terminal is called nano though thats it.  Is there anyone who might consider helping me ?

Thanks.

---

### Post by Frogs Hair on 2014-11-21
> I have heard though if you use a laptop and even a desktop that the CPU for any normal tasks uses more than windows does. I dual boot with Win-7 and see no difference in tasks like web browsing and playing video. Windows and Linux have processes unique to each operating system and with Linux some desktop environments require more resources than others.

---

### Post by grahammechanical on 2014-11-21
I have been using Ubuntu for 7 years and I would not think of messing with the code of Ubuntu. It is certainly not something a new user should be attempting. Ubuntu is Free and Open Source Software (FOSS). That means it is possible to obtain the code and modify it. You cannot say that about Windows.

You might find a utility in System Settings for adjusting brightness. I use a desktop. So, I do not have the ability to change the screen brightness level. But Ubuntu running on a laptop might give you that option.

By the way, the terminal is called "terminal" and nano is a text editor. And considering that each new version of Microsoft Windows requires ever more powerful hardware but Linux does not, I cannot see how Windows would use less CPU resources than Linux.

Regards,

---

### Post by pfeiffep on 2014-11-21
> **hebdave said:**
> High my hardware appears to work fine with my 14.04LTS on my laptop. I have heard though if you use a laptop and even a desktop that the CPU for any normal tasks uses more than windows does. If this is so is there a way to trim down the usage a bit in the code or settings. Also I find myself constantly having to turn down the brightness to half and wondered if you could help me turn down the default permanently ? Perhaps there is an easy number I can reduce in the code. 

I have not idea about codes and programming by the way which is why I'm posting in the beginners section. I do not that the terminal is called nano though thats it.  Is there anyone who might consider helping me ?

Thanks.CPU Frequency Scaling Monitor is available - I have it set to on demand on my laptop. It can be installed / activated by adding it to a panel - I'm using Ubuntu 14.04.1 (LTS) with gnome flashback installed so I'm not quite certain the steps to suggest if you're using the default desktop environment. 

I had difficulty with the brightness control on my laptop and had to install  Intel linuxgraphics, of course this only applies if you have Intel graphics. Details can be found on my[ post.]("http://ubuntuforums.org/showthread.php?t=2251752")

By applying these two 'fixes' I significantly increased battery life!

You may not want to use nano currently maybe never. It's part of the 'normal' Ubuntu installation and I strongly suggest simply ignoring it versus trying to remove it. 
Using the Linux terminal and a text editor such as nano provides finer control of your system than using the gui tools. 

The folks who regularly frequent this forum are all willing to help - can you please be more specific as to with what you need help?

---

### Post by hebdave on 2014-11-27
High we tend to read Google and see these things said in the wrong context. So its nothing Ive experienced personally with the CPU. It was just a question really. 

One thing I would want to do is some how get the GUI to have a **fixed** light setting. Currently when you reboot you have to manually re-adjust the brightness every time. The GUI's slider should have a feature where by you can save the brightness at the level permanently. Its quite bad after all the re-designs of Ubuntu this has not been picked up. This would be quite a few people point of view I feel.

Thanks.

---

### Post by Frogs Hair on 2014-11-27
I know some users with intel graphics have had success with solution 2 at the link.    [http://askubuntu.com/questions/450131/make-xconf-configuration-permanent](http://askubuntu.com/questions/450131/make-xconf-configuration-permanent)

The following terminal command will display graphics information. ```
lspci
```

---

### Post by hebdave on 2014-11-28
Oh hec I think I am doing something wrong. Do I need to just enter it before the 0 and do I need to press the ctrl O at some point and ctrl exit with the terminal. I seem to only have learnt bits last time with doing hibernate and am still confused how to use the terminal. Can you perhaps replicate how I might try and do this as a newbie and give an exact order of events. It might encourage people in the future to have a go at it rather than being not 100 % certain from the "Ask Ubuntu" link you have given. Need a bit of a helping hand hear sorry ! I did try and do it. Hope I have not wrecked the system or anything. It is 

00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05) 

by the way.

Cheers.

---

### Post by Frogs Hair on 2014-11-28
The lspci command won't damage anything and the terminal can be closed after using it . The line you are looking for should look something like the following depending on what kind of graphics card/chip is installed. I've not had to use any work around to get the brightness setting working and don't know why anyone should have to but apparently there is a problem with some computers.      

```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)

```

---

### Post by hebdave on 2014-11-30
Hi is it safe to post the whole lot on here. I cannot see which one you want. Ive posted one above already which I hope you saw. There are some below too that Ive given but not all of them. I cannot find ones which directly uses the word graphics in the sentence. The first one I posted above originally was my best guess. The other bits I posted related to not knowing all the steps to take from looking at the Ask abuntu link you gave where another person had been answered. This was due to not knowing still how to properly access writing , savings , exiting in the terminal. I had understood I enter the things ask ubuntu said before the command though. If you are meaning await further guidance after putting the  [COLOR=#000000][FONT=Ubuntu Mono]lspci that is fine.

[/FONT][/COLOR]If its not something you have had to deal with personally and had no experience really did you want some one else to step in ? The problem is my poor computer skills excuting whats been told of me so far. ie- it appears simple to anyone else , but perhaps I cannot see exactly the steps i'm needing to complete it easily. Or the terminal has a variation on the normal terminal. Has anyone written a blog with screen shot stages or done a video to show how to rectify it. What do I Google ?

00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)

00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)

---

### Post by Frogs Hair on 2014-11-30
You can post the entire output if you like. I have helped a friend the intel work around I linked and it was successful .There are others viewing this thread and would post if they had something to offer. Post the output so we can see what graphics card or chip you are using and go from there.

---

### Post by hebdave on 2014-12-01
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
02:00.0 Network controller: Intel Corporation Centrino Wireless-N 100
03:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
04:00.0 Ethernet controller: Qualcomm Atheros AR8151 v2.0 Gigabit Ethernet (rev c0)



```

Is that okay. Just to clarify my last post. I am saying I struggled with the placement issues and working of the terminal for this task. I did ask about hibernate and that seemed easier to do for some reason. So if someone can replicate the process to see if anything happens that you think I would not get. I am not saying thats the only way to help me. I have of course looked at the ask ubuntu link ( thanks to Frogshair) and tried to work out what goes where. As mentioned I may of done something wrong here with the writing and saving process. There should not be anything wrong with the link provided just *me* being the weakest link ! :???:

---

### Post by Frogs Hair on 2014-12-01
```
VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)DE
```

That's the one ! You can try the work around I linked from ask ubuntu and if you want it broken down into steps more than it is I will be glad to to help, just report back if you are not at ease with the instructions provided.

---

### Post by hebdave on 2014-12-01
Hi yes I couldnt grasp it after trying the ask ubuntu concepts and execution before was what I meant. I had decided to just try to see if I could do it before you checked my ASUS graphics type anyway. I got stuck understanding the terminal placement of the command ask ubuntu suggested with how to place the cursor at the beginning. Also then the way to then move the words in the terminal to put them at the start of it if that was required. Was I supposed to put directly in front on the same line or the prior line before also. Do i use the arrow keys initially or instead making it writeable, and at which point to make the "save" happen. And if I need to hit return at any point on my keyboard. Things like that I need to gain confidence in and couldn't fully gather. I used arrow keys to place the words for hibernate in a thread I started recently elsewhere and then made it writeable I think and then saved it- I should of wrote down how I did it for hibernate as it was probably a similar method. 

I will write down exactly the steps I take this time round so I can gain a bit of confidence here. Thanks hope I am making some sense at least. Here is am embarrassed icon :oops:

---

### Post by Frogs Hair on 2014-12-01
1. Open Terminal

2. Copy  & Paste and Enter the following command 

```
sudo apt-get install gksu 
```

3. Enter Password

4. Copy  & Paste and Enter the following command 

```
gksudo gedit /usr/share/X11/xorg.conf.d/20-intel.conf

```
5. Enter Password only if prompted  


This creates a configuration file in gedit.

6.Copy and Paste the text below in the new file which will be blank 


```
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"

EndSection
```

7. Save and close gedit

8. Close all programs and restart

Source: [http://askubuntu.com/questions/450131/make-xconf-configuration-permanent](http://askubuntu.com/questions/450131/make-xconf-configuration-permanent)

---

### Post by hebdave on 2014-12-04
Hi I restarted and there is no difference so far. It still makes me turn down the brightness manually. I noticed this error came up in the terminal after I placed this command, I think -

```
[COLOR=#000000][FONT=Ubuntu Mono]gksudo gedit /usr/share/X11/xorg.conf.d/20-intel.conf[/FONT][/COLOR]
```

It did open gedit text editor up and allowed me to put the next step of code into it and I saved it. But on looking back at the terminal I got an error I believe after the above gedit command was entered -

```
(gedit:3050):Gtk-WARNING **: Calling Inhibit failed:GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The nameorg.gnome.SessionManager was not provided by any .service files

(gedit:3050):Gtk-WARNING **: Calling Inhibit failed:GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The nameorg.gnome.SessionManager was not provided by any .service files
```

I have restarted the computer twice and it still reverts back to me having to change the graphic bar in settings to a lower light level. Just to be clear in case you weren't I was looking to make any adjustment permenant on re-booting.

Do I proceed and use this -

```
[TABLE]
[TR="bgcolor: transparent"]
[TD="class: votecell, bgcolor: transparent"][CENTER]down vote[/CENTER]
[/TD]
[TD="class: answercell, bgcolor: transparent"]Type this command in Terminal:
xrandr --output LVDS-0 --brightness 0.5
0.5 is used to decreased to adjust screen Brighness.
Should work Perfectly.



[/TD]
[/TR]
[/TABLE]

```

 
and then possibly add this -

```
[COLOR=#333333][FONT=UbuntuRegular]sudo setpci -s 00:02.0 F4.B=xx[/FONT][/COLOR]
```

I don't suppose you can test it can you if you have virtualbox or something. I fear a restart problem may occur according to ask ubuntu otherwise. I got the commands from your ask ubuntu prior link so I am not suddenly knowing more about computing.

I'm very thankful you made an easy to follow guide above I am sorry it has not worked so far.

I'll check back soon. Thanks for giving up your time. :)

---

### Post by Frogs Hair on 2014-12-04
The GTK errors when gedit or other graphical applications are opened via the terminal are fairly normal. The work-around is supposed  to and does stabilize the brightness setting for many people with intel graphics, but it is just a work-around. I'm familiar only with the steps I posted and used that method successfully on a friends computer.I haven't used anything outside of post 2 on the Ask Ubuntu page. I would do some web searching because there are various brightness fixes posted, but make sure they are current to your Ubuntu version.

---

### Post by hebdave on 2014-12-07
High thanks Frogs hair for all your help. Can I just quickly ask if I would implement things through gedit in the same way for the other ideas on ask ubuntu. And is there any chance of causing ubuntu to not start or anything else that could be bad to stop it working correctly ? If anyone else has a suggestion I am all ears. There are quite a few ideas on the ask ubuntu link. I am just not sure which one to do without causing myself more problems as a beginner with ubuntu ?

Thanks all.

---

### Post by Frogs Hair on 2014-12-08
You can try the following as suggested in the link , but it's not clear as to whether it's a permanent fix or not.  
```
xrandr --output LVDS-0 --brightness 0.5
```

---

### Post by xubu2 on 2014-12-08
This works for me to set the brightness.
Open **etc/rc.local** and paste the following line **above** "exit 0":
```
echo 5 > /sys/class/backlight/acpi_video1/brightness
```
Replace the number 5 with the brightness level you want.

Don't go over the maximum of your hardware.
This command is for checking the maximum:
```
cat /sys/class/backlight/acpi_video0/max_brightness
```

---

### Post by hebdave on 2014-12-09
High thanks I will have a go. Is this all done with the terminal or some in the gedit editer as well. I might need independent answers from each of you, I'm not sure.

many thanks we'll get there.

---

### Post by xubu2 on 2014-12-09
Just open the file manager with sudo in the terminal.
I'm on Xubuntu so for me it's: **sudo thunar**
I believe it's nautilus in Ubuntu.
So it should be: **sudo nautilus**
Then go to **etc** and open **rc.local **with gedit (rightclick).
Then change it like this:
```

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
echo 5 > /sys/class/backlight/acpi_video1/brightness
exit 0
```

---

