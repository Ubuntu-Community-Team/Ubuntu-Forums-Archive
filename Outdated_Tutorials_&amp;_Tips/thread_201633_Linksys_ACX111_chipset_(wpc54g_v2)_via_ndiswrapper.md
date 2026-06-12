---
title: "Linksys ACX111 chipset (wpc54g v2) via ndiswrapper"
date: 2006-06-22
forum: Outdated Tutorials &amp; Tips
---

### Post by dmizer on 2006-06-22
[COLOR="Red"]I am officially retiring this thread.

You can make this card work by changing dapper's native acx module firmware using **Kobalt's** method instead of this howto. It integrates with network manager and there's not nearly as much CLI editing involved (just three lines).  You can find well written directions for it here: [http://www.ubuntuforums.org/showthread.php?t=233565&highlight=wpc54g](http://www.ubuntuforums.org/showthread.php?t=233565&highlight=wpc54g)

To make this card work in any distribution after Edgy, try this link: [http://www.ubuntuforums.org/showthread.php?t=324148](http://www.ubuntuforums.org/showthread.php?t=324148)[/COLOR]
I can no longer make the following method work to enable my wpc54g v2 card in Dapper.

Disclaimers:
======================================
This how to is specific to THIS card; however, it may be adapted to work on other cards.  The chipset in question here is the Texas instruments ACX111 chipset.  I have no experience with any other wireless cards other than the ones in my possession, so if you have a Linksys card but it does not have an ACX111 chipset, I will not likely be able to assist you.  Furthermore, most cards containing this chipset seem to work "out of the box".

I have not tested, nor will I be able to test WEP as I am using a wireless HUB without encryption capabilities.  Brickferd has tested and successfuly enabled encryption using this method.  Directions appear at the end of this thread as well as in post number [23]("http://www.ubuntuforums.org/showpost.php?p=1315230&postcount=23").

Also note, most of this has been pulled from an existing thread here: [http://www.ubuntuforums.org/showthread.php?t=5645](http://www.ubuntuforums.org/showthread.php?t=5645) so if what follows doesn't help you, you may find your answer there.

I have foccused on CLI interface instructions to allow this method to work in any of the winodow managers supported in the Ubuntu line (mine happened to be icewm).
======================================

**First of all,  you're going to need ndiswrapper installed:**

This howto does not require the cvs version of ndiswrapper, so the one in the universe repos will be fine (note: If you already have the cvs version installed, I cannot garantee this method).  Just make sure you get both the ndiswrapper, and the ndisgtk packages.

Just open synaptic, search for ndiswrapper and both packages should appear.

**Next, you&#8217;re going to need the windows driver:**

Create a directory in your home folder called linksys:
```
cd
mkdir linksys
cd linksys
```

Download the windows driver from Linksys:
```
wget ftp://ftp.linksys.com/pub/network/wpc54g_v2_driver_utility_v2.0.zip
```

Extract the archive:
```
unzip wpc54g_v2_driver_utility_v2.0.zip
```

(special thanks to [yellow5]("http://ubuntuforums.org/showpost.php?p=1016180&postcount=68") for the next step)
linux is case sensitive for file names, but windows is not, so there's a little file name snafu that we have to fix before we can move on.
- tnet1130.sys should be TNET1130.sys
- LSTINDS4.sys should be Lstinds4.sys
```
mv tnet1130.sys TNET1130.sys
mv LSTINDS4.sys Lstinds4.sys
```

**Load the driver into ndiswrapper for the module:**
```
sudo ndiswrapper -i lsbcmnds.inf
sudo ndiswrapper -i LSTINDS.INF
sudo modprobe ndiswrapper
```

**With your WPC54g ver. 2 card in the PCMCIA slot, check to make sure ndiswrapper correctly loaded the card:**
```
ndiswrapper -l
```
[SIZE="1"]note: this is a lower case L, not an upper case i or the number one.[/SIZE]

You should get output that looks something like this:
```
Installed drivers:
lsbcmnds                driver installed
lstinds         driver installed, hardware present
```
If not, you may need to go back and review some of the steps or take a look at the wiki here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)

**Now we associate the module with the card:**
At this point, my card still did not have a power light because Ubuntu is trying to load the acx_pci module to drive this card.  But the acx_pci module won't drive the card (thanks to [blazerte]("http://http://www.ubuntuforums.org/member.php?u=37632") for this tip).  There were other modules trying to load for this card too.  [SIZE="3"]*You can remove them with [size="2"][FONT="Lucida Console"]sudo modprope -r modulename[/FONT][/size] and then blacklisting them*[/SIZE], but I wanted the ndiswrapper module to load automatically for this card.  This can be done by making an entry in /etc/pcmcia/config.opts as follows:

First, you need to figure out what Ubuntu calls your card.  Just look at the entry for your card in lspci:
```
lspci
```
and it should give an output similar to this:
```
0000:06:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
```

**_The following step listed in grey is not needed_** (left here for my own reference)
[COLOR="Silver"]
#Next, you need to know the manfid:
```
cardctl ident
```
#and the output should look similar to this:
```
Socket 0:
  no product info available
Socket 1:
  no product info available
  manfid: 0xf7ff, 0xfe5b
```
[/color]
**_Resume howto from here:_**

Now, using the above information we can edit pcmcia config with a new entry.  Using your favorite editor (mine's nano) edit /etc/pcmcia/config.opts and add the following lines (adjusting yours so that it matches the output of lspci and cardctl ident from above)
```
card "Texas Instruments ACX 111 54Mbps Wireless Interface"
  bind "ndiswrapper"
```

**Add ndiswrapper to your modules file so that it will be included on boot up:**
```
sudo echo ndiswrapper >> /etc/modules
```

**Restart your network:**
```
sudo /etc/init.d/networking restart
```
Your power light should come on (if not, try rebooting). Also check iwconfig and you should have wlan0 listed.

**Finally, connecting to the internet:**.

This card needs a scan before it can accept wireless settings. But you can't add wireless settings while the card is up, thus making it difficult to connect after entering the wireless settings becase the whole process is time sensitive.  To get around this, I just splice the whole command together with && like so:
```
sudo iwlist wlan0 scan&& sudo iwconfig wlan0 channel 1 essid youressid mode Managed&& sudo ifup wlan0
```
If you don't already know what your network settings are, you can just scan ([size="1"][FONT="Lucida Console"]sudo iwlist wlan0 scan[/font][/size]) first and then edit the above string to your settings.

At this point, your card should be connected, however, the link light will not come on. You can check ifconfig to verify that you have a dhcp lease.

Just a few additional notes:

Thanks to [brickferd]("http://ubuntuforums.org/member.php?u=139961"), for the following information on wep in post [23]("http://www.ubuntuforums.org/showpost.php?p=1315230&postcount=23"):
You should also be able to enable encryption by adding &#8220;key open XXXXXXXXXXXXXXXX&#8221;, where X is your key in hex format, to the end of this section: [size="1"][FONT="Lucida Console"]&#8220;sudo iwconfig wlan0 channel 1 essid youressid mode Managed&#8221;[/font][/size]

Though you will not have to load the ndiswrapper module at every boot, you will have to issue the &#8220;sudo iwlist wlan0 ...&#8221; command at every boot. I included it in a startup script so it comes up &#8220;automatically&#8221;. Sloppy, but it works.

If you get an error that reads "Ignoring unknown interface wlan0=wlan0" you can fix it by doing the following:
(Breezy only) Edit /etc/network/run/ifstate to include the line [size="1"][FONT="Lucida Console"]wlan0=wlan0[/font][/size].

(Dapper and Breezy) Include [size="1"][FONT="Lucida Console"]iface wlan0 inet dhcp[/font][/size] (or the appropriate static references) in /etc/network/interfaces.

Any problems, post 'em and I'll do what I can to help.

---

### Post by Agent86 on 2006-06-22
I'm using a ACX111-based Netgear WG311v2 card in Dapper. I found that ndiswrapper is unnecessary UNLESS you are using WPA encryption.

Out of the box, Dapper detects the ACX card and loads the native Linux driver. However, you may need to edit a couple of files to get it to work.

[This]("http://ubuntuforums.org/showpost.php?p=780673&postcount=2") post tells you how to edit your /etc/network/interfaces file. However, if you still can't see your access point after doing a scan, you may need to change the firmware version that Ubuntu loads (it may not be compatible with your particular card).

[This]("http://ubuntuforums.org/showpost.php?p=1063861&postcount=2")  post tells you how to change the firmware version that Ubuntu loads.

If you need WPA encryption, you are living in "interesting times." [This]("http://www.ubuntuforums.org/showpost.php?p=703020&postcount=1") post details the steps I had to take to get WPA working (Following the instructions under the "Downloading required tools" section, then skipping down to the "Network Manager and Dependencies" section) Yes, I tried the Network Manager, wpa_supplicant, and ndiswrapper packages in the repositories, but they didn't get WPA working on my card.

---

### Post by dmizer on 2006-06-22
[QUOTE=Agent86]I'm using a ACX111-based Netgear WG311v2 card in Dapper. I found that ndiswrapper is unnecessary UNLESS you are using WPA encryption.[/QUOTE]
Yes, this seems to be true of most of the acx111 based cards EXCEPT the Linksys version.  I really have no idea why this is the case.

---

### Post by Agent86 on 2006-06-22
[QUOTE=dmizer]Yes, this seems to be true of most of the acx111 based cards EXCEPT the Linksys version.  I really have no idea why this is the case.[/QUOTE]
Maybe someone with the your card and Dapper can report on whether the new acx drivers support the Linky now, with or without a firmware version change.

---

### Post by dmizer on 2006-06-22
[QUOTE=Agent86]Maybe someone with the your card and Dapper can report on whether the new acx drivers support the Linky now, with or without a firmware version change.[/QUOTE]
I'm going to test dapper myself this weekend.  There have not been any [firmware updates]("http://www.linksys.com/servlet/Satellite?childpagename=US%2FLayout&packedargs=page%3D2%26cid%3D1115416835852%26c%3DL_Content_C1&pagename=Linksys%2FCommon%2FVisitorWrapper&SubmittedElement=Linksys%2FFormSubmit%2FProductDownloadSearch&sp_prodsku=1115416827032") released for this card since it was new.

This version uses a the Texas Instruments chipset, while the rest of the versions in this line of card use some variation of the Broadcom chipset.

---

### Post by dmizer on 2006-06-26
this works fine in dapper (xubuntu).  also worked in fedora core 5 with a few slight modifications to directory locations etc.

*edit: after a round or two of updates, this card no longer works correctly in dapper.  still working on the problem.

*edit II: modified the howto to reflect the changes necessary to make this card work in dapper or breezy.

---

### Post by dmizer on 2006-07-09
> **Agent86 said:**
> Maybe someone with the your card and Dapper can report on whether the new acx drivers support the Linky now, with or without a firmware version change.

acx drivers crash my dapper within a few minutes, but at least the card is detected and powered now.  have to figure out how to change acx's firmware and see if that helps.

---

### Post by MBro on 2006-07-11
> **dmizer said:**
> acx drivers crash my dapper within a few minutes, but at least the card is detected and powered now.  have to figure out how to change acx's firmware and see if that helps.

Same.  My acx Netgear wg311v2 is recognized out of the box but it cannot see, scan or manually connect to any networks.  Something is messed up with the driver / firmware on the default install.  It worked out of the box in Hoary (whatever the second ubuntu release was).  Even though it worked I still installed ndiswrapper and used the netgear drivers it it greatly boosted my signal strength.  I don't feel the gpl acx drivers are that good.  Still better than broadcom.

Ndis really isn't a hastle.  The only problem I ran into was blacklisting my acx driver.  After I cleared that up wireless has been a breeze.

---

### Post by dmizer on 2006-07-11
> **MBro said:**
> Same.  My acx Netgear wg311v2 is recognized out of the box but it cannot see, scan or manually connect to any networks.  Something is messed up with the driver / firmware on the default install.
indeed there is.  found this bug the other night: [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/30766](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/30766)

looks like there's been a fix posted too.

---

### Post by Zodiac on 2006-07-20
I am trying this in dapper, and the result of "cardctl ident" is:

Socket 0:
  no product info available
Socket 1:
  no product info available

So I can't move to the next step, however, my power lite is on...

---

### Post by HeavyAl on 2006-07-20
> **Agent86 said:**
> I'm using a ACX111-based Netgear WG311v2 card in Dapper. I found that ndiswrapper is unnecessary UNLESS you are using WPA encryption.

Out of the box, Dapper detects the ACX card and loads the native Linux driver. However, you may need to edit a couple of files to get it to work.

[This]("http://ubuntuforums.org/showpost.php?p=780673&postcount=2") post tells you how to edit your /etc/network/interfaces file. However, if you still can't see your access point after doing a scan, you may need to change the firmware version that Ubuntu loads (it may not be compatible with your particular card).

[This]("http://ubuntuforums.org/showpost.php?p=1063861&postcount=2")  post tells you how to change the firmware version that Ubuntu loads.



Just a quick note of caution on this. I tried to use the above links to get my Linksys ACX111 card working (the lights are on, but nobodys home it seems) and it caused me not to be able to load my desktop after reboot. It just hangs after you hit login.

Anyway, its easy enough to fix if you're familiar with a cl-based text editor such as vim. Just login to the failsafe session and remove the entries that are marked in the above solutions.

I'm sure that there are many people who found the above solution useful, but in my case it was touch and go for a few moments and I hope this little note saves someone some frustration.

---

### Post by Zodiac on 2006-07-20
So, this card isn't going to be working in Ubuntu anytime soon eh?

---

### Post by dmizer on 2006-07-20
it will work.  just give me some time.  this howto was written up for breezy, and although i initially succeeded in getting it to work in dapper, i've since run into problems with it.

it would seem that ubuntu thinks this card is a usb adapter rather than a pcmcia adapter.  so i am researching how linux detects usb to correct the problem.

also, your card is hanging the system because the usb driver being assigned to it will lock the pc.  give me a bit more time and i'll either post here or create a new thread.

---

### Post by Zodiac on 2006-07-21
Awesome... if you need any assitance let me know.

Not that I have any idea what I am doing, but maybe I can try out some things for you. 

Lemme know... :)

---

### Post by brickferd on 2006-07-26
All, I'm new to Linux and have been doing quite a bit of reading and this thread FINALLY helped me to get my wpc54g v2 card to at least power up and to be recognized when I run iwconfig.  My problem now is that I cannot get it to associate with the access point.  A scan shows that the access point is out there, but no matter what I try, I can't get it stick.  Any ideas?

Here's my iwconfig readout:

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:10 dBm   Sensitivity=0/3
          RTS thr:4096 B   Fragment thr:4096 B
          Encryption key:XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XX   Security mode:restri cted
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

---

### Post by mfoerster on 2006-07-27
These instructions worked great for me!  I did not update any firmware.  Thanks!!:D

---

### Post by dmizer on 2006-07-27
> **brickferd said:**
> All, I'm new to Linux and have been doing quite a bit of reading and this thread FINALLY helped me to get my wpc54g v2 card to at least power up and to be recognized when I run iwconfig.  My problem now is that I cannot get it to associate with the access point.  A scan shows that the access point is out there, but no matter what I try, I can't get it stick.  Any ideas?

Here's my iwconfig readout:

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:10 dBm   Sensitivity=0/3
          RTS thr:4096 B   Fragment thr:4096 B
          Encryption key:XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XX   Security mode:restri cted
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

first of all, are you using dapper or breezy, because if you're using dapper, it may be that a recent upgrad has fixed the card identification issue i've been having (i haven't had time yet to dig into it).

for troubleshooting your issue, please post the results of:
```
sudo iwlist scan wlan0
```
it looks like you are using encryption, so i'm not sure that i can be of much help because i really can't test it or configure it.

at this point, you may have luck configuring your network with the network gui in system > administration > network.  when i was using breezy with this card, i couldn't get it to work this way because apparently the card needs a scan in order to connect to the correct network but you might have better luck in dapper.

thanks mfoerster, it's good to know i didn't go through all that for nothing ... lol.

---

### Post by brickferd on 2006-07-27
Hey dmizer,

Thanks for the quick reply, I don't have time to run the scan and post results but I can tell you that I'm running dapper.  I know the encrytption might also be a hurdle and I'm planning to turn it off and give it a shot without.  I'm able to go into the gui, and see the network and tell the system to connect and make that the active connection, which it says it has done, but then I get nothing.

I'll post more later, thanks.

---

### Post by dmizer on 2006-07-27
> **Zodiac said:**
> Awesome... if you need any assitance let me know.

Not that I have any idea what I am doing, but maybe I can try out some things for you.

Lemme know... :)
Zodiac: here's what worked for me, try this:

go back and edit pcmcia config.opts:
```
sudo nano /etc/pcmcia/config.opts
```
and completely remove the line about manfid.

test that for me and see if it works.  if so, i'll make the change in the howto permanent.

---

### Post by shinyblue on 2006-07-29
Just wanted to say **thanks **for the pointer to the cardbus/pcmcia thiny - got mine working!:D

kubuntu nuby

---

### Post by brickferd on 2006-07-29
dmizer,

Here's my scan results:

wlan0     Scan completed :
          Cell 01 - Address: 00:0D:88:B8:AA:78
                    ESSID:"This_Better_Work"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-36 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:0C:41:35:61:FA
                    ESSID:"linksys"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-81 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

Thanks again for any help on this!

---

### Post by dmizer on 2006-07-29
brickferd:
first of all, i see you have two access points in range.  something i notice about those two networks is that they are both using the same channel.  i suggest for matters of avoiding possible confusion that you change your access point's channel to something else.  you may not need to do anything more that this to get your card to connect.

for your wep, are you using 128 bit or something else?  you might have more luck using 64 bit wep.  when you enter your hex key for 64 bit wep, you don't need to enter dashes.

also, once you change the channel for your access point, don't forget to change the "sudo iwconfig ..." section to match.

shinyblue:
glad to know it worked for you!

---

### Post by brickferd on 2006-07-29
OK, update.

I re-read the FAQs on ndiswrapper wiki and tried the following:
iwconfig wlan0 key open 'wepkey'

And then: iwconfig wlan0 essid This_Better_Work

And finally!  

root@eric-laptop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"This_Better_Work"
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0D:88:B8:AA:78
          Bit Rate:54 Mb/s   Tx-Power:10 dBm   Sensitivity=0/3
          RTS thr:4096 B   Fragment thr:4096 B
          Encryption key:XXXX-XXXX-XXXX-XXXX-XXXX-XXXX-XX   Security mode:open
          Power Management:off
          Link Quality:100/100  Signal level:-37 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

So this is great, right?  Not so fast, still no access, and furthermore when I run ifconfig, here's the output:

root@eric-laptop:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0B:DB:99:AC:5D
          inet addr:192.168.0.101  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:dbff:fe99:ac5d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1023 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:687360 (671.2 KiB)  TX bytes:178371 (174.1 KiB)
          Interrupt:7

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:181 errors:0 dropped:0 overruns:0 frame:0
          TX packets:181 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:9072 (8.8 KiB)  TX bytes:9072 (8.8 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:0F:66:BE:9E:71
          inet addr:192.168.0.108  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:66ff:febe:9e71/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:49 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7478 (7.3 KiB)  TX bytes:2862 (2.7 KiB)
          Interrupt:11 Memory:f8020000-f8022000


Does it mean anything to see "Ethernet" for both eth0 and wlan0?

I'm sooo close here, thanks for the continued help!

---

### Post by dmizer on 2006-07-29
that's really strange, two ip's.

first of all, go into networking and disable eth0.  you don't have an onboard wireless adapter do you?  also, do change the channel for your network so we're sure you don't have interference from your second access point.

edit: wait, you did ifconfig ... before you ran the connection command, were you connected to the internet via an ethernet cable?  if so, you'll have to disconnect that and run: sudo ifdown eth0.

you can't be connected to the internet twice through two different adapters.  so if you have previous access with your lan cable, you'll have to terminate it before you can get access via your wireless adapter.

good news is that you got an ip.  so once you disable your lan connection, you should be good.  let me know, and i'll update the howto with your information on wep.

---

### Post by brickferd on 2006-07-30
dmizer,

You are the best!  I stumbled my way through turning down eth0 even before I saw your reply and I'm happy to report that I'm up and running on wireless, just like you figured out.  Thanks so much for all of your help with this issue.

---

### Post by dmizer on 2006-07-30
> **brickferd said:**
> dmizer,

You are the best!  I stumbled my way through turning down eth0 even before I saw your reply and I'm happy to report that I'm up and running on wireless, just like you figured out.  Thanks so much for all of your help with this issue.
that's absolutely fantastic.  and thanks for stiking with it and testing out wep for me, i really wasn't sure if it would work or not.

i've updated the howto with your information and a little plug for you ;)

---

### Post by Raistlin355 on 2006-07-30
Ok, I messed around with this card on Dapper Drake 6.06 for about 3 hours.  Cudos to dmizer for making an excellent Howto.  I finally did get the card working after trying everything I could think of and all the forums resources, and it works wonderfully!!!  In the end I used the stock network manager and it worked!  I tried blacklisting the acx driver, thats a no go cause it wouldn't even start.  I tried to change acx's firmware, no go.  I can't confirm this right now but I think for Dapper all you have to do is install the drivers (after the name change of course, I would have never figured that out) and use the network manager to put in your settings.  I also thought that the network manager doesn't work all the time and you can edit the /etc/interfaces file directly.  BTW I am using 128 bit WEP and no problems!!! Again thanks!!

---

### Post by dmizer on 2006-07-30
> **Raistlin355 said:**
> I can't confirm this right now but I think for Dapper all you have to do is install the drivers (after the name change of course, I would have never figured that out) and use the network manager to put in your settings.

glad to know i helped.  if you get network manager to work let me know.  i have not been successful in this.  i think the problem is that the card won't accept settings until it sees a scan.

but if you get it to work, please post back and let us know how you did it.

---

### Post by Zodiac on 2006-08-01
Okay, it worked... sort of... I can get it to connect, but only if I am not running any security (well, 128bit WEP wouldn't work...) and I cannot use Network manager at all...

But there is progress! Still, I may just try to get my D-Link card working... I think that might be easier... 

Thanks!

---

### Post by dmizer on 2006-08-01
zodiac:
with wep, it may not always work the first time through.  this is true even in windows.  sometimes cards have a difficult time with it.

can you post your version of this line:
```
sudo iwlist wlan0 scan&& sudo iwconfig wlan0 channel 1 essid youressid mode Managed key open && sudo ifup wlan0
```
and include the part about your wep key?  i'd like to see if we can get wep working for you.  then if you stick with it, maybe we can give network manager a shot ...
just on a whim, for wep, try this:
```
sudo iwlist wlan0 scan&& sudo iwconfig wlan0 channel 1 essid youressid mode Managed s:mykey enteryourcodeprhasehere&& sudo ifup wlan0
```

---

### Post by gaj555 on 2006-08-04
Hello, I'm a new user to Ubuntu 6.06, and i'm looking to configure my computer for use with a WEP enabled home wireless network. I'm looking for a wireless card (USB or PCI) that will work "out-of-the-box" i.e., so I don't have to configure using "sudo gedit blah blah blah" because it puzzles me :confused: . I have ndiswrapper installed from an attempted installation of a Netgear WG111 but I could never get my head round that. Also i have ndisgtk installed too. I have managed to get the LED on my dongle (wg111) to light up - but thats about it. Are there any wireless cards i can use with no fiddling??

Thanks.

---

### Post by gaj555 on 2006-08-04
Also, according to [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=%28wg111%29%7C%286.06%29](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=%28wg111%29%7C%286.06%29) , isn't the Linksys WMP54G completely and easily compatible?

---

### Post by dmizer on 2006-08-04
well gaj555, i'm terribly sorry you're having so much trouble, but neither of the cards you mention (netgear wg111 or wmp54g) are included in this howto.  furthermore i really don't have any experience with either of these cards.

your best bet at this point is just to review the cards on the link you posted from the wiki and find a card that works out of the box with dapper.  and, if you run into trouble, just ask for help in the forum.

sorry i really can't offer you much more assistence than that.  i only have two wireless cards in my posession a netgear ma401 wireless b which works out of the box, but is slow.  and the card mentioned in this howto (linksys wpc54g v2)

---

### Post by Raistlin355 on 2006-08-04
Ok, since my last post I have not had the card working on my laptop.  I could not figure out why, so I decided to brainstorm.  After thinking about it for awhile I realized that when I had it working was when I was messing around with the "acx" driver that loads at boot.  I had kept it from booting and the card didn't power on.  But I ran the ```
sudo modprobe ndiswrapper
``` command and for some reason ```
sudo ndiswrapper acx
``` and guess what? it worked!!  Now I had no idea that it was the order that the drivers are loading the was keeping the card from working!!  
So if you are having trouble with the card not connecting but powering on try running ```
sudo modprobe -r acx
``` then ```
sudo modprobe ndiswrapper
``` then ```
sudo modprobe acx
``` and see if that don't work!  Good Luck!!

Also I don't seem to have to run the very long scan & setup string anymore, it just works all the time now without any problems.

---

### Post by dmizer on 2006-08-05
Raistlin355, do me a favor and post your output of the following:
```
ndiswrapper -l
```

---

### Post by Raistlin355 on 2006-08-05
Sure ```
Installed ndis drivers:
lsbcmnds                driver present
lstinds         driver present, hardware present

```

You know I thought I would have to use the commands in my previous post every time I booted that machine but I don't.  Weird

---

### Post by dmizer on 2006-08-05
yeah i've been neglecting my updates, so my card has been okay.  once i updated my machine it broke my card again.  i'll have to figure out why it's doing that.  the way i've created this howto, should prevent this card from breaking when updates are uploaded.

if you're having problems, your best bet may simply be to blacklist the acx module, but i'll take a closer look at this tonight some time and see if i can come up with a more perminant solution.

---

### Post by Kobalt on 2006-08-10
The WPC54G v.2 is fully compatible with Dapper, without using Ndiswrapper. Check this out : 
[http://www.ubuntuforums.org/showthread.php?t=233565&highlight=wpc54g]("http://www.ubuntuforums.org/showthread.php?t=233565&highlight=wpc54g")

Cheers ! :rolleyes:

---

### Post by dmizer on 2006-08-10
thanks kobalt!  i'll link you up in the first post of my howto :)

---

### Post by Raistlin355 on 2006-08-10
dmizer, did you try kobalt's solution?  Did it work cause I could not get it to work, but I was using another howto that wasn't as specific as kobalt's and I don't feel like breaking the wireless on the computer just to experiment.

---

### Post by dmizer on 2006-08-10
i suppose i should test it before i pimp it huh? lol.  i will try it tonight after i get home from work.  played with it a bit this morning, but i was distracted ;)

the only thing is, i know that the only problem with the acx driver packeged by default with dapper is the firmware.  otherwise it should work.

there have been reports that the acx driver is significantly slower than ndiswrapper.  but the trade off is that i believe this card will work correctly with network manager when using the acx driver.  so once you get it installed, you don't have to mess with the command line anymore.

if you want to try it, you can do so without breaking your current setup.  all you have to do is follow the directions given by Kobalt.  additionally you will have to change /etc/pcmcia/config.opts to read as follows:
```
card "Texas Instruments ACX 111 54Mbps Wireless Interface"
  bind "acx"
```
and restart your network:
```
sudo /etc/init.d/networking restart
```
once you've done that, then the card will load with the acx driver instead of ndiswrapper when you plug it in.  if you wish to go back to ndiswrapper, just change /etc/pcmcia/config.opts back to: bind "ndiswrapper".

---

### Post by Raistlin355 on 2006-08-10
Hmmm, I'll try it on the next update or when I have to reinstall.  The thing of it is, on my lappy I am using the acx driver with the ndiswrapper setup as the acx driver is the only thing that will turn the card on, but I have it loading the ndiswrapper drivers first. weird

---

### Post by dmizer on 2006-08-10
> **Raistlin355 said:**
> The thing of it is, on my lappy I am using the acx driver with the ndiswrapper setup as the acx driver is the only thing that will turn the card on, but I have it loading the ndiswrapper drivers first. weird
it's not possible to use ndiswrapper and acx at the same time.  the thing that's most likely fixing your card is these two commands:
sudo modprobe -r acx
sudo modprobe ndiswrapper

the sudo modprobe acx doesn't make a difference because the card is already loaded and active with the ndiswrapper module.  so even if the system has the acx module loaded, it's not doing anything to your card.  ndiswrapper and acx are two different modules and cannot work together.

if sudo modprobe acx does make a difference, it may be that you're already running the card on the acx driver instead of the ndiswrapper driver.  if you do an lsmod, you can see if the acx module is loading or if the ndiswrapper module is loading.

---

### Post by Kobalt on 2006-08-11
ACX being slower than Ndiswrapper ? I never heard of that... Just so you know, I have a router with a 28 Mb/s DSL connection from which I pick up my Wifi connection. With my WPC54G card I can download at an average speed of 600 Kb/s... 
Keep me posted if you get your card to work with my little trick ;)

---

### Post by Raistlin355 on 2006-08-11
> **dmizer said:**
> it's not possible to use ndiswrapper and acx at the same time.  the thing that's most likely fixing your card is these two commands:
sudo modprobe -r acx
sudo modprobe ndiswrapper

the sudo modprobe acx doesn't make a difference because the card is already loaded and active with the ndiswrapper module.  so even if the system has the acx module loaded, it's not doing anything to your card.  ndiswrapper and acx are two different modules and cannot work together.

if sudo modprobe acx does make a difference, it may be that you're already running the card on the acx driver instead of the ndiswrapper driver.  if you do an lsmod, you can see if the acx module is loading or if the ndiswrapper module is loading.

Yeah I understand that, but at the same time if I remove ndiswrapper from the system it doesn't work anymore.  The acx driver alone can't drive the card so there is something else that I'm missing.  
Like I said sudo modprobe -r acx & sudo modprobe ndiswrapper & sudo modprobe acx loads it up fine, but you have to modprobe acx at the end.  
Your right though its the acx driver that is finally loaded when the card is working not ndiswrapper like I thought.  

Out of curiosity if ndiswrapper was the driver driving the card what would it say in the terminal about the driver?

---

### Post by dmizer on 2006-08-11
> **Kobalt said:**
> ACX being slower than Ndiswrapper ? I never heard of that... Just so you know, I have a router with a 28 Mb/s DSL connection from which I pick up my Wifi connection. With my WPC54G card I can download at an average speed of 600 Kb/s... 
Keep me posted if you get your card to work with my little trick ;)
i just read it ... i can't prove or disprove it.

anyway ... i was successful in getting my card to work using your method.  thank you.  also, i was able to use network manager to activate the card.

---

### Post by dmizer on 2006-08-11
> **Raistlin355 said:**
> Like I said sudo modprobe -r acx & sudo modprobe ndiswrapper & sudo modprobe acx loads it up fine, but you have to modprobe acx at the end.

please post the output of dmesg after you've performed this.

---

### Post by Raistlin355 on 2006-08-11
ok

```
[4294667.296000] Linux version 2.6.15-23-386 (buildd@rothera) (gcc version 4.0.3  (Ubuntu 4.0.3-1ubuntu5)) #1 PREEMPT Tue May 23 13:49:40 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[4294667.296000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000e9c00 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 000000000fff0000 (usable)
[4294667.296000]  BIOS-e820: 000000000fff0000 - 000000000ffffc00 (ACPI data)
[4294667.296000]  BIOS-e820: 000000000ffffc00 - 0000000010000000 (ACPI NVS)
[4294667.296000]  BIOS-e820: 00000000fff80000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 255MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 65520
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:0
[4294667.296000]   DMA32 zone: 0 pages, LIFO batch:0
[4294667.296000]   Normal zone: 61424 pages, LIFO batch:15
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:0
[4294667.296000] DMI 2.3 present.
[4294667.296000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x00 0f6de0
[4294667.296000] ACPI: RSDT (v001 PTLTD    RSDT   0x06040000  LTP 0x00000000) @ 0x0fffbaa3
[4294667.296000] ACPI: FADT (v001 INTEL  440BX    0x06040000 PTL  0x000f4240) @ 0x0ffffb65
[4294667.296000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x0ffffbd9
[4294667.296000] ACPI: DSDT (v001 PTLTD      Ersa 0x06040000 MSFT 0x0100000b) @ 0x00000000
[4294667.296000] ACPI: PM-Timer IO Port: 0x1008
[4294667.296000] Allocating PCI resources starting at 20000000 (gap: 10000000:ef f80000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: root=/dev/hda1 ro quiet splash
[4294667.296000] Local APIC disabled by BIOS (or by default) -- you can enable i t with "lapic"
[4294667.296000] mapped APIC to ffffd000 (01201000)
[4294667.296000] Initializing CPU#0
[4294667.296000] PID hash table entries: 1024 (order: 10, 16384 bytes)
[4294667.296000] Detected 697.827 MHz processor.
[4294667.296000] Using pmtmr for high-res timesource
[4294667.296000] Console: colour VGA+ 80x25
[4294671.461000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[4294671.463000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[4294671.491000] Memory: 248884k/262080k available (1976k kernel code, 12576k re served, 606k data, 288k init, 0k highmem)
[4294671.491000] Checking if this processor honours the WP bit even in superviso r mode... Ok.
[4294671.552000] Calibrating delay using timer specific routine.. 1395.86 BogoMI PS (lpj=697931)
[4294671.552000] Security Framework v1.0.0 initialized
[4294671.552000] SELinux:  Disabled at boot.
[4294671.552000] Mount-cache hash table entries: 512
[4294671.552000] CPU: After generic identify, caps: 0387f9ff 00000000 00000000 0 0000000 00000000 00000000 00000000
[4294671.552000] CPU: After vendor identify, caps: 0387f9ff 00000000 00000000 00 000000 00000000 00000000 00000000
[4294671.552000] CPU: L1 I cache: 16K, L1 D cache: 16K
[4294671.552000] CPU: L2 cache: 256K
[4294671.552000] CPU serial number disabled.
[4294671.552000] CPU: After all inits, caps: 0383f9ff 00000000 00000000 00000040  00000000 00000000 00000000
[4294671.552000] mtrr: v2.0 (20020519)
[4294671.552000] CPU: Intel Pentium III (Coppermine) stepping 03
[4294671.552000] Enabling fast FPU save and restore... done.
[4294671.552000] Enabling unmasked SIMD FPU exception support... done.
[4294671.552000] Checking 'hlt' instruction... OK.
[4294671.556000] checking if image is initramfs... it is
[4294673.806000] Freeing initrd memory: 6836k freed
[4294673.845000] ACPI: Looking for DSDT ... not found!
[4294673.850000] ACPI: setting ELCR to 0200 (from 0020)
[4294674.097000] NET: Registered protocol family 16
[4294674.097000] EISA bus registered
[4294674.097000] ACPI: bus type pci registered
[4294674.098000] PCI: PCI BIOS revision 2.10 entry at 0xfd9ce, last bus=1
[4294674.098000] PCI: Using configuration type 1
[4294674.099000] ACPI: Subsystem revision 20051216
[4294674.103000] ACPI: Interpreter enabled
[4294674.103000] ACPI: Using PIC for interrupt routing
[4294674.105000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[4294674.105000] PCI: Probing PCI hardware (bus 00)
[4294674.106000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[4294674.113000] PCI quirk: region 1000-103f claimed by PIIX4 ACPI
[4294674.113000] PCI quirk: region 1040-104f claimed by PIIX4 SMB
[4294674.113000] Boot video device is 0000:01:00.0
[4294674.113000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[4294674.118000] ACPI: PCI Interrupt Link [LNKA] (IRQs 10) *0, disabled.
[4294674.118000] ACPI: PCI Interrupt Link [LNKB] (IRQs 10) *0, disabled.
[4294674.119000] ACPI: PCI Interrupt Link [LNKC] (IRQs *5)
[4294674.119000] ACPI: PCI Interrupt Link [LNKD] (IRQs 9) *0, disabled.
[4294674.123000] ACPI: Embedded Controller [EC0] (gpe 9) interrupt mode.
[4294674.125000] ACPI: Power Resource [PFAN] (off)
[4294674.125000] Linux Plug and Play Support v0.97 (c) Adam Belay
[4294674.125000] pnp: PnP ACPI init
[4294674.132000] pnp: PnP ACPI: found 11 devices
[4294674.132000] PnPBIOS: Disabled by ACPI PNP
[4294674.132000] PCI: Using ACPI for IRQ routing
[4294674.132000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps , post a report
[4294674.134000] pnp: 00:04: ioport range 0x1000-0x104f could not be reserved
[4294674.134000] pnp: 00:04: ioport range 0xfe00-0xfe01 has been reserved
[4294674.135000] PCI: Bridge: 0000:00:01.0
[4294674.135000]   IO window: 2000-2fff
[4294674.135000]   MEM window: fc100000-fdffffff
[4294674.135000]   PREFETCH window: 28000000-280fffff
[4294674.135000] PCI: Bus 2, cardbus bridge: 0000:00:0a.0
[4294674.135000]   IO window: 00001800-000018ff
[4294674.135000]   IO window: 00001c00-00001cff
[4294674.135000]   PREFETCH window: 20000000-21ffffff
[4294674.135000]   MEM window: 22000000-23ffffff
[4294674.135000] PCI: Bus 6, cardbus bridge: 0000:00:0a.1
[4294674.135000]   IO window: 00003000-000030ff
[4294674.135000]   IO window: 00003400-000034ff
[4294674.135000]   PREFETCH window: 24000000-25ffffff
[4294674.135000]   MEM window: 26000000-27ffffff
[4294674.135000] **** SET: Misaligned resource pointer: cea9e6e2 Type 07 Len 0
[4294674.136000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[4294674.136000] PCI: setting IRQ 10 as level-triggered
[4294674.136000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKA] -> GSI 10 (l evel, low) -> IRQ 10
[4294674.136000] PCI: Setting latency timer of device 0000:00:0a.0 to 64
[4294674.136000] ACPI: PCI Interrupt 0000:00:0a.1[A] -> Link [LNKA] -> GSI 10 (l evel, low) -> IRQ 10
[4294674.136000] PCI: Setting latency timer of device 0000:00:0a.1 to 64
[4294674.136000] Simple Boot Flag at 0x37 set to 0x1
[4294674.137000] audit: initializing netlink socket (disabled)
[4294674.137000] audit(1155350040.135:1): initialized
[4294674.137000] VFS: Disk quotas dquot_6.5.1
[4294674.137000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[4294674.137000] Initializing Cryptographic API
[4294674.137000] io scheduler noop registered
[4294674.137000] io scheduler anticipatory registered
[4294674.137000] io scheduler deadline registered
[4294674.137000] io scheduler cfq registered
[4294674.137000] Limiting direct PCI/PCI transfers.
[4294674.138000] isapnp: Scanning for PnP cards...
[4294674.495000] isapnp: No Plug & Play device found
[4294674.536000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:MOUS] at 0x60,0x64 ir q 1,12
[4294674.538000] serio: i8042 AUX port at 0x60,0x64 irq 12
[4294674.538000] serio: i8042 KBD port at 0x60,0x64 irq 1
[4294674.538000] Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ shari ng enabled
[4294674.538000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294674.545000] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[4294674.546000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 bl ocksize
[4294674.546000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[4294674.546000] ide: Assuming 33MHz system bus speed for PIO modes; override wi th idebus=xx
[4294674.546000] mice: PS/2 mouse device common for all mice
[4294674.547000] EISA: Probing bus 0 at eisa.0
[4294674.547000] Cannot allocate resource for EISA slot 1
[4294674.547000] Cannot allocate resource for EISA slot 2
[4294674.547000] Cannot allocate resource for EISA slot 3
[4294674.547000] EISA: Detected 0 cards.
[4294674.547000] NET: Registered protocol family 2
[4294674.556000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[4294674.556000] TCP established hash table entries: 16384 (order: 4, 65536 byte s)
[4294674.556000] TCP bind hash table entries: 16384 (order: 4, 65536 bytes)
[4294674.556000] TCP: Hash tables configured (established 16384 bind 16384)
[4294674.556000] TCP reno registered
[4294674.557000] TCP bic registered
[4294674.557000] NET: Registered protocol family 1
[4294674.557000] NET: Registered protocol family 8
[4294674.557000] NET: Registered protocol family 20
[4294674.557000] Using IPI Shortcut mode
[4294674.557000] ACPI wakeup devices:
[4294674.557000]  LID CRD0 CRD1 COM1 MDM0 PWRB
[4294674.557000] ACPI: (supports S0 S1 S3 S4 S5)
[4294674.557000] Freeing unused kernel memory: 288k freed
[4294674.579000] input: AT Translated Set 2 keyboard as /class/input/input0
[4294674.698000] vga16fb: initializing
[4294674.698000] vga16fb: mapped to 0xc00a0000
[4294674.814000] Console: switching to colour frame buffer device 80x25
[4294674.814000] fb0: VGA16 VGA frame buffer device
[4294675.920000] Capability LSM initialized
[4294676.000000] ACPI: Fan [FAN] (on)
[4294676.012000] ACPI: CPU0 (power states: C1[C1] C2[C2])
[4294676.012000] ACPI: Processor [CPU0] (supports 4 throttling states)
[4294676.040000] ACPI: Thermal Zone [THRM] (42 C)
[4294677.265000] PIIX4: IDE controller at PCI slot 0000:00:07.1
[4294677.265000] PIIX4: chipset revision 1
[4294677.265000] PIIX4: not 100% native mode: will probe irqs later
[4294677.265000]     ide0: BM-DMA at 0x1070-0x1077, BIOS settings: hda:DMA, hdb: pio
[4294677.265000]     ide1: BM-DMA at 0x1078-0x107f, BIOS settings: hdc:DMA, hdd: pio
[4294677.266000] Probing IDE interface ide0...
[4294677.530000] hda: HITACHI_DK23AA-12, ATA DISK drive
[4294678.142000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[4294678.551000] Probing IDE interface ide1...
[4294679.223000] hdc: MATSHITADVD-ROM SR-8174, ATAPI CD/DVD-ROM drive
[4294679.529000] ide1 at 0x170-0x177,0x376 on irq 15
[4294679.548000] hda: max request size: 128KiB
[4294679.570000] hda: 23579136 sectors (12072 MB) w/512KiB Cache, CHS=23392/16/6 3, UDMA(33)
[4294679.571000] hda: cache flushes not supported
[4294679.571000]  hda: hda1 hda2 < hda5 >
[4294679.605000] hdc: ATAPI 24X DVD-ROM drive, 512kB Cache, UDMA(33)
[4294679.605000] Uniform CD-ROM driver Revision: 3.20
[4294680.026000] usbcore: registered new driver usbfs
[4294680.026000] usbcore: registered new driver hub
[4294680.032000] USB Universal Host Controller Interface driver v2.3
[4294680.033000] PCI: Enabling device 0000:00:07.2 (0000 -> 0001)
[4294680.033000] **** SET: Misaligned resource pointer: cfa005e2 Type 07 Len 0
[4294680.033000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 9
[4294680.033000] PCI: setting IRQ 9 as level-triggered
[4294680.033000] ACPI: PCI Interrupt 0000:00:07.2[D] -> Link [LNKD] -> GSI 9 (le vel, low) -> IRQ 9
[4294680.033000] uhci_hcd 0000:00:07.2: UHCI Host Controller
[4294680.034000] uhci_hcd 0000:00:07.2: new USB bus registered, assigned bus num ber 1
[4294680.034000] uhci_hcd 0000:00:07.2: irq 9, io base 0x000010e0
[4294680.035000] hub 1-0:1.0: USB hub found
[4294680.035000] hub 1-0:1.0: 2 ports detected
[4294680.309000] Attempting manual resume
[4294680.342000] usb 1-2: new low speed USB device using uhci_hcd and address 2
[4294680.395000] EXT3-fs: mounted filesystem with ordered data mode.
[4294680.395000] kjournald starting.  Commit interval 5 seconds
[4294704.794000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[4294704.805000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[4294705.135000] ltmodem: module license 'Proprietary' taints kernel.
[4294705.139000] Loading Lucent Modem Controller driver version 8.26-alk-8
[4294705.141000] PCI: Enabling device 0000:00:06.0 (0000 -> 0003)
[4294705.141000] **** SET: Misaligned resource pointer: ceba9802 Type 07 Len 0
[4294705.142000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[4294705.142000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [LNKB] -> GSI 10 (l evel, low) -> IRQ 10
[4294705.142000] Detected Parameters Irq=255 BaseAddress=0x1400 ComAddress=0x10c 8
[4294705.142000] ttyLTM0 at I/O 0x1400 (irq = 255) is a Lucent/Agere Modem
[4294705.637000] piix4_smbus 0000:00:07.3: Found 0000:00:07.3 device
[4294705.722000] ACPI: PCI Interrupt 0000:00:0a.0[A] -> Link [LNKA] -> GSI 10 (l evel, low) -> IRQ 10
[4294705.722000] Yenta: CardBus bridge found at 0000:00:0a.0 [1509:4260]
[4294705.722000] Yenta O2: res at 0x94/0xD4: e8/00
[4294705.722000] Yenta O2: old bridge, disabling read prefetch/write burst
[4294705.845000] Yenta: ISA IRQ mask 0x08b8, PCI irq 10
[4294705.845000] Socket status: 30000007
[4294705.876000] ACPI: PCI Interrupt 0000:00:0a.1[A] -> Link [LNKA] -> GSI 10 (l evel, low) -> IRQ 10
[4294705.876000] Yenta: CardBus bridge found at 0000:00:0a.1 [1509:4260]
[4294705.995000] Linux agpgart interface v0.101 (c) Dave Jones
[4294705.998000] Yenta: ISA IRQ mask 0x08b8, PCI irq 10
[4294705.998000] Socket status: 30000821
[4294706.033000] agpgart: Detected an Intel 440BX Chipset.
[4294706.038000] agpgart: AGP aperture is 64M @ 0xf8000000
[4294706.558000] Synaptics Touchpad, model: 1, fw: 5.5, id: 0x9b58b1, caps: 0x80 4793/0x0
[4294706.558000] serio: Synaptics pass-through port at isa0060/serio1/input0
[4294706.597000] input: SynPS/2 Synaptics TouchPad as /class/input/input1
[4294706.666000] pccard: CardBus card inserted into slot 1
[4294706.715000] **** SET: Misaligned resource pointer: caf93a22 Type 07 Len 0
[4294706.715000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 5
[4294706.715000] PCI: setting IRQ 5 as level-triggered
[4294706.715000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [LNKC] -> GSI 5 (le vel, low) -> IRQ 5
[4294706.733000] gameport: ES1938 is pci0000:00:04.0/gameport0, io 0x10c0, speed  1065kHz
[4294706.943000] Real Time Clock Driver v1.12
[4294706.993000] input: PC Speaker as /class/input/input2
[4294707.031000] Floppy drive(s): fd0 is 1.44M
[4294707.045000] FDC 0 is a post-1991 82077
[4294707.200000] parport: PnPBIOS parport detected.
[4294707.200000] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE,EPP]
[4294707.514000] usbcore: registered new driver hiddev
[4294707.567000] input: PS/2+USB Mouse as /class/input/input3
[4294707.567000] input: USB HID v1.11 Mouse [PS/2+USB Mouse] on usb-0000:00:07.2 -2
[4294707.567000] usbcore: registered new driver usbhid
[4294707.567000] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
[4294707.846000] ts: Compaq touchscreen protocol output
[4294708.175000] acx: Loaded combined PCI/USB driver, firmware_ver=1.2.1.34
[4294708.175000] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[4294708.176000] PCI: Enabling device 0000:06:00.0 (0000 -> 0002)
[4294708.176000] ACPI: PCI Interrupt 0000:06:00.0[A] -> Link [LNKA] -> GSI 10 (l evel, low) -> IRQ 10
[4294708.176000] PCI: Setting latency timer of device 0000:06:00.0 to 64
[4294708.176000] acx: found ACX111-based wireless network card at 0000:06:00.0, irq:10, phymem1:0x26020000, phymem2:0x26000000, mem1:0xd09a0000, mem1_size:8192,  mem2:0xd0b00000, mem2_size:131072
[4294708.274000] cs: IO port probe 0x100-0x3af: clean.
[4294708.276000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[4294708.277000] cs: IO port probe 0x820-0x8ff: clean.
[4294708.278000] cs: IO port probe 0xc00-0xcf7: clean.
[4294708.279000] cs: IO port probe 0xa00-0xaff: clean.
[4294708.282000] cs: IO port probe 0x100-0x3af: clean.
[4294708.284000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[4294708.285000] cs: IO port probe 0x820-0x8ff: clean.
[4294708.286000] cs: IO port probe 0xc00-0xcf7: clean.
[4294708.287000] cs: IO port probe 0xa00-0xaff: clean.
[4294709.204000] acx: form factor 0x01 ((mini-)PCI / CardBus), radio type 0x16 ( Radia), EEPROM version 0x05, uploaded firmware 'Rev 1.2.1.34' (0x03010101)
[4294709.204000] acx v0.3.21: net device wlan0, driver compiled against wireless  extensions 19 and Linux 2.6.15-23-386
[4294709.205000] usbcore: registered new driver acx_usb
[4294711.105000] NET: Registered protocol family 17
[4294711.773000] lp0: using parport0 (interrupt-driven).
[4294711.912000] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[4294712.094000] Adding 514040k swap on /dev/hda5.  Priority:-1 extents:1 across :514040k
[4294712.257000] EXT3 FS on hda1, internal journal
[4294712.263000] IBM TrackPoint firmware: 0x0b, buttons: 2/3
[4294712.499000] input: TPPS/2 IBM TrackPoint as /class/input/input4
[4294712.953000] md: md driver 0.90.3 MAX_MD_DEVS=256, MD_SB_DISKS=27
[4294712.953000] md: bitmap version 4.39
[4294714.066000] device-mapper: 4.4.0-ioctl (2005-01-12) initialised: dm-devel@r edhat.com
[4294715.132000] cdrom: open failed.
[4294716.791000] NET: Registered protocol family 10
[4294716.791000] lo: Disabled Privacy Extensions
[4294716.791000] IPv6 over IPv4 tunneling driver
[4294717.274000] wlan0: duplicate address detected!
[4294723.939000] ACPI: AC Adapter [ACAD] (on-line)
[4294724.016000] ACPI: Battery Slot [BAT0] (battery present)
[4294724.176000] ACPI: Power Button (FF) [PWRF]
[4294724.176000] ACPI: Lid Switch [LID]
[4294724.177000] ACPI: Power Button (CM) [PWRB]
[4294724.448000] ibm_acpi: IBM ThinkPad ACPI Extras v0.12a
[4294724.448000] ibm_acpi: http://ibm-acpi.sf.net/
[4294724.506000] pcc_acpi: loading...
[4294736.703000] ppdev: user-space parallel port driver
[4294737.355000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[4294737.356000] apm: overridden by ACPI.
[4294740.027000] wlan0 (WE) : Driver using old /proc/net/wireless support, pleas e fix driver !
[4294744.430000] Bluetooth: Core ver 2.8
[4294744.430000] NET: Registered protocol family 31
[4294744.430000] Bluetooth: HCI device and connection manager initialized
[4294744.430000] Bluetooth: HCI socket layer initialized
[4294744.561000] Bluetooth: L2CAP ver 2.8
[4294744.561000] Bluetooth: L2CAP socket layer initialized
[4294744.674000] Bluetooth: RFCOMM socket layer initialized
[4294744.674000] Bluetooth: RFCOMM TTY layer initialized
[4294744.674000] Bluetooth: RFCOMM ver 1.7



```

---

### Post by dmizer on 2006-08-13
okay Raistlin355, sorry it took me so long. had to do some digging to find the right command.

try this.  post the output of the following:
```
sudo ethtool -i wlan0
```

---

### Post by Raistlin355 on 2006-08-13
k
```
Cannot get driver information: Operation not supported

```

---

### Post by CoreyE on 2006-09-03
Well at first i tried the post you linked to, from Kobalt, didnt work. So i decided to try yours. Well everything went ok, had a few problems, mainly from my stupidity when it comes to linux, as in this is my second day with it, but i got all the way to the last step, and hit my problem. When i try to scan i get nothing. I know all my network settings, im the one who set them up. Heres what i get when i enter that last command:

> root@ce-laptop:/home/corey# iwlist wlan0 scan&& iwconfig wlan0 channel 8 essid linksys mode Managed&& ifup wlan0
wlan0     No scan results
ifup: interface wlan0 already configured

any help would rock. ive got it working with a lan cable for now, but i cant use the lan cable for ever, the routers not in my room.

---

### Post by dmizer on 2006-09-03
i noticed your commands didn't have "sudo" in front of them.  are you running as root?  if so, this may be one of the reasons you're having problems with the other how to.

you can break your machine pretty quickly while running as root.  it may seem easier, but in the long run you'll be better off learning from the start how to run without root privileges.

try this:
```
ifdown wlan0&& iwlist wlan0 scan&& iwconfig wlan0 channel 8 essid linksys mode Managed&& ifup wlan0
```
i still think you'll have more luck with the other method.

---

### Post by Rayne on 2006-09-11
ok here is what i get from "sudo iwlist wlan0 scan"

wlan0 Scan complete:
Cell 01 - Address: 00:16:B6:A2:89:6D
ESSID:"linksys"
Protocol"IEEE 802.11b
Mode:Managed
Frequency:2.437 GHz (Channel 6)
Quality:0/100 Signal level:-59 dBm Noise level:-256 dBm
Encryption key:off
Bit Rates:1 Mbs; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
          9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
          48 Mb/s; 54 Mb/s
Extra:bcn_int=100
Extra:atim=0

i have power to it about reading this tutorial, but still can't get any link what so ever, any ideas?

---

### Post by dmizer on 2006-09-11
several updates ago, i stopped being able to make this method work, but since kobalts method (linked in red at the top of my post on the first page) worked so well for me, i haven't spent a lot of time trying to make this work again.

if there's still interest here, i'll see what i can do about trying to make it work again, but kobalt's is far more painless than my own.

what is the output after this:
```
sudo ifdown wlan0&& sudo iwlist wlan0 scan&& sudo iwconfig wlan0 channel 6 essid linksys mode Managed&& sudo ifup wlan0
```

---

### Post by Rayne on 2006-09-11
```
Network interface is managed from NetworkManager
NetworkManager cannot be advised to take down and interface.
Set up another interface insted.
```

---

### Post by Rayne on 2006-09-11
bump

---

### Post by dmizer on 2006-09-11
sorry for the delay.  you caught me just when i was headed to bed.

what desktop environment are you using?

and post the output of:
```
lspci | grep ACX
```

---

### Post by Rayne on 2006-09-11
> **dmizer said:**
> sorry for the delay.  you caught me just when i was headed to bed.

what desktop environment are you using?

and post the output of:
```
lspci | grep ACX
```


GNOME

output:
"02:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface"

---

### Post by dmizer on 2006-09-11
if you go to system > administration > network

do you see wlan0 listed?  if so, try configuring your network settings there.

if in administration, you have both network and network manager listed, that might be the cause of your problem.  i've never been able to configure network manager to play nice with gnome's default networking.

---

### Post by Rayne on 2006-09-11
are you talking about in the start menu? if so im not seeing it

---

### Post by dmizer on 2006-09-12
it should say "applications" rather than start.  but right next to applications is places, and next to places should be system.  if you don't see "system" there, then you've either removed it or it's been removed somehow.

---

### Post by Rayne on 2006-09-12
> **dmizer said:**
> it should say "applications" rather than start.  but right next to applications is places, and next to places should be system.  if you don't see "system" there, then you've either removed it or it's been removed somehow.


Next to "Places" is "Desktop" on mine

---

### Post by dmizer on 2006-09-12
it should have the three options shown on the top bar in the screen shot here: [http://www.ubuntu.com/include/img/desktop.png](http://www.ubuntu.com/include/img/desktop.png)

you changed it so there's no more top panel and you have applications and places down on the bottom bar?  if so, it would appear that you haven't included "system" which is also necessary.  you can regain it with a right click > add to panel and selecting the right option.

sorry, i don't use gnome, so i can't tell you which option is the correct option.

---

### Post by Rayne on 2006-09-12
i have not idea how to set it but i know under Applications there is a system menu

---

### Post by dmizer on 2006-09-16
okay ... i figured out today how to make this work without using network manager.  but i think you might still run into problems.

post the output of:
uname -r

and i will follow up with some commands.

---

### Post by tjcravey on 2009-05-28
This method worked for me on Ubuntu 9.04 (Jaunty Jackelope)
 
Thanks!!!

---

### Post by dmizer on 2009-05-28
> **tjcravey said:**
> This method worked for me on Ubuntu 9.04 (Jaunty Jackelope)
 
Thanks!!!

Unbelievable! :)

I just updated the howto a few days ago, but I don't have the card anymore so I had no way to test it. Wasn't sure if it would work or not. Thanks for letting me know!

In fact, you probably would have had an easier time of it if you had followed the more current tutorial located here: [http://ubuntuforums.org/showthread.php?t=324148](http://ubuntuforums.org/showthread.php?t=324148)

---

