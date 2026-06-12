---
title: "Graphic Cards and Drivers"
date: 2012-07-15
forum: New to Ubuntu
---

### Post by KaisaUbun2 on 2012-07-15
I'm really new to Ubuntu I used Ubuntu 7.04 Wasn't really feeling it yet, then used 9.04 and 10.04 as well I loved the improvements and now 12.04 is great I am loving it. I have a few problems though. One being the Graphic Driver I have an Nvidia GT 525m (1Gb) any idea how I can get the drivers for it? Preferably NVidia but anything that makes it work is good. ( or maximize it's potential)

---

### Post by ranger1021994 on 2012-07-15
Check this menu
==>System Setting ==> Additional Drivers
Or you can go to Nvidia website and manually download  .run files for Linux based system [If they provide ]

---

### Post by Pilot6 on 2012-07-15
You can install drivers using normal way
sudo apt-get nvidia-current

If it does not work for some reason, you can add x-swat ppa and get the newest one.

---

### Post by KaisaUbun2 on 2012-07-15
How do i then install the manually downloaded driver? 

Also I tried the x-swat ppa but when I go to the nvidia X it says " You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server."

---

### Post by Pilot6 on 2012-07-15
It is not a good idea to install manually downloaded drivers, because you will need to reinstall them after each kernel update.
I think you did something wrong with x-swat ppa

Just enter in terminal
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current

---

### Post by KaisaUbun2 on 2012-07-15
this is exactly what I did, and as far as I'm concerned it seemed to finish without issue. Still getting the error message however. Any other Ideas?

---

### Post by Pilot6 on 2012-07-15
Did you reboot after install?

---

### Post by KaisaUbun2 on 2012-07-15
Naturally.

---

### Post by NikTh on 2012-07-15
> **KaisaUbun2 said:**
> this is exactly what I did, and as far as I'm concerned it seemed to finish without issue. Still getting the error message however. Any other Ideas?
Hi ,
It is possible you have hybrid graphics. Nvidia optimus and intel (integrated to CPU). 


Give the result of this command ```
lspci -nnk | grep -iA2 vga
```

Put the results inside [CODE] tags by highlighting the text and click on # symbol at the top of message pane .
Thanks

---

### Post by Basher101 on 2012-07-15
i dont know why but ubuntu has some troubles with nvidia drivers.

I use a GTX 570 and i always got it solved by installing the 3 packages ```
nvidia-current
``````
nvidia-common
``` and ```
nvidia-settings
``` install all those 3 and click at the additional drivers again. Reboot and it should solve your problem


kudos

---

### Post by KaisaUbun2 on 2012-07-15
I know for a fact that I am not using an integrated graphic card. I like to play video games and made sure to get a pretty graphic card that could run most if not all video games. And it also has a TV tuner. 

[CODE] -Dell-System-XPS-L702X:~$ lspci -nnk | grep -iA2 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
    Subsystem: Dell Device [1028:04b8]
    Kernel driver in use: i915
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation Device [10de:0dd6] (rev a1)
    Subsystem: Dell Device [1028:04b8]
    Kernel driver in use: nvi  [CODE]

---

### Post by KaisaUbun2 on 2012-07-15
> **Basher101 said:**
> i dont know why but ubuntu has some troubles with nvidia drivers.

I use a GTX 570 and i always got it solved by installing the 3 packages ```
nvidia-current
``````
nvidia-common
``` and ```
nvidia-settings
``` install all those 3 and click at the additional drivers again. Reboot and it should solve your problem


kudos

I'm not absolutely sure how I should run those, I am really new to this linux thing. So if you could elaborate if this works 1000 thanks

---

### Post by NikTh on 2012-07-15
Hi , 
Ok. Yes you have hybrid graphics ... so  there is a project about hybrid Nvidia and intel , called bumblebee..
Run these commands one at time in your terminal..to install bumblebee . 
```
sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia
```reboot your pc.. and see if your problem corrected.
Here is the bumblebee project --> [http://bumblebee-project.org/](http://bumblebee-project.org/)
Thanks

---

### Post by KaisaUbun2 on 2012-07-15
Okay, here it says my HDMI input will temporarily not work until they come out with a fix? I don't have a VGA port or adapter? Thank you for everyone's support by the way.

---

### Post by KaisaUbun2 on 2012-07-15
> **NikTh said:**
> Hi , 
Ok. Yes you have hybrid graphics ... so  there is a project about hybrid Nvidia and intel , called bumblebee..
Run these commands one at time in your terminal..to install bumblebee . 
```
sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia
```reboot your pc.. and see if your problem corrected.
Here is the bumblebee project --> [http://bumblebee-project.org/](http://bumblebee-project.org/)
Thanks

Okay I have done this. Now I hate to be difficult but i'm not really sure what exactly just happened or what I have done? just for future reference could you explain, also the nvidia x server is gone...

---

### Post by NikTh on 2012-07-15
> **KaisaUbun2 said:**
> Okay I have done this. Now I hate to be difficult but i'm not really sure what exactly just happened or what I have done? just for future reference could you explain, also the nvidia x server is gone...

Hi , 
what do you mean about the nvidia x server is gone ? 
try to reinstall nvidia drivers.. with this command
```
sudo apt-get install --reinstall nvidia-current 
``` , reboot needed for driver take place. 

Bumblebee its a project that someone can use when has 2 graphics cards , (like you have) . Nvidia has this optimus technology and can cooperate with intel. Operating system use either Nvidia or intel depends what job you want to do.. 
This project (bumblebee) ensures that switch (Nvidia -intel ) will work as it should. 
Thanks

---

### Post by KaisaUbun2 on 2012-07-15
Okay Well for right now I open the Nvidia X server by optirun nvidia-settings -c :8 

I can't find it in the dash but that's okay Thanks a lot for the help! The card is at least showing up now. The HDMI port still isn't working though, any ideas?

---

### Post by Basher101 on 2012-07-15
> **KaisaUbun2 said:**
> I'm not absolutely sure how I should run those, I am really new to this linux thing. So if you could elaborate if this works 1000 thanks

I can't find it in the dash but that's okay Thanks a lot for the help! The card is at least showing up now. The HDMI port still isn't working though, any ideas?

oh my apologies, you need to run the same command to install packages which is ```
sudo apt-get install - program -
``` just replace - program - with the package/application you want to install. In this case it would be ```
sudo apt-get install nvidia-current
``````
sudo apt-get install nvidia-common
``````
sudo apt-get install nvidia-settings
```

kudos

---

### Post by NikTh on 2012-07-15
> **KaisaUbun2 said:**
> Okay Well for right now I open the Nvidia X server by optirun nvidia-settings -c :8 

I can't find it in the dash but that's okay Thanks a lot for the help! The card is at least showing up now. The HDMI port still isn't working though, any ideas?

Hi , 
are you sure that you connected the hdmi correct ? Its possible motherboard had 2 hdmi ports. Try to switch and see . 

Try to reinstall all packages.. 
```
sudo apt-get install --reinstall nvidia-current nvidia-settings nvidia-common
```

After above command , please give the results of this command 
```
 apt-cache policy nvidia-current nvidia-common nvidia-settings
``` 
**Please post results here inside [CODE] tags by highlighting the text and click on # symbol on top of message pane. **
Thanks

---

### Post by KaisaUbun2 on 2012-07-16
I only have one Hdmi port which is the one connected to the Nvidia Graphic card, my Integrated card doesn't have any ports at all, on the bumblebee website they were saying they were still working on a fix but there are some solutions out there.

---

### Post by KaisaUbun2 on 2012-07-16
> **NikTh said:**
> Hi , 
are you sure that you connected the hdmi correct ? Its possible motherboard had 2 hdmi ports. Try to switch and see . 

Try to reinstall all packages.. 
```
sudo apt-get install --reinstall nvidia-current nvidia-settings nvidia-common
```After above command , please give the results of this command 
```
 apt-cache policy nvidia-current nvidia-common nvidia-settings
```**Please post results here inside ```
 tags by highlighting the text and click on # symbol on top of message pane. **
Thanks
[CODE]
nvidia-current:
  Installed: 302.17-0ubuntu1~precise~xup1
  Candidate: 302.17-0ubuntu1~precise~xup1
  Version table:
 *** 302.17-0ubuntu1~precise~xup1 0
        500 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
     295.40-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
nvidia-common:
  Installed: 1:0.2.44
  Candidate: 1:0.2.44
  Version table:
 *** 1:0.2.44 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
nvidia-settings:
  Installed: 302.17-0ubuntu1~precise~xup3
  Candidate: 302.17-0ubuntu1~precise~xup3
  Version table:
 *** 302.17-0ubuntu1~precise~xup3 0
        500 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
     295.33-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main amd64 Package
```s

And what is this and what does it mean?

---

### Post by NikTh on 2012-07-16
> **KaisaUbun2 said:**
> ```

nvidia-current:
  Installed: 302.17-0ubuntu1~precise~xup1
  Candidate: 302.17-0ubuntu1~precise~xup1
  Version table:
 *** 302.17-0ubuntu1~precise~xup1 0
        500 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
     295.40-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
nvidia-common:
  Installed: 1:0.2.44
  Candidate: 1:0.2.44
  Version table:
 *** 1:0.2.44 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
nvidia-settings:
  Installed: 302.17-0ubuntu1~precise~xup3
  Candidate: 302.17-0ubuntu1~precise~xup3
  Version table:
 *** 302.17-0ubuntu1~precise~xup3 0
        500 http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
     295.33-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main amd64 Package
```s

And what is this and what does it mean?
Hi ,
This means that you have installed all the required packages correctly. 
I don't really know (i have not Hybrid Graphics) , maybe bumblebee not work well for you. 
A last thought : Boot in to bios configuration and try to disable integrated intel graphics (if you have this option.) Search it. 
Thanks

---

