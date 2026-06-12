---
title: "Lubuntu - How to Disable Touchpad Click?"
date: 2012-07-20
forum: New to Ubuntu
---

### Post by 2CV67 on 2012-07-20
I am running Lubuntu 11.10 on an Asus Eeepc 1015PED.

The touchpad is WAY too sensitive, so using it results in frequent unwanted selections & activations.
In Windows, I can turn the touchpad "Click" option off & that is just fine.
In Lubuntu, I have not found out how to do that.

I tried gpointing-device-settings which seemed to work, but reverted after reboot.

I found a lot of complex suggestions, none of which seem to fit:
[https://help.ubuntu.com/community/Lubuntu/KeyboardMouse](https://help.ubuntu.com/community/Lubuntu/KeyboardMouse)
[http://ubuntuforums.org/showthread.php?t=1457053](http://ubuntuforums.org/showthread.php?t=1457053)
[http://ubuntuforums.org/showthread.php?t=1901820](http://ubuntuforums.org/showthread.php?t=1901820)
[http://ubuntuforums.org/showthread.php?t=1875683](http://ubuntuforums.org/showthread.php?t=1875683)

Is there a simple, preferably GUI solution to what seems a very basic sort of question?

Thanks!

---

### Post by sudodus on 2012-07-20
I suggest you try touchpad-indicator. See this link

[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=2012745_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2012745")

---

### Post by 2CV67 on 2012-07-20
> **sudodus said:**
> I suggest you try touchpad-indicator.

Thanks, but it looks like Touchpad-Indicator turns off the whole touchpad.
I just want to turn off the "Click" or "Tap" function.

---

### Post by MoebusNet on 2012-07-20
I used this for my Lubuntu 12.04 installation: 

press> alt+f2
type> gksudo leafpad /etc/xdg/lxsession/Lubuntu/autostart

add your " @synclient MaxTapTime=0 "

thats the global for lubuntu session.

I found this at:

[http://ubuntuforums.org/showthread.php?t=1457053](http://ubuntuforums.org/showthread.php?t=1457053)

---

### Post by NikTh on 2012-07-20
> **MoebusNet said:**
> I used this for my Lubuntu 12.04 installation: 

press> alt+f2
type> gksudo leafpad /etc/xdg/lxsession/Lubuntu/autostart

add your " @synclient MaxTapTime=0 "

thats the global for lubuntu session.

I found this at:

[http://ubuntuforums.org/showthread.php?t=1457053](http://ubuntuforums.org/showthread.php?t=1457053)
Hi,

+1 . I do the same thing. 
Give the command ```
synclient
``` and see what value affects the touchpad click . I think its TapButton , but i am not sure. 
Then add it to autostart and you will be fine. 
Thanks

---

### Post by 2CV67 on 2012-07-21
Thanks everybody - it is working fine now.

Some details:
The Lubuntu documentation on this 
[https://help.ubuntu.com/community/Lubuntu/KeyboardMouse](https://help.ubuntu.com/community/Lubuntu/KeyboardMouse)
says to edit *~/.config/lxsession/Lubuntu/autostart* - but I don't have that file to edit. (Documentation needs updating?)

I had found thread 
[http://ubuntuforums.org/showthread.php?t=1457053](http://ubuntuforums.org/showthread.php?t=1457053) (mentioned in original post) 
but had not tried the critical part: *edit /etc/xdg/lxsession/Lubuntu/autostart.*
I do have that file, so I opened it as root & added the line *@synclient MaxTapTime=0* & saved.

After reboot, touchpad clicking is disabled & I am happy!

I would have been even happier with a simpler & more obvious GUI method, of course...

---

### Post by Kevin McCready on 2012-07-21
To turn my touchpad on or off I use
off =
sudo modprobe -r psmouse

to disable touchpad create a file  
sudo leafpad /etc/modprobe.d/blacklist-touchpad.conf
add: 
blacklist	psmouse
save. Reboot.

then to enable the touchpad again:
sudo modprobe psmouse

---

### Post by NikTh on 2012-07-21
> **Kevin McCready said:**
> To turn my touchpad on or off I use
off =
sudo modprobe -r psmouse

to disable touchpad create a file  
sudo leafpad /etc/modprobe.d/blacklist-touchpad.conf
add: 
blacklist    psmouse
save. Reboot.

then to enable the touchpad again:
sudo modprobe psmouse

Hi , 
sorry that i post in this solved thread again , but the configuration that you provide will disable completely the touchpad . 
OP want to disable only touchpad click
Also i  think it its more easier with one simple command in terminal 
```
echo '*@synclient MaxTapTime=0' | sudo tee -a **/etc/xdg/lxsession/Lubuntu/autostart*
```Regards

---

### Post by 2CV67 on 2012-07-21
What a pity I can't just GUI:
> Preferences > Input Device Preferences > Touchpad > Tap > Deactivate...

Without having to find or memorise all this stuff about @synclient, sudo leafpad, blacklist-touchpad etc etc.

No?

In Windows7 on the same PC, I easily found:
Control Panel > Mouse Properties > Elan Smart Pad > Tapping > Enable > Uncheck
Requires no training, no forum, no memory...

Sigh...

But thanks again for the help, guys!

---

### Post by MG&amp;TL on 2012-07-21
> **2CV67 said:**
> What a pity I can't just GUI:
> Preferences > Input Device Preferences > Touchpad > Tap > Deactivate...

Without having to find or memorise all this stuff about @synclient, sudo leafpad, blacklist-touchpad etc etc.

No?

In Windows7 on the same PC, I easily found:
Control Panel > Mouse Properties > Elan Smart Pad > Tapping > Enable > Uncheck
Requires no training, no forum, no memory...

Sigh...

But thanks again for the help, guys!

Developers (in general) don't read the forums. If that's something you want done, drop it on the mailing list.

---

### Post by sudodus on 2012-07-21
[QUOTE=MG&TL12120349]Developers (in general) don't read the forums. If that's something you want done, drop it on the mailing list.[/QUOTE]
+1
or at [[COLOR="Red"]_http://brainstorm.ubuntu.com/_[/COLOR]]("http://brainstorm.ubuntu.com/") :-)

---

### Post by buskerjoe on 2012-09-11
i upgraded to ubuntu 12.4 and have spent 20-30% of my online time pressing "ctrl z" to undo problems caused by erratic, jumpy cursor. i will never never again accept an offer to upgrade; it has caused me untold grief through the years, every single time i do it!

   i've been to Absolute Beginner Talk, and my complaint about both there and here is:

  almost everyone involved in these conversations seems to hold degrees in computer engineering! what about woodcutters, streetsingers, seamstresses.... you know, we do exist. we use computers, and are attracted to the ubuntu philosophy and idea. but it can be discouraging, rather than empowering. a few of us are stubborn or unimaginative enough or rut-prone enough to persist. but a potentially great idea is restricted to a relatively tiny sub-culture.
  i wish they had english speakers as part of the team, to put some of this into language accessible to Everyman.   anyway.. back to the cursor... i will find someone to emply some of the advanced solutions i've encountered. they're over my head, needlessly complex it seems to this citizen streetsinger revolutionary.

---

