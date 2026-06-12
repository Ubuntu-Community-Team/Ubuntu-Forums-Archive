---
title: "At a loss?"
date: 2014-04-21
forum: New to Ubuntu
---

### Post by rosswmcgee on 2014-04-21
Ubuntu 14.04.lts clean install will not let me adjust display resolution. It is way to large. What to do?  It says built in display on cannot shut it off. There is a pop up that says select a

monitor to change its properties:drag itto rearrange its placement. Again I am stymied.

---

### Post by Vladlenin5000 on 2014-04-21
Probably you need a different - proprietary - graphics driver. Please post the information regarding your graphics card. And easy way to know it is using the following command in terminal ```
lspci
```, find the line starting with "VGA" and then post here the full line. Thank you.

---

### Post by rosswmcgee on 2014-04-21
It is NIVIDIA MCP61

I an trying another install, because no terminal will not recognize password, what fun!! I have been trying to install 14.04 lts for days no go, next failure I will put back 12.04 lts and try an upgrade.

---

### Post by oldfred on 2014-04-21
Not sure what model nVidia you have, I have an old 9600GT.
And my screen is also very large.
But I go into system settings and select software and then other drivers. I found it a bit tricky to get to system settings and the software screen as it is off the bottom of the screen. 
But once I selected proprietary nVidia driver for my version of nVidia card, loged out and back in it worked just fine.

---

### Post by rosswmcgee on 2014-04-21
Cannot get there screen goes red. If i upgrade from 12.04 lts instead of a clean install will the uprade have the same problem as the clean install? We shall see.

---

### Post by buzzingrobot on 2014-04-21
Might  be worth adding "nomodeset" as a kernel boot parameter to see if that boots you into a usable screen, from where you can try to remedy things permanently.

---

### Post by WoodenWalker on 2014-04-21
What do you mean terminal will not recognize password? Are you referring to the password for the root user? In my experiences the password for root needs to be set after install. If I am misunderstanding, please clarify. Thank you. :)

---

### Post by oldos2er on 2014-04-21
> **rosswmcgee said:**
> I an trying another install, because no terminal will not recognize password, what fun!! 

It's normal for nothing to be echoed to the screen when entering your password into a terminal. See [http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)

---

### Post by rosswmcgee on 2014-05-11
Sorry still do not get it.

---

### Post by Vladlenin5000 on 2014-05-11
Your graphics card/chip is a nVidia GeForce 6150 and yes, you need proprietary drivers as I already mentioned and the easiest way to get them as also been commented here already.

---

### Post by rosswmcgee on 2014-05-11
VGA compatible controller: NVIDIA Corporation C61 [GeForce 6150SE nForce 430] (rev a2)


So what and where do I get what I need please and thank you? Also can I get it now before the clean install?

---

### Post by Vladlenin5000 on 2014-05-11
Yes, you can get it now. The easiest way has been explained in post #4. Please be aware of the issue also commented in that post. It really can be tricky due to the incorrect resolution you have now. I think you can also install via command line with the command below but _please please please_ try the GUI approach first. If you're unable to do it, before testing my suggestion, _please wait for @[**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=852711") to confirm if the below command is correct and/or if there's something missing_.

```
sudo apt-get install nvidia-current
``` followed by a reboot.

---

### Post by rosswmcgee on 2014-05-11
Patience please, I am running mint Maya, I could not get a good enough 14.04lts install  to do what you suggest. 
So do I do this with Maya and then attempt a new 14.0 4lts clean install?  Or would you install 12.04 lts and upgrade?

---

### Post by Vladlenin5000 on 2014-05-11
I would try 14.04 right away however "Maya" is based on 12.04, I think. What exactly didn't work to your liking in your previous attempts with 14.04?

BTW, your (onboard) graphics chip, albeit legacy already, isn't that old to have issues even with the open-source driver, except maybe resolution issues with certain monitors it doesn't recognize properly. The latest driver recommended by nVIDIA is the 304.88, released less than a year and a half ago.

---

### Post by LastDino on 2014-05-11
Drivers problem is happening in 14.04 so no point in getting it in Maya Mint and then trying to install 14.04. I wouldn't suggest installing 12.04 under normal circumstance *unless* it has ran successfully on your machine previously. Nevertheless, you're still more than likely to experience the problem if you did do it successfully and upgraded to 14.04 from there. 

Password problem is 100% from your end, it doesn't show up as you type so no need to panic, just type it and hit enter. If it is correct/same as the one you typed when installing, it will be accepted.

As already described, best way to get them for you is from that GUI solution of Oldfred. 
Not related but out of curiosity; How did you manage to install if Ubuntu is having that level of resolution problem? o-o

Another thing you can try is remove your Nvidia graphic card and attach monitor cable to on board socket
>then do the installation if problem persists
>then install the nvidia drivers or at least download the driver package to install manually, and install your graphic card 
>then install those drivers if you haven't already.
Should work most of the times ;)

---

### Post by rosswmcgee on 2014-05-12
I would try 14.04 right away however "Maya" is based on 12.04, I think. What exactly didn't work to your liking in your previous attempts with 14.04? 

Answer:

 I tried several attempts with Beta and then with the final release. I tried the immodest as well each time a different result, such as the minute I used the mouse the screen
would go red, or the install would screen size would be huge with no way to adjust, as I could not get to it. So as far as trying to adjust drivers no way to do so. I guess the easiest
way out for me now is to use Maya, wait to see if Mint 17 corrects the problem. I just got too eager, 12.04 lts was working fine, perhaps should have done the upgrade but opted
for clean install which as you see never was a success. The ubuntu forums are great. I have fixed many a problem with help here, so if we are scoring really this the first ever
linux distro that I have not been successful with. Thanks every one.


Read this on MInt forum:

ubuntu 14.04 used 3.13.0.x which have some kind of bug affecting some AMD graphic card users. When installing the proprietary drivers that os offered by ubuntu or when downloading them from AMD and installing, the system crashes and doesn't start up. So I tried 14.04 on another computer, same varied problems, Ubuntu hung a lot of AMD computer folks out to lunch, and believe me I have spent hours on this.

I have installed fedora, pc linux ubuntu 12.04, mint maya , open suse, and others but not U14.04.

---

### Post by rosswmcgee on 2014-05-15
Sorry, but just trying to understand:

After repeated failures I tried another computer with similar results with 14.04lts. So looking again at your post I tried to change drivers on one of the machines, which is now

running Maya.  The video drivers shown as available but not activated are:
 NVDIA 173 ,

NVDIA  304 recommended

NVDIA 304 updates

NVDIA  96

So on one MAYA I changed it to NVDIA 304 updates and it is currently in use.

On the other I tried changing to  NVDIA 304 updates and it did not work gave me a blank screen which in the end forced me to do another MAYA clean install, and as of now none  of the proprietary

drivers are activatedon that machine. So I guess I am asking should I try another install of 14.04 lts on the driver activated computer? Also are any of the other ubuntus such s lubuntu or xbuntu having the

same problem for AMD users?? 

I

---

### Post by rosswmcgee on 2014-05-15
Tried this now have out of range on the Maya 13

---

### Post by rosswmcgee on 2014-05-16
And the winning answer is!!!!!!!!!!!!!!!! ta da ta da. 

MInt Qiana 17 installs on AMD computers, and it is beautiful.

---

