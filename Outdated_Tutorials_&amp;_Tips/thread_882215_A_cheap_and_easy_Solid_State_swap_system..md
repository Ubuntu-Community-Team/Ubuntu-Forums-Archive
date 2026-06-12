---
title: "A cheap and easy Solid State swap system."
date: 2008-08-06
forum: Outdated Tutorials &amp; Tips
---

### Post by Kernel_Krunch on 2008-08-06
[FONT="Microsoft Sans Serif"]

This is part 1 of 2 and is designed as a quick quide on device formating and partitioning.  If you already know this, and how to find the serial number, then please proceed to [COLOR="blue"]_part 2_[/COLOR]

[COLOR="Red"]**_Hardware Requirements_**[/COLOR]
A) Minimum 4 USB2.0 memory storage devices.  Identical make and model of at lest 512MB in size preferred. Maximum 32(untested).
B) A motherboard with USB2.0 ports properly configured in BIOS.

[COLOR="Blue"]**_Procedure_**[/COLOR]
1.) Open a text file with gedit for recording device information.

2.) Open a Terminal(Applications->Accessories->Terminal) and enter
```
tail -f /var/log/messages
```

3.) Now insert the usb device and you should see something like the following
> Aug  6 11:53:37  kernel: [ 2059.400832] scsi9 : SCSI emulation for USB Mass Storage devices
Aug  6 11:53:42  kernel: [ 2064.404667] scsi 9:0:0:0: Direct-Access     Kingston DataTraveler 2.0 PMAP PQ: 0 ANSI: 0 CCS
Aug  6 11:53:43  kernel: [ 2064.973349] sd 9:0:0:0: [sde] 1953792 512-byte hardware sectors (1000 MB)
Aug  6 11:53:43  kernel: [ 2064.973970] sd 9:0:0:0: [sde] Write Protect is off
Aug  6 11:53:43  kernel: [ 2064.976592] sd 9:0:0:0: [sde] 1953792 512-byte hardware sectors (1000 MB)
Aug  6 11:53:43  kernel: [ 2064.977218] sd 9:0:0:0: [sde] Write Protect is off
Aug  6 11:53:43  kernel: [ 2064.977226]  sde: sde1
Aug  6 11:53:43  kernel: [ 2064.978024] sd 9:0:0:0: [sde] Attached SCSI removable disk
Aug  6 11:53:43  kernel: [ 2064.978060] sd 9:0:0:0: Attached scsi generic sg5 type 0

*Here we see my device has been named sde, yours will probably be different (i.e. sda or sdc).*

4.) Record the device name.

5.) *(If you have a brand new device, never used, then you can skip this step)* An icon should have appeared on your desktop pointing to your newly inserted usb device.  Open the icon, check for data files and **_back them up_** because they are going to be erased of all data.

6.) Right click the desktop icon pointing to your device and choose 'unmount volume'.

7.) Open another Terminal and type
```
udevinfo -a -p `udevinfo -q path -n /dev/xxx`
```
Change the xxx to the device name you recorded.  Find the section that looks something like this:
>   looking at parent device '/devices/pci0000:00/0000:00:10.4/usb5/5-6':
    KERNELS=="5-6"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{dev}=="189:519"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="80"
    ATTRS{bMaxPower}=="200mA"
    ATTRS{urbnum}=="2225"
    ATTRS{idVendor}=="0951"
    ATTRS{idProduct}=="1608"
    ATTRS{bcdDevice}=="0100"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="480"
    ATTRS{busnum}=="5"
    ATTRS{devnum}=="8"
    ATTRS{version}==" 2.00"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Kingston"
    ATTRS{product}=="DataTraveler 2.0"
    ATTRS{serial}=="5B790F860008"
and record the serial number (i.e. mine is 5B790F860008 ).

8.) Now to make the device a swap device. Enter the command ```
sudo parted /dev/xxx
```
To make things easier I will paste my console and you can mimic the answers replacing values where needed.  
[I][B]notes: The End value comes from this line "Disk /dev/sde: 1000MB" and might be different for your device, depending on its size.
Watch out for hotplug, it might mount your drive while your working on the device; be sure to umount it before making a change in parted.[/B][/I]
[INDENT]```
tommy@thepark:~$ sudo parted /dev/sde
GNU Parted 1.7.1
Using /dev/sde
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            

Disk /dev/sde: 1000MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size   Type      File system  Flags
 1      0.51kB  500MB   500MB  primary   ext2              
 2      500MB   1000MB  500MB  extended               lba  

(parted) rm 2                                                             
(parted) rm 1                                                             
(parted) print                                                            

Disk /dev/sde: 1000MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End  Size  Type  File system  Flags

(parted) mkpartfs
Partition type?  primary/extended? primary                                
File system type?  [ext2]? linux-swap                                     
Start? 0                                                                  
End? 1000MB                                                               
(parted) print                                                            

Disk /dev/sde: 1000MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      0.51kB  1000MB  1000MB  primary  linux-swap        

(parted) quit                                                             
tommy@thepark:~$ 

```[/INDENT]
9.) Repeat for each device.

Now proceed to [COLOR]_part 2_[/COLOR]
[/FONT]

---

