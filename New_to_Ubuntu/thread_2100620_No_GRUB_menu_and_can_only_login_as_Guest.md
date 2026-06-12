---
title: "No GRUB menu and can only login as Guest"
date: 2013-01-02
forum: New to Ubuntu
---

### Post by nmorst on 2013-01-02
Hi,  Need some help, much appreciated! I'll get right into it. The problem started when I couldn't connect to a wifi connection from Ubuntu as I am being prompted for a root password, which I don't have and can't get, as I can only log in as a guest, since ubuntu (12.04) does not accept my login details.  I'm a complete linux beginner so please bear with me. I recently installed ubuntu thru wubi on my (2nd hand) Asus eeePC (w/o cd-dvd drive), dual booting with win 7 starter. Install was flawless, and when starting up comp I get what I assume is the windows GRUB menu where I have 3 options: "windows 7", "ubuntu" or "windows memory diagnostic" (under "Tools"). If I choose "Ubuntu", a text appears on a black screen saying "mount: can't read proc/mounts: no such file or directory". Then the black screen is suddenly filled with paragraph symbols, before actually starting ubuntu.   When I get to the Ubuntu login screen I can only login with a "Guest Session". When I try the normal login and I input my username and password, I am just told that my password is invalid and that I should try again. I have already reinstalled ubuntu as I thought maybe I had mistyped my password or that caps lock was on. But indeed that wasn't the case. I simply can't enter ubuntu with the admin account.  I've searched for hours on ubuntu forums and have tried to boot into recovery mode so as to 'reset' my Ubuntu password from the terminal, by pressing (and sometimes holding) Esc or Shift or F6 or F2 or F9 on startup. This is after I have chosen Ubuntu from the windows GRUB menu. I also tried pressing esc and shift while in the windows GRUB menu but to no avail.  I can however access the terminal from ubuntu in the guest mode and from the login screen. When I try to log in that way it just tells me my password is invalid as well. I suppose my "root" problem is that I can't get to Ubuntu GRUB menu to apply any of the fixes I have seen on the forums to change password or reinstall drivers or to reinstall the MBR or GRUB settings...(?)  So just to sum up:  - Can't use wifi from guest access without authentication password, since I - Can't get authentication password through terminal as guest account is not allowed to - Can't enter admin account - Can't get access to Ubuntu GRUB menu with all the kernel and recovery mode options (only windows GRUB menu I reckon) so that I can reset password or update drivers on startup or whatever  I would very much like to be able to log into admin account! Not just to connect to Wifi obviously. Starting to get really frustrating! Would very much appreciate any help.   Cheers, N

---

### Post by grahammechanical on 2013-01-02
I am not sure if you understand things correctly. When installing Ubuntu by means of Wubi we run Ubuntu inside Windows as a kind of Windows application.

Secondly, unlike Windows we do not have an Administrator account. The password that we choose when we install Ubuntu is the administrator password. We run Ubuntu as a standard user then when we need administrator privileges Ubuntu asks us to authenticate. That is when we enter our password. Once the task is complete Ubuntu takes us back to standard user privileges.

There seem to be two issues here. The invalid password and the "mount: can't read proc/mounts: no such file or directory".

Here is a link to the Wubi mega thread. Something there may help.

[http://ubuntuforums.org/showthread.php?t=1639198]("http://ubuntuforums.org/showthread.php?t=1639198")

Regards.

---

### Post by nmorst on 2013-01-02
Thx for the swift reply.  > **grahammechanical said:**
> I am not sure if you understand things correctly. When installing Ubuntu by means of Wubi we run Ubuntu inside Windows as a kind of Windows application.  That is, there is no Ubuntu GRUB menu when having installed ubuntu with wubi? Cus when I start my comp I am given a choice of win7 or ubuntu.    > **grahammechanical said:**
> Secondly, unlike Windows we do not have an Administrator account. The password that we choose when we install Ubuntu is the administrator password. We run Ubuntu as a standard user then when we need administrator privileges Ubuntu asks us to authenticate. That is when we enter our password. Once the task is complete Ubuntu takes us back to standard user privileges.   But it seems I can only log in thru 'Guest session', where the normal login is trhu the 'standard session' then (where the install/admin passwd is required?).   Also, do you reckon this issue is related to the mount proc mounts error?  Thx

---

### Post by rambabup on 2013-02-10
Hi,

I too faced exactly same issue.

Let me explain the issue for my case:

wubi installer is 12.04 but ubuntu installed is 13.04.

grub menu shows only 2 options like this:
Windows 7
ubuntu

, after selecting ubuntu, while booting the error shows is:
mount: can't read '/proc/mounts' : no such file or directory

Major problem is that i can't login with the login details which i entered while installing wubi application. Only able to login to guest account. In this account too can't give my password for root. 

Probably root file system has not mounted in my PC. The installation i have choosen is C: drive itself, where windows is also installed, i will try uninstalling and install in a separate partition.

Another thing is i have n't found terminal option on guest account, i have worked on Linux environment previously but this one is looking strange to me. 

If i press shift+control+F1, tty1 opens but login details are failing, so i am forced to shut power to do further activities.

Please let me know if the problem is something other than i think.


I have attached my system information for the hardware details purpose.


Operating System
Name	Microsoft Windows 7 Home Premium Edition (64-bit)
Service Pack	Service Pack 1
Build Number	7601
DirectX Version	11
Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz (CPU:0)
Name	Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz
Cores	4
Threads	8
System Memory
Total Physical Memory	6.00 GB
Maximum Supported Memory	8.00 GB
Battery - Microsoft ACPI-Compliant Control Method Battery
Battery Name	Dell
Type	LION - Lithium Ion
Battery Serial Number	768
Hard Drive - TOSHIBA MK6461GSY
Vendor	Toshiba
Model Number	TOSHIBA MK6461GSY
Serial Number	51GJT3Q7T
Marketed Size	640.1 GB
Optical Drive - TSSTcorp DVD+-RW TS-L633J
Model Number	TSSTcorp DVD+/-RW TS-L633J
Drive Serial Number	R8126GMB614960
Firmware Revision	D500

Thanks,
rambabu

---

### Post by bcbc on 2013-02-10
Rambapup - if it installed 13.04 you should file a bug. [http://bugs.launchpad.net/wubi/+filebug](http://bugs.launchpad.net/wubi/+filebug)

---

### Post by jayeshdiwan on 2013-02-21
Hi friends,

M facing the same problem,couldn login as admin, cnt change root pswrd, bt quit relaxed as its the issue with 13.04.....please nebody who can solve dis problem.....
> **rambabup said:**
> Hi,

I too faced exactly same issue.

Let me explain the issue for my case:

wubi installer is 12.04 but ubuntu installed is 13.04.

grub menu shows only 2 options like this:
Windows 7
ubuntu

, after selecting ubuntu, while booting the error shows is:
mount: can't read '/proc/mounts' : no such file or directory

Major problem is that i can't login with the login details which i entered while installing wubi application. Only able to login to guest account. In this account too can't give my password for root. 

Probably root file system has not mounted in my PC. The installation i have choosen is C: drive itself, where windows is also installed, i will try uninstalling and install in a separate partition.

Another thing is i have n't found terminal option on guest account, i have worked on Linux environment previously but this one is looking strange to me. 

If i press shift+control+F1, tty1 opens but login details are failing, so i am forced to shut power to do further activities.

Please let me know if the problem is something other than i think.


I have attached my system information for the hardware details purpose.


Operating System
Name    Microsoft Windows 7 Home Premium Edition (64-bit)
Service Pack    Service Pack 1
Build Number    7601
DirectX Version    11
Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz (CPU:0)
Name    Intel(R) Core(TM) i7-2630QM CPU @ 2.00GHz
Cores    4
Threads    8
System Memory
Total Physical Memory    6.00 GB
Maximum Supported Memory    8.00 GB
Battery - Microsoft ACPI-Compliant Control Method Battery
Battery Name    Dell
Type    LION - Lithium Ion
Battery Serial Number    768
Hard Drive - TOSHIBA MK6461GSY
Vendor    Toshiba
Model Number    TOSHIBA MK6461GSY
Serial Number    51GJT3Q7T
Marketed Size    640.1 GB
Optical Drive - TSSTcorp DVD+-RW TS-L633J
Model Number    TSSTcorp DVD+/-RW TS-L633J
Drive Serial Number    R8126GMB614960
Firmware Revision    D500

Thanks,
rambabu

---

### Post by bcbc on 2013-02-21
> **jayeshdiwan said:**
> Hi friends,

M facing the same problem,couldn login as admin, cnt change root pswrd, bt quit relaxed as its the issue with 13.04.....please nebody who can solve dis problem.....

Hi jayeshdiwan
Please attach your log file from the %TEMP% directory. It will be called something like wubi-xx.xx-revxxx.log. (Or pastebin it and post the link).

Thanks

---

### Post by Dequan_Wade on 2013-09-01
After searching on Youtube and Wikis and other sources including Ubuntu's forum pages I have found no way of creating a account leaving me stuck with the two accounts "Login" and "Guest Session" I don't really know what Login is for but I attempted to put the account information that Wubi asked me to put in when installing and failed. When I go into Guest, I tried to make an account and entered the password I had set in when I insalled Ubuntu with Wubi but, still never worked out. I looked on Youtube on how to fix the  current issue I was having and always got the wrong results. I was hoping someone from this website can create a video for the issue and leave a link to the video please. As this problem continues I've gotten a bit annoyed and if there is no way in fixing it I'll have to completely uninstall Ubuntu and all it offers and continue using Windows I guess.

---

### Post by Jonathan Precise on 2013-09-01
Please, **DO NOT USE THE WINDOWS INSTALLER!!!!!** There are some reported bugs about not creating an account properly. This means only Guest can be used. **PLEASE UNINSTALL!!!!!!!!!!** Use the traditional dual-boot instead.

(You mentioned Win-7 Starter, which is usually for net-books. Please post how much disk space you have before carrying on, as lack of disk space could be an issue.)

Please note: Use the windows partition re-sizer to shrink the partition. Then use ubuntu to install to the free-space using the something else option (don't forget to make a swap partition for ubuntu)

---

