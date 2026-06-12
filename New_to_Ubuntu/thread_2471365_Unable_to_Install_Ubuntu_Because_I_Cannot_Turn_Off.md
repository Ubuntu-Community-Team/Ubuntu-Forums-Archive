---
title: "Unable to Install Ubuntu Because I Cannot Turn Off RST"
date: 2022-01-27
forum: New to Ubuntu
---

### Post by androy518 on 2022-01-27
Device: HP Pavilion 15t touch (15t cs-200)
I want to install Ubuntu on my laptop but I am unable to do so because I cannot turn off RST on my laptop. I started by following a guide I found on YouTube([https://www.youtube.com/watch?v=D4WyNjt_hbQ](https://www.youtube.com/watch?v=D4WyNjt_hbQ)) I got to around 18 minutes into the guide when the installer said that I needed to turn off RST. There was a QR code paired with the message so I scanned the code with my phone and followed the instructions provided. The instructions said to open the Registry Editor and to set two variables to be equal to 0. Their file locations are here (Computer\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\iaStorV\StartOverride) and here (Computer\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\storahci\StartOverride). After I set the variables to be equal to zero, I restarted my computer, pressed esc to pause the startup, then pressed f10 to enter my laptop's BIOS. After this, the BIOS settings appeared and there were 4 tabs (Main, Security, System Configuration, and Exit). There was nothing that I could do in Main except look at the system log, security had unrelated settings and I needed to change a setting so I did not need to exit yet so I went to System Configuration > UEFI Device Configuration > Intel(R) Rapid Storage Technology. This is where I saw the Hard Drive and the Optane Memory that is on my computer. 
When I selected the Hard Drive, this info appeared: Controller Type: AHCI, Controller Interface: SATA, and Status: Non-RAID. 
When I checked the Optane Memory, this info appeared: Controller Type: NVMe, Controller Interface: PCIe, and I believe the status was Disabled or inactive.
Additionally, there was no option available that would allow me to change any of the controller types or controller interfaces. This seems unusual to me because the guide in the QR code that was provided to me while I was trying to install Ubuntu said that I needed to "re-configure Windows to use AHCI" but the hard drive already appears to be using AHCI. 
After I saw this information, I exited BIOS and booted back into the USB drive that I was trying to install Ubuntu from. When I tried to install it again, I got the same error and QR code. After this, I booted back into Windows, tried the same process again, and got the same result. After this, I went back to Windows and opened Intel(R) OptaneTM Memory and Storage Management because I thought that the Optane memory might be causing this issue. This is where I saw that the PCIe Intel Optane Memory was disabled. When I saw that it was disabled, I went back into the BIOS and recombined the Optane Memory and the Hard Drive. Then I tried to install Ubuntu again and got the same message. After this, I looked online for some guides on how to disable the Intel Optane Memory because I still thought that it was causing this issue. In those guides, and app called "Intel Rapid Storage Technology" was used to disable the Optane memory. I tried installing it from this link([https://www.intel.com/content/www/us/en/download/19512/intel-rapid-storage-technology-driver-installation-software-with-intel-optane-memory-10th-and-11th-gen-platforms.html](https://www.intel.com/content/www/us/en/download/19512/intel-rapid-storage-technology-driver-installation-software-with-intel-optane-memory-10th-and-11th-gen-platforms.html)) but no application appeared. Does anyone know what I am doing incorrectly? I like the OS based on my experience using it from the USB drive and I want to install it.

**EDIT: **Link to pictures of my BIOS Menu [https://imgur.com/a/q6GMKFL ]("https://imgur.com/a/q6GMKFL")

**Update: **Physically removing the Optane Memory from my laptop has caused the RST Error to disappear. 
[URL="https://imgur.com/a/q6GMKFL"]



[/URL]

---

### Post by tea for one on 2022-01-28
You may have to disable some pre-installed software managing the RST.
Here are some more links to try and help.
[https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500](https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500)
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)
[https://softwarekeep.com/help-center/how-to-download-standard-sata-ahci-controller-driver-on-windows-10](https://softwarekeep.com/help-center/how-to-download-standard-sata-ahci-controller-driver-on-windows-10)
[https://ubuntuforums.org/showthread.php?t=2458373&page=2&highlight=rst+optane](https://ubuntuforums.org/showthread.php?t=2458373&page=2&highlight=rst+optane)

---

### Post by androy518 on 2022-01-28
Thank you for the help. I followed all of the links that you provided. Hopefully, the information that I provide will be helpful for solving this problem.

**Link 1: **
In link 1, the solution provided was to type this command in the terminal "[COLOR=#232629][FONT=ui-monospace]bcdedit /set {current} safeboot minimal[/FONT][/COLOR]", reboot, change the operation mode to AHCI, boot back into windows, type this command into the terminal "[COLOR=#232629][FONT=ui-monospace]bcdedit /deletevalue {current} safeboot[/FONT][/COLOR]", then reboot again. I have already tried this before but when I entered the BIOS, there was still no option that would allow me to change the operation mode. One conversation on this thread did catch my attention ([https://chat.stackexchange.com/rooms/129132/discussion-between-sergio-and-ramhound](https://chat.stackexchange.com/rooms/129132/discussion-between-sergio-and-ramhound)). In this thread, there is a screenshot of an "Intel(R) Chipset SATA/PCIe RST Premium Controller" which I have this on my computer but the conversation ended before any further instructions were provided so I am not sure if I need to do anything with this controller.
[B]
Link 2: 
[/B]These are the instructions that I tried follow in my original post. I could not complete them because there was no option to switch the operation mode and my hard drive was already listed as SATA AHCI.

**Link 3:**
I clicked on the link to the Intel drivers but I did not know which driver to install from the list. I tried clicking on the second driver from the top then clicking on the .cab file that appeared in the popup window but nothing seemed to happen after that. After I clicked the .cab file, I tried to follow the instructions further by opening the device manager but there was no category called "[COLOR=#000000][FONT=Ubuntu]IDE ATA/ATAPI controllers[/FONT][/COLOR]". There was a category called Storage controllers. This is the category where I found the "Intel(R) Chipset SATA/PCIe RST Premium Controller" which I mentioned under the Link 1: section.
My computer has this processor: Intel(R) Core(TM) i7-8565U CPU @ 1.80GHz   1.99 GHz

[B]Link 4: 
[/B]The [COLOR=#000000]"Intel® [/COLOR][COLOR=#417394]Optane[/COLOR][COLOR=#000000]&#8482; Memory and Storage Management Application"[/COLOR] that was mentioned on this website is installed on my computer. When I checked this application, It said that the Intel Optane Memory Status was disabled. I tried to boot into Ubuntu from the flash drive and install it. I got the same QR code. Then I booted back into Windows and enabled the Optane Memory. After I did this, I booted back into Ubuntu and got the same QR code when trying to install. I then tried booting into BIOS again and checking the Hard Drive and Optane Memory. This time, it said that the Optane Memory was being used as a Cache and the hard drive was the same as before. It showed that the Optane Memory was working. I then disabled the Optane Memory from the BIOS, booted back in to Windows, restarted the computer, then booted back into Ubuntu to try to install Ubuntu on my computer but I got the same QR code.

---

### Post by tea for one on 2022-01-28
> **androy518 said:**
>  then booted back into Ubuntu to try to install Ubuntu on my computer but I got the same QR code.
You have mentioned this QR code a few times and I do not know what it is or what it is supposed to do?
Hopefully, someone else who has knowledge of this will be able to offer assistance.

---

### Post by androy518 on 2022-01-28
This is a link to a screenshot of the QR Code: [https://imgur.com/CSGF3k8](https://imgur.com/CSGF3k8)
Scanning it takes you to: [https://help.ubuntu.com/rst/](https://help.ubuntu.com/rst/)
It seems to contain the same information as a link from a previous post: [https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)

---

### Post by androy518 on 2022-01-28
I have edited my original post with a link to images of my BIOS menu ([https://imgur.com/a/q6GMKFL](https://imgur.com/a/q6GMKFL)). I did not see any way to change the operation mode of my hard drive.

---

### Post by tea for one on 2022-01-28
Ah, I understand the QR code now.
I've never seen this page of the installer before because I do not have RST enabled.
Thanks for the info.

I wish I could help more but I've already provided the links which have helped other users previously.

---

### Post by tea for one on 2022-01-28
I've just noticed that you have TPM Enabled in the UEFI set-up.
Generally, it is better to disable before running the installer.

---

### Post by tea for one on 2022-01-28
I do not know if this is helpful but post no. 30 of [https://ubuntuforums.org/showthread.php?t=2466159&page=3](https://ubuntuforums.org/showthread.php?t=2466159&page=3) has another link to Intel Optane Tools.

---

### Post by oldfred on 2022-01-28
Are these the same info you have?
HP 15 disable Optane
[https://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/How-to-Disable-Optane-in-Bios-and-set-Disk-Controller-to/td-p/7354483](https://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/How-to-Disable-Optane-in-Bios-and-set-Disk-Controller-to/td-p/7354483) & 
[https://askubuntu.com/questions/1331889/grub-bootloader-issue-with-dual-boot-dual-drive-install-windows-10-ubuntu-20-10](https://askubuntu.com/questions/1331889/grub-bootloader-issue-with-dual-boot-dual-drive-install-windows-10-ubuntu-20-10)
[https://askubuntu.com/questions/1162452/problem-installing-ubuntu-in-a-laptop-with-intel-optane](https://askubuntu.com/questions/1162452/problem-installing-ubuntu-in-a-laptop-with-intel-optane)
HP with optane
[https://askubuntu.com/questions/1257230/dual-boot-ubuntu-with-windows-cannot-change-from-raid-to-ahci-through-bios](https://askubuntu.com/questions/1257230/dual-boot-ubuntu-with-windows-cannot-change-from-raid-to-ahci-through-bios)

HP 17-BY4063CL Laptop shows UEFI screens, needed 21.04 since new Intel chip
[https://ubuntuforums.org/showthread.php?t=2462045](https://ubuntuforums.org/showthread.php?t=2462045)

Dell also has an app from Intel to remove Optane.
Optane removal apps
removal (setuprst.exe and setupoptanememory.exe - both from Dell
Asus Zenbook UX425EA w/Intel Iris Xe Graphics - turn off optane with Windows Optane app
[https://ubuntuforums.org/showthread.php?t=2458373](https://ubuntuforums.org/showthread.php?t=2458373)

---

### Post by androy518 on 2022-01-29
> **tea for one said:**
> I do not know if this is helpful but post no. 30 of [https://ubuntuforums.org/showthread.php?t=2466159&page=3](https://ubuntuforums.org/showthread.php?t=2466159&page=3) has another link to Intel Optane Tools.
This thread describes a very similar issue to the one that I am having but I do not see the link to Intel Optane Tools on the page.

---

### Post by androy518 on 2022-01-29
> **oldfred said:**
> Are these the same info you have?
HP 15 disable Optane
[https://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/How-to-Disable-Optane-in-Bios-and-set-Disk-Controller-to/td-p/7354483](https://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/How-to-Disable-Optane-in-Bios-and-set-Disk-Controller-to/td-p/7354483) & 
[https://askubuntu.com/questions/1331889/grub-bootloader-issue-with-dual-boot-dual-drive-install-windows-10-ubuntu-20-10](https://askubuntu.com/questions/1331889/grub-bootloader-issue-with-dual-boot-dual-drive-install-windows-10-ubuntu-20-10)
[https://askubuntu.com/questions/1162452/problem-installing-ubuntu-in-a-laptop-with-intel-optane](https://askubuntu.com/questions/1162452/problem-installing-ubuntu-in-a-laptop-with-intel-optane)
HP with optane
[https://askubuntu.com/questions/1257230/dual-boot-ubuntu-with-windows-cannot-change-from-raid-to-ahci-through-bios](https://askubuntu.com/questions/1257230/dual-boot-ubuntu-with-windows-cannot-change-from-raid-to-ahci-through-bios)

HP 17-BY4063CL Laptop shows UEFI screens, needed 21.04 since new Intel chip
[https://ubuntuforums.org/showthread.php?t=2462045](https://ubuntuforums.org/showthread.php?t=2462045)

Dell also has an app from Intel to remove Optane.
Optane removal apps
removal (setuprst.exe and setupoptanememory.exe - both from Dell
Asus Zenbook UX425EA w/Intel Iris Xe Graphics - turn off optane with Windows Optane app
[https://ubuntuforums.org/showthread.php?t=2458373](https://ubuntuforums.org/showthread.php?t=2458373)

This link seems very similar to the issue that I am having ([https://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/How-to-Disable-Optane-in-Bios-and-set-Disk-Controller-to/td-p/7354483](https://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/How-to-Disable-Optane-in-Bios-and-set-Disk-Controller-to/td-p/7354483)). It says that the advanced options in BIOS are locked by HP. Is there any way to unlock the advanced options.

This entire situation also seems unusual because when I disabled the Optane memory from the application on my computer and in the BIOS, it said that the hard drive was in SATA/AHCI mode but when I tried to install Ubuntu, the installation detected RST even after I turned off the Optane Memory.

---

### Post by tea for one on 2022-01-29
> **androy518 said:**
> This thread describes a very similar issue to the one that I am having but I do not see the link to Intel Optane Tools on the page.

[https://www.intel.com/content/www/us/en/download/19520/intel-memory-and-storage-tool-cli-command-line-interface.html?wapkw=optane%20cli%20linux](https://www.intel.com/content/www/us/en/download/19520/intel-memory-and-storage-tool-cli-command-line-interface.html?wapkw=optane%20cli%20linux)

Does your UEFI set up have an admin or master password to access Advanced Options?

---

### Post by androy518 on 2022-01-29
> **tea for one said:**
> [https://www.intel.com/content/www/us/en/download/19520/intel-memory-and-storage-tool-cli-command-line-interface.html?wapkw=optane%20cli%20linux](https://www.intel.com/content/www/us/en/download/19520/intel-memory-and-storage-tool-cli-command-line-interface.html?wapkw=optane%20cli%20linux)

Does your UEFI set up have an admin or master password to access Advanced Options?

In this screenshot of my BIOS([https://imgur.com/gRoxb3V](https://imgur.com/gRoxb3V)) it says that the Administrator password and Power-on password are both clear.

---

### Post by tea for one on 2022-01-29
Perhaps you have to create an Admin password to access Advanced Options?

I have a 5 year old HP Netbook where the UEFI Security tab also shows Administrator Password as [COLOR="#0000CD"]Clear[/COLOR]
However, it does not prevent me altering any setting because I do not have inaccessible Advanced Options.
My device is a basic model and I'm sure that yours has many more features.

There is little consistency in UEFI firmware even within iterations from the same vendor.

---

### Post by androy518 on 2022-01-29
> **tea for one said:**
> Perhaps you have to create an Admin password to access Advanced Options?

I have a 5 year old HP Netbook where the UEFI Security tab also shows Administrator Password as [COLOR=#0000CD]Clear[/COLOR]
However, it does not prevent me altering any setting because I do not have inaccessible Advanced Options.
My device is a basic model and I'm sure that yours has many more features.

There is little consistency in UEFI firmware even within iterations from the same vendor.


I just set an Admin password but the advanced options did not appear.

---

### Post by tea for one on 2022-01-30
Not much progress so far, but let's see...........

Image no. 2 (from post no. 1) of your UEFI shows Intel (R) Rapid Storage Technology, have you clicked the little white arrow?
Anything there? (screenshot attached)

You previously reported that you could disable Optane within Windows 10 and also set the 931.5GB drive to AHCI.
Even then Ubuntu installer displayed the message about "turning off RST"

After setting AHCI and disabling Optane, have you considered physically [COLOR="#0000FF"]removing[/COLOR] the Optane disk?
I have read that other owners of similar devices have replaced the Optane drive with M.2 nvme or ssd for additional storage.
Proceed cautiously, it may prevent booting into Windows if HP have chained everything together?

Ensure you have backed up your personal data and have a Windows 10 repair disk available.

---

### Post by androy518 on 2022-01-30
I will try removing the Optane memory manually when I get the tools to do so.
This is the menu behind the white arrow head: [https://imgur.com/XrBcDK2](https://imgur.com/XrBcDK2)
This is what appears under SATA: [https://imgur.com/gkBldMB](https://imgur.com/gkBldMB)
This is what appears under PCIe: [https://imgur.com/lAILUNr](https://imgur.com/lAILUNr)

---

### Post by oldfred on 2022-01-30
It is interesting that the small SSD is seen as NVMe.
I then am not sure what Optane is other than proprietary Intel or just a brand name for its NVMe?
NVMe is its own standard for drive access. 
[https://en.wikipedia.org/wiki/NVM_Express#Comparison_with_AHCI](https://en.wikipedia.org/wiki/NVM_Express#Comparison_with_AHCI)

I recently saw where a hard drive vendor created a HDD using NVMe. It would not really be faster since HDD, but then only NVMe interface required.

The only tool you need to change NVMe drives is a tiny screw driver, like you use to repair eyeglasses or similar.

---

### Post by androy518 on 2022-02-14
Physically removing the Optane Memory from my laptop stopped the RST error from appearing. Thank you all.

---

### Post by tea for one on 2022-02-14
> **androy518 said:**
> Physically removing the Optane Memory from my laptop stopped the RST error from appearing. Thank you all.

Good news.
Have you now installed Ubuntu?

---

### Post by MAFoElffen on 2022-02-14
> **tea for one said:**
> You have mentioned this QR code a few times and I do not know what it is or what it is supposed to do?
Hopefully, someone else who has knowledge of this will be able to offer assistance.
Being that I had to work as a Certified HP, Dell and Lenovo Warranty Service Tech, I have some Phone Apps from them to scan and decode the QR codes for me, and to tell me what those errors mean.

I've run tests on this and did some investigation on this on my own... Intel RST and Intel Optane is tricky with Linux. 

If you have both Windows and Linux, you "have to" turn off all the options in the UEFI BIOS, then you also physically remove the Optane card. It cannot be there if you plan to run both Windows and any Linux OS. ***Even with all the BIOS Options turned off***, if it is 'there', both Windows and Linux can (somehow) still see the Optane card connected on the Bus when they do their device checks of the hardware, during boot of the OS. Windows, if ran, will try to re-activate it and take ownership of it. (You can see it in the Windows system logs!!!) Linux will see it, but see that the Windows stuff still in it's cache... (Remember that I said 'even after the BIOS settings have been turned off..." You would think that logically, that it magically turns off some kind of switch, but it doesn't. It seems that the BIOS settings only disable some 'features' that support it.)

For most Users, they cannot install Linux if an Optane Card is in the system. There is a way to install Ubuntu on hardware with Optane, if it is the only OS (No Windows OS), but it requires certain settings, certain drivers, and that the Optane card is initialized so that is has 'nothing' in it's cache from any other OS'es... This means that their can also only be "one" Linux OS there of one version. But the installation process of that is above the skill level of most Users. If it is done wrong, they can brick hardware. So for most Users, the answer is still a "No".

This is just what I have personally experienced and found out for myself.

EDIT:
For followon Users reading this later, the fastest and easiest way to remove an Intel Optane card from your system, is to have the system completely shut down and all cables disconnected. Set the system on an anti-static mat. Remove the Optane card as per your system's guidance. (Unplug the card.) On initial start-up after that, go directly to your BIOS Firmware Settings and reset the BIOS to factory defaults. Since the BIOS will not see the Optane Card there (this time), it will set the correct settings for what is there automatically for you. Make any other changes to the BIOS that you need to install that version of Linux to your system. Save the changes and go on...

---

### Post by androy518 on 2022-02-15
> **tea for one said:**
> Good news.
Have you now installed Ubuntu?
I currently have Ubuntu installed on my laptop and I am liking the operating system. I am currently planning to run Windows through a virtual machine in the future so that I can use some applications that only run on Windows.

---

### Post by tea for one on 2022-02-15
> **androy518 said:**
> I currently have Ubuntu installed on my laptop and I am liking the operating system.

Excellent - I hope that you can consider marking the thread as solved to help other forum users/searchers.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

There is a lot of useful information in this discussion especially post 22 from [COLOR="#0000FF"]MAFoElffen[/COLOR].
I don't recall any other thread where the Optane drive was physically removed and Ubuntu was consequently installed with success.
The comment about resetting the UEFI to defaults (after removing the Optane drive) is probably beneficial.
Sometimes, secure boot may be a default, therefore be vigilant.
> **androy518 said:**
>  I am currently planning to run Windows through a virtual machine in the future so that I can use some applications that only run on Windows.
There is an active Virtualisation forum [https://ubuntuforums.org/forumdisplay.php?f=308](https://ubuntuforums.org/forumdisplay.php?f=308)

---

### Post by ctrl-alt-delete on 2022-03-24
On the HP EliteDesk 800 G5 TWR to turn this off, go to the BIOS:

Advanced, System Options

Uncheck - Configure Storage Controller for Raid

Uncheck - Configure Storage Controller for Intel Optane


Back to Main then Exit and Save

**Warning:** if Windows has this enabled and you are dual booting, you must resolve Windows dependencies first or you will lose access to Windows.

I had no need for this as I was erasing Windows from my system.

---

