---
title: "wireless connection problems"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by haydemon on 2008-07-23
I cannot connect to the wireless network at home with my laptop. I just installed Ubuntu 8.04 (the Hardy Heron version). I´ve tried 2 different wireless cards: Netgear MA401 and Linksys WPC11 ver.3. When I run iwconfig, I get the following output:

lo no wireless extensions

eth0 no wireless extensions

eth2 IEEE 802.11b ESSid:"" Nickname:¨Prism I¨
Mode:Managed Frequency:2.447 GHz Access Point: 00:1C:F0:60:8D23

Bit Rate:11 Mb/s
Retry short limit:8 RTS thr:off Fragment thr:off
Power Management:off
Link Quality=54/92 Signal level=-37 dBm Noise level=-140 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc;0 Missed beacon:0

When I runn ifconfig, this is the output:

eth0 Link encap:Ethernet HWaddr 00:02:3f:77:99:e3
UP BROADCAST MULTICAST MTU:1500 Metric:1
Rx packets:0 errors:0 dropped:0 overruns:0 frame:0
Tx packate:0 errors:0 dropped:0 Overruns:0 carrier:0
Collisions:0(0.0 B) TX bytes:0 (0.b.B)
Interrupt:10 Base address:0x3000

lo Link encap:Local Loopback
Int addr:127.0.20,1 Mask 255.0.0.0
inet6 addr: ::1/128 scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
Rx packets::2406 errors:0 dropped:0 overruns:0 frame:0
TX packats:2406 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:164572 (160.7 KB) TX bytes:164572 (160.7 KB)

All this with the Linksys card. Thanks for your help! BTW, I cannot download anything without being connected to Internet, so I¨m between a rockc & a hard place. Thans in advance.

---

### Post by ApOgEEs on 2008-07-24
If you wanna make your Netgear MA401 working, Check out this thread [http://ubuntuforums.org/showthread.php?t=809589](http://ubuntuforums.org/showthread.php?t=809589)

---

### Post by haydemon on 2008-07-25
Either card (Netgear MA401 or Linksys WPC11.ver3) are detected, in fact they work quite well with an unencrypted network. I cannot get either one to work with WPA, however,

---

### Post by caljohnsmith on 2008-07-25
> **haydemon said:**
> Either card (Netgear MA401 or Linksys WPC11.ver3) are detected, in fact they work quite well with an unencrypted network. I cannot get either one to work with WPA, however,
So what kind of WPA encryption are you using, e.g. WPA personal/PSK, WPA2, etc.? Are you setting up your connection thru the System > Admin > Network program? Do you have your router set up to use some sort of authentication, like shared key? (Usually under the advanced wireless settings on your router). It would help if you provide as many details as possible. :)

---

### Post by haydemon on 2008-07-25
I'm using WPA Personal. It requires encryption, I have the key. Going through the System > Administration > Network manager, AS WELL AS at the command line, following different paths suggested by different users. I'm running the latest version of Ubuntu (8.04 hardy heron) in a Toshiba Satellite (very old) 1105 model (I think--it's at home, I'm at work right now). It works with a non-encrypted connection, but not with this one. I've downloaded the driver (wpa_supplicant), but when I type sudo wpa_suplicant -Dwext ieth2 -c /etc/wpa_supplicant.conf I get an error message (which I can't replicate right now, becz like I said, my laptop is at home, and I don't remember it). Thx.

---

### Post by germanix on 2008-07-25
hi haydemon.Had the same problem now my wlan is running. I found the answer in the Linux Mint Wiki.(worked on my Ubuntu too)
[http://www.linuxmint.com/wiki/index.php/MintWifi](http://www.linuxmint.com/wiki/index.php/MintWifi)...
Here is what you do:
sudo gedit /etc/network/interfaces
then edit the interfaces file. Leave the loopback interfaces lo (the first two line)
They should now look like this:
auto lo
iface to inet loopback
save and close the file
In a terminal type:
sudo /etc/init.d/networking restart
Right click on the Network manager icon. It should show "networking enabled"
Left click on the icon.
It now shows the varios wireless routers detected in your area
click on the router you wish to connect to, enter your password or key and low and behold you are connected.
If this does not work it tells you there what to do next, but this was all I needed.
hope it works for you too.

---

### Post by germanix on 2008-07-25
hi haydemon.Had the same problem now my wlan is running. I found the answer in the Linux Mint Wiki.(worked on my Ubuntu too)
[http://www.linuxmint.com/wiki/index.php/MintWifi](http://www.linuxmint.com/wiki/index.php/MintWifi)
Here is what you do:
sudo gedit /etc/network/interfaces
then edit the interfaces file. Leave the loopback interfaces lo (the first two line)
They should now look like this:
auto lo
iface to inet loopback
save and close the file
In a terminal type:
sudo /etc/init.d/networking restart
Right click on the Network manager icon. It should show "networking enabled"
Left click on the icon.
It now shows the varios wireless routers detected in your area
click on the router you wish to connect to, enter your password or key and low and behold you are connected.
If this does not work it tells you there what to do next, but this was all I needed.
hope it works for you too.

---

### Post by haydemon on 2008-07-25
Here is a question for y'all out there: in reading a post in another forum, I came across the following instruction: Create a file called /etc/default/wpasupplicant, add entry ENABLED=0.

How do I do that? In other wds, how does one "create a file" at the command line? If not for this specific instruction, I think I might have the answer to my problem. (BTW, the post is in [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html). From all comments, this is the panacea for all people out there who have had problems with this issue. We'll see...)

---

### Post by germanix on 2008-07-25
When I posted the above I was informed that the post did not go through and asked to post again, now I see it posted double, sorry about that.

---

### Post by jimv on 2008-07-25
I never got NetworkManager to work with WPA, but I was able to get connected using WICD.

Make sure that you have WPA Supplicant installed.  

sudo apt-get install wpasupplicant

---

### Post by haydemon on 2008-07-25
Yes, it is installed. Thx. Still no worky. :(

---

### Post by haydemon on 2008-07-25
I saw that. No worries. Thanks for the sugggestion. I'll try it at home tonite. I'll post results. (Fingers crossed!) ;)

---

### Post by germanix on 2008-07-25
[http://www.linuxmint.com/wiki/index.php/MintWifi](http://www.linuxmint.com/wiki/index.php/MintWifi)

This is the link that will hopefully solve all of your problems.

---

### Post by haydemon on 2008-07-25
Again, how does one "create a file" at the command line?:confused:

---

### Post by caljohnsmith on 2008-07-25
> **haydemon said:**
> Here is a question for y'all out there: in reading a post in another forum, I came across the following instruction: Create a file called /etc/default/wpasupplicant, add entry ENABLED=0.

How do I do that? In other wds, how does one "create a file" at the command line? If not for this specific instruction, I think I might have the answer to my problem. (BTW, the post is in [http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html](http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html). From all comments, this is the panacea for all people out there who have had problems with this issue. We'll see...)
I do not know if that will solve your problem, but whether it does or not, here is how you would create a file with "ENABLED=0" in it at the command line as root user (since that file you want to create should be owned by root and it also is in a directory that requires root privileges):
```
sudo bash -c 'echo ENABLED=0 > /etc/default/wpasupplicant'
```
Be sure no /etc/default/wpasupplicant file all ready exists, or you will overwrite it with the above command.

---

### Post by haydemon on 2008-07-25
Be sure no /etc/default/wpasupplicant file all ready exists, or you will overwrite it with the above command.[/quote]

How do I check if it already exists?:confused:

---

### Post by caljohnsmith on 2008-07-25
> **haydemon said:**
> Be sure no /etc/default/wpasupplicant file all ready exists, or you will overwrite it with the above command.
How do I check if it already exists?:confused:
You could just:
```
ls /etc/default/wpasupplicant
```
And if it returns "ls: cannot access /etc/default/wpasupplicant: No such file or directory" then you know it doesn't exist. :)

---

### Post by haydemon on 2008-07-25
> **caljohnsmith said:**
> You could just:
```
ls /etc/default/wpasupplicant
```And if it returns "ls: cannot access /etc/default/wpasupplicant: No such file or directory" then you know it doesn't exist. :)
Thanks!

---

### Post by haydemon on 2008-07-26
Well, here is the latest on the wireless networkng problem: nothng has worked. I¨ve followed several different threads, sets of instruction, set and reset my settings, etc., etc., andit still doesn´t work. It recognizes the wireless card,I see the network Mgr icon, I see the connecton, BUT, I cannot get it show a WPA connection; only WEP connections. I must be able to set a WPA connection,and insert an encryption key,as determined  by the router we are using. I´m at a loss!:confused:

---

### Post by caljohnsmith on 2008-07-26
> **haydemon said:**
> Well, here is the latest on the wireless networkng problem: nothng has worked. I¨ve followed several different threads, sets of instruction, set and reset my settings, etc., etc., andit still doesn´t work. It recognizes the wireless card,I see the network Mgr icon, I see the connecton, BUT, I cannot get it show a WPA connection; only WEP connections. I must be able to set a WPA connection,and insert an encryption key,as determined  by the router we are using. I´m at a loss!:confused:
OK, if you open System > Admin > Network, hit the unlock button and type in your password, click on the "Wireless Connection" to highlight it (and make sure the check box is checked), hit properties, under "password type" you should be able to choose WPA and then enter your password below that. Have you tried that? Or where are you seeing that it limits you only to WEP? Please give more details.

---

### Post by haydemon on 2008-07-28
Still nothing works. wpasupplicant already installed. Done a long time ago (relatively speaking). I refuse to give up! I'm still open for suggestions. Thanks all.[-o<

---

### Post by caljohnsmith on 2008-07-28
I agree with a previous poster, I would give WICD a try in your case; it is a network manager that many people find works better than the Gnome network manager. Just download the .deb 1.4.2 version file from:

[http://sourceforge.net/project/showfiles.php?group_id=194573](http://sourceforge.net/project/showfiles.php?group_id=194573)

If you download it into your Public directory in your home folder, here is how you would install it from the command line:
```
cd ~/Public
sudo dpkg -i wicd_1.4.2-1-all.deb
```

---

### Post by haydemon on 2008-08-01
> **caljohnsmith said:**
> OK, if you open System > Admin > Network, hit the unlock button and type in your password, click on the "Wireless Connection" to highlight it (and make sure the check box is checked), hit properties, under "password type" you should be able to choose WPA and then enter your password below that. Have you tried that? Or where are you seeing that it limits you only to WEP? Please give more details.
The latter. It only limits to WEP connections. No WPA choices at all.

---

### Post by trekguy on 2008-08-01
FWIW, I just started with Ubuntu when Hardy Heron came out.  I had been trying to get wireless to work on my Toshiba laptop (Netgear) for quite a while.  Finally gave up and bought an Edimax USB ... it works out of the box with HH.

---

