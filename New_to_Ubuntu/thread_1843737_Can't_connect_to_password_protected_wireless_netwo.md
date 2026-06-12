---
title: "Can't connect to password protected wireless network"
date: 2011-09-13
forum: New to Ubuntu
---

### Post by CommuneOfLoon on 2011-09-13
I originally posted this to Networking & Wireless, but realized since I don't even know how to change the router channel, that maybe this is a better place for me to post.

I just moved to a new place, and I'm having trouble connecting to the  wireless network setup. The password for the network works fine for  getting a Mac and Ubuntu 10.04 on my laptop connected, but the Ubuntu  10.04 on my desktop just asks for the password, and then tries to  connect for a couple of minutes before asking for the password again.  The password is definitely correct. I'm using a external Belkin  46D4050v2, which I previously configured and got working. I'm trying to  connect to a Netgear Wireless-G Router WGR614v9. 

I know there's probably some command line output that would be useful to  add here, but I don't know what, so please let me know and I will post  it. 

Thanks.

---

### Post by Dreamer Fithp Apprentice on 2011-09-14
I have no idea what the source of your problem is but until you solve it, have you considered just connecting the desktop to the router with a cable? The ones I've used had a socket for an ethernet cable and the cabled connection, unlike the wireless connections, did NOT require a password, so if it is the password recognition that is for some reason going wrong, that should bypass the problem. It shouldn't even ask for one. Not sure all routers work the same but I've had 2 and they both worked that way.

Also I suspect it will be a more reliable and slightly faster connection. I could be wrong. Stranger things have happened.

---

### Post by lisati on 2011-09-14
I have a WGR614V7 that I sometimes use and haven't had a problem in a long time.

A couple of possibilities: 1) does the request for a password mention anything about a "keyring"? 2) Is MAC filtering active on the router? 3) Is one of your devices using WEP and the other WPA?

---

### Post by fdrake on 2011-09-14
can you please run a scan of your wifi spot, and post the results for the follwing commands:
```

sudo iwlist scan
nm-tool
less /var/log/syslog | grep -i wpa

```

also tell us what's the name of your essid network.

ps; if you are using wpa encryption make sure use either wpa or wpa2 do not select mix mode. and try if that solves your problem.

---

### Post by dfarrell07 on 2011-09-14
This is obvious, but solves lots of issues of this nature: reboot your modem, router and computer. Good luck :)

---

### Post by gandaran on 2011-09-14
> but the Ubuntu 10.04 on my desktop just asks for the password, and then tries to connect for a couple of minutes before asking for the password again
most likely wireless driver/firmware problem, post the details of wireless chipset and if you have installed the drivers.

---

### Post by CommuneOfLoon on 2011-09-14
Firstly, thanks for all replies on this! The community here is the biggest reason I'm still on Ubuntu.

Other possibly useful info: I followed [bk's instructions in post #2]("http://ubuntuforums.org/showthread.php?t=1509403") to originally get my adapter working almost a year ago. The wireless router was already set up when I moved in, so I do not know it's configuration.

> **Dreamer Fithp Apprentice said:**
> I have no idea what the source of your problem is but until you solve it, have you considered just connecting the desktop to the router with a cable? 

I have thought of this, and may well come back to it, but I figured trying to fix the wireless problem might be useful as a learning experience (I also don't have any ethernet cables at the moment).

> **lisati said:**
> A couple of possibilities: 1) does the request for a password mention  anything about a "keyring"? 2) Is MAC filtering active on the router? 3)  Is one of your devices using WEP and the other WPA?

1. No.
2. I don't know; how would I check this?
3. By devices do you mean the router and adapter? Based on the below, looks like the router I want is using WPA, but I don't know how to check this for my adapter (assuming that is what you are referring to).

> **fdrake said:**
> can you please run a scan of your wifi spot, and post the results for the follwing commands:
```

sudo iwlist scan
nm-tool
less /var/log/syslog | grep -i wpa

```also tell us what's the name of your essid network.

ps; if you are using wpa encryption make sure use either wpa or wpa2 do  not select mix mode. and try if that solves your problem.

For ```
sudo iwlist scan
``` ("****" is what I'm trying to connect to):
```

Version:1.0 StartHTML:0000000167 EndHTML:0000005111 StartFragment:0000000457 EndFragment:0000005095    	 	 	 	 	 	  lo        Interface doesn't support scanning.  
 

 eth0      Interface doesn't support scanning.  
 

 wlan0     Scan completed :  
           Cell 01 - Address: 00:1E:2A:7E:BE:1A  
                     Protocol:802.11b/g/n  
                     ESSID:"*****"  
                     Mode:Managed  
                     Channel:7  
                     Quality:37/100  Signal level:-75 dBm  Noise level:-97 dBm  
                     Encryption key:on  
                     Bit Rates:54 Mb/s  
           Cell 02 - Address: 00:24:B2:0F:75:B2  
                     Protocol:802.11b/g  
                     ESSID:"****"  
                     Mode:Managed  
                     Channel:11  
                     Quality:100/100  Signal level:-39 dBm  Noise level:-97 dBm  
                     Encryption key:on  
                     Bit Rates:54 Mb/s  
                     IE: WPA Version 1  
                         Group Cipher : TKIP  
                         Pairwise Ciphers (2) : CCMP TKIP  
                         Authentication Suites (1) : PSK  
                     IE: IEEE 802.11i/WPA2 Version 1  
                         Group Cipher : TKIP  
                         Pairwise Ciphers (2) : CCMP TKIP  
                         Authentication Suites (1) : PSK  
 
```



For ```
nm-tool
```:

```


 NetworkManager Tool  
 

 State: connecting  
 

 - Device: eth0 -----------------------------------------------------------------  
   Type:              Wired  
   Driver:            r8169  
   State:             unavailable  
   Default:           no  
   HW Address:        1C:6F:65:4B:0E:1F  
 

   Capabilities:  
     Carrier Detect:  yes  
     Speed:           10 Mb/s  
 

   Wired Properties  
     Carrier:         off  
 

 

 - Device: wlan0  [Auto ****] ----------------------------------  
   Type:              802.11 WiFi  
   Driver:            usb  
   State:             connecting (need authentication)  
   Default:           no  
   HW Address:        00:22:75:A2:CD:85  
 

   Capabilities:  
 

   Wireless Properties  
     WEP Encryption:  yes  
     WPA Encryption:  yes  
     WPA2 Encryption: yes  
 

   Wireless Access Points  
     ****: Infra, 00:24:B2:0F:75:B2, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2 
     *****:       Infra, 00:1E:2A:7E:BE:1A, Freq 2442 MHz, Rate 54 Mb/s, Strength 31 WEP  
 
```

Nothing came up for ```
less /var/log/syslog | grep -i wpa
```, but perhaps I don't understand how this is supposed to be input.

When trying to sign on to the network or edit connections, WPA & WPA2 are the only options.

> **dfarrell07 said:**
> This is obvious, but solves lots of issues of  this nature: reboot your modem, router and computer. Good luck :smile:

Haha, yes, gave this a try, no luck. Interestingly, though (cause I had to try it again), my adapter still was recognizing and trying to connect to the network even when I unplugged it. 

> **gandaran said:**
> most likely wireless driver/firmware problem,  post the details of wireless chipset and if you have installed the  drivers.

I don't know what the wireless chipset is. I'm pretty sure the driver was installed w the instructions I link to at the top of this post.



Thanks, again!

---

### Post by gandaran on 2011-09-14
> I don't know what the wireless chipset is. I'm pretty sure the driver was installed w the instructions I link to at the top of this post.
from the link you posted I think it's a ralink chipset,
lets check which driver is loaded when the adapter is connected, type in terminal
```
lsmod
``` 
paste here all output

---

### Post by fdrake on 2011-09-14
the fact that less "/var/log/syslog | grep -i wpa" does not out anything suggest me that you do not have a wpasupplicant installed.
run this command please:
```

sudo aptitude install wpasupplicant wpagui libengine-pkcs11-openssl  libc6 libdbus-1-3 libnl1 libpcsclite1 libreadline6 libssl0.9.8 lsb-base adduser
sudo apt-get update && sudo apt-get upgrade

```
reboot and try again to connect.

also i'd like to point out that you are using mixed mode of wpa and wpa2 encryption. once you are able to connect to your router go to wireless security and choose 1 only of the 2 encryptions. this will make your connection more stable.

---

### Post by h4x0l2 on 2011-09-14
2 things I can see that may be the issue...

1) make sure the USB cable is alright and seated properly... dumb, but not to be overlooked.

2) while you are in the "trying to connect" mode go to the web browser and type in 192.168.1.1 and if you get a popup asking for a login, you are connected with the router, and then it kicks you out possibly due to an IPv6 error. if that is the case, go to Administration>Network Tools - select your device and disable IPv6.


I had the IPv6 headache, then I got this to fix it: [http://www.google.com/products/catalog?client=ubuntu&channel=fs&q=zew2500p&oe=utf-8&um=1&ie=UTF-8&tbm=shop&cid=13010890668535934823&sa=X&ei=EulwTtqDDqne0QHxk5WkCg&ved=0CCAQ8wIwAQ](http://www.google.com/products/catalog?client=ubuntu&channel=fs&q=zew2500p&oe=utf-8&um=1&ie=UTF-8&tbm=shop&cid=13010890668535934823&sa=X&ei=EulwTtqDDqne0QHxk5WkCg&ved=0CCAQ8wIwAQ)

---

### Post by grahammechanical on 2011-09-14
When you first try to make a wireless connection you are asked to authenticate by entering the wireless (router pass phrase - not yout log in password) and then selecting an encryption mode, which can be WEP or WPA.

If the router is set to WPA WPA2 then network manager must also be set to WPA WPA 2. The two devices (the router and your computer) must match.

The print out from the nm-tool shows that network manager is working with your wireless adapter because it is detecting in range wireless networks and identifying the encryption methods used by those wireless devices.

You can click the network icon and select Edit Connections and from there you can check out the connection to see if you are using the correct pass phrase and correct encryption method.

Network manager remembers the pass phrase, even incorrect ones, and it might be trying to connect with the wrong pass phrase or encryption method.

Sometimes it works when you delete any connection that you have put in and then allow Network manager to start afresh.

Regards.

---

### Post by CommuneOfLoon on 2011-09-14
> **gandaran said:**
> from the link you posted I think it's a ralink chipset,
lets check which driver is loaded when the adapter is connected, type in terminal
```
lsmod
```paste here all output

```

Version:1.0 StartHTML:0000000167 EndHTML:0000004296 StartFragment:0000000457 EndFragment:0000004280                                   Module                  Size  Used by  
 binfmt_misc             7960  1  
 snd_hda_codec_atihdmi     3023  1  
 snd_hda_codec_realtek   279008  1  
 snd_seq_dummy           1782  0  
 snd_seq_oss            31191  0  
 snd_seq_midi            5829  0  
 snd_rawmidi            23420  1 snd_seq_midi  
 snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi  
 snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event  
 snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq  
 snd_hda_intel          25805  2  
 snd_hda_codec          85759  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel  
 snd_hwdep               6924  1 snd_hda_codec  
 snd_pcm_oss            41394  0  
 snd_mixer_oss          16299  1 snd_pcm_oss  
 snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss  
 snd_timer              23649  2 snd_seq,snd_pcm  
 fbcon                  39270  71  
 tileblit                2487  1 fbcon  
 font                    8053  1 fbcon  
 bitblit                 5811  1 fbcon  
 softcursor              1565  1 bitblit 
 ppdev                   6375  0  
 rt2870sta             525366  1  
 fglrx                2353486  31  
 vga16fb                12757  1  
 parport_pc             29958  1  
 vgastate                9857  1 vga16fb 
 snd                    71283  16 snd_hda_codec_realtek,snd_seq_oss,snd_rawmidi,snd_seq,snd_seq_device,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer 
 serio_raw               4918  0  
 soundcore               8052  1 snd  
 snd_page_alloc          8500  2 snd_hda_intel,snd_pcm  
 i2c_piix4               9639  0  
 edac_core              45423  0  
 edac_mce_amd            9278  0  
 shpchp                 33711  0  
 lp                      9336  0  
 parport                37160  3 ppdev,parport_pc,lp  
 r8169                  39714  0  
 ohci1394               30260  0  
 usbhid                 41116  0  
 hid                    83888  1 usbhid  
 floppy                 63156  0  
 mii                     5237  1 r8169  
 ahci                   38030  2  
 ieee1394               94771  1 ohci1394  
 pata_atiixp             4209  0  
 
```> **fdrake said:**
> the fact that less "/var/log/syslog | grep -i  wpa" does not out anything suggest me that you do not have a  wpasupplicant installed.
run this command please:
```

sudo aptitude install wpasupplicant wpagui libengine-pkcs11-openssl   libc6 libdbus-1-3 libnl1 libpcsclite1 libreadline6 libssl0.9.8 lsb-base  adduser
sudo apt-get update && sudo apt-get upgrade

```reboot and try again to connect.

also i'd like to point out that you are using mixed mode of wpa and wpa2  encryption. once you are able to connect to your router go to wireless  security and choose 1 only of the 2 encryptions. this will make your  connection more stable.

Can't download those things because not connected to internet. I accessed the router (EDIT: I meant modem, not router; I don't know how to access the router, 192.168.1.1 doesn't work) through the MacBook I'm using, and I didn't see any place to change the encryption. Any ideas how to do this?

> **h4x0l2 said:**
> 2 things I can see that may be the issue...

1) make sure the USB cable is alright and seated properly... dumb, but not to be overlooked.

2) while you are in the "trying to connect" mode go to the web browser  and type in 192.168.1.1 and if you get a popup asking for a login, you  are connected with the router, and then it kicks you out possibly due to  an IPv6 error. if that is the case, go to Administration>Network  Tools - select your device and disable IPv6.


I had the IPv6 headache, then I got this to fix it: [http://www.google.com/products/catalog?client=ubuntu&channel=fs&q=zew2500p&oe=utf-8&um=1&ie=UTF-8&tbm=shop&cid=13010890668535934823&sa=X&ei=EulwTtqDDqne0QHxk5WkCg&ved=0CCAQ8wIwAQ](http://www.google.com/products/catalog?client=ubuntu&channel=fs&q=zew2500p&oe=utf-8&um=1&ie=UTF-8&tbm=shop&cid=13010890668535934823&sa=X&ei=EulwTtqDDqne0QHxk5WkCg&ved=0CCAQ8wIwAQ)

USB secure; I have wireless network options, just can't connect. 

Nothing came up when I tried to access the router. Just to check, I went to Edit Connections for the network and IPv6 was set to "Ignore".

---

### Post by gandaran on 2011-09-14
> rt2870sta             525366  1 
you do have the right driver loaded, sorry to have wasted your time

---

### Post by h4x0l2 on 2011-09-14
> **CommuneOfLoon said:**
> Can't download those things because not connected to internet. I accessed the router (EDIT: I meant modem, not router; I don't know how to access the router, 192.168.1.1 doesn't work) through the MacBook I'm using, and I didn't see any place to change the encryption. Any ideas how to do this?



USB secure; I have wireless network options, just can't connect. 

Nothing came up when I tried to access the router. Just to check, I went to Edit Connections for the network and IPv6 was set to "Ignore".


Try enabling the IPv6.. just to rule it out.

as for editing the router settings, plug it in ethernet and 192.168.1.1.. should get you into it.

---

### Post by CommuneOfLoon on 2011-09-14
> **grahammechanical said:**
> When you first try to make a wireless connection you are asked to authenticate by entering the wireless (router pass phrase - not yout log in password) and then selecting an encryption mode, which can be WEP or WPA.

If the router is set to WPA WPA2 then network manager must also be set to WPA WPA 2. The two devices (the router and your computer) must match.

The print out from the nm-tool shows that network manager is working with your wireless adapter because it is detecting in range wireless networks and identifying the encryption methods used by those wireless devices.

You can click the network icon and select Edit Connections and from there you can check out the connection to see if you are using the correct pass phrase and correct encryption method.

Network manager remembers the pass phrase, even incorrect ones, and it might be trying to connect with the wrong pass phrase or encryption method.

Sometimes it works when you delete any connection that you have put in and then allow Network manager to start afresh.

Regards.

Gotcha. Then yes, they match; I'm trying to connect w "WPA & WPA2 Personal" and it looks like the router is set up w WPA and WPA2.

I've tried deleting the connection a few times, and password is definitely correct.

---

### Post by CommuneOfLoon on 2011-09-14
> **gandaran said:**
> you do have the right driver loaded, sorry to have wasted your time

No need to apologize, I appreciate you trying to help diagnose the problem. 

Out of curiosity, how do you know it's the correct driver? Is that just the generic correct driver for wireless? (just trying to learn what some of this stuff means)

> **h4x0l2 said:**
> Try enabling the IPv6.. just to rule it out.

as for editing the router settings, plug it in ethernet and 192.168.1.1.. should get you into it.

Okay, just got a cable, I'll give it a try.

Setting IPv6 to Automatic did not work.

---

### Post by CommuneOfLoon on 2011-09-14
Okay, so using the ethernet cable, I was able to install those things you suggested, fdrake (out of curiosity, what were the programs?). Restarted, but still not able to access the wireless network. Also, plugging the ethernet into the LAN modem jack, I was still not able to access the modem using 192.168.1.1.

---

### Post by gandaran on 2011-09-14
> Out of curiosity, how do you know it's the correct driver? Is that just the generic correct driver for wireless? (just trying to learn what some of this stuff means)
the instructions on the link you used to fix the adapter all you had to do is blacklist the wrong loaded _rt2800usb_ driver and load the correct _rt2870sta_ driver that works with the adapter, there isn't any install, Ubuntu already has the ralink drivers built in but in your case was loading the wrong driver.

---

### Post by gandaran on 2011-09-14
> Gotcha. Then yes, they match; I'm trying to connect w "WPA & WPA2 Personal" and it looks like the router is set up w WPA and WPA2.
set up with WPA and WPA2? you mean the dreaded mix of the two?
if so then that could be the problem.

edit:
read posts #15 and #16 on your link you used to fix the adapter about WPA issues with the ralink driver.

---

### Post by h4x0l2 on 2011-09-14
> **gandaran said:**
> set up with WPA and WPA2? you mean the dreaded mix of the two?
if so then that could be the problem.


^--- agreed.


If you can't get into the router via 192.168.1.1 with an Ethernet connection, theres a few things to look at:

1) unplug everything from the router, and replug it in. POWER LAST
2) Make sure that when you have the Ethernet plug to the computer, its not in #1... I used #2. 
3) Make sure the lan cards IP doesn't conflict with the router IP. If that happens, it won't do anything since it can't "connect to itself".


if all else fails:
4) Return the router and buy linksys. I had the router that you have, ran into connectivity issues with Ubuntu, then I changed out the router for a linksys and it automagically connected. On another computer running fedora, I got it to connect to the Netgear router buy getting a new wireless card.


One thing to know about Ubuntu from experience: Buy stuff that is about 1 year old if you plan on having it automagically connect. Odds are, the compatibility issues have already been worked out for the release.




This isn;t to say you can't get this router to work, because you can by doing as gandaran stated by blacklisting a certain driver. But if you are a new user and don't feel like dealing with hassle over wireless, go with linksys routers over 1 year old, and adapters that are 1-2 years old.

Thats just my 2c.



[http://support.netgear.com/app/products/model/a_id/2591](http://support.netgear.com/app/products/model/a_id/2591)

---

### Post by CommuneOfLoon on 2011-09-14
It's not my router, so that's not an option, but I do plan on getting a Linksys from the Ubuntu "approved" list when I move out.

Unplugging everything, and then replugging (power last in both cases) did not help. I also only have one ethernet port on my computer. *That said*, I just found the proper address on the back of the modem (and yes, I feel stupid, since I've looked for it several times already and missed it). Switched the encryption to just one of them, and now wireless is working!

In short, having it set to WPA & WPA2 was causing the issue.

Thanks, all, for helping me diagnose and fix this issue.

---

### Post by anewguy on 2011-09-14
Whose router?  Ask them if there is MAC filtering on since this would prevent you from connecting to the router wirelessly even with the correct passphrase/password.  If so, they should be able to administer the router and add your MAC address.  If this is a single-family dwelling, and you are the only one using the router, you could always reset the router and put everything in the way you want it.  If it's not yours or it's for a multi-family dwelling, then you need to contact the person responsible for the router.  Remember: the encryption type and passphrase/password must match, and if MAC filtering is "on" on the router and your computer has never connected wirelessly to the router before you will need your MAC address added to the list in the router.

It's been recommended, and I would definitely be sure you have cleared previous connection attempts:

- right click on the network manager icon
- click on "Edit Connections"
- delete any entries in that window (as mentioned, they do sometimes replace your own manual attempt so the password/passphrase doesn't "take".  I've had this happen in the past myself.

It should also be noted that the address is not always 192.168.1.1 even with the brand in question, and therefore the router shouldn't be deemed as bad just because that doesn't work.  As an example, if you have a setup as we have here the address is changed:  DSL modem with built-in ethernet ports using the 192.168 range.  A wireless router plugged into that ends up with a range of 10.0.  So, to connect to the wireless router "console" I have to connect to 10.0.0.1, not 192.168.1.1.

Dave ;)

---

