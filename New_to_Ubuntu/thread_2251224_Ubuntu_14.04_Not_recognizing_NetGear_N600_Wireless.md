---
title: "Ubuntu 14.04 Not recognizing NetGear N600 Wireless dual band Usb adapter WNDA3100 V1"
date: 2014-11-02
forum: New to Ubuntu
---

### Post by Leonardo_R._Marque on 2014-11-02
Hello, I am new to Ubuntu and I have this NetGear usb wireless adapter and Ubuntu does not recognize it. I have no wireless card built into the computer so I cannot use the internet or download. I have tried the command line lsusb and this came up:


  Bus 001 Device 004: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
    [FONT=&quot]Bus 001 Device 006: ID 154b:005b PNY [/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]Bus 001 Device 002: ID 054c:021f Sony Corp. [/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]Bus 005 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]Bus 003 Device 002: ID 046d:08f0 Logitech, Inc. QuickCam Messenger[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
  [FONT=&quot][/FONT]
  [FONT=&quot]Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub[/FONT]
  [FONT=&quot][/FONT]
  

What do I do next?

---

### Post by Bucky Ball on 2014-11-02
Welcome. These wireless cards are known to be problematic in Ubuntu. There is an old school fix (which uses ndiswrapper which should generally be avoided at all costs and is only needed in very few cases now) and you should start [HERE]("http://ubuntuforums.org/showthread.php?t=2221251").

You'll need to get online with a cable for the fix to work, though. 

Good luck.

Just a tip: Always do a [search]("https://duckduckgo.com/?q=+WNA3100+ubuntu+14.04") prior to posting.

---

### Post by Leonardo_R._Marque on 2014-11-02
Well, I don't have ethernet or dial up internet, all I have is the computer and the adapter. Sorry.

---

### Post by Bucky Ball on 2014-11-02
In that case, you'd need to download the required ndiswrapper and wireless card Windows driver on a machine that is online or get a new adapter that is known to work out of the box. They are cheap.

---

### Post by Leonardo_R._Marque on 2014-11-02
Do you have any recommendations for good adapters?

---

### Post by Bucky Ball on 2014-11-02
Most things with Realtek or Broadcom wireless cards are normally good. Anything that was released 'yesterday', i.e. very new, may or may not work.

The confusing thing is that the device might be called a TP-Link blah blah, or any other brand name, but it is the wireless chip inside that counts, not the brand. Do a little research for wireless devices that work 'out of the box' on Ubuntu. There is a lot of info out there. 

[https://duckduckgo.com/?q=wireless+that+works+out+of+the+box+ubuntu](https://duckduckgo.com/?q=wireless+that+works+out+of+the+box+ubuntu)

PS: If the card worked in a previous version it will work in the newer ones, too. Generally.

---

### Post by JeQhdMD on 2014-11-03
[COLOR=#000000]Atheros drivers are usually a good match (as several were open-sourced years ago).  Look for "ath9k_htc" driver.

Top recommended is TP-Link TL-WN722N with atheros chipset (AR9271 or AR7010)

[/COLOR]Also, I have had very good experience with the Panda Ultrawifi listed below

Just check on Amazon - these are mostly in the $10 to $25 range, although the top of line TL-WN822N is a bit more

[COLOR=#000000]~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/COLOR]
[COLOR=#000000]|| Brand || Model || Chipset || Driver || Plug and Play || Phone ||[/COLOR]
[COLOR=#000000]~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/COLOR]
[COLOR=#000000]TP-Link || TL-WN722N || AR9271 || ath9k_htc || Yes || ||[/COLOR]
[COLOR=#000000]~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/COLOR]
[COLOR=#000000]TP-Link || TL-WN822N || AR7010 || ath9k_htc || Yes || ||[/COLOR]
[COLOR=#000000]~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/COLOR]
[COLOR=#000000]""""" || """"" || AR9287 || """"" || Yes || ||[/COLOR]
[COLOR=#000000]~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/COLOR]
[COLOR=#000000]Airlink || AWL5088 || RTL8188CUS || ??? || Yes || ||[/COLOR]
[COLOR=#000000]~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/COLOR]
[COLOR=#000000]"""" || """" || RTL8192CUS || ??? || Yes || ||[/COLOR]
[COLOR=#000000]~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/COLOR]
[COLOR=#000000]Panda || Ultra Wifi || RTL8188CUS || ??? || Yes || ||[/COLOR]
[COLOR=#000000]~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/COLOR]
[COLOR=#000000]"""" || """" || RTL8192CUS || ??? || Yes || ||[/COLOR]
[COLOR=#000000]~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/COLOR]
[COLOR=#000000]Edimax || EW-7811UN || RTL8188CUS || ??? || Yes || ||[/COLOR]
[COLOR=#000000]~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/COLOR]
[COLOR=#000000]ASUS || USBN13 || RTL8188CUS || ??? || Yes || ||[/COLOR]
[COLOR=#000000]~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~[/COLOR]

---

### Post by Bucky Ball on 2014-11-03
Please provide [LINKS]("http://www.amazon.com/s/ref=nav_search_go?url=search-alias%3Daps&field-keywords=wireless+usb+linux").

Where did you find that list?

---

### Post by JeQhdMD on 2014-11-03
Hello Bucky,

Yes - - links are always best but I skipped that as Rudy-boy (mini-schnauzer jack russell cross) was pulling my pants leg and I thought it best to "hit the trail" before I "hit the floor" ;). . . but in future, Rudy-boy will just have to wait another minute ( . . it's the jack russell in him).
............................
BTW , , re graphics, I often use links to an image directory I have on Imgur . . . so, perhaps I also copied the wrong code thereby embedding the file rather than linking it.   Is that an option (other than thumbnails on the Ubuntu forums - if not, it's no problem using thumbnails.)
............................
Re the list . . . I have a database (Cherrytree) that allows for table format (less rich text) - so cut and paste didn't quite capture the matrix right.   I do have all those adapters, and have tested them out on several linux laptops and desktops.   Right now, I'm using the TP-Link WN822N - - on a Lenovo H410 desktop without built in wireless.   Has worked absolutely perfect for the last two years and connects to my gateway in basement at about 75% strength.   

Greg

---

