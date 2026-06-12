---
title: "Can't Share a Ubuntu Folder with Windows 10"
date: 2022-07-27
forum: New to Ubuntu
---

### Post by pcman51 on 2022-07-27
Very Frustrated.. !!
I've tried everything, but likely missing the obvious.
I just reinstalled Ubuntu 22.04 lts so I have a clean install.
Install XRDP, Works perfectly.
Clicked Share a folder, Says it needed to install software, I Assume Samba ??
I Can even see all the "Workgroup" shared folders on my local network on the Ubuntu 22.04 and access them after entering User/PW
However on the Windows 10 PC side.. No Go ..

Goto one of 2 Windows 10 desktops and I see the Ubuntu Server, and I click on of the two two shared folders, 
I click the folder, it asks for User and PW, I enter the only user account I have on the Ubuntu Server, and it won't accept that.

I'm reluctant to start putting in a bunch of other commands via terminal, as I don't want to screw up this clean installation..

Please !! Can someone help..??

---

### Post by TheFu on 2022-07-27
[s][https://ubuntu.com/tutorials/install-and-configure-samba](https://ubuntu.com/tutorials/install-and-configure-samba) is the guide to setup a samba server on Ubuntu 22.04.[/s]  This will let Windows computers access storage on a Linux system.  Seems that tutorial is way, way, out of date. Sorry.  Here's the Ubuntu Server Guide: [https://ubuntu.com/server/docs/samba-introduction](https://ubuntu.com/server/docs/samba-introduction) samba introduction.  The meat seems to be here: [https://ubuntu.com/server/docs/samba-file-server](https://ubuntu.com/server/docs/samba-file-server)  ... since you likely aren't running AD or LDAP.

If you want to go the other way, use an Ubuntu Desktop to connect to a Windows network share, the instructions are different. I didn't google them, but suspect they aren't hard to find.

---

### Post by pcman51 on 2022-07-28
[B]Let me Clarify here...
[/B]
_I'm **NOT** using a **Ubuntu Server OS**_. I'm using **Ubuntu Desktop 22.04 OS**..

And **I have very minimal knowledge of Linux**. 

[B]Problem: I can't access a Shared Folder on my Ubuntu Desktop Computer.
I can See the Shared Ubuntu Folders on the Win 10 Desktop, but I Don't have privileges to access to shared folders (Won't accept the User/PW)
[/B]
Some say Ubuntu is easy. So far not the case for me, some say other distro's like Mint OS are easier for (First Time Window) Users? Unknown.
But it seems so far This Distro seems WAY Complicated and problematic. And I realize my Lack of knowledge is likely the problem. 
BTW: I'm a retired Network Admin, so I'm quite computer Network Savvy. For what that's worth. LoL :razz:

I did install OpenMediaVault 6 and it was Super Easy to share Files and do Backups. It worked Perfectly even on Windows Desktop Clients.
**But my goal is now to use Ubuntu 22.04 Desktop OS for:**
(1) RDP Terminal Services using XRDP (Working)
(2) Folder Sharing (**Not working**)
(3) Backups (**NA so far, until (2) is resolved**)

_**Present Setup:**_
1. OpenMediaServer 6 and it works perfectly on all my home devices, sharing files and folders on workstations, and Media devices.
2. Windows server 2016: Works perfectly sharing File and Folders on all devices including the new** Ubuntu Desktop 22.04 that can open the folders on the Windows Server. Yet not the other way around**.
3. Raspberry Pi acting as DNS server running PiHole. (Working and Stable)
4. Raspberry Pi Running Home Assistant.(working and Stable)
5. 2ea Windows 10 Workstations, and 3 Thin Client Devices. (All Stable and Working)

Reason I've listed many of my devices on my Network is because EVERYTHING Works fine EXCEPT UBUNTU Desktop 22.04 OS Computer.
I'm sure it's something to do with Samba? As the Folders show up on my Clients, but Windows doesn't accept the User/PW to the shared folder on Ubuntu.

SO the problem again is .. Windows 10 does not allow me to access to a Shared Folder on my Ubuntu Desktop OS..
I can see the Folders on the Network, but I don't have the privileges to access from Windows 10

Sorry for the rambling here. But I asked weeks ago and never got anywhere with this.
Thank you so very much in advance for anyone's Help..

---

### Post by pcman51 on 2022-07-28
Thanks for the suggestions. 
I looked at your link. Yes Maybe.
[https://ubuntu.com/server/docs/samba-file-server](https://ubuntu.com/server/docs/samba-file-server)

But why do I need to do this when Ubuntu Desktop 22.04 OS has the GUI commands on the desktop ??

---

### Post by pcman51 on 2022-07-28
Also the Ubuntu Desktop 22.04 OS finds my Windows Shared Folders on both my workstations and Windows Server just fine. Just not the other way around.

---

### Post by ActionParsnip on 2022-07-28
Did you run:
```

sudo apt update
sudo apt -y install samba

```

---

### Post by ActionParsnip on 2022-07-28
If you can SSH to the system then you have an SFTP server by default and Windows will be able to connect to that with all sorts of clients.

---

### Post by Morbius1 on 2022-07-28
> **pcman51 said:**
> Very Frustrated.. !!
...
I just reinstalled Ubuntu 22.04 lts so I have a clean install.
.
Clicked Share a folder, Says it needed to install software, I Assume Samba ??
...
Goto one of 2 Windows 10 desktops and I see the Ubuntu Server, and I click on of the two two shared folders, 
I click the folder, it asks for User and PW, I enter the only user account I have on the Ubuntu Server, and it won't accept that.

It appears you created what samba calls a "usershare" from your file manager and that you are using Ubuntu 22.04.

[1] Unlike Windows there are two passwords for your Linux user when using samba.

The password you use locally when you log into the server itself and the one you use for samba. You need to add your user to the samba password database, for example to add myself I would run:
```
sudo smbpasswd -a morbius
```

[2] Since you are creating shares from your file manager it is likely they are in your home folder because that is what it's designed to do.

Ubuntu 22.04 changed the permissions on your home folder such that only the owner of the home folder itself can access anything under it. This is true on the server itself and via samba.

There are multiple ways around this issue but if you are only accessing it with your own Linux user name it shouldn't be an issue.

Should you have further problems posting the output of the following commands will tell us how you are set up:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by TheFu on 2022-07-28
> **pcman51 said:**
> [B]Let me Clarify here...
[/B]
_I'm **NOT** using a **Ubuntu Server OS**_. I'm using **Ubuntu Desktop 22.04 OS**..

And **I have very minimal knowledge of Linux**. 
 

This is just background.  Since Morbius1 is here, follow those suggestions. He has a knack for samba and solving issues.

Samba is used for both desktops and servers.  The server instructions will work for desktop installs too.  Linux isn't like MSFT. It doesn't withhold anything just because you installed a GUI.  Everything is available and generally works, but not always.

"Server" is a generic term ... don't think if it as a piece of hardware.  In software, "server" implies there are "clients", at least 1.  For connections between 2 computers, 1 is the client and the other is the server - about 99.99% of the time (there are exceptions, but very few).

Usershares seem to cause multiple unintended issues.  We've seen that in these forums related to non-Samba/CIFS stuff.  You may want to rethink using that mode for a few years.

As for having a remote desktop, I'd encourage you NOT to use RDP, but x2go instead.  I ran a connection from a Win7 machine into a Linux desktop for a few years all day, every day, both over the LAN and over the internet, from 4 continents.  x2go is secure, solid, and performs 2-3x better than VNC or RDP solutions, IME.  Others have seen similar results - "like comparing night and day" is a common statement after they switch.  A few people post about x2go here with instructions, so if you choose to go that way, be certain to look those up. Get ssh working between the 2 systems before attempting x2go. It uses ssh-based authentication, so that is required anyway.

---

### Post by pcman51 on 2022-07-28
> **TheFu said:**
> 
As for having a remote desktop, I'd encourage you NOT to use RDP, but x2go instead.  I ran a connection from a Win7 machine into a Linux desktop for a few years all day, every day, both over the LAN and over the internet, from 4 continents.  x2go is secure, solid, and performs 2-3x better than VNC or RDP solutions, IME.  Others have seen similar results - "like comparing night and day" is a common statement after they switch.  A few people post about x2go here with instructions, so if you choose to go that way, be certain to look those up. Get ssh working between the 2 systems before attempting x2go. It uses ssh-based authentication, so that is required anyway.

Yes Indeed I understand the security risks. But this is only used on a Local Home Network.
And mostly for Home Automation in my own home.
I have 3ea Dell/Wyse Thin Clients that only support the legacy RDP. So in my case XRDP works really well for my needs.
If I find the time, I might one day consider flashing the tiny SSD on the Thin Clients with a more modern Thin Client Linux Distro. But for now things works great. 
My Biggest Goal is the retire my Windows 2016 Server that's EOL and no longer gets security updates, the Ubuntu 22.04 Server will hopefully make that happen.

---

### Post by TheFu on 2022-07-28
> **pcman51 said:**
> Yes Indeed I understand the security risks. But this is only used on a Local Home Network.
And mostly for Home Automation in my own home.
I have 3ea Dell/Wyse Thin Clients that only support the legacy RDP. So in my case XRDP works really well for my needs.
If I find the time, I might one day consider flashing the tiny SSD on the Thin Clients with a more modern Thin Client Linux Distro. But for now things works great. 
My Biggest Goal is the retire my Windows 2016 Server that's EOL and no longer gets security updates, the Ubuntu 22.04 Server will hopefully make that happen.

You are the first person I've heard of actually getting one of those remote RDP systems working.  Yes, then you have this handled, though you may need to disable some RDP security that MSFT added and it is likely Ubuntu followed with their default compile-time options for RDP-based tools.  OTOH, I don't know.  Haven't touched RDP in  very long time.

---

### Post by pcman51 on 2022-07-29
> **ActionParsnip said:**
> Did you run:
```

sudo apt update
sudo apt -y install samba

```

Yes . Says Samba is already installed with latest version

I can share  folder in GUI menu, and it shows up in my Windows Network PC, but won't me access my credentials to access the shared folder.
I've only created two user accounts.
1. The main user rdp1
2. the second rdp2
Both have admin rights according to the GUI menu.. I don't know how to check that by the Terminal.


I'M at a total loss here.. Any Help Please ..

---

### Post by pcman51 on 2022-07-29
> **pcman51 said:**
> Thanks for the suggestions. 
I looked at your link. Yes Maybe.
[https://ubuntu.com/server/docs/samba-file-server](https://ubuntu.com/server/docs/samba-file-server)


So Why does Ubuntu 22.04 boast to have GUI desktop menus , and now you and others are telling me that  the GUI interface doesn't work, 
And I must learn to use complicated Linux commands?

Of that's what it is ok. But Why ???

Trust me I'm willing to learn, but my 35 years in Windows Server or Desktop, everything is GUI menu driven. Even the most complex setups in a server environment.
I truly want to learn Ubuntu, But this is making me an typical example of why Windows users like myself struggle so with changing over.

All I simply want to do is Share a folder on Ubuntu to my entire network.
That should be pretty Basic.
And I have some 35 years experience in the Computer Field.

---

### Post by pcman51 on 2022-07-29
**So Why does Ubuntu 22.04 boast to have simple GUI desktop menus ?, But it doesn't work?  **
And others are telling me that  the GUI interface doesn't work, 
And I must learn to use complicated Linux commands? in a terminal environment?

[B]All I simply want to do is Share a folder on Ubuntu to my entire network.
That should be pretty Basic. The Menu says Share a Folder in your network. [/B]
It installed Samba, yet people are telling me to installed it again manually, and it says it's installed. 
I'm not perfect and totally willing to learn, and I have some many years experience in the Computer Field.

But Why the GUI interface in Ubuntu it doesn't work???

Trust  me I'm willing to learn, but my 35 years in Windows Server or Desktop,  everything is GUI menu driven. Even the most complex setups in a server  environment.
I truly want to learn Ubuntu, But this is making me an  typical example of why Windows users like myself struggle so with  changing over.

Thanks in Advance for any help. And sorry if I'm venting some frustration, but this is my second clean installation.

---

### Post by TheFu on 2022-07-29
Did you do what Morbius1 said in post #8 above?  It you don't follow instructions, how can anyone help?  Specifically, did you add a username to the samba-specific password file?  This is different from a Linux username which is used for console or ssh logins.

Linux isn't Windows.  If you think it is, you'll always be disappointed.  There are very different philosophical differences.  Linux runs on a $5 raspberry pi Zero. Linux runs on supercomputers with 100K nodes.

Flexibility means there are usually multiple ways to accomplish the same or similar results.  Not everyone uses the GUI very much. I don't. That's why I didn't say "point at X", "click on Y" 35 times, like happens with Windows instructions. 

BTW, nobody here works for Canonical/Ubuntu.  While we want to help, we don't know you or your expectations. The "Ubuntu Desktop Guide" probably has a section on sharing files with Windows.  The Desktop Guide you need is dependent on which GUI/DE you are using.

---

### Post by Morbius1 on 2022-07-30
For professionally developed and _supported_ desktop operating systems that use SMB by default ( Windows 10 /11 and MacOS ) it has historically never been easier to set up a simple Samba home server in Linux.

Install Samba:
```
sudo apt install samba
```
Make it so Windows can discover and connect to it by installing WS-Discovery:
```
sudo apt install wsdd
```
Make sure avahi is installed:
```
sudo apt install avahi-daemon
```

All that's left to do is create the share.

You can do that from your file manager if you want you just need to remember about the permissions of the home folder.

I've done this many times for many different users. It takes less time to set up that it did to write this post.


If you view all of that is far too complicated or if you think that is all too last century I would suggest you either:

*** Just run the Linux desktop as a desktop for a while until you get accustomed to how things work and the limitations one sees in it's use.

*** Or .. Don't use Linux.

---

### Post by pcman51 on 2022-07-30
```
 Should you have further problems posting the output of the following commands will tell us how you are set up:
testparm -s
```
```
net usershare info --long
```[/QUOTE]

[B]FYI:  The user is "rdp2"  and the shared folders are "Documents_home" , "Documents"
I did as you suggested "sudo smbpasswd -a rdp2"[/B]
**OK, Here's what testparm produced. Is all "Greek" to me LoL.**[COLOR=#26A269][B].

rdp1@server1[/B][/COLOR]:[COLOR=#12488B]**~**[/COLOR]$ testparm -s
Load smb config files from /etc/samba/smb.conf
Loaded services file OK.
Weak crypto is allowed

Server role: ROLE_STANDALONE

# Global parameters
[global]
    log file = /var/log/samba/log.%m
    logging = file
    map to guest = Bad User
    max log size = 1000
    obey pam restrictions = Yes
    pam password change = Yes
    panic action = /usr/share/samba/panic-action %d
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd program = /usr/bin/passwd %u
    server role = standalone server
    server string = %h server (Samba, Ubuntu)
    unix password sync = Yes
    usershare allow guests = Yes
    idmap config * : backend = tdb


[printers]
    browseable = No
    comment = All Printers
    create mask = 0700
    path = /var/spool/samba
    printable = Yes


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

---

### Post by pcman51 on 2022-07-30
> **TheFu said:**
> Did you do what Morbius1 said in post #8 above?  It you don't follow instructions, how can anyone help?  Specifically, did you add a username to the samba-specific password file?  This is different from a Linux username which is used for console or ssh logins.

Linux isn't Windows.  If you think it is, you'll always be disappointed.  There are very different philosophical differences.  Linux runs on a $5 raspberry pi Zero. Linux runs on supercomputers with 100K nodes.

Flexibility means there are usually multiple ways to accomplish the same or similar results.  Not everyone uses the GUI very much. I don't. That's why I didn't say "point at X", "click on Y" 35 times, like happens with Windows instructions. 

BTW, nobody here works for Canonical/Ubuntu.  While we want to help, we don't know you or your expectations. The "Ubuntu Desktop Guide" probably has a section on sharing files with Windows.  The Desktop Guide you need is dependent on which GUI/DE you are using.


Sorry if I sounded negative. This is all a learning curve for me , and while I have years of experience in Networking and Servers, I've got minimal with Linux. I have installed and running two Raspberry Pi Servers, and recently installed OpenMediaVault 6 and all went without a hitch.
I also realize it will likely turn out to be something stupidly simple that I missed called my learning curve. 
And doesn't help that I'm 71 years old. HaHa.. OK Let's make that my excuse.. LoL

But I'm very Grateful for everyone's help, and hopefully can assist others also in the future.

More notes are below.. Thanks so very much..

---

### Post by Morbius1 on 2022-07-30
You have no samba shares defined in smb.conf.

If you did create any they must be samba usershares. So post the output of this command:
```
net usershare info --long
```

---

### Post by pcman51 on 2022-07-30
> **ActionParsnip said:**
> Did you run:
```

sudo apt update
sudo apt -y install samba

```

Yes already tried this.. NO Go .. But Thanks

---

### Post by pcman51 on 2022-07-30
> **Morbius1 said:**
> You have no samba shares defined in smb.conf.

If you did create any they must be samba usershares. So post the output of this command:
```
net usershare info --long
```

[B]THANKS IN ADVANCE.. Here's the info you requested..

FYI:  The user is "rdp2"  and the shared folders are "Documents_home" , "Documents"
I did as you suggested "sudo smbpasswd -a rdp2"[/B]
**OK, Here's what testparm produced. Is all "Greek" to me LoL.**[COLOR=#26A269][B].

rdp1@server1[/B][/COLOR]:[COLOR=#12488B]**~**[/COLOR]$ testparm -s
Load smb config files from /etc/samba/smb.conf
Loaded services file OK.
Weak crypto is allowed

Server role: ROLE_STANDALONE

# Global parameters
[global]
    log file = /var/log/samba/log.%m
    logging = file
    map to guest = Bad User
    max log size = 1000
    obey pam restrictions = Yes
    pam password change = Yes
    panic action = /usr/share/samba/panic-action %d
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd program = /usr/bin/passwd %u
    server role = standalone server
    server string = %h server (Samba, Ubuntu)
    unix password sync = Yes
    usershare allow guests = Yes
    idmap config * : backend = tdb


[printers]
    browseable = No
    comment = All Printers
    create mask = 0700
    path = /var/spool/samba
    printable = Yes


[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers

---

### Post by pcman51 on 2022-07-30
> **ActionParsnip said:**
> Did you run:
```

sudo apt update
sudo apt -y install samba

```

**YES Thank You.. Samba is installed, But still not working..**

---

### Post by pcman51 on 2022-07-31
[FONT=arial]Hi [URL="https://ubuntuforums.org/member.php?u=982144"][COLOR=#000000]Morbius1

Just wanted to share my SUCCESS on the problem of Access to Ubuntu Shared folders on my Windows 10 PC.
I'm not even sure why this is working, as I'm just learning my way around here.

So I have 4 Hard Drives on my Ubuntu 22.04 Server

When I was on the desktop of the Ubuntu server via XRDP, I realized I could no longer access the drives shown in the Files App..
So I right clicked the folder to "UnMount" the one drive, then when I clicked the folder again it remounted it and I had access to it. 
Then I created a new folder named "WD1TBShare" and then right click it to bring up the GUI menu to enable Local Network Share.

Bingo !!!  I went to my Windows 10 PC and all the shared folder on the Ubuntu Server were now fully accessible with the Log in credentials.
So all 4 drives are fully accessible.

Now can someone explain why if I unmounted the Hard Drives and the Mounted them they now worked??

And secondly, Did I actually Fit It ??[/COLOR][/URL][/FONT][B][URL="https://ubuntuforums.org/member.php?u=982144"][COLOR=#000000]
[/COLOR][/URL][/B][URL="https://ubuntuforums.org/member.php?u=982144"]
[/URL][TABLE="class: ct-table pf-c-table pf-m-grid-md"]
[TR="class: content-level-0"]
[TD]ntfs filesystem[/TD]
[TD][/TD]
[TD="class: ct-text-align-right"]1.82 TiB[/TD]
[/TR]
[/TABLE]
[TABLE="class: ct-table pf-c-table pf-m-grid-md"]
[TR="class: content-level-0"]
[TD]/dev/sdc1[/TD]
[TD]ntfs filesystem[/TD]
[TD]/media/rdp1/80GB-Sata[/TD]
[TD="class: ct-text-align-right"]74.5 GiB[/TD]
[/TR]
[/TABLE]
[TABLE="class: ct-table pf-c-table pf-m-grid-md"]
[TR="class: content-level-0"]
[TD]vfat filesystem[/TD]
[TD][/TD]
[TD="class: ct-text-align-right"]932 GiB[/TD]
[/TR]
[/TABLE]

---

### Post by TheFu on 2022-07-31
There are 2 methods to mount storage. They are NOT the same.
A "real mount" (my term, not generally used) is the method were we put mount information into system files.  This allows full control and is normally performed via the /etc/fstab file entries.  1 line per mounted file system.  autofs can also be used to achieve similar results while still being a "real mount".  These are mounts that happen by the OS regardless of what a user does (unless the settings for the specific mount say to wait for a user to cause the mount).

Then there is the GUI method provided by any number of file managers.  These typically use some software from Gnome and don't touch the fstab.  These are temporary mounts and always require a user to point-n-click.  This means that anything dependent on a mount being available has to wait until some user manually causes the fake-mount to occur.  Additionally, these fake-mounts are typically 20-30% slower.

In short, use real mounts whenever something is important.  Use fake mounts purely for convenience, understanding the limitations.

BTW, unless a physical device will be directly connected to a Windows computer, it is best to use a native Linux file system, not NTFS, exFAT, or FAT32.  Windows people seldom know much about file systems.  There are many (perhaps too many) available in Linux.  The main reason to use Linux file systems is for their native permissions support. Many tools need that and expect it.  The Windows file system can be tricked into supporting those things, slightly, through manual mount options.  Regardless, chown and chmod will never work with NTFS, exFAT, or FAT32 file systems.  Of course, the settings are for all files inside the file system, since this is a trick.  For storage that will be shared over a network, there it ZERO reason to leave it as NTFS.

Wikipedia has a few articles which list file system features. It is easily found. There is a table.  The overview is the use ext4 on SSD or HDD partitions unless you have a specific need for some other file system.  For slower flash storage, Linux has f2fs, which is sorta like exFAT in the purpose, but not as widely supported. f2fs - "flash friendly file system".  Part of that friendliness is that it is not journaled to reduce writes. That's good and bad.  All modern file systems use journals to limit corruption. It is a good thing.  NTFS is journaled, ext3/4, ZFS, btrfs, xfs, which are the most popular file systems are all journaled. There are more.  Journaling is good, for non-flash storage media where we don't worry about write count limits.

If you'd like help setting up real mounts, ask.  Post the output from these 2 commands:
```
sudo fdisk -l
lsblk -e 7 -o name,size,type,fstype,mountpoint,uuid
```
along with where  you'd like each to be mounted.  Adding 3 lines to the fstab is all that is needed and running 1 command, 1 time. After that point, those file systems will be mounted at boot.

---

### Post by pcman51 on 2022-07-31
> **TheFu said:**
> There are 2 methods to mount storage. They are NOT the same.

If you'd like help setting up real mounts, ask.  Post the output from these 2 commands:
```
sudo fdisk -l
lsblk -e 7 -o name,size,type,fstype,mountpoint,uuid
```
along with where  you'd like each to be mounted.  Adding 3 lines to the fstab is all that is needed and running 1 command, 1 time. After that point, those file systems will be mounted at boot.

Thank you here's the resuts you requested. Also read my other notes below to see more.

> rdp2@server1:~$ lsblk -e 7 -o name,size,type,fstype,mountpoint,uuid

NAME      SIZE TYPE FSTYPE MOUNTPOINT                  UUID
sda     111.8G disk                                    
&#9500;&#9472;sda1      1M part                                    
&#9500;&#9472;sda2    513M part vfat   /boot/efi                   EB0D-0393
&#9492;&#9472;sda3  111.3G part ext4   /                           f0943d0e-34c9-4962-a4d5-af17124d2c9d
sdb     931.5G disk                                    
&#9492;&#9472;sdb1  931.5G part vfat   /media/rdp2/WD1TBHardDr     FACB-0886
sdc      74.5G disk                                    
&#9500;&#9472;sdc1   74.5G part ntfs   /media/rdp1/80GB-Sata       60E616DD5EBAFAD0
&#9492;&#9472;sdc2 1023.5K part                                    
sdd       1.8T disk ntfs   /media/rdp2/2 TB Hard Drive 7A6A423D11A9D1D8


[SIZE=2][FONT=arial]**I found that the Mount/Unmount via the GUI File Manager is only Temporary**, and if I restart the Ubuntu Server the Shared folder no longer works, so I have to simply unmount and the remount if that makes sense?

So I am missing something, but delighted I'm making headway here, thanks to all your help.

 [/FONT][/SIZE][FONT=arial][URL="https://ubuntuforums.org/member.php?u=982144"][COLOR=#000000]> [SIZE=2]
When I was on the desktop of the Ubuntu server via XRDP, I realized I could no longer access the drives shown in the Files App..[/SIZE]
So I right clicked the folder to "UnMount" the one drive, then when I  clicked the folder again it remounted it and I had access to it. 
Then I created a new folder named "WD1TBShare" and then right click it to bring up the GUI menu to enable Local Network Share.

Bingo !!!  I went to my Windows 10 PC and all the shared folder on the  Ubuntu Server were now fully accessible with the Log in credentials.
So all 4 drives are fully accessible.
Now can someone explain why if I unmounted the Hard Drives and the Mounted them they now worked.

[/COLOR][/URL][/FONT][B][URL="https://ubuntuforums.org/member.php?u=982144"][COLOR=#000000]
[/COLOR][/URL][/B]

---

### Post by TheFu on 2022-08-01
Please edit the post above and replace the "quote-tags" with "code-tags", so the columns line up correctly.  I'll wait for that fix.  How? [Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code) explains.

I do see that the external storage isn't using native Linux file systems. That isn't good. It means you'll never be able to use chmod or chown on the files, so getting the permissions correct will never work except for dumb data files that you want everyone on the machines to have access.

---

### Post by pcman51 on 2022-08-01
> **TheFu said:**
> Please edit the post above and replace the "quote-tags" with "code-tags", so the columns line up correctly.  I'll wait for that fix.  How? [Https://ubuntuforums.org/misc.php?do=bbcode#code](Https://ubuntuforums.org/misc.php?do=bbcode#code) explains.

I do see that the external storage isn't using native Linux file systems. That isn't good. It means you'll never be able to use chmod or chown on the files, so getting the permissions correct will never work except for dumb data files that you want everyone on the machines to have access.

This code seems to be working. However I noticed if I reboot, the shares do not stay. Once I Unmount & ReMount by clicking the drive in the GUI it works again.
On testing in my house, I found that everything was accessible on Windows, and even on my TV's using android streaming box
I was also reading some one different formats. I just need it to be compatible with Windows, Linux, Android..

Thank You so very much for your assistance, and patients. 

I think this is what you want ?

> ```
rdp2@server1:~$ lsblk -e 7 -o name,size,type,fstype,mountpoint,uuid
NAME      SIZE TYPE FSTYPE MOUNTPOINT                  UUID
sda     111.8G disk                                    
&#9500;&#9472;sda1      1M part                                    
&#9500;&#9472;sda2    513M part vfat   /boot/efi                   EB0D-0393
&#9492;&#9472;sda3  111.3G part ext4   /                           f0943d0e-34c9-4962-a4d5-af17124d2c9d
sdb     931.5G disk                                    
&#9492;&#9472;sdb1  931.5G part vfat   /media/rdp2/WD1TBHardDr     FACB-0886
sdc      74.5G disk                                    
&#9500;&#9472;sdc1   74.5G part ntfs   /media/rdp1/80GB-Sata       60E616DD5EBAFAD0
&#9492;&#9472;sdc2 1023.5K part                                    
sdd       1.8T disk ntfs   /media/rdp2/2 TB Hard Drive 7A6A423D11A9D1D8


```

---

### Post by TheFu on 2022-08-01
Yes, code tags make terminal output have the correct columns. Much easier to read.

And where do you want each to be mounted?  They can be placed anywhere, though I'd strongly recommend against using anywhere under /home/ or /media/ ... those places can cause other issues, which are best avoided.  A mount point is what I'm asking for. This is an empty directory for each file system to be mounted.  

I use 
/d/D1
/d/D2
/d/D3
/TV
/Data/

but it is possible to mount anywhere that you need storage.  For example, I also mount specific file systems to 
```
Filesystem                                  Type  Size  Used Avail Use% Mounted on
/dev/mapper/istar--8TB--B-jellyfin_varlib   ext4   89G  6.8G   77G   9% /var/lib/jellyfin
/dev/mapper/istar--8TB--B-plex_varlib       ext4   89G   40G   44G  48% /var/lib/plexmediaserver
```
because those specific locations needed much more storage than I want to allocate to a typical /var/ file system.

Is that helpful?

So assuming I can't talk you into reformatting from NTFS to a useful file system, like ext4,  You'll want a line like this for the 80G SATA:
```
UUID=60E616DD5EBAFAD0   /d/80G-Sata  ntfs  windows_names,nodev,nosuid,noatime,async,big_writes,timeout=2,uid=1000,gid=1000,fmask=0002,dmask=0002      0    0
```
I assume you want the username with uid of 1000 and gid of 1000 to be the owner. If not, change those numbers to match the username/groupname (name or number is fine).  The trailing last two zeros are important. They control whether fsck is attempted, what order and if it should be parallelized.  NTFS cannot be fsck'd on Linux. The fmask and dmask are about file and directory permissions for every file in the file system. These options are kludges for non-Linux file systems and far from ideal.

You'll gonna have issues with sdd. because is doesn't have a partition table.  This is against standard best practices and many data recovery tools will not work at all if there isn't a partition table.  You really, really, should fix that.

Having spaces in the LABEL will cause hassles. While you can do it, just always quote it for any uses, it will be a hassle.  If those mount points shown above are caused by the partition LABEL, instead of mounting by UUID, you can mount using the unique LABEL. It must be unique.
```
LABEL=80GB-Sata  /mount/point  fs-type   mount options    0  0 
```
Is how that works.  I prefer mounting by label if it isn't an LVM-LV file system. Labels have better meaning for humans than useless device names or UUIDs.

To quote a LABEL that has spaces, 
```
LABEL="2 TB Hard Drive"  /mount/point  fs-type   mount options    0  0 
```
I'm assuming the gvfs mounts (GUI point-n-click mounting) has decided the mount location based on the LABEL. That is pretty common.

Inside the fstab file, there is usually a header that has the fields explained.  There are 6 fields. Spaces are the default separator, so each field cannot have spaces ... especially the options.  1 line for each mount.  There's no wrapping allowed.

To edit nearly all system files with just the sudoers and passwd file as exceptions, use the sudoedit command.
```
$ sudoedit /etc/fstab
```
and make the changes like I've shown.  vfat has slightly different options.  vfat can apply to fat32, fat12 and a few other file systems.  I don't have any exFAT storage here (personal political statement on my part), so I don't know if vfat applies to exfat file systems too.

Since you've posted the info for / (111.3G), I'd add that / really shouldn't be so large. About 40G is the largest that should be setup for the / partition on an expertly configured system. Storage allocations are mainly about future needs, security settings, backups, recovery, and OS upgrades.  The best practice is to have different file systems for logs, the OS, and user files ... that means at least 3 or 4 partitions are needed on most Linux systems.  But people are lazy and that includes Canonical.

Hope this is helpful.
Also, with the options I've provided, you'll want to ensure the storage is connected and powered before booting the OS. The timeout should make the boot continue if they aren't, but samba won't like that you are trying to share non-existent storage.

---

### Post by pcman51 on 2022-08-01
I am truly thankful for your time and patients with me. 

I'll have more time to digest all you posted out later today or tomorrow.
But just as the "Code Tags" took me like an hour, as I didn't fully understand how that worked. LoL

I'm still in a learning stage here on how the server will be setup.
* The 80GB HD will likely go away as it was only for testing, and a new 4TB drive will be added.

What I vision so far is this.
1. the 120GB SSD will have nothing else on it but the OS and Applications like, XRDP, Cockpit, and other apps I want to explore in the future.
2. Drive 2 will be the 1TB HD
3. Drive 3 will be the 2TB HD
4. Drive 4 will be a 4GB HD that I just purchased.
5. I will likely attach (on and off) several USB external Hard Drives mainly as single backup of the OS and other critical data, but not used after unless needed.

BTW: I figured out how to have the server go to "Standby" after a set time of none use, thus saving power.
* I'm now able to fully access the Server remotely (Locally), so now a headless server.
* XRDP works excellent and I'll be using up to 3ea Thin Clients using RDP, including a couple android devices.
* Cockpit is another nice way to access the server. I know there are others, but for now very nice.
* I'm using a WOL (Wake on Lan) apps on my Cell Phone, PC, even TV, when I need to Wake up the Server.
* Not sure how or why yet, but several Folders are now fully accessible by my various Media devices, and secure by User/PW. 

** My Next step is to have the server make daily backup from one drive to another. I think I'll be fine when that time comes.

In closing again thanks, I'll reply in detail once I've digested all you've share here. Thank Again

---

