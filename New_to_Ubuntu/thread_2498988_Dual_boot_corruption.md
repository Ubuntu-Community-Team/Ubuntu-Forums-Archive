---
title: "Dual boot corruption"
date: 2024-07-06
forum: New to Ubuntu
---

### Post by win-refugee on 2024-07-06
Hello community.     Help!    ;-)

I have a brand new HP Envy laptop with Win11 Pro pre-installed, which means BitLocker encrypted drive on the 1 TB SSD. After the ESP partition, and the windows recovery partition, the main OS partition was about 850 GB.  Its has HP UEFI firmware, with FastBoot OFF and Secure Boot ON.  Because of BitLocker, i used Windows disc management to shrink the main partition to 128 GB, leaving the rest for the Linux installation to partition = 128 GB for linux OS & apps; the rest for /home.  I intend to share the /home partition between Windows and Linux.  

I installed Xubuntu_24.04.  I was successfully able to secure boot into either Windows or Xubuntu, and share the BitLocker protected Windows files with Linux (Thunar).  Then i tried out a LiveUSB version of Lubuntu_24.04. PowerDown on that trial hung.  I eventually recovered by holding down the laptop power button (long press).  After that Windows boot was OK, but Xubuntu would not boot properly.  

Selecting Xubuntu from the Grub 2.12 menu results in a blank screen which hangs forever (or at least 10 minutes). 
Selecting Xubuntu (advanced) from the Grub 2.12 menu, and then the "generic" option gives a little more info. It results in log screen, which prints 2 lines and then hangs.
loading Linux 6.8.0-36-generic ....
loading inital ramdisk ....

Selecting Xubuntu (advanced) from the Grub 2.12 menu, and then the "recovery" brings up another options menu.  I tried a few, and discovered that just selecting the 'resume' option allows the boot to complete. 

So i'm trying to debug why a clean boot is no longer achievable.  
I did an update of packages.  No joy.
I read through /var/log/boot.log.  I poured over the output of 'sudo journalctl'.  Nothing i could spot.  I did see a notice that the boot sector and its backup differ.  The log claims this was repaired. 

Anyone have a suggestion ?

---

### Post by tea for one on 2024-07-07
> **win-refugee said:**
> I installed Xubuntu_24.04.  I was successfully able to secure boot into either Windows or Xubuntu, and share the BitLocker protected Windows files with Linux (Thunar).  Then i tried out a LiveUSB version of Lubuntu_24.04. PowerDown on that trial hung.  I eventually recovered by holding down the laptop power button (long press).  After that Windows boot was OK, but Xubuntu would not boot properly. 
A hard shutdown can, sometimes, damage mounted filesystems.
Boot into a live "Try Ubuntu" session and check the filesystems with fsck.
I suspect that your ESP was still mounted when you used the power button.

---

### Post by Impavidus on 2024-07-07
> **tea for one said:**
> A hard shutdown can, sometimes, damage mounted filesystems.
Boot into a live "Try Ubuntu" session and check the filesystems with fsck.
I suspect that your ESP was still mounted when you used the power button.
It looks like that. In particular, as
> **win-refugee said:**
> I tried a few, and discovered that just selecting the 'resume' option allows the boot to complete.it looks like this resulted in a damaged graphics driver. Reinstalling kernels and drivers may help.

Also,> **win-refugee said:**
> ...  leaving the rest for the Linux installation to partition = 128 GB for  linux OS & apps; the rest for /home.  I intend to share the /home  partition between Windows and Linux.128GB for root is some overkill. Ubuntu wants more than it used to, in particular with all hose snaps (which I avoid), but by system is still happy with 32GB root, if which I only use half. /home must use a native Linux filesystem, typically ext4 these days, and Windows cannot access that. You may be able to get access from Windows using a third-party driver, but I wouldn't put too much confidence in that. And I expect Windows wants something similar to a home directory on an ntfs partition. You can however use a shared data partition. Just make it ntfs and don't expect Linux permissions to work there. Some people use it to store their web browser profile, email, documents.

---

### Post by grahammechanical on 2024-07-07
> Selecting Xubuntu from the Grub 2.12 menu results in a blank screen which hangs forever (or at least 10 minutes). 
Selecting Xubuntu (advanced) from the Grub 2.12 menu, and then the  "generic" option gives a little more info. It results in log screen,  which prints 2 lines and then hangs.
loading Linux 6.8.0-36-generic ....
loading inital ramdisk ....

Selecting Xubuntu (advanced) from the Grub 2.12 menu, and then the  "recovery" brings up another options menu.  I tried a few, and  discovered that just selecting the 'resume' option allows the boot to  complete. 


As fas as I understand things, loading Xubuntu using Advanced Options>Recovery>Resume will load a kernel to the desktop using a open source video driver instead of a proprietary video driver that was installed. I know of no other difference. Here is something you can try when at the recovery menu:

Select Network - that should establish an internet connection. Then select Root - That will get you a command line where you can run commands, such as

```
apt update
apt upgrade
dpkg
```

The command dpkg will fix broken packages. To get back to the recovery menu - type exit.

Then select resume and then try rebooting to load with the proprietary video driver.

Regards

---

### Post by win-refugee on 2024-07-09
Thanks to all who responded.
I tried fsck, both from the boot-advanced-recovery menu, and from a LiveUSB.  It reported just files and blocks/clusters.  No corruption.  
I tried apt update and upgrade.  Some out-of-date files, but made no difference to the problem. 
dpkq requires a package name.  i didn't know what package is the problem.  I used the package manager to search for 'video driver' packages and found a few.  Did a package re-install on them.  No impact.

So, in the end i bit the bullet and reinstalled Xubuntu from the LiveUSB.  In fact i did this several times, simplifying as debug was still unsuccessful.  I had some other problems that i thought were un-related.  But this process made suspect they are related.

In the end, i have Xubuntu installed on a single partition.  The last dialog in the installation has a "Restart" button.  Nothing about the USB stick.  So i hit that button and waited.  No indication of progress, and no message about removing the USB stick.  Laptop power still on.  So after about 5 minutes, i pulled out the stick and hit ENTER.  The first boot into the new installation then executed.

I entered by ADmin password at the login prompt, and was presented with a desktop.  i opened a terminal and executed the following 3 lines.
> sudo apt update 
> sudo apt upgrade
> sudo apt update
The first indicated 52 packages.  The second upgraded those packages. And the 3rd indicated 0 packages.

I then powered down (not restart).  After a minute, i powered on again.
This boot returned me to the condition i originally reported.  Boot Xubuntu hangs.  Boot  Xubuntu advanced generic hangs in initRam.  Boot Xubuntu advanced recovery resume gets me to the login screen.  But when i enter my admin password pauses for a few seconds, then blanks the screen, then presents me with the same dialog again.  Entering the password for a second time gets me in. 
Shortly thereafter, usually as i touch the panel to configure it, an error dialog pops up "Xubuntu encountered an internal error".  As i ask for details (and a few more password dialogs) it appears to relate to xfce-panel.

The system is functional, just a bit inconvenient - boot choice path, double authentication.  But clearly it is not fully healthy.  
Any ideas ?

---

### Post by tea for one on 2024-07-10
> **win-refugee said:**
> The system is functional, just a bit inconvenient - boot choice path, double authentication.  But clearly it is not fully healthy.  
Any ideas ?
Not booting cleanly must be frustrating...........

How about playing around with Windows 11 and/or UEFI settings?

_Windows Settings_
Disable Bitlocker
Disable Fast Start Up i.e. Windows is not hibernating

_UEFI Settings_ (if present)
Disable Secure Boot 
Disable Fast Boot  
Disable Legacy mode 
Disable the following (if present):-
TPM (Trusted Platform Module)
PTT (Platform Trust Technology)
FTPM (Firmware Trusted Platform Module)
TPT (Trust Platform Technology)
Lock UEFI BIOS Settings
Boot Order Lock

Enable Microsoft 3rd Party UEFI CA 

Previous forum posts have indicated that toggling on/off any and all of the above have improved the boot process.
Unfortunately, it's a matter of trial and error because each vendor has a unique perspective for UEFI settings.

---

### Post by win-refugee on 2024-07-10
> **tea for one said:**
> Not booting cleanly must be frustrating...........

How about playing around with Windows 11 and/or UEFI settings?

_Windows Settings_
Disable Bitlocker
Disable Fast Start Up i.e. Windows is not hibernating

_UEFI Settings_ (if present)
......
Previous forum posts have indicated that toggling on/off any and all of the above have improved the boot process.
Unfortunately, it's a matter of trial and error because each vendor has a unique perspective for UEFI settings.


Bit Locker should not be an issue.  The ESP partition wherein UEFI resides (and is shared between Linux and Windows)  is not encrypted. 
The Windows partition is not used by Linux - but i am able to mount and access it from the Thunar File Manager after entering its recovery key.

Fast Boot is already OFF.

I am not willing to operate with TPM OFF or Secure Boot OFF. 
Perhaps as a debugging experiment, but not as an operational solution. 
Given the threats today, just not something i'm willing to sacrifice.

After several more experiments, it seems the "internal errors" may be because i tried to save my panel configurations and restore them in the
new installation.  If i just manually re-perform all these panel configurations changes, those internal errors seem to go away.

I don't know where to go next.  Live with the inconvenience, vs experiment with other distros (probably with other desktops). 

Linux Mint XFCE 21.3 worked fine, except it could not find my wifi.  Likely version 22.beta will solve that problem, but will it just return me to these same Ubuntu 24.04 issues ?
Lubuntu worked great from the LiveUSB (but so did XUbuntu).  But its the same Ubuntu base so why would it be different ?  
MX Linux 23.3, with its AntiX boot process also had secure boot issues, and graphics driver problems.
Maybe Debian ?

Anyway, thanks for your thoughts.

---

### Post by win-refugee on 2024-07-12
Just an update.
Ubuntu published a security update today (0-0-38).   I updated, which ended with a message to restart the machine.  i did.
Problems gone!     The default Xubuntu GRUB selection now boots cleanly to a login screen.  I sign in with my password, without the dialog repeating.
Hurray!  A very nice experience.

A few hours later, i used the LightDM Greeter settings to change the login background.  When i restarted, both problems re-appeared.
It was great for a while.

My guess (thats all it is) is that some of the configuration files (not just code files) are getting caught up in the signature calculations. So as soon as i make a config change, the signature no longer matches on boot.  Somehow the "recovery" path is less strict, and allows me in despite the signature mismatch.  Guess i'll wait until the next security patch and try again.

---

### Post by TheFu on 2024-07-12
Might be helpful if you looked up the boot process for Linux to understand the different stages and why anything before actually logging in is different from everything after.

Also, there is no admin account.  You've simplified what is happening incorrectly and used an incorrect term.  By default the account made during installation is part of the sudo group.  Being a member of that normal, unix, group conveys the ability to access some files, like sudo.  Other users cannot.  If you like, you can always login as a user who isn't in the sudo group, say, second-user. then use **su - {first-user}** to change to the userid in the sudo group for administrative access, if you like.


What is 0-0-38? Don't look like a date to me.

Dualbooting is a mess.  I stopped doing that about 15 yrs ago when virtualization became excellent to allow running the multiple OSes on the same hardware concurrently. Using VMs is much more convenient too.  Plus, multiple OSes aren't fighting over control of the boot process or storage encryption.

---

### Post by win-refugee on 2024-07-12
> **TheFu said:**
> 
Might be helpful if you looked up the boot process for Linux to understand the different stages and why anything before actually logging in is different from everything after.


Do you have some links to suggest where i might read about that ?

Ubuntu-generic-0-0-38 was the security update? What i had installed was Ubuntu-generic-0-0-36.

> **TheFu said:**
> 
 Also, there is no admin account.  You've simplified what is happening incorrectly and used an incorrect term.  By default the account made during installation is part of the sudo group.  Being a member of that normal, unix, group conveys the ability to access some files, like sudo.  Other users cannot.  If you like, you can always login as a user who isn't in the sudo group, say, second-user. then use **su - {first-user}** to change to the userid in the sudo group for administrative access, if you like.


I understand about Linux users and groups, and permissions.  I'm not crazy about how Ubuntu has done it.  There is no 'root' user login nor home directory, but in essence 'root' is the PRIMARY user.  Files are owned by 'root' and there is a 'root' group with just that user.  I defined an Administration user as part of the install process.  Ubuntu docs say this first defined user has administration privileges.  That user belongs to the 'admin' group.  Sure enough, login as Admin and do 'sudo' and you can access many things owned by 'root'.  Logged in as this admin user, i created my user account.  It has its own username and password, its own /home/userA directory.  It belongs to the predefined 'users' group.  It can sudo to admin privileges. 

So what did i simplify incorrectly, and what term was incorrect ?

---

### Post by TheFu on 2024-07-12
> **win-refugee said:**
> Do you have some links to suggest where i might read about that ?
Web search tools will find them.  LDP.org is probably the best for generic information.

> **win-refugee said:**
> 
I understand about Linux users and groups, and permissions.  I'm not crazy about how Ubuntu has done it.  There is no 'root' user login nor home directory, but in essence 'root' is the PRIMARY user.  Files are owned by 'root' and there is a 'root' group with just that user.  I defined an Administration user as part of the install process.  Ubuntu docs say this first defined user has administration privileges.  That user belongs to the 'admin' group.  Sure enough, login as Admin and do 'sudo' and you can access many things owned by 'root'.  Logged in as this admin user, i created my user account.  It has its own username and password, its own /home/userA directory.  It belongs to the predefined 'users' group.  It can sudo to admin privileges. 

There certainly is a root user and a root HOME directory. They just aren't directly accessible, as in some other systems.  Logging in directly as root is prevented both local and remote.  GUI sessions cannot be started as root either. These are all security choices.  You are free do disagree about them, if you like.

The admin group is just there to allow permissions to files and directories that shouldn't be available to just any end user.  Standard Unix group and permissions. Nothing more. There's nothing special about "admin" or "administrator" or anything similar.  While "root" is often "special", it isn't strictly required as the name. That's a Linux thing, not anything special about Ubuntu.  And I haven't been active on a Unix system in so long that I wouldn't state it is optional there, but it was when I was a UNIX admin.  A few scripts might check that the username is "root", but that is a bug.  A uid of zero, 0, is what those scripts should be checking.

It is possible to change from using the admin or sudo Unix groups to using some other named groups, if you prefer. There's nothing special about the names or the uid/gid of those two groups, except that they are setup by default for a number of other tools in those config files.  There may be some lazy programs where the developer did hard code specific group membership for extra access, but I'd be surprised of that were true.  GUI programs often take shortcuts like that, because GUI programmers don't always really understand things. Their expertise is in making bloated code for point-n-click stuff, not understanding the deeper parts of the OS.

BTW, I capitalize Unix with specific meanings.
UNIX = commercial UNIX - like Solaris, AIX, HP-UX, Digital Unix, Irix, etc. al.
Unix = any UNIX-like OS, which includes BSD, Linux, AT&T UNIX, and all the other UNIX flavors.
Linux = anything that uses the Linux Kernel from Kernel.org. If I use that, it means I either don't know or am not certain if Unix or UNIX applies too.

It is sorta like how we use 
# to denote a root shell and
$ to denote a non-root shell.

Details matter.

THERE IS NO ADMIN USER that is tied to any specific name.  Also, HOME directories don't need to be in /home/{username} if you don't want that.  It is a Linux convention, but lots of places don't follow it for a number of reasons.  There is a Standards document for file systems and the layout for UNIX, Unix and Linux systems.  Recent versions of Linux do say /home/ is for non-root HOME directories.  I don't know why this restriction was put in place.  There's no mandated reason for it across all Linuxen, regardless of what Ubuntu Snap development team may think.  That's a problem for a different day.

Calling an account "Admin" doesn't make it so.  It is the group membership that matters.  One user with full admin rights can add other users with or without admin rights.  Your choice.  If admin rights happen to the 2nd and later users added to a system and you didn't specifically set those up, you either weren't paying attention or have a misconfigured system.  

sudo isn't just for elevating to root privilege. It can be used to change to any other user on the system and in many situations, when setting up a user to have specific sudo capabilities, they do not get root, but some other, usually a daemon uid, privileges for running specific commands with specific options.  For example, accessing config files for a web server often is limited to www-data, not root, so a webmaster wouldn't get generic sudo -to- root, but just sudo -to- www-data user privileges.  Lazy admins might allow the webmaster full sudo when it isn't necessary. That breaks the idea of least privilege needed to do their job.

Things that seem similar to how other non-Unix OSes do things, usually aren't the same at all.  It is easy to make assumptions based on knowledge from those other OSes and because most of the time, those ideas seem to fit, accept them as true, when they are not. It is a common issue.

Ubuntu, at the core, isn't any different than any other Linux OS.  They've made some customizations in the belief that some of those things are more secure or easier or aid in productivity.  If you don't like it, there are other OSes to pick from, including many Linux variants.  Or you can change the Ubuntu customizations to do what you like, but that is often more hassle than it is worth.

You are posting in the New user sub-forum here, so I've assumed you are new.  It usually takes a few years for all the subtle things in Unix-like OSes to become clearer and the genius in how things are setup to be seen. There is an elegance.  Just remember that there are only two types of things in Unix.  Files and processes.  Everything that doesn't show up in the system process table (use ps aux to see), those are files.  With that understanding, you can see why uids, gids, and permissions are so important.  They control all access.

---

