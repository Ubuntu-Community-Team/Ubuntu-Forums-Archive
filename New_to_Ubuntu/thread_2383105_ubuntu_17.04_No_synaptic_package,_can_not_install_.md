---
title: "ubuntu 17.04 No synaptic package, can not install any new application"
date: 2018-01-20
forum: New to Ubuntu
---

### Post by rosyjag on 2018-01-20
I am a windows 7 user, absolutely new to Linux. I installed Ubuntu 17.04 using a universal USB installer, along side my windows. I get the Grub menu and get to the Ubuntu desktop. I am not able to install any new application; can not install a WiFi driver for net connection. There is no synaptic package. Please help.

---

### Post by ajgreeny on 2018-01-20
The choice of 17.04 as your installation candidate was very unfortunate as on Jan 13 that version lost support meaning the repositories have moved to EOL (End Of Life) URLs.

By changing your /etc/apt/sources.list file you could install some new packages but that would be a very short term action to take as those packages along with the rest of your OS will receive no further security updates.

You really should upgrade to 17.10, or better in my opinion, clean install the last long term support version, 16.04.

If you really want to upgrade see [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades) for details of how to do so.

---

### Post by Impavidus on 2018-01-21
As stated above, you installed an old release. It is a fresh install, so you don't have a lot to lose, so I suggest a fresh install of either 16.04 LTS (supported until April 2021) or 17.10 (supported until July 2018). The next long term support (18.04 LTS) version will come in 3 months. Normally we recommend new users to stick to LTS releases, but if you intend to move on to 18.04 shortly after its release, it doesn't really matter. You can simply install 16.04 or 17.10 over 17.04, wiping 17.04 in the process.

---

### Post by rosyjag on 2018-01-22
OK, I shall download and install 16.04 LTS. Should I take kernel version or full version?
Thanks

---

### Post by Geoffrey_Arndt on 2018-01-22
Don't know what the "kernel version" is - - - as the normal two choices are the "desktop" version or the "server" version.    Based on the kind of question you asked, you want the desktop version (64 bit).   Also, using the torrent seed is much faster to download (and more reliable):

[https://www.ubuntu.com/download/alternative-downloads](https://www.ubuntu.com/download/alternative-downloads)

---

### Post by rosyjag on 2018-01-22
Thanks for the help. To install the 16.04, do I need to first uninstall the 17.04? If yes, How do I do it? I could not find the Ubuntu file, whether I logged into Ubuntu or the Windows (Neither in the C drive nor in the Control panel add/remove programs). Sorry if I am asking stupid questions.

---

### Post by Impavidus on 2018-01-23
No need to uninstall 17.04 first.

As you already have Windows on that computer, it would be safest to use manual partitioning. When you have to choose the installation type, choose "something else". Instruct the installer to use your current Ubuntu partition(s) and mark it/them for formatting, make sure the Windows partition(s) is/are not marked for formatting.

You won't find an Ubuntu file as there is none. Your Ubuntu lives on an entire file system. And you won't find it in Windows as Ubuntu lives not in, but alongside Windows. Unless you use some sort of virtualisation, of course.

One more thing: Is this a bios or uefi system? Most Windows 7 systems are bios, which should make things easy.

---

### Post by rosyjag on 2018-01-23
It's a Bios system. I shall get back after downloading and installing 16.04. Thanks

---

### Post by rosyjag on 2018-01-25
How can I find in which drive my previous installation of Ubuntu 17.04 has been done? I do not remember the  earlier installation steps. Sorry, getting old, I guess (67).
Thanks

---

### Post by Impavidus on 2018-01-25
In the window in the installer where you have to select the partition where you want to install Ubuntu, it should list the partition type for every partition. The partition you used for Ubuntu 17.04 is probably an ext4 partition. Windows uses one or more NTFS partition(s).

---

### Post by rosyjag on 2018-01-26
Downloaded ubuntu-16.04.3-desktop-i386.iso. Mounted it to a USB pen-drive using Universal-USB-Installer-1.9.7.9, as I did for the Ubuntu 17. Set the Bios Boot to load from USB.
Installation type- Chose "something else". In the next window, selected the partition with the ext4 & clicked "continue".
Message: No Root file system is defined. Correct this from partition menu".
I could not see how to do this. So I went back and tried, instead of "something else", "remove 17.04 and install". Same message about root file system.
I also tried making it FAT32 instead of ext4.
Eventually, I don't know how, the installer went ahead and I selected Language=English US, Time zone India (Kolkatta). Then instead of continuing, the message was like: "Installer crashed. Can not copy files to hard disc. Try cleaning CD/DVD. (My Hard disc is ST3500413AS ATA device, working fine. My DVD drive sometimes get stuck, but I thought that DVD drive is not essential for the installation)
Then the message: When you close this window you can get the error log.
But could not close the window, it kept hanging.
Thanks guys, I really appreciate your prompt and caring help.

---

### Post by Impavidus on 2018-01-26
When you select the partition to use for Ubuntu, you have to mark it for formatting and set its mountpoint to /. That will make it the root partition. Best to make it ext4. There are some other possibilities, but you can't install Ubuntu on a fat32 or ntfs partition. "Remove 17.04 and install" may work fine too. I never install Ubuntu that way as my needs are always complex enough to need manual partitioning.

"Installer crashed. Can not copy files to hard disc. Try cleaning CD/DVD," is not the clearest error message I've ever seen. It could be a bad usb drive. Have you checked it for defects? When you boot the live disk, there should be the option to check it for defects.

---

### Post by rosyjag on 2018-02-02
Reached up to entering my name and user name; while I was at it, I got the error message: [Errno 5] input/output error, and also the same message as before, something like "installation failed, not able to write files to hard disk" and it was just hanging. After shutting down from the old Ubuntu17, could not boot again. so no Windows, too. The service person found that the Hard disc was completely wiped out, but in a good condition. He reinstalled the Windows and the next attempt at installing Ubuntu16 had the same results. Don't know how I can succeed in my wish to use Ubuntu, since none of the service persons I know can help me. Any suggestion would be appreciated.
Thanks

---

### Post by mörgæs on 2018-02-02
Which computer are you using?
Can you do a live boot without installing?

---

### Post by rosyjag on 2018-10-03
Sorry about the long absence. I am back to try installing again. I have a 32-bit OS with Intelcore i3 CPU, 530 @2.93 GHz and 2GB RAM. Under alternative downloads with BitTorrent, ubuntu-16.04.5-desktop-i386.iso is available. Would that be OK for me?

---

### Post by deadflowr on 2018-10-03
> Would that be OK for me?
Yes
Your system can handle any version of Ubuntu.
But why 32-bit?

---

### Post by rosyjag on 2018-10-03
Glad to say that I have installed 16.04 and it is working. Now Ubuntu offers me to upgrade to 18.04. But I have a 32-bit OS and I saw somewhere that 18.04 is not compatible with 32-bit systems. So I should not opt for that upgrade, right?
Thanks

---

### Post by Topsiho on 2018-10-04
That's right: Ubuntu 18.04 is not available for 32-bits processors. Maybe a lighter version of Ubuntu, Xubuntu, Lubuntu or so. That you'll have to investigate (google for it) yourself :). Ubuntu 16.04 is supported until 2021, so there is no hurry. But you'll have to be aware that 32 bits is getting obsolete rapidly.

Topsiho

---

### Post by deadflowr on 2018-10-04
32-bit packages still exist on 18.04
They just stopped building 32-bit installation images.
The logic being any machine that can run the modern versions of Ubuntu should be 64-bit.
There isn't any compelling reason to run 32-bit on any machine that can run 64-bit.
The old standard argument was that RAM usage being a giant difference doesn't really hold up to snuff.
As RAM on 64-bit versus 32-bit is mostly negligible.
(The argument being 64-bit requires twice the memory, which is not the case.)

This link is from 16.04, but it still holds up, mostly:
[https://bryanquigley.com/posts/memory-usage/ubuntu-16-04-livecd-memory-usage-compared.html]("https://bryanquigley.com/posts/memory-usage/ubuntu-16-04-livecd-memory-usage-compared.html")

---

### Post by rosyjag on 2018-10-09
Is it necessary to install an antivirus software? If yes, any recommendations? (I am on 16.04.5 LTS 32bits)

---

### Post by wildmanne39 on 2018-10-09
No you really do not need antivirus software, if you have more questions that do not pertain to solving the synaptic package issue please start another thread on that issue, we only allow one topic per thread.

Thanks!

---

### Post by oldos2er on 2018-10-09
> **rosyjag said:**
> Is it necessary to install an antivirus software? If yes, any recommendations? (I am on 16.04.5 LTS 32bits)

Please see [https://ubuntuforums.org/showthread.php?t=510812](https://ubuntuforums.org/showthread.php?t=510812)

---

