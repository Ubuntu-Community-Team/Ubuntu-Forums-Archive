---
title: "Attempting to dual boot Ubuntu with Windows 10 on HP Envy Notebook"
date: 2017-05-18
forum: New to Ubuntu
---

### Post by ksofkso on 2017-05-18
Hi everyone,

I've been attempting to install Ubuntu alongside my pre-existing Windows 10 install on my HP Envy Notebook for a week or so now. I've attempted multiple installs, have tried Ubuntu, Xubuntu, Linux Mint as well as other non-Debian based installations and I'm at my wit's end! I would really appreciate some help or suggestions if anybody has any.

Just a little bit about my PC:
HP Envy Notebook
AMD A10-8700P Radeon R6, 10 Compute Cores 4C+6G 1.8GHz processor
8gb RAM
x64-based processor

So in my various attempts at installation, I have disabled fast shutdown, kept UEFI on (not using legacy boot), have tried with secure boot disabled or enabled. None of this seems to be an issue, and on *most* occasions the live USB for whatever distro I have looked at has worked. Installation appears to go smoothly. I can rearrange the booting order in my UEFI settings so that grub is prioritised over the Windows bootloader. All this appears to be fine. However, when I actually attempt to boot into the newly installed distro, it either freezes on the loading screen, never loads at all, or I get a massive wall of text that appears to hang after a while, all requiring me to hard restart. There doesn't appear to be any consistency to what happens after installation, all that I know is I can never actually boot into the desktop environment like I can during the live installation. I've told myself to just give up a few times, after all, Windows works fine (in fact very speedily on this laptop!) but I really want to give Linux a go. So here I am, posting here, asking for any sage advice if anybody has any to offer?

Thanks a lot.

---

### Post by TheFu on 2017-05-18
It is probably the HP issue.  Vaguely remember that HP doesn't follow the UEFI standards so you have to manually do something inside the efi directory partition to get it working on HP machines.  Lots of thread here about that already full of links and steps to solve it.

It really is an HP issue, not Ubuntu.

---

### Post by ajgreeny on 2017-05-18
It may well be that problem so have a good look at this long thread about UEFI boot problems and solutions.
[https://ubuntuforums.org/showthread.php?t=2147295](https://ubuntuforums.org/showthread.php?t=2147295)

---

### Post by oldfred on 2017-05-18
I do not know AMD specific issues, well.

What model HP?
Some other HP and so far all HP have had UEFI boot issues. But many work arounds.
But with AMD &  AMD graphics you also may have another issue. You need to know which specific AMD family you have and then which driver works with that device.

       [http://askubuntu.com/questions/870453/live-boot-usb-install-of-16-04-fails-on-hp-pavilion-23?noredirect=1#comment1349777_870453](http://askubuntu.com/questions/870453/live-boot-usb-install-of-16-04-fails-on-hp-pavilion-23?noredirect=1#comment1349777_870453)
[http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook](http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook)
Some HP will not boot a flash drive that is gpt partitioned. Some only boot from the USB2 port not USB3 ports.
[http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260](http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260)
HP Check if Customized UEFI settings available like this  HP ProBook 4340
[https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216](https://ubuntuforums.org/showthread.php?t=2332681&p=13527216#post13527216)
HP Envy 700-430QE desktop used bcdedit to dual boot
[URL="http://ubuntuforums.org/showthread.php?t=2260681"]http://ubuntuforums.org/showthread.php?t=2260681
[/URL]
 Envy M6 Change boot order sudo efibootmgr -o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889) 

      
 Trying AMDGPU-PRO 17.10 On Ubuntu 17.04 (does not work directly)
[http://www.phoronix.com/scan.php?page=news_item&px=AMDGPU-PRO-Ubuntu-17.04](http://www.phoronix.com/scan.php?page=news_item&px=AMDGPU-PRO-Ubuntu-17.04)
[URL="https://help.ubuntu.com/community/AMDGPU-PRO-Driver"]https://help.ubuntu.com/community/AMDGPU-PRO-Driver
[/URL]
 Radeon: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
AMDGPU: [https://help.ubuntu.com/community/AMDGPU-Driver](https://help.ubuntu.com/community/AMDGPU-Driver)
AMDGPU-PRO: [https://help.ubuntu.com/community/AMDGPU-PRO-Driver](https://help.ubuntu.com/community/AMDGPU-PRO-Driver) 

[URL="https://help.ubuntu.com/community/AMDGPU-PRO-Driver"]
[/URL] 

    [URL="http://ubuntuforums.org/showthread.php?t=2260681"]
[/URL]

---

### Post by RobGoss on 2017-05-18
There are a few computer manufactures that make it really hard to get Linux installed on to those machines, I can't say if HP is on that list but I know Acer should be at the top. With help from these forums I think we can get Linux on just about any machine hang in there

---

### Post by oldfred on 2017-05-18
@RobGoss
Actually Acer is one of the better ones as it at least has a way using UEFI password & setting trust.
HP, newer Toshiba's, Sony and a few others only boot "Windows Boot Manager" by description which is a violation of UEFI standard. Ubuntu has position paper also saying vendors should not use description as part of UEFI boot.
But only a few systems do not boot Ubuntu at all, but some just give up now that it is more complicated.

---

### Post by RobGoss on 2017-05-19
@Old Fred

Thanks for providing  this information it's good to know, speaking from experience I had the hardest time trying to get Ubuntu installed on a Acer I have 

I did not want to mess things up because it's my wife machine I'm just baby sitting with all the rest of my machines. I just downloaded reFInd and use a USB to boot the Linux Os on that Acer

If it were my machine I would have tried installing Ubuntu with out having to boot using a USB drive

---

