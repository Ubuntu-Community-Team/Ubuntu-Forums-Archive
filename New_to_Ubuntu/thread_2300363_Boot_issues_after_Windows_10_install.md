---
title: "Boot issues after Windows 10 install"
date: 2015-10-25
forum: New to Ubuntu
---

### Post by Indray on 2015-10-25
Hi everyone,

I've recently launched the update to upgrade my Windows 7 to Windows 10. I previously had installed Ubuntu last year and I was not aware that Windows 10 was that rude about other OS installed on the machine. Im not using Ubuntu anymore, I have another computer dedicated to that. But after the first reboot I got the famous "No such partition, grub rescue >"

So after looking on the Internet, I tried the "recommended repair" from Boot Repair Disk mounted on a Usb stick through Rufus. First I have to say that whn im trying to start a fresh "64-bit session" with Boot Repair Disk (BRD), my computer doesnt not boot. First my screen is totally messed up for a while (strange multi colored randomly screen) and then I have message without GUI saying a lot of "failed to idle channel 0xcccc0001 [xorg[7699]]" and a lot of other no understable messages... so I reboot on BRD and I chose the "64-bit session (failsafe)" and finally it boots.

I've done the "recommended repair" and it looks like it finishes right. So I properly shutdown the computer but when I try to boot on my hard drive I got the grub rescue error again. So I post here my Boot-info in order to get a little bit of help to get my computer booting again.

[http://paste.ubuntu.com/12945291/](http://paste.ubuntu.com/12945291/)

Thanks in advance, I stay available for any infos that might help you to figure out what is going on.

EDIT : I managed to continue Windows 10 installation by doign the following :
- Download Windows 10 Media Creation Tool x64 from official retailer
- Create an USB Bootable with the software
- Boot on it, and figure out to launch a command prompt (Advanced Options)
- Type the following command which worked for me : "bootrec /fixmbr" and then "bootrec /fixboot"
- "Operation successful" should prompt (I hope) and you should be able to boot without the USB stick and Windows 10 will continue his update process.

I've found this on another forum : [http://superuser.com/questions/198232/boot-windows-from-grub-rescue](http://superuser.com/questions/198232/boot-windows-from-grub-rescue) 

Hope this will help somebody someday :D

---

### Post by yancek on 2015-10-25
Your boot repair output shows Grub code in the MBR.  It also shows no Linux partitions on the drive.  The code in the MBR is looking for sda6 which does not exist.  This would be where almost all the Grub files required to boot would reside.  Was that your old Ubuntu partition?  I expect it was.  Did you still have Ubuntu installed on this drive when you upgraded to windows 10?  I would not expect that upgrade to overwrite it.

I don't know if boot repair can repair the proprietary windows code, generally you need the windows installation disk with the repair option.  Maybe someone more familiar with windows will have a suggestion.

---

### Post by Indray on 2015-10-25
Hmm thanks for your answer.

I had my Ubuntu not working since a long time and I never managed to solve that, so my Ubuntu install before the Windows 10 update was messy.
But, now I'd really like to know what is going on ? Can't I remove Grub and make my computer boot on Windows 10 with liveUSB boot-repair session ?
I am totally lost.

---

### Post by yancek on 2015-10-25
> Can't I remove Grub and make my computer boot on Windows 10 with liveUSB boot-repair session ?

I don't know but I doubt it.  Windows is proprietary and I have read that boot repair can make some repairs but I've never needed to use and don't use windows.  You can easily remove Grub (actually you already have removed 90%+ of it from the partition) by overwriting the code in the MBR.  Generally, you need the windows install media for that with the Repair option.  You have all the windows boot files on your partition, you just need to get this code in the MBR from windows.  The link below is to the microsoft support site with a detailed explanation of repairing the MBR with the windows disk.

[https://support.microsoft.com/en-us/kb/927392](https://support.microsoft.com/en-us/kb/927392)

More info on creating a system repair disk.  You can do it on another computer but it needs to be the same release version of windows.

[http://www.sevenforums.com/tutorials/2083-system-repair-disc-create.html](http://www.sevenforums.com/tutorials/2083-system-repair-disc-create.html)

If you have a Recovery disk you created when you first booted windows, that might work, not sure?  You could try booting your Recovery disk to see if it has a "Repair" option.
According to the link below, you might be able to use boot repair.  Take a look and give it a try if you want.  Never used it myself so don't know if it will work but the people who posted seemed to have success.

[http://askubuntu.com/questions/326532/how-to-fix-the-mbr-for-windows-7](http://askubuntu.com/questions/326532/how-to-fix-the-mbr-for-windows-7)

---

### Post by Indray on 2015-10-25
Thanks sir. I'll update my thread and mark it as solved, maybe will it help other.

---

