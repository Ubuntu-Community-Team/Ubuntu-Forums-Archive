---
title: "Problem with connecting to internet on Ubuntu 12.1 34 bit on toshiba c855-s5239"
date: 2013-01-03
forum: New to Ubuntu
---

### Post by vadertater on 2013-01-03
I installed Ubuntu 12.1 from a 34-bit disk on my Toshiba C855-S5239 (I probably should have gotten the 64 bit and I plan to do that soon). It's dual-boot, so I still have Windows 7. 

The problem is I cannot connect to the internet. The computer can see the different networks around, but it does not connect to them.

I researched the issue a while ago and found a lot of information on this particular issue, but I could not find it again when I tried this morning.

I think it has to do with drivers.

I know very little about how to use linux and ubuntu. Any help would be greatly appreciated. I think there is a lot of info out there about this issue, but I do not know how to find it or where to find it. A push in the right direction would mean a lot!

---

### Post by tlhIngan on 2013-01-03
You mean Ubuntu 12.10 and it's a 32-bit disk, right?
I assume you mean Ubuntu lists some wireless networks under Preferences > Network Connections > Wireless
Try clicking your connection in the list and then "Edit...".
You often need to specify passwords and encryption type for these to work, make sure you know them.

---

### Post by RottNKorpse on 2013-01-03
Is this a fresh install (as a dual boot) or have you had this for a while and the WiFi thing just started happening?

32bit is oddly still the recommended version right now...not sure why. If you do decided to get a new comp with 64bit, then check out [www.System76.com](www.System76.com) (Ubuntu/Linux laptop/desktop vendor)

---

### Post by vadertater on 2013-01-06
tlhIngan: You are exactly right. 32 bit Ubuntu 12.10. And yes, it lists the wireless preferences. I already tried the password and the password I used was correct, yet the computer never actually connected to the network... it just stopped attempting to connect.

RottNKorpse: No, this install was about a month or two ago. The WiFi situation stareted immediately. 
      At school, I never had to ability to even recognize there was a wireless network. And at home, I have the ability to see it, but I cannot connect to it. And thanks for the link, I'll check it out.




The  issue still stands as previously stated. I'm reading a book called "Getting started with Ubuntu Linux" and it mentions that some hardware is not fully compatible with Ubuntu, so I'm trying to figure that out now.

---

### Post by squakie on 2013-01-06
Post back the output of :

lspci | grep Network

iwconfig

ifconfig

These will help us know:

- what chipset your wireless is using to help us know what driver you should be using

- various pieces of configuration information, including what driver is currently in use


With that information, we can get an idea where things stand right now and go from there.

BTW - if you have ever entered in the wrong password for a network you are connecting to (remember it is case sensitive), you would be better off going to network manager, choosing edit connections, and delete the entry there for the network you want to connect to.  Then go back and go to network manager again, click on the network you want to connect to, and it should ask for the password/passkey/passphrase - click the box under the password box so you can see what you enter in the password., then try to connect.  Watch the connection to see what point it gets to:  authorizing, obtaining IP address, etc., and post that back as well.

---

### Post by vadertater on 2013-01-07
squakie, I just copied and pasted the whole thing so here you go.
 
[FONT=Courier New][SIZE=2]nathan@nathan-Satellite-C855:~$ lspci | grep Network[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]02:00.0 [COLOR=darkorange]Network[/COLOR] controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev ff)[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]nathan@nathan-Satellite-C855:~$ iwconfig[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]wlan0 IEEE 802.11bgn ESSID:off/any [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Mode:Managed Access Point: Not-Associated Tx-Power=20 dBm [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Retry long limit:7 RTS thr=2347 B Fragment thr:off[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]Power Management:off[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]lo no wireless extensions.[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]nathan@nathan-Satellite-C855:~$ ifconfig[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]lo Link encap:Local Loopback [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]inet addr:127.0.0.1 Mask:255.0.0.0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]inet6 addr: ::1/128 Scope:Host[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]UP LOOPBACK RUNNING MTU:16436 Metric:1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]RX packets:176 errors:0 dropped:0 overruns:0 frame:0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]TX packets:176 errors:0 dropped:0 overruns:0 carrier:0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]collisions:0 txqueuelen:0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]RX bytes:14304 (14.3 KB) TX bytes:14304 (14.3 KB)[/SIZE][/FONT]
 
[FONT=Courier New][SIZE=2]wlan0 Link encap:Ethernet HWaddr e0:ca:94:f1:9b:31 [/SIZE][/FONT]
[FONT=Courier New][SIZE=2]UP BROADCAST MULTICAST MTU:1500 Metric:1[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]RX packets:0 errors:0 dropped:0 overruns:0 frame:0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]TX packets:0 errors:0 dropped:0 overruns:0 carrier:0[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]collisions:0 txqueuelen:1000[/SIZE][/FONT]
[FONT=Courier New][SIZE=2]RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)[/SIZE][/FONT]
 
I'm having trouble connecting again. I'm not even given the option to see wireless networks. I do have the password correct. I set it to not connect automatically and I am restarting....

---

### Post by vadertater on 2013-01-07
I'd what happened, but I cannot even see the different networks anymore, so I cannot see the step at which the connection fails

---

### Post by squakie on 2013-01-07
Look in [this]("http://askubuntu.com/questions/205575/12-10-x64-rtl8188ce-intermittent-slow-internet-connection") at the 1 answer - it's fairly simple if it works.  Don't worry that the answer says 8192 - just go ahead and try it.

---

### Post by vadertater on 2013-01-08
squakie, I plugged in /etc/modprobe.d/rtl8192.conf and I got No such file or directory. So maybe I need that file...
 
I then plugged in the second command: options rtl8192ce ips =0 fwlps=0 debug =2 and I got command not found. 
 
So from my intuition, I would guess I do not have a particular file or driver that I need to run my realtek wireless card. Would it be as simple as downloading and installing the driver from the realtek website like mentioned in this response [askubuntu.com/a/178098/24489]("http://askubuntu.com/a/178098/24489") (taken from the one you sent me)??

---

### Post by vadertater on 2013-01-09
I found these... not too sure what they are talking about.

[http://www.linlap.com/toshiba_satellite_c850-c855](http://www.linlap.com/toshiba_satellite_c850-c855)
Apparently I managed to pick a laptop that does not work well with any distro. I didn't find too much useful info from the various posts... just that I should stop buying toshiba if I want to use linux pain-free. 

[http://forums.toshiba.com/t5/Networking-Wi-Fi/Any-suitable-linux-for-toshiba-L655-satellite/td-p/120133](http://forums.toshiba.com/t5/Networking-Wi-Fi/Any-suitable-linux-for-toshiba-L655-satellite/td-p/120133)
And above, I found something on another toshiba satellite. And the responder posted what he did to solve the problem. Would a similar thing be feasible for fixing ubuntu??

---

### Post by vadertater on 2013-01-12
Could I get some help with my previous response (with the links)?

I feel like this might be the answer... but A) I'm not entirely sure - at all B) I'd have no idea how to go about attempting to solve this problem. 

Any insight would be greatly appreciated!

---

### Post by vadertater on 2013-01-14
I don't want to try this and mess anything up... I really don't know anything except for "sudo reboot" when it comes to linux and the terminal. I found this fix guide for Ubuntu 8.04. for my wireless trouble. So my questions are:

1) will I be able to attempt this fix using some language changes for my Toshiba model and for this version of Ubuntu and will I really jack anything up if I use the old code or something like that. I really know nothing about linux... so this information would be helpful.

2) Any changes I would need to make to the code?

---

### Post by squakie on 2013-01-14
You need to get the driver from RealTek:

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=48&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true#RTL8188CE)

The readme included says it includes the driver for your adapter - the file was updated Jan 9 of this year.

This is an archive that needs to be unpacked, then the source needs to be compiled using make, followed by sudo make install

If you have any questions or problems trying to do this just post back and we can help you through it.

---

### Post by vadertater on 2013-01-14
Is "make" the compiler program or is it a command for the terminal??

That should clarify a lot. If it's just a command, I should be able to figure out how to use it.

---

### Post by tlhIngan on 2013-01-14
--- Just posted to fix the title. There's no such thing as Ubuntu 12.1, and there are no 34-bit editions.
:lolflag:

---

### Post by squakie on 2013-01-14
You would open a terminal window, change working directory (cd) to the folder the files were unpacked to, then (if the readme doesn't mention a config first):

make

sudo make install


Then I'd reboot.

---

### Post by vadertater on 2013-03-10
Squakie,

I hope it's not too late to keep asking help. I started school right after your last post... and so I was focusing on that. I have started playing around with this again for the past couple hours by reading some other guides and trying to figure out your instructions.

So far this is what I've done.

1. Download linux_mac80211_0012.0207.2013.tar.bz2
2. Transfer linux_mac80211_0012.0207.2013.tar.bz2 via flash drive to ubuntu. I then saved this tar.bz2 to the desktop. I then right clicked that sucker and then hit "extract here" to do something or other... this created rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013
3. I then changed directory as ordered via the following: cd /home/nate/Desktop/rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013
4. Directory was successfully changed.
5. Then I did the following: xdg-open readme
6. readme opens up and it says it will work for my wirelss card, it doesn't specifically mention it will work for ubuntu 12.10, but I assume it will work since it's for >= kernel 2.6.35

and I don't believe it says I need to config anything... so I tried "make" and I got back /lib/modules/3.5.0-17-generic/build: no such file or director. Stop. and on the following line I got [all] Error 2. So I probably have to config something, right? is all this information/instructions found within the readme?

---

### Post by vadertater on 2013-03-10
Further down the readme - at the end actually - it mentions I may need to install wpa_supplicant and install it. So I typed into the terminal: "find wpa_supplicant" and it does not exist, so do you know how to find that? I tried wireless.kernel.org and i am very confused on how to navigate that site.

---

### Post by vadertater on 2013-03-11
Any help from anyone would be greatly appreciated. please

---

### Post by vadertater on 2013-03-11
I am know replying to this thread from Ubuntu 12.10! Thanks for all your help... not sure exactly what I ended up doing... but it worked. And it has been working for about 15 mins longer than it ever has before so I think the future is looking pretty solid for ubuntu and I

thanks! I hope to be bugging your for more advanced questions in the future

---

### Post by vadertater on 2013-03-11
Back again...

I used the Software Updater to update everything, following that, I rebooted... now I'm back in the same hole again. I re-read the entire thread and tried that first solution again, but it didn't work. It said the option command does not exist.

I've tried make, sudo make install and that hasn't worked. It stops at the make. 

When it started working this morning, it was after I was playing with wpa_supplicant. But I'm not sure what that is (I'm pretty sure it's just optional from what I was reading). So... I'm still clueless here. 


Any idea how to install the tarball without internet connection? all the guides I'm finding require me to first use apt-get to install some kind of command software to make installing these a lot easier.

---

