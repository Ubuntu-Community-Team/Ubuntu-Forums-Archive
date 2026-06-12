---
title: "Network setup"
date: 2021-02-09
forum: New to Ubuntu
---

### Post by dwf2008 on 2021-02-09
Hi all, I am Brand New to this Linux thing. Today I tried the Ubuntu live boot to give it a test run. I was able to get the sound working and play a couple of MP3s. (Yayyyy). But videos would not play. I tried MOV and MP4 formats. Do I need to do something to enable them?

More importantly it appears I had no network connection. I tried to follow the directions to configure manually but got lost in the less than intuitive interface. I have an ethernet connection on the motherboard (Gigabyte AORUS Pro AC) and a Netgear Nighthawk router. Windows had no trouble finding it and making the connection. Is there a trick to make this work in Ubuntu?

Thanks

PS. my hope is to set this up as a dual boot system with win10.

---

### Post by Autodave on 2021-02-09
Please give us some info on your machine.  Also, what version of 'buntu did you install?

---

### Post by dwf2008 on 2021-02-09
Thank you. Sorry I was derelict. It is the newest version of Ubuntu 20.04.2. The PC is a new build. Gigabyte AORUS Pro B550 AC, Ryzen 7 3800X, 32 gig g.skill RAM, Crucial P5 1Tb ssd. 
Thanks for any insights.

As an aside, the WIN10 Pro install seems to be working OK except the sleep timers are inoperative, no screensaver, no sleep, etc. I have been troubleshooting this for about 2 weeks now without success. However when I boot Ubuntu, the screen off timer seems to work just fine. This indicates to me that the problem is with windows and not the hardware, unless the 2 operating systems use different circuits for their timers. Does anyone know if this is the case, or is my thinking not straight?

---

### Post by rsteinmetz70112 on 2021-02-11
Is this a dual boot with Windows 10 on the same SSD?

I see it is a 2.5Gig Ethernet and wifi. Have you tried the wifi?

---

### Post by dwf2008 on 2021-02-11
The intent is to dual boot but ubuntu is not installed yet. I was running it in trial mode before actually installing. I am not using the wireless since I have a hardwired ethernet to avoid confusing things.
Thanks

---

### Post by TheFu on 2021-02-11
Welcome to the bleeding edge. You've found it with new hardware.  In general, long-time Linux people know to be 12-18 months behind on hardware to avoid/mitigate the issue you seem to be having.

2.5Gig Ethernet drivers often need the latest kernels for any hope of support. Don't quote me, but I think 5.9 or later are needed.  Probably not something for someone really new to tackle.

It is good to say that things are working with Windows, thanks, but know that the failure lies with the driver makers (i.e. the HW vendor), not Linux, not Canonical.  The vendor is responsible for providing solid, working, drivers and clearly has not. You may have better driver support with 20.10, but IDK. May need to wait until 21.04.  I only run LTS releases, so 20.10 and 21.04 won't touch my systems.

BTW, we really need to get the exact chips used for the stuff that isn't working to help at all. And even then, we are just going to google that device and "driver ubuntu" to see that 500 other people have the same issue (probably) and to see less than helpful recommendations to get the driver from Intel or Realtek, compile, and install it.  Every new kernel will require this same thing - a new kernel happens about 2x a month for most kernel lines.  But getting the needed programs to compile stuff isn't easy without a working network.

Or you can spend $25 and get an addon NIC that is well supported, known to work great, that can be used while you wait for the kernel to catch up to your bleeding-edge hardware. Any Intel PRO/1000 or i210 or i211 NIC should be fine.

May be worth trying the wifi, for now too. If that works, you'll have a much easier time, but often the wifi drivers would be bleeding edge if the ethernet drivers are too.  But you'll never know without trying.

To provide the information we need, we have a chicken/egg problem.  Providing the detailed information is best using either **lshw** or **inxi** programs, but those aren't usually part of the Live environment or a fresh install.  So, probably the easiest thing is to give you an ugly, complex, command to type.  Sorry:
```
lspci   -vk   |  egrep     --after-context=8    'Ethernet|Network' | tee /tmp/log
```
I've exaggerated the spaces for clarity. Only 1 space is needed. 

Then copy /tmp/log to a USB drive that can be read by Windows ... since I assume you are booting Windows to post here.  Copy/paste the file here - probably best to use Notepad++, not notpad for the copy/paste in Windows or the wrapping will be all wrong in your post.  **Code tags** would be helpful - the Advanced Editor in these forums has a '#' button. Use that, but don't worry too much.  [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code) explains more, if you care to make it easier to help you by using code tags.

---

### Post by dwf2008 on 2021-02-12
Thanks TheFu. About half of your response is over my head. The half I sort of understand is that you want me to run the command below and post the results. I assume this is done in something similar to a DOS/Cmd window. Can you tell me how to access that capability after booting the trial version of Ubuntu?
Thanks 
[COLOR=#000000]Code:[/COLOR]
lspci   -vk   |  egrep     --after-context=8    'Ethernet|Network' | tee /tmp/log

---

### Post by TheFu on 2021-02-12
Sorry, I don't know how to tell you to do that.

[https://help.ubuntu.com/](https://help.ubuntu.com/) has the Ubuntu Desktop Guide.  Be certain to select the version for your release.

[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) might be helpful. It is a free, no hassle, book, that explains those sorts of things - not just the what to type, but the "why."

---

### Post by grahammechanical on 2021-02-12
> But videos would not play. I tried MOV and MP4 formats. Do I need to do something to enable them?

You need third party/proprietary audio & video codecs. Ubuntu is Free & Open Source Software (F.O.S.S). The Ubuntu install media does not contain non-free, closed source, proprietary, third party software. And this includes video drivers. When we install Ubuntu we get an option to download and install third party software with a warning that in some countries it may be illegal to do so. It is our choice. When you install Ubuntu and tick that box you may find that video files will play. Another name for these codecs is Ubuntu Restricted Extras. They can be installed after installation.

Some users of Linux believe in only using Free and Open Source Software. And Ubuntu does not force proprietary software on us.

Regards

---

