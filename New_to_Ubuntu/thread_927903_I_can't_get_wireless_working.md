---
title: "I can't get wireless working"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by ubunt2guy on 2008-09-23
I cannot get my wireless working on my new ubuntu install.

I need a rt73 driver installed manually with terminal and I am way to new to figure out if i am executing any commands correctly or incorrectly.  I used theses instructions and still nothing has happened except that now there aren't any networks detected...

I am extremely frustrated and wasted way too much time going through this convoluted process.


If anyone can help out a noobie that would be great, but til then I'm going to revert back to my windows pc...

cheers

---

### Post by ubunt2guy on 2008-09-23
these instructions:  [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

---

### Post by hyper_ch on 2008-09-23
if it doesn't work out for you then you should use whatever works out for you...

---

### Post by Tatty on 2008-09-23
Are you getting any error messages while you go through the instructions?

Also, are you saying you could see other networks before but not now?  that makes it sound like the driver was working before - could you see but not connect?

---

### Post by ubunt2guy on 2008-09-23
> **Tatty said:**
> Are you getting any error messages while you go through the instructions?

Also, are you saying you could see other networks before but not now?  that makes it sound like the driver was working before - could you see but not connect?

yes i could see all networks (about 4) before and now after a few commands in the terminal they aren't being detected anymore...

I have a feeling that I installed the driver from source, compiled, etc but left out a step.  I dont know which step though...  (This is my first command line experience besides college 101 IT class and i'm a little lost.  Why can't synaptic have the rt73 driver?????!!!)

---

### Post by ubunt2guy on 2008-09-23
well when i installed ubuntu on my laptop i could see about four different networks, including mine, with varying degrees of strength.  My neighbors network, downstairs network, my network but now i can't see anything.  does this mean the driver was working?  I DID try to enter my wep key nothing ever connected so i just assumed the driver wasan't installed.

---

### Post by LowSky on 2008-09-23
if you could see the network then you shouldn't have needed to install any drivers. plus those instructions ar eover a year old, you should have questioned their use before using them.

did you reboot the computer?

---

### Post by ubunt2guy on 2008-09-23
yes i rebooted.  i feel stupid. i just didn't know how to know if there is a driver present.   i guess i will just reinstall ubuntu, huh?  start over?

---

### Post by Vorian Grey on 2008-09-23
Reinstalling would be the easiest way.

---

### Post by Tatty on 2008-09-23
Agreed, re-installing would be easiest for you, rather than trying to work backwards through that how-to to get back to where you were.

When you have re-installed try connecting via the command line.  Try starting heree:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#Router%20Connection](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#Router%20Connection)

Then ask back on here if you need any more help.

It may be that you will need to make a simple little script to connect via wireless.  You can then just double click this script each time you boot to connect.  I had to do this with feisty because my wireless driver was then in the same boat as yours, annoying but it tied me over till it was working out of the box in gutsy.

---

### Post by NewJack on 2008-09-23
Can I make a suggestion.  Next time you post a thread, please tell us what the problem is in the title.  Rather than "i may be giving up on ubuntu", it may be more helpful to your cause.  There are a ton of helpful souls in the Ubuntu community that can help you before you plan to just quit.  You only created 3 threads (this being one of them), and you went from "Hey I need a wireless driver" to "I'm outta here".

My intent is not to be harsh, but I do get "raised up" over some of the "Leaving Ubuntu" threads.  I see a lot of people dump on the OS without requesting help first.  Unfortunately, some things aren't perfect in Ubuntu or Linux in general due to hardware manufacturers resistance in supplying proper Linux drivers for their products.  There are usually workarounds for these things, you just have to be patient.  Windows/Microsoft would have just as many problems if the manufacturers did the same thing to them. 

/rant off

---

### Post by ubunt2guy on 2008-09-23
> **NewJack said:**
> Can I make a suggestion.  Next time you post a thread, please tell us what the problem is in the title.  Rather than "i may be giving up on ubuntu", it may be more helpful to your cause.  There are a ton of helpful souls in the Ubuntu community that can help you before you plan to just quit.  You only created 3 threads (this being one of them), and you went from "Hey I need a wireless driver" to "I'm outta here".

My intent is not to be harsh, but I do get "raised up" over some of the "Leaving Ubuntu" threads.  I see a lot of people dump on the OS without requesting help first.  Unfortunately, some things aren't perfect in Ubuntu or Linux in general due to hardware manufacturers resistance in supplying proper Linux drivers for their products.  There are usually workarounds for these things, you just have to be patient.  Windows/Microsoft would have just as many problems if the manufacturers did the same thing to them. 

/rant off

well said,  thanks for the heads up.  I was just really frustrated because i like to do things myself and felt defeated...

---

### Post by ubunt2guy on 2008-09-23
> **Tatty said:**
> Agreed, re-installing would be easiest for you, rather than trying to work backwards through that how-to to get back to where you were.

When you have re-installed try connecting via the command line.  Try starting heree:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#Router%20Connection](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#Router%20Connection)

Then ask back on here if you need any more help.

It may be that you will need to make a simple little script to connect via wireless.  You can then just double click this script each time you boot to connect.  I had to do this with feisty because my wireless driver was then in the same boat as yours, annoying but it tied me over till it was working out of the box in gutsy.

ok so i reinstalled (Fiesty).  

The applet shows many networks (neighbors, downstairs, mine) now and I entered my WEP.  

Now it just says it is connected but at 0%.
 

  went to terminal
  iwconfig says:
[FONT="Courier New"]
IEEE 802.11g ESSID: ""
Mode:Managed Frequency:2.462 GHz Access Point:  Not-Associated
RTS thr:off  Fragment thr=2346 B
Link Quality:0   Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0  Missed beacon:0
[/FONT]

I was thinking of plugging in an ethernet connection and updating to Gutsy; do you think there will be a driver available if I need one? 

What should i do?

cheers

---

### Post by bwang on 2008-09-23
The newest version of Ubuntu is Hardy Heron (8.04 LTS). You should use that.

---

### Post by Another Monkey on 2008-09-23
Gutsy?  Try Hardy.  Wireless worked for me straight out of the box (with a nasty little Belkin dongle).

Samba and Windows networking though....now that is a battle!

---

### Post by ubunt2guy on 2008-09-23
> **bwang said:**
> The newest version of Ubuntu is Hardy Heron (8.04 LTS). You should use that.

ok but will that solve the wireless problem?

---

### Post by 73ckn797 on 2008-09-23
I had some similar issues with Hardy and a wireless connection. On my laptop, after a re-install, I could not connect. After much frustration and a determination to get it to work, I restarted the router and it worked.

Another time with a desktop box It would not connect. I reloaded Ubuntu Hardy and things began working. I cannot explain what happened on that deal.

Does the connection work from a LiveCD? My desktop box would connect off of the liveCD so I installed it.

Not much technical help here but hopefully an encouragement to stick with it.

---

### Post by panhandle on 2008-09-23
People have had problems with this chipset in Feisty, but it works (at least for most) quite well in Hardy.

Once in Hardy, you likely will not have to use the command line at all for wireless network connection.

---

### Post by ubunt2guy on 2008-09-23
> **73ckn797 said:**
> I had some similar issues with Hardy and a wireless connection. On my laptop, after a re-install, I could not connect. After much frustration and a determination to get it to work, I restarted the router and it worked.

Another time with a desktop box It would not connect. I reloaded Ubuntu Hardy and things began working. I cannot explain what happened on that deal.

Does the connection work from a LiveCD? My desktop box would connect off of the liveCD so I installed it.

Not much technical help here but hopefully an encouragement to stick with it.

never worked on a live cd.  thanks though

---

### Post by ubunt2guy on 2008-09-23
> **panhandle said:**
> People have had problems with this chipset in Feisty, but it works (at least for most) quite well in Hardy.

Once in Hardy, you likely will not have to use the command line at all for wireless network connection.

ok thanks.  I'll update...then be back

---

### Post by Tatty on 2008-09-23
> **ubunt2guy said:**
> ok but will that solve the wireless problem?

There are no guarentees, but there is usually lots of added hardware support between each release, so theres a chance it may be fixed in Hardy.

I would reccomend installing Hardy first, If it still doesnt work then we can continue from there.

If i recall there were quite a few wireless chipsets in feisty which didnt work out of the box (mine included).

---

### Post by bobnutfield on 2008-09-23
> IEEE 802.11g ESSID: ""
Mode:Managed Frequency:2.462 GHz Access Point: Not-Associated
RTS thrff Fragment thr=2346 B
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

You are connected but it is not configured.  Open a terminal and type:

> sudo dhclient wlan0  #if that is the name of your wireless

You have not been assigned an IP address.

---

### Post by dub_u on 2008-09-23
Correct me if I'm wrong, but as I remember from my fresh install of Hardy my RT73-dongle (D-Link DWL G122) used the RT73USB driver as default. My experiences of this driver is that it is quite cranky and works a while both when booting from live cd as well as after installing the system. 
It connects to the WLAN but disconnects after a short while.

Even though I followed the instructions at [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236) I sometimes need to "wake the card up" by entering 

```
sudo iwconfig wlan0 essid MY_ESSID

sudo dhclient wlan0
```

just to make it connect to my wireless network.

You have blacklisted rt73usb in /etc/modprobe.d/blacklist I suppose?

---

### Post by ubunt2guy on 2008-09-23
> **bobnutfield said:**
> You are connected but it is not configured.  Open a terminal and type:

  #if that is the name of your wireless

You have not been assigned an IP address.

ok tried that.  

i got a bunch of stuff and at the bottom it says:

[FONT="Courier New"]
No DHCPOFFERS recieved.
No working leases in persistent database - sleeping.[/FONT]

---

### Post by ubunt2guy on 2008-09-23
i have a feeling nobody has ever gotten wireless working and this is all a hoax to drive me insane...

---

### Post by Tatty on 2008-09-23
> **ubunt2guy said:**
> i have a feeling nobody has ever gotten wireless working and this is all a hoax to drive me insane...

Lol maybe it is ;)

No seriously, there are always stumbling blocks when you first try a linux distro, particularly if your hardware does not play well.  I am trying to remember how to get wireless from the command line, but I havent had to do this manually since feisty so its a bit hazy.

can you post the output of:

```
sudo iwlist scan
```

---

### Post by styfle on 2008-09-23
I'm having a similar problem.
sudo iwlist scan works fine but its just connecting thats the problem
[http://ubuntuforums.org/showthread.php?t=924554](http://ubuntuforums.org/showthread.php?t=924554)

---

### Post by CaesarsAdvocate on 2008-09-24
Well, I feel the same as ubunt2guy.
Thinking of reconciling with windoze, or just giving up on enjoying my computer altogether. Or buy a Mac.

So many ppl say many different things, including howtos, the official documentation is horrible.... it's made dummy-simple, but why aren't there dummy-simple configuration interfaces? It's all so full of dead ends. I'm asked to compile stuff, before I get any basic understanding of anything. How to check what drivers I have installed? Where is the connect button?

No documents from which you can actually learn, not follow instructions you don't understand, getting output not mentioned in the instructions which you cannot interpret?

The problem is, without internet, an OS is not so usable these days. This is the great barrier, and until I can pass it, I have to keep restarting dozens of time, trying to carry out instructions I don't understand, them not working etc etc....

---

### Post by Perfect Storm on 2008-09-24
Thread title changed.

Please keep it tech related from now on :KS

Thanks


regards
A.I. Dude
Ubuntu Forum Staff

---

### Post by ubunt2guy on 2008-09-24
> **Tatty said:**
> Lol maybe it is ;)

No seriously, there are always stumbling blocks when you first try a linux distro, particularly if your hardware does not play well.  I am trying to remember how to get wireless from the command line, but I havent had to do this manually since feisty so its a bit hazy.

can you post the output of:

```
sudo iwlist scan
```

ok so I went to terminal and entered: sudo iwlist scan 

[SIZE="2"]lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning : Operation not supported

wlan0     No scan results[/SIZE]

---

### Post by ubunt2guy on 2008-09-24
**sudo iwlist scan**

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning : Operation not supported

wlan0     No scan results

** sudo dhclient wlan0 **

Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:13:d3:7f:f0:83
Sending on   LPF/wlan0/00:13:d3:7f:f0:83
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

**sudo iwconfig**

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  IEEE 802.11g  Frequency:2.462 GHz  
          RTS thr:off   Fragment thr=2346 B   
          
wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


anyone make sense of all this?  i feel like i'm almost there...

---

### Post by bobnutfield on 2008-09-24
What kernel are you using?  In reading these posts, you were updating to Hardy.  Has that been done?  In any case, try this from the commandline:

> sudo ifconfig wlan0 up
> sudo iwconfig wlan0 essid any
> sudo iwconfig wlan0 key <your WEP key>
> sudo dhclient wlan0

Try these commands in order.  If you do not get an IP address after these commands, then your inet config needs attention.  This wireless chipset has been supported natively since 2.6.22.

Post the results back

---

### Post by ubunt2guy on 2008-09-24
> **bobnutfield said:**
> What kernel are you using?  In reading these posts, you were updating to Hardy.  Has that been done?  In any case, try this from the commandline:






Try these commands in order.  If you do not get an IP address after these commands, then your inet config needs attention.  This wireless chipset has been supported natively since 2.6.22.

Post the results back

kevin@kevin-laptop:~$ sudo ifconfig wlan0 up
kevin@kevin-laptop:~$ sudo iwconfig wlan0 essid any 
kevin@kevin-laptop:~$ sudo iwconfig wlan0 key **********
kevin@kevin-laptop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:13:d3:7f:f0:83
Sending on   LPF/wlan0/00:13:d3:7f:f0:83
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by ubunt2guy on 2008-09-24
i don't know what to do.

I've upgraded to Hardy and in the corner detects 3 networks -including mine- but still no connection.  

I'm starting to think it is the WEP key.  I use this key for other computers in my house including my mobile device and it works...


any help would be great

cheers

---

### Post by bobnutfield on 2008-09-24
If you are seeing networks then you are connected, and you may be right about the WEP being the thing that is stopping your connection.  I do need encryption from my wireless, so I do not have a great deal of experience trouble shooting that, but there are many experts on this in this forum.  When you left click the network icon and choose your network, what happens?

---

### Post by ubunt2guy on 2008-09-24
> **bobnutfield said:**
> If you are seeing networks then you are connected, and you may be right about the WEP being the thing that is stopping your connection.  I do need encryption from my wireless, so I do not have a great deal of experience trouble shooting that, but there are many experts on this in this forum.  When you left click the network icon and choose your network, what happens?

a window appears asking for WEP 128-bit passphrase

---

### Post by bobnutfield on 2008-09-24
Then I am guessing you are right, that something wrong with the encryption key is keeping you from connecting.  If you know how to do it, you might try (just for testing purposes), disabling encryption to see if you can connect.

---

### Post by dub_u on 2008-09-24
Just thought of one thing regarding WEP key.
If you have special characters in your key, you might consider the following:

When I used WEP encryption on my wireless network I could only connect when i wrote

```
sudo ifconfig wlan0 key s:"ABCDEFG1234&" 
```

but not 

```
sudo ifconfig wlan0 key s:ABCDEFG1234& 
```

Don't know if this is of any help, but it might be worth a try if you manage to connect with the WEP encryption turned off and have special characters in your original WEP key.

---

### Post by styfle on 2008-09-24
I thought WEP keys can only be numbers and letters

---

### Post by ubunt2guy on 2008-09-24
all that i know is wifi doesn't work...

I think I've tried everything.  


Actually, the most infuriating thing is that I don't know if I have tried everything...

---

### Post by ubunt2guy on 2008-09-24
> **bobnutfield said:**
> What kernel are you using?  In reading these posts, you were updating to Hardy.  Has that been done?  In any case, try this from the commandline:






Try these commands in order.  If you do not get an IP address after these commands, then your inet config needs attention.  This wireless chipset has been supported natively since 2.6.22.

Post the results back

I've tried all of this, and nothing.  I can see that the network is detected but when I enter the WEP key still nothing...

---

### Post by ubunt2guy on 2008-09-24
WAIT A BREAKTHROUGH!!!

I connected to a network!  But it isn't my network.  Maybe there is something with the WEP encryption!  woohoo!

---

### Post by psychoxfreak on 2008-12-30
i may be giving up on ubuntu also i cant fix anything on it and i have a hp pavilion dv9000 so i dont know what to do i have done everything in every forum and still no internet i installed everything and still nada someone please help me email at [email]mdzedzej@yahoo.com[/email] if you are willing to walk me through via phone please do that is so much easier thanks.

---

