---
title: "Wireless connection problem &amp; script query"
date: 2012-04-17
forum: New to Ubuntu
---

### Post by Mingcorra on 2012-04-17
Okay, I'm unable to conect to internet using current wireless. I was previously using Ubuntu 10 (dual boot with W7) and connecting on 3Com wireless router with no problems. Then I updated to Ubuntu 11.1 and around the same time switched from router to **Alfa Wireless AWUS036NH** wireless unit. While this unit works fine in W7, the same cannot be said for Ubuntu, despite the manufacturer providing instructions for doing so. Unfortunately, it seems the manufacturer's instructions are only good for Ubuntu 9.whatever and haven't been updated for the latest release. From what I can find on the web, and the forums here seem to be very helpful with solutions, I understand largely what needs to be done to solve the problem, that being adjusting some code and whatnot to affect a workaround. Herein lies the second part of my problem - being a very green Ubuntu convert I have no idea where to start pasting all these helpful code fixes.

For instance, I found this just this evening...
[http://www.leftech.com/getting_awus036nh_working_ubuntu_11_10.html](http://www.leftech.com/getting_awus036nh_working_ubuntu_11_10.html)

But without the knowledge of where and how to insert it, I'm lost. I can keep using Windows but I'd rather be on Ubuntu now.

Any help will of course be greatly appreciated.
Cheers.

---

### Post by Mingcorra on 2012-04-17
Right, I fluked the script and got lucky. Now my AWUS036NH connects alright but I need to insert the following code into sudo each time...

sudo modprobe rt2800usb

Is there some way I can enter it once only? The full script which I was able to use the above line to make it work is as follows...

#!/bin/bash
#A little script to get the AWUS036NH working in ubuntu 11.10
#It also boosts the tx power to 1W
#Coded by GUNN4R, 15 Oct 2011
if [ "$#" -eq 0 ]
then
  echo -e "Not Enough Arguements!\\nUsage:\\nboost.sh start  -- starts the card"
  echo "boost.sh wlan5  -- this boosts the tx power to 1MW"
  exit
fi

sudo modprobe rt2800usb
sleep 2

if [ "$1" = "start" ]
then
  echo '148f 3070' | sudo tee /sys/bus/usb/drivers/rt2800usb/new_id
  ifconfig
else
  sudo ifconfig $1 up
  sudo iw reg set BO
  sudo iwconfig $1 txpower 30
  iwconfig
fi

I have the modprobe line saved on desktop now but a simpler solution would be preferable. Thanks in advance to anyone who can help.
Cheers,
Mingcorra.

---

