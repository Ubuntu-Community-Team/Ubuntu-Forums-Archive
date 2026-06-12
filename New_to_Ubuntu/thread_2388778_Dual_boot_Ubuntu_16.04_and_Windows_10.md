---
title: "Dual boot Ubuntu 16.04 and Windows 10"
date: 2018-04-07
forum: New to Ubuntu
---

### Post by imaginary.duck on 2018-04-07
I bought a new computer:
Lenovo Legion Y520 (Intel Core i7-7700HQ, 16GB RAM, 1TB HDD, 128GB SSD, Nvidia GeForce GTX 1050 4GB, Windows 10 Home)

Now I am trying to dual boot it with Ubuntu 10.
Disabled "fast boot" and "secure boot".

I tried to make live USB in both Ruthus and Unetbootin.
Tried both to make a live USB with "MBR partition scheme for BIOS or UEFI" and "GPT partition scheme for UEFI" option. 

When I reach fourth steep, where I can partition the computer, I get the following error:
"This machine's firmware has started the installer in UEFI mode but it looks like there may be existing operating systems already installed using "BIOS compatibility mode". If you continue to install Debian in UEFI mode, it might be difficult to reboot the machine into any BIOS-mode operating systems later. If you wish to install in UEFI mode and don't care about keeping the ability to boot one of the existing systems, you have the option to force that here. If you wish to keep the option to boot an existing operating system, you should choose NOT to force UEFI installation here."

Attached a picture of partition table.
Looks like Ubuntu can't find the SSD disk where Windows 10 is currently installed.
[ATTACH=CONFIG]279192[/ATTACH]

Any ideas how to solve the problem?
Virtual box is not a solution for me. :)

---

### Post by oldfred on 2018-04-07
You said you bought new computer. Vendors are required to install Windows in UEFI mode which requires gpt partitioning.

But your partitioning has none of the extra partitions that Windows has with UEFI, and looks like a typical BIOS/MBR configuration.
Did you reinstall Windows in 35 year old BIOS/MBR configuration. That works but is not current normal configuration.

Post this, if it says partition table: MBR/dos/msdos, then Windows must be in BIOS boot mode.

sudo parted -l

Also if drive was orginally gpt and Windows installed in BIOS mode it incorrectly converts drive from gpt to MBR. It leaves backup gpt partition table and Linux tools see both and do not know which you want. You then need to use fixparts to remove backup gpt data.
       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda

---

### Post by imaginary.duck on 2018-04-07
> **oldfred said:**
> You said you bought new computer. Vendors are required to install Windows in UEFI mode which requires gpt partitioning.

But your partitioning has none of the extra partitions that Windows has with UEFI, and looks like a typical BIOS/MBR configuration.
Did you reinstall Windows in 35 year old BIOS/MBR configuration. That works but is not current normal configuration.

Post this, if it says partition table: MBR/dos/msdos, then Windows must be in BIOS boot mode.

sudo parted -l

Also if drive was orginally gpt and Windows installed in BIOS mode it incorrectly converts drive from gpt to MBR. It leaves backup gpt partition table and Linux tools see both and do not know which you want. You then need to use fixparts to remove backup gpt data.
       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda

Attached is the output
[ATTACH=CONFIG]279199[/ATTACH]

---

### Post by oldfred on 2018-04-07
Usually better to just copy terminal or text directly into Forum. But best to also include code tags to preserve formatting.

It says drive is gpt. But it does not have an ESP - efi system partition (FAT32 with boot flag)?

Does Windows boot directly from UEFI/BIOS?

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by imaginary.duck on 2018-04-08
Here is the output from Boot-info
[http://paste.ubuntu.com/p/XzQdRGW9cz/](http://paste.ubuntu.com/p/XzQdRGW9cz/)

This is after boot repair:
[http://paste.ubuntu.com/p/hnzSbmcRVd/](http://paste.ubuntu.com/p/hnzSbmcRVd/)

Doesn't seem to work... :(

---

### Post by oldfred on 2018-04-08
You are not showing any working systems.
You do have UEFI entries for Windows, but partition does not exist, and Linpus Lite which is your USB.

Are you not installing Ubuntu? I do not know Linpus Lite it seems to be Fedora based, not even based on Ubuntu.

But you do not have a working Windows nor any other installed system.
Best to start over.

You may be able to reinstall Windows. But also then have to add drivers manually. Or see if your vendor has the OEM version that includes everything for your system.
 Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c) 

Then if you want Ubuntu, install it after Windows. Lots of detail on UEFI install in link in my signature below.

---

### Post by imaginary.duck on 2018-04-08
> **oldfred said:**
> You are not showing any working systems.
You do have UEFI entries for Windows, but partition does not exist, and Linpus Lite which is your USB.

Are you not installing Ubuntu? I do not know Linpus Lite it seems to be Fedora based, not even based on Ubuntu.

But you do not have a working Windows nor any other installed system.
Best to start over.

You may be able to reinstall Windows. But also then have to add drivers manually. Or see if your vendor has the OEM version that includes everything for your system.
 Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c) 

Then if you want Ubuntu, install it after Windows. Lots of detail on UEFI install in link in my signature below.

I don't know why it is written "Linpus". I downloaded the ISO file from Ubuntus homepage then I created the live PC with Rufus and Unetbootin.

Think I found my product key by right clicking on "My PC". There is a product key that starts with 00325....
Could that be my Windows 10 key?
Is that enough or do I need something else as well?

If I reinstall Windows 10. Will I break my warranty?
I have done dual boot Windows and Ubuntu install many times before.
However, I have never done it with UEFI and only with Windows 7 or below. 
When I reinstall Windows 10. Is there something I should look out for?
Is there some step where I manually have to create or change something?
Or can I just do the usual: press next, next, next ...

---

### Post by oldfred on 2018-04-08
Have not installed Windows since XP. 

But with new UEFI systems, how you boot install media UEFI or BIOS is how it then installs. And you want UEFI.
I do not think since product key is in UEFI, it is even recognized with BIOS install, even if a valid key exists on system. You should not have to type key in.

---

### Post by yancek on 2018-04-08
A better site  for answers to your questions about microsoft and product keys is their site at the link below.  

  [https://support.microsoft.com/en-us/help/10749/windows-product-key](https://support.microsoft.com/en-us/help/10749/windows-product-key)

---

### Post by imaginary.duck on 2018-04-09
(Sorry for more photos. I don't want to type any passwords on a Windows PC.
Windows is only for gaming and nothing else. :lolflag:)

I go insane with this project.
Tried to reinstall Windows 10, but I get the same issue there.
It only finds a part from SSD disk.
[ATTACH=CONFIG]279226[/ATTACH]

Called Lenovo support and they meant that Microsoft have put some protection since Windows 8 that makes it impossible to do dual boot with Linux.
That can't be true as I have seen so many guides about dual booting Ubuntu with Windows 10.

Read several posts about that Microsoft are hiding some of their partitions. 
Downloaded MiniTool partition.
Found that none of my partition was hidden, however, I found a weird 16 MB partition. Could that be the reason?


[ATTACH=CONFIG]279224[/ATTACH][ATTACH=CONFIG]279225[/ATTACH]

If I want to delete all old partitions, how do I do that the easiest way?

I also tried to get support from Microsoft, but it was so many steps and so complicated I just gave up.

---

### Post by kevmccarthy on 2018-04-09
I had a windows 10 PC to start with. Created a blank partition with any partition manager, boot from USB or CD and select install. It comes to a menu asking if you want to keep windows etc. Voila,

Kev

---

### Post by imaginary.duck on 2018-04-09
Also tried complete factory reset. Didn't work either.
What I noticed is that both Windows and Ubuntu can't find the SSD disk at all during installation.
The 128 MB comes from HDD disk.
Can it be that Ubuntu live USB disk doesn't have the SSD driver?
Does anyone know how to check it and update it?

---

### Post by oldfred on 2018-04-09
Your last screen shot shows RAID as one of settings.

Some other brands, Dell for instance have RAID setting on by default with Windows 10. But drive is not RAID.
So for those systems not really RAID, change drives to AHCI, but often have to install the AHCI driver in Windows first.
       XPS 13 9350 Windows reinstall & discussion of RAID vs. AHCI
[https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/](https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/) 
            RAID to AHCI
[https://askubuntu.com/questions/963087/install-dual-boot-ubuntu-with-windows-10-and-raid-on/963100#963100](https://askubuntu.com/questions/963087/install-dual-boot-ubuntu-with-windows-10-and-raid-on/963100#963100) 
            Dell XPS 8920 & Nvidia GTX 1060 & PCIe M2 drive Raid change to AHCI
[https://ubuntuforums.org/showthread.php?t=2360929](https://ubuntuforums.org/showthread.php?t=2360929) 
    

The system reserved is a Windows required partition.
       BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[URL="https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations"]https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations
      [/URL]
 Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition) 
    [URL="https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations"]
[/URL]

---

### Post by imaginary.duck on 2018-04-09
Thank you guys so much for all your replies. 
oldfred post together with this blog:
[http://triplescomputers.com/blog/uncategorized/solution-switch-windows-10-from-raidide-to-ahci-operation/](http://triplescomputers.com/blog/uncategorized/solution-switch-windows-10-from-raidide-to-ahci-operation/)
made everything work as normal.

---

