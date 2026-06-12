---
title: "HOWTO: ipw3945 connecting to a University Network (802.1x / PEAP)"
date: 2006-09-02
forum: Outdated Tutorials &amp; Tips
---

### Post by UltraMathMan on 2006-09-02
First of all this is my first HOWTO and it details how I got connected to Lehigh University's wireless network with wpa_supplicant. I decided to post this as I was having trouble finding info on this subject [of connecting to a University 802.1x network] and figured this might serve as a springboard to help others connect to their own 802.1x University networks.

**I recommend backing up all config files before editing them and take no responsibility for any damage this *may* cause**

Ok, that said let's get started, first make sure you have the wpa_supplicant installed.```
sudo apt-get install wpasupplicant
```

Now create the wpa_supplicant configuration file```
sudo gedit /etc/wpa_supplicant/wpa_supplicant.conf
```
then paste the following, *edit as needed* and save.
```
# for lehigh university
network={
        ssid="lu"
        scan_ssid=1
        key_mgmt=IEEE8021X
        eap=PEAP
        phase2="auth=MSCHAPV2"
        identity="*your university login name*"
        password="*your password*"
}

```

Now edit /etc/network/interfaces with ```
sudo gedit /etc/network/interfaces
```
adding ```
wpa-driver wext
wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
``` under your wireless interface.

Restart networking ```
sudo /etc/init.d/networking restart
``` and enjoy!

Hope this helps somebody :biggrin:

*Adapted from [http://coral.ie.lehigh.edu/~asm4/howtos/wireless.html](http://coral.ie.lehigh.edu/~asm4/howtos/wireless.html)

---

### Post by UltraMathMan on 2006-10-06
Ok, so I went home today and couldn't connect through Administration -> Networking to my WEP encrypted network. It seems wpa_supplicant takes control of the networking management and for those of you who happen to use this HowTo note that you will need to add any future network config to the wpa_supplicant.conf file eg: ```
 # wireless for home
network={
        ssid="*your network name*"
        key_mgmt=NONE
        wep_key0=
        wep_tx_keyidx=1
}
``` where wep_key0=*your wep key*

See the link at bottem of previous post for full config file example.

---

### Post by vkkim on 2006-10-07
Thanks!  I'm at LU as well and it works great!

---

### Post by visik7 on 2006-10-09
better to use the facilities in /etc/network/interfaces

here is my conf:
"DON'T CUT AND PASTE THE CODE MUST BE ADAPTED"
```

auto eth1
iface eth1 inet dhcp
        wpa-driver wext # this is the default and useless if set to wext only usefull if you need another driver (supported by wpa_supplicant
        wpa-ap-scan 2
        wpa-ssid <ssid>
        wpa-scan-ssid 1
        wpa-key-mgmt IEEE8021X
        wpa-eap TTLS
        wpa-anonymous-identity anonymous
        wpa-phase2 auth=PAP
        wpa-identity <username>
        wpa-password <password>

```

but I've a little python script that detect where am I and select the right conf, this is the /etc/network/interfaces:
"DON'T CUT AND PASTE THE CODE MUST BE ADAPTED"
```

auto eth1
mapping eth1
        script /etc/network/scripts/checkap
        map uni <replace with the mac address of the campus ap>
        map home <replace with the mac address of the home ap>

iface uni inet dhcp
        wpa-ap-scan 2
        wpa-ssid <ssid>
        wpa-scan-ssid 1
        wpa-key-mgmt IEEE8021X
        wpa-eap TTLS
        wpa-anonymous-identity anonymous
        wpa-phase2 auth=PAP
        wpa-identity <username>
        wpa-password <password>

iface home inet dhcp
        wireless-essid CAME
        wireless-mode managed

```

and this is the python script for check the wireless
(/etc/network/scripts/checkap)
```

#!/usr/bin/python

import time, pyiw, sys, os

excepted = 'yes'
while excepted == 'yes':
        try:
                iface = pyiw.WirelessInterface(sys.argv[1])
                excepted = 'no'
        except:
                excepted = 'yes'
        time.sleep(1)

buffer = sys.stdin.read()

networks = buffer.split('\n')
i=0
while i<len(networks):
        networks[i] = networks[i].split(' ')
        i+=1

for node in iface.Scan():
        for mac in networks:
                if node ['ap_mac'] in mac:
                        print mac[0]
                        break


```

attached there is a python module needed for discover the wireless (put it in /etc/network/scripts/ or wherever you have the checkap script)

---

### Post by randomnumber on 2006-10-11
I am at UWF (Univ. of West FL) and no one seems to know how to connect to their wireless with linux. I have been using my laptop as a dual boot and been booting XP so that it is logged onto the network then rebooting and using linux. Some how the connection stays. I can even boot linux up an hour later and it will still be able to connect, it is only when I come in the next day that I can not connect without booting XP first.

Anyway, I used the first part of your thread and tried to connect without booting XP first and it connected. It maybe a fluke so I will try a few more times before saying it works. Being that the network allows for connections for long periods of time after original connection I can not truely have tested it. If it turns out that it works I would be happy to submit the information to the school so that others at our school can use linux on our wireless network.

I have network manager conrtolling my connections and it seems to work well. I do not have to add the extra on this thread about being on different networks. If the network is there, it connects.

I want to say thanks for the information and I am excited to see if it connects tommorrow. 

THANKS

It would be neat if someone would explain why switching os would leave a availble connection.

---

### Post by randomnumber on 2006-10-13
I tried the connection setup and it works half way. The config file does not seem to work. It could be that I error ed in setting up the config file. I have found that I can get a connection using network-manager that can be added to your system. It is not the manager that ubuntu uses as default, you have to add network-manager and disable the connections through the default manager so that this application can access the network card. If you do not disable the network card, network-manger will not be able to use/see the network card.

I connect to the network by:
1.click the network-manager icon
2.select “Connect to Other Wireless Network..”
3.change “Wireless Security:” to “WPA Enterprise”
  This expands the menu to have more options
4.type network name, example “uwf-argo-air”
5.change “EAP method” to “PEAP”
6.change “Key Type:” to “Dynamic WEP”
7.type user id in “Identity”, UWF sail lab I.D.
8.type user password in “Password”, UWF sail Lab password
9.Then connect.

Network Manager appears to be using wpa_supplicant. If you are interested In seeing information from wpa_supplicant while connecting you can install and run wpa_gui. These applications are run as root so you would to type sudo wpa_gui to get it to work. 

I hope this is a process that really works. I will continue to test the connection to see if it is a fluke of success.

Thanks everyone.

a nice page and has how to install network-manager
[http://ubuntuguide.org/wiki/Dapper#How_to_Configure_Ubuntu.2FKubuntu_with_WPA_using_Network-Manager](http://ubuntuguide.org/wiki/Dapper#How_to_Configure_Ubuntu.2FKubuntu_with_WPA_using_Network-Manager)

---

### Post by ubuntu_demon on 2006-10-17
I'm having problems connecting to wireless university network (PEAP,WEP)
[http://ubuntuforums.org/showthread.php?t=278603](http://ubuntuforums.org/showthread.php?t=278603)

Thanks for taking a look :)

---

### Post by randomnumber on 2006-10-18
To aid any in figureing out if your network can be conneted to the same as mine I an leaving a link to the how to guides from my school for XP, mac. for comparison.

[http://portal.knowledgebase.net/display/2n/articleDirect/index.asp?aid=133405&r=0.9166834](http://portal.knowledgebase.net/display/2n/articleDirect/index.asp?aid=133405&r=0.9166834)

good luck everyone.

---

### Post by halfdan.k on 2007-01-09
A fairly good and graphical guide to dapper 6.06 and a (common) uni wifi wep/peap 802.1x network...made my day :)

[http://www.sai.uio.no/it/oppkobling/wireless-linux-eng.html](http://www.sai.uio.no/it/oppkobling/wireless-linux-eng.html)

---

### Post by dennis.groome on 2007-03-02
There's lots of great information in this thread. I have a similar problem, but I'm trying to get a connection to a wired network over ethernet using PEAP-MSCHAPv2 and 802.1x. Can these configurations be adapted to use a wired NIC on eth0? What needs to be changed?

---

### Post by staticsage on 2007-03-19
> **dennis.groome said:**
> There's lots of great information in this thread. I have a similar problem, but I'm trying to get a connection to a wired network over ethernet using PEAP-MSCHAPv2 and 802.1x. Can these configurations be adapted to use a wired NIC on eth0? What needs to be changed?

I'm facing the same problem. Anyone know where to start with this?

---

### Post by dennis.groome on 2007-03-19
Try this: [http://www.ubuntuforums.org/showthread.php?t=380220](http://www.ubuntuforums.org/showthread.php?t=380220)

Let us know if it works and/or any problems you encounter.

---

### Post by staticsage on 2007-03-20
Worked for me... thanks a lot!

---

### Post by irlkersten on 2007-03-28
I'm in the DIT college in Ireland and they've setup a new wireless network. The problem is the only instructions they've given to access it are for windowsxp. I have tried to translate these to ubuntu using any information I could find in this thread but so far I haven't managed to get it working. The instuctions they gave are as follows:

```

802.1X Supplicant Configuration for DItsecure

The following instructions are for Windows XP SP2: other platforms or software may
 display different menus and forms but the same information will need to be entered.

1.Right click on the wireless network icon in the system tray and select View available
 wireless networks

2.Select the ‘ditsecure’ SSID and click Connect (this attempted connection will fail, 
but it will ensure that Windows is aware that the network exists).

3.Select Change advanced settings

4.Select the Wireless networks tab

5.Select the ‘ditsecure’ SSID from preferred networks

6.Click on Properties, which will open an ditsecure properties window with the
 Association tab selected.

7.Set Network authentication to Open.

8.Set Data Encryption to WEP.

9.Ensure that Key is provided for me automatically is ticked. 

10.Select the Authentication tab.

11.Ensure that Enable IEEE 802.1X authentication for this network is ticked.

12.Set the EAP Type to Protected EAP (PEAP)

13.Deselect Authenticate as computer and Authenticate as guest.

14.Select EAP Properties:

15.Select Authentication method as Secured Password (EAP-MSCHAP v2).

16.Select Configure...

17.Ensure that Automatically use my Windows logon name and password is NOT 
selected.

18.Click OK on the EAP MSCHAP v2 properties window. 

19.Ensure that Validate server certificate is NOT ticked.

20.Click OK for the PEAP Properties.

21.Click OK for ditsecure Properties.

22.Click OK for Wireless Network Connection Properties.

23.A dialogue balloon associated with the wireless network icon in the systems tray 
will appear, prompting the user to Select a certificate or other credentials. Click on 
this balloon.

24.In the resultant Enter Credentials window, enter your Active Directory username 
and password, leaving the domain field blank.

25.Click OK. Your laptop should now authenticate your credentials with your network
 and, if successful, gain network access.

```

Any ideas what needs to be configured to make this work on ubuntu? I'm running feisty (beta) so I have wpasupplicant and network-manager installed by default. I've tried to connect though the network manager by clicking on "Connect to other wireless network" and then "WPA Enterprise" and filling in what details I know from the windows instructions above, but it fails. Any suggestions on this?

---

### Post by UltraMathMan on 2007-03-28
Looks very similar (if not identical) to Lehigh's. Did you try the original instructions?

---

### Post by dennis.groome on 2007-03-28
> **irlkersten said:**
> 

Any ideas what needs to be configured to make this work on ubuntu? I'm running feisty (beta) so I have wpasupplicant and network-manager installed by default. I've tried to connect though the network manager by clicking on "Connect to other wireless network" and then "WPA Enterprise" and filling in what details I know from the windows instructions above, but it fails. Any suggestions on this?

Check the link I gave two or three posts above this one. Let us know if that helped.

---

### Post by irlkersten on 2007-03-28
> Looks very similar (if not identical) to Lehigh's. Did you try the original instructions?

I did, but they seemed to be somewhat different on feisty and wouldn't work for me. I'll take another look at them though. I'm sure it's just me not understanding something somewhere.

> Check the link I gave two or three posts above this one. Let us know if that helped.

Will do. :-) I've setup everything according to the link now, and also have the settings from the original post setup with the help of your link. I can't wait to try it once I'm back in college tomorrow :-)

---

### Post by jaywee on 2007-05-11
hmm, I thought I will never conect to the internet at the library,may this can help!

---

### Post by austraind on 2007-05-20
hey,
Thanks a lot. Your method really worked. I have been banging my head over the internet setup for a week now.Tried every possible option untill i stumbled on ur thread.
Now it connects like sweet. :-)

cheers,
austraind

---

### Post by 3006828 on 2007-06-05
You guys are gods :D

thannk you so much fo your collective experiences :) im sitting in a windows shell salivating at the thought of being able to run *nix completely here in the library. :D:D


Thank you a Bucket LOAD!! 


and sorry for pasting a new thread without doing a proper google search :(

---

### Post by ranger47 on 2007-08-15
I followed the instructions, but it keeps asking me for a WEP key.  Any ideas?

---

### Post by captainmnb on 2007-08-28
I followed the original Lehigh instructions, slightly modified for my university's network (as per [http://www.sas.upenn.edu/computing/wireless/airpennnet_linux.html](http://www.sas.upenn.edu/computing/wireless/airpennnet_linux.html)), and it works sporadically, but not consistently.  Coming out of suspend, it works about half the time, and switching to a wired connection and back also breaks it sometimes.

It seems that something in the procedure took over the network manager, as the panel icon no longer lists available wireless networks, and when connected it just shows the two computers networked icon rather than signal strength as it used to.

Any ideas as to what is wrong here?

(I'm running Feisty on a Thinkpad X41 tablet.)

---

### Post by UltraMathMan on 2007-08-28
@ranger47: Did you edit /etc/network/interfaces and restart networking, network manager should be "taken over" by wpa-supplicant, so you shouldn't need to do anything with it to connect after following the instructions.

@captainmnb: When you are having problems have you tried restarting networking? I remember that fixing a lot of snags for me. It also sounds like a acpi problem, perhaps its not shutting something off, or not starting it back up, check through dmesg for clues on that. As I've said earlier in the thread wpa-supplicant DOES take over all networking from network manager and any additional config must be done through wpa-supplicant.

-Hope this helps ;)

---

### Post by phatalbert on 2007-09-01
@captainmb,

Hi, I'm at Penn too, but I'm having trouble getting it to work even sporadically. Which bits of [http://www.sas.upenn.edu/computing/wireless/airpennnet_linux.html](http://www.sas.upenn.edu/computing/wireless/airpennnet_linux.html) did you use? Just the different wpa_supplicant config file or did you use this ?
> wpa_supplicant -c /etc/airpennnet.conf -i DEV -D DRIVER -B 

---

### Post by captainmnb on 2007-09-01
> **phatalbert said:**
> @captainmb,

Hi, I'm at Penn too, but I'm having trouble getting it to work even sporadically. Which bits of [http://www.sas.upenn.edu/computing/wireless/airpennnet_linux.html](http://www.sas.upenn.edu/computing/wireless/airpennnet_linux.html) did you use? Just the different wpa_supplicant config file or did you use this ?

You need to do both of those steps, but make sure you have your device right for DEV and the correct driver.  And don't forget to restart networking.  I have mine working about 90% of the time now, although I have to restart dbus after coming out of suspend sometimes (not entirely sure why).

---

### Post by victorgreen on 2007-09-03
Im also at Penn trying to connect to AirPennNet. Im using iwl4965 though on an Thinkpad X61 with 7.04 Kernel 2.6.22-8. I also followed the instructions on [http://www.sas.upenn.edu/computing/wireless/airpennnet_linux.html](http://www.sas.upenn.edu/computing/wireless/airpennnet_linux.html). 

Connecting via the instructions on the site gives me this:
wpa_supplicant -c /etc/airpennnet.conf -i wlan0 -D iwl4965 -B 
Unsupported driver 'iwl4965'.

But, wext gives me this:
sudo wpa_supplicant -c /etc/airpennnet.conf -i wlan0 -D wext

ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 4 value 0x0 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - bind(PF_UNIX): Address already in use
ctrl_iface exists and seems to be in use - cannot override it
Delete '/var/run/wpa_supplicant/wlan0' manually if it is not used anymore
Failed to initialize control interface '/var/run/wpa_supplicant'.
You may have another wpa_supplicant process already running or the file was
left by an unclean termination of wpa_supplicant in which case you will need
to manually remove this file before starting wpa_supplicant again.
Segmentation fault (core dumped)

---

### Post by Rikiji on 2007-10-18
> **victorgreen said:**
> Im also at Penn trying to connect to AirPennNet. Im using iwl4965 though on an Thinkpad X61 with 7.04 Kernel 2.6.22-8. I also followed the instructions on [http://www.sas.upenn.edu/computing/wireless/airpennnet_linux.html](http://www.sas.upenn.edu/computing/wireless/airpennnet_linux.html). 

Connecting via the instructions on the site gives me this:
wpa_supplicant -c /etc/airpennnet.conf -i wlan0 -D iwl4965 -B 
Unsupported driver 'iwl4965'.

But, wext gives me this:
sudo wpa_supplicant -c /etc/airpennnet.conf -i wlan0 -D wext

ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 4 value 0x0 - ioctl[SIOCSIWAUTH]: Operation not supported
WEXT auth param 5 value 0x1 - bind(PF_UNIX): Address already in use
ctrl_iface exists and seems to be in use - cannot override it
Delete '/var/run/wpa_supplicant/wlan0' manually if it is not used anymore
Failed to initialize control interface '/var/run/wpa_supplicant'.
You may have another wpa_supplicant process already running or the file was
left by an unclean termination of wpa_supplicant in which case you will need
to manually remove this file before starting wpa_supplicant again.
Segmentation fault (core dumped)
I'm in Italy, same problem here!
i use iwl4965 drivers.
following the instructions i found on my university website i got the same error you wrote above...
How did you manage to resolve?

---

### Post by Techninja on 2007-11-15
I work at Olympic College were we have a similar set-up (802.1x w/ PEAP / MS-Chapv2).

Is there some way to have it prompt for the username / password whenever I need to connect?  Or is there a way to have the my credentials stored in the config encrypted?  I fall under a strict security policy which prevents me from storing my credentials in plain text.

---

### Post by staticsage on 2007-11-15
Is this connection wired, or wireless?

If it is wireless, then NetworkManager stores and encrypts your credientials.

If you have to authenticate for a wired network, you have to create a wpa_supplicant.conf with your password in plaintext. You can change the read permissions on this file so it cannot be read without root credentials.

If that is not secure enough you can always encrypt the wpa_supplicant.conf. Then write a script to run when you want to connect that will decrypt the file and execute wpa_supplicant. That might be a little overkill, but it is really the only way to do it until NetworkManager supports 802.1x for wired connections.

---

### Post by Soranus on 2007-12-04
UltraMathMan: Thanks for posting this! I've been trying to get the IT people at school to help me figure out how to set up my laptop for their wireless to no avail. They claim it is not possible unless one runs Windows or Mac. Hahahaha! But, it didn't work completely, so I tried setting up a new network the way Randomnumber suggested.

RandomNumber: Between your setup steps and UltraMathMan's changes, I was up and running on the university wireless in less than 10 minutes! 

I've had to use Windows for the past four years at school and, thanks to the school, I got a virus that wiped out my Windows drive. I wiped the drive, and now only have Ubuntu. Thanks!

---

### Post by UltraMathMan on 2007-12-04
Glad you were able to get it working!

---

### Post by Chris Kupka on 2008-02-13
AGH...tried it through network manager, as per the earlier post, but I don't have the etc/ssl/certs/Thawte_Premium_Server_CA.pem file on my computer (nor do I know where to get it).

I have been screwing around w/ the wpa_supplicant using my university's instructions for connection to AirPennNet
([http://www.sas.upenn.edu/computing/wireless/ubuntu/configure.html](http://www.sas.upenn.edu/computing/wireless/ubuntu/configure.html))

my interfaces reads:

auto lo
iface lo inet loopback

auto ath0
iface ath0 inet dhcp
wpa-driver madwifi
wpa-conf /etc/wpa_supplicant.cont

I also executed:

sudo wpa_supplicant -c/etc/wpa_supplicant.conf -i ath0 -D madwifi -d

AND 

sudo wpa_supplicant -c/etc/wpa_supplicant.conf -i ath0 -D madwifi -B

as well as 

sudo ifup ath0

AND, alternatively,

sudo ifdown ath0.

I'm pretty sure I've tried every possible permutation.

when I enter:

sudo /etc/init.d/networking restart

it tells me there there are 

No DHCPOFFERS received.
No working leases in persistent database - sleeping.

when wpa_supplicant takes over network manager, I can still connect to other wireless networks, though I lose the gnome-network manager icon.  For now I have deleted the ath0 line from my /etc/network/interfaces file to be able to use the network manager.

I still can't connect to my university's wireless, and the whole school shifts over in April (right before law school exams start up).

HELP!!!?!?!?!?!

---

### Post by Chris Kupka on 2008-02-13
typo - where it says wpa_supplicant.cont I meant wpa_supplicant.conf

My legal writing instructor is right...always proofread...

---

### Post by Chris Kupka on 2008-02-13
OK, so, the IT people who gave me the wpa_supplicant.conf file had "airsas" listed as their ssid, which I suppose works if you are trying to connect to the School of Arts and Sciences (SAS...).  After changing that to "airpennnet", the name of the wireless I am trying to connect to, I get an actual output for

sudo wpa_supplicant -c/etc/wpa_supplicant.conf -i ath0 -D madwifi -d

the output will seemingly go all night (I'm going to let it, I need some sleep).  It still "fails to associate with AirPennNet", however.

I'm at my wits end.

---

### Post by UltraMathMan on 2008-02-13
> **Chris Kupka said:**
> AGH...tried it through network manager, as per the earlier post, but I don't have the etc/ssl/certs/Thawte_Premium_Server_CA.pem file on my computer (nor do I know where to get it).

You may need to do ```
sudo apt-get install ca-certificates
``` to get the certificates - otherwise you can get them from the [thawte Root Certificate Download Page]("http://www.thawte.com/roots/"). 

Have things been working any better since your last post?

---

### Post by Chris Kupka on 2008-02-18
I got the certificates, and it gets the process one step further, but it still ends in error.

I think the problem is the line:

EAPOL: Could not get master key for decrypting EAPOL-Key keys

After

SSL: (however many) bytes pending from ssl-out
SSL: (however many) bytes left to be sent out (of total (however many) bytes)

it kicks out

EAP: method process -> ignore=FALSE methodState=MAY_CONT decision=FAIL

That happens a few times, until I get:

CTRL-EVENT-EAP-FAILURE EAP authentication failed

Eventually it ends on:

EAPOL: startWhen --> 0

at which point it waits a few minutes, starts all over again, and ends the same way.

I can send you the entire output, if need be.

Thanks.

---

### Post by kripz on 2008-05-07
Ive tried everything to connect to my schools wireless. Can someone please take some time to figure it out for me? the IT Technicians dont support linux.

Links to guides:
[Wireless networking Windows (1234 KB)]("http://www.deakin.edu.au/its/publications/userguide-wireless-networking-winxp.pdf")
[Wireless networking Macintosh (791 KB) ]("http://www.deakin.edu.au/its/publications/userguide-wireless-networking-mac.pdf")

Ive tried:

WPA Enterprise and WPA2 Enterprise
PEAP
Automatic and TKIP and TTLS and AES-CCMP
[email]username@deakin.edu.au[/email]
password (in ascii, no special encoding)
Client cert blank
Server cert set to /etc/ssl/cert/Thawte_Premium_Server_CA.pem and blank
blank private key file
blank private key and my password (in ascii, no special encoding)

---

### Post by jhwilliams on 2008-08-27
I have iwl3945, and followed the directions as they are; but it's not working for me. I'm at Lehigh. Here's the output when I try to kick off wpa_supplicant manually. Ideas?


```
sudo wpa_supplicant -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf -dd

Initializing interface 'wlan0' conf '/etc/wpa_supplicant/wpa_supplicant.conf' driver 'default' ctrl_interface 'N/A' bridge 'N/A'
Configuration file '/etc/wpa_supplicant/wpa_supplicant.conf' -> '/etc/wpa_supplicant/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
ctrl_interface_group='0' (DEPRECATED)
Line: 3 - start of a new network block
ssid - hexdump_ascii(len=2):
     6c 75                                             lu              
scan_ssid=1 (0x1)
key_mgmt: 0x8
eap methods - hexdump(len=16): 00 00 00 00 19 00 00 00 00 00 00 00 00 00 00 00
phase2 - hexdump_ascii(len=13):
     61 75 74 68 3d 4d 53 43 48 41 50 56 32            auth=MSCHAPV2   
identity - hexdump_ascii(len=8):
     75 73 65 72 6e 61 6d 65                           username        
password - hexdump_ascii(len=12): [REMOVED]
Priority group 0
   id=0 ssid='lu'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
SIOCGIWRANGE: WE(compiled)=22 WE(source)=21 enc_capa=0xf
  capabilities: key_mgmt 0xf enc 0xf
WEXT: Operstate: linkmode=1, operstate=5
Own MAC address: 00:1f:3c:45:e7:38
wpa_driver_wext_set_wpa
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
wpa_driver_wext_set_countermeasures
wpa_driver_wext_set_drop_unencrypted
Setting scan request: 0 sec 100000 usec
ctrl_interface_group=0
Added interface wlan0
RTM_NEWLINK: operstate=0 ifi_flags=0x1002 ()
Wireless event: cmd=0x8b06 len=12
Ignore event for foreign ifindex 3
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=2):
     6c 75                                             lu              
Trying to get current scan results first without requesting a new scan to speed up initial association
Received 0 bytes of scan results (0 BSSes)
Scan results: 0
Selecting BSS from priority group 0
Try to find WPA-enabled AP
Try to find non-WPA AP
No suitable AP found.
Setting scan request: 0 sec 0 usec
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b19 len=16
Received 1820 bytes of scan results (7 BSSes)
Scan results: 7
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 02:13:ce:00:00:bd ssid='Kbar' wpa_ie_len=0 rsn_ie_len=0 caps=0x12
   skip - no WPA/RSN IE
1: 00:18:ba:5b:5e:90 ssid='lu' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:1c:10:74:56:ca ssid='shruti' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
3: 00:1a:70:d9:ac:80 ssid='IloveAprilJonesalsocliffsucks' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
4: 00:18:4d:4b:2d:40 ssid='KariB' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
5: 00:16:b6:0e:f7:d4 ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
6: 00:1f:33:23:f9:d4 ssid='KPLS' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 02:13:ce:00:00:bd ssid='Kbar' wpa_ie_len=0 rsn_ie_len=0 caps=0x12
   skip - SSID mismatch
1: 00:18:ba:5b:5e:90 ssid='lu' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   selected non-WPA AP 00:18:ba:5b:5e:90 ssid='lu'
Trying to associate with 00:18:ba:5b:5e:90 (SSID='lu' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: clearing own WPA/RSN IE
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b04 len=16
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=18
Authentication with 00:00:00:00:00:00 timed out.
Added BSSID 00:18:ba:5b:5e:90 into blacklist
No keys have been configured - skip key clearing
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=2):
     6c 75                                             lu              
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b19 len=16
Received 766 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 02:13:ce:00:00:bd ssid='Kbar' wpa_ie_len=0 rsn_ie_len=0 caps=0x12
   skip - no WPA/RSN IE
1: 00:18:ba:5b:5e:90 ssid='lu' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:1f:33:23:f9:d4 ssid='KPLS' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 02:13:ce:00:00:bd ssid='Kbar' wpa_ie_len=0 rsn_ie_len=0 caps=0x12
   skip - SSID mismatch
1: 00:18:ba:5b:5e:90 ssid='lu' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   selected non-WPA AP 00:18:ba:5b:5e:90 ssid='lu'
Trying to associate with 00:18:ba:5b:5e:90 (SSID='lu' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: clearing own WPA/RSN IE
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b04 len=16
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=18
Authentication with 00:00:00:00:00:00 timed out.
BSSID 00:18:ba:5b:5e:90 blacklist count incremented to 2
No keys have been configured - skip key clearing
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b19 len=16
Received 997 bytes of scan results (4 BSSes)
Scan results: 4
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 02:13:ce:00:00:bd ssid='Kbar' wpa_ie_len=0 rsn_ie_len=0 caps=0x12
   skip - no WPA/RSN IE
1: 00:1a:70:d9:ac:80 ssid='IloveAprilJonesalsocliffsucks' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:1f:33:23:f9:d4 ssid='KPLS' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
3: 00:0b:6b:32:ba:18 ssid='S_BETHLM_KIZ1440' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 02:13:ce:00:00:bd ssid='Kbar' wpa_ie_len=0 rsn_ie_len=0 caps=0x12
   skip - SSID mismatch
1: 00:1a:70:d9:ac:80 ssid='IloveAprilJonesalsocliffsucks' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:1f:33:23:f9:d4 ssid='KPLS' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
3: 00:0b:6b:32:ba:18 ssid='S_BETHLM_KIZ1440' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No APs found - clear blacklist and try again
Removed BSSID 00:18:ba:5b:5e:90 from blacklist (clear)
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 02:13:ce:00:00:bd ssid='Kbar' wpa_ie_len=0 rsn_ie_len=0 caps=0x12
   skip - no WPA/RSN IE
1: 00:1a:70:d9:ac:80 ssid='IloveAprilJonesalsocliffsucks' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:1f:33:23:f9:d4 ssid='KPLS' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
3: 00:0b:6b:32:ba:18 ssid='S_BETHLM_KIZ1440' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 02:13:ce:00:00:bd ssid='Kbar' wpa_ie_len=0 rsn_ie_len=0 caps=0x12
   skip - SSID mismatch
1: 00:1a:70:d9:ac:80 ssid='IloveAprilJonesalsocliffsucks' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
2: 00:1f:33:23:f9:d4 ssid='KPLS' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
3: 00:0b:6b:32:ba:18 ssid='S_BETHLM_KIZ1440' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=2):
     6c 75                                             lu              
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b19 len=16
Received 1290 bytes of scan results (5 BSSes)
Scan results: 5
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 02:13:ce:00:00:bd ssid='Kbar' wpa_ie_len=0 rsn_ie_len=0 caps=0x12
   skip - no WPA/RSN IE
1: 00:18:ba:5b:5e:90 ssid='lu' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:1a:70:e1:f9:24 ssid='bejlehem' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
3: 00:12:0e:89:fe:81 ssid='07FX09042817' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
4: 00:1f:33:23:f9:d4 ssid='KPLS' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 02:13:ce:00:00:bd ssid='Kbar' wpa_ie_len=0 rsn_ie_len=0 caps=0x12
   skip - SSID mismatch
1: 00:18:ba:5b:5e:90 ssid='lu' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   selected non-WPA AP 00:18:ba:5b:5e:90 ssid='lu'
Trying to associate with 00:18:ba:5b:5e:90 (SSID='lu' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: clearing own WPA/RSN IE
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b04 len=16
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=18
Authentication with 00:00:00:00:00:00 timed out.
Added BSSID 00:18:ba:5b:5e:90 into blacklist
No keys have been configured - skip key clearing
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b19 len=16
Received 716 bytes of scan results (3 BSSes)
Scan results: 3
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 02:13:ce:00:00:bd ssid='Kbar' wpa_ie_len=0 rsn_ie_len=0 caps=0x12
   skip - no WPA/RSN IE
1: 00:1f:33:23:f9:d4 ssid='KPLS' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
2: 00:0b:6b:34:9a:0f ssid='S_BETHLM_KIZ0790' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 02:13:ce:00:00:bd ssid='Kbar' wpa_ie_len=0 rsn_ie_len=0 caps=0x12
   skip - SSID mismatch
1: 00:1f:33:23:f9:d4 ssid='KPLS' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
2: 00:0b:6b:34:9a:0f ssid='S_BETHLM_KIZ0790' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No APs found - clear blacklist and try again
Removed BSSID 00:18:ba:5b:5e:90 from blacklist (clear)
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 02:13:ce:00:00:bd ssid='Kbar' wpa_ie_len=0 rsn_ie_len=0 caps=0x12
   skip - no WPA/RSN IE
1: 00:1f:33:23:f9:d4 ssid='KPLS' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
2: 00:0b:6b:34:9a:0f ssid='S_BETHLM_KIZ0790' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 02:13:ce:00:00:bd ssid='Kbar' wpa_ie_len=0 rsn_ie_len=0 caps=0x12
   skip - SSID mismatch
1: 00:1f:33:23:f9:d4 ssid='KPLS' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
2: 00:0b:6b:34:9a:0f ssid='S_BETHLM_KIZ0790' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No suitable AP found.
Setting scan request: 5 sec 0 usec
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=2):
     6c 75                                             lu              
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b19 len=16
Received 1590 bytes of scan results (6 BSSes)
Scan results: 6
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1d:7e:c9:9a:ed ssid='Hercules' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 02:13:ce:00:00:bd ssid='Kbar' wpa_ie_len=0 rsn_ie_len=0 caps=0x12
   skip - no WPA/RSN IE
2: 00:18:ba:5b:5e:90 ssid='lu' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
3: 00:12:0e:7d:7e:b0 ssid='07B405806284' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
4: 00:12:0e:89:97:70 ssid='APT403' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
5: 00:1f:33:23:f9:d4 ssid='KPLS' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:1d:7e:c9:9a:ed ssid='Hercules' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 02:13:ce:00:00:bd ssid='Kbar' wpa_ie_len=0 rsn_ie_len=0 caps=0x12
   skip - SSID mismatch
2: 00:18:ba:5b:5e:90 ssid='lu' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   selected non-WPA AP 00:18:ba:5b:5e:90 ssid='lu'
Trying to associate with 00:18:ba:5b:5e:90 (SSID='lu' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: clearing own WPA/RSN IE
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b04 len=16
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=18
Authentication with 00:00:00:00:00:00 timed out.
Added BSSID 00:18:ba:5b:5e:90 into blacklist
No keys have been configured - skip key clearing
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b19 len=16
Received 1290 bytes of scan results (5 BSSes)
Scan results: 5
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 02:13:ce:00:00:bd ssid='Kbar' wpa_ie_len=0 rsn_ie_len=0 caps=0x12
   skip - no WPA/RSN IE
1: 00:18:ba:5b:5e:90 ssid='lu' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:18:3a:a7:16:c9 ssid='08FX04053964' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
3: 00:1c:10:74:56:ca ssid='shruti' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
4: 00:16:b6:0e:f7:d4 ssid='' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 02:13:ce:00:00:bd ssid='Kbar' wpa_ie_len=0 rsn_ie_len=0 caps=0x12
   skip - SSID mismatch
1: 00:18:ba:5b:5e:90 ssid='lu' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   selected non-WPA AP 00:18:ba:5b:5e:90 ssid='lu'
Trying to associate with 00:18:ba:5b:5e:90 (SSID='lu' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: clearing own WPA/RSN IE
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b04 len=16
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=18
Authentication with 00:00:00:00:00:00 timed out.
BSSID 00:18:ba:5b:5e:90 blacklist count incremented to 2
No keys have been configured - skip key clearing
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=2):
     6c 75                                             lu              
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b19 len=16
Received 1332 bytes of scan results (5 BSSes)
Scan results: 5
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1c:10:31:cf:30 ssid='nicksnet' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 02:13:ce:00:00:bd ssid='Kbar' wpa_ie_len=0 rsn_ie_len=0 caps=0x12
   skip - no WPA/RSN IE
2: 00:18:ba:5b:5e:90 ssid='lu' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - blacklisted
3: 00:12:0e:89:fe:81 ssid='07FX09042817' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
4: 00:1f:33:23:f9:d4 ssid='KPLS' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:1c:10:31:cf:30 ssid='nicksnet' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 02:13:ce:00:00:bd ssid='Kbar' wpa_ie_len=0 rsn_ie_len=0 caps=0x12
   skip - SSID mismatch
2: 00:18:ba:5b:5e:90 ssid='lu' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - blacklisted
3: 00:12:0e:89:fe:81 ssid='07FX09042817' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
4: 00:1f:33:23:f9:d4 ssid='KPLS' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No APs found - clear blacklist and try again
Removed BSSID 00:18:ba:5b:5e:90 from blacklist (clear)
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 00:1c:10:31:cf:30 ssid='nicksnet' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 02:13:ce:00:00:bd ssid='Kbar' wpa_ie_len=0 rsn_ie_len=0 caps=0x12
   skip - no WPA/RSN IE
2: 00:18:ba:5b:5e:90 ssid='lu' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
3: 00:12:0e:89:fe:81 ssid='07FX09042817' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
4: 00:1f:33:23:f9:d4 ssid='KPLS' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 00:1c:10:31:cf:30 ssid='nicksnet' wpa_ie_len=26 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
1: 02:13:ce:00:00:bd ssid='Kbar' wpa_ie_len=0 rsn_ie_len=0 caps=0x12
   skip - SSID mismatch
2: 00:18:ba:5b:5e:90 ssid='lu' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   selected non-WPA AP 00:18:ba:5b:5e:90 ssid='lu'
Trying to associate with 00:18:ba:5b:5e:90 (SSID='lu' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: clearing own WPA/RSN IE
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b04 len=16
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=18
Authentication with 00:00:00:00:00:00 timed out.
Added BSSID 00:18:ba:5b:5e:90 into blacklist
No keys have been configured - skip key clearing
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (broadcast SSID)
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b19 len=16
Received 1234 bytes of scan results (5 BSSes)
Scan results: 5
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 02:13:ce:00:00:bd ssid='Kbar' wpa_ie_len=0 rsn_ie_len=0 caps=0x12
   skip - no WPA/RSN IE
1: 00:18:ba:5b:5e:90 ssid='lu' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:12:0e:89:fe:81 ssid='07FX09042817' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
3: 00:0b:6b:34:9a:0f ssid='S_BETHLM_KIZ0790' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
4: 00:1f:33:23:f9:d4 ssid='KPLS' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 02:13:ce:00:00:bd ssid='Kbar' wpa_ie_len=0 rsn_ie_len=0 caps=0x12
   skip - SSID mismatch
1: 00:18:ba:5b:5e:90 ssid='lu' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   selected non-WPA AP 00:18:ba:5b:5e:90 ssid='lu'
Trying to associate with 00:18:ba:5b:5e:90 (SSID='lu' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: clearing own WPA/RSN IE
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b04 len=16
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=18
Authentication with 00:00:00:00:00:00 timed out.
BSSID 00:18:ba:5b:5e:90 blacklist count incremented to 2
No keys have been configured - skip key clearing
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
Setting scan request: 0 sec 0 usec
State: DISCONNECTED -> SCANNING
Starting AP scan (specific SSID)
Scan SSID - hexdump_ascii(len=2):
     6c 75                                             lu              
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b19 len=16
Received 1024 bytes of scan results (4 BSSes)
Scan results: 4
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 02:13:ce:00:00:bd ssid='Kbar' wpa_ie_len=0 rsn_ie_len=0 caps=0x12
   skip - no WPA/RSN IE
1: 00:18:ba:5b:5e:90 ssid='lu' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - blacklisted
2: 00:12:0e:89:97:70 ssid='APT403' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
3: 00:1f:33:23:f9:d4 ssid='KPLS' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 02:13:ce:00:00:bd ssid='Kbar' wpa_ie_len=0 rsn_ie_len=0 caps=0x12
   skip - SSID mismatch
1: 00:18:ba:5b:5e:90 ssid='lu' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - blacklisted
2: 00:12:0e:89:97:70 ssid='APT403' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - SSID mismatch
3: 00:1f:33:23:f9:d4 ssid='KPLS' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - SSID mismatch
No APs found - clear blacklist and try again
Removed BSSID 00:18:ba:5b:5e:90 from blacklist (clear)
Selecting BSS from priority group 0
Try to find WPA-enabled AP
0: 02:13:ce:00:00:bd ssid='Kbar' wpa_ie_len=0 rsn_ie_len=0 caps=0x12
   skip - no WPA/RSN IE
1: 00:18:ba:5b:5e:90 ssid='lu' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
2: 00:12:0e:89:97:70 ssid='APT403' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   skip - no WPA/RSN IE
3: 00:1f:33:23:f9:d4 ssid='KPLS' wpa_ie_len=0 rsn_ie_len=0 caps=0x1
   skip - no WPA/RSN IE
Try to find non-WPA AP
0: 02:13:ce:00:00:bd ssid='Kbar' wpa_ie_len=0 rsn_ie_len=0 caps=0x12
   skip - SSID mismatch
1: 00:18:ba:5b:5e:90 ssid='lu' wpa_ie_len=0 rsn_ie_len=0 caps=0x11
   selected non-WPA AP 00:18:ba:5b:5e:90 ssid='lu'
Trying to associate with 00:18:ba:5b:5e:90 (SSID='lu' freq=2437 MHz)
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: clearing own WPA/RSN IE
No keys have been configured - skip key clearing
wpa_driver_wext_set_drop_unencrypted
State: SCANNING -> ASSOCIATING
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
wpa_driver_wext_associate
Setting authentication timeout: 10 sec 0 usec
EAPOL: External notification - portControl=Auto
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b06 len=12
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b04 len=16
RTM_NEWLINK: operstate=0 ifi_flags=0x1003 ([UP])
Wireless event: cmd=0x8b1a len=18
CTRL-EVENT-TERMINATING - signal 2 received
Removing interface wlan0
State: ASSOCIATING -> DISCONNECTED
wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT)
WEXT: Operstate: linkmode=-1, operstate=5
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
wpa_driver_wext_set_wpa
wpa_driver_wext_set_drop_unencrypted
wpa_driver_wext_set_countermeasures
No keys have been configured - skip key clearing
Cancelling scan request
Cancelling authentication timeout
WEXT: Operstate: linkmode=0, operstate=6
```

---

### Post by jhwilliams on 2008-08-28
Okay! Solved the problem above. iwlwifi 1.20 in ubuntu hardy 8.04 -19-generic is broken (well, not completely, but can't do 8021x.)

so, unload the iwlwifi module, and build/install the latest compat-wireless stuff. Check out the compat-wireless project: [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)

---

### Post by UltraMathMan on 2008-08-28
Nice, I was scratching my head over that output.

---

### Post by silverhammermba on 2010-10-13
Sorry to dredge this thread up from prehistory, but I'm trying to connect to Lehigh's network on 10.04. I've configured everything according to the OP, but with no luck.

The only informative thing I've tried is:
```
$sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant/wpa_supplicant.conf
Trying to associate with 00:1e:7a:ab:c0:10 (SSID='lu' freq=2462 MHz)
Association request to the driver failed
Associated with 00:1e:7a:ab:c0:10
Authentication with 00:1e:7a:ab:c0:10 timed out.
```
And it just keeps doing that over and over again with a bunch of different 'lu' connections with different mac addresses, failing every time with a time out. Every now and then it throws in some
```
ioctl[SIOCSIWMLME]: Link has been severed
ioctl[SIOCSIWAP]: Operation not permitted
ioctl[SIOCSIWESSID]: Operation not permitted
```
and
```
CTRL-EVENT-EAP-STARTED EAP authentication started
```
but it keeps failing. I've left it running for quite a while but I don't think it gets anywhere.

I'm sure that wlan0 is the correct interface, but I'm not sure about the driver. Does the "driver failed" stuff mean that it isn't?

Also I'm wondering about what I should put in my /etc/network/interfaces file. Right now it's
```
auto lo
iface lo inet loopback

iface wlan0 inet dhcp
   wpa-driver wext
   wpa-conf /etc/wpa_supplicant/wpa_supplicant.conf
```

What could I be doing wrong? Or is there something I just haven't tried yet?

---

### Post by staticsage on 2010-10-13
What wireless card do you have? Was it not detected properly on install?

Depending on your wireless card, you shouldn't have to use wpa_supplicant any more. Ubuntu should detect your card and install an open source driver or suggest a binary through the Restricted Hardware / Additional Drivers feature (I don't remember which it was called in 10.04).

As far as configuring connectivity to a network, NetworkManager (tray icon) should really be taking care of it for you. I believe it has supported 802.1x for both wired and wireless for a while now.

---

### Post by silverhammermba on 2010-10-13
Oops, I just assumed the option still wasn't there. I'm still kind of having an issue. I selected the options in Network manager based on the OP.

Wireless Security: Dynamic WEP (802.1x)
Authentication: Protected EAP
Anonymous Identity: 
CA certificate: (None)
PEAP version: Automatic
Inner authentication: MSCHAPv2
Username: myusername
Password: mypassword

The ones I'm not sure about are CA certificate and anonymouse identity. I'm assuming the latter can be left blank, but where the hell would I get a certificate from? When connecting through Windows you don't need to manually supply one (I'm not sure if its acquired automatically or somesuch).

**Edit:**Issue resolved. I tried again and it worked.

---

### Post by staticsage on 2010-10-13
> **silverhammermba said:**
> 

**Edit:**Issue resolved. I tried again and it worked.

Glad it worked!

---

### Post by silverhammermba on 2010-10-13
Heh, new problem now! I can connect to the lu network but every couple of minutes, I get disconnected and reconnected. Sometimes it re-prompts me for the security information as well. It's very annoying!

I think it's because there are a whole bunch of lu access points and for some reason it keeps switching me between them. If I do 'iwlist wlan0 scan' it comes up with a whole bunch of 'lu' entries, all with different addresses (and varying signal strengths).

I think that if I add each access point as a separate wireless network it stops prompting me for security information - making the random disconnect reconnects slightly less annoying - but so far I already have 15 different addresses. Who knows how many more I would find if I use my netbook somewhere else on campus.

Is there some way I can make it pick an 'lu' and stick to it? Or to switch between them without prompting me when it finds a new one?

---

### Post by staticsage on 2010-10-13
Most of these modern mesh type networks with multiple access points should allow you to 'roam' between APs. When you are prompted for your login information again it is usually because the authentication process to an AP fails (most likely due to a weak signal).

There may be better drivers available for the card you are using, but someone else will likely have to point you in the right direction for that as I don't actually have that card and have not tested drivers.

It has been a while since I worked on wireless issues, but try this first. Determine what driver you're using:

```
lshw -C network
```

From my brief research, I believe there are two for the card, ipw3945 and iwlwifi. Unfortunately most of the information on issues with this card is very old. Does any hardware come up in restricted hardware?


EDIT: By the way, you might want to search for signal issues or create a new thread for the new issue.

---

