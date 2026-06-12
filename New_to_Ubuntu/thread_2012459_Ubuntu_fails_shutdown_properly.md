---
title: "Ubuntu fails shutdown properly"
date: 2012-06-29
forum: New to Ubuntu
---

### Post by mijonuha on 2012-06-29
Hi
I am Using Ubuntu 12.04 LTS precise. When I restart or hibernate, it is ok. But when I shut it down, it get stuck on this page:

[IMG]http://i.minus.com/jxHuClYPRIVYG.jpg[/IMG]

and it stops. there are 2 or 3 days i have found such problem.
I don't know what to do, and where to check. please help

---

### Post by Gone fishing on 2012-06-29
If you click Esc before it freezes you will be able to see the console messages and what it is freezing on. I would guess unmounting something but that's a guess.

---

### Post by mijonuha on 2012-07-06
This is what I see:

[IMG]http://i.minus.com/iIbXm5sGQuaGz.jpg[/IMG]

side-by-side to this screenshot:
[IMG]http://i.minus.com/i0LuhnmOylh7u.jpg[/IMG]


BTW, My startup is also abnormal. It takes a long time to boot up. What do you think is wrong?
When It wants to startup for around 20 sec it shows only purple screen before ubuntu logo appears and during that time even by pressing Escape I don't see the happening events.
Here is bootchart of my last startup:
[http://i.minus.com/iju782fxXYOkQ.png](http://i.minus.com/iju782fxXYOkQ.png)

also, after hibernates usually it works ok but the next time I restart it takes 20 sec before showing ubuntu logo and during this time it only shows:
kernel_thread_helper+0x6 0x10

It looks like a spooky computer. So any help is so appreciated.
If you have any idea, please do not hesitate to post.

thanks very much

---

### Post by Gone fishing on 2012-07-06
I think it maybe a USB device is having a problem - can you try starting up and shutting down after removing the USB devices in  turn?

---

### Post by mijonuha on 2012-07-06
> **Gone fishing said:**
> I think it maybe a USB device is having a problem - can you try starting up and shutting down after removing the USB devices in  turn?

Dear bro, I have no idea about how to remove USB. Do you mean USB attached wire or USB driver related to OS? this is my fstab:
what should I do next?

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda5 :
UUID=9e7dcb6d-8616-4768-8e01-6ad13665002c    /    ext4    errors=remount-ro    0    1
#Entry for /dev/sda1 :
UUID=5A04B61004B5EF5F    /media/5A04B61004B5EF5F    ntfs    defaults,users,guest,uid=1000,gid=1000,locale=en_US.utf8    0    0
#Entry for /dev/sda2 :
UUID=547A5A737A5A51BA    /media/Document    ntfs    defaults,users,guest,uid=1000,gid=1000,exec,locale=en_US.utf8    0    0
#Entry for /dev/sda3 :
UUID=00826E68826E6260    /media/Media    ntfs    defaults,users,guest,uid=1000,gid=1000,exec,locale=en_US.utf8    0    0
#Entry for /dev/sda6 :
UUID=18898708-d622-4e51-ad87-8aeb3cee6040    none    swap    sw    0    0
#none    /proc/bus/usb    usbfs    devgid=128,devmode=664    0    0

#none    /proc/bus/usb    usbfs    devgid=126,devmode=664    0    0

```

---

### Post by krustenBrot on 2012-07-06
I reckon he means every USB Device physically plugged into your computer. :)

edit: everything that got a connector like this one:
 [IMG]https://encrypted-tbn2.google.com/images?q=tbn:ANd9GcQ__Y_hpKC2-3TSOS5DjnkWALOFwHMgOe0WNB8XUcQ6goPPpmmtVA[/IMG]

---

### Post by mijonuha on 2012-07-06
I have detached all USB wires(including my mouse USB) and restarted the computer and here is the bootchart:
[http://i.minus.com/iPTtfcO06j1OK.png](http://i.minus.com/iPTtfcO06j1OK.png)

for shutdown the problem happens randomly. so I cannot give you new screen shot for shut down.

---

### Post by Gone fishing on 2012-07-06
Sorry not conclusive ;)

Try looking in these to files for errors /var/log/boot.log and /var/log/dmesg 

```
gedit /var/log/boot.log
``` and ```
gedit /var/log/dmesg
``` post back any errors you find

---

### Post by mijonuha on 2012-07-06
> **Gone fishing said:**
> Sorry not conclusive ;)

Try looking in these to files for errors /var/log/boot.log and /var/log/dmesg 

```
gedit /var/log/boot.log
``` and ```
gedit /var/log/dmesg
``` post back any errors you find

Files are attached.
inside the boot.log there are some invalid characters.

---

### Post by codingman on 2012-07-06
@OP
I can't see your image. Please fix this! That would be helpful. 

Also, did you shutdown from terminal? If so...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1007112](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1007112)

---

### Post by NikTh on 2012-07-06
For the delay of boot i think all those /media NTFS and more... partitions that you had include in you fstab are responsible. 
When system has too many partitions to mount during boot , its normal to delayed. 

For the shutdown problem , i am not sure , but try to add this parameter in grub. 
```
gksudo gedit /etc/default/grub
``` 
find this line : **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"**   
and make it exactly like this : **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force**" 

Then run in terminal 
```
sudo update-grub
``` 
reboot and check if shutdown works .

---

### Post by mijonuha on 2012-07-06
> **codingman said:**
> @OP
I can't see your image. Please fix this! That would be helpful. 

Also, did you shutdown from terminal? If so...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1007112](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1007112)

I shut down normally, only hibernates are done from terminal.
Which link is corrupted? they look OK. give me the link to fix

---

### Post by harisund on 2012-07-06
Can you try "sudo poweroff" from the command line and see if it shuts down correctly?

---

### Post by codingman on 2012-07-06
> **mijonuha said:**
> I shut down normally, only hibernates are done from terminal.
Which link is corrupted? they look OK. give me the link to fix

They are fixed now. 

Hmm... same problem here in Quantal 12.10 when shutting down from the terminal.

---

### Post by mijonuha on 2012-07-06
> **NikTh said:**
> For the delay of boot i think all those /media NTFS and more... partitions that you had include in you fstab are responsible. 
When system has too many partitions to mount during boot , its normal to delayed. 

For the shutdown problem , i am not sure , but try to add this parameter in grub. 
```
gksudo gedit /etc/default/grub
```find this line : **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"**   
and make it exactly like this : **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force**" 

Then run in terminal 
```
sudo update-grub
```reboot and check if shutdown works .

i removed media partitions from fstab. the reduced time is not that much considerable but the chart looks a little bit different:
[http://i.minus.com/iTmD9Vxd3o3Nu.png](http://i.minus.com/iTmD9Vxd3o3Nu.png)

**acpi** is already set on **force**

Just now i faced the bad shut down again, I had done nothing except for checking ubuntuforum on browser and changing fstab(removing media partition)

bootlog and dmesg are attached.
now i am thinking about reinstallation of ubuntu. i have nothing to lose.

---

### Post by Gone fishing on 2012-07-07
Just looking at your dmesg and I noticed 

> [    7.821385] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   39.049118] ADDRCONF(NETDEV_UP): eth0: link is not ready

It seems that attempting to load the Ethernet card is taking 31 seconds. Are you using this card? can you remove, disable or change it? Mine is taking a lot less.

---

### Post by mijonuha on 2012-07-07
> **Gone fishing said:**
> Just looking at your dmesg and I noticed 



It seems that attempting to load the Ethernet card is taking 31 seconds. Are you using this card? can you remove, disable or change it? Mine is taking a lot less.

i checked the /etc/network/interfaces:
```
auto lo
iface lo inet loopback
```and this is the result of ifconfig:
```
eth0      Link encap:Ethernet  HWaddr a4:bd:b6:da:e8:4c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:46 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:23671 errors:0 dropped:0 overruns:0 frame:0
          TX packets:23671 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4111065 (4.1 MB)  TX bytes:4111065 (4.1 MB)

wlan0     Link encap:Ethernet  HWaddr 78:e3:10:e0:85:04  
          inet addr:192.168.5.103  Bcast:192.168.5.255  Mask:255.255.255.0
          inet6 addr: fe80::7be4:ff:fe03:4204/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:602522 errors:0 dropped:0 overruns:0 frame:0
          TX packets:513578 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:753055179 (753.0 MB)  TX bytes:69924800 (69.9 MB)

```

how should I remove eth0 ?

---

### Post by NikTh on 2012-07-07
> **mijonuha said:**
> 
Just now i faced the bad shut down** again**, I had done nothing except for checking ubuntuforum on browser and changing fstab(removing media partition).

What do you mean by **again** ? The shutdown problem was solved , but when you removed the fstab entries its here again ? 

Maybe the shutdown problem is relatively to this :  [http://ubuntuforums.org/showthread.php?t=1968376](http://ubuntuforums.org/showthread.php?t=1968376)
Try to remove (if you have) restricted (additional) driver for graphics card and see if fixed.

---

### Post by mijonuha on 2012-07-07
> **NikTh said:**
> What do you mean by **again** ? The shutdown problem was solved , but when you removed the fstab entries its here again ? 

Maybe the shutdown problem is relatively to this :  [http://ubuntuforums.org/showthread.php?t=1968376](http://ubuntuforums.org/showthread.php?t=1968376)
Try to remove (if you have) restricted (additional) driver for graphics card and see if fixed.

shutdown hanging problem happens randomly maybe in every 4 shutdowns once. after changing fstab it happened again. unfortunately I dont know what exexactly results to shutdown in some cases.
i dont have any additional graphic drive.

:confused:   :(   :confused:

---

### Post by NikTh on 2012-07-07
> **mijonuha said:**
> 
i dont have any additional graphic card.

:confused:   :(   :confused:

Driver i mean. Not graphics card as hardware.. 
give the result of this command 
```
lspci -nnk | grep -iA2 vga
```

---

### Post by mijonuha on 2012-07-07
> **NikTh said:**
> Driver i mean. Not graphics card as hardware.. 
give the result of this command 
```
lspci -nnk | grep -iA2 vga
```

```

aran@AR-PC:~$ lspci -nnk | grep -iA2 vga
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Manhattan [Mobility Radeon HD 5400 Series] [1002:68e0]
    Subsystem: Dell Device [1028:0447]
    Kernel driver in use: fglrx_pci

```

[IMG]http://i.minus.com/jiuyX0uK0hS7M.jpg[/IMG]

Sorry for typing wrong. I meant 'graphic drive' but wrote 'graphic card'

---

### Post by Gone fishing on 2012-07-07
What is the box laptop - desktop? I was thinking if you are not using the ethernet either removing it physically or disabling in BIOS. Otherwise unticking connect automatic in network manager.

I can't see any errors in dmesg but this card does seem to be taking a long time.

---

### Post by NikTh on 2012-07-07
See here for the shutdown problem. --> [http://askubuntu.com/questions/132143/stuck-on-reboot-and-shutdown](http://askubuntu.com/questions/132143/stuck-on-reboot-and-shutdown) . 
_**I don't know**_ what **acpi=noirq **parameter doing.. but you can try it.


You can also try to deactivate (purge) the proprietary driver fglrx fot ATI . If you have any problems with graphics e.g poor performance or lag ...etc then you can activate the driver again.
It is not necessary to activate the additional (proprietary) driver IF the open source (radeon) works for you.

---

### Post by mijonuha on 2012-07-08
thanks friends but it's over
I finally reinstalled the Ubuntu.
next time i will install unnecessary applications on virtual machine to keep my main os safe.
till now everything is normal

---

