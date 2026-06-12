---
title: "connecting to the internet using phone as gprs modem via bluetooth"
date: 2008-05-01
forum: Philippine Team
---

### Post by jajabinx on 2008-05-01
:confused::confused:Tagal ko na pong nagbababad para mapagana ang pagconnect ng aking laftaf sa aking gprs-enabled nokia via bluetooth. I tried Gnome PPP at wvDial.

Niwei, halos pareho lang ang nangyayari pag ginagamit ko ang Gnome PPP o wvDial.

My phone somehow receives something kasi nagpaprompt ang phone ko saying "Connected to Jajabinx" pero after a millisecond, "Disconnected:Jajabinx" or minsan naman "Packet data not allowed" although I have set up my packet data settings on my phone. While my phone gives the error and discon message, sa terminal logs ko, it says:

> [INDENT]
root@jaja-laptop:~# wvdial
--> WvDial: Internet dialer version 1.60
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Sending: AT+CGDCONT=,"IP","SMART"
AT+CGDCONT=,"IP","SMART"
OK
--> Modem initialized.
--> Sending: ATDT*99#
--> Waiting for carrier.
ATDT*99#
NO CARRIER
--> No Carrier!  Trying again.[/INDENT]

Now my settings are:

wvdial.conf: 

[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=,"IP","SMART"
Modem = /dev/rfcomm0
Phone = *99***1#
Username = username
Password = password
New PPPD = yes
ISDN = yes
BAUD = 115200
Stupid Mode = yes
Carrier Check = no

My Gnome PPP settings are somehow the same as that in my wvdial kasi i'm mini-mayni-minimo ako, except sa init strings which is the same as that on the wvdial.

Help help. Baka may workaround kayo kasi i've browsed other forums. The "No carrier!" message na narereceive ko sa terminal when I try to connect is a recurring issue.

---

### Post by jajabinx on 2008-05-08
:popcorn::guitar:Hehe, have successfully made it work! So excited that I am posting my new wvdial.conf settings...

> 
[Dialer Defaults]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","internet"
Modem = /dev/rfcomm0
Phone = *99#
Username = yourusername
Password = yourpassword
New PPPD = yes
ISDN = no
BAUD = 115200
Stupid Mode = yes
Carrier Check = no

I'll be posting the detailed steps in case anyone wants to also use their mobile phones as their gprs modem.

---

### Post by jepong on 2008-05-08
> **jajabinx said:**
> :popcorn::guitar:Hehe, have successfully made it work! So excited that I am posting my new wvdial.conf settings...



I'll be posting the detailed steps in case anyone wants to also use their mobile phones as their gprs modem.

thanks sa info... tagal ko na gusto try 'to. :-)

---

### Post by jajabinx on 2008-05-09
Heto na...
Ang aking mga gadgets, Nokia 6151 at Acer Aspire 4720.
I'm on Ubuntu 8.04.
And the steps i took,
[B]
1. Activate my GPRS setting.[/B]

Send **SET N6151** to 211.
The access keyword will also activate MMS and 3G.

**2. Install Bluetooth utilities.**

Acer Aspire 4720 has a built-in Bluetooth so all I need to do is press the Bluetooth button and I'll get the Bluetooth applet after making sure that I have the latest **bluez-utils**, **bluez-gnome** and **wvdial**.

    ```
$ sudo apt-get upgrade **bluez-utils bluez-gnome wvdial**
```

else,

    ```
$ sudo apt-get install **bluez-utils bluez-gnome wvdial**
```

or, from the Synaptic Package Manager, search for **bluez** then mark **bluez-utils** and **bluez-gnome** for installation. Same goes for **wvdial**.
[B]
3. The Pairing[/B]

I set my laptop as my phone's paired device. And on my laptop's Bluetooth menu, set my phone as a trusted device.
[B]
4. The Binding[/B]

Now, I have to make sure that my phone and laptop can communicate and discuss things like creating connection and sending/receiving packet data. =)

To know my MAC or BD address:
    ```
$ hcitool scan

    Scanning ...
    **[COLOR="Blue"]00:11:22:33:44:55[/COLOR]** Japot
```

To get my DUN channel (which is 1)
    ```
$ sdptool search dun

    Searching for dun on 00:11:22:33:44:55 ...
    Service Name: Dial-up networking
    Service RecHandle: 0x1005f
    Service Class ID List:
    "Dialup Networking" (0x1103)
    "Generic Networking" (0x1201)
    Protocol Descriptor List:
    "L2CAP" (0x0100)
    "RFCOMM" (0x0003)
    Channel: **[COLOR="Blue"]1[/COLOR]**
    Language Base Attr List:
    .....

```

After getting the MAC and Channel, type:
    ```
$ rfcomm bind 0 **[COLOR="Blue"]00:11:22:33:44:55 1[/COLOR]**
```

To check if my GPRS modem and my phone was ready to meet, I typed:
    ```
$ rfcomm

    rfcomm0: 00:11:22:33:44:55 channel 1 clean

```
Seeing **clean**, I edited  **[COLOR="Blue"]/etc/bluetooth/rfcomm.conf[/COLOR]** to create the binding:

> # RFCOMM configuration file.

    rfcomm0 {
    bind **yes**;
    device **00:11:22:33:44:55**;
    channel **1**;
    comment "Jajabinx's N6151";

Then, I edited **[COLOR="Blue"]/etc/wvdial.conf[/COLOR]**

   >  [Dialer Defaults]
    Init1 = ATZ
    Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
    Init3 = AT+CGDCONT=1,"IP","Internet"
    Modem = /dev/rfcomm0
    Phone = *99#
    Username = jajabinx
    Password = wordpass
    New PPPD = yes
    ISDN = no
    BAUD = 115200
    Stupid Mode = yes
    Carrier Check = no

The Init3 line is what I exactly used. If you're using Globe, better call customer service to know your APN.

**5. The Connection**

Now, my laptop is ready to communicate with my phone and discuss things like creating connection and sending/receiving packet data. =)

After creating the settings above, this is what I need to type to create the connection:

    ```
$ wvdial

    --> WvDial: Internet dialer version 1.60
    --> Initializing modem.
    ATZ
    OK
    ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
    OK
    AT+CGDCONT=1,"IP","Internet"
    OK
    ATDT*99#
    CONNECT
    [... ppd logs]
    --> local  IP address 10.157.192.194
    --> remote IP address 10.6.6.6
    --> primary   DNS address 203.84.191.216
    --> secondary DNS address 121.1.3.250

```

**6. The Surfing**

The boxed "G" showing on the phone's upper left display signals active connection to the net.

To terminate connection, just do a **Ctrl+C**.

There! :)

---

### Post by NakedSnake on 2008-05-22
do you have any tip using Sony Ericsson K800 as modem
thanks

---

### Post by extent on 2008-07-03
> **NakedSnake said:**
> do you have any tip using Sony Ericsson K800 as modem
thanks

Yes. Use mozilla browser instead of internet explorer. in mozilla tools>options choose connection settings and use 193.113.200.195 for http proxy. Port 8080. Choose to use this proxy server for all protocols.

---

### Post by mpeter on 2008-11-19
Thanks Jajabinx. Great post. This worked for me on Intrepid. On Hardy I used Blueman Bluetooth Manager, but this does not work on Intrepid and I have been looking for a solution.

---

### Post by jepong on 2008-12-02
i tried your tips using a P990i (globe telecom)... on my desktop it say im connected but there is no G or any indication my phone is connected.

---

### Post by jepong on 2008-12-03
i got it working bu nothing is happening with my network manager.. are there things needed to be configured after the mobile is connected?

---

### Post by raoul-newbie on 2008-12-16
pwede pong patulong maggamit ng motorola e1070(singapore model)as modem for ubuntu intrepid...  this modem is my only means to connect to the internet. i've read that moto4lin is the only means para magamit ko ang phone as modem.

---

### Post by jepong on 2008-12-16
may problem ata bluetooth sa intrepid... ayaw mag pair ng phone ko at ng laptop.

---

### Post by nurazizah on 2009-02-02
Hi, I tried this and so far it's the one that works most. I got to wvdial and then my phone asked for a pass key. What should it be? I didn't set up any passkeys and my phone is not locked in any way.

Please help. an using a Samsung F330 and an acer aspire one on xubuntu 8.10

---

### Post by nurazizah on 2009-02-09
I still couldn't solve the passkey problem. Tried all sorts of numbers such as 1234, 0000 etc, none worked. Edited hcid.conf didn't work either. Then I found this interface, blueman.

[http://blueman-project.org](http://blueman-project.org)

[http://tanere.blogspot.com/2008/11/mobile-broadband-over-bluetooth-on.html](http://tanere.blogspot.com/2008/11/mobile-broadband-over-bluetooth-on.html)

Even though I couldn't connect with it (I've decided to stop trying to fix the bluetooth connection, at least for a little while, driving me nuts), blueman works for lots of others. Try it.

---

### Post by danested on 2009-12-27
Thank you for this post. i'm Gonna Try it out now. Hope this works.

---

