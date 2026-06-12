---
title: "Globe Visibility"
date: 2008-10-22
forum: Philippine Team
---

### Post by icodeme on 2008-10-22
May gumagamit  ba dito?

---

### Post by jsgotangco on 2008-10-22
if you're using it with the Huawei e220 modem, it works flawlessly with Linux because the modem driver is already part of the stock kernel

---

### Post by icodeme on 2008-10-23
Hi,

 Thanks for the reply bro.. I am a newb and i don't anything of ths since it's my first time in Ubuntu. I really love use it. Can you please provide me some guideline to do this?

Thank you so much

---

### Post by icodeme on 2008-10-23
> **jsgotangco said:**
> if you're using it with the Huawei e220 modem, it works flawlessly with Linux because the modem driver is already part of the stock kernel


___________________________________
How can I know if I'm using that kind of modem? i just recently purchase globe visibility. yung postpaid po na may sim? Sensya na la tlga ako idea dito

SALAMAT SALAMAT

---

### Post by geobz on 2008-10-28
I'm pretty new with Ubuntu as well (July 2008 ) and recently bought the Globe Visibility Thumb drive HSDPA modem (ZTE MF626). Just wondering if anybody knows how to make it work with Hardy. 

If anybody knows, please show us step by step. I'm just a regular guy fed up with windows and all the trash that keeps flying through them.

Thanks!

---

### Post by icodeme on 2008-10-28
I got hardy and I found some info here: [http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy)

---

### Post by loell on 2008-10-28
we really need more info, hope those users will start posting.

```
dmesg
```

---

### Post by icodeme on 2008-10-28
> **loell said:**
> we really need more info, hope those users will start posting.

```
dmesg
```

What is this code for? Kasi nung inexecute siya, ang haba ng lumabas and it's quite hard to copy paste the result

---

### Post by loell on 2008-10-28
> **icodeme said:**
> What is this code for? Kasi nung inexecute siya, ang haba ng lumabas and it's quite hard to copy paste the result

[what is dmesg]("http://linuxgazette.net/issue59/nazario.html")

---

### Post by icodeme on 2008-10-28
OK.. Here it is. Somehow I believe this is isn't complete coz I can't get it all:

---

### Post by loell on 2008-10-28
so you have that modem? is  it Hauwie or is it the ZTE one? to know.. type,

```
 lsusb 
``` 


And you could, ```
dmesg > mydmesg.txt 
``` to put dmesg into **mydmesg.txt** file , just upload and attach it here.

---

### Post by icodeme on 2008-10-28
I curently don't use it now cause I got myself a smartbro yesterday. Somehow, it is the ZTE dude. The ZTE has an exe file to execute the interface of Globe Visibility and I started this thread to know if there's anything that we can do about this Uwi kasi ako sa probinsiya this friday and I'll need it. :)

---

### Post by loell on 2008-10-28
ok, whenever you have it, just attach it, and do the dmesg and upload-attach the text file,  this is only a work in progress. we'll just try to gather more info for later use.

---

### Post by icodeme on 2008-10-28
Ok. I plugged it and here it goes.

---------------------------------------------------------------


[13774.831634] usb 5-4: new high speed USB device using ehci_hcd and address 6
[13774.978479] usb 5-4: configuration #1 chosen from 1 choice
[13774.984763] scsi5 : SCSI emulation for USB Mass Storage devices
[13774.988599] usb-storage: device found at 6
[13774.988607] usb-storage: waiting for device to settle before scanning
[13776.803114] DoRxHighPower(): RF_ZEBRA, Upper Threshold: 99 LOWER Threshold: 70
[13778.795583] DoRxHighPower(): RF_ZEBRA, Upper Threshold: 99 LOWER Threshold: 70
[13779.984732] usb-storage: device scan complete
[13779.986752] scsi 5:0:0:0: CD-ROM            ZTE      USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 0
[13780.030714] sr1: scsi3-mmc drive: 0x/52x cd/rw xa/form2 cdda tray
[13780.030811] sr 5:0:0:0: Attached scsi CD-ROM sr1
[13780.030863] sr 5:0:0:0: Attached scsi generic sg2 type 5

---

### Post by loell on 2008-10-28
its been identified as a cdrom?

```
[13779.986752] scsi 5:0:0:0: CD-ROM ZTE USB SCSI CD-ROM 2.31 PQ: 0 ANSI: 0
```

---

### Post by icodeme on 2008-10-28
> **loell said:**
> its been identified as a cdrom?

```
[13779.986752] scsi 5:0:0:0: CD-ROM ZTE USB SCSI CD-ROM 2.31 PQ: 0 ANSI: 0
```

Yeah, it is! It opens all the files in a folder. :) Well I don't know what is the difference of smartbro kit from this..

---

### Post by icodeme on 2008-10-28
How bout loading the .exe file from the globe visibility via WINE? hehehe

---

### Post by icodeme on 2008-10-28
Good news bro. It pushed tru. 80% now

---

### Post by loell on 2008-10-29
> **icodeme said:**
> Good news bro. It pushed tru. 80% now

meh.. :tongue:

drivers through wine will never work, it never did. :D

---

### Post by icodeme on 2008-10-29
Got crossover now bro :) But the cursor still is lost when in focus lol! Somehow maybe in Intrepid it'll be fixed.

Still loving Linux.:)

---

### Post by loell on 2008-10-29
can you confirm if the modem is indeed **ZTE MF620**?

by posting your **lsusb** ?

---

### Post by icodeme on 2008-10-29
> **loell said:**
> can you confirm if the modem is indeed **ZTE MF620**?

by posting your **lsusb** ?

Actually it is ZTE MF626 HSDPA

------------------------------
Bus 005 Device 005: ID 19d2:0031  
Bus 005 Device 004: ID 0bda:8187 Realtek Semiconductor Corp. 
Bus 005 Device 003: ID 0402:5602 ALi Corp. Video Camera Controller
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 15ca:00c3  
Bus 001 Device 001: ID 0000:0000

---

### Post by loell on 2008-10-29
you'll gonna have to dive in, with this  instruction.

[http://linuxate.blogspot.com/2008/05/zte-mf620-in-linux.html]("http://linuxate.blogspot.com/2008/05/zte-mf620-in-linux.html")


still waiting for the proper config file for zte-mf626

[http://www.draisberghof.de/usb_modeswitch/bb/viewforum.php?f=3]("http://www.draisberghof.de/usb_modeswitch/bb/viewforum.php?f=3")

---

### Post by icodeme on 2008-10-29
> **loell said:**
> you'll gonna have to dive in, with this  instruction.

[http://linuxate.blogspot.com/2008/05/zte-mf620-in-linux.html]("http://linuxate.blogspot.com/2008/05/zte-mf620-in-linux.html")


still waiting for the proper config file for zte-mf626

[http://www.draisberghof.de/usb_modeswitch/bb/viewforum.php?f=3]("http://www.draisberghof.de/usb_modeswitch/bb/viewforum.php?f=3")

I'm into it. I'll wait for the config file in the forum you provided.
TY

---

### Post by geobz on 2008-11-07
Hey guys,

Pls let me know if you have any luck configuring the MF-626 with Hardy. And if you do, please give me a step by step instruction on how to install it properly.

Super Thanks!

---

### Post by mkone on 2008-11-30
how about for huawei e220. may config na po ba?

---

### Post by loell on 2008-12-01
> **mkone said:**
> how about for huawei e220. may config na po ba?

[http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=74&highlight=e220]("http://www.draisberghof.de/usb_modeswitch/bb/viewtopic.php?t=74&highlight=e220")

---

### Post by riclags on 2008-12-04
> **icodeme said:**
> I got hardy and I found some info here: [http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy)

hi all, will globe visibility work on 8.10 (intrepid) version of ubuntu? i checked the network configuration/manager and under mobile broadband, there were entries for globe telecom, globe telecom (wap), smart and sun.

so me thinks that it will work out of the box with no need to do some technical stuff? or is it wishful thinking? :p i don't want to shell out PhP2.5k and find out it will not work.

any info is appreciated.

---

### Post by mkone on 2008-12-06
it will. tested with 8.10(intrepid)

---

### Post by riclags on 2008-12-07
> **mkone said:**
> it will. tested with 8.10(intrepid)
is this for the postpaid or the prepaid dongle/modem? coz in their website, they have 2 types of usb dongle/modem. thanks.

---

### Post by garybrlow on 2009-01-03
(Huawei E160) it works out of the box on intrepid. Just use the mobile wizard on the network-manager/nm-applet Globe Telecom setting is available but you have to change the Number to *99***1#, remove the APN value, remove username/password (password is persistent just leave it that way). After changing the settings you can now connect to Globe Visibility. The only thing I haven't figured out yet is to lock  the connection to 3g and use Open DNS with the connection. Well other than that its works. :)

---

### Post by dodimar on 2009-01-04
> **garybrlow said:**
> (Huawei E160) it works out of the box on intrepid. Just use the mobile wizard on the network-manager/nm-applet Globe Telecom setting is available but you have to change the Number to *99***1#, remove the APN value, remove username/password (password is persistent just leave it that way). After changing the settings you can now connect to Globe Visibility. The only thing I haven't figured out yet is to lock  the connection to 3g and use Open DNS with the connection. Well other than that its works. :)

If you want to use opendns... you could set that up on Ubuntu's network properties (instead of setting up the dns values on the modem), that works better that setting it up on the modem (as for my experience).

---

### Post by riclags on 2009-01-28
> **garybrlow said:**
> (Huawei E160) it works out of the box on intrepid. Just use the mobile wizard on the network-manager/nm-applet Globe Telecom setting is available but you have to change the Number to *99***1#, remove the APN value, remove username/password (password is persistent just leave it that way). After changing the settings you can now connect to Globe Visibility. The only thing I haven't figured out yet is to lock  the connection to 3g and use Open DNS with the connection. Well other than that its works. :)

hi gary. i have the huawei e160 modem and i tried what you suggested but i still cannot connect. it keeps saying that the connection has been disconnected. when i inserted the dongle, it was installed in ubuntu as e220. is that causing the problem?

thanks.

---

### Post by garybrlow on 2009-02-26
Globe's Visibility configurations has changed somewhat. Try using these settings:
1) Using the wizard use the Globe Telecom default setting.
2) In the Mobile Broadband Tab, leave the Number as is (*99#) do not change it like the 
    previous config (*99***1#). The previous setting works for Windows but fails in 
    X/K/Ubuntu.
3) Remove the Username but leave the Password unchanged. 
4) Remove the APN.
5) Leave the PPP settings unchanged.
6) In the IPv4 Settings Tab, set method to Automatic. Click ok and try the connection.

(Was able to post this using the above configuration.)

---

### Post by Maverick1385 on 2009-02-27
> **garybrlow said:**
> Globe's Visibility configurations has changed somewhat. Try using these settings:
1) Using the wizard use the Globe Telecom default setting.
2) In the Mobile Broadband Tab, leave the Number as is (*99#) do not change it like the 
    previous config (*99***1#). The previous setting works for Windows but fails in 
    X/K/Ubuntu.
3) Remove the Username but leave the Password unchanged. 
4) Remove the APN.
5) Leave the PPP settings unchanged.
6) In the IPv4 Settings Tab, set method to Automatic. Click ok and try the connection.

(Was able to post this using the above configuration.)

wow guys, thanks!

i was contemplating on getting a globe visibility but was wondering if i can make it work on my ubuntu desktop. :) 

i guess it does so im gonna try it for myself.

---

### Post by garybrlow on 2009-03-01
For those who want to use Globe Visibility with OpenDns, I finally figured out the setting to make it work. In my previous post (#35) follow everything until step 3.
Step 4 and onwards, as follows:

4) Instead of removing the APN, replace it with "http.globe.com.ph".
5) Leave the PPP settings unchanged.(No change for step 5)
6) In the IPv4 Settings Tab, do not change the actual default setting 
    "Automatic (PPP) address only". Just replace the default DNS servers with the OpenDNS  
    public ip addresses "208.67.222.222,208.67.220.220". Click ok and try the connection.

Note: You can use the APN part with the full "Automatic (PPP)" setting as well.

---

### Post by iLoveSade on 2009-03-12
It seems that my Globe Visibility mf626 is not detected. Is this supporteD?:(

---

### Post by jepong on 2009-03-12
try mo na nakasaksak na yung usb modem then ON mo pc mo.

ganyan ginagawa ko sa PLDT WeRoam Plan on a ZTE MF622 usb modem. badtrip nga kasi minsan detected sa modem but most of the time usb drive. restart lang me untl makuha cya.

---

### Post by kgpdeveloper on 2009-06-09
I don't like Globe so much but it's interesting to know that visibility works for Ubuntu.

---

### Post by tr3s on 2009-06-14
> **garybrlow said:**
> For those who want to use Globe Visibility with OpenDns, I finally figured out the setting to make it work. In my previous post (#35) follow everything until step 3.
Step 4 and onwards, as follows:

4) Instead of removing the APN, replace it with "http.globe.com.ph".
5) Leave the PPP settings unchanged.(No change for step 5)
6) In the IPv4 Settings Tab, do not change the actual default setting 
    "Automatic (PPP) address only". Just replace the default DNS servers with the OpenDNS  
    public ip addresses "208.67.222.222,208.67.220.220". Click ok and try the connection.

Note: You can use the APN part with the full "Automatic (PPP)" setting as well.

gary, you're the man!!! thanks bro

i've been to a lot of headaches on manual setup using usb_modeswitch and wvdial since i can't find any guide on using the gnome network manager until i found your post. it worked flawlessly, hurrraaay! we just need the right configuration.

by the way, do you know what settings should we use for the smartbro usb dongle?

many thanks again

---

### Post by edibanez on 2009-06-14
Hi... I'm using globe broadband tattoo i think it's huawei e220 and it sometimes work with kde-network-manager but most of the times i'm using wvdial to connect... and just works fine... only problem is you can't get it to fix on 3g signals..

---

### Post by tr3s on 2009-06-14
edibanez, can you post your wvdial.conf? please... thanks

---

### Post by edibanez on 2009-06-14
here is my wvdial.conf entry:
```

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Modem Type = Analog Modem
Baud = 9600
New PPPD = yes
Modem = /dev/ttyUSB0
ISDN = 0
 Phone = *99***1#
 Password = globe
 Username = globe

```

---

### Post by tr3s on 2009-06-14
Now, that worked for me. Thank you

---

### Post by edibanez on 2009-06-14
glad i could help...

---

### Post by londonbabs on 2009-08-10
anybody ever found a way to lock those keys on 3G networks ?
I use O2 mobile broadband on pay as you go with the huawei E160, it works a charm but keeps jumping from a network to another, making the connection wobbly at times, anyone got around this yet ?

---

### Post by pinoyskull on 2009-08-13
There's a workaround, if you have a windows pc setup your usb modem there and lock the settings to use 3G Only, not 3G preferred.  That way when you use it in Ubuntu,  it will use 3G 

Or

Use umtsmon in Ubuntu :)

---

### Post by GeorgeVita on 2009-08-13
Hi, would you like to test the following?> **GeorgeVita said:**
> ...searching internet I found an 'extracted' info for Huawei modems:```
AT^SYSCFG=13,1,3FFFFFFF,2,4 # GPRS only
AT^SYSCFG=2,1,3FFFFFFF,2,4 # GPRS prefered

AT^SYSCFG=14,2,3FFFFFFF,2,4 # 3G ONLY
AT^SYSCFG=2,2,3FFFFFFF,2,4 # 3G prefered
```I tested the above using **wvdial** (my 'All weather' method to connect) and GPRS only (as I never had the 3G > GPRS problem). I can state that my E169 was always in 'green led' sssslllloooowwwww internet connection! (this message posted via GPRS network)...
>>> You can send this command from **wvdial.conf** or any serial terminal program as **minicom**.

Regards,
George

---

### Post by exkludge on 2009-08-18
you can try this:
[http://thespotontheweb.blogspot.com/2009/08/globe-tattoo-diy-antenna.html](http://thespotontheweb.blogspot.com/2009/08/globe-tattoo-diy-antenna.html)

i even tried to use a "llanera" (yeah usually used in cooking lecheplan) for this... and guess what... my e1552 signal stays at WCDMA to HSDPA full bars.
:)

---

### Post by pinoyskull on 2009-08-18
i had my E220 strapped on a 1x2 lumber and inserted an 500ml water bottle to protect the modem from rain then attached 2x5meters USB cable with Booster, got it from CDRking, then attached to my laptop :), always got fullbar on HSDPA.

That's what I used to do before. Now I enjoy my Globe WiMax :D

Note: even if you have fullbar HSDPA that doesnt mean that you have fast internet.

---

### Post by dan.catacutan on 2009-11-23
> **tr3s said:**
> Now, that worked for me. Thank you

[COLOR=SeaGreen]
Hi! I just installed Ubuntu on my laptop. I'm pretty amazed and would really make it as my primary OS. However, I can't connect to the internet using this Globe Visibility Modem e220 (Globe Plan).

Can someone assist me? or give me step by step procedure? I saw a lot of codes, but I don't know how to use it. 

Here's the problem I've been encountering:

When I plug in the usb modem, I see the Network Connection Icon (upper right corner of the screen) blinking and has a rotation icon. and a mesasge will pop up asking if I will allow it always, or no. However, i'm stucked on it. Mouse is moving, but can't click anything. So I have no other choice but to shutdown by pressing the power buttong for 5-7 seconds.

Hope you could assist me on my problem.

Thank you!

Regards,
Dan Catacutan[/COLOR]

---

