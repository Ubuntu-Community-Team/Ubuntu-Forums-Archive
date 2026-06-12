---
title: "windows 10 times changing"
date: 2020-02-08
forum: New to Ubuntu
---

### Post by coley9225 on 2020-02-08
I'm VERY new to linux based systems. After 2 years of failed install attempts, with multiple distros, I have finally got a functioning dual boot with windows 10 and lubuntu 18.04.3. Now that I've accomplished that, the fun of learning a new os begins. The first couple things I need to fix are being able to disable the touchpad, and an issue with the times my os shows. When I use lubuntu, I get the correct time,but when I reboot into windows the time is always off by 5 hours. I've checked the system clock( in uefi settings), and it is set correctly. I had this issue when using the live usb as well. Not a major issue, more of an inconvenience. The other thing is, I can disable my touchpad when using windows with fn+6, but that doesn't work in lubuntu. I normally don't like to use the touchpad, but a keyboard toggle command would be preferred to totally disabling it, in case of mouse failure. As I mentioned, I'm new to this, and while not totally in the dark with command line, I would need pretty  detailed instructions for things. Any tips will be greatly appreciated, and links to online manuals so I can look things up myself would be awesome. Thanks in advance, I look forward to learnig lubuntu so I can reduce my windows use, or kick windows to the curb completely.

---

### Post by CatKiller on 2020-02-08
> **coley9225 said:**
> When I use lubuntu, I get the correct time,but when I reboot into windows the time is always off by 5 hours. I've checked the system clock( in uefi settings), and it is set correctly. I had this issue when using the live usb as well. Not a major issue, more of an inconvenience. 

The issue is that Windows expects the hardware clock on your motherboard - powered by the small battery - to be set to the local time. Every other operating system expects that clock to be set to UTC. It doesn't strictly matter which one you use, but trying to use both means that the clock keeps being wrong by however many hours your timezone is from GMT. You can change Windows to use UTC or you can change Lubuntu to use the local time. Either will work, although I can't remember exactly how off the top of my head.

---

### Post by coley9225 on 2020-02-08
Thank you, I'll check into the how-to of changing 1 or the other.

---

### Post by alanthelinuxguy on 2020-02-08
> **coley9225 said:**
> When I use lubuntu, I get the correct time,but when I reboot into windows the time is always off by 5 hours.

As CatKiller noted, you can have Linux use the local time.  Do this by opening Terminal and using the command: [FONT=&quot]sudo timedatectl set-local-rtc 1 --adjust-system-clock

See: [/FONT][https://linuxnorth.wordpress.com/2017/12/12/incorrect-system-time-in-linux-mint-18-3/](https://linuxnorth.wordpress.com/2017/12/12/incorrect-system-time-in-linux-mint-18-3/) for associated details.

---

### Post by coley9225 on 2020-02-11
Thanks for the help. I have the time situation fixed, now on to disabling the touchpad. I have found that 'snyclient touchpadoff=1" will disable the tracking, but not the click action. With the help of the forums and my stubbornness( I fought my computer for 2 years to get Lubuntu to fully install...lol), I'm sure I will get it figured out. I would prefer a bash script that I can assign a keyboard shortcut to, in case of mouse failure, but anything will do for now.

---

### Post by yancek on 2020-02-11
You can use:  synclient ClickPad=1 to turn off the left click option on the touchpad and run synclient -l to get a list of options.

---

### Post by coley9225 on 2020-02-13
I would like to thank Catkiller ans Alanthelinuxguy for the help with the time change issue. I can now go from lubuntu to windows without having to constantlyreset the o/s system time. I would also like to thank kevdog and holger_gehrke for the help with my touchpad issue( on another thread). To be able to switch touchpad on/off, I wrote a bash script(shown below, in case someone else needs it) to toggle between on and off. I was told that the linux community would be very helpful, and indeed you are. Thanks again.

#!/bin/bash

#Toggle touchpad on/off with keyboard input

echo  "Do you want touchpad on?"
echo   "answer Y/N"
    read answer
     answer=${answer^^}
if  [[  ${answer} = 'Y' ]] ;
    then $(synclient touchpadoff=0)
    echo "touchpad on"
else
    $( synclient touchpadoff=1)
    echo "touchpad off"
fi
Thanks to the help I've received,I can now mark this thread solved.

---

### Post by TheFu on 2020-02-13
Didn't support for 18.04.3 end?  The current version is 18.04.4.  OP needs to run 
```
sudo apt update
sudo apt dist-upgrade

```to get onto a supported release.  This link has a chart about 70% down the page: [https://ubuntu.com/about/release-cycle](https://ubuntu.com/about/release-cycle)    The .5 release (expected Aug 2020) gets the remaining of the 5 yrs + extended + ESM support.  That link is really good for the charts.

Let me check something ... 
```
$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 18.04.4 LTS
Release:        18.04
Codename:       bionic
```

---

### Post by mastablasta on 2020-02-14
the .3 is still supported, however it will be changed to .4 when doing the system update anyway.

---

