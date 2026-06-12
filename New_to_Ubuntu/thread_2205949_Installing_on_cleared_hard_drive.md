---
title: "Installing on cleared hard drive"
date: 2014-02-16
forum: New to Ubuntu
---

### Post by ashley6 on 2014-02-16
I have a computer running windows 8.  It wont accept my password anymore and after hours of talking with Microsoft I have decided to clear the hard drive.  I have tried to load my Ubuntu LiveCD but it wont load.  How hard will it be to install Ubuntu after I clear the hard drive, I am pretty computer knowledgeable.  I dont have anything on the computer worth saving.

---

### Post by Vladlenin5000 on 2014-02-16
The LiveCD not loading is unrelated with the state of the HDD. Once loaded and in the live session installing Ubuntu should be as easy as double-clicking install in the desktop and following the installation wizard. If you intend it to be the only OS in that computer just accept the first option in the step where it asks where to install it.
Now... Considering your computer came with Windows 8 preinstalled then it has a few more steps regarding UEFI that should be accounted for prior to running the live session and/or installation process: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

However - again - the LiveCD not loading is unrelated to the steps mentioned in the above link.

---

### Post by grahammechanical on 2014-02-16
The Ubuntu install process has an option to Use the Entire Disk that will wipe out everything already on the disk. That is how simple it is once you get the live session to run. You say the live session wont load. What error messages do you get? What happens. Wiping the hard drive will not solve the problem of the live session not loading. You should read this.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> 
[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.
[/LIST]


I am not sure if wiping the hard drive will remove the necessity of running the Ubuntu live session in EFI mode.

> [COLOR=#333333][FONT=Ubuntu]if Ubuntu is the only operating system on your computer, then it does not matter, you can install Ubuntu in EFI mode or not[/FONT][/COLOR]

> [COLOR=#333333][FONT=Ubuntu]Use a 64bit disk of Ubuntu[/FONT][/COLOR]

You do not even tell us what version of Ubuntu that you wish to install.

> [COLOR=#333333][FONT=Ubuntu]Set up your firmware (BIOS) to boot the disk in UEFI mode[/FONT][/COLOR]

Then

> 
[LIST]
[*=left]nothing special is required if you use the automatic installer of Ubuntu ("Install Ubuntu alongside others" or "Erase the disk and install Ubuntu"). Important: if you have a pre-installed Windows and you want to keep it, do not choose "Erase the disk and install Ubuntu".
[/LIST]


Regards.

---

### Post by Impavidus on 2014-02-16
The problem could be that secure boot and/or fast boot are still on. No experience with that myself though.

---

### Post by ashley6 on 2014-02-16
I cant access to turn off the FastStartup.  I tired system restore to a point 2 months ago but it still wont allow me to log in.  I have tried clearing the hard drive but it just said that I am missing a file partition.

---

### Post by bc.haynes on 2014-02-16
Please tell us more about your computer....Processor, RAM, Video card, etc.

---

### Post by bc.haynes on 2014-02-16
Do you know how to get into the BIOS settings?  Do you know what kind of BIOS you have?

---

### Post by ashley6 on 2014-02-16
CPU Celeron CPU 1037U, 1.8GHz, RAM 4096, System BIOS 1.2, running windows 8. I think I might have gotten a virus because no matter what I try I cant get it to accept a password.

---

### Post by bc.haynes on 2014-02-16
> Do you know how to get into the BIOS settings? Do you know what kind of BIOS you have? 
Is the BIOS AMI, Phoenix, or another brand?

---

### Post by ashley6 on 2014-02-16
I have no idea how to find out what type BIOS.

---

### Post by bc.haynes on 2014-02-16
Are you on another computer besides the one you want to erase?

---

### Post by bc.haynes on 2014-02-16
ok, I assume you are on another computer, right? If you are, reboot the one you want to fix and, as it boots up, keep pressing, tapping on the F2 key to see if that gets you into the BIOS.

---

### Post by ashley6 on 2014-02-16
It says that the system BIOS Version is 1.2 I dont know where to look for what type it is.

---

### Post by Vladlenin5000 on 2014-02-16
> **ashley6 said:**
> It says that the system BIOS Version is 1.2 I dont know where to look for what type it is.

Look for AMI, Phoenix, etc. word anywhere in the pages. It must be one of the known 'brands'...

(EDIT)

It might be easier just to tell us what brand/model of computer you have.

---

### Post by ashley6 on 2014-02-16
Nothing else listed with the BIOS information.  The Computer is a Toshiba Satellite C55-A5300.

---

### Post by Vladlenin5000 on 2014-02-16
Thanks.

Here's the specs: [http://www.toshiba.com/us/computers/laptops/satellite/C50/C55-A5300](http://www.toshiba.com/us/computers/laptops/satellite/C50/C55-A5300)
Experts, please dig in. :D

---

