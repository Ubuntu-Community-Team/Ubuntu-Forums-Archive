---
title: "Sharing email between two Tb instances in dual boot config (ubuntu &amp; win xp)"
date: 2014-05-02
forum: New to Ubuntu
---

### Post by Cbhihe on 2014-05-02
Good day,
Am a total newbie here. This is my first post (except for my small introductory post from 1 hour ago).
I am just about to install Ubuntu with Dual Boot on my Intel 9300 64bit enabled laptop running xp pro with 3GB of RAM. 
Before I do that I'd like to ask a few basic questions:

After burning my Ubuntu 14.04 (LTS) ISO on a disc, the 1st thing I want to do upon reboot is to partition my HD [COLOR="#000080"][COLOR="#B22222"]manually[/COLOR][/COLOR]. 
  What I have on a 200GB internal HD:
   - 50 GB NTFS for volume C: Win XP Pro system
   - 140 GB FAT32 for volume D:    ... contains all data and in particular my Tb email repositary
  What I want:
   - 35 GB NTFS for volume C: Win XP Pro OS   [COLOR="#0000FF"]<- resize[/COLOR]
   - 5 GB for Lx SWAP   [COLOR="#0000FF"]new[/COLOR]
   - 10 GB ext3 or ext4 for ~/home (2 Lx users)    [COLOR="#0000FF"]new[/COLOR]
   - 120 GB FAT32 for volume D: Data (only)    [COLOR="#0000FF"]<- resize[/COLOR]
   - 20 GB ext4 for Ubuntu OS    [COLOR="#0000FF"]new[/COLOR]

Q-1: Does the above partition scheme look reasonable ?
( I did not mention space for GRUB2, assuming the install will manage that by itself)

Q-2: I put 10GB aside for ~/home because I read somewhere that in case of distro upgrades, that will help me preserve most or all settings from the previous version, therefore smoothing the way. Is this correct ?

Q-3: [title of post] I want to use Mozilla Tb both in my XP Pro OS environment and in the Ubuntu OS envt. 
I also would like to share all the email between the two Tb instances, all 7GB of it.
That is, no matter whether I receive or send email in one or the other OS envt, I would like to see that reflected the next time I open TB in the other envt. Both Tb applications should share the same email repository on the HD.  Is it at all possible ?
That email is presently stored on D:\ and I could easily relocate it in a logical partition of its own (either FAT32 or NTFS) if necessary. I don't know that that would change something to anything though.
I have not found anything about this in the forum or elsewhere, although I am sure scores of people must have had the exact same idea before.

Thanks for any help. Cheers.

---

### Post by Elfy on 2014-05-02
- 5 GB for Lx SWAP new
- 10 GB ext3 or ext4 for ~/home (2 Lx users) new
- 20 GB ext4 for Ubuntu OS new

Leaving aside the windows filesystems - sort of ... 

If you are having the 120Gb data partition - wouldn't the main data for home would be there? Other than configs and cache - the majority of /home is going to be data

Now as far as the size for / goes - that really depends on what you intend to do tbh.  If you're not doing much out of the ordinary - then I'd suggest changing it. To be honest - I'd be inclined towards not having a seperate /home if you have data elsewhere - linux will read your windows filesystem. 

As far as thunderbird goes - I don't actually share mine between OS's types - BUT my thunderbird folder is in a partition I mount elsewhere - I edit the .ini file in /home/user/.thunderbird - and I DO share it between any of the various xubuntu installs I have running at any one time.

```
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=0
Path=/mnt/Spare/mozillatbird.default
```

You can see that I mount it in /mnt/Spare

---

### Post by Cbhihe on 2014-05-02
@ Elfy - thanks. :KS

Ok for sharing Tb email. I had no idea that it could be done at all between various instances of Tb under various Lx OS. 
I supposed those instances of Tb do not run simultaneously in your case. Or do they ?
I will report on whether it works for me between Win XP pro and Ubuntu 14.04. (I don't close this thread for that reason just yet).

You are right for /home of course. It will be in the FAT32  D:\ volume, for the exact reason you mention.
Instead of /home I should have written /tmp (2 Lx users). That will be in its own logical 10GB ext4 space 
I figure this should be enough for /tmp, as this machine will essentially be used :
- for conventional programming by two simultaneous users on a network.
- as mock server to render/test web sites being programmed, with mySql hooks.

Cheers.

---

### Post by Elfy on 2014-05-02
>  I supposed those instances of Tb do not run simultaneously in your case. Or do they ?No.

---

### Post by oldfred on 2014-05-02
I have had a shared Thunderbird with XP since about 2007. It was one of the first changes I did as my wife kept wanting to check email while I was learning Ubuntu. I also moved Firefox profile. Somewhat surprised over the years I have not had issues. I try to update versions about the same time in each install, but not always identical. And it has worked. 

Your TB is large, but then I regularly houseclean out deleted messages and do not save many. And anything with large attachments gets the attachment saved and email deleted.

In 2007 I used FAT32, but when NTFS driver became more reliable, I converted to NTFS for my shared data partition with update to 9.10. But  I added a new hard drive, so I had lots of space to move things around.
I still have Firefox & Thunderbird profiles in a shared NTFS partition but do not use XP anymore but have several Ubuntu installs all mounting the same profiles.

[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)

In a new install I find I have to start TB once so it creates default folder & profile, then edit/copy my standard profile to replace the new one it created. As Elfy posted you change is relative and path to match mount in Ubuntu. You do need to edit fstab with a permanent mount so it is there when you reboot.

Unless you can have a larger /home I would just keep /home inside / as one partition. You still have to backup data either way and if a new user easier to use. I used only / & swap with shared partition for years or until new drive gave me room to experiment.

---

### Post by Cbhihe on 2014-05-03
Thank you oldfred. 
It answers it all.
I am going to review all of the links you provide and apply the modifications as fit when my OS is up and running.
Cheers.

---

