---
title: "Windows 7"
date: 2012-02-02
forum: New to Ubuntu
---

### Post by pqku on 2012-02-02
Hi,

I have the dvd to install windows 7.
Now on my laptop i have ubuntun 11.10. I want to install windows 7 and erase ubuntu at the same time. DO i have something special to do ?

Thank you

---

### Post by Dngrsone on 2012-02-02
No; Windows is pretty good about wiping out any other OS when installing.

---

### Post by ohadcn on 2012-02-02
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by QIII on 2012-02-02
You may find that Windows will barf and tell you there is not any room on the disk or that it is not formatted.  Your partitions are probably in a format alien to Windows.

If that happens, just stop your installation and use gparted from the Live CD to delete your partitions and make one large NTFS partition.  Windows should happily install.

---

### Post by Kixtosh on 2012-02-02
The only "special" thing you will have to do is make sure you boot from the DVD drive and not the HDD.

I've never had an issue installing any version of Windows, since W2K. Generally, the installation disk will easily identify the hard drive and its capacity, and will offer to format the drive to NTFS. That will consequently wipe out any installation of Ubuntu that may have been on there. It's quite easy to do and I have never experienced issues with the procedure.

Be prepared for the updates, after installation, to take quite a while ... and require a few reboots as well. For security reasons, do NOT use the default administrator account as your default user account. Make sure you set up at least one administrator account (that will not be used for daily operations), and one user account that does NOT have an administrator profile (that you will use 95% of the time, or more, for daily operations such as web browsing, office productivity, etc.). After that, you can set up a default user for start up, but it should be the user account, not the administrator account.

---

### Post by pqku on 2012-02-03
Thank you for you answers.
Why should i create and administrator apart ?

---

### Post by lisati on 2012-02-03
> **pqku said:**
> Thank you for you answers.
Why should i create and administrator apart ?

It's about *safety*. A "normal" user can't do all the same things that an administrator does, and this offers *one* level of protection.

---

### Post by Kixtosh on 2012-02-03
Yes, it's possibly the biggest mistake people make when using Windows:

[LIST]
[*]An administrator account profile is used by default after setup, and remains as such for the normal user account, so any security breaches immediately have access to the whole system.
[*]On Windows versions prior to Vista and W7, the user would make the same mistake (using and administrator profile for daily use, frequently with a weak password), but to compound the issue, an administrator user profile was also frequently (if not always, I'm not sure) present _by default_, with the user name "administrator", and a BLANK password!
[/LIST]
Windows Vista and 7 have improved this dramatically, but you still need to set up your default user profile and keep it separate from the main administrator profile. You can even have your computer or laptop boot directly to your user profile without requesting a password if you so choose, but make sure both profiles DO have a secure password! 

Prior to Vista, setting up a non-administrator user profile could be quite annoying, because so many things could NOT be done at all without an administrator profile, so even those who knew about the security concerns would ignore the necessity to keep the daily user profile separate from the main administrator profile. Even more frequently, the default profile with user name "administrator" was not known to be present, so it was never "locked down" with a proper user name change and secure password. Since Vista and W7, you can accomplish all but the most infrequent tasks without having an administrator profile just by using temporary password authentication, much like "sudo" in a Linux Terminal, or the root password.

Once you've set up your Windows, just make sure you have TWO profiles at a minimum, and that the profile you intend to use normally does not have administrator privileges.

---

### Post by Lalaith on 2012-02-03
All of you Ubuntu users (and I guess all Linux users in general) are such a good people. I am learning everyday important things even about Windows!!! 
(feeling lucky I stumbled with this thread)

pqku, why do you want to erase Ubuntu? Is it because the newbie experience didn't please you? If this is your case, there's plenty of people to help you here, as you can see :) Maybe it's a point to consider [dual boot]("https://help.ubuntu.com/community/WindowsDualBoot") and give Ubuntu another try...

---

### Post by pqku on 2012-02-03
> **Lalaith said:**
> All of you Ubuntu users (and I guess all Linux users in general) are such a good people. I am learning everyday important things even about Windows!!! 
(feeling lucky I stumbled with this thread)

pqku, why do you want to erase Ubuntu? Is it because the newbie experience didn't please you? If this is your case, there's plenty of people to help you here, as you can see :) Maybe it's a point to consider [dual boot]("https://help.ubuntu.com/community/WindowsDualBoot") and give Ubuntu another try...

Thank you all for your answer.

Lalaith, I erase Linux because I don't really need it. I mainly use this computer for skype, but skype is very ugly and have so many problem on linux. So windows 7 is more fit. And on my main computer is a mac , and i really enjoy the OS.
But of course linux is wonderful , if you need it !

---

### Post by d4m1r on 2012-02-03
> **pqku said:**
>  skype is very ugly and have so many problem on linux. 

Just my opinion but I'd say fixing the Skype issues on linux yourself is easier than having to install a whole new OS just to use Skype ;)

Google "native linux skype" and there should be topics on how to fix the common issues.

---

