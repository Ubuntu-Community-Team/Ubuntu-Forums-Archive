---
title: "How Do I Get Online?"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by JuanTing on 2008-05-23
How do I get online?

I loaded ubuntu onto my hard drive from CD. I have been increasingly disillusioned with Microsoft Windows and did not bother with any of this partitioning stuff. I jumped right in and decided to use the new system from the start. I finished up with a computer which only had an Ubuntu operating system. I cannot get online with that computer without downloading some drive or other from the Ubuntu site. Ubuntu will not allow me to reinstall windows. I get the message that this is not supported by Ubuntu. I could not uninstall Ubuntu so I am in a catch 22 position.  I cannot get online without getting online first.
I do not particularly wish to uninstall Ubuntu I just wanna get online with that computer. Any advice please?

---

### Post by hyper_ch on 2008-05-23
How do you try to get online? Through wireless? If so, have you not an ethernet card in the computer?

---

### Post by The Cog on 2008-05-23
How are you trying to get online? Ethernet, wireless, dialup modem card?

As much detail as you can give would help, especially the make of the network adapter.

---

### Post by meborc on 2008-05-23
are you using a laptop or a desktop? does sticking the net-cable in not fix the problem? :) strange...

try sticking it in and opening the terminal... then type **sudo dhclient** enter ... enter your password... what happens? do you now have internet? (this will work with automatic dhcp)

what do you mean ubuntu will not allow windows to be installed :) put in the windows cd... reboot your computer from cd... format c: ... install windows

---

### Post by JuanTing on 2008-05-23
Thank you for your interest folks. I have broadband (ADSL) but it is not my computer that is preventing me from getting online it is the Ubunto operating system. There is nothing wrong with my equipment only the system.

---

### Post by JuanTing on 2008-05-23
> **meborc said:**
>  what do you mean ubuntu will not allow windows to be installed :) put in the windows cd... reboot your computer from cd... format c: ... install windows

I tried that one chum. No dice.

---

### Post by iaculallad on 2008-05-23
Are you directly connected to your ADSL modem? Could you directly ping your ADSL modem?
Try to post the output of:

**ifconfig eth0**

---

### Post by hyper_ch on 2008-05-23
> **JuanTing said:**
> Thank you for your interest folks. I have broadband (ADSL) but it is not my computer that is preventing me from getting online it is the Ubunto operating system. There is nothing wrong with my equipment only the system.

Why is it Ubuntu operating system? What makes you think so?

---

### Post by ugm6hr on 2008-05-23
> **JuanTing said:**
> Thank you for your interest folks. I have broadband (ADSL) but it is not my computer that is preventing me from getting online it is the Ubunto operating system. There is nothing wrong with my equipment only the system.

That was never questioned.

Unfortunately, we are unable to help without knowing what you mean.  Ubuntu does not prevent you from getting online, just as Windows did not.  Just as in Windows, you may need a "driver" to make your hardware work.

Without knowing what your hardware is, we can't help.

So - if you want some advice, please provide the following details:
1. Wired or Wireless?
2a. If wired - ethernet or USB?
2b. If wireless - internal or USB wifi adaptor?
3. How are you online at the moment?
4. The output from the following commands may be useful, dependent on the answers to the above:
```
lspci
lsusb
lshw -C network
```

---

### Post by JuanTing on 2008-05-23
> **hyper_ch said:**
> Why is it Ubuntu operating system? What makes you think so?

It gives me a message explaing I need to download summat from the Ubutu site. I need to get online to download the means to get online. I cannot load windows either because the system will not allow it.

---

### Post by JuanTing on 2008-05-23
> **ugm6hr said:**
> That was never questioned.

Unfortunately, we are unable to help without knowing what you mean.  Ubuntu does not prevent you from getting online, just as Windows did not.  Just as in Windows, you may need a "driver" to make your hardware work.

Without knowing what your hardware is, we can't help.

So - if you want some advice, please provide the following details:
1. Wired or Wireless?
2a. If wired - ethernet or USB?
2b. If wireless - internal or USB wifi adaptor?
3. How are you online at the moment?
4. The output from the following commands may be useful, dependent on the answers to the above:
```
lspci
lsusb
lshw -C network
```

Okay. Firstly. I am using my old puter to get online now.
I have broadband so I use a filter and no modem. The filter is plugged into a USB port. It connects straight from the phone line.
I have nothing fancy to negotiate. No wireless thingies or other fancy gear. All I wanna do is connect to the web as I did using windows. I cannot connect without downloading the driver. I cannot download the driver without getting online.
I have dissconnected my other puter and was resigned to the fact that I would need to replace my drives so I could reload windows.

---

### Post by iaculallad on 2008-05-23
> **JuanTing said:**
> It gives me a message explaing I need to download summat from the Ubutu site. I need to get online to download the means to get online. I cannot load windows either because the system will not allow it.

Try to be specific with your answers: Why can't you load windoze, is it dual booted with Ubuntu? Try to post error messages so we could be in track with you. This is like blind leading the blind so give us clues/guide.

---

### Post by JuanTing on 2008-05-23
> **iaculallad said:**
> Try to be specific with your answers: Why can't you load windoze, is it dual booted with Ubuntu? Try to post error messages so we could be in track with you. This is like blind leading the blind so give us clues/guide.
I don't have windows on that puter. I only have Ubutu.

---

### Post by ugm6hr on 2008-05-23
> **JuanTing said:**
> Okay. Firstly. I am using my old puter to get online now.
I have broadband so I use a filter and no modem. The filter is plugged into a USB port. It connects straight from the phone line.

I have never encountered an ADSL connection that does not require some form of modem (cable-modem or ADSL modem).  This filter you use - do you have details about it?  What ADSL supplier do you use (and in which country)?I

As an aside - you can reinstall Windows without replacing your drives.  If you would prefer to do that - ask.

---

### Post by JuanTing on 2008-05-23
> **ugm6hr said:**
> I have never encountered an ADSL connection that does not require some form of modem (cable-modem or ADSL modem).  This filter you use - do you have details about it?  What ADSL supplier do you use (and in which country)?I

As an aside - you can reinstall Windows without replacing your drives.  If you would prefer to do that - ask.

I am in the UK. Virgin is my ISP.I have "SeedTouch" usb/330 ADSL filter/modem. This repaces the onboard modem. I would prefer to use Ubutu but I cannot get online with it. Okay I would re-load windows so that I could download the necessary drives for Ubutu. I tried to re-load my windows to get out of trouble but a message tells me that the system does not support what I am trying to load. ( Forget exact message.)

---

### Post by ugm6hr on 2008-05-23
> **JuanTing said:**
> I am in the UK. Virgin is my ISP.I have "SeedTouch" usb/330 ADSL filter/modem. This repaces the onboard modem. I would prefer to use Ubutu but I cannot get online with it. Okay I would re-load windows so that I could download the necessary drives for Ubutu. I tried to re-load my windows to get out of trouble but a message tells me that the system does not support what I am trying to load. ( Forget exact message.)

OK. Speedtouch 330 Modem - a common freebie modem here.

Unfortunately, Ubuntu doesn't support it "out-of-the-box".  I believe PCLinuxOS does.

Anyway - since you can get online with your old computer - download the files linked in the tutorial below, and transfer to Ubuntu using a USB FLash disc (or CD-R or whatever).

Then you should be able to just double-click on them in order (in Ubuntu).  As the instructions - use the correct version (32- or 64-bit).

[http://ubuntuforums.org/showthread.php?t=797804](http://ubuntuforums.org/showthread.php?t=797804)

Anything doesn't work - ask again (with details!)

---

### Post by quinnten83 on 2008-05-23
JuanTing, 
your entire post to us is completely unclear.
from what I gather this is what has happened so far, please tell us if it is correct.
- you placed the ubuntu cd when running windows
- you installed ubuntu and told it to wipe everything
- It installed, you tried opening firefox, but you got an address could not be found error.
- there appeared on the upper right corner a message stating that in order to connect to the internet Ubuntu needs to download and install some software
- you clicked on the option to download and it gave you an error that there was no network connection found.
- you right clicked on the two monitors in the rightupper corner and you could not select a connection.
You decided you wanted windows back and popped the windows cd back in while still in Ubuntu
Ubuntu gave you an error message saying it can not do what you want (that would be correct, because you cannot install windows from within ubuntu) You need to boot from the windows cd an then install it.

If you have a usbkey could you post a screenshot.
We are having a lot of trouble understanding what the problem is.

---

### Post by JuanTing on 2008-05-23
> **ugm6hr said:**
> OK. Speedtouch 330 Modem - a common freebie modem here.

Unfortunately, Ubuntu doesn't support it "out-of-the-box".  I believe PCLinuxOS does.

Anyway - since you can get online with your old computer - download the files linked in the tutorial below, and transfer to Ubuntu using a USB FLash disc (or CD-R or whatever).

Then you should be able to just double-click on them in order (in Ubuntu).  As the instructions - use the correct version (32- or 64-bit).

[http://ubuntuforums.org/showthread.php?t=797804](http://ubuntuforums.org/showthread.php?t=797804)

Anything doesn't work - ask again (with details!)


Thank you. I am trying that now.

---

