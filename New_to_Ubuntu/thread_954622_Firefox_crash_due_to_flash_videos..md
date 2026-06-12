---
title: "Firefox crash due to flash videos."
date: 2008-10-21
forum: New to Ubuntu
---

### Post by Pagh on 2008-10-21
Hey everybody.

I have a question regarding Firefox and flash videos.

The problem is that whenever I watch a Flash video my browser (Firefox 3) crashes - as if it had been subject to a pkill command or whatever. I was kinda clueless of what to do so i just tried to install the newest version of flash palyer (the one from adobe). This didn't help the slightest bit.

So is there anyone that know a way of solving this rather annoying problem?


All the best Kasper Roland Pagh

Ps. when I install flash player 10 (using the standard package installer for Ubuntu 8.4) does Firefox then automatically use it instead of flash player 9??

---

### Post by Duck2006 on 2008-10-21
> when I install flash player 10 (using the standard package installer for Ubuntu 8.4) does Firefox then automatically use it instead of flash player 9??

Did you uninstall flash player first?

---

### Post by HellNoire on 2008-10-21
Pagh, I woudl remove flash player 9 and install flash player 10, normally the new updates are more stable.

PS: Never knew ten was out yet. Thanks for the info ;)

---

### Post by eternalnewbee on 2008-10-21
Try this and see if it solves anything:
sudo apt-get install libflashsupport
If it doesn't, see this thread:
[http://ubuntuforums.org/showthread.php?t=953377&highlight=hate+flash](http://ubuntuforums.org/showthread.php?t=953377&highlight=hate+flash)

---

### Post by gandaran on 2008-10-21
Pagh
firefox 3.0.3 and flash 10 work very well, just make sure firefox is updated and use only flash 10, remove all other flash versions and libflashsupport, libflashsupport is responsible for firefox crashes!

---

### Post by wolfen69 on 2008-10-21
> **gandaran said:**
> libflashsupport is responsible for firefox crashes!

link to support that?

---

### Post by eternalnewbee on 2008-10-21
Here another confused soul..

---

### Post by gandaran on 2008-10-21
> **wolfen69 said:**
> link to support that?
wolfen 
it's unbelievable that a ubuntu forum user like you, who's been around here a long time should should have doubts about this, surely you must have read lots and lots of posts here about libflashsupport problems and know that it is in fact responsible for firefox crashes, well if you haven't read any just google libflashsuport crashes.
[http://www.google.pt/search?hl=pt-PT&q=libflashsupport+firefox+crashes&btnG=Pesquisa+do+Google&meta=](http://www.google.pt/search?hl=pt-PT&q=libflashsupport+firefox+crashes&btnG=Pesquisa+do+Google&meta=)

---

### Post by wolfen69 on 2008-10-21
> **gandaran said:**
> surely you must have read lots and lots of posts here about libflashsupport problems and know that it is in fact responsible for firefox crashes


sorry to disappoint you, but i do not read every single post. nobody here knows everything. i didn't realize that by being a long time member that i was obligated to know certain things. in the future i will do my best to research all of ubuntu's problems and memorize the answers.

---

### Post by eternalnewbee on 2008-10-21
Good luck with that:guitar:

---

### Post by kansasnoob on 2008-10-21
Assuming this is either 8.04 or 8.10 try this:

```
 sudo apt-get install --reinstall ubuntu-restricted-extras
```

(Of course change that to kubuntu or xubuntu if that's what you're running)

Then:

```
sudo apt-get remove --purge flashplugin-nonfree
```

Then:

```
cd ~/.mozilla
rm flashplayer.xpt libflashplayer.so
```

(That may take a minute so be patient and don't worry if it says "not found" or some such)

Then install the "apt" version of flash from here:

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

It'll now show up in synaptic as adobe-flashplugin rather than flashplugin-nonfree.

Now close Firefox and restart the desktop (Crtl > Alt > Backspace).

Hopefully flash will work.

Another great help is installing flashblock from synaptic.

---

### Post by Pagh on 2008-10-21
First of all: Thanks for all the quick and helpful replies.

To kansasnoob: There is no file called flahsplayer.xpt in the said folder - there is a libflashplayer.so - which I deleted. Then i go to the adobe home page but I'm somewhat unable to install the .APT version (an javascript alarm box pop up and says: "Can not find 'adobe-flashplugin'") 
- however .deb works fine - is it okay to use that one? 


Once again tanks for the fast and helpful replies!

---

### Post by philinux on 2008-10-21
libflashsupport was this for pulse audio and flash 9 and is not needed now.
[http://www.pulseaudio.org/wiki/FlashPlayer9Solution](http://www.pulseaudio.org/wiki/FlashPlayer9Solution)

To the OP

In the address bar of firefox type this
```
about:plugins
```

Let us know which flash version firefox is using.

---

### Post by Pagh on 2008-10-21
Okay I just tried out to install the .deb version again - and now it seems that everything is working fine!!! The problem properly was that the flash 9 was still installed. 

So everything is fine now! thanks a lot everyone :-D

---

### Post by gandaran on 2008-10-21
> - however .deb works fine - is it okay to use that one? 

yes, the deb package or any other package you download here [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash) contains the same flash version
in-fact you can use any of those packages if you know how to handle/install them in ubuntu
the .deb package just makes a simple ubuntu install.

---

### Post by ebe0 on 2009-01-21
**Thank you all.**
I had a simillar problem. When i opened flash videos firefox would crash sometimes (just vainsh without any error or anything).
My installation before the fix-
ubuntu 8.04.1 (2.6.24-23-generic)
Mozilla Firefox 3.0.5
flashplugin-nonfree
libflashsupport

The fix
I used information from 
1. [https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)
2. [http://ubuntuforums.org/showpost.php?p=5999380&postcount=17](http://ubuntuforums.org/showpost.php?p=5999380&postcount=17)
from [http://ubuntuforums.org/showthread.php?t=953377&highlight=hate+flash](http://ubuntuforums.org/showthread.php?t=953377&highlight=hate+flash)
3. and this post

a.
```
sudo apt-get remove libflash-mozplugin libflashsupport flashplugin-nonfree
```
(In my installation i didn't have libflash-mozplugin)
b.
then download Flash 10 from [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb)
and installed it.

c.
reboot the computer

Now firefox was not crashing anymore, however totem and mplayer were not playing videos smoothly
So i installed libflashsupport again

d.
```
sudo apt-get install libflashsupport

```

Hope this is useful.

---

### Post by kaston on 2009-01-25
i dled and installed flash 10 from this link:  [http://fpdownload.macromedia.com/get...r_10_linux.deb](http://fpdownload.macromedia.com/get...r_10_linux.deb) and then rebooted, but when i do an about:plugins in firefox, it still shows flash9.  any idea why?

---

### Post by Rackstar on 2009-03-15
I followed the steps of Kansasnoob, and finally, after months of suffering this worked!

And then I was stupid enough to install the updates for adobe-flashplugin. Then the same stuff happens. So basically: running the .deb from adobe itself worked fine, after updating through the normal repositories it starts crashing again.

How do I stop getting asked to upgrade the package? Otherwise I'll install it again without knowing.

EDIT: I did "about:plugins" in firefox, and then I saw there were two entries of shockwave flash
- Shockwave Flash 10.0 r22
- Shockwave Flash 10.0.0.d525

I did not know which one was more recent, but I disabled the second one. Did the update I previously was talking about. And still no crashes. I don't understand why there were two, because i have done all the possible remove and--purge commands I could find.

EDIT: Again crashing, will try to do the steps again, and try something else

EDIT: did purge on adobe-flashplugin and then reinstalled it back through synaptic, did some heavy flash browsing, no crashes yet, but won't be sure until in a day

EDIT: first crash, it seems that it became better, but still crashes, just going to buy me a fresh new stressball then.

Thanks

---

