---
title: "Nvidia Pro drivers/GTX750/800x600 only"
date: 2015-03-24
forum: New to Ubuntu
---

### Post by tony76 on 2015-03-24
I got a new computer. I wanted to make the move  from windows to linux. I am new linux. I have had a steep learning curve in working this issue. Since i have made the move, i cant adjust my  resolution. I have tried Fedora 21 and now Ubuntu 14.04. They both do  the same thing. I am having more success with Ubuntu. On fedora I was not  able to get my nvidia drivers working. I was able to install the pro  drivers on Ubuntu. However i did get an error that lib32 support was missing but It continued to install.   i would like to stay on Ubuntu. To  the crux of the problem, or what i think is the problem. I am not sure  why but my edid is not being recognized. I dont know if it is my video  card or some other component. I have been working on this for several  days. I have followed several walk-throughs. I have reinstalled my  Ubuntu a couple of times. So far so good on the reinstalls. :) 

Latest steps on Ubuntu:
----- I have tried several ways to change my xorg.conf file.
            ---that included adding modes ex:"1440x900_60"
            ---i used xrandr to generate a modeline for the xorg.conf
            ---i tried to use xrandr ---addmode(no joy) xrandr -q shows 800x600 only 
                  --wont allow me to add a mode line beyond 800x600
----- I have tried to make my own edid and add it to the xorg.conf file
             ----- under section i added - option "CustomEDID" "DFP-3:/etc/X11/***.bin"(no joy)
              ---- i also added option "IgnoreEDIDChecksum" "DFP-3"
                   ----caveat is that i used nvidia-config --customedid command (?)

I  went this route because the xorg.log doesn&#8217;t recognize my monitor.  xrandr doesn&#8217;t show  my monitor specs. get-edid | parse-edid doesn&#8217;t show  them. I got the .bin by plugging my monitor into a windows laptop and  exporting a file from the Phoenix edid designer.  Short of buying windows 7 i am not  sure what do. i thought adding the .bin i created to grub might be  better. I saw a walk-through. i am not completely sure i can do that. I  would need a super newb walk-through. i just added the ignore checksum. I saw an error for it while pasting the xorg.log in pastebin. after i added the checksum, i got more edid info in the log. The edid i created seems broken. I am still getting errors in the log that it cant be read correctly. I would appreciate any help or advice. Thanks! 

[Tony's-Xorg.conf-3/24/15-1:55pm]("http://pastebin.com/ZCGF9i7J")

[IMG]http://pastebin.com/i/t.gif[/IMG] [Tony's-Xorg.server.log-3/24/15-1:55pm]("http://pastebin.com/Ypqcz9aw")


i continued to compare my saved .bin file with the log binary.


my saved .bin file:

0x   00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F 
    ------------------------------------------------ 
00 | 00 FF FF FF FF FF FF 00 10 AC 03 F0 4D 54 36 33 
10 | 0F 12 01 03 68 29 1A 78 EE C1 25 A3 56 4B 99 27 
20 | 11 50 54 BF EF 80 95 00 71 4F 81 80 95 0F 01 01 
30 | 01 01 01 01 01 01 9A 29 A0 D0 51 84 22 30 50 98 
40 | 36 00 98 FF 10 00 00 1C 00 00 00 FD 00 38 4B 1E 
50 | 53 0E 00 0A 20 20 20 20 20 20 00 00 00 FF 00 37 
60 | 33 37 33 31 38 34 38 33 36 54 4D 20 00 00 00 FC 
70 | 00 44 45 4C 4C 20 53 45 31 39 38 57 46 50 00 0E

The xorg file sees this:
      6.059] (--) NVIDIA(GPU-0):   ff ff ff ff ff ff ff 00  10 ac 04 f0 4d 54 36 33
[     6.059] (--) NVIDIA(GPU-0):   0f 12 01 03 80 29 1a 78  ee c1 25 a3 56 4b 99 27
[     6.059] (--) NVIDIA(GPU-0):   11 50 54 bf ef 80 95 00  71 4f 81 80 95 0f 01 01
[     6.059] (--) NVIDIA(GPU-0):   01 01 01 01 01 01 9a 29  a0 d0 51 84 22 30 50 98
[     6.059] (--) NVIDIA(GPU-0):   36 00 98 ff 10 00 00 1c  00 00 00 fd 00 38 4b 1e
[     6.059] (--) NVIDIA(GPU-0):   53 0e 00 0a 20 20 20 20  20 20 00 00 00 ff 00 37
[     6.059] (--) NVIDIA(GPU-0):   33 37 33 31 38 34 38 33  36 54 4d 01 00 00 00 fc
[     6.059] (--) NVIDIA(GPU-0):   00 44 45 4c 4c 20 53 45  31 39 38 57 46 50 00 14
[     6.059] (--) NVIDIA(GPU-0): 
[     6.059] (--) NVIDIA(GPU-0):   00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[     6.059] (--) NVIDIA(GPU-0):   00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[     6.059] (--) NVIDIA(GPU-0):   00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00

---

### Post by jimmy-frydkaer on 2015-03-25
Have you tried using **additional drivers** from your Dash? (Top icon on the left on your desktop)

After installing the correct non-free driver you can install **sysinfo** from Ubuntu Softwarecenter.

In your sysinfo program, after install/reboot of your non-free driver, you'll see an NVIDIA entry in the bottom in the left listing. From here you can start the nVidia Display Settings from where you can fine tune your settings.

---

### Post by kc1di on 2015-03-25
Also after installing the driver from additional drivers you should see a Nvidia x-server setting applet in your cotrol center , you would now use that to set the resolution on your monitor instead of the regular monitor setting tool.  Good Luck and welcome to Ubuntu :)

---

### Post by mastablasta on 2015-03-25
at least you get the desktop. anyway try newer drivers (maybe via PPA) - they should support this card better.

---

### Post by residualbit on 2015-03-25
Which driver did you actually install and from where?

I have a 750ti and have been using the 346.xx driver without issue.

```
sudo add-apt-repository -y ppa:xorg-edgers/ppa

sudo apt-get update

sudo apt-get install nvidia-346 nvidia-settings
```

---

### Post by tony76 on 2015-03-25
[COLOR=#000000]jimmy-fyrdkaer - when i first got ubuntu installed, i didnt get a prompt for additional drivers. when i actually searched for additional drivers, i didnt get an option to add any. I was not aware of the sysinfo tool. I will definitely add that.[/COLOR]

kcd1- would the additional drivers be part of the 346 drivers from the repo? I used a walk-through that disabled nouveau and any nvidia drivers from the initial install. Then I tried the 347 and 304 pro drivers from the nvidia website. 

mastablasta - thanks for the links. I definitely need those. 

oxnate - Thank you for the advice. When i get home I will try to add the ppa and 346 drivers and  let everyone know how it goes.

---

### Post by dino99 on 2015-03-25
it's time to upgrade to 15.04, which is the best release at time; nvidia-346 is included to the vivid archive and works smootly

---

### Post by residualbit on 2015-03-25
9d9, upgrading to a still-in-beta, non-lts release is probably not the best advice for someone new to ubuntu and already having issues... Installing nvidia-346, or any other drivers from the ppa is pretty simple and most cases, still let's you enjoy a stable LTS release.

tony76, you weren't seeing anything in the additional drivers tool because the repositories in 14.04 (and 14.10) don't have the drivers officially needed to support that card. I've heard that 331 will 'mostly' work, but only 340 and later officially support it. 346 is the current, stable, 'long lived branch' nvidia driver, so it is definitely the one to go with, especially for that card.

Let me know if that that ppa i mentioned above doesn't work out for you.

---

### Post by tony76 on 2015-03-25
Oxnate - Thanks! The ppa drivers were a breeze. My computer still had a fit about the edid.  Phoenix edid designer added a weird format that confused my card. I removed the hyphens and the numbers to the left and top of the hyphens. Once i copied the file and readded it to to my xorg file, boom i was in business. I learned a lot for the trouble. i cant knock that. Thanks all! I am hoping to eventually help others. 

[COLOR=#000000]0x 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F [/COLOR]
[COLOR=#000000]------------------------------------------------ [/COLOR]
[COLOR=#000000]00 | 00 FF FF FF FF FF FF 00 10 AC 03 F0 4D 54 36 33 [/COLOR]
[COLOR=#000000]10 | 0F 12 01 03 68 29 1A 78 EE C1 25 A3 56 4B 99 27 [/COLOR]
[COLOR=#000000]20 | 11 50 54 BF EF 80 95 00 71 4F 81 80 95 0F 01 01 [/COLOR]
[COLOR=#000000]30 | 01 01 01 01 01 01 9A 29 A0 D0 51 84 22 30 50 98 [/COLOR]
[COLOR=#000000]40 | 36 00 98 FF 10 00 00 1C 00 00 00 FD 00 38 4B 1E [/COLOR]
[COLOR=#000000]50 | 53 0E 00 0A 20 20 20 20 20 20 00 00 00 FF 00 37 [/COLOR]
[COLOR=#000000]60 | 33 37 33 31 38 34 38 33 36 54 4D 20 00 00 00 FC [/COLOR]
[COLOR=#000000]70 | 00 44 45 4C 4C 20 53 45 31 39 38 57 46 50 00 0E [/COLOR]

---

### Post by sandyd on 2015-03-25
Hi, if you have found a solution to your thread, please mark this thread as solved via Thread Tools -> Mark Thread as Solved.

Thanks!

---

