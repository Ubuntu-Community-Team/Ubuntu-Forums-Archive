---
title: "I don't can install ubuntu22.04 from USB live Stick at my new hard disk"
date: 2023-03-12
forum: New to Ubuntu
---

### Post by maisnon on 2023-03-12
When I'll install Ubuntu 22.04 from my live USB Stick, then I have the message that there was something with my hard disk. When I wanted to format, I have a Problem with the Installer and it quit. Therefore, I don't know what else I can make to format oder install Ubuntu. I have tried it with gparted and a lot of trys with other options when I have tried to install ist from the USB Stick. There are the posibilities that I can delete the hard disk and install, or I can make my own partititions and so on, but it doesn't run. 

This message I am writing during live Ubuntu is working. 

I have this Crash report: 
Sorry, the application install.py has stopped unexpectedly. 

Title: install.py crashed with AssertionError in _init_(): Failed to mount the target: /target

I can't copy the text in this report. There are much more, but I don't know what is interesting for you.


Perhaps, someone can help me.

---

### Post by MAFoElffen on 2023-03-12
First, it would be helpful to know what you are trying to install onto...

If you look at the [sticky on UbuntuForums 'system-info']("https://ubuntuforums.org/showthread.php?t=2475931"), at the top of this Section's Page, follow the instructions to download and run that script from the Forum's GitHub page... Or got directly to the [GitHub page]("https://github.com/UbuntuForums/system-info"), and follow the instructions there. When running the script, from a LiveCD (using Try), please choose to upload the script to a PasteBin, then copy the URL to post in your post, so we can look at it...

---

### Post by maisnon on 2023-03-12
I hope I have made it correct, because at least in the report they have spoken about two files. This has 2000 lines, but it is the text from the file system-info. Here is the link: [https://pastebin.com/YcumHdqt](https://pastebin.com/YcumHdqt)

Thank you, very much!

---

### Post by maisnon on 2023-03-12
I have made another live USB stick, if the old one is the problem.

---

### Post by oldfred on 2023-03-12
You posted the program, not the output of the program.

It offers to upload to Internet & you can copy & paste link.
I typically just save report for my own information.

---

### Post by maisnon on 2023-03-12
I am so sorry, I am not English, therefore I understood wrong the first  time. Now I have the link to Pastebin.  [https://paste.ubuntu.com/p/DgXnQqRqVk/](https://paste.ubuntu.com/p/DgXnQqRqVk/)

---

### Post by oldfred on 2023-03-13
Another HP and with nVidia. HP ZBook 15
HP does not make it particularly easy to install, but most are able to once they do all the work arounds.

Did you use zfs partitioning?
I do not know zfs, and based on your question I assume you are not a knowledgeable Linux user?
Default is till ext4 for partition format and best to use that if this is your first install.

Drive configuration is showing issues on zd0, but do not know if from zfs (and maybe ok) or actual drive issue.

HP Zbook 15 NVRAM locked, install issues
[https://ubuntuforums.org/showthread.php?t=2482555](https://ubuntuforums.org/showthread.php?t=2482555)
hp 250 g3  Change boot order in UEFI settings
[https://ubuntuforums.org/showthread.php?t=2467077](https://ubuntuforums.org/showthread.php?t=2467077)

HP 15 disable Optane, your report is not showing Optane, but not sure if it normally shows that  or not.
[https://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/How-to-Disable-Optane-in-Bios-and-set-Disk-Controller-to/td-p/7354483](https://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/How-to-Disable-Optane-in-Bios-and-set-Disk-Controller-to/td-p/7354483) & 
[https://askubuntu.com/questions/1331889/grub-bootloader-issue-with-dual-boot-dual-drive-install-windows-10-ubuntu-20-10](https://askubuntu.com/questions/1331889/grub-bootloader-issue-with-dual-boot-dual-drive-install-windows-10-ubuntu-20-10) & 
[https://askubuntu.com/questions/1162452/problem-installing-ubuntu-in-a-laptop-with-intel-optane](https://askubuntu.com/questions/1162452/problem-installing-ubuntu-in-a-laptop-with-intel-optane)

---

### Post by MAFoElffen on 2023-03-13
@oldfred -- zd0 is a ramdisk for ZFS & ZSys for the crytolock keystore... So he not only installed with ZFS, he installed with ZFS Encrypted.

If you played with things after the install with gparted, we do not know what you "may" have done that may have changed things from what the installer would have done.

What I would try first, just in case your didn't change anything is ask what it does now(?) Does it flash the grub menu (or not), then go to a black screen and stay there? If so, if you press the <Down-Arrow>, does it show a text screen asking for the passphrase, with a couple "*" characters following? If so, then <Backspace" until the "*" characters are gone and enter the passphrase you entered during the setup... That may be the only thing stopping you from booting... If that was all that was wrong, and you did not change anything.

If that is not your problem, then I would suggest starting over, after ensuring you set the BIOS options that oldfred suggested. It looks like you once had Windows, but it is gone now. So no choice of going back there in that direction, unless you wanted to renistall that. I4zf not, then I would suggest installing with the Erase all option, to overwrite, what you did.

Lets talk about "File Managers". LVM2 and ZFS are file managers, that give you more flexibilities and options. Bit if you do not learn to use them, then it just sits there, uitlitzing less than 5% of it's capabilities. I promote and use ZFS. But I would not recommend it to a new user, who is not familiar, nor comfortable with using the command line. LVM2, well there are more people familiar with using that here, so I would feel more comfortable that someone could talk you through using that if you had a problem or needed to do something with that.

Enryption adds it own layer of support and such. Unless you have a requirement, or a very burning desire that tht is what you really need, then I would try a more vanilla installation, where you could concetrate on learning, and enjoying the new operating system, then in the future, taking the plunge for learning and using more... But, ultimately, that is your decision on that.

---

### Post by maisnon on 2023-03-14
That's right, before I wanted to install Ubuntu, I have had a windows  System (Windows 11), but it was on another hard disk. That was too  small, therefore I've bought another much greater. (1 TB) And now I want  to install Ubuntu. 
I've had a few attempts to install. After I was able to install everything from the live stick (with the default settings), I couldn't boot. 
It was saying that no boot system was installed on the hard drive. So I started differents installing, for example, with the partitions too. 
Although I've had set EFI for the EFI partition, it was always a fat system afterwards, i.e. a Windows system and EFI was missing.

Now I'll follow the links and see what I need to change in the BIOS to make the first part accessible for Ubuntu as well.

I will get back to you later.

---

### Post by maisnon on 2023-03-14
Thank you very much for your help. Now it was working. I reset the BIOS to default and then the Ubuntu installation worked fine and I was able to boot, too. Now I set everthing up und will enjoy Ubuntu. 

Where can I say that the problem is solved?

---

### Post by MAFoElffen on 2023-03-14
If you go to the Upper Right of this page, Select the link called "Thread Tools"... Then "Solved".

---

