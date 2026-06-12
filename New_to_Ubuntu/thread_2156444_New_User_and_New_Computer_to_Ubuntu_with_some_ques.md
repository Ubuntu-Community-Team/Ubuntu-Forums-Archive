---
title: "New User and New Computer to Ubuntu with some questions"
date: 2013-06-21
forum: New to Ubuntu
---

### Post by MotoDog on 2013-06-21
I am a completely new Ubuntu user.  I have a Zortec Cube (5x5x1.75") with AMD processor.
I installed 12.04 LTS from a USB Thumb Drive.  I did NOT use an AMD version of Ubuntu?  I think it was i386 32 bit version?
I could not find it at the download section online.  I have seen versions with AMD in the file name?

Should I use one of them?

A few other questions.............

So far I don't know how to get the built in Wireless to work.  There is an led on the front panel, it never has lit.

Ubuntu does not see any wireless networks.  Is there a way to see what hardware is in the box thru Ubuntu?


Another problem is plugged in USB Thumb drives are there after booting, but go away sometimes?

They have files written by a PC.  Do they have to be formatted special for Ubuntu?

Thanks for any help, this has been a big learning experience.

---

### Post by ahallubuntu on 2013-06-21
~

---

### Post by ahallubuntu on 2013-06-21
~

---

### Post by papibe on 2013-06-21
Hi MotoDog. Welcome to the forum ):P

The ISO naming convention may be the sort of your confusion. There's no such thing as an special version for Intel or AMD. They are actually two versions: a 32bits (i386), and a 64bits (amd64).

The naming convention has to do with historic reason, but it does not target just AMD processors.

If your processor supports 64bit instructions, then you can choose either version to install. If you have 4GB+ of RAM, I'd recommend using the 64bits version. Below that it is not that important.

Regards.

---

### Post by squakie on 2013-06-21
For your wireless, let's start with some information:

Open a terminal window (search for terminal in the unity menu)

type:

lspci <press enter>

Copy that output (cut and paste) in a reply here.

iwconfig <press enter>

Copy that output (cut and paste) in a reply here.

ifconfig <press enter>

Copy that output (cut and paste) in a reply here.


This will give us a little more information to go on before we offer suggestions or ask more questions.

---

### Post by MotoDog on 2013-06-21
OK, THANKS for all the help!
I can't believe all the replies to my questions!
I still see the USB Thumb Dives go away?
I used the text editor and rebooted to get to a Thumb Drive to get these results.
Now I am on a Windows computer that has access to this group.

Here is the results for the three Terminal Commands I was asked to help figure out the Wireless.

Hope I did it correctly............

mikey@mikey-ZBOXNANO-AD12:~$ lspci 
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Complex 
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 9808 
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Wrestler HDMI Audio [Radeon HD 6250/6310] 
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 14h Processor Root Port 
00:10.0 USB controller: Advanced Micro Devices [AMD] Hudson USB XHCI Controller (rev 03) 
00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [IDE mode] (rev 40) 
00:12.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11) 
00:12.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11) 
00:13.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11) 
00:13.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11) 
00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 14) 
00:14.1 IDE interface: Advanced Micro Devices [AMD] Hudson IDE Controller (rev 40) 
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01) 
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11) 
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40) 
00:14.5 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11) 
00:14.7 SD Host controller: Advanced Micro Devices [AMD] Hudson SD Flash Controller 
00:15.0 PCI bridge: Advanced Micro Devices [AMD] Device 43a0 
00:15.3 PCI bridge: Advanced Micro Devices [AMD] Device 43a3 
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43) 
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1 
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2 
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3 
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4 
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6 
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5 
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7 
03:00.0 Network controller: Ralink corp. Device 3290 
03:00.1 Bluetooth: Ralink corp. Device 3298 
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06) 
mikey@mikey-ZBOXNANO-AD12:~$ 

mikey@mikey-ZBOXNANO-AD12:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

mikey@mikey-ZBOXNANO-AD12:~$ 

mikey@mikey-ZBOXNANO-AD12:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:01:2e:4c:02:31  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:6560 (6.5 KB)  TX bytes:6560 (6.5 KB) 

mikey@mikey-ZBOXNANO-AD12:~$

---

### Post by ahallubuntu on 2013-06-21
~

---

### Post by MotoDog on 2013-06-22
Trying to get Ralink RT3290 installed, things went as instructed for a while!

I made it to step 6 in the procedure.  After editing the config.mk file OK, the "make" command had lots of warnings.
It took lots of time to complete.

I tried it a second time and it failed quickly?

When I did a "sudo gedit/ect/modules' " I got a " >"  ??
maybe nothing in that file?
The instructions say save and exit, but with > showing, I did not know how to save and exit?

---

### Post by newbie2ubunt2 on 2013-06-22
i also am new will be following this thread, 1 question though can u load drivers from jump drive to ubuntu without internet i have a dell pavilion 4 i just blew windows away and i think i messed up oh well only one way to learn jump right in.

---

### Post by deadflowr on 2013-06-22
Was that a complete typo?

The command should be

```
gksudo gedit /etc/modules
```

gedit is the text editor.
/etc/modules is the file.
and gksudo gives you root privileges for graphical applications.

gksudo for graphical
sudo for non-graphical, aka command line programs.

---

### Post by newbie2ubunt2 on 2013-06-22
deadflwr will this help in loading aircard program also i have it on my desktop but can't seem to do anything with it it for a verizon vl600 aircard
i typed in this command i only have 2 modules that load at boot they are  lp, rtc what ever they are

---

### Post by MotoDog on 2013-06-22
[http://askubuntu.com/questions/253632/how-do-i-get-a-ralink-rt3290-wireless-card-working](http://askubuntu.com/questions/253632/how-do-i-get-a-ralink-rt3290-wireless-card-working)

I used this thread and the command in step 8 was sudo gedit/ect/modules'  the modules with something at the thingy at the  end is probably a typo?

Although I did not know how to get out of the editor in Terminal (>) I gave up.

Guess what!!!  I went back later and I noticed the tiny led on the box was now light!

So, without knowing why, it works fine. I connect to the house wireless router!
 The Zotac Box is tiny 5x5x1.75"  It has 4 USB, 2 Video Outputs ( I had to buy and adapter to run a VGA monitor, on Amazon).  It has audio outputs and inputs as well as a camera card reader on the front.
They even added and optical sensor on the front and a remote control and dongle?

So I am really happy with it and Ubuntu 1204 LTS 32 bit.  I am trying to get Microchips MPLABX working now with an ICD3 debugger for programming Pics.  Lots of bugs in the Linux Version!    They are trying to drop there Windows MPLAB,
I am really worried.  The X version uses Java and Netbeans, seems very complicated and buggy?

So the link above did the trick, even though I did not understand everything.

Thanks, I am glad I asked for help here, I would have never figured out anything without you guys!
Mikey:D

---

