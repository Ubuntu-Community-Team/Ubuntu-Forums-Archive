---
title: "MAJOR install problems (theres a lot)"
date: 2021-03-22
forum: New to Ubuntu
---

### Post by inveron on 2021-03-22
Hello everyone here so im really new to linux. Ive dealt with windows all my life and well lets just say im sick of it so i decided to try linux out. And it has not been a fun time so far. Im going to run through everything ive done in the past 2 days so maybe someone can point something out along the way.



So yesterday, i started doing some research on everything and how to install it and dual boot with windows.. I shortly learned later that i would need a usb drive. I didnt have one on hand at the time (i do now) so i looked up another way to pull it off. Naturally, i tried unetbootin. That was a pain. It did not work and i understand thats not how unetbootin is supposed to be used but i didnt feel like waiting to be able to get my hands on a drive. So the only thing that happened was it set me back a few steps. Not only could i not install linux but now i have unetbootin stuck in my windows boot options and its still there even after i did a system restore to march 16th which was wayyy before i started all of this. That and a ton of research into linux was all i did yesterday.

Alright onto todays step backward;

So i mostly gave up today until low and behold i got a usb. So i tried creating a live usb with some other installer (i forget the name) that had failed horribly so i got rid of the partition on the usb and after a little bit of playing around i got another one set up with universal usb installer. With a bit of playing around with the eufi firmware settings and disabled quick boot and changed the boot priorities around a bit. So after that i was able to boot from the usb! the excitement faded though. Once i played around with it i installed linux, once it got close to the end it said something i didnt get a chance to read til my second attempt at an install. It said something about it not being able to install certain apps and couldnt send a report because my install wasnt legit. Of course it was i got it straight off of ubuntus website. On the first attempt straihgt after this it said ubuntu had installed and if i restarted i could get into ubuntu. So i restarted and was greeted with the windows bootloader with 2 options; to boot into windows or unetbootin. after that i just did a system restore with windows to get the same result. so after this i did my second attempt at installing ubuntu. so this reinstalled over the initial install from the first attempt. So i let it sit there for a while and i got the error i mentioned earlier straight after so once i finished up with that i decided i was going to redo the download of the iso and start from scratch. Theres a problem with that though. My linux install is still there and i cant access it through the bootloader. I know its there because my hdd size is 82 gigs instead of the 450 something it was beforehand. 

So that is basically everything. I have tried everything i can think of ergo why i set up a forum account to ask around here. Thanks in advance to anyone reading this. 

My laptop specs:
Amd A9: 2 cores 2 threads with about 3.6 ghz if its boosting the base clock is 3.1
8gb of ram
integrated graphics w 1gb vram
226gb ssd with my windows install
i replaced the disck drive with a disk catty and a 500gb hard drive

---

### Post by empv on 2021-03-22
i think u should post your error image!

---

### Post by Impavidus on 2021-03-23
As you mention uefi settings, I'll assume you've got a modern computer with a pre-installed Windows 10 system (or Windows 8, doesn't matter).

Typically, one uses Windows tools to shrink Windows partitions and Linux tools to deal with Linux partitions. If you already used Linux tools on Windows partitions (which may not always be successful), make sure to run some filesystem checks from Windows.

I've read that you must disable secure boot if you install proprietary drivers on Linux. If you don't, secure boot is irrelevant for Ubuntu (but not all Linux distros).

To make sure Ubuntu can access the Windows partition and the Linux bootloader can boot Windows, FastStartup (a Windows feature) must be disabled. Windows can automatically change those settings (FastStartup and secure boot) when it installs updates.

On the first hard drive, there's an efi partition, containing the bootloader. On modern systems, there can be multiple bootloaders installed at the same time, so there will be a Windows bootloader and a Linux bootloader. The latter is known as grub. The Windows bootloader can only boot Windows, the Linux bootloader can boot both systems (provided Windows FastStartup has been disabled). After successful installation, you can use uefi settings to choose the bootloader. On some computers (HP comes to mind), it's a bit hard to convince the computer to use the Linux bootloader, on others (for example most Dells) it all works automatically.

It's hard to get an non-legit Linux system. It's against the idea of open source.

Dual booting Windows and Ubuntu isn't as easy as it used to be, but can still be done. Some people prefer virtual machines or different physical hardware. If you have an older (7–11 years) computer lying around, gathering dust, this is an opportunity to put Ubuntu on it. Ubuntu runs on older computers than Windows.

You didn't mention which version of Ubuntu you attempt to install. I recommend 20.04.

---

### Post by inveron on 2021-03-23
yeah im using 20.04, i had already disabled the fast boot but i had no idea the secure boot could mess with it too. I had gotten access to the grub bootloader but only through booting from the usb which sometimes didnt even work. Id try booting directly from the hdd with the install on it and all it did was bring me back to where i started but ill definetely mess with eufi settings a bit and disable secure boot and try to get into the grub bootloader, Thank you!

---

### Post by inveron on 2021-03-23
yeah i wouldve i just had no idea how to screenshot in try ubuntu, if i get a chance to get a screenshot i will definitely update the post if i can snag one.

---

### Post by inveron on 2021-03-23
Update: so i now know that i just have to get into the grub boot manager, theres a problem though. I disabled secure boot in eufi  and i went over to change boot priorities and grub boot manager was just not there so i started looking it up and i tried the thing with the command line to change the default to grub after i went to restart, nothing changed. So at least i know exactly what i need to figure out now. Thanks to everyone helping out.

---

### Post by yancek on 2021-03-23
Just a guess here, but it seems you have installed Ubuntu in Legacy mode and windows is UEFI.  This and much is  explained at the official Ubuntu documentation site at the link below.  I expect had you read it, you would have avoided these problems.  The site has been online for about 5 years.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I don't know what went wrong with your efforts with unetbootin but what you were trying to do was a 'frugal' install which basically puts the Ubuntu live/installer on  a partition on your hard drive rather than a usb drive.  When you reboot you should be able to select that entry from the boot menu and get the Ubuntu live/installer.  This has been around for at least a decade and has been successfully used by 10's of thousands of people.  The unetbootin boot menu entry is on the windows menu so you will need to remove it while using windows.

---

