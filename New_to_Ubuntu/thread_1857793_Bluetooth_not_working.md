---
title: "Bluetooth not working"
date: 2011-10-11
forum: New to Ubuntu
---

### Post by amitshiva on 2011-10-11
[FONT="Trebuchet MS"]Hello everyone,

I'm completely new to Ubuntu(read Windows refugee)and currently using 11.04. Though everything seems to be working fine, there is a problem with bluetooth. For some reason, it is not working. I have a Dell Inspiron 1440 Laptop and the wireless works flawlessly(just had to install additional drivers). But can't get this working.

I have read many post on various sites(including threads in this forum) but they seem to bring no smile to my face.

The bluetooth icon is pretty much visible with the option of turning on or off, but that doesn't solve.

Please help.[/FONT]

---

### Post by JSchultheis on 2011-10-11
> **amitshiva said:**
> [FONT="Trebuchet MS"]Hello everyone,

I'm completely new to Ubuntu(read Windows refugee)and currently using 11.04. Though everything seems to be working fine, there is a problem with bluetooth. For some reason, it is not working. I have a Dell Inspiron 1440 Laptop and the wireless works flawlessly(just had to install additional drivers). But can't get this working.

I have read many post on various sites(including threads in this forum) but they seem to bring no smile to my face.

The bluetooth icon is pretty much visible with the option of turning on or off, but that doesn't solve.

Please help.[/FONT]

Hello!

What do you want the bluetooth to do? Telephone? Listen to music/video?

Is the problem with the computer or the 'headset'? Do you have indication that it is turning on? (this can also be an option in BIOS to turn on and off bluetooth)

Have you successfully used the bluetooth headset on another device?

---

### Post by JSchultheis on 2011-10-11
[SIZE="2"][FONT="Times New Roman"][COLOR="Blue"]***_[[COLOR="Blue"]click the blue text :check this thread out :thread link[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1856128")_***[/COLOR][/FONT][/SIZE]

---

### Post by matt_symes on 2011-10-11
Hi

Is the bluetooth built in ?

Open a terminal and type these commands on after another
```

lsusb
sudo hcitool dev
sudo hcitool scan
sudo rfkill list
```

Enter your password when prompted. It will not be echoed to the screen.

Post the results back here by copying and pasting from the terminal into your next post.

Kind regards

---

### Post by amitshiva on 2011-10-11
> **matt_symes said:**
> Hi

Is the bluetooth built in ?

Open a terminal and type these commands on after another
```

lsusb
sudo hcitool dev
sudo hcitool scan
sudo rfkill list
```

Enter your password when prompted. It will not be echoed to the screen.

Post the results back here by copying and pasting from the terminal into your next post.

Kind regards

Here are the results:

amit@amit-Inspiron-1440:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:6400 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
amit@amit-Inspiron-1440:~$ sudo hcitool dev
[sudo] password for amit: 
Devices:
amit@amit-Inspiron-1440:~$ sudo hcitool scan
Device is not available: No such device
amit@amit-Inspiron-1440:~$ sudo rfkill list
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
amit@amit-Inspiron-1440:~$

---

### Post by amitshiva on 2011-10-11
> **JSchultheis said:**
> Hello!

What do you want the bluetooth to do? Telephone? Listen to music/video?

Is the problem with the computer or the 'headset'? Do you have indication that it is turning on? (this can also be an option in BIOS to turn on and off bluetooth)

Have you successfully used the bluetooth headset on another device?

Hi,

I just want bluetooth to transfer files between phone-laptop, etc. The problem is that the in-built bluetooth adapter doesn't seem to be working. The bluetooth icon is pretty much visible but doesn't work. Tried all options, but all in vain.

Please help

---

### Post by matt_symes on 2011-10-11
Hi

This is a problem
> 
1: dell-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: noOpen a terminal and type

```
sudo rfkill unblock all
```Then try to connect again. Post back if unsuccessful.

Kind regards

---

### Post by amitshiva on 2011-10-11
> **matt_symes said:**
> Hi

This is a problem
Open a terminal and type

```
sudo rfkill unblock all
```Then try to connect again. Post back if unsuccessful.

Kind regards

Thanks a ton Matt for all your help, but it doesn't seem to work even now.

Here are the results:


amit@amit-Inspiron-1440:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 013: ID 413c:8162 Dell Computer Corp. 
Bus 003 Device 012: ID 413c:8161 Dell Computer Corp. 
Bus 003 Device 011: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0c45:6400 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
amit@amit-Inspiron-1440:~$ sudo hcitool dev
[sudo] password for amit: 
Devices:
amit@amit-Inspiron-1440:~$ sudo hcitool scan
Device is not available: No such device
amit@amit-Inspiron-1440:~$ sudo rfkill list
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
amit@amit-Inspiron-1440:~$ 


I don't wanna sound greedy, but please help. So far this is the only thing which is taking time.

Thanks again

---

### Post by matt_symes on 2011-10-11
Hi

Let's check the service is running. What's the output of (post back both commands)
[FONT=monospace]
[/FONT]```
service bluetooth status
```

and let's try restarting it just in case.

```
sudo service bluetooth restart
```

Kind regards

---

### Post by gandaran on 2011-10-11
> Bus 003 Device 011: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
have you installed the broadcom wireless drivers?
look in additional drivers, if the driver is there activate it.

edit:
just read now on your first post you did install from additional drivers so now the question is where they broadcom drivers? or do you have a different wireless chipset brand?

have a look at this google search
[http://www.google.pt/#hl=en-us&cp=21&gs_id=2&xhr=t&q=BCM2046B1+USB+2.0+Hub+part+of+bcm2046+bluetooth&pf=p&sclient=psy-ab&site=&source=hp&pbx=1&oq=BCM2046B1+USB+2.0+Hub&aq=0vL&aqi=g-vL2&aql=&gs_sm=&gs_upl=&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=a79fc2c3ec77b05f&biw=1024&bih=652](http://www.google.pt/#hl=en-us&cp=21&gs_id=2&xhr=t&q=BCM2046B1+USB+2.0+Hub+part+of+bcm2046+bluetooth&pf=p&sclient=psy-ab&site=&source=hp&pbx=1&oq=BCM2046B1+USB+2.0+Hub&aq=0vL&aqi=g-vL2&aql=&gs_sm=&gs_upl=&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=a79fc2c3ec77b05f&biw=1024&bih=652)
looks like this bluetooth device is very difficult

---

### Post by amitshiva on 2011-10-12
> **matt_symes said:**
> Hi

Let's check the service is running. What's the output of (post back both commands)
[FONT=monospace]
[/FONT]```
service bluetooth status
```

and let's try restarting it just in case.

```
sudo service bluetooth restart
```

Kind regards

Hi, 

Here are the results and it's surprising and confusing at the same time

amit@amit-Inspiron-1440:~$ service bluetooth status
 * bluetooth is not running
amit@amit-Inspiron-1440:~$ sudo service bluetooth restart
[sudo] password for amit: 
 * Stopping bluetooth                                                    [ OK ] 
 * Starting bluetooth                                                    [ OK ] 
amit@amit-Inspiron-1440:~$ service bluetooth status
 * bluetooth is not running
amit@amit-Inspiron-1440:~$ 


Any clue please?

---

### Post by amitshiva on 2011-10-12
> **gandaran said:**
> have you installed the broadcom wireless drivers?
look in additional drivers, if the driver is there activate it.

edit:
just read now on your first post you did install from additional drivers so now the question is where they broadcom drivers? or do you have a different wireless chipset brand?

have a look at this google search
[http://www.google.pt/#hl=en-us&cp=21&gs_id=2&xhr=t&q=BCM2046B1+USB+2.0+Hub+part+of+bcm2046+bluetooth&pf=p&sclient=psy-ab&site=&source=hp&pbx=1&oq=BCM2046B1+USB+2.0+Hub&aq=0vL&aqi=g-vL2&aql=&gs_sm=&gs_upl=&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=a79fc2c3ec77b05f&biw=1024&bih=652](http://www.google.pt/#hl=en-us&cp=21&gs_id=2&xhr=t&q=BCM2046B1+USB+2.0+Hub+part+of+bcm2046+bluetooth&pf=p&sclient=psy-ab&site=&source=hp&pbx=1&oq=BCM2046B1+USB+2.0+Hub&aq=0vL&aqi=g-vL2&aql=&gs_sm=&gs_upl=&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=a79fc2c3ec77b05f&biw=1024&bih=652)
looks like this bluetooth device is very difficult


Yes, I have broadcom drivers installed. However, being a windows user(read refugee), I had to install a separate bluetooth drivers to get in running(apart from WiFi drivers). Do you think that could be the problem. 

As said, the WiFi is working fine, it's just this damn bluetooth.

I'm also enclosing a screenshot of the driver details.

---

### Post by matt_symes on 2011-10-12
Hi

Let's check the kernel messages. Open a terminal and type
[FONT=monospace]
[/FONT]```
dmesg | grep -i bluetooth

```

Please post results back here.

Kind regards

---

### Post by amitshiva on 2011-10-12
> **matt_symes said:**
> Hi

Let's check the kernel messages. Open a terminal and type
[FONT=monospace]
[/FONT]```
dmesg | grep -i bluetooth

```

Please post results back here.

Kind regards

Sorry but the results are....actually nothing

amit@amit-Inspiron-1440:~$ dmesg | grep -i bluetooth
amit@amit-Inspiron-1440:~$ 
amit@amit-Inspiron-1440:~$ dmesg | grep -i bluetooth
amit@amit-Inspiron-1440:~$ dmesg | grep -i bluetooth
amit@amit-Inspiron-1440:~$ dmesg | grep -i bluetooth
amit@amit-Inspiron-1440:~$

---

### Post by amitshiva on 2011-10-12
> **amitshiva said:**
> Sorry but the results are....actually nothing

amit@amit-Inspiron-1440:~$ dmesg | grep -i bluetooth
amit@amit-Inspiron-1440:~$ 
amit@amit-Inspiron-1440:~$ dmesg | grep -i bluetooth
amit@amit-Inspiron-1440:~$ dmesg | grep -i bluetooth
amit@amit-Inspiron-1440:~$ dmesg | grep -i bluetooth
amit@amit-Inspiron-1440:~$

And when I turned ON the bluetooth, this is what came up:


amit@amit-Inspiron-1440:~$ amit@amit-Inspiron-1440:~$ dmesg | grep -i bluetooth
amit@amit-Inspiron-1440:~$: command not found
amit@amit-Inspiron-1440:~$ amit@amit-Inspiron-1440:~$ 
amit@amit-Inspiron-1440:~$: command not found
amit@amit-Inspiron-1440:~$ amit@amit-Inspiron-1440:~$ dmesg | grep -i bluetooth
amit@amit-Inspiron-1440:~$: command not found
amit@amit-Inspiron-1440:~$ amit@amit-Inspiron-1440:~$ dmesg | grep -i bluetooth
amit@amit-Inspiron-1440:~$: command not found
amit@amit-Inspiron-1440:~$ amit@amit-Inspiron-1440:~$ dmesg | grep -i bluetooth
amit@amit-Inspiron-1440:~$: command not found
amit@amit-Inspiron-1440:~$ amit@amit-Inspiron-1440:~$ 
amit@amit-Inspiron-1440:~$: command not found
amit@amit-Inspiron-1440:~$

---

### Post by matt_symes on 2011-10-12
Hi

```
amit@amit-Inspiron-1440:~$ amit@amit-Inspiron-1440:~$ dmesg | grep -i bluetooth
amit@amit-Inspiron-1440:~$: command not found
amit@amit-Inspiron-1440:~$ amit@amit-Inspiron-1440:~$ 
amit@amit-Inspiron-1440:~$: command not found
amit@amit-Inspiron-1440:~$ amit@amit-Inspiron-1440:~$ dmesg | grep -i bluetooth
amit@amit-Inspiron-1440:~$: command not found
amit@amit-Inspiron-1440:~$ amit@amit-Inspiron-1440:~$ dmesg | grep -i bluetooth
amit@amit-Inspiron-1440:~$: command not found
amit@amit-Inspiron-1440:~$ amit@amit-Inspiron-1440:~$ dmesg | grep -i bluetooth
amit@amit-Inspiron-1440:~$: command not found
amit@amit-Inspiron-1440:~$ amit@amit-Inspiron-1440:~$ 
amit@amit-Inspiron-1440:~$: command not found
amit@amit-Inspiron-1440:~$
```

I don't quite understand the above.

Let's try these steps.

1. Switch off your bluetooth.
2. In the terminal type
```
sudo dmesg -c > /dev/null
```
3. Switch on bluetooth and wait 10 seconds.
4. type
```
dmesg
```
5. Post results back here.

Please can you post between code tags like this

[noparse]```
dmesg results
```[/noparse]

to get non formatted output like this

```
dmesg results
```

Kind regards

---

### Post by amitshiva on 2011-10-12
> **matt_symes said:**
> Hi

```
amit@amit-Inspiron-1440:~$ amit@amit-Inspiron-1440:~$ dmesg | grep -i bluetooth
amit@amit-Inspiron-1440:~$: command not found
amit@amit-Inspiron-1440:~$ amit@amit-Inspiron-1440:~$ 
amit@amit-Inspiron-1440:~$: command not found
amit@amit-Inspiron-1440:~$ amit@amit-Inspiron-1440:~$ dmesg | grep -i bluetooth
amit@amit-Inspiron-1440:~$: command not found
amit@amit-Inspiron-1440:~$ amit@amit-Inspiron-1440:~$ dmesg | grep -i bluetooth
amit@amit-Inspiron-1440:~$: command not found
amit@amit-Inspiron-1440:~$ amit@amit-Inspiron-1440:~$ dmesg | grep -i bluetooth
amit@amit-Inspiron-1440:~$: command not found
amit@amit-Inspiron-1440:~$ amit@amit-Inspiron-1440:~$ 
amit@amit-Inspiron-1440:~$: command not found
amit@amit-Inspiron-1440:~$
```

I don't quite understand the above.

Let's try these steps.

1. Switch off your bluetooth.
2. In the terminal type
```
sudo dmesg -c > /dev/null
```
3. Switch on bluetooth and wait 10 seconds.
4. type
```
dmesg
```
5. Post results back here.

Please can you post between code tags like this

[noparse]```
dmesg results
```[/noparse]

to get non formatted output like this

```
dmesg results
```

Kind regards

Hello,

Here are the results. Pardon me if i haven't got the codes right, since i'm newbie and learning to do all this Linux thing.


```
amit@amit-Inspiron-1440:~$ sudo dmesg -c > /dev/null
[sudo] password for amit: 
amit@amit-Inspiron-1440:~$ dmesg
[ 4461.800161] usb 3-1: new full speed USB device using uhci_hcd and address 8
[ 4461.980168] hub 3-1:1.0: USB hub found
[ 4461.982096] hub 3-1:1.0: 3 ports detected
[ 4462.262197] usb 3-1.1: new full speed USB device using uhci_hcd and address 9
[ 4462.400311] input: HID 413c:8161 as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.1/3-1.1:1.0/input/input15
[ 4462.400543] generic-usb 0003:413C:8161.0005: input,hidraw0: USB HID v1.11 Keyboard [HID 413c:8161] on usb-0000:00:1a.0-1.1/input0
[ 4462.474125] usb 3-1.2: new full speed USB device using uhci_hcd and address 10
[ 4462.605330] input: HID 413c:8162 as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.2/3-1.2:1.0/input/input16
[ 4462.605566] generic-usb 0003:413C:8162.0006: input,hidraw1: USB HID v1.11 Mouse [HID 413c:8162] on usb-0000:00:1a.0-1.2/input0
amit@amit-Inspiron-1440:~$
```

---

### Post by matt_symes on 2011-10-12
Hi
[FONT=monospace]
And that is after enabling bluetooth ? There is no mention of a bluetooth device at all.

Is it enabled in the BIOS ?

Kind regards
[/FONT]

---

### Post by amitshiva on 2011-10-12
> **matt_symes said:**
> Hi
[FONT=monospace]
And that is after enabling bluetooth ? There is no mention of a bluetooth device at all.

Is it enabled in the BIOS ?

Kind regards
[/FONT]

Yes, have checked, it is enabled.

I'm not sure, but in one of the previous posts, it is mentioned that for some Dell bluetooth drivers, some users got it going only after they booted into Windows and installed drivers there and activated and then booted in Ubuntu.

Sounds weird to me, but seems like there is no hope for this one, Been reading about this is many forums and posts, but all in vain.

Another thing, even in Windows, I had to install a drivers individually both for WiFi and bluetooth. However in Ubuntu, I only see WiFi driver. Could that be a problem too?

---

### Post by gandaran on 2011-10-12
> **amitshiva said:**
> Yes, I have broadcom drivers installed. However, being a windows user(read refugee), I had to install a separate bluetooth drivers to get in running(apart from WiFi drivers). Do you think that could be the problem. 

As said, the WiFi is working fine, it's just this damn bluetooth.

I'm also enclosing a screenshot of the driver details.
read this thread carefully
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)
see if there's any other broadcom package needed to install, the bluetooth drivers are included in the wireless drivers.
and check if linux-firmware package is installed.

---

### Post by matt_symes on 2011-10-12
Hi
> 
Another thing, even in Windows, I had to install a drivers individually  both for WiFi and bluetooth. However in Ubuntu, I only see WiFi driver.  Could that be a problem too?I am  beginning to think this is a serious driver or kernel issue. It may be a case of trying to track down and compiling a driver or patch. Maybe.....

What's the output of (with bluetooth on)...

```
ls /sys/class/bluetooth
```I expect the above command to say 'No such file or directory'

I have not owned your laptop make and model so i am not sure if i can help here.

Kind regards

---

### Post by amitshiva on 2011-10-12
> **matt_symes said:**
> Hi
I am  beginning to think this is a serious driver or kernel issue. It may be a case of trying to track down and compiling a driver or patch. Maybe.....

What's the output of (with bluetooth on)...

```
ls /sys/class/bluetooth
```I expect the above command to say 'No such file or directory'

I have not owned your laptop make and model so i am not sure if i can help here.

Kind regards

Hello Matt. This is what comes up:


```
amit@amit-Inspiron-1440:~$ ls /sys/class/bluetooth
ls: cannot access /sys/class/bluetooth: No such file or directory
amit@amit-Inspiron-1440:~$
```

That is something which I'm bit skeptical about. I guess I should learn to live without Bluetooth now :D

---

### Post by amitshiva on 2011-10-12
> **gandaran said:**
> read this thread carefully
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)
see if there's any other broadcom package needed to install, the bluetooth drivers are included in the wireless drivers.
and check if linux-firmware package is installed.

Thanks for the input Gandaran. Sorry, but since I'm new to Linux and Ubuntu, I'm unsure how to install the Linux-firmware package. As far as I see, all the broadcom drivers/package seems to be installed, unless there is a hidden settings or something(already done under additional drivers. Please see attached snapshot in the trailing thread)

---

### Post by deepak365 on 2011-10-13
Try this in terminal

" sudo /etc/init.d/bluetooth restart "

I think it will solve your problem.

---

### Post by gandaran on 2011-10-13
> **amitshiva said:**
> Thanks for the input Gandaran. Sorry, but since I'm new to Linux and Ubuntu, I'm unsure how to install the Linux-firmware package. As far as I see, all the broadcom drivers/package seems to be installed, unless there is a hidden settings or something(already done under additional drivers. Please see attached snapshot in the trailing thread)
use synaptic package manager to install and remove applications and check whats installed.
type in the search bar 'bcm' to show which broadcom packages are installed.
you can also use Ubuntu software center and the command line apt-get but synaptic is better to control everything.

---

### Post by amitshiva on 2011-10-13
> **deepak365 said:**
> Try this in terminal

" sudo /etc/init.d/bluetooth restart "

I think it will solve your problem.

That did not work

---

### Post by amitshiva on 2011-10-13
> **gandaran said:**
> use synaptic package manager to install and remove applications and check whats installed.
type in the search bar 'bcm' to show which broadcom packages are installed.
you can also use Ubuntu software center and the command line apt-get but synaptic is better to control everything.

Hello Gandaran,

I found out certain hardware/driver installation in synaptic package manager but unsure what needs to be done. I'm posting a snapshot of the available/mentioned driver/hardware config.

Most of them are unchecked.

Also, out of curiosity, are we close to have 'it' working? :)


Thanks a ton

---

### Post by gandaran on 2011-10-13
> Also, out of curiosity, are we close to have 'it' working?
I don't think so, this bluetooth card looks very difficult, I haven't found one single article on how to make it work only lots of users with the same problem and no fix.
don't go about installing any broadcom package unless it's recommended, you mite mess up the wireless drivers.

---

### Post by amitshiva on 2011-10-13
> **gandaran said:**
> I don't think so, this bluetooth card looks very difficult, I haven't found one single article on how to make it work only lots of users with the same problem and no fix.
don't go about installing any broadcom package unless it's recommended, you mite mess up the wireless drivers.

My bad. Do you think the drivers which were provided for windows could be of any use? Basically what I mean is if we need any additional drivers to install or something?

---

### Post by gandaran on 2011-10-13
> **amitshiva said:**
> My bad. Do you think the drivers which were provided for windows could be of any use? Basically what I mean is if we need any additional drivers to install or something?
no, you cant use the windows drivers (only windows wireless drivers can be made to work on ubuntu using ndiswrapper).
what I have found out is that this issue with this bluetooth driver mostly affects only some Dell laptops and probably the only answer to fix is to remove the buletooth driver in windows then download and install another driver provided by Dell reboot to ubuntu and bluetooth should be working, thats all I could find.

---

### Post by amitshiva on 2011-10-13
> **gandaran said:**
> no, you cant use the windows drivers (only windows wireless drivers can be made to work on ubuntu using ndiswrapper).
what I have found out is that this issue with this bluetooth driver mostly affects only some Dell laptops and probably the only answer to fix is to remove the buletooth driver in windows then download and install another driver provided by Dell reboot to ubuntu and bluetooth should be working, thats all I could find.


Ok, now the question is how do i remove the driver from windows(since i'm not running on dual boot). Only Ubuntu is installed on my laptop?

---

