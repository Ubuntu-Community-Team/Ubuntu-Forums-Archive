---
title: "Wireless connection problems"
date: 2012-05-10
forum: New to Ubuntu
---

### Post by simonbr1970 on 2012-05-10
[SIZE=3][FONT=Calibri]A couple of days ago I created a bootable USB drive for the current release of Ubuntu. When I recovered from how jaw dropping’ly fast it was compared to my old OS, I have discovered a couple of challenges. The main one being I am unable to get internet access through my wireless connection (can’t get to the router either and no ping response) When I look at network manger though the . Wired connection works fine though. [/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Hardware is Dell Inspiron studio xps 1640, through a D-link DSL 2780 router. I do have WPA/WPA2 enabled – have switched this off without success, but may need to try this again.[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]First question is would wireless usually be expected to work when booting from USB.[/FONT][/SIZE]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[SIZE=3][FONT=Calibri]Second question, is more general suggestions on what I could try to get this working please.[/FONT][/SIZE]
 
 
```

[COLOR=black][FONT=Arial]ubuntu@ubuntu:~$ lspci | grep Network [/FONT][/COLOR]
[COLOR=black][FONT=Arial]04:00.0 Network controller: Intel Corporation WiFi Link 5100 [/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]ubuntu@ubuntu:~$ iwconfig [/FONT][/COLOR]
[COLOR=black][FONT=Arial]lo no wireless extensions. [/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]wlan0 IEEE 802.11abgn ESSID:"TALKTALK-D92498" [/FONT][/COLOR]
[COLOR=black][FONT=Arial]Mode:Managed Frequency:2.412 GHz Access Point: 28:10:7B:D9:24:98 [/FONT][/COLOR]
[COLOR=black][FONT=Arial]Bit Rate=1 Mb/s Tx-Power=15 dBm [/FONT][/COLOR]
[COLOR=black][FONT=Arial]Retry long limit:7 RTS thr:off Fragment thr:off [/FONT][/COLOR]
[COLOR=black][FONT=Arial]Power Management:off [/FONT][/COLOR]
[COLOR=black][FONT=Arial]Link Quality=70/70 Signal level=-39 dBm [/FONT][/COLOR]
[COLOR=black][FONT=Arial]Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0 [/FONT][/COLOR]
[COLOR=black][FONT=Arial]Tx excessive retries:0 Invalid misc:62 Missed beacon:0 [/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]eth0 no wireless extensions.[/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]ubuntu@ubuntu:~$ nm-tool [/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]NetworkManager Tool [/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]State: connected (global) [/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]- Device: wlan0 [TALKTALK-D92498] --------------------------------------------- [/FONT][/COLOR]
[COLOR=black][FONT=Arial]Type: 802.11 WiFi [/FONT][/COLOR]
[COLOR=black][FONT=Arial]Driver: iwlwifi [/FONT][/COLOR]
[COLOR=black][FONT=Arial]State: connected [/FONT][/COLOR]
[COLOR=black][FONT=Arial]Default: yes [/FONT][/COLOR]
[COLOR=black][FONT=Arial]HW Address: 00:22:FB:6D:C9:F4 [/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]Capabilities: [/FONT][/COLOR]
[COLOR=black][FONT=Arial]Speed: 1 Mb/s [/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]Wireless Properties [/FONT][/COLOR]
[COLOR=black][FONT=Arial]WEP Encryption: yes [/FONT][/COLOR]
[COLOR=black][FONT=Arial]WPA Encryption: yes [/FONT][/COLOR]
[COLOR=black][FONT=Arial]WPA2 Encryption: yes [/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]Wireless Access Points (* = current AP) [/FONT][/COLOR]
[COLOR=black][FONT=Arial]TalkTalk4bfc5: Infra, 00:21:63:77:80:94, Freq 2452 MHz, Rate 54 Mb/s, Strength 19 WPA [/FONT][/COLOR]
[COLOR=black][FONT=Arial]*TALKTALK-D92498:Infra, 28:10:7B:D9:24:98, Freq 2412 MHz, Rate 54 Mb/s, Strength 85 WPA WPA2 [/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]IPv4 Settings: [/FONT][/COLOR]
[COLOR=black][FONT=Arial]Address: 192.168.1.7 [/FONT][/COLOR]
[COLOR=black][FONT=Arial]Prefix: 24 (255.255.255.0) [/FONT][/COLOR]
[COLOR=black][FONT=Arial]Gateway: 192.168.1.1 [/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]DNS: 192.168.1.1 [/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]- Device: eth0 ----------------------------------------------------------------- [/FONT][/COLOR]
[COLOR=black][FONT=Arial]Type: Wired [/FONT][/COLOR]
[COLOR=black][FONT=Arial]Driver: tg3 [/FONT][/COLOR]
[COLOR=black][FONT=Arial]State: unavailable [/FONT][/COLOR]
[COLOR=black][FONT=Arial]Default: no [/FONT][/COLOR]
[COLOR=black][FONT=Arial]HW Address: 00:22:19:E9:62:E4 [/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]Capabilities: [/FONT][/COLOR]
[COLOR=black][FONT=Arial]Carrier Detect: yes [/FONT][/COLOR]
[COLOR=black][FONT=Arial]Speed: 100 Mb/s [/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]
[COLOR=black][FONT=Arial]Wired Properties [/FONT][/COLOR]
[COLOR=black][FONT=Arial]Carrier: off [/FONT][/COLOR]
[COLOR=black][FONT=Arial] [/FONT][/COLOR]

```

---

### Post by sadaruwan12 on 2012-05-10
Welcome friend to the forum can you tell us what is the version of your Ubuntu ditro and what is the vendor of the Wirelesss card ?

---

### Post by grahammechanical on 2012-05-10
I cannot see much wrong with those listings that you have provided.

Your iwconfig is much the same as mine except that a Bit Rate=1Mb/s is much slower than mine, which is 54 Mb/s

Your nm-tool listing is much the same as mine. Again the Capabilities Speed is shown as 1Mb/s when the wireless access points are 54Mb/s.

The signal strength is 85. Mine is 78. Note this from nm-tool

> State: connected

And you are connected to 

> *TALKTALK-D92498:Infra, 28:10:7B: D9:24:98, Freq 2412 MHz, Rate 54 Mb/s, Strength 85 WPA WPA2

This ( * ) says the access point you are connect to.

This access point requires WPA WPA2 to be the method of encryption used not only for the pass phrase but for the wireless transmissions. Turning it off at the computer will not make it work if WPA WPA2 is still enabled in the router.

Both router/hub need to the set for WPA WPA2.

You say this

> The main one being I am unable to get internet access through my wireless connection (can&#8217;t get to the router either and no ping response) 

You are getting a connection to the router by wireless (or so it seems to me) but you are not getting a connection to the Internet. Is the router getting a connection to your ISP?

Do you know how to access the settings of the router/hub?

Here is a thought. Was this USB install done with Persistence? If not then it is just like a live CD. Changes such as making a wireless connection will not survive an OS shutdown. You may need to use Network Manger to connect to your wireless access point every time and you will need to enter the wireless key or pass phrase.

Regards.

---

### Post by simonbr1970 on 2012-05-10
I am running release 12.04 with persistence enabled.
Wireless card is [COLOR=black][FONT=Arial]: Intel Corporation WiFi Link 5100  and it seems to be picking up 
[COLOR=black][FONT=Arial]Driver: iwlwifi [/FONT][/COLOR]
[COLOR=black][FONT=Arial][/FONT][/COLOR] 
[COLOR=black][FONT=Arial]Just had a look here 
[[FONT=Calibri][SIZE=3][COLOR=#800080]https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel[/COLOR][/SIZE][/FONT]]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel")
and it suggests using  iwlagn  as the driver.
 
How would I make the change to try this driver instead?
[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by simonbr1970 on 2012-05-11
I have triued doing a full install but made no difference. I have also tried a different router and turned off WPA/WPA2..........hmmmmmm
 
Still stuck though on how I could use the alternative IWLAGN drivers. Any clues appreciated.

---

### Post by simonbr1970 on 2012-05-17
Just found a workin solution here......

[http://ubuntuforums.org/showthread.php?p=11945151#post11945151](http://ubuntuforums.org/showthread.php?p=11945151#post11945151)

Phew !!!!!

---

