---
title: "wifi completely borked in kubuntu"
date: 2011-06-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by buzzmandt on 2011-06-11
todays updates and todays daily build wifi is completely gone. just my card or others have this too? I have Atheros AR242x

---

### Post by cpatrick08 on 2011-06-12
> **buzzmandt said:**
> todays updates and todays daily build wifi is completely gone. just my card or others have this too? I have Atheros AR242x
i am running kubuntu 11.10 and my intel pro wireless 3945 is not working glad to know it is not just me hope it is fixed soon

---

### Post by cariboo on 2011-06-12
Can either of you connect via wireles using the instructions [here]("http://ubuntuforums.org/showthread.php?t=571188")?

---

### Post by xeizo on 2011-06-12
Normal network(wired) disappeared as well for me. I thought it was me installing the 3.0.0-rc2 kernel simultaneously that borked things.

The mainline Oneiric rc2-kernel couldn't run nvidia-current, despite tweaking files according to previous posts, so I had to compile my own rc2-kernel which worked fine with the new patched 275.*.*-nvidia. But network disappeared.

It seems it was todays updates(I did them) instead.

Anyway, I solved the issue by reverting to a safe-boot command line and removing all files in /tmp and /var/tmp plus all hidden folders and hidden conf-files in /home/"Me" and /root using Midnight Commander as su. Reboot. Everything working again!

I forced KDE to auto reconfigure itself using the above method, which apparently was one way of solving it. I have no idea what was the actual borked component.

Anyway, 3.0.0-rc2 and the latest Nvidia up and running, sweet!  :)

---

### Post by jerrylamos on 2011-06-12
Not on kubuntu here, but wireless has been in bad shape last couple of days on Acer Aspire one netbook.  Finally got going by hooking up wired interface then doing update & upgrade on 12 June, on top of 10 June daily build - the last one available.

Removed wired interface & rebooted wireless working.  At least until the next update...

Jerry

---

### Post by buzzmandt on 2011-06-12
still not working here with todays updates, i'll get tomorrows update and check back in

---

### Post by Hershey on 2011-06-14
Updates pulled in a new version of plasma-widget-networkmanagement today. My wifi is working again (eeepc 1000H).

---

### Post by buzzmandt on 2011-06-14
thank you hershey, will try asap

---

### Post by xanas3712 on 2011-08-20
Looks like it's broken again, as it sees aps but when I try to connect to any it shows  a little checkmark and five bars but then just blinks back to no access.

---

### Post by buzzmandt on 2011-08-20
not having any issues here, 3 laptops and a desktop all wireless.

this laptop is now a new install as of yesterdays daily build, all the rest are continuous updates from the start of this dev cycle

grab you new daily and try out the live and see if it's still giving you a fit.
[http://cdimage.ubuntu.com/kubuntu/daily-live/current/](http://cdimage.ubuntu.com/kubuntu/daily-live/current/)

Also what wireless card do you have as i think all of these except for one is atheros
```
lspci | grep Wireless
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
buzzmandt@buzzmandt-Compaq-Presario-CQ60-Notebook-PC:~$ 

```

---

### Post by xanas3712 on 2011-08-20
I'll try a new livecd.  Does anyone know how to get older kernel if that's the problem?  At the hotel I didn't notice an issue but I think that was because it was unsecured wireless, but all of a sudden when I got home with my AP I can't get a connection.  Basically, kubuntu shows the AP but when I attempt to connect it blinks off and then on again.

WHen I tried to follow manual instructions for accessing AP via console, I get from iwpriv "wlan0 no private ioctls."

So I think iwlagn (the module used for my card) is borked or something.

lspci shows this:
03:00.0 Network controller: Intel Corporation WiFi Link 5100

On the kernel question, currently I'm running 3.0.0.8 and 3.0.0.7 doesn't let wifi work either. I think when wifi was working before I left I was running 3.0.0.6

(I've been trying kernel ppa but all of those kernels don't seem to get me into kdm, not sure why... no errors show in Xorg.0.log but I get a bunch of messages on startup that are udev errors with any of the mainline kernels I've tried so far).

---

### Post by xanas3712 on 2011-08-20
Hmm.. well wifi works on the livecd and iwpriv still returns "no private ioctls" so apparently I guess those aren't connected.  But I have idea where a log is placed for this kde network manager to find out what is actually wrong with my install.  

But apparently however it connects it doesn't require iwpriv to work as I'm posting from it on wifi now with the livecd on usb stick.

[http://pastebin.com/me8kp0Z6](http://pastebin.com/me8kp0Z6) is what I get right now from the iwlagn module while it's working...



Edit: 
Rebooted, tried moving home directory, removing /tmp/* and /var/tmp/* and that didn't work
Tried wicd, this "tries" harder, but doesn't work.  It does seem like it's going to connect for awhile but fails at the end saying bad password (it's not, I have an asus transformer working with the same password, and have looked at it closely and retyped/etc.)

I'm trying wpa_supplicant now with
network={
ssid="myssid"
key_mgt=WPA-PSK
pairwise=CCMP TKIP
group=TKIP
psk="myssidspassword"
}

For group and pairwise I got the values using iwlist scan (group showed only TKIP but pairwise should CCMP TKIP).  I have seen some configs that list proto=RSN and have tried with and without that (and with proto=WPA).

The command I'm using is sudo wpa_supplicant -iwlan0 -c/etc/wpa_supplicant.conf -dd -Dwext > test (I'm also trying it with Dnl80211 and that doesn't seem to work either.

The contents of test are here:

[http://pastebin.com/XVQA7aLS](http://pastebin.com/XVQA7aLS)

---

### Post by buzzmandt on 2011-08-20
have you tried reinstalling key components?  assuming that you can connect wired, if not i take it back ](*,)
```
sudo apt-get install network-manager plasma-widget-networkmanagement --reinstall
```

---

### Post by xanas3712 on 2011-08-20
I can connect wired, and will try to reinstall those, if not though I guess I'll just reinstall the OS on this thing.  I have spent enough time it was probably worth it to do that, but I know I had to deal with the whole nouveau -> nvidia driver issues last time I did.  I think that's probably easier to solve than this though.

Edit:
Ugh.. well, going to try reinstalling from the latest livecd I guess.  I really don't like doing this because it doesn't help my understanding of how this occurs at all, but I'm totally out of options.  There doesn't seem to be any further information and I've already read a lot about wpa_supplicant/etc. so I don't think there is anywhere else for me to go from here. 

The card definitely comes up, it doesn't seem to be an issue with the module.  It can scan, but it just can't authenticate using any software I have and nothing logs sufficiently to say why, I think this is probably because it's expected for the AP to do something in return and it just doesn't because for whatever reason the broadcast back to it is wrong.. I just don't have any clue why.

I get wlan0: authenticate with... (try1) in dmesg, then wlan0: associatied, then wlan0: diassociating from ... by local choice (reason=3) and that's it. 

On wpa_supplicant I get more text but basically the same attempt to associate, then disconnection due to timeout on authentication.    I've tried it with passphrase in quotations and with wpa_passphrase converting it, but nothing seems to work.

Edit2: Actually, I'm resizing a partition, I'll run the new one separately so that later if I have more time I can try to figure out what is different/wrong about it in case it could possibly help someone else.  It bothers me to give up on anything...

Edit3: System is working fine with the new install, so it's not just the livecd itself that worked fine.  I did have to go through the nouveau vs nvidia driver thing for a bit again, which requires removing nouveau, blacklisting nouveau (because it's not actually entirely removed when you remove it), then installing nvidia-current.

---

