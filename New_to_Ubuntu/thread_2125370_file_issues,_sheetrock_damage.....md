---
title: "file issues, sheetrock damage...."
date: 2013-03-13
forum: New to Ubuntu
---

### Post by alabamatoy on 2013-03-13
12.04 LTS.

OK, so I have created a new user (for my Domestic Supervisor).  She wants some stuff copied from her windows XP file share, which she gathered into a single folder.  So I dutifully open the "home folder" app and after futzing around I find /usr/home/wife/Desktop and I then open another "home folder" app and find the Windows stuff and attempt to copy.  It tells me no can do because Im not the owner.  I am the owner, I bought and paid for this bloody machine and I installed the bleeping Ubuntu, and I want the dad-ratted blankety blank directory copied with all its contents, NOW!!!!  I AM GOD ON THIS PC, understand, Ubuntu?  No, I didnt think you would.

So I try to do this same action through terminal with sudo and mkdir and cp and now it tells me that the folder, which I can clearly see on the home folder app, is not a directory (even though I created it with mkdir), so CP cannot copy to it.  Sorry about that hole in the sheetrock, dear, I'll fix it this weekend, you wanted our little home office repainted anyway, right?

SO....real simple, be gentle on the idiotic newb here, how do I copy a folder for my lovely bride from her windows share (which I can access) to the same folder on her Ubuntu desktop?

Rhetorical question:  Why is this so bloody difficult?  Why am I being told that Im not the owner, when I am logged in as admin under the account that installed the OS?  What obvious simple concept am I missing?  I want to learn how to think in Ubuntu so I dont have to ask all these stupid questions.

---

### Post by ManamiVixen on 2013-03-13
To answer you question of ownership. By default, the only true administrator in Linux is "root" Meaning outside of root, all users only have access to their home folder. The meaning of "administrator" for a typical Linux user is addition of your name to the Sudoers file. The Sudoers file gives a user privalidge to root commands and access to the system through your provided user account password. The reason for that is to make Linux more secure, if you were actually running as root all the time, it leaves your computer vunerable to attack, so by making all users use sudo, reduces that risk. Any typical user outside the sudoers file will not be able to do administrative stuff.

---

### Post by oldos2er on 2013-03-14
> **alabamatoy said:**
> So I try to do this same action through terminal with sudo and mkdir and cp and now it tells me that the folder, which I can clearly see on the home folder app, is not a directory

You can do this graphically with ```
gksudo nautilus
```

---

### Post by DuckHook on 2013-03-14
> **alabamatoy said:**
> ...  I am the owner, I bought and paid for this bloody machine and I installed the bleeping Ubuntu, and I want the dad-ratted blankety blank directory copied with all its contents, NOW!!!!  I AM GOD ON THIS PC, understand, Ubuntu?

You are confusing two senses of the word owner. You may have bought and paid for your box, but Ubuntu assumes that any one user (owner) would not want any other user (another owner) to peek into (much less modify) files for which they have no business accessing. Since this same behaviour is what makes it impossible for viruses to modify critical system files, those "restrictions" you are cursing are the same ones that make it unnecessary to install anti-virus bloatware in Linux.

Basically, your beloved boss can access her files, but you can't--not by default anyways. There are very simple ways to accommodate your requirements, but this involves a conscious decision on either her part or the system admin's part to permit such access. In general, the concept of permissions is central to Linux operations and is almost entirely missing in XP. This is the same reason that XP is malware paradise whereas Linux offers such lean pickings.

> SO....real simple, be gentle on the idiotic newb here, how do I copy a folder for my lovely bride from her windows share (which I can access) to the same folder on her Ubuntu desktop?

So... real simple: the way to copy the folder is to log out, then log back in as your wife, then create the directory, then copy. The act of logging out drops you as the current user (owner). Logging in as your wife makes her the current user (owner). Now, the creation of directory and subsequent copy can proceed because, as far as the system is concerned, the proper owner is properly messing around with files/directories which he/she is the only one allowed to mess with. Command line jockeys can use shortcuts to achieve this same result by openign up a terminal and doing:```
su new_user
```but this is just confusing to new users so I don't recommend it. The logout-log-back-in-as-new-user method is conceptually the easiest for new users to understand.

You may have created a subdirectory owned by root in your beloved's directory in your last attempt to copy the file. This subdirectory will cause problems and further confusion because it is not actually owned by your wife. If so, then delete that directory (you will need root privileges to delete because it was originally created by root-remember: no messing with directories you don't own). You can then create the directory properly, now logged in as wifey, thereby creating a directory whose owner is wifey.

> Rhetorical question:  Why is this so bloody difficult?  Why am I being told that Im not the owner, when I am logged in as admin under the account that installed the OS?  What obvious simple concept am I missing?  I want to learn how to think in Ubuntu so I dont have to ask all these stupid questions.

It isn't difficult. However, it does require you to think in a different way and with far more respect for security than that for which XP ever gave a tinker's hoot. Linux is basically saying this: for the sake of safety and security, it does not assume that the person installing the OS is god. Instead, it assumes that you want to be god if and only if you expressly say you do, and even then, only for a 15 minute interval sufficient to do your god-thing. Therefore, every god-commandment must be prefaced with "sudo" (or gksudo, for graphical apps), absent which you are not god but just ordinary everyday Joe User who has no privilege to monkey around with any directory but his own.

I strongly encourage you to read [this]("https://wiki.ubuntu.com/BasicSecurity"), [this]("http://www.psychocats.net/ubuntu/security") and [this]("https://sites.google.com/site/easylinuxtipsproject/security"). They are wonderful primers about Ubuntu security. Especially important are the sections on ownership and privileges.

---

### Post by Cheesemill on 2013-03-14
> **DuckHook said:**
> 
Basically, your beloved boss can access her files, but you can't--not by default anyways.

Actually you can.

By default a Ubuntu installation gives all users home directories 755 permissions, which means that any user can read any other users files.

---

### Post by DuckHook on 2013-03-14
> **Cheesemill said:**
> Actually you can.

By default a Ubuntu installation gives all users home directories 755 permissions, which means that any user can read any other users files.

I appreciate such niceties, but this is confusing to new users. They want to know why they can't fiddle with others' files. If you want to point out 755 permissions, you need to also explain what this means, in layman's terms. I agree with your correction, though.

---

### Post by alabamatoy on 2013-03-14
> **oldos2er said:**
> You can do this graphically with ```
gksudo nautilus
```

This produces a dialog box that says "Nautilus could not create the required folder "/root/.config/nautilus <linebreak> Before running Nautilus, please create the following folder, or set permissions such that Nautilus can create it."

This is where Microsoft has it all over Linux.  "following folder"?  There is nothing following.  And I have no idea how to "set permissions such that Nautilus can create it".  But I think this sudo file explorer is probably exactly what I need.  So how do I fix this new problem?  :-)

> **DuckHook said:**
> So... real simple: the way to copy the folder  is to log out, then log back in as your wife, then create the directory,  then copy.


This doesnt work, because under her  account, the MS Windows partition is not visible or accessible.  Maybe  what I need is a /home/shared or something where all the users of this  box can access and share files.  That might work...

> **DuckHook said:**
> I appreciate such niceties, but this is  confusing to new users. They want to know why they can't fiddle with  others' files. If you want to point out 755 permissions, you need to  also explain what this means, in layman's terms. I agree with your  correction, though.

I understand chmod.  I learned on unix a long time ago before the  existence of GUIs.  So I can usually get around reasonably well in  terminal.  What I am not understanding, I guess, is how to run some app  in the GUI like filemanager as superuser.  I guess I feel like I need to  log in once as SU and do what I need to do as SU and then log out and  back in as me as regular user.  Maybe this "gksudo" will help me.  

> **DuckHook said:**
> I strongly encourage you to read [this]("https://wiki.ubuntu.com/BasicSecurity"), [this]("http://www.psychocats.net/ubuntu/security") and [this]("https://sites.google.com/site/easylinuxtipsproject/security"). They are wonderful primers about Ubuntu security. Especially important are the sections on ownership and privileges.

Thanks,  this is what Im after - some reading to understand the concepts so I dont have  to act the fool on this forum and pester yall all the time with  elementary questions.

Now how do I fix the Nautilus issue?

---

### Post by ManamiVixen on 2013-03-14
Try "sudo -i nautilus" instead.

---

### Post by QIII on 2013-03-14
Use gksudo with graphical applications.

---

### Post by ManamiVixen on 2013-03-14
gksudo dosen't work for him. It crashes Nautilus. I've personally never had an issue with sudo -i for GTK apps.

---

### Post by QIII on 2013-03-14
Then gksudo should be addressed.  sudo alone with graphical apps can wreak havok with file permissions in some circumstances.

---

### Post by alabamatoy on 2013-03-14
> **ManamiVixen said:**
> Try "sudo -i nautilus" instead.

```
doc@upstairsPC-Linux:~$ sudo -i nautilus
Initializing nautilus-gdu extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

```

Enable user sharing?

---

### Post by ManamiVixen on 2013-03-14
Thats an ok error. Ubuntu dosen't have Samba installed by default and Nautilus was just pointing it out.

---

### Post by ManamiVixen on 2013-03-14
But as QII stated, don't use sudo -i, I use it cause I know how to change the permissions when needed. Then again, it isn't that hard. Just right click a file or folder and it lists the permissions right there. 

Instead do:
sudo mkdir /root/.config/nautilus

then:
gksudo nautilus

---

### Post by DuckHook on 2013-03-14
> **alabamatoy said:**
> This produces a dialog box that says "Nautilus could not create the required folder "/root/.config/nautilus <linebreak> Before running Nautilus, please create the following folder, or set permissions such that Nautilus can create it."

This is where Microsoft has it all over Linux. "following folder"? There is nothing following. And I have no idea how to "set permissions such that Nautilus can create it". But I think this sudo file explorer is probably exactly what I need. So how do I fix this new problem?

I agree with you that Linux error messages are often very obscure and frustrating. The error message should have simply omitted the word "following". It is referring to the /root/.config/nautilus folder. For what it's worth, I also find Windows error messages just as obscure and frustrating, but that's neither here nor there. I believe what is happening here is that trying to run nautilus (which is the file manager) as root requires a root user config directory. This has also happened to me in some installs, but absence of this directory has never prevented nautilus from launching, but only from storing anything like your preferences for your next use. In any case, you can create one by doing:```
sudo mkdir /root/.config/nautilus
```

> This doesnt work, because under her account, the MS Windows partition is not visible or accessible. Maybe what I need is a /home/shared or something where all the users of this box can access and share files. That might work...

How are you mounting the NTFS partition? Assuming that you are dual booting, [here]("https://help.ubuntu.com/community/MountingWindowsPartitions") are the instructions for mounting your NTFS partition so that it is accessible to all users at boot. If your Ubuntu is a WUBI install, I'm not familiar enough with WUBI to advise you.

> ...this is what Im after - some reading to understand the concepts...

[Here]("https://help.ubuntu.com/community/ExternalGuides") is a megasite linking to many resources for Ubuntu and Linux.

---

### Post by alabamatoy on 2013-03-16
> **DuckHook said:**
>  In any case, you can create one by doing:```
sudo mkdir /root/.config/nautilus
```

When I run that I get : "mkdir: cannot create directory `/root/.config/nautilus': File exists" Yet every time I run nautilus, I get the same error.  Ubuntu is quite frustrating....

[QUOTE=DuckHook;12558104]How are you mounting the NTFS partition? Assuming that you are dual booting, [here]("https://help.ubuntu.com/community/MountingWindowsPartitions") are the instructions for mounting your NTFS partition so that it is accessible to all users at boot. If your Ubuntu is a WUBI install, I'm not familiar enough with WUBI to advise you.  I have no idea how the NTFS partition is mounted, its all whatever the default Ubuntu setup configured it to be.

I dont know what a "wubi" is, but I will do some reading and searching on that link.  Thanks!

I still cannot copy the folder to my wife's desktop.  I have spent an hour or more already chasing this trivial, simple action.  It would have been 15 seconds in MS Windows - open file manager, edit copy and navigate to destination folder and click paste.  Im not liking Ubuntu thus far, or else there is a major obvious concept Im not getting etc.  

I have tried opening two Nautilus windows with sudo and the "copy to other window" is grayed out on both.  This is getting very old.  I dont want to be an Ubuntu or Linux expert, I want to be an Ubuntu USER.

---

### Post by alabamatoy on 2013-03-16
OK, so I log into Ubuntu under wife's account, open a terminal window, and attempt to run nautilus with sudo, and it tells me the password is wrong.  For heaven's sake, this is bloody ridiculous!!  Sudo should be sudo regardless of what user account its under.  Im hating Ubuntu so far. I open "system settings" and click on "user accounts" and there's virtually nothing there, I cannot allow SUDO under wife's account there, I cant do much of anything except change passwords.  Its all but useless.  I am very frustrated with this inscrutable operating system.  Im tired of trying to figure this out logically, because obviously, Ubuntu and I do not share any basis of same logic.  I cannot get the built-in NIC to work ( [http://ubuntuforums.org/showthread.php?t=2118634](http://ubuntuforums.org/showthread.php?t=2118634) ), I cannot get my printer to work ( [http://ubuntuforums.org/showthread.php?t=2125711](http://ubuntuforums.org/showthread.php?t=2125711) ), and now this.  If I dont make some progress pretty soon, Im gonna ditch Ubuntu for good.  Can you blame me?

I have a chemical engineering degree and a master in computers science, and Im a CISSP.  I have a pretty good understanding of coding, I manage some websites with ASP code base, purchasing integrated with Paypal etc etc and TCP/IP and IPv4 and IPv6 and all that stuff.  But this OS is killing me.  If I cant figure these simple problems out, how on earth can the Ubuntu developers expect the layman to figure it out and make use of this OS?  Someone needs to go back to the drawing board and start over.  Or else theres something inherently screwed up with this particular install.  

And now Im getting "application update manager has closed unexpectedly".  I click on "details" and I get a wonderful little spinning asterisk which just.....spins.  So I click on "hide details" and select "send an error report to help fix this problem" and click "relaunch" and the process starts over.  Ubuntu sux so far.

OK, rant is over, back to problem at hand.  Please tell me, how do I copy this folder from the windows share to a user's desktop, and ensure that the user has full rights to it?

---

### Post by steeldriver on 2013-03-16
Generally, with the default Ubuntu umasks, you need elevated privileges to **write to** somewhere that doesn't belong to you, but not to **read from** somewhere that does not belong to you. (Yes there are exceptions, such as reading root-owned files containing sensitive stuff like wireless credentials.) So, logged into your wife's account you should not need to use sudo to copy to her account from anywhere she can 'see' (i.e. has read permissions to).

FWIW 'sudo' always wants the password of the invoking user (i.e. in this case your wife's) - if your wife's account does not belong to the sudo group it simply wont work.

SUMMARY:

- copying FROM your account TO her account will require sudo (and you will probably need to change the ownership of the copied files after)

- copying TO your wife's account AS your wife: no sudo (nor gksudo), she just needs read permissions on the files she wants to copy, the copied files will become owned by her - MUCH EASIER

---

### Post by DuckHook on 2013-03-16
Firstly, an attempt to solve your immediate problem:

I suspect that you are now logging in under your wife's account and trying to sudo from there. Ubuntu won't let you do this because your wife is not starting out with admin privileges. Otherwise, it would be easy for some bad guy to just log in as a guest and gain sudo privileges as well. You need to do one of two things:

1. Do your sudo work from your own account (assuming that this was the account you originally set up), or
2. Give you wife admin privileges. This is a one-time procedure that will allow her to elevate to sudo privileges thereafter.

We will leave this to another time. Or you can research it on your own. At this point, let's just try to get your NTFS partition mounted permanently so that every user can see and use it. Here are the relevant steps from the link I gave you earlier:

1. Log in to your *own* account.
2. Make a backup copy of your fstab file by doing:```
sudo cp /etc/fstab /etc/fstab_old
```
3. Determine which NTFS partition you want to mount by doing:```
sudo blkid
```From previous link...> an example output from a computer setup with a Vista/Ubuntu dual-boot and shared NTFS data partition is shown here:

    /dev/sda1: LABEL="Recovery" UUID="B23613F43613B875" TYPE="ntfs" 
    /dev/sda2: LABEL="Windows" UUID="38CE9483CE943AD8" TYPE="ntfs" 
    /dev/sda3: LABEL="Data" UUID="519CB82E5888AD0F" TYPE="ntfs" 
    /dev/sda5: UUID="00d7d951-2a35-40fd-8e5d-411bb824ff3b" TYPE="swap" 
    /dev/sda6: LABEL="Ubuntu" UUID="6044b1d0-208e-4ab3-850d-03a92e1516fc" TYPE="ext4" 

The first three partitions, all NTFS, are the ones that concern us here. There are no FAT32 partitions. In this instance, all three NTFS partitions have partition labels, which makes it easier to identify the purpose of each. If your blkid output does not include partition labels, this means that the partitions do not have labels and you will have to determine which partition you wish to mount by another means. Of the three NTFS partitions, we are going to configure /etc/fstab with only the third, the Data partition.
4. Create the directory we want to use for mounting the NTFS partition:```
sudo mkdir /media/Data
```
5. Edit your fstab file by bringing up gedit in admin mode with:```
gksudo gedit /etc/fstab
```
6. Create this line at the end of the file, replacing the example UUID with the output you actually get from your own earlier blkid command:```
UUID=519CB82E5888AD0F  /media/Data  ntfs-3g  defaults,windows_names,locale=en_US.utf8  0 0
```...If locale is not US, then substitute proper locale.

7. Save and exit gedit. Reboot.

These instructions are simply lifted from the instructions previously linked. Every user should now be able to access the NTFS partition you have defined.

Secondly, some unsolicited advice:

Ubuntu is not for everyone. In your case, it might be best for you to stick with the OS that you know. And no one would blame you, even if they were stuck-up enough to think it their business in the first place. However, it should be noted that you are trying to mount a non-native file system onto a multi-user environment while preserving Linux security--a non-trivial exercise by any measure. Windows won't even mount non-native partitions like ext4, so the contrast to the "ease" of Windows is hollow.

Lastly, an observation:

Frustration is completely understandable. Trying to do complex things in Linux is a tough learning curve. Many of us have been through it and sympathize with you. However, coming on a forum of enthusiasts, all of whom are volunteering their time and knowledge, and then dissing their favourite OS is not the best way to ask for help. As already said, if Ubuntu is not for you, then feel free to delete it.

---

### Post by alabamatoy on 2013-03-17
> **DuckHook said:**
> Firstly, an attempt to solve your immediate problem:

I suspect that you are now logging in under your wife's account and trying to sudo from there. Ubuntu won't let you do this because your wife is not starting out with admin privileges. Otherwise, it would be easy for some bad guy to just log in as a guest and gain sudo privileges as well. 

I fixed this part, thanks.

> **DuckHook said:**
> 
You need to do one of two things:

1. Do your sudo work from your own account (assuming that this was the account you originally set up), or
2. Give you wife admin privileges. This is a one-time procedure that will allow her to elevate to sudo privileges thereafter.

Understood.  Conceptually, to me, administratot should be administrator.  But, as I am learning, its not.  One must not be administrator, but also sudo all the time.  I dont like this, I find it irritating and pointless, but I understand it and can live with it.

> **DuckHook said:**
> 1. Log in to your *own* account.
2. Make a backup copy of your fstab file by doing:```
sudo cp /etc/fstab /etc/fstab_old
```
3. Determine which NTFS partition you want to mount by doing:```
sudo blkid
```From previous link...
4. Create the directory we want to use for mounting the NTFS partition:```
sudo mkdir /media/Data
```
5. Edit your fstab file by bringing up gedit in admin mode with:```
gksudo gedit /etc/fstab
```
6. Create this line at the end of the file, replacing the example UUID with the output you actually get from your own earlier blkid command:```
UUID=519CB82E5888AD0F  /media/Data  ntfs-3g  defaults,windows_names,locale=en_US.utf8  0 0
```...If locale is not US, then substitute proper locale.
7. Save and exit gedit. Reboot.

Wow.

> **DuckHook said:**
> 
Lastly, an observation:

Frustration is completely understandable. Trying to do complex things in Linux is a tough learning curve. Many of us have been through it and sympathize with you. However, coming on a forum of enthusiasts, all of whom are volunteering their time and knowledge, and then dissing their favourite OS is not the best way to ask for help. As already said, if Ubuntu is not for you, then feel free to delete it.

You are correct, of course.  But I would think that a group of people who are volunteering to support "their favorite OS" would embrace my situation and think to themselves "wow, maybe its time to move beyond some of this arcane command line stuff, and give users some easy "click here" kind of tools.  For example, the partition access issue you kindly assisted me with above.  Is it unreasonable to expect a "make available to all users" in the GUI somewhere?

Like I said, I really didnt set out to LEARN Ubuntu, I set out to USE Ubuntu because of its reputation for security and stability.  What I have learned thus far is that intuitively simple things (copying a folder, setting up a printer, getting network functioning using remote desktop) are incredibly difficult to do for the beginner, even one who is pretty competent in general with computers and networks.  NOTHING thus far with my Ubuntu experience has been easy or simple.  With all due respect to the community (and I sincerely mean that) I would think this would be taken as something more than "dissing their favourite OS" when its coming from a sincere person simply trying to use the "favorite OS".

Thanks for the help, and I really, truly mean my "dissing" as constructive criticism.  I do not mean it as snide or destructive.

Thanks to all who have assisted and educated me thus far.  I will probably be asking more stupid questions.......

---

### Post by oldos2er on 2013-03-17
There are no stupid questions!

Your concerns are common coming from Windows users new to Linux. They are valid too, not saying they're not; but [Linux is not Windows]("http://linux.oneandoneis2.org/LNW.htm"), and is not intended to be a drop-in replacement for Windows--even a distro as friendly as Ubuntu. Concepts such as separation of the user and administrator accounts and the security model based on that are deeply rooted (pun intended!) in Linux's Unix roots, and it's doubtful they're going to change. Use of command line shell is similar, it's the lowest common denominator of both administrative tasks and system configuration. There are many GUI tools available to do many (but not all) of these tasks though.

I hope you will give Ubuntu a chance, I really believe it's a worthwhile OS to both learn and use.

---

### Post by DuckHook on 2013-03-17
> **alabamatoy said:**
> You are correct, of course. But I would think that a group of people who are volunteering to support "their favorite OS" would embrace my situation and think to themselves "wow, maybe its time to move beyond some of this arcane command line stuff, and give users some easy "click here" kind of tools.

I will be the first to agree with you that Linux is obscure, arcane, finnicky and intimidating. However, you must realize that the people on these forums are not developers. In fact, the developers rarely visit this forum. We may be enthusiasts, but have little if any input into the development of Ubuntu. So the idea that "its time to move beyond some of this arcane command line stuff, and give users some easy "click here" kind of tools" is a misapprehension about what powers we have to do anything about it.

> For example, the partition access issue you kindly assisted me with above. Is it unreasonable to expect a "make available to all users" in the GUI somewhere?

Oddly enough, this expectation is unreasonable in the following sense: unlike proprietary software, Linux is a volunteer community effort that evolves through code contributions from its volunteer base. In this communal development model, the hacker base contributes such coding themselves as they seek to fulfill their own needs. Unlike proprietary software, the source code for every single component is available for download straight from the repository. As one with an IT degree, you can add this functionality yourself. In my case, I could not code to save my life. Therefore, I am content (well... mostly) to adapt to the constraints of the OS because I have made the decision to avoid having to learn how to code.

I don't want to sound like a paragon of patience. I've [ranted]("http://ubuntuforums.org/showthread.php?t=2110447&p=12483668#post12483668") about the shortcomings of Ubuntu just as you have and was reminded by a moderator that my rant was pointless and counterproductive. He pointed me to the developers' site where I could affect the changes I was ranting about (gulp). That very effectively brought home to me what it was that I liked about Linux in the first place, and why just complaining about it was hypocritical of me.

> Like I said, I really didnt set out to LEARN Ubuntu, I set out to USE Ubuntu because of its reputation for security and stability.

It is impossible to use anything without learning. This is as true of Windows as it is of Ubuntu. The fact that Windows is prevalent means that people just take their sunk investment in their Windows learning for granted and want to port that learning to Linux with no further effort on their part, which is not only an unfair expectation, but itself creates all sorts of problems, mainly having to do with atrocious habits and awful security behaviour.

Ubuntu's reputation for security and stability is well-earned. But it is secure and stable for precisely the reasons you don't like: disabling admin account, sudo for everything, minimal permissions to everyone, treating every new user as a potential threat, requiring password to wipe your nose, etc. What's funny is that when I started, I took exactly the same exasperated stand you do "Why do I need sudo? Just give me root access dammit!" until I wiped out my entire root directory one day with a boneheaded deletion while logged in as root. I learned the value of sudo the hard way. Problem is, I don't know how to convey this sort of experience to new Windows users who have been lured into a lifetime of bad habits by the frankly horrific enablement philosophy of Windows so that they now think of the abnormal as normal and the unnatural as natural. See [this]("http://ubuntuforums.org/showthread.php?t=2120814&page=4&p=12536563#post12536563") thread.

> What I have learned thus far is that intuitively simple things (copying a folder, setting up a printer, getting network functioning using remote desktop) are incredibly difficult to do for the beginner

I might--just might--agree with you on printing and remote desktop, but your choice of copying this particular folder in fact serves as a counterexample to your position:

As difficult as you found it, at least it was possible to mount your NTFS partition and make it available to all users. The tools, though obscure, are already part of the standard Ubuntu install. By contrast, please describe, in the same detail as I have, how to mount an ext4 partition in Windows and make it available to all users. This is simply not possible in a default Windows installation. Windows can't even see non-native partitions, never mind read them. So, I disagree with your characterization of your particular "copying a folder" exercise as "intuitively simple". You are mischaracterizing the depth of the problem and misattributing the reasons for its difficulty. Ubuntu sees its native partitions with as much if not more ease than Windows. As a bonus, it can see non-native partitions, but not with the same ease. You have focused on the lack of ease and ignored the fact that it's a bonus.

> NOTHING thus far with my Ubuntu experience has been easy or simple.

This is more than a slight exaggeration. I suspect that your initial install went pretty smoothly. Your home directory was probably set up correctly right out of the box, and you were able to use all of the standard Ubuntu tools seamlessly and properly. Libreoffice likely launched ready to use, as did Gimp, Rhythmbox, Firefox, Thunderbird, and on and on. And here are a few areas where Ubuntu is far easier and simpler than Windows:

1. The installation process took 20 minutes from start to finish.
2. You didn't have to put up with activation codes, agreeing to intolerable EULAs, or generally being treated like the vendor is doing you a favour allowing you to use their precious OS.
3. You didn't have to configure any anti-virus, wait for interminable signature downloads, or put up with twenty minutes of disk thrashing as the anti-virus app sniffed through every one of your files.
4. You don't have to defrag your HDD every week just to get it back to a fraction of the speed it had at install.
5. You can adjust any configuration file using a simple text editor instead of having to wallow around in the guts of some registry that is more obscure, more fragile and more impenetrable than any Linux config file in creation.
6. You go to one repository to get most everything you need and don't have to hunt all over heck's half-acre to download stuff that you just pray isn't infested with trojans, spykits or malware.
7. Last but not least, you didn't have to pay for the privilege of being abused in any of the above ways.

> With all due respect to the community (and I sincerely mean that) I would think this would be taken as something more than "dissing their favourite OS" when its coming from a sincere person simply trying to use the "favorite OS".

As already said, your frustration is completely understandable and we sympathize. The dissing observation came from your comment that "Ubuntu sux". However, this is one user, at least, who understands how we can sometimes say things in the depths of frustration that would have been better phrased in calmer circumstances.

> Thanks for the help, and I really, truly mean my "dissing" as constructive criticism. I do not mean it as snide or destructive.

You don't come across as snide or destructive or I would have simply not bothered to help. Believe me, the vast majority of us who strive to help have walked in your shoes. I do confess that I repaired my share of sheet-rock when first starting out. We're on your side.

> Thanks to all who have assisted and educated me thus far. I will probably be asking more stupid questions.......

As oldos2er has already said, "There are no stupid questions". In fact, I encourage you to ask on these forums rather than trying to muddle through on your own. You will find that, despite its inevitable blemishes, one of the best things about Linux is the Linux community itself--always ready to help. I've never found another one like it.

...and I, in turn, really mean it when I say,
Good luck and Happy Ubuntuing!

---

