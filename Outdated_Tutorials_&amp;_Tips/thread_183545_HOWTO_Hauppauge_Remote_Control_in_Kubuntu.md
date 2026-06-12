---
title: "HOWTO: Hauppauge Remote Control in Kubuntu"
date: 2006-05-28
forum: Outdated Tutorials &amp; Tips
---

### Post by jon_benge on 2006-05-28
[RIGHT]**[SIZE="4"]Version 2.2[/SIZE]**[/RIGHT]

This guide is depreciated. Configuring Lirc for Hardy Heron is slightly different than before. New guide coming soon for Kubuntu *and *Ubuntu


Get your Hauppauge remote control working in Ubuntu with Lirc and IRKICK. Based on the Hauppauge Nova-T PCI 909 with the newer remote control. This guide might work with other Hauppauge boards, though this is not confirmed. You may have to find / create different 'hardware.conf' and 'lircd.conf' configuration files.


Okay, let's get to it.. :)


**[SIZE="5"]PART 1: Initial Configuration[/SIZE]**


We need to find out if the standard Kubuntu kernel has detected your remote control. We can check this by typing the following command into a terminal window.

```
cat /proc/bus/input/devices
```

A load of text will appear. Look for something similar to what is shown below:

```
I: Bus=0001 Vendor=0070 Product=9002 Version=0001
**N: Name="cx88 IR (Hauppauge Nova-T DVB-T"**
P: Phys=pci-0000:01:02.0/ir0
S: Sysfs=/class/input/input3
**H: Handlers=kbd event3**
B: EV=100003
B: KEY=100fc312 214a802 0 0 0 0 18000 41a8 4801 9e1680 7bb80 0 10000000
```

There are two important things to look for here. The **'N:Name'** proves the remote control has been detected properly and the **'H:Handlers'** shows us what *'event number'* our remote control is mapped to. As you can see, my Event number is currently '3'.
Unfortunately, these event numbers are dynamically assigned, so your remote control will not always stay at the Event number it's at now. When the event numbers change, the remote control will simply not work, or worse, the mouse and keyboard will lock up. We can solve this problem by manually assigning an *Event ID* to our remote control, so it never changes.

Enter the command below into a terminal and replace 'eventx' with your Event number.

```
udevinfo -a -p $(udevinfo -q path -n /dev/input/**eventx**)
```

The output of that command should be similar to what you see below.

```

device '/sys/class/input/input3/event3' has major:minor 13:67
  looking at class device '/sys/class/input/input3/event3':
    KERNEL=="event3"
    SUBSYSTEM=="input"
    SYSFS{dev}=="13:67"

follow the "device"-link to the physical device:
  looking at the device chain at '/sys/devices/pci0000:00/0000:00:0e.0/0000:02:09.0':
    BUS=="pci"
    ID=="0000:02:09.0"
    **DRIVER=="cx8800"**
    SYSFS{class}=="0x040000"
    SYSFS{device}=="0x8800"
    SYSFS{irq}=="209"
    SYSFS{local_cpus}=="1"
    SYSFS{modalias}=="pci:v000014F1d00008800sv00000070sd00009002bc04sc00i00"
    SYSFS{subsystem_device}=="0x9002"
    SYSFS{subsystem_vendor}=="0x0070"
    **SYSFS{vendor}=="0x14f1"**

  looking at the device chain at '/sys/devices/pci0000:00/0000:00:0e.0':
    BUS=="pci"
    ID=="0000:00:0e.0"
    DRIVER=="unknown"
    SYSFS{class}=="0x060400"
    SYSFS{device}=="0x00ed"
    SYSFS{irq}=="0"
    SYSFS{local_cpus}=="1"
    SYSFS{modalias}=="pci:v000010DEd000000EDsv00000000sd00000000bc06sc04i00"
    SYSFS{subsystem_device}=="0x0000"
    SYSFS{subsystem_vendor}=="0x0000"
    SYSFS{vendor}=="0x10de"

  looking at the device chain at '/sys/devices/pci0000:00':
    BUS==""
    ID=="pci0000:00"
    DRIVER=="unknown"
```


As you can see, I have highlighted the 'Driver' and 'SYSFS(Vender)' entries. The driver entry will reflect the type of card you are using. This will always be the 'cx8800' for the Hauppauge Nova-T cards. 
We will use the 'SYSFS{vendor}' entry to uniquely identify the remote control when we assign a static Event number. Make a note of your 'SYSFS(vender)=ID' because we will use it in the next step. For reference, my SYSFS(vender) is "0x14f1", which will probably be the same for all Nova-T cards.

Now we need to create a rule to map SYSFS(vender) to an Event ID. To do this, enter the command below.

```
sudo nano /etc/udev/rules.d/10-local.rules
```

Copy and paste the following into the new file.

```
KERNEL=="event*",SYSFS{vendor}==**"0x14f1"**,SYMLINK="input/irremote"
```

[COLOR="Red"]IMPORTANT:[/COLOR] Replace "0x14f1" with your own SYSFS(vender), if different.

Press 'CTRL+X', then 'Y', followed by 'Enter' to save and close the file.

Now we need to restart UDEV with the following command.

```
sudo /etc/init.d/udev restart
```

To confirm the configuration is a success, enter the following command.

```
ls -l /dev/input
```

If all has gone well, you should see an output similar to what you see below.

```
total 0
crw-rw---- 1 root root 13,  64 2006-10-02 22:27 event0
crw-rw---- 1 root root 13,  65 2006-10-02 22:27 event1
crw-rw---- 1 root root 13,  66 2006-10-02 22:27 event2
crw-rw---- 1 root root 13,  67 2006-10-02 22:27 event3
crw-rw---- 1 root root 13,  68 2006-10-02 22:27 event4
**lrwxrwxrwx 1 root root       6 2006-10-02 22:27 irremote -> event3**
crw-rw---- 1 root root 13,  63 2006-10-02 22:27 mice
crw-rw---- 1 root root 13,  32 2006-10-02 22:27 mouse0
crw-rw---- 1 root root 13, 128 2006-10-02 22:27 ts0
```



**[SIZE="5"]PART 2: Installing The Lirc Server[/SIZE]**


We need to install *lirc*, the Linux Infra-Red Receiver. Lirc will handle all of the communication between your remote control and your computer

```
sudo aptitude install lirc
```

Time for another little test! You will need to have **two terminals** open at the same time to perform this test. In the first terminal, type what you see below

```
sudo /usr/sbin/lircd -H dev/input -d /dev/input/irremote -n
```

And in the second terminal, type:

```
irw
```

Press some buttons on the remote control and you should see some output in one of the terminals. Once you have done with that, press CTRL+C to finish.



**[SIZE="5"]PART 3: Configuration Files[/SIZE]**


You need to download the zip file attached to this post and extract it to reveal the "lircd.conf" and "hardware.conf" configuration files. You need to move these files to /etc/lirc

```
sudo chown root:root hardware.conf lircd.conf
```
```
sudo mv lircd.conf /etc/lirc
```
```
sudo mv hardware.conf /etc/lirc
```

Finally, activate the Lirc server by typing:

```
sudo /etc/init.d/lirc start
```



**[SIZE="5"]PART 4: Installing The KDE Lirc Front End, IRKICK[/SIZE]**


The next thing we need to do is install the KDE front end for lirc, called IRKICK.

```
sudo aptitude install kdelirc
```

*[COLOR="Red"]NOTE:[/COLOR] For this very reason, this guide is for Kubuntu users only. I am not aware of a GNOME front end for Lirc. But if you know of one, this is when you should install it.*



**[SIZE="5"]PART 5: Key Mapping[/SIZE]**


Go to the *K menu*, point to *Utilities* and click on *KDE Lirc Server (IRKICK)*.

If you don't see it there, you may have to wait a couple of seconds, or reboot your computer.

Look over at your taskbar and you will see a little antenna. If your configuration is a success, the antenna will be surrounded by red radiowaves. 

This icon will light up whenever a button is pressed on the remote control. Press a few buttons now to test it for yourself!

All that is left to do now is to configure the buttons on the remote control to perform a specific action. 
Right click the antenna icon in your taskbar and select *configure*. Click the *add* button on the **right hand side** and a wizard will begin and guide you through the rest!



**[SIZE="5"]PART 6: Starting IRKICK Automatically with KDE[/SIZE]**


This is actually quite simple. Right click the IRKICK icon in the taskbar and choose 'Quit'. A notice pops up asking if you would like IRKICK to start automatically with KDE. Simply click OK. 

Enjoy! :)





***********************************************
[I]**[SIZE="4"]Acknowledgements:[/SIZE]** 
Thanks go out to the author of  [this guide]("http://parker1.co.uk/mythtv_ubuntu2.php"), from which my own guide is based[/I]
Thanks to James Muscatt for helping out at [Hauppauge forums]("http://www.hauppauge.co.uk/board/showthread.php?t=7085").

---

### Post by jon_benge on 2006-06-10
**[COLOR="Red"][SIZE="4"]FIXED IN VERSION 2.0[/SIZE][/COLOR]**

[SIZE="5"]**NOTE**[/SIZE]

Kubuntu has a habit of swapping the input event numbers after every restart. Your Hauppauge remote control might be assigned Event3 at first, but the next time you reboot you might find it at Event2.

If this happens, your mouse or keyboard will lock up and you will have to restart the computer. The only fix for this is not to start IRKICK automatically with KDE. First check what Event number your Hauppauge remote is assigned, and if it's the same as before you can safely start IRKICK.

I have not found a proper fix for this yet.

---

### Post by jon_benge on 2006-07-27
Does anyone know if there is an updated Kaffeine & Amarok extension for IRKICK?

I've found that the current extensions are missing quite a few functions from those apps

---

### Post by hpne on 2006-07-28
Thank you for a great howto! I finally got my Hauppauge hvr 1100 remote working with your help :D  However, I have the same problem as you: usually my mouse freezes when I start irkick. Help needed :confused:

---

### Post by jon_benge on 2006-07-28
> **hpne said:**
> Thank you for a great howto! I finally got my Hauppauge hvr 1100 remote working with your help :D  However, I have the same problem as you: usually my mouse freezes when I start irkick. Help needed :confused:

It could be that your Hauppauge Remote Control Event number has changed.

Check it using the command:

```
cat /proc/bus/input/devices
```

BTW, have you recently plugged in a new Joypad or other input device? Doing so generally upsets the current event number order. For example, my Hauppauge Remote Control is usually assigned Event3. However, when I plug in my Saitek Joypad, my remote control event number becomes 4 - which causes the mouse lockups etc

As I said, I am still looking for a fix to this :(

---

### Post by hpne on 2006-07-29
> **jon_benge said:**
> It could be that your Hauppauge Remote Control Event number has changed.

Check it using the command:

```
cat /proc/bus/input/devices
```

BTW, have you recently plugged in a new Joypad or other input device? Doing so generally upsets the current event number order. For example, my Hauppauge Remote Control is usually assigned Event3. However, when I plug in my Saitek Joypad, my remote control event number becomes 4 - which causes the mouse lockups etc

As I said, I am still looking for a fix to this :(


Nope, I don't have any other input devices plugged in. Also the event number of my remote does not change after restart. It seems that the mouse problem has disappeared (don't know how), but I have another issue: after every reboot my remote dies; there is no signal at all. I have to remove lirc and reinstall it; then it works again. It seems that something is not loading when the system restarts...

---

### Post by jon_benge on 2006-07-29
Have you configured IRKICK to start automatically with KDE? Follow Part 6 of my tutorial again.

If that still doesn't help, you can try restarting Lirc manually by typing:

```
sudo /etc/init.d/lirc start
```

And you can get Lirc to re-read it's configuration files by typing:

```
sudo /etc/init.d/lirc reload
```

Also, if you mouse locks up again in the future, you can stop lirc by typing:

```
sudo /etc/init.d/lirc stop
```

---

### Post by ElrohirMacBeorn on 2006-10-31
> **jon_benge said:**
> 

Kubuntu has a habit of swapping the input event numbers after every restart. Your Hauppauge remote control might be assigned Event3 at first, but the next time you reboot you might find it at Event2.
[...]
I have not found a proper fix for this yet.

First, thanks for the great Howto, finally I got my remote to work. Regarding the swapping of input event numbers, I found a solution which worked for my at once on  [http://parker1.co.uk/mythtv_tips.php](http://parker1.co.uk/mythtv_tips.php)

Elrohir

---

### Post by jon_benge on 2006-10-31
Thanks.

I've added the changes to the guide.

---

### Post by closet geek on 2007-01-06
Just wanted to say thank you, your tutorial helped me get everything up and running smoothly!

cg

---

### Post by seiflotfy on 2007-01-11
hi 
i have a little problem
somehow it doesnt recognize anything from the remote
it works fine under windows but not under ubuntu
can u tell me how u installed the card please :)
i used a selfwritten tutorial at [https://wiki.ubuntu.com/seiflotfy](https://wiki.ubuntu.com/seiflotfy)
i can watch dvb-t now :)

here is my problem

> seif@Snoopy:~$ cat /proc/bus/input/devices
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0 
B: EV=120013
B: KEY=402000000 3802078f840d001 f2ffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1 
B: EV=40001
B: SND=6

I: Bus=0011 Vendor=0002 Product=0006 Version=003e
N: Name="ImExPS/2 Logitech Explorer Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/class/input/input2
H: Handlers=mouse0 event2 ts0 
B: EV=7
B: KEY=1f0000 0 0 0 0
B: REL=103

I: Bus=0018 Vendor=0000 Product=0000 Version=0000
N: Name="Pinnacle PCTV"
P: Phys=i2c-0/0-0071/ir0
S: Sysfs=/class/input/input3
H: Handlers=kbd event3 
B: EV=100003
B: KEY=108fc010 210080200000000 0 48000 2180c0000801 9e168000000000 4ffc



i have no idea why it writes pinnacle
and even if i try to use events 0 -3 and i get nothign form the remote 
please help

---

### Post by jon_benge on 2007-01-24
I didn't need to set up my Hauppauge Nova-T 909 card because Kubuntu configured it automatically. All I needed to do was launch Kaffeine and tune the channels.

---

### Post by xroads42 on 2007-01-29
hi.

i have a problem installing my Haupauge HVR-1300 remote control.
i did the steps described in part 1, but 
udevinfo -a -p $(udevinfo -q path -n /dev/input/event2)
returns:
```
...
 looking at device '/devices/pci0000:00/0000:00:09.0/0000:05:06.1':
    ID=="0000:05:06.1"
    BUS=="pci"
    DRIVER==**"cx88_audio"**
    SYSFS{modalias}=="pci:v000014F1d00008811sv00000070sd00009601bc04sc80i00"
    SYSFS{local_cpus}=="ff"
    SYSFS{irq}=="58"
    SYSFS{class}=="0x048000"
    SYSFS{subsystem_device}=="0x9601"
    SYSFS{subsystem_vendor}=="0x0070"
    SYSFS{device}=="0x8811"
    **SYSFS{vendor}=="0x14f1"**
...

```
as you can see, the entry for DRIVER is not "cx8800".. I continued anyway but
sudo evtest /dev/input/irremote is not reacting on input via my remote control...

Do i need to change the driver?? And how can i do this?

edit:
some other information:
```

jens@jens-desktop:~$ **cat /proc/bus/input/devices**
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0 
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 f2ffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1 
B: EV=40001
B: SND=6

I: Bus=0001 Vendor=0070 Product=9601 Version=0001
N: Name="cx88 IR (Hauppauge WinTV-HVR130"
P: Phys=pci-0000:05:06.1/ir0
S: Sysfs=/class/input/input2
H: Handlers=kbd event2 
B: EV=100003
B: KEY=100fc312 214a802 0 0 0 0 18000 41a8 4801 9e1680 0 0 10000ffc

I: Bus=0003 Vendor=046d Product=c03d Version=2000
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:02.0-4/input0
S: Sysfs=/class/input/input3
H: Handlers=mouse0 event3 ts0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103
```
```
**ls -l /dev/input**
insgesamt 0
drwxr-xr-x 2 root root      80 2007-01-29 17:15 by-id
drwxr-xr-x 2 root root     140 2007-01-29 17:15 by-path
crw-rw---- 1 root root 13,  64 2007-01-29 17:08 event0
crw-rw---- 1 root root 13,  65 2007-01-29 17:08 event1
crw-rw---- 1 root root 13,  66 2007-01-29 17:08 event2
crw-rw---- 1 root root 13,  67 2007-01-29 17:08 event3
lrwxrwxrwx 1 root root       6 2007-01-29 17:15 irremote -> event2
crw-rw---- 1 root root 13,  63 2007-01-29 18:08 mice
crw-rw---- 1 root root 13,  32 2007-01-29 17:08 mouse0
crw-rw---- 1 root root 13, 128 2007-01-29 17:08 ts0




```

---

### Post by jon_benge on 2007-01-30
Yeah, CX88_audio looks like it's refering to the audio device of the Hauppauge card.

Evtest doesn't work for me either, that's why I removed that particular test from this guide. You should check the functionality of the remote by issuing:

```
sudo /usr/sbin/lircd -H dev/input -d /dev/input/irremote -n
```

And type...

```
irw
``` 

...in another terminal

Failing that...

Well it seems the remote control has been mapped to Event 2 correctly so instead of using 'irremote' you could use the raw 'event2' instead. You may be interested at looking at my old guide, as it uses the raw event numbers instead. See [here]("http://www.hauppauge.co.uk/board/showthread.php?t=8336"). Be aware though that using my old method can cause problems because the event numbers are not always static. So on occasion you may find your remote control mapped to Event 3 or 4. When that happens, your remote control won't work and your keyboard and / or mouse will lock up. You will have to reboot if that happens

---

### Post by xroads42 on 2007-01-30
i tried that with 
sudo /usr/sbin/lircd -H dev/input -d /dev/input/irremote -n
and with the correct eventx form /proc/bus/input/devices .. and then irw in an other terminal...

but still no reaction on input. I guess there must be something else wrong...
here is the output from sudo /usr/sbin/lircd -H dev/input -d /dev/input/irremote -n
```

lircd-0.8.0[5436]: lircd(userspace) ready
lircd-0.8.0[5436]: accepted new client on /dev/lircd //comment: i started irw here
lircd-0.8.0[5436]: initializing '/dev/input/irremote'
lircd-0.8.0[5436]: removed client                         //comment: i closed irw here
lircd-0.8.0[5436]: closing '/dev/input/irremote'

```

At least a smal success: i did an update yesterday and now udevinfo says cx8800 for driver.. 
```

 looking at device '/class/input/input3/event3':
    KERNEL=="event3"
    SUBSYSTEM=="input"
    SYSFS{dev}=="13:67"

  looking at device '/class/input/input3':
    ID=="input3"
    BUS=="input"
    DRIVER==""
    SYSFS{uniq}==""
    SYSFS{phys}=="pci-0000:05:06.0/ir0"
    SYSFS{name}=="cx88 IR _Hauppauge WinTV-HVR130"

  looking at device '/devices/pci0000:00/0000:00:09.0/0000:05:06.0':
    ID=="0000:05:06.0"
    BUS=="pci"
    DRIVER=="cx8800"
    SYSFS{modalias}=="pci:v000014F1d00008800sv00000070sd00009601bc04sc00i00"
    SYSFS{local_cpus}=="ff"
    SYSFS{irq}=="58"
    SYSFS{class}=="0x040000"
    SYSFS{subsystem_device}=="0x9601"
    SYSFS{subsystem_vendor}=="0x0070"
    SYSFS{device}=="0x8800"
    SYSFS{vendor}=="0x14f1"

  looking at device '/devices/pci0000:00/0000:00:09.0':
    ID=="0000:00:09.0"
    BUS=="pci"
    DRIVER==""
    SYSFS{modalias}=="pci:v000010DEd0000005Csv00000000sd00000000bc06sc04i01"
    SYSFS{local_cpus}=="ff"
    SYSFS{irq}=="0"
    SYSFS{class}=="0x060401"
    SYSFS{subsystem_device}=="0x0000"
    SYSFS{subsystem_vendor}=="0x0000"
    SYSFS{device}=="0x005c"
    SYSFS{vendor}=="0x10de"

  looking at device '/devices/pci0000:00':
    ID=="pci0000:00"
    BUS==""
    DRIVER==""

```

---

### Post by kenmiles on 2007-02-01
I have set up my remote as in the instructions and all buttons work except the number buttons, there is no output indicated on the irkick icon when they are pressed. It is not the remote because if I close irkick they work ok but no other buttons do.
I am running Ubuntu 6.10 and Kaffeine 0.8.2 and KDE 3.5.5.
Any idea's please.

Thanks in advance, Kenneth.

---

### Post by jon_benge on 2007-02-03
> **kenmiles said:**
> I have set up my remote as in the instructions and all buttons work except the number buttons

I had the same problem as you, but I never got around to fixing it because I decided to move back to Dapper Drake :) What ever the problem is, it's specific to Edgy Eft. I'll look into it and see what I can find.

---

### Post by kenmiles on 2007-02-03
> **jon_benge said:**
> I had the same problem as you, but I never got around to fixing it because I decided to move back to Dapper Drake :) What ever the problem is, it's specific to Edgy Eft. I'll look into it and see what I can find.

Thanks for that, I hope you can find an answer to it as it's got me beat.
Regards, Kenneth.
[http://kmiles.co.uk](http://kmiles.co.uk)

---

### Post by jon_benge on 2007-02-05
I've done some searching around the internet and it appears as if the Lirc that ships with Edgy is broken. Now I may be wrong on this; something else may be the cause.

I am going to up-port the Dapper Drake version of Lirc to Edgy. I will also backport the Fiesty version. I will upload both debian packages, built specifically for Edgy, tomorrow. Would you mine testing them out for me?

---

### Post by kenmiles on 2007-02-06
> **jon_benge said:**
> I've done some searching around the internet and it appears as if the Lirc that ships with Edgy is broken. Now I may be wrong on this; something else may be the cause.

I am going to up-port the Dapper Drake version of Lirc to Edgy. I will also backport the Fiesty version. I will upload both debian packages, built specifically for Edgy, tomorrow. Would you mine testing them out for me?

I will test them for you with pleasure if you let me know how I can get the files, I am new to linux after spending years on windows.
Regards, kenneth.

---

### Post by jon_benge on 2007-02-06
Right, try this package:

[http://www.zshare.net/download/lirc_0-8-0-9ubuntu16-10_i386-deb.html](http://www.zshare.net/download/lirc_0-8-0-9ubuntu16-10_i386-deb.html)

---

### Post by kenmiles on 2007-02-06
> **jon_benge said:**
> Right, try this package:

[http://www.zshare.net/download/lirc_0-8-0-9ubuntu16-10_i386-deb.html](http://www.zshare.net/download/lirc_0-8-0-9ubuntu16-10_i386-deb.html)

Everthing works but the number buttons, so no difference.

Regards, Kenneth.

---

### Post by jon_benge on 2007-02-06
So we can conclude that the problem lies elsewhere. I'll keep searching around the internet and see what I can dig up. Also let me know if you find anything

---

### Post by kenmiles on 2007-02-07
> **jon_benge said:**
> So we can conclude that the problem lies elsewhere. I'll keep searching around the internet and see what I can dig up. Also let me know if you find anything

I don't know if this will help but when I start IRKICK I get the following message:

"X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device"

even though IRKICK starts ok.

Regards, Kenneth.

PS. When I type this command in one terminal "sudo /usr/sbin/lircd -H dev/input -d /dev/input/irremote -n" and "irw" in another all buttons work except the number ones so it points to a bug in lirc somewere.

---

### Post by cebe11 on 2007-08-12
kenmiles:  Did you ever find a solution to this?  I'm having exactly this problem with the same remote on Ubuntu Edgy.
thanks

---

### Post by jon_benge on 2007-09-09
The problem is due to the lircd.conf file containing incorrect settings for the number buttons. I have now attached a zip file to the first post containing an updated lircd.conf file. Simply replace your old one with this and it should work perfectly!

---

### Post by ptitmain on 2007-10-14
Thanks a lot for this great howto. It's the first time I am able to completely configure my remote with amarok+kaffeine.

I configured all that in irkick: I attached to this post my irkickrc if it could help someone. This file is to be put in:

~/.kde/share/config

Rename the file irkickrc.txt into irkickrc. Then relaunch your irkick and you will have my config for amarok and kaffeine.

Just a final remark: in the files you provided (hardware.conf and lircd.conf) I modified the input device directly (it's more simple I think). For me, my remote is on event4, so I put in hardware.conf:

DEVICE="/dev/input/event4"

Regards,
Ptitmain.

---

