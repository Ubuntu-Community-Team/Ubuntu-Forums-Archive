---
title: "[SOLVED] How to Share an Hardy Partition on a Windows LAN?"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by bettyhills on 2008-11-06
I installed Ubuntu Hardy Heron 8.04.1 onto a PC.  The Linux PC has an 80gb drive and a 10gb drive.  

There are several WinXP PCs in the building connected to each other on a LAN using Microsoft's home networking.  The network is behind a router and a software firewall.  Sharing is enabled.

I would like to share **just the 10gb drive** (partition) with the WinXP PCs. They should have read and write privileges. 
The XP machines should not see the 80gb drive.

The Ubuntu machine should not be able to see or read or write into the XP machines.

I _am_ an absolute beginner.  Can anyone tell me step-by-step how to make Ubuntu's 10gb drive available to the other Windows PCs on the home network?

Thank you in advance for any help.

---

### Post by stephanvaningen on 2008-11-06
You need to install samba to start with.
After that, it (of course) needs to be configured (done in /etc/share/samba/smb.conf or /etc/samba.smb.conf)...
--
I'm looking into the necessary conf-changes to do in this conf.-file ... I'll be back with more specifics about this...

---

### Post by Sarmacid on 2008-11-06
Yes, you have to configure samba server, check this for more info [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by stephanvaningen on 2008-11-06
> **Sarmacid said:**
> Yes, you have to configure samba server, check this for more info [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
He's right, but concidering your comment on 'absolute new' (or something): try these steps:

*(commands written here can be executed with Applications -> Accesories -> Terminal)*

1. This will show you the mounted drives:
 ```
sudo fdisk -l
```
Select the 10G-drive here and note the device name (/dev/sdxy where x=a,b,.. and y=1,2,..) - for your case: the smalles part is the 10G-disk (ignore the swap-line) - *possible name I'ld guess is /dev/sda2*

2. Do this command and write down the other /xx/yy-link next to the /dev/*sda2* (where sda2 is the ID you noted in the fdisk-part)

3. Now start editing the /etc/samba/smb.conf file:
(This results in editing the config-file with administration-privileges)
 ```
sudo gedit /etc/samba/smb.conf
```

4. Go to section [global] and add:
[global]
	workgroup = WORKGROUP
[*mysharename*] 
	comment = *My share description*
	path = ***/path-to-disk/***
	read only = no
	guest ok = yes

5. Re-start samba:
 /etc/init.d/samba restart

Can you tell me if this worked, of not: feedback on which step did not...

---

### Post by bettyhills on 2008-11-06
stephanvaningen, 

I followed your instructions as well as I could understand them. Hope I did not misinterpret.  I entered:

[global]
workgroup=MSHOME
[Public]
comment=My share description
path= /dev/sdb1
read only=no
guest ok=yes

Because the second HDD had two device names, I also tried:
[global]
workgroup=MSHOME
[Public]
comment=My share description
path= /dev/sdb1
path= /dev/sdb5
read only=no
guest ok=yes

In both instances the response was something like "Open permission denied.  Stopping daemons. Failed to kill 5967 - operation not permitted.  Failed to kill 5969 - operation not permitted.  Open permission denied."

Thank you for the assistance.

---

### Post by stephanvaningen on 2008-11-07
looking into it... Be back in a few minutes..

You may remove the line with the sdb5 to start with, because I presume that that will be the swap-partition.

---

### Post by bettyhills on 2008-11-07
Thank you for your help.  I was able to make the necessary changes using Terminal, gksudo nautilus, and sharing a folder on the drive from there.  (It would not let me share the whole drive.)

---

### Post by stephanvaningen on 2008-11-07
Oh, ok.
--
Sorry I did not come back immediately, shortly after my reply the website was down for hardware upgrades or something ("ubuntu-geek"-message?), and after that it was end of my break at work... :-/
--
Anyway: I did have time during that period to do another test and that was: doing *everything* via GUI/nautilus i.o. manually configuring smb.conf. What I did, and which worked well was:
[LIST]
[*]Completely un-installed samba
[*]Right-clicked on a folder which I selected to share
[*]The system itself suggested to install samba
[*]via the properties-screen of the folder (tab: Share) change these options
[*]I had only access from a Windows computer if I accessed the share, providing a userID/password of an existing user on the Linux-computer, but I did not switch-on 'Enable guest access' either, so that figures.
[/LIST]

---

### Post by bettyhills on 2008-11-08
I was wrong.  The sharing issue is not solved.  Thank you for all you have done to help me work this out.  

Between the changes you told me to make to smb.conf and  nautilus, I was able to access a directory I am calling "Public" on the Ubuntu 10gb HDD and transfer files to a WinXP PC via the LAN **one time** and thought the problem was solved.

Now, however, I can see the "Public on the server (Samba,Ubuntu)" in the list of network shares from Windows PCs, but cannot access the share without a password.  No password has been set so there is no password.

Back in Nautilus, permission for users to access without a password is grayed out.  Also, Nautilus tells me that I do not have permission to change options and to see my administrator.

You have been extremely generous.  The changes to smb.conf were critical.  Thank you for your time and kindness.

Any further ideas will be appreciated....

---

### Post by bettyhills on 2008-11-10
This is solved (partially), and for anyone else with a similar problem, here is the essence of the fix:

For reasons not part of this issue, my Ubuntu 8.04.1 PC had to be assigned a STATIC IP. After days more research, I learned that Network Manager in 8.04.1 cannot handle STATIC IPs. This is a _known bug_. 

I **upgraded to 8.10 Intrepid Ibex** using Update Manager.  It all went flawlessly in under an hour. It is now possible for the Ubuntu PC to create SHARES. The Ubuntu PC can see all the Windows PCs on the LAN.

WINDOWS - A few further steps are necessary:  In my case I found that Sharing must be enabled on each of the Windows PCs all the way down to the lowest directory I intend to use for transferring files onto an NTFS HDD. Also, permission to access the STATIC IP address was enabled in each Windows PC software firewall (Zone Alarm.)

UBUNTU - Use the Samba Config Utility (after insalling it via Synaptic Pkg Mgr), to set up Sharing on the Ubuntu PC.  System->Administration->Samba->Add Share->Properties->Basic:  Fill in the directory, fill in the sharename (checkmark both writable and visible), and make Access = Allow access to everyone.
Samba Users: your username
Server Settings:  Basic:  Workgroup = name of the windows workgroup.  Leave the description as it was filled in automatically.
Security:  Authentication mode = SHARE
Encryption = YES
Guest Account = your username

Then browse to the particular directory's Properties, and enable sharing again. 

All of these settings persist through a reboot *EXCEPT* "allow other users to write to this share".  This is likely an unsolved bug.

It is not perfect but at this point the machines see each other on the LAN and can trade files.

If you have a STATIC IP and cannot network with Windows PCs on your LAN, the issue is amost solved in the Intrepid Ibex update.  Read the 8.10 known issues to make sure you will not lose something else in the upgrade, and if not, go for it.

---

