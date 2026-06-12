---
title: "Trying to install Ubuntu on older Win10  for dual boot or seperate install."
date: 2024-11-08
forum: New to Ubuntu
---

### Post by shaussie on 2024-11-08
This is a very basic question:  I am trying to download and install Ubuntu 22.04 on an older model Lenovo M71e desktop, Win 10 Pro (Build 17134).  I realize that this Build is earlier than the Build 19041 required.  One solution which comes to mind is to try and D/L an earlier version of Ubuntu which does not have this later Build requirement.

Please suggest some fool-proof method to get **ANY** copy of Ubuntu installed and running on my PC.  I have tried Rufus and 128Gb pen drive but the system does not read the .iso file from the drive.  

Dual boot or separate install, whichever is easier at this early stage.

Many Thanks.

---

### Post by ajgreeny on 2024-11-08
Tell us more about that hardware than just the model number.
What CPU, how much  RAM, what graphics card, if any, and is it a UEFI system?
If the machine had Windows 10 when purchased new it will certainly be UEFI as that was mandated by Microsoft for any preinstalled Win10 computers.

---

### Post by grahammechanical on 2024-11-08
> I realize that this Build is earlier than the Build 19041 required.  One  solution which comes to mind is to try and D/L an earlier version of  Ubuntu which does not have this later Build requirement.

I do not understand what that sentence means. Installing Ubuntu does not require a certain build of Windows. I am guessing that you are wanting to use Windows Subsystem for Linux (WSL). The requirement to use a certain build of Windows or greater is a Microsoft requirement. Not a Ubuntu requirement.

You should also know that older versions of Ubuntu are no longer supported. When support ends the ubuntu version does not get any more security fixes. What would be the point of installing and older version of Ubuntu? Perhaps you want to experience upgrading from one version of Ubuntu to a newer version. I had the urge to do that once. It was fun but a waste of time and effort ultimately.

> You must be running Windows 10 version 2004 and higher (Build 19041 and  higher) or Windows 11 to use the commands below. If you are on earlier  versions please see [the manual install page]("https://learn.microsoft.com/en-us/windows/wsl/install-manual").

[https://learn.microsoft.com/en-us/windows/wsl/install](https://learn.microsoft.com/en-us/windows/wsl/install)

I think you will find that the installation of Ubuntu in WSL is controlled by Microsoft. I doubt if you will be able to select another version of Ubuntu than the one that is automatically installed.

Regards.

---

### Post by yancek on 2024-11-08
I didn't understand the reference to Windows Builds but I guess it might relate to WSL.  The link below to the Ubuntu documentation discusses using it and installing Ubuntu.  I don't see anything there indicating you would use rufus or an iso written to a usb but I've never used WSL.  

[https://documentation.ubuntu.com/wsl/en/latest/guides/install-ubuntu-wsl2/](https://documentation.ubuntu.com/wsl/en/latest/guides/install-ubuntu-wsl2/)

You might clarify if this is what you are attempting to do or if you want to actually do an install of Ubuntu to the hard drive.  I expect the WSL which is a type of virtualization would be slower.

---

### Post by oldfred on 2024-11-08
Full dual boot or overwrite of entire drive erasing Windows.
Be sure to boot in UEFI boot mode.

Also link on how to create a  bootable DVD or USB flash drive, using Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

If hardware is older, then a lightweight flavor may be better. Full Ubuntu works better on newer systems, typically those that can run Windows 11.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)

---

### Post by shaussie on 2024-11-09
Many thanks ajgreeny,  grahammechanical, yancek, oldfred, for your help and advise.

What am I trying to do:  

1.  Ultimately, to get Sagemath installed on my very dated PCs to relearn some mathematics.
2.  To install Sagemath on the dated PCs does not work with WSL due to Window Build issues.
3.  I have tried dual-boot which also does not work.
4.  I am trying to go for a simple lightweight Ubuntu download in a 60Gb partition, so I can get familiar with
     Linux commands and reading files in a Win10 file structure (if this is possible).  This is the objective
     at this time.  Meanwhile Sagemath I can access through CoCalc online / cloud.
5.   I am a retired engineer based in Sydney.  My competence in software is not high.  I sincerely thank you
     for your help.  I will follow up your ideas and suggestions.
6.  System information is as follows:

OS Name    Microsoft Windows 10 Pro
Version    10.0.17134 Build 17134
Other OS Description     Not Available
OS Manufacturer    Microsoft Corporation
System Name    EMAAD
System Manufacturer    LENOVO
System Model    3132A7M
System Type    x64-based PC
System SKU    To be filled by O.E.M.
Processor    Intel(R) Core(TM) i3-2100 CPU @ 3.10GHz, 3100 Mhz, 2 Core(s), 4 Logical Processor(s)
BIOS Version/Date    LENOVO 9QKT23AUS, 07-Jun-11
SMBIOS Version    2.6
Embedded Controller Version    255.255
BIOS Mode    Legacy
BaseBoard Manufacturer    LENOVO
BaseBoard Model    Not Available
BaseBoard Name    Base Board
Platform Role    Desktop
Secure Boot State    Unsupported
PCR7 Configuration    Binding Not Possible
Windows Directory    C:\WINDOWS
System Directory    C:\WINDOWS\system32
Boot Device    \Device\HarddiskVolume1
Locale    United States
Hardware Abstraction Layer    Version = "10.0.17134.619"
User Name    EMAAD\freshcare01
Time Zone    AUS Eastern Daylight Time
Installed Physical Memory (RAM)    8.00 GB
Total Physical Memory    7.85 GB
Available Physical Memory    4.46 GB
Total Virtual Memory    15.9 GB
Available Virtual Memory    12.2 GB
Page File Space    8.00 GB
Page File    C:\pagefile.sys
Kernel DMA Protection    Off
Virtualization-based security    Not enabled
Device Encryption Support    Reasons for failed automatic device encryption: TPM is not usable, PCR7 binding is not supported, Hardware Security Test Interface failed and device is not InstantGo, Un-allowed DMA capable bus/device(s) detected, Disabled by policy, TPM is not usable
Hyper-V - VM Monitor Mode Extensions    Yes
Hyper-V - Second Level Address Translation Extensions    Yes
Hyper-V - Virtualization Enabled in Firmware    No
Hyper-V - Data Execution Protection    Yes

... Have a good weekend, Shaussie.

---

### Post by joepesci2 on 2024-11-09
> **shaussie said:**
> Many thanks ajgreeny,  grahammechanical, yancek, oldfred, for your help and advise.

What am I trying to do:  

1.  Ultimately, to get Sagemath installed on my very dated PCs to relearn some mathematics.
2.  To install Sagemath on the dated PCs does not work with WSL due to Window Build issues.
3.  I have tried dual-boot which also does not work.
4.  I am trying to go for a simple lightweight Ubuntu download in a 60Gb partition, so I can get familiar with
     Linux commands and reading files in a Win10 file structure (if this is possible).  This is the objective
     at this time.  Meanwhile Sagemath I can access through CoCalc online / cloud.
5.   I am a retired engineer based in Sydney.  My competence in software is not high.  I sincerely thank you
     for your help.  I will follow up your ideas and suggestions.
6.  System information is as follows:

OS Name    Microsoft Windows 10 Pro
Version    10.0.17134 Build 17134
Other OS Description     Not Available
OS Manufacturer    Microsoft Corporation
System Name    EMAAD
System Manufacturer    LENOVO
System Model    3132A7M
System Type    x64-based PC
System SKU    To be filled by O.E.M.
Processor    Intel(R) Core(TM) i3-2100 CPU @ 3.10GHz, 3100 Mhz, 2 Core(s), 4 Logical Processor(s)
BIOS Version/Date    LENOVO 9QKT23AUS, 07-Jun-11
SMBIOS Version    2.6
Embedded Controller Version    255.255
BIOS Mode    Legacy
BaseBoard Manufacturer    LENOVO
BaseBoard Model    Not Available
BaseBoard Name    Base Board
Platform Role    Desktop
Secure Boot State    Unsupported
PCR7 Configuration    Binding Not Possible
Windows Directory    C:\WINDOWS
System Directory    C:\WINDOWS\system32
Boot Device    \Device\HarddiskVolume1
Locale    United States
Hardware Abstraction Layer    Version = "10.0.17134.619"
User Name    EMAAD\freshcare01
Time Zone    AUS Eastern Daylight Time
Installed Physical Memory (RAM)    8.00 GB
Total Physical Memory    7.85 GB
Available Physical Memory    4.46 GB
Total Virtual Memory    15.9 GB
Available Virtual Memory    12.2 GB
Page File Space    8.00 GB
Page File    C:\pagefile.sys
Kernel DMA Protection    Off
Virtualization-based security    Not enabled
Device Encryption Support    Reasons for failed automatic device encryption: TPM is not usable, PCR7 binding is not supported, Hardware Security Test Interface failed and device is not InstantGo, Un-allowed DMA capable bus/device(s) detected, Disabled by policy, TPM is not usable
Hyper-V - VM Monitor Mode Extensions    Yes
Hyper-V - Second Level Address Translation Extensions    Yes
Hyper-V - Virtualization Enabled in Firmware    No
Hyper-V - Data Execution Protection    Yes

... Have a good weekend, Shaussie.


Hi Shaussie! if you want to try Ubuntu/Linux, have you considered virtualization? That way you can install the OS in a virtual machine without having to worry about anything else.
I dont know if you have this option.

I know this isnt your original question in the thread, but i wanted to provide a possible alternative.
Regards.

---

### Post by grahammechanical on 2024-11-09
As I see things these are your options:

1) Upgrade Windows 10 to build 19041 or greater.
2) install a Windows program that you can learn mathematics with.
3) Buy a book on mathematics and run the exercises in existing Windows programs/applications already installed. Such as the word processor and spreadsheet.
4) Install the Windows version of LibreOffice. You can run equations in Writer & Calc. It comes with a Maths module.

[https://www.libreoffice.org/](https://www.libreoffice.org/)

[https://www.libreoffice.org/download/download-libreoffice/?type=win-x86_64&version=24.8.2&lang=en-GB](https://www.libreoffice.org/download/download-libreoffice/?type=win-x86_64&version=24.8.2&lang=en-GB)[URL="https://www.libreoffice.org/download/download-libreoffice/?type=win-x86_64&version=24.8.2&lang=en-GB"]
[/URL]
5) Dual boot with Linux

> I have tried Rufus and 128Gb pen drive but the system does not read the .iso file from the drive.

Open another question on this forum to deal with this problem. You describe your hardware as old. But it is not that old as to be obsolete. Your CPU is the most powerful of Intel's dual core CPUs of that time. You have 8GB RAM. Which is more than enough. You do not tell us what video adapter you have. How much dedicated video memory does it have? Ubuntu with the Gnome desktop environment may be too resource hungry for your machine. Look at Xubuntu or Lubuntu. Or Edubuntu. It might suite your needs.

[https://ubuntu.com/desktop/flavours](https://ubuntu.com/desktop/flavours)

[https://www.edubuntu.org/](https://www.edubuntu.org/)

6) As the above post recommends - install in a virtual machine.

7) Find an online study course.

Regards

---

### Post by yancek on 2024-11-09
>  I have tried dual-boot which also does not work. 

Yes it does for millions of users.  It may not have worked for you but it will not be possible to help with the information you posted.    Apparently part of the problem is with WSL.

> I am trying to go for a simple lightweight Ubuntu download in a 60Gb partition
 

Did you download the Ubuntu iso, verify the download with the checksum, write the iso to some device (DVD/USB) and boot from that device?   You indicate that you have windows 10 installed but I don't see anything indicating the drive is GPT which would mean an EFI install.  You can check if it is GPT by following the instructions at the link below.  I ask because part of your output above shows:  BIOS Mode Legacy

[https://www.tenforums.com/tutorials/84888-check-if-disk-mbr-gpt-windows.html](https://www.tenforums.com/tutorials/84888-check-if-disk-mbr-gpt-windows.html)

It might be easier to use virtual software on windows and boot/install ubuntu there.

---

### Post by oldfred on 2024-11-09
Not sure what math you want to learn.
Ubuntu has all of these and a variety of sagemath databases.
```
Cantor supports various mathematical applications as backends (provided in
external packages):
 * Maxima Computer Algebra System (cantor-backend-maxima)
 * R Project for Statistical Computing (cantor-backend-r)
 * Sage Mathematics Software (cantor-backend-sage)
 * Octave (cantor-backend-octave)
 * Python (cantor-backend-python3)
 * Scilab (cantor-backend-scilab)
 * Qalculate! (cantor-backend-qalculate)
 * Lua (cantor-backend-lua)


```

---

### Post by shaussie on 2024-11-11
My sincere thanks to ajgreeny,  grahammechanical, yancek, oldfred, and [[COLOR=#000000]joepesci2[/COLOR]]("https://ubuntuforums.org/member.php?u=2192319")[COLOR=#000000] for your very helpful advice and ideas.

After several attempts at download various Ubuntu versions including Minimal, I was able to make it work through VirtualBox 7.1.4, as this was one of the suggestions given to me on this forum.

I can use SageMath through CoCalc at very minimal cost. ($5 /mo).  The current release of Ubuntu 24.04 does not support SageMath, some earlier versions did, and a future 26.04 LTS also may have this feature.

One last question has to do with copying (works fine) and pasting (does not work) when copying multiline commands from Windows into the Ubuntu terminal.  Is there any type of copy/paste/clipboard that works or some workable solution which you know of.

Once again my sincere thanks to you.  Please advice how I can report that my query has been fully answered on this forum.

Kind regards,
Shaussie 

[/COLOR]

---

### Post by Irihapeti on 2024-11-12
Under Thread Tools, there is an item "Mark this thread as solved". Selecting that will mark the thread accordingly.

---

### Post by yancek on 2024-11-12
> [COLOR=#000000]One last question has to do with copying (works  fine) and pasting (does not work) when copying multiline commands from  Windows into the Ubuntu terminal.  Is there any type of  copy/paste/clipboard that works or some workable solution which you know  of.[/COLOR] 

You will probably need guest additions in virtualbox and shared folders and you can find numerous site discussing this such as the one below or for a more detailed explanation, you can go to the 2nd link below which is the user manual which discusses shared folders and guest addtitions in more detail.

[https://forums.virtualbox.org/viewtopic.php?t=93726](https://forums.virtualbox.org/viewtopic.php?t=93726)

[https://download.virtualbox.org/virtualbox/7.1.4/UserManual.pdf](https://download.virtualbox.org/virtualbox/7.1.4/UserManual.pdf)

---

