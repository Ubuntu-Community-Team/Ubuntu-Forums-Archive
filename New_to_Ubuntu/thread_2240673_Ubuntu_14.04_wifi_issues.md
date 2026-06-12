---
title: "Ubuntu 14.04 wifi issues"
date: 2014-08-21
forum: New to Ubuntu
---

### Post by DanielMartin on 2014-08-21
Hello

I'm quite new to Ubuntu, I've downloaded and installed the latest version. I have a few issues.

- my wifi doesn't reconnect after suspending my laptop and will only work for an hour or so when turned on and I'm using the laptop before I have to restart the system to get a better signal. Any drop in the signal whilst I'm using the laptop will make it stop working.

- microphone on the laptop doesn't work / is barely barely audible (as in, my voice is faint in the distance despite being close to the laptop despite turning the microphone up in sound settings).

Solutions please wonderful people? :)

Laptop: Lenovo G50-70 i5 8gb

---

### Post by Jonathan Precise on 2014-08-21
Hello DanielMartin. Welcome to the forums!


1) Try running [FONT=Courier New]pkexec kill -9 `pidof NetworkManager`[/FONT], and type your password when prompted.
2) Same problem here. What do you use the microphone for? It is unusable for me in voice recording, yet it works like a charm for me in screen recording.

---

### Post by DanielMartin on 2014-08-22
I don't know how to run that command ... I'm completely new to Ubuntu. I can run sudo commands but not commands unless people type out exactly what to put.

---

### Post by jason128 on 2014-08-22
I'm in the exact same boat as you, Daniel. I've some command line experience from other os, but very little in linux. I will be following this thread closely. I've heard this community is second-to-none as far as supporting members.

---

### Post by Jonathan Precise on 2014-08-22
@DanielMartin: Every time the WiFi doesn't reconnect after suspend, please open a terminal (press Ctrl. + Alt. + T) and copy/paste the command:
```
pkexec kill -9 `pidof NetworkManager`
```
It should not give any output. If it does, post it here with [noparse]```
Code Tags
```:
```
Code Tags
```

[HR][/HR]

@jason128: Welcome to the forums!

Please follow the above instructions to fix problem #1.

---

### Post by jason128 on 2014-08-22
thank you @jonathan. I'm actually not sure my wifi problem is the same as @daniel. I've never successfully connected over wifi. Always had to use hard cable. Ubuntu "sees" all available networks and attempts to connect, albeit unsuccesfully. I've been searching around some qa forums and have run across some extensive answers involving using the terminal to id my laptop hardware, then manually downloading driver, then using the terminal to "install" the driver. Idk if that is what I need to do?

---

### Post by jason128 on 2014-08-22
I'm currently checking out the [http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108) to get as much initial help as i can, as far as basic terminal character entry.

---

### Post by DanielMartin on 2014-08-22
It gives no output - failed to parse argument 'pidof NetworkManager'

---

### Post by sotiris2 on 2014-08-22
Did you copy and paste the command or typed it in yourself? 
Also try ```
sudo service network-manager restart
```
It will ask for you password but it wont show dots or asteriks as you type. It is working though so just type and press enter.

---

### Post by DanielMartin on 2014-08-22
> **sotiris2 said:**
> Did you copy and paste the command or typed it in yourself? 
Also try ```
sudo service network-manager restart
```
It will ask for you password but it wont show dots or asteriks as you type. It is working though so just type and press enter.

   It gives no output - failed to parse argument 'pidof NetworkManager' - I typed this in myself
 

 and the second piece of code just put my wifi on trying to  connect for several minutes before saying I was disconnected, trying again - before I got bored of waiting for it to connect and restarted my system which immediately connected to the wifi.

---

### Post by sotiris2 on 2014-08-22
Can you give us the outputs of ```
sudo lshw | grep [Ww]ireless ; sudo lspci | grep [wW]ireless
``` ?

---

### Post by DanielMartin on 2014-08-22
danielmartin@danielmartin-Lenovo-G50-70:~$ sudo lshw | grep [Ww]ireless ; sudo lspci | grep [wW]ireless
[sudo] password for danielmartin: 
                description: Wireless interface
                product: RTL8723BE PCIe Wireless Network Adapter
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8723be driverversion=3.13.0-34-generic firmware=N/A ip=192.168.1.72 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter
danielmartin@danielmartin-Lenovo-G50-70:~$

---

### Post by sotiris2 on 2014-08-22
Well there are some problems with this device as seen [here](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1320070).
They suggest some technical solutions that I 'm not sure I can guide you through (and I have to go online for now) but maybe somebody else can. 

A temp fix is to run ```
sudo [FONT=Ubuntu Mono]rmmod rtl8723be && modprobe rtl8723be
``` when you lose connectivity which should enable to reconnect without rebooting. Apparently later versions of the kernel will fix this bug so in the future as you update you won't have to fix it manually.
[/FONT]

---

### Post by varunendra on 2014-08-22
> **sotiris2 said:**
> A temp fix is to run ```
sudo rmmod rtl8723be && modprobe rtl8723be
```

If this works, you can make it automatic by creating a conf file as follows -
```
touch Desktop/modules
```
This will create a file named "modules" on your Desktop. Now open it with your text editor, and put (copy-paste) the following line in it -
```
SUSPEND_MODULES="$SUSPEND_MODULES rtl8723be"
```
Proofread, save and close the file.

Now copy it to the location where it should be -
```
sudo cp Desktop/modules /etc/pm/config.d
```
Reboot > suspend > resume, and let us know if it worked.

Basically, it tries to do the same thing as the combination of the rmmod/modprobe commands sotiris2 suggested, only automatically and elegantly.

However, if it doesn't help (nor do the rmmod/modprobe commands), please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

**PS:**
By the way, it is highly recommended to use "modprobe -r" instead of "rmmod". It does the same thing (removes the module due to "-r" option), but safely and smartly compared to "rmmod" which is potentially not as much safe (may crash a running session in some cases).

---

### Post by DanielMartin on 2014-08-22
Is it worth trying this now? I downloaded two kernels from the link to the problem above and it seems to have solved the issue but I think its slowed my system down a little bit. I think the WIFI issue is resolved now I think ... 

Its just the microphone issue now that exists I think

---

### Post by varunendra on 2014-08-22
Your thread title indicates a wifi issue. If that is solved, please mark the thread as such using "Thread Tools" link above the top post. For your microphone issue, you should start a new thread in "Hardware" or "Multimedia" section, with a title that clearly indicates the problem you want to solve.

And of course, if there is no problem anymore (with the wifi), no fix is needed. :)

---

### Post by rakesh343 on 2015-01-13
Hi Varunendra, sotiris2

I'm facing a similar problem at this thread that remains unresolved. I've done all that suggested in this thread but it remains unresolved. Need some urgent help  there. It is at this: [http://ubuntuforums.org/showthread.php?t=2260466&p=13206625#post13206625]("http://ubuntuforums.org/showthread.php?t=2260466&p=13206625#post13206625")

Please help.

---

### Post by sotiris2 on 2015-01-15
So you get permission denied. Try it like this ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -r rtl8723be && sudo modprobe rtl8723be
```[/FONT][/COLOR]

---

### Post by paul205 on 2015-05-03
The only way that worked for me, was stated in the bug report at :

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1320070](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1320070)

at the end there is a link to a script which disables your bluetooth (and maybe other things)..... This fixed the problem for me ... But obviously stopped bluetooth working ...

Here is a direct liink to the script supplied by [https://launchpad.net/~pqwoerituytrueiwoq:](https://launchpad.net/~pqwoerituytrueiwoq:)

[http://pastebin.com/LiC7PA1M](http://pastebin.com/LiC7PA1M)

Paul

---

