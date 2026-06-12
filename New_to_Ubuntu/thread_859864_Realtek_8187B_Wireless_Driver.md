---
title: "Realtek 8187B Wireless Driver"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by Zerp64 on 2008-07-15
This is driving me mad. I have been trying to get Ubuntu 8.04 LTS working on one of my client's laptops. I have everything on his laptop working just fine (it's a Gateway T-Series), except for his Realtek 8187B Wireless card. I have tried Ndiswrapper. I have tried installing those modified Linux Drivers. Nothing had worked so far. This is becoming a major pain for me, and I've been at it for days.

If you need any additional info, I'd be happy to supply it for you. Just *please* help me out here! I am willing to try anything, including what I have already tried, in case I missed a step.

---

### Post by echo314 on 2008-07-15
First things first. Lets get some more info on what you have tried so far. 

Can you show us the commands you used and output you got while using ndiswrapper in the command line, and tell us about the drivers you are trying to use with it (what version of Windows they are for, what kids of files ex. .ini, .bin)

---

### Post by bobnutfield on 2008-07-15
There are a number of threads on this forum for this chipset, here is one of them:

[http://ubuntuforums.org/showthread.php?t=571046&highlight=Realtek+8187B]("http://ubuntuforums.org/showthread.php?t=571046&highlight=Realtek+8187B")

I myself have it working fine with ndiswrapper.  You must use the Win98 drivers and add one extra line to the .inf file and it works.

Bob

EDIT:  If you are interested, I will give you step by step instructions on how I got mine to work.

---

### Post by Zerp64 on 2008-07-15
> **bobnutfield said:**
> There are a number of threads on this forum for this chipset, here is one of them:

[http://ubuntuforums.org/showthread.php?t=571046&highlight=Realtek+8187B]("http://ubuntuforums.org/showthread.php?t=571046&highlight=Realtek+8187B")

I myself have it working fine with ndiswrapper.  You must use the Win98 drivers and add one extra line to the .inf file and it works.

Bob

EDIT:  If you are interested, I will give you step by step instructions on how I got mine to work.

Please post some instructions! That would be great!

Anyways, here's what I've done so far:

I have tried to use the patched Reaktek drivers that supposedly work with kernel 2.6.24. (found [here.]("http://www.datanorth.net/~cuervo/rtl8187b/")) I did get them to work, in the sense of the network manager detects the wireless card and I am able to pick an access point. I tried to connect to a WEP-protected point, which cause a complete freeze. Not even the Raising Skinny Elephants shut down key worked, so I assume it was a kernel panic. And plus, even if the thing did work, the owner of this laptop would have to input those couple commands ever time the computer boots up. Not fun.

I have also tried using Ndiswrapper with WinXP, Win2k, and Win98SE Realtek driver. Obviously didn't work, although installing the 2k and 98SE drivers through the Ndiswrapper GUI showed that the hardware was present. The card did not show under the network manager, so I couldn't do anything with it regardless of Ndiswrapper saying the hardware was present.

By the way, **lsusb** shows this when I run it:
```
dan@dan-laptop:~$ lsusb
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 12cf:c001  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. 
Bus 001 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 04f2:b027 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 0000:0000  

```

---

### Post by bobnutfield on 2008-07-16
OK, if you have done all of that, I don't need to go all through the steps, just this.

As mentioned, you must use the Win98 (not win98se) driver from the Realtek site, which you said you have.  You will need the .inf file and the .sys file.  I put them both in my home directory to find them easily with ndiswrapper.

Before installing them with ndiswrapper, open the .inf file with a text editor.  You will see a section of the file that looks like this:

```
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB/VID_0BDA&PID_8187&REV_0200
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8189&REV_0200
```

Add this line directly below it:

```
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8197&REV_0200
```

Save the changes and install with ndiswrapper.  I am assuming you know all the steps with ndiswrapper.

Then, of course verify that the "device present" report is given.

Then, open a terminal and issue these commands:

```
sudo ifconfig wlan0 mode managed
```
```
sudo ifconfig wlan0 essid <your essid>
```
```
sudo ifconfig wlan0 up
```
```
dhcpcd wlan0
```

By this time your wireless should be showing up in the network config GUI.

If you are not able to save the config entered above  with the network GUI, you may have to write it as a little script and save to /etc/local/rc.d so that it comes when you boot.

And thats it!  It works great for me with a Toshiba A210.

Good Luck with it.

Bob

---

### Post by Zerp64 on 2008-07-17
> **bobnutfield said:**
> OK, if you have done all of that, I don't need to go all through the steps, just this.

As mentioned, you must use the Win98 (not win98se) driver from the Realtek site, which you said you have.  You will need the .inf file and the .sys file.  I put them both in my home directory to find them easily with ndiswrapper.

Before installing them with ndiswrapper, open the .inf file with a text editor.  You will see a section of the file that looks like this:

```
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB/VID_0BDA&PID_8187&REV_0200
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8189&REV_0200
```

Add this line directly below it:

```
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8197&REV_0200
```

Save the changes and install with ndiswrapper.  I am assuming you know all the steps with ndiswrapper.

Then, of course verify that the "device present" report is given.

Then, open a terminal and issue these commands:

```
sudo ifconfig wlan0 mode managed
```
```
sudo ifconfig wlan0 essid <your essid>
```
```
sudo ifconfig wlan0 up
```
```
dhcpcd wlan0
```

By this time your wireless should be showing up in the network config GUI.

If you are not able to save the config entered above  with the network GUI, you may have to write it as a little script and save to /etc/local/rc.d so that it comes when you boot.

And thats it!  It works great for me with a Toshiba A210.

Good Luck with it.

Bob

Didn't work. Running

 ```
sudo ifconfig wlan0 mode managed
```

Returns:

 ```
mode: Unknown host
```

So of course I still need help. Do you think you can maybe send me a link to a win98 driver real quick? I do not think that I have the correct driver. Maybe you can just help me out a little bit more?

---

### Post by Zerp64 on 2008-07-19
Bump... come on guys, I need one little link. I can't find the Win98 driver anywhere.

---

### Post by Zerp64 on 2008-07-20
I just realized... this laptop is 64-bit. The drivers I've been trying to use (most recently from [_here_]("http://meanmachine.wordpress.com/2008/05/15/wireless-rtl8187b-on-toshiba-a200-1v0-ubuntu-804/")) are 32-bit! I've checked my syslogs after noticing that ndiswrapper doesn't load on boot, and they say "kernel is 64-bit, but Windows driver is not 64-bit; bad magic 010B".

I don't like this... how do I get around this? Will I need to reinstall the 32-bit version of Ubuntu on this system?


[EDIT] Okay, let's start over. Installed a 32-bit version of Ubuntu 8.04. Now when I try to follow the instructions mentioned in this post, ndiswrapper no longer says that the hardware is present.

Please help me. I'm going slowly insane.

---

### Post by bobnutfield on 2008-07-24
[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187B]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=1&PFid=1&Level=6&Conn=5&DownTypeID=3&GetDown=false&Downloads=true#RTL8187B")

The above link will take you to the realtek site for the correct driver.  Scroll down to the 8187B section, download the drivers, and select the **WIN98** driver (XP, WinME, Vista will NOT work.)  Do the editing to the inf file as I have posted, and it should work just like it has for me on Hardy (I am using it now to write this).  Make sure that after you get the "hardware present" response that you do:

```
sudo modprobe ndiswrapper
```

It is after that that the hardware should show up in your GUI config applications.  

Let us know how it works for you.

Bob

---

### Post by tjwoosta on 2008-07-24
you should really search the forums before posting a topic

(this driver has been covered multiple times)

**the realtek linux driver from the site will not work**

but anyway i can help you out (i have this same exact driver in a gateway m-series)

this is the best thread around that covers this card
[http://ubuntuforums.org/showthread.php?t=765671]("http://ubuntuforums.org/showthread.php?t=765671")

if you cant find the working driver there then you probably dont have an 8187b

EDIT: also i can confirm that the linux driveer mentioned in this thread does work on 64bit and 32bit no-problem

---

### Post by Zerp64 on 2008-07-25
> **tjwoosta said:**
> you should really search the forums before posting a topic

(this driver has been covered multiple times)

**the realtek linux driver from the site will not work**

but anyway i can help you out (i have this same exact driver in a gateway m-series)

this is the best thread around that covers this card
[http://ubuntuforums.org/showthread.php?t=765671]("http://ubuntuforums.org/showthread.php?t=765671")

if you cant find the working driver there then you probably dont have an 8187b

EDIT: also i can confirm that the linux driveer mentioned in this thread does work on 64bit and 32bit no-problem

Yes, I saw that this was posted a few times after I posted it myself. Sorry about that...

Anyways, your guys' advice worked. The problem has been fixed, and now the guy is happy with his speedy new OS. He's a really big fan of the Compiz cube...

---

### Post by bobnutfield on 2008-07-27
Well, I certainly cannot speak for everyone, but I have a Toshiba A210 with the Realtek 8187B, and I did not get the drivers to work for me described in that thread..  As I have mentioned, I DID get it to work beautifully with NDISWRAPPER and the Win98 modified .inf driver.  Further, I do not have to do anything to bring the interface up when I boot the laptop.  I simply put the little script I described above in rc.d/local, and it works great.  If it is not working for others using this method, I cannot tell you why other than it may be specific to the laptop in question.  As far as I know, all of the 8187B wireless chipsets are internal USB connections, which is why the .inf file of the Win98 driver has to be edited.

Bob

---

### Post by Zerp64 on 2008-07-30
> **bobnutfield said:**
> Well, I certainly cannot speak for everyone, but I have a Toshiba A210 with the Realtek 8187B, and I did not get the drivers to work for me described in that thread..  As I have mentioned, I DID get it to work beautifully with NDISWRAPPER and the Win98 modified .inf driver.  Further, I do not have to do anything to bring the interface up when I boot the laptop.  I simply put the little script I described above in rc.d/local, and it works great.  If it is not working for others using this method, I cannot tell you why other than it may be specific to the laptop in question.  As far as I know, all of the 8187B wireless chipsets are internal USB connections, which is why the .inf file of the Win98 driver has to be edited.

Bob

Yeah, I believe it was just specific to this laptop, although I am no hardware guru and cannot even theorize what the differences between the two chips are. And why the hell did these laptop manufacturers decide to use an internal USB chip? Am I being stupid, or is this actually as the name implies?

Anyways, just a small update: The wireless device was detected, and listed available networks with appropriate signal strengths shown, but could not connect. I solved this by running "sudo /etc/init.d/networking stop". It could then connect freely to his WPA-encrypted wireless router. Can anyone tell me why I needed to *stop* networking to allow wireless networking? Was it because the laptop was using Ndiswrapper for the wireless driver?

---

### Post by bobnutfield on 2008-07-31
> Anyways, just a small update: The wireless device was detected, and listed available networks with appropriate signal strengths shown, but could not connect. I solved this by running "sudo /etc/init.d/networking stop". It could then connect freely to his WPA-encrypted wireless router. Can anyone tell me why I needed to stop networking to allow wireless networking? Was it because the laptop was using Ndiswrapper for the wireless driver?

This is usually because the internal eth0 is up at boot time and may conflict with other networking, such as wireless.  At least, that is how it has worked for me,  You can have both ethernet and wireless working at the same time, but I think they have to be brought up separately.

---

