---
title: "Internet problem"
date: 2011-10-10
forum: New to Ubuntu
---

### Post by MrTeal on 2011-10-10
Hi
I am fairly new to the whole Linux thing.  My internet is perfect.  It works on the other computers in my house.  When I try to connect to the family wifi I put in the password and the wifi thing at the top right does the blinking thing.  After about you a minute the password prompt will come up again.  I am using 11.04

---

### Post by hollowsyndicate on 2011-10-10
wat brand n model is it?

---

### Post by MrTeal on 2011-10-10
Hi super new to this.

I just installed everything very nice. (11.04)
I connected to my internet and everything was working fine.  I decided to restart my computer.  When it's back up no internet.  I can see my neighbors but not mine.  The other computers in my house are fine.  



Best regards

---

### Post by papibe on 2011-10-10
Is this the same problem as you had [here]("http://ubuntuforums.org/showthread.php?t=1857237")?

Were you able to connect to your Wifi?

Regards.

---

### Post by harry_r_s on 2011-10-10
Ubuntu automattically connects to the last known wifi access point after restart.
First of all Check these:

1. Make sure Your network is discoverable on other devices too.
2. Refresh your search.
3. The hardware settings are set to default.
:popcorn:

---

### Post by MrTeal on 2011-10-10
Everything is set to defualt and discoveable. The other problem of internet I asked also applies here.  I try to join the neighborr's wifi that has no security;  but I couldn't.

---

### Post by mörgæs on 2011-10-10
Threads merged. Please don't create multiple threads on the same subject.

---

### Post by MrTeal on 2011-10-10
Sorry about that.  It's just one problem after another.  I'm thinking of downgrading to 10.04


I am using
Modem: Motorola SB51O1U

Router:  Netgear N300 WNR2000

---

### Post by MrTeal on 2011-10-10
Bump

---

### Post by MrTeal on 2011-10-11
Bump

---

### Post by MrTeal on 2011-10-11
Edit: threads have merged

---

### Post by JSchultheis on 2011-10-11
> **MrTeal said:**
> I'm new to this.  I can't connect to the internet.  I do not see my wirless internet on the list and the connect to a hidden internet doesn't work.  When my internet does show up (Rarely at night) I press connect and the bars flash like its trying to connect. After a minute it gives me the prompt to put my password back in.

Hello friend.

So reading through the quote, it sounds like you actually do connect, but sometimes get knocked off the network.

Is that true?

*hidden network pertains to a setting on the router in which it does not broadcast its given name; have you programmed your router that way?

---

### Post by MrTeal on 2011-10-11
That could be a possibility.  Now that I think about it when it does show upin the list it always says I get disconnected.  But the problem is it doesn't show up in my wirless connections.  How do you tell if you router had been programmed like that?

---

### Post by mörgæs on 2011-10-11
Like I told you before: One problem - one thread.
Please don't make me write this a third time.

---

### Post by MrTeal on 2011-10-11
HOW do I check if it's programmed to be hidden?  I don't think it is because it shows up on Windows 7 and Xbox.

Once again 
I am using
Modem: Motorola SB51O1U

Router:  Netgear N300 WNR2000




To admin: Sorry about the threads I haven't been getting any answers and I need internet to do my homework.

---

### Post by JSchultheis on 2011-10-11
I am still trying to gather more info and also hoping a guru will jump in or that your other research will pay off, meanwhile, if it was hidden you would have gone out of your way to program it that way. It would not be visible to the xbox and window7 comp without going through a process. 

And even then, you could use whatever reset button it has to undo any effect like that.

As for checking, do you have the guide? At the Netgear site they are asking if what version of WNR2000. 

But seriously, this 'hidden network' discussion is spinning wheels, simply fruitless hypothetical talk.

Have you ever successfully logged into this router with this ubuntu system?

---

### Post by MrTeal on 2011-10-11
I'll get back to yyou on the model when I get home.  I have connected twice.  Once when I tried it on install and right after install.

---

### Post by wildmanne39 on 2011-10-11
Hi, I will try to help you but I am having some computer issues at the moment so you will have to be patient.

Please open a terminal by hitting ctrl+alt+t copy and paste these commands into it then paste the information here:
```
cat /etc/lsb-release; uname -a
```
```
sudo lshw -C network
```
```
lspci -nnk | grep -iA2 net
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by MrTeal on 2011-10-11
Alright It's going to take awhile to type it because I am doing this on my phone. >_>

---

### Post by wildmanne39 on 2011-10-11
Hi, do you have a flash drive that you can put the output on then post it here using another computer with internet access.
Thank you

---

### Post by MrTeal on 2011-10-11
I didn't understand the last line of the post. (the # thing).  But heres the info
 
```
 
[COLOR=black][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]ian@ian-HPE-500f:~$ cat /ect/lsb-release; uname -a[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]cat: /ect/lsb-release: No such file or directory[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]Linux ian-HPE-500f 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]ian@ian-HPE-500f:~$ sudo lshw -C network[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman][sudo] password for ian: [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]  *-network               [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]       description: Wireless interface[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]       product: RT3090 Wireless 802.11n 1T/1R PCIe[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]       vendor: Ralink corp.[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]       physical id: 0[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]       bus info: pci@0000:02:00.0[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]       logical name: wlan0[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]       version: 00[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]       serial: 68:a3:c4:01:89:56[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]       width: 32 bits[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]       clock: 33MHz[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.38-8-generic firmware=0.11 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]       resources: irq:17 memory:feaf0000-feafffff[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]  *-network[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]       description: Ethernet interface[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]       vendor: Realtek Semiconductor Co., Ltd.[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]       physical id: 0[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]       bus info: pci@0000:03:00.0[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]       logical name: eth0[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]       version: 05[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]       serial: 78:ac:c0:a4:e8:98[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]       size: 10Mbit/s[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]       capacity: 100Mbit/s[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]       width: 64 bits[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]       clock: 33MHz[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]       resources: irq:43 ioport:e800(size=256) memory:febff000-febfffff memory:fdffc000-fdffffff[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]ian@ian-HPE-500f:~$ lspci -nnk | grep -iA2 net[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]02:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090][/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]            Subsystem: Lite-On Communications Inc Device [11ad:6632][/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]            Kernel driver in use: rt2800pci[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]--[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]            Subsystem: Hewlett-Packard Company Device [103c:2ab1][/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]            Kernel driver in use: r8169[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]ian@ian-HPE-500f:~$ iwconfig[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]lo        no wireless extensions.[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]eth0      no wireless extensions.[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]wlan0     IEEE 802.11bgn  ESSID:"TennisNutty"  [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]          Tx-Power=20 dBm   [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]          Retry  long limit:7   RTS thr:off   Fragment thr:off[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]          Power Management:off[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]ian@ian-HPE-500f:~$ rfkill list all[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]0: phy0: Wireless LAN[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]            Soft blocked: no[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]            Hard blocked: no[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]ian@ian-HPE-500f:~$ lsmod[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]Module                  Size  Used by[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]cryptd                 20510  0 [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]aes_x86_64             17208  0 [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]aes_generic            38279  1 aes_x86_64[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]cdc_acm                22574  0 [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]nls_iso8859_1          12713  1 [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]nls_cp437              16991  1 [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]vfat                   21708  1 [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]fat                    61374  1 vfat[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]binfmt_misc            17565  1 [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]parport_pc             36959  0 [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]ppdev                  17113  0 [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]usblp                  18233  0 [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]snd_hda_codec_hdmi     28103  1 [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]snd_hda_codec_realtek   336693  1 [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]snd_hda_intel          33211  2 [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]snd_hwdep              13604  1 snd_hda_codec[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]snd_seq_midi           13324  0 [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]snd_rawmidi            30486  1 snd_seq_midi[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]snd_seq_midi_event     14899  1 snd_seq_midi[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]radeon                982197  3 [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]snd_timer              29602  2 snd_pcm,snd_seq[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]rt2860sta             543010  0 [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]ttm                    76664  1 radeon[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]arc4                   12529  2 [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]drm_kms_helper         42136  1 radeon[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]rt2800pci              18535  0 [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]psmouse                73535  0 [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]drm                   227495  5 radeon,ttm,drm_kms_helper[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]edac_core              53845  0 [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]lp                     17825  0 [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]soundcore              12680  1 snd[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]parport                46458  3 parport_pc,ppdev,lp[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]snd_page_alloc         18529  2 snd_hda_intel,snd_pcm[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]rt2800lib              45181  1 rt2800pci[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]crc_ccitt              12667  2 rt2860sta,rt2800lib[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]rt2x00pci              14322  1 rt2800pci[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]rt2x00lib              49235  3 rt2800pci,rt2800lib,rt2x00pci[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]serio_raw              13166  0 [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]mac80211              294370  3 rt2800lib,rt2x00pci,rt2x00lib[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]sp5100_tco             13744  0 [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]i2c_algo_bit           13400  1 radeon[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]edac_mce_amd           23464  0 [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]i2c_piix4              13303  0 [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]k10temp                13119  0 [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]cfg80211              178528  2 rt2x00lib,mac80211[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]eeprom_93cx6           12725  1 rt2800pci[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]usbhid                 46956  0 [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]hid                    91020  1 usbhid[/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]usb_storage            53538  1 [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]uas                    17996  0 [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]ahci                   25951  2 [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]r8169                  48022  0 [/FONT][/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3][/SIZE][/FONT][/COLOR]
[COLOR=black][SIZE=3][FONT=Times New Roman]libahci                26642  1 ahci[/FONT][/SIZE][/COLOR]
[COLOR=black][/COLOR]
[COLOR=black][/COLOR]
[COLOR=black][/COLOR]
[COLOR=black][/COLOR]
[COLOR=black][/COLOR]
[COLOR=black][/COLOR]
[COLOR=black][/COLOR]
[COLOR=black][/COLOR]
[COLOR=black][/COLOR]
[COLOR=black][/COLOR]
[COLOR=black][/COLOR]

```

---

### Post by wildmanne39 on 2011-10-11
Hi, let's try this before moving on to a new driver.
```
sudo su
echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
exit
```
```
sudo modprobe rt2860sta
```
Thank you

---

### Post by MrTeal on 2011-10-11
Is that all one code or three seperate codes? Because there is no such directory for the echo line.


It says bash: /ect/modprone.d/blacklist.con: No such file or directory

---

### Post by wildmanne39 on 2011-10-11
It is all one code, copy and paste the complete code into the terminal.
Thank you

---

### Post by MrTeal on 2011-10-11
First code doesn't work for me:/.  I'm pretty sure I typed it correctly.

---

### Post by wildmanne39 on 2011-10-11
Hi, please copy and paste the complete code into the terminal.

It will not show any output unless there is an error.
Thank you

---

### Post by MrTeal on 2011-10-11
All the codes work except for 
It says "No such file or Directory"
echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf

---

### Post by wildmanne39 on 2011-10-11
Hi, please post the output of:
```
cat /etc/modprobe.d/blacklist.conf
```
Thank you

---

### Post by MrTeal on 2011-10-11
root@ian-HPE-500f:/home/ian# cat /ect/modprobe.d/blacklist.conf
cat: /ect/modprobe.d/blacklist.conf: No such file or directory

---

### Post by alphacrucis2 on 2011-10-11
> **MrTeal said:**
> root@ian-HPE-500f:/home/ian# cat /ect/modprobe.d/blacklist.conf
cat: /ect/modprobe.d/blacklist.conf: No such file or directory

Should be **etc** rather than **ect**

---

### Post by wildmanne39 on 2011-10-11
Hi, the command is not correct please copy and paste the commands into the terminal, they have to be exact, spacing, capitalization, everything.
Thank you

---

### Post by MrTeal on 2011-10-11
Damn you English teacher.

ian@ian-HPE-500f:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

---

### Post by wildmanne39 on 2011-10-11
Hi, alright we have learned that the terminal is not forgiving when it comes to commands, so we are good now, do not worry about the small stuff.

Please copy and paste this complete command into the terminal: It is all one command.
```
sudo su
echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
exit
``` 
Then
```
sudo modprobe rt2860sta
```
Thank you

---

### Post by MrTeal on 2011-10-11
One thing after another

ian@ian-HPE-500f:~$ sudo su echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf exit
bash: /etc/modprobe.d/blacklist.conf: Permission denied




EDIT:   I'll change to admin
EDIT 2: I changed my profile to administrator but no luck

---

### Post by alphacrucis2 on 2011-10-11
> **MrTeal said:**
> One thing after another

ian@ian-HPE-500f:~$ sudo su echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf exit
bash: /etc/modprobe.d/blacklist.conf: Permission denied




EDIT:   I'll change to admin
EDIT 2: I changed my profile to administrator but no luck

Try three commands

```
sudo su
```

Should prompt for password and put you into an admin shell. Then

```
echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist.conf
```

Should make the required change to the blacklist.conf file. Then

```
exit
```

Exit from admin shell back to normal.

---

### Post by wildmanne39 on 2011-10-11
Hi, did you try it the way alphacrucis2 suggested?

When you type your password into the terminal it will not show anything as you type for security reasons.
Thank you

---

### Post by MrTeal on 2011-10-12
OK worked this time.   I also did sudo modprobe rt2860sta

---

### Post by alphacrucis2 on 2011-10-12
Hi MrTeal, If Wildmane's instructions have fixed your problem you should mark the thread as solved.

---

### Post by MrTeal on 2011-10-12
It didn't :/.  I can now see my wirless internet; but I can't connect to it.  It keeps giving me the prompt to put in my password.  There is no spelling errors.

---

### Post by gandaran on 2011-10-12
> **MrTeal said:**
> It didn't :/.  I can now see my wirless internet; but I can't connect to it.  It keeps giving me the prompt to put in my password.  There is no spelling errors.
what type of wireless security is set on the router and what channel?
try changing the security, if its wpa2 change to wpa or wep just to check if it works and if it's using a channel anything over 11 choose a lower one.

---

### Post by wildmanne39 on 2011-10-12
Hi, that is a good sign when you can see the connections.

Please post the results of:
```
nm-tool
```
```
iwconfig
```
```
sudo iwlist scan
```
```
sudo cat /var/log/syslog | grep -e rt2 -e firmware | tail -n35
```
```
dmesg | egrep 'rt2|firm|radio|switch|wlan0'
```
I know some of these commands we have run before but we need to do them again because now you can see the network and some of the information that did not show up before, should now.
Thank you

---

### Post by pierreyy on 2011-10-12
hello, 

 Are you sure you selected the proper router security information? ( wep, or wpa or wpa2 dont forget that within the security options you have different types of security such as hexedimal keys or 128 bit passphrases...) 

good luck

---

### Post by MrTeal on 2011-10-12
How do I check what channel?  Its WPA2 the passcode is 10 units long.  I'm pretty sure it's Linksys.

---

### Post by MrTeal on 2011-10-13
Wow sorry I didn't see your post for some reason.
 
 
 
 
 
 
[COLOR=black][FONT=Times New Roman]ian@ian-HPE-500f:~$ nm-tool[/FONT][/COLOR]
 
 
 
 
[COLOR=black][FONT=Times New Roman]NetworkManager Tool[/FONT][/COLOR]
 
 
 
 
[COLOR=black][FONT=Times New Roman]State: disconnected[/FONT][/COLOR]
 
 
 
 
[COLOR=black][FONT=Times New Roman]- Device: wlan0 ----------------------------------------------------------------[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Type: 802.11 WiFi[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Driver: rt2860[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]State: disconnected[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Default: no[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]HW Address: 00:00:00:00:00:00[/FONT][/COLOR]
 
 
 
 
[COLOR=black][FONT=Times New Roman]Capabilities:[/FONT][/COLOR]
 
 
 
 
[COLOR=black][FONT=Times New Roman]Wireless Properties[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]WEP Encryption: yes[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]WPA Encryption: yes[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]WPA2 Encryption: yes[/FONT][/COLOR]
 
 
 
 
[COLOR=black][FONT=Times New Roman]Wireless Access Points [/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Connors 2.4 GHz: Infra, 98:FC:11:64:E5:E2, Freq 2437 MHz, Rate 16 Mb/s, Strength 31 WPA WPA2[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]TennisNutty_EXT: Infra, A2:21:B7:9D:F3:AD, Freq 2462 MHz, Rate 18 Mb/s, Strength 31 WPA2[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]TennisNutty: Infra, 30:46:9A:9C:F5:CC, Freq 2462 MHz, Rate 16 Mb/s, Strength 89 WPA2[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]ShortSpruce-guest: Infra, 98:FC:11:64:E5:E4, Freq 2437 MHz, Rate 16 Mb/s, Strength 31[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Steve-System: Infra, 00:21:29:7D:F2:5E, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA[/FONT][/COLOR]
 
 
 
 
 
 
[COLOR=black][FONT=Times New Roman]- Device: eth0 -----------------------------------------------------------------[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Type: Wired[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Driver: r8169[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]State: unavailable[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Default: no[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]HW Address: 78:AC:C0:A4:E8:98[/FONT][/COLOR]
 
 
 
 
[COLOR=black][FONT=Times New Roman]Capabilities:[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Carrier Detect: yes[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Speed: 10 Mb/s[/FONT][/COLOR]
 
 
 
 
[COLOR=black][FONT=Times New Roman]Wired Properties[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Carrier: off[/FONT][/COLOR]
 
 
 
 
 
 
 
 
 
 
 
 
 
 
[COLOR=black][FONT=Times New Roman]ian@ian-HPE-500f:~$ iwconfig[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]lo no wireless extensions.[/FONT][/COLOR]
 
 
 
 
[COLOR=black][FONT=Times New Roman]eth0 no wireless extensions.[/FONT][/COLOR]
 
 
 
 
[COLOR=black][FONT=Times New Roman]wlan0 Ralink STA ESSID:"" Nickname:"RT2860STA"[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Mode:Auto Frequency=2.462 GHz Access Point: A2:21:B7:9D:F3:AD [/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Bit Rate=1 Mb/s [/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]RTS thr:off Fragment thr:off[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Link Quality=68/100 Signal level:0 dBm Noise level:-115 dBm[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Tx excessive retries:0 Invalid misc:0 Missed beacon:0[/FONT][/COLOR]
 
 
 
 
 
 
 
 
 
 
 
 
[COLOR=black][FONT=Times New Roman]ian@ian-HPE-500f:~$ sudo iwlist scan[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][sudo] password for ian: [/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]lo Interface doesn't support scanning.[/FONT][/COLOR]
 
 
 
 
[COLOR=black][FONT=Times New Roman]eth0 Interface doesn't support scanning.[/FONT][/COLOR]
 
 
 
 
[COLOR=black][FONT=Times New Roman]wlan0 Scan completed :[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Cell 01 - Address: 00:21:29:7D:F2:5E[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Protocol:802.11b/g[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]ESSID:"Steve-System"[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Mode:Managed[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Channel:6[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Quality:52/100 Signal level:-69 dBm Noise level:-115 dBm[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Encryption key:on[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Bit Rates:54 Mb/s[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]IE: WPA Version 1[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Group Cipher : TKIP[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Pairwise Ciphers (1) : TKIP[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Authentication Suites (1) : PSK[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Cell 02 - Address: 30:46:9A:9C:F5:CC[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Protocol:802.11b/g/n[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]ESSID:"TennisNutty"[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Mode:Managed[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Channel:11[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Quality:78/100 Signal level:-59 dBm Noise level:-115 dBm[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Encryption key:on[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Bit Rates:144 Mb/s[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]IE: IEEE 802.11i/WPA2 Version 1[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Group Cipher : CCMP[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Pairwise Ciphers (1) : CCMP[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman]Authentication Suites (1) : PSK[/FONT][/COLOR]
 
 
 
 
 
 
 
 
 
 
[COLOR=black][FONT=Times New Roman][COLOR=black][SIZE=3] [/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman]ian@ian-HPE-500f:~$ sudo cat /var/log/syslog | grep -e rt2 -e firmware |tail -n35[/FONT][/COLOR][SIZE=3] [/SIZE]
[COLOR=black][SIZE=3] [/SIZE][/COLOR]
[COLOR=black][SIZE=3] [/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman][sudo] password for ian: [/FONT][/COLOR]
[COLOR=black][SIZE=3] [/SIZE][/COLOR]
[COLOR=black][SIZE=3] [/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman]Oct 12 17:26:12 ian-HPE-500f kernel: [70475.406409] rt28xx_close call RT28xxPciAsicRadioOff fail![/FONT][/COLOR][SIZE=3] [/SIZE]
[COLOR=black][SIZE=3] [/SIZE][/COLOR]
[COLOR=black][SIZE=3] [/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman]Oct 12 17:26:12 ian-HPE-500f kernel: [70475.434844] <==== rt28xx_init, Status=0[/FONT][/COLOR][SIZE=3] [/SIZE]
[COLOR=black][SIZE=3] [/SIZE][/COLOR]
[COLOR=black][SIZE=3] [/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman]Oct 12 17:26:42 ian-HPE-500f kernel: [70505.326906] <==== rt28xx_init, Status=0[/FONT][/COLOR][SIZE=3] [/SIZE]
[COLOR=black][SIZE=3] [/SIZE][/COLOR]
[COLOR=black][SIZE=3] [/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman]Oct 12 17:28:05 ian-HPE-500f kernel: [70589.125677] rt28xx_close call RT28xxPciAsicRadioOff fail![/FONT][/COLOR][SIZE=3] [/SIZE]
[COLOR=black][SIZE=3] [/SIZE][/COLOR]
[COLOR=black][SIZE=3] [/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman]Oct 12 17:28:05 ian-HPE-500f kernel: [70589.153775] <==== rt28xx_init, Status=0[/FONT][/COLOR][SIZE=3] [/SIZE]
[COLOR=black][SIZE=3] [/SIZE][/COLOR]
[COLOR=black][SIZE=3] [/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman]Oct 12 20:59:04 ian-HPE-500f kernel: [83247.356866] <==== rt28xx_init, Status=0[/FONT][/COLOR][SIZE=3] [/SIZE]
[COLOR=black][SIZE=3] [/SIZE][/COLOR]
[COLOR=black][SIZE=3] [/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman]Oct 12 22:18:48 ian-HPE-500f kernel: [88031.323502] <==== rt28xx_init, Status=0[/FONT][/COLOR][SIZE=3] [/SIZE]
[COLOR=black][SIZE=3] [/SIZE][/COLOR]
[COLOR=black][SIZE=3] [/SIZE][/COLOR]
[COLOR=black][FONT=Times New Roman]Oct 12 22:20:18 ian-HPE-500f kernel: [88121.296503] <==== rt28xx_init, Status=0[/FONT][/COLOR][SIZE=3] [/SIZE]
[COLOR=black][SIZE=3] [/SIZE][/COLOR]
[/FONT][/COLOR] 
 
 
 
 
 
 
 
 
 
 
 
[COLOR=black][FONT=Times New Roman]ian@ian-HPE-500f:~$ dmesg |egrep 'rt2|firm|radio|switch|wlan0'[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 21.328927] rt2860sta: module is from the staging directory, the quality is unknown, you have been warned.[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 21.340264] rt2860 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 21.340297] rt2860 0000:02:00.0: setting latency timer to 64[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 21.661623] Console: switching to colour frame buffer device 240x67[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 22.281363] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 22.361320] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 32.490041] wlan0: no IPv6 routers present[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 114.305554] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 120.455560] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 131.020857] wlan0: no IPv6 routers present[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 197.304457] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 207.520066] wlan0: no IPv6 routers present[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 292.255880] rt28xx_close call RT28xxPciAsicRadioOff fail![/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 292.282007] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 302.340045] wlan0: no IPv6 routers present[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 424.044371] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 444.796226] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 452.441325] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 455.454196] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 458.465738] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 461.477394] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 467.185893] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 477.990065] wlan0: no IPv6 routers present[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 584.295932] rt28xx_close call RT28xxPciAsicRadioOff fail![/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 584.325848] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 595.190065] wlan0: no IPv6 routers present[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 2683.605866] rt28xx_close call RT28xxPciAsicRadioOff fail![/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 2683.634044] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 2693.950046] wlan0: no IPv6 routers present[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 3207.361333] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 3218.000064] wlan0: no IPv6 routers present[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 3285.772028] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 3295.990046] wlan0: no IPv6 routers present[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 3313.230085] wlan0: no IPv6 routers present[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 3323.239983] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 3333.380057] wlan0: no IPv6 routers present[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 3343.414845] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 3353.440064] wlan0: no IPv6 routers present[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 3446.235907] rt28xx_close call RT28xxPciAsicRadioOff fail![/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 3446.266858] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 3455.415900] rt28xx_close call RT28xxPciAsicRadioOff fail![/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 3455.444866] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 3474.350070] wlan0: no IPv6 routers present[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 3484.242689] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 3494.560031] wlan0: no IPv6 routers present[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 3541.247772] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 3551.880069] wlan0: no IPv6 routers present[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 3594.825851] rt28xx_close call RT28xxPciAsicRadioOff fail![/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 3594.852171] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 3614.470072] wlan0: no IPv6 routers present[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 3624.235935] rt28xx_close call RT28xxPciAsicRadioOff fail![/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 3624.264756] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 3634.330057] wlan0: no IPv6 routers present[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 3734.235925] rt28xx_close call RT28xxPciAsicRadioOff fail![/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 3734.266893] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 3740.605936] rt28xx_close call RT28xxPciAsicRadioOff fail![/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 3740.634963] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 3750.740067] wlan0: no IPv6 routers present[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 3921.920060] wlan0: no IPv6 routers present[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 3931.327923] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 3941.800058] wlan0: no IPv6 routers present[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 3978.335854] rt28xx_close call RT28xxPciAsicRadioOff fail![/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 3978.364463] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 3989.070067] wlan0: no IPv6 routers present[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 4905.745439] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 4908.535519] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 4911.715833] rt28xx_close call RT28xxPciAsicRadioOff fail![/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 4911.742056] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 4921.780052] wlan0: no IPv6 routers present[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 4953.880060] wlan0: no IPv6 routers present[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 4963.334482] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 4973.570046] wlan0: no IPv6 routers present[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 5556.914982] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 5567.240070] wlan0: no IPv6 routers present[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 5668.035767] rt28xx_close call RT28xxPciAsicRadioOff fail![/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 5668.064953] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][ 5679.080053] wlan0: no IPv6 routers present[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][33590.138859] rt28xx_close call RT28xxPciAsicRadioOff fail![/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][33590.167899] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][33595.335844] rt28xx_close call RT28xxPciAsicRadioOff fail![/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][33595.364748] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][33614.850036] wlan0: no IPv6 routers present[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][33625.337946] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][33635.370051] wlan0: no IPv6 routers present[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][70475.406409] rt28xx_close call RT28xxPciAsicRadioOff fail![/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][70475.434844] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][70495.950065] wlan0: no IPv6 routers present[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][70505.326906] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][70515.620040] wlan0: no IPv6 routers present[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][70589.125677] rt28xx_close call RT28xxPciAsicRadioOff fail![/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][70589.153775] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][70600.130027] wlan0: no IPv6 routers present[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][83238.130083] wlan0: no IPv6 routers present[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][83247.356866] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][83258.020047] wlan0: no IPv6 routers present[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][88021.230080] wlan0: no IPv6 routers present[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][88031.323502] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][88042.130080] wlan0: no IPv6 routers present[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][88121.296503] <==== rt28xx_init, Status=0[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Times New Roman][88131.730047] wlan0: no IPv6 routers present[/FONT][/COLOR]

---

### Post by wildmanne39 on 2011-10-13
Hi, please post the results of:
```
lsmod | grep rt2
```

What is the name of the network you are trying to connect too?
Thank you

---

### Post by MrTeal on 2011-10-13
TennisNutty.  I will when I get home.  I'm at the doctor's office

---

### Post by MrTeal on 2011-10-14
[COLOR=black][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman]ian@ian-HPE-500f:~$ lsmod | grep rt2[/FONT][/COLOR][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][COLOR=black][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman]rt2860sta             543010  0 [/FONT][/COLOR][COLOR=black][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Times New Roman]crc_ccitt              12667  1 rt2860sta[/FONT][/COLOR][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][COLOR=black][FONT=Times New Roman][SIZE=3] [/SIZE][/FONT][/COLOR]

---

### Post by wildmanne39 on 2011-10-14
Hi, your router is set to wpa2 which is what I usually recommend, but there are many bug reports with the drivers for your wireless card, one says you can use wep in 11.04 but not wpa2.

We can try that before installing a new driver for your card.

Open your web browser type 192.168.0.1 into the address bar, hopefully that will access your router then go into wireless security and change it to wep then save your settings and close your browser.

You will need to be hard wired to the router for this to work, but you do not have to be able to connect to the internet.

In the top right corner of the screen click on internet icon edit connection and in the wireless change it to wep and inter your new wep key given to you while you were in the router.
Thank you

---

### Post by MrTeal on 2011-10-14
So your saying I need to use an ethernet cable to connect to my router?  So let me clarify
1 Enter the ip in the web
2 change it to wep
3 Plug my computer in to the wired ethernet
4 Change the internet to wep in the wirless option (Kinda confused about this part)

---

### Post by wildmanne39 on 2011-10-14
Hi,
> First you will need to be hard wired to the router for this to work, but you do not have to be able to connect to the internet.

Then
> Open your web browser type 192.168.0.1 into the address bar, hopefully that will access your router then go into wireless security and change it to wep then save your settings and close your browser.

Then
> In the top right corner of the screen click on internet icon, click on edit connection and in the wireless change it to wep and inter your new wep key given to you while you were in the router.

It is likely this will not work but we should try before trying to install a new driver that also has some issues.
Thank you

---

### Post by MrTeal on 2011-10-14
^ What do you recommend?

---

### Post by wildmanne39 on 2011-10-14
Hi, have you tried what I mentioned in post 48?

Also for your wireless to work you have to disconnect any other internet first like wired or a usb connection.
Thank you

---

