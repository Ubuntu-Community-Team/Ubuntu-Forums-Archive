---
title: "Failed to load module &quot;nv&quot; (why is my comp SO SLOW?)"
date: 2012-01-01
forum: New to Ubuntu
---

### Post by maryalesia on 2012-01-01
I am running 11.10 with the GNOME 3 shell on a gateway FX laptop with a nvidia geforce 9800M GTS graphics card. 

My computer has gotten slower than it was when I was running an extremely fragmented Vista with iTunes open. IT IS RIDICULOUS. 

According to my network settings, my wireless connection is running around 100 Mb/s, and yet it took my computer about twenty minutes to download one measely mp3 file from amazon. In system monitor under the resources tab, my network history graph has my comp receiving 0-50 Kib/s. Sometimes it is just bytes, singular. 

My computer is the only one in the house doing this, so I know it isn't the WiFi crapping out on me. 

Switching to fallback GNOME classic didn't do anything. 

While fiddling around, I opened up X diagnostic settings, clicked "display error messages", and was met with this gem:

Failed to load module "nv" (module does not exist, 0) 

I was then given these "workaround" options, with the caveat that no matter how many times I checked the box next to them and pressed "apply", they were unchecked the next time I opened up the application:

Disable VESA framebuffer driver
Disable PAT memory

- is any of that connected to how freakishly slow my computer has gotten? 

I'M GOING NUTS

thankyou all in advance for any help you can give me

---

### Post by maryalesia on 2012-01-01
used the wrong prefix for this thread - should be ubuntu instead of lubuntu - but I don't know how to change that / can't figure it out because my computer is running so slowly that when I click on "thread tools" ... nothing ... happens. It seriously took over a minute just to load the reply to thread page.

---

### Post by wildmanne39 on 2012-01-01
Hi, no that is not why your computer is slow, please post the output of these commands and we will see if we can find the problem.
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
``` 
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by oldfred on 2012-01-01
+1 on wildmanne39 suggestions.

Edited title for you.

If slow with wi-fi use Ethernet to download nVidia and other updates before testing wi-fi.

---

### Post by maryalesia on 2012-01-01
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux mary-P-7805u 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:34:47 UTC 2011 i686 i686 i386 GNU/Linux
mary@mary-P-7805u:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller [11ab:436b] (rev 16)
	Subsystem: Gateway 2000 Device [107b:0696]
	Kernel driver in use: sky2
--
04:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
	Subsystem: Intel Corporation WiFi Link 5100 AGN [8086:1201]
	Kernel driver in use: iwlagn
mary@mary-P-7805u:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:"EQTF8"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:26:75:59:1C:4A   
          Bit Rate=150 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:18957  Invalid misc:1459   Missed beacon:0

mary@mary-P-7805u:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

---

### Post by maryalesia on 2012-01-01
hope that is helpful - I am losing my mind! 

had to keep myself busy somehow, though, so messed around with other distros on my back-up laptop. :D

---

### Post by wildmanne39 on 2012-01-01
Hi, please try this I think it will help a lot:
```
gksudo gedit /etc/modprobe.d/iwlagn.conf
```
Add a single line:
```
options iwlagn 11n_disable=1
```
Proofread carefully, save and close gedit. Reboot.
Thanks

---

### Post by maryalesia on 2012-01-01
when I typed in the first code you gave me, this happened in terminal (before a gedit window opened):
```
(gksudo:20865): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:20865): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:20865): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gksudo:20865): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
``` 

is this normal? should I still add the line you gave me with the gedit window that opened?

---

### Post by wildmanne39 on 2012-01-01
Hi, that is a separate issue and yes still add the line.
Thanks

---

### Post by maryalesia on 2012-01-02
When I typed in that line, saved and reboot, I no longer had wireless as an option in network settings. Deleted the line from the file and am rebooting now - typing this from my phone.

---

### Post by wildmanne39 on 2012-01-02
Hi, please go back to post 7, I changed the one line of code to enter, try it now and I think it will work.
Thanks

---

