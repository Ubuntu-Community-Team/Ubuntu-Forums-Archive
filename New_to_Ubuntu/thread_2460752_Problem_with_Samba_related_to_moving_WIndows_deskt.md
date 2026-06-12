---
title: "Problem with Samba related to moving WIndows desktop files to newly installed Ubuntu"
date: 2021-04-17
forum: New to Ubuntu
---

### Post by markb60000 on 2021-04-17
I am trying to set up the transfer of my Windows 10 desktop files to Ubuntu 0.04, which I just installed.

 
In doing so, I installed Samba, but did so incorrectly.  I tried to uninstall the program, but, as shown below, the delete was aborted.
Is there a way to delete Samba, or should I forget about the remnants of the installation, and use a program that does what Samba does?  Or should I use another method to move my Windows desktop documents to Ubuntu?  If so, what is the easiest way to do so?

Thanks,
Mark


```
mark@mark-HP-Notebook:~$ sudo apt-get remove --purge samba
Reading package lists... Done
Building dependency tree      
Reading state information... Done
The following packages were automatically installed and are no longer required:
  attr ibverbs-providers libcephfs2 libibverbs1 librados2 librdmacm1
  samba-vfs-modules tdb-tools
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  samba*
0 upgraded, 0 newly installed, 1 to remove and 6 not upgraded.
After this operation, 16.6 MB disk space will be freed.
Do you want to continue? [Y/n] Y
Abort.
mark@mark-HP-Notebook:~$ sudo apt-get autoremove --purge samba
Reading package lists... Done
Building dependency tree      
Reading state information... Done
The following packages will be REMOVED:
  attr* ibverbs-providers* libcephfs2* libibverbs1* librados2*
  librdmacm1* samba* samba-vfs-modules* tdb-tools*
0 upgraded, 0 newly installed, 9 to remove and 6 not upgraded.
After this operation, 35.8 MB disk space will be freed.
Do you want to continue? [Y/n] Y
Abort.
```

---

### Post by wildmanne39 on 2021-04-17
Moved to New to Ubuntu sub-forum.

---

### Post by Morbius1 on 2021-04-18
It's not clear how one installs samba "incorrectly". You may have configured it incorrectly but there is a way to restore the default settings without removing or purging everything samba.

Is it running? Run the following command to determine it's state:
```
sudo service smbd status
```
If it is running run this command to see how it is set up:
```
testparm -s
```
Or worst case see if you still have a smb.conf file:
```
 cat /etc/samba/smb.conf
```

---

### Post by CelticWarrior on 2021-04-18
Are Windows and Ubuntu in different machines in the same network or is it a dual-boot?

---

### Post by ipv2 on 2021-04-20
> **markb60000 said:**
> another method to move my Windows desktop documents to Ubuntu

1. on the windows machine share a folder / folders & grant read / write access.

2. on the ubuntu machine : files > other locations > in the enter server address box = smb://ipaddressofwindowsmachine > connect > pop-up window for authorization > shared folders from windows.

note : you do not need samba for this method.

---

### Post by CelticWarrior on 2021-04-20
> **ipv2 said:**
> 1. on the windows machine share a folder / folders & grant read / write access.

2. on the ubuntu machine : files > other locations > in the enter server address box = smb://ipaddressofwindowsmachine > connect > pop-up window for authorization > shared folders from windows.

note : you do not need samba for this method.

Please note it *does *need Samba and it'll be be installed on demand if not installed already.

And I don't know about you and the others but I'm still not convinced this has anything to do with networking. Please check my post above ;)

---

### Post by ipv2 on 2021-04-20
> **CelticWarrior said:**
> Please note it *does *need Samba and it'll be be installed on demand if not installed already.

no it will not.

i am using this method & there is absolutely no samba on my machine.

---

### Post by ipv2 on 2021-04-20
> **CelticWarrior said:**
> Please note it *does *need Samba and it'll be be installed on demand if not installed already.

```
smb status
```

gives me Command smb not found.

```
smbstatus --shares
```

gives me Command 'smbstatus' not found, but can be installed with:

sudo apt install samba

```
sudo nano /etc/samba/smb.conf
```

gives me [ Directory '/etc/samba' does not exist ]

```
sudo apt install samba
```

asks me for permission to install samba.

if you know any other way to check if samba is installed let me know.

---

### Post by ActionParsnip on 2021-04-20
If you have openssh-server running then use. SFTP, no need for Samba. Dead easy

---

### Post by ipv2 on 2021-04-20
> **ActionParsnip said:**
> If you have openssh-server running then use. SFTP, no need for Samba. Dead easy

can this be used for file sharing over a lan network between ubuntu 20.04.2 & windows 10 pro?

or does it require ubuntu server & windows server?

---

### Post by ActionParsnip on 2021-04-20
Sure, just use something like Filezilla on Windows. There are even applications to mount SFTP in Windows (when doesn't Windows need another application to do anything remotely useful?). File sharing is a basic thing. Doesn't need a server OS. You could even use NFS which Windows can access natively. Loads options

---

### Post by ipv2 on 2021-04-20
> **ActionParsnip said:**
> when doesn't Windows need another application to do anything remotely useful?

:lolflag:

> **ActionParsnip said:**
> Sure, just use something like Filezilla on  Windows. There are even applications to mount SFTP in Windows. File sharing is a basic thing. Doesn't need a server OS. You  could even use NFS which Windows can access natively. Loads  options

cool will try them out.

thank you.

---

### Post by Morbius1 on 2021-04-21
> **ipv2 said:**
> 1. on the windows machine share a folder / folders & grant read / write access.

2. on the ubuntu machine : files > other locations > in the enter server address box = smb://ipaddressofwindowsmachine > connect > pop-up window for authorization > shared folders from windows.

note : you do not need samba for this method.
I got so fixated on the [highlight]installed samba incorrectly[/highlight] reference I lost sight of what the OP was trying to do. He's trying to "pull" files from Win10 to Linux. You are 98.76% correct. The Linux client to this Win10 server does not require the samba ( server ) package to be installed. The file manager as you described uses a samba client library ( libsmbclient ) to connect to the share and that is installed by default.

* Side note: You don't need any 3rd party application to set up an SSH server on WIn10. It already has that capability it just needs to be enabled:*
> Settings > Apps -> Apps & features > Optional Features > OpenSSH Server
Then it needs to be started:
> Services > OpenSSH SSH Server
You can either start it manually at that point or have it start automatically at boot which ... oh I don't know ... I guess you can do ... but I'd rather start it only when needed.

Then go through the same process you described for smb in Nautilus - except using ssh:
```
 ssh://win10-user-name@server
```

Where "server" can be the Win10 mDNS hostname ( win10.local for example ) or its ip address.

---

### Post by ipv2 on 2021-04-21
> **Morbius1 said:**
> You are 98.76% correct.

:lol:

will surely check out the ssh thingy.

thank you.

---

### Post by markb60000 on 2021-04-25
They are in the same network.

Mark

---

### Post by markb60000 on 2021-04-25
i did not see the "grant read/write" access , but, I did go to the File, sharing, advanced sharing, permissions, checked each of these three boxes:  "full control" , "change" , "read" 

Then, as you suggested, on the Ubuntu account (which is on a different computer, but in the same network, I "[COLOR=#000000] on the ubuntu machine : files > other locations > in the enter server address box = smb://ipaddressofwindowsmachine > connect > pop-up window for authorization > shared folders from windows."  

The repsonse was "No results found.  Try a different search."  Any suggestions (I have Windows 10).   THanks, Mark
[/COLOR]

---

### Post by SeijiSensei on 2021-04-25
Install [WinSCP]("https://winscp.net/eng/download.php") on the Windows machine.  Then install the openssh-server package on the Ubuntu box.  Use WinSCP to connect to the Ubuntu box via SCP. If the Linux box doesn't respond to a "hostname" just use its IP address instead.  You'll have a two-pane file manager you can use to move stuff back and forth between the machines.

---

### Post by ipv2 on 2021-04-25
> **markb60000 said:**
> I did go to the File

are you sharing a single file or a folder?

> **markb60000 said:**
> on a different computer, but in the same network

this is lan sharing right? as in both the computers are plugged in via a cable in to the same router.

> **markb60000 said:**
> [COLOR=#000000]The repsonse was "No results found.  Try a different search."[/COLOR]

strange! it is not a search.

> **markb60000 said:**
> [COLOR=#000000]I have Windows 10[/COLOR]

windows : control panel > network & internet > network & sharing settings > advanced sharing settings >

1. private : on & on

2. guest / public : off & off

3. all networks : off 128bit off

---

