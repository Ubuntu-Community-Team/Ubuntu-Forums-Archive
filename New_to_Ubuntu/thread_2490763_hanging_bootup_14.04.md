---
title: "hanging bootup 14.04"
date: 2023-09-14
forum: New to Ubuntu
---

### Post by jaxom98 on 2023-09-14
Laptop: Asus X55A , factory standard as far as I know.
OS ubuntu 14.04

Problem: partial boot failure. It waits doing nothing ,then has timed out shows a fewlines:

Gave up waiting for root device.  Common problems:
-Boot args  (cat  /proc/cmdline)
 - Check rootdelay= (did system wait long enough?)
  -Check root= (did system wait fot right device?)
-Missing modules (cat  /proc/modules; ls /dev
Alert!  /dev/disk/by-uuid/d6825235-a641-48e4-87e3-2e9bea133c26 does not exist.  Dropping to a shell!


BustBox v1.21.1 (Ubuntu 1:1.21.0-1Ubuntu1.4) built-in shell (ash)
Enter help for a list of built-in commands.

(initramfs)

If I enter help, I get 11 line of dense abreviations without punctuation. Confused.
It ends with 
(initramfs)

So I do a hard shut down and restart, this brings up 3 lines of boot  menu:
*Ubuntu
advanced options for Ubuntu
System setup

Click on advanced options brings up:
*Ubuntu, with linux 3.13.0-170 generic
Ubuntu, with linux 3.13.0-170 generic  (recovery mode)
Ubuntu, with linux 3.13.0-143 generic
Ubuntu, with linux 3.13.0-143 generic  (recovery mode)
Ubuntu, with linux 3.13.0-92 generic
Ubuntu, with linux 3.13.0-92 generic  (recovery mode)
Ubuntu, with linux 3.13.0-87 generic
Ubuntu, with linux 3.13.0-87 generic  (recovery mode)
Ubuntu, with linux 3.13.0-32 generic 
Ubuntu, with linux 3.13.0-32 generic  (recovery mode)

Using the top 2 lines with 3.13.0-173 does not work.  It just goes to (initramfs) and hangs.

Using the lower lines with ...0-143, ...0-92, ...0-87, ...0-32, in generic mode does a regular startup. 
Using the recovery mode line the recovery goes past the problem then asks to finish boot up in regular mode.

How can I set the startup to : Ubuntu, with linux 3.13.0-143 generic  so I can get a normal startup ?
Currently I am powering up the doing a hard shutdown when  the (initramfs) comes up and restarting and using  advanced option and ...0-143... startup to get booted up. Pita, but it works. 

 PC has crashed, so I don't want to do an OS upgrade on the laptop(this problem) or any thing major at this time.
Thank you in advance.

---

### Post by MAFoElffen on 2023-09-14
Ubuntu Linux 14.04 LTS reached the end of its five-year LTS window on April 30th 2019.

Is this on ESM? ESM for 14.04 will end at April 2024.

What many will tell you here, is that members support active supported releases.

It has not had a security update in years... So what has changed that you know of?

---

### Post by Rubi1200 on 2023-09-15
Echoing what MAFoElffen just said, running outdated versions of Ubuntu puts your system at serious risk.

 > PC has crashed, so I don't want to do an OS upgrade on the laptop(this problem) or any thing major at this time

Depending on the hardware, it takes on average 20-40 minutes for a fresh install. Seems to me that is a small price to pay for security.

---

### Post by jaxom98 on 2023-09-15
Hello MaFoElffen and Rubi 1200, my PC has crashed and has put my data out of reach until the data recovery people get it back.The encryption key was taken down as well.
  So I am using an old laptop for now. All I am aiming for is to speed up bootup to normal time as currently I effectively have to do a double bootup to start laptop.

---

### Post by MAFoElffen on 2023-09-15
So is this laptop 32bit? Which would somewhat explain things as 18.04 Lubuntu was the last 32bit Ubuntu flavor available. Debian still has 32bit.

On this "laptop", that you are using temporarily while your PC is being repaired, do you have anything on it of importance? Meaning do you want to backup what is on it before trying to repair it, and try to fix it? And if it can not, are you willing to reinstall an OS?

Unfrotunately, the boot-repair script is only built for bionic as the oldest supported release. So you could not install the script, but you could boot it from a Boot-Repair LiveUSB, run the report and post the URL here to where it uploads to, for members to look at.

---

### Post by ajgreeny on 2023-09-16
> **jaxom98 said:**
> Hello MaFoElffen and Rubi 1200, my PC has crashed and has put my data out of reach until the data recovery people get it back.The encryption key was taken down as well.
  So I am using an old laptop for now. All I am aiming for is to speed up bootup to normal time as currently I effectively have to do a double bootup to start laptop.
What do you mean exactly by "the encryption  key was taken down"?

If encryption is involved and you have lost or forgotten the required key needed to get into the system I'm  afraid the data you want is probably gone forever; that, after all, is why we use encryption!
.

---

### Post by MAFoElffen on 2023-09-16
Reread Post #4. I read that differently.

The OP is talking about 2 different machines:
[LIST=1]
[*]A PC that was encrypted that crashed.
[*]A laptop that he is using in the meanwhile, while someone is trying to recover encrypted data on machine #1...
[/LIST]
 
Still awaiting responses to my questions.

---

### Post by yancek on 2023-09-17
This problem is specific to booting the most recent kernel (linux 3.13.0-170 generic), correct?  Has that kernel ever booted successfully?  If not, I'm not sure what changed or how it changed but the line below in your initial post indicated the system is looking for a specific partition UUID which does not exist.  Run blkid and check the output.  Does it show that UUID?  If not, it needs to be changed to the correct UUID, in grub.cfg and/or /etc/fstab.  If your other kernels are booting, I would check the grub.cfg entries first for the UUID on the latest kernel entry.  The UUID for each kernel version boot entry, should be the same 

> Alert!  /dev/disk/by-uuid/d6825235-a641-48e4-87e3-2e9bea133c26 does not exist.  Dropping to a shell!
 

If you look at the output you posted, the line above the UUID line states "Missing modules (cat  /proc/modules; ls /dev".  I expect that is in reference to kernel modules for the new kernel.  Since 14.04 has been out of support for years, how did you get the new kernel, archives?

Did the new kernel ever boot or is this a new problem with it?    I don't know why one kernel would have a different UUID than others by simply updating Grub.  Manually modifying it could be a problem with a simple typo but I don't know that happened.  Try getting the boot repair iso and running it with the Create BootInfo Summary option rather than trying repairs and post the link here.  The above questions and many more will be answered with that info.

---

### Post by MAFoElffen on 2023-09-17
"It could be" a few things.

Corrupted filesystem.
Broken Grub Boot loader.
Missing headers files for the kernel.
Failing hard disk.

The thing to do first would be to run The [Ubuntu 'system-info' script]("https://github.com/UbuntuForums/system-info") so we know what we are looking at, and which filesystem has "UUID=d6825235-a641-48e4-87e3-2e9bea133c26". Alternately if you do
```

lsblk -o name,label,size,fstype,UUID,PARTUUID,model

```
And posted the output within code tags, then we would at least have something to start with.

In Post #5 I asked for you t run the Boot-Info report from the Boot Repair disk. In Post #8 yancek also request to see that...

---

### Post by jaxom98 on 2023-09-18
Hello MAFoElffen, ajgreeny, and yancek, I was unexpectedly away and off line yesterday, sorry.

MAFoElffen re post 5, laptop is 64 bit running 64 bit OS. Also there is some new data I want to keep.

ajgreeny, post 6,I was using deja dup I had a multiple failure in the PC that corrupted the grub loader(dual boot Ubuntu20.04.6/ win 10) and when that was bypassed, the OS (ubuntu 20.04.6) was corrupted as well. The OS was reinstalled and it worked for 3 days then the grub had a major failure (missing files) and some plain language files on the data drive got corrupted as well, including, it seems,the encryption key to the backup files. This was beyond me,I  so sent the data drive to the experts , they are working on it now.

Yancek, I pulled the laptop out of storeage(textbook bootup) and clicked on update when the window came up and the trouble started on restart.

MAFoElffen Barely know how to drive termanil ,so keep it very simple.
    I ran the command alex@alex-X55A:~$ lsblk -o name,label,size,fstype,UUID,PARTUUID,model
lsblk: unknown colum: PARTUUID,model

I tried to boot into the laptop via a live ubuntu disk, and stuffed up. I set the boot order to dvd player first then Hdd 2nd. It worked on the first boot up, but failed on the 2nd bootup. When I checked the boot order the dvd was removed completely.
I was following a tutorial to boot from a live cd/dvd to download ppa files for boot repair. It would not open termanil so I shut down and got a different live dvd and found the cd/dvd boot option removed.  I shut then.

---

### Post by yancek on 2023-09-18
There is an explanation on how to update an EOL version of Ubuntu to get the archives at the link below.  Never tried it so...?  I would have expected errors on screen when you tried to do a simple update with your EOL Ubuntu.

[https://dev.to/chefgs/upgrading-an-end-of-life-eol-ubuntu-os-to-lts-version-3a36](https://dev.to/chefgs/upgrading-an-end-of-life-eol-ubuntu-os-to-lts-version-3a36)

Have you tried booting one of the old kernels which you say boot and checking the /boot/grub/grub.cfg file for the menuentries for the newest kernel?  Which UUID does it show?  If you run blkid, do you see output and does the UUID which you indicate in your initial post failed show in the output?

---

### Post by MAFoElffen on 2023-09-18
Dang. There is a difference in the options of 'lsblk' for the version installed for 14.04 LTS... I just spun up a 14.04.6 LTS VM to verify...Do
```

lsblk -o name,label,size,UUID,model

```
Please, when posting commands and output, post them within CODE Tags. Forum Policy. To edit your Post with the last reply to me, by going to "Edit Post" > "Go Advanced"... Select the Command and it's output with your mouse to highlight. Select the "#" icon to wrap the selected text with CODE Tags. When posting new posts, you can use the "Adv Reply" Editor with the expanded Editor Menu to use that "#" icon. Just trying to keep you out of trouble here on the Forum.

---

### Post by jaxom98 on 2023-09-18
MAFoElffen are the  code taags in the right place?  I have never used them before.

alex@alex-X55A:~$< lsblk -o name,label,size,UUID,model>
<NAME   LABEL   SIZE UUID MODEL>
<sda          698.7G      WDC WD7500BPVX-0>
<&#9500;&#9472;sda1         512M      >
<&#9500;&#9472;sda2       694.3G>      
<&#9492;--sda3         3.9G      >
<sr0           1024M      DVD-RW DVRTD11RS>
alex@alex-X55A:~$ 
alex@alex-X55A:~$ 
alex@alex-X55A:~$ 
alex@alex-X55A:~$ 
alex@alex-X55A:~$ 

yanck,
alex@alex-X55A:~$< /boot/grub/grub.cfg>
<bash: /boot/grub/grub.cfg: Permission denied>
alex@alex-X55A:~$ 
I checked user  accounts and alex is listed as administrator.  How  can admin be denied???

---

### Post by jaxom98 on 2023-09-18
I also got a pop up message saying "Internal error"  It refered to kernal 3.13.0-143 as being improperly shut down. I tried to copy and paste into tremanil, but it would not copy, then accidently uploaded to Canononical (error report). I will try for a screen shot next time.

---

### Post by yancek on 2023-09-19
>  I checked user  accounts and alex is listed as administrator.  How  can admin be denied??? 				

Only when using sudo does the user alex have sudo/admin rights so you can do:  sudo cat /boot/grub/grub.cfg   The cat command will open the file in the terminal so you can check but not modify anything.  After entering the command, you should be prompted for the user password (user alex).

When you are at a prompt in a terminal and see "alex@alex-X55A:~$", you are logged in as a user.  If your prompt shows "alex@alex-X55A:~#" you have root/sudo/admin rights. 

With regard to the CODE tags, when you are writing a response, mouse up to the icons above the text entry box.  The center row with the icon (#) is what you want.  Mouse over the icons to find out what they are.

You might try running a filesystem check on the device partitions as an improper shutdown can damage filesystems.

---

### Post by MAFoElffen on 2023-09-19
The "#" Icon shows up in the expanded toolbar of the Advanced Editor. You can get into the Advanced Editor by using the "Adv Reply" or "Go Advanced" buttons when posting... Or when Editing a post: "Ediit Post" > "Go Advanced".

Or you can add them manually like this:

[noparse]```

Your commands
and raw output
in here...

```[/noparse]

---

### Post by jaxom98 on 2023-09-20
Hello, yanck and MAFoElffen,  I tried to log in as administrator and was locked out.  I checked the pasword note book and verified I was using the correct password, I was. I then checked the administrator account and found the admin password character count does not match the note book admin character count by 1 character. I have tried all the combinations and failure.

Is there any way to bypass the admin account to make changes to the boot up?

---

### Post by jaxom98 on 2023-09-21
Please consider this thread closed. The admin lockout was the last straw.
I will tolerate the laptop double boot until the PC is repaired then  reinstall the laptop OS.

To yanck and MAFoElffen, thank you for your time.

---

### Post by MAFoElffen on 2023-09-21
You did not understand... Just because your useid is an admin account, does nto mean that it will execute a coomand as an administrator, until you tell it to. That is true for Linux, Unix and Windows. 

In Windows, you tell something to run as an Administrator by right clicking and using "Run as Administator" or opening the Cmd Windows Or PowerShell as an Administrator, then running commands in that window, as that Adminstrator. If for some reason you start something that needs admin permissions, it will sometimes pop open a Window that asks to you log in as an admin to okay it.

In Linux, to run a command with elevated admin permissions, you preface the command with the word "sudo", which will ask you to confirm with your password, then when confirmed, will execute that command with elevated permissions.

There is nothing wrong with that. That is just how things work.

If you can get to a Grub2 Boot menu on boot, then select "Advanced Options" > Select an earlier kernel with a rescue mode > Select chdsk... That will go through the entries in the /etc/fstab file, which all the filsesystem's associated with your system, check and fix those filesystems.

If that does not work, boot from a Live Installer media (DVD, USB, etc), select "try". Open a terminal session and do
```

sudo fsck /dev/sda2

```
As you can see from the results of what I asked you to post... They returned no UUID's, which should have been about at least 18 digits of hexadecimal numbers. Coupled with not being able to locate the filesystems from your install, that, to me, points to a suspected filesystem integrity problem. The above instructions should fix that.

Good luck.

---

