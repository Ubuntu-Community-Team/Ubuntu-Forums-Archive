---
title: "wifi key problem ubuntu 9.04"
date: 2012-04-29
forum: New to Ubuntu
---

### Post by stowning on 2012-04-29
I just loaded 9.04 on an old Dell Latitude C610 laptop - I chose this because of a post saying 9.04 worked well and later versions were a bit memory hungry (the laptop only has 512MB RAM). It powered up fine and picked up my WiFi network (from a MiFi broadband dongle from Three.ie). I clicked on the 'connect' button and got the security menu. It has a box for 'Wireless Security' with options for WEP 40/128 bit key, WEP 128 bit Passphrase, LEAP or Dynamic WEP (802.1x), it has a box to enter the key then a box for WEP Index and finally a box for Authentication with choice of Open System or Shared Key. Below this are two buttons - a 'cancel' button which is active and a 'connect' button which is inactive. My WiFi key is 8 characters - when I enter it in the key box I expected the 'connect' key to become active but it doesn't. No matter what combination of selections I make I can't get this button to activate. I suspect that I need a WPA capability but I'm not sure on this. Any ideas on how I can set the WiFi key correctly and connect to the network?

---

### Post by Peripheral Visionary on 2012-04-29
9.04 is no longer supported. My old hand-me-down Dell has 512 RAM as well and runs Xubuntu just fine! The newest version has much fewer wifi issues, and the new kernel supports much more hardware. Try out Xubu 12.04 on a LiveCD first. It should automagically detect your wifi and most other peripherals. If it works on LiveCD, it'll likely work installed (only much faster than a LiveCD. Enjoy!

---

### Post by kostkon on 2012-04-29
Security-wise, 12.04 is a much better choice. As *Peripheral Visionary* already suggested, try Xubuntu or Lubuntu.

---

### Post by stowning on 2012-04-30
I tried installing 12.04 - at one point it asks to connect to the network. I clicked on this and it finds the correct network and asks for the password (presumably the WiFi key) when I enter this it spins the network icon in the top right hand corner then comes back asking for the password again - it did this 3 times before I cancelled and opted not to connect to the network during install. It then went on and showed the Install screen followed by the 'Your web experience' and 'Instant Messaging' info boxes then the Install box disappears and I was presented with an 'Installer irrecoverable error' message. I tried re-installing and it goes through the same sequence but no 'irrecoverable error' message - instead it accesses the CD a few more times then hangs with a grey screen. How should I proceed?

---

### Post by stowning on 2012-04-30
Just searched for 12.04 install failures and found that the install needs a network connection which I don't have. I'm now trying the alternate install which doesn't need the network. Still not sure why the network won't accept the WiFi password but will get to this if/when the install completes.

---

### Post by mörgæs on 2012-04-30
You will get the best results with wired internet access no matter which ISO you are using.

Are you trying Lubuntu now?

---

### Post by stowning on 2012-04-30
Tried using the 12.04 alternate install version - it loads up to the point where it starts to 'Detecting Network Controller' then hangs with a pink screen. Lovely!!!.  Looks like the network is a real problem - the message I got on the previous install with the standard 12.04 was that the controller was a Texas Instrument PCI 1410 PC card Cardbus Controller. The standard install gets further than the alternate install but both fail eventually. IF I could solve the problem of the password then I'm sure the standard install would work. Any ideas on where to go next?

PS. I used Xubuntu 12.04 as the standard download but could only find ubuntu-12.04 for the alternate. I don't have access to any wired network - I only have access through my broadband WiFi connection.

---

### Post by steeldriver on 2012-04-30
Pardon me for jumping in, but are you sure the issue is not just that you are trying to connect a WEP device to a WPA-only network? Your 8-character password sounds more like WPA - have you checked your router's wireless settings?

I run Xubuntu 11.10 on a Thinkpad of the same vintage (X30 / PIII-M / 1G RAM) and gave up on the internal wireless card - it only supports WEP and is only a/b. You could throw in a WPA capable USB or CardBus g/n adapter for a few $$, that's what I have done. 

Hope this helps

---

### Post by stowning on 2012-04-30
Yes I think it is a WPA device - the problem with 9.04 is that there is no setting for WPA only WEP and LEAP (see first post). There is also no way to change any of the 'router' settings as it is a standalone device with a WiFi front end and a broadband connection to a mobile network as a back-end. It's one step up from the standard 'broadband mobile dongle'. I have it working on a laptop running Windows 7 and also a laptop using Ubuntu 11.10 but can't get it working on this third laptop.  I have now tried downloading Lubuntu 12.04 on this laptop and it fails constantly with the message 'general error mounting filesystem - a maintenance shell will now be started'. So went back and re-installed 9.04 succesfully just to make sure I wasn't going insane and hadn't irreparably damaged the system. Then tried running Lubuntu using this stable system - same 'general error mounting file system'.
It's getting late and I'm getting tired - will try running the Ubuntu alternative install from this 'stable' system tomorrow - it shouldn't make any difference but why is 9.04 loading OK (but apparently not supporting WPA) when all the others are failing the install one way or another?

---

### Post by stowning on 2012-04-30
Just re-read Steeldriver's post - I was interpreting it the wrong way (told you I was tired). What you're saying is that the network at the router is WPA but the card in the laptop is only capable of WEP - will check this out and try the fix suggested if this is the case.

---

### Post by ammofreak on 2012-04-30
Hi stowning):P: sounds like a wifi security issue. Also, as suggested by someone else, I always hard wire for installation purposes. Things seem to go a lot better....:)

---

### Post by steeldriver on 2012-04-30
> **stowning said:**
> Just re-read Steeldriver's post - I was interpreting it the wrong way (told you I was tired). What you're saying is that the network at the router is WPA but the card in the laptop is only capable of WEP - will check this out and try the fix suggested if this is the case.

Hi, yes that's exactly what I was trying to say

I've done a bit more googling for ya, it looks like your C610 likely has a TrueMobile 1150 card with a Lucent/Orinoco chipset - with recent drivers it *should* be capable of WPA-PSK but not WPA2, I think. Note that even if you were able to change your wireless settings to WEP  that would be a bad idea from a security PoV - arguably OK to confirm  the issue but not a good long term fix.

Here are a couple of threads that might be relevant

[http://ubuntuforums.org/showthread.php?t=1935133](http://ubuntuforums.org/showthread.php?t=1935133)

[http://ubuntuforums.org/showthread.php?t=1861591]("http://ubuntuforums.org/showthread.php?t=1935133")

I have no idea why you are now having problems mounting the system btw

---

### Post by stowning on 2012-05-02
To support full WPA I've ordered a Dlink USB WiFi dongle - hopefully this will fix the network problem and may also fix the install problem.

---

