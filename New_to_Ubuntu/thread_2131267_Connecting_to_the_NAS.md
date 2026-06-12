---
title: "Connecting to the NAS"
date: 2013-04-01
forum: New to Ubuntu
---

### Post by Phil Binner on 2013-04-01
I have a Dlink NAS DNS-325.  When I browse files it's there, absolutely fine, but when I want to connect from an application, such as Thunderbird (or anything else) the network is just not available.  This is not just the NAS that's not available, it's the whole network, but the NAS is what concerns me at the moment.

I have been told I need to mount the NAS at startup, and have been directed to a site "http://ubuntuforums.org/showthread.php?t=249889", which instructs me to run the commands 

$ sudo apt-get update
$ sudo apt-get install nfs-common

Following is the result:

bigbin@Bigbin-Ubuntu:~$ sudo apt-get update
[sudo] password for bigbin: 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release.gpg                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release.gpg        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release                       
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B]                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Sources                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Sources               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Sources                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Sources                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main i386 Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted i386 Packages              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe i386 Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse TranslationIndex
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted TranslationIndex 
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe TranslationIndex   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Sources        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Sources  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Sources    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release                         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Sources            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main i386 Packages            
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted i386 Packages      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe i386 Packages        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse i386 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main TranslationIndex         
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse TranslationIndex   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted TranslationIndex   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe TranslationIndex     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en_GB                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex      
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en                   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en_GB          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en             
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en_GB          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en_GB  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en               
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Translation-en_GB        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Translation-en           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Translation-en_GB  
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Translation-en     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en        
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_GB
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
Fetched 72 B in 31s (2 B/s)
Reading package lists... Done
bigbin@Bigbin-Ubuntu:~$ sudo apt-get install nfs-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libunity6 linux-headers-3.2.0-24 kde-l10n-engb screen-resolution-extra
  linux-headers-3.2.0-24-generic-pae
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libgssglue1 libnfsidmap2 libtirpc1 rpcbind
The following NEW packages will be installed
  libgssglue1 libnfsidmap2 libtirpc1 nfs-common rpcbind
0 upgraded, 5 newly installed, 0 to remove and 22 not upgraded.
Need to get 413 kB of archives.
After this operation, 1,298 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main libgssglue1 i386 0.3-4ubuntu0.1 [22.0 kB]
Get:2 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/main libtirpc1 i386 0.2.2-5 [84.4 kB]
Get:3 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main rpcbind i386 0.2.0-7ubuntu1.2 [41.9 kB]
Get:4 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise/main libnfsidmap2 i386 0.25-1ubuntu2 [30.6 kB]
Get:5 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) precise-updates/main nfs-common i386 1:1.2.5-3ubuntu3.1 [234 kB]
Fetched 413 kB in 16s (25.1 kB/s)                                              
Selecting previously unselected package libgssglue1.
(Reading database ... 544091 files and directories currently installed.)
Unpacking libgssglue1 (from .../libgssglue1_0.3-4ubuntu0.1_i386.deb) ...
Selecting previously unselected package libtirpc1.
Unpacking libtirpc1 (from .../libtirpc1_0.2.2-5_i386.deb) ...
Selecting previously unselected package rpcbind.
Unpacking rpcbind (from .../rpcbind_0.2.0-7ubuntu1.2_i386.deb) ...
Selecting previously unselected package libnfsidmap2.
Unpacking libnfsidmap2 (from .../libnfsidmap2_0.25-1ubuntu2_i386.deb) ...
Selecting previously unselected package nfs-common.
Unpacking nfs-common (from .../nfs-common_1%3a1.2.5-3ubuntu3.1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up libgssglue1 (0.3-4ubuntu0.1) ...
Setting up libtirpc1 (0.2.2-5) ...
Setting up rpcbind (0.2.0-7ubuntu1.2) ...
 Removing any system startup links for /etc/init.d/rpcbind ...
portmap start/running, process 17189
Setting up libnfsidmap2 (0.25-1ubuntu2) ...
Setting up nfs-common (1:1.2.5-3ubuntu3.1) ...

Creating config file /etc/idmapd.conf with new version

Creating config file /etc/default/nfs-common with new version
Adding system user `statd' (UID 117) ...
Adding new user `statd' (UID 117) with group `nogroup' ...
Not creating home directory `/var/lib/nfs'.
statd start/running, process 17423
gssd stop/pre-start, process 17452
idmapd start/running, process 17496
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
bigbin@Bigbin-Ubuntu:~$ ^C

Then tried to view the location:

bigbin@Bigbin-Ubuntu:~$ showmount -e 192.168.1.73
clnt_create: RPC: Port mapper failure - Unable to receive: errno 111 (Connection refused)

Then tried to mount the NAS in a directory called nfs:

bigbin@Bigbin-Ubuntu:~$ sudo mkdir /nfs
[sudo] password for bigbin: 
bigbin@Bigbin-Ubuntu:~$ cd /nfs
bigbin@Bigbin-Ubuntu:/nfs$ cd /
bigbin@Bigbin-Ubuntu:/$ sudo mount -o soft,intr,rsize=8192,wsize=8192 192.168.1.73:/volume1 /nfs
mount.nfs: Connection timed out

Can anyone help please.  This is one of the problems preventing my migration from Windows, though by no means the only one.

regards

Phil Binner

---

### Post by SeijiSensei on 2013-04-01
Does the NAS provide any logs for diagnosis?

Does the NAS have "no_root_squash" set as an NFS option?  Without that, root cannot mount an NFS share.

---

### Post by Phil Binner on 2013-04-01
I'm afraid I can't answer those questions.  The NAS is a 2 disc RAID system, but when I log on I don't see any NFS settings.  Could it be that it doesn't use NFS.

All the log shows for today is starting and stopping the fan.

All I can tell you for certain is that I have no problem accessing the NAS frof the file browser, but it is not accessible from anywhere else.

---

### Post by steeldriver on 2013-04-01
As a first step you could install nmap on the client and at least probe the server to see if the usual nfs and rpcbind ports are open, for instance on my little Netgear ReadyNas I get

```
$ nmap -A -T4 192.168.1.127 | grep -e '^111' -e '^2049'
111/tcp   open  rpcbind     2 (rpc #100000)
2049/tcp  open  nfs         2-4 (rpc #100003)
```

[with the ReadyNas I *can* actually ssh into it and look at its /etc/exports file directly but that's an unsupported hack - I suspect you may be limited to whatever you see via your NAS's standard web interface]

---

### Post by Phil Binner on 2013-04-01
I installed nmap but couldn't find it to run it. The software ncentre says it's installed, but it isn't in the all applications list from Dash Home.  So then I installed the GUI frontend zxenmap and ran that.  It complained that I wasn't a root user, but ran anyway.  Following is the output:

Warning:  You are not root -- using TCP pingscan rather than ICMP

Starting Nmap 5.21 ( [http://nmap.org](http://nmap.org) ) at 2013-04-01 15:44 BST
NSE: Loaded 36 scripts for scanning.
Initiating Ping Scan at 15:44
Scanning 192.168.1.73 [6 ports]
Completed Ping Scan at 15:44, 0.00s elapsed (1 total hosts)
Initiating Parallel DNS resolution of 1 host. at 15:44
Completed Parallel DNS resolution of 1 host. at 15:44, 0.00s elapsed
Initiating Connect Scan at 15:44
Scanning 192.168.1.73 [1000 ports]
Discovered open port 445/tcp on 192.168.1.73
Discovered open port 139/tcp on 192.168.1.73
Discovered open port 3306/tcp on 192.168.1.73
Discovered open port 80/tcp on 192.168.1.73
Discovered open port 443/tcp on 192.168.1.73
Discovered open port 548/tcp on 192.168.1.73
Discovered open port 515/tcp on 192.168.1.73
Discovered open port 8000/tcp on 192.168.1.73
Completed Connect Scan at 15:44, 0.03s elapsed (1000 total ports)
Initiating Service scan at 15:44
Completed NSE at 15:45, 0.46s elapsed
NSE: Script Scanning completed.
Nmap scan report for 192.168.1.73
Host is up (0.00063s latency).
Not shown: 992 closed ports
PORT     STATE SERVICE     VERSION
80/tcp   open  http        lighttpd 1.4.25
|_html-title: Site doesn't have a title (text/html).
139/tcp  open  netbios-ssn Samba smbd 3.X (workgroup: WORKGROUP)
443/tcp  open  ssl/http    lighttpd 1.4.25
|_html-title: Site doesn't have a title (text/html).
445/tcp  open  netbios-ssn Samba smbd 3.X (workgroup: WORKGROUP)
515/tcp  open  printer     LPRng (Not authorized)
548/tcp  open  afp?
3306/tcp open  mysql       MySQL (unauthorized)
8000/tcp open  http-alt?
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at [http://www.insecure.org/cgi-bin/servicefp-submit.cgi](http://www.insecure.org/cgi-bin/servicefp-submit.cgi) :
SF-Port8000-TCP:V=5.21%I=7%D=4/1%Time=51599D4C%P=i686-pc-linux-gnu%r(GetRe
SF:quest,6A,"HTTP/1\.0\x20404\x20File\x20Not\x20Found\r\nContent-Type:\x20
SF:text/html\r\n\r\n<b>The\x20file\x20you\x20requested\x20could\x20not\x20
SF:be\x20found</b>\r\n")%r(FourOhFourRequest,6A,"HTTP/1\.0\x20404\x20File\
SF:x20Not\x20Found\r\nContent-Type:\x20text/html\r\n\r\n<b>The\x20file\x20
SF:you\x20requested\x20could\x20not\x20be\x20found</b>\r\n");

Host script results:
| nbstat:  
|   NetBIOS name: D-LINK-NAS, NetBIOS user: <unknown>, NetBIOS MAC: <unknown>
|   Names
|     D-LINK-NAS<00>       Flags: <unique><active>
|     D-LINK-NAS<03>       Flags: <unique><active>
|     D-LINK-NAS<20>       Flags: <unique><active>
|     \x01\x02__MSBROWSE__\x02<01>  Flags: <group><active>
|     WORKGROUP<1d>        Flags: <unique><active>
|     WORKGROUP<1e>        Flags: <group><active>
|_    WORKGROUP<00>        Flags: <group><active>
| smb-os-discovery:  
|   OS: Unix (Samba 3.2.8)
|   Name: Unknown\Unknown
|_  System time: 2013-04-01 15:34:24 UTC+1
|_smbv2-enabled: Server doesn't support SMBv2 protocol

Read data files from: /usr/share/nmap
Service detection performed. Please report any incorrect results at [http://nmap.org/submit/](http://nmap.org/submit/) .
Nmap done: 1 IP address (1 host up) scanned in 95.53 seconds



Is that any help.

---

### Post by steeldriver on 2013-04-01
OK well I'm *not* an expert on these kinds of things but that looks to me like it is only sharing via SAMBA - you'd need to look at the Dlink documentation to see if it's possible to turn on nfs sharing, if not you should be able to mount using cifs (SAMBA) after installing the cifs-utils package, e.g. for a public (no authentication required) share:

```

$ sudo mkdir -p /mnt/nas-01/public
$ sudo mount -t cifs //192.168.1.127/public /mnt/nas-01/public
Password:
$ ls /mnt/nas-01/public/
Downloads  Program Files  setup  Software  Thumbs.db
$
```

or for a private share

```

$ sudo mkdir -p /mnt/nas-01/home/myuser
$
$ sudo mount -t cifs -ouser=myuser,pass=xxxxxxxx //192.168.1.127/myuser /mnt/nas-01/home/myuser
$
$ ls /mnt/nas-01/home/myuser/
Misc  Other  Visual Studio 2008
$
```

You can also use a credentials file I think - after installing cifs-utils you can refer to the man page for all the options / syntax

```
man mount.cifs
```

Oh and fwiw you would run nmap direct from the command line after starting a terminal (Ctrl-Alt-t)

---

### Post by gordintoronto on 2013-04-01
You just need to do this once: make sure your file manager is set to display hidden files. In your Home folder, scroll down to .gvfs and right-click on it. Select "Make Link." The Link will not be hidden, drag it onto your desktop.

After making sure the drive is mounted, from your application's save dialogue navigate to Desktop, select "Link to .gvfs" and the network drive will appear in it. One more double-click and you can save.

---

### Post by Phil Binner on 2013-04-23
Hi. Thanks for that.  After a very busy time I have returned to Ubuntu and applied the fix Gordintoronto provided, and it did work after I had selected the NAS inside the link to .gvfs.  Only until I rebooted , though.  Have I missed something or is there something else I should do to prevent me having to prime .gvfs each new start up.

---

### Post by Phil Binner on 2013-04-23
next tried steeldrivers option. The results are following:

bigbin@Bigbin-Ubuntu:~$ sudo mkdir -p /mnt/d-link-nas/public
[sudo] password for bigbin: 
bigbin@Bigbin-Ubuntu:~$ sudo mount -t cifs //192.168.1.127/public /mnt/d-link-nas/public
mount: wrong fs type, bad option, bad superblock on //192.168.1.127/public,
       missing codepage or helper program, or other error
       (for several filesystems (e.g. nfs, cifs) you might
       need a /sbin/mount.<type> helper program)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

bigbin@Bigbin-Ubuntu:~$ 

My problem is that I am really a GUI man, and only moderately competant at that.  Every time I venture forth into the terminal it's like I'm in a foreign country.  Any more help would be appreciated.

---

### Post by steeldriver on 2013-04-23
Haven't re-read the whole thread, but if you want to go the CIFS route then make sure you have the cifs-utils package installed (it isn't by default) and try again

```
sudo apt-get install cifs-utils

sudo mount -t cifs //192.168.1.127/public /mnt/d-link-nas/public
```

Obviously replace 192.168.1.127 with your actual NAS IP

---

### Post by Phil Binner on 2013-04-23
Actually the ip address confused me, because the ip address of the machine I'm using just happens to be 192.168.1.127, so I assumed you'd got that from the documentation I included in the reams above.  Anyway, in the meantime I have found a comprehensive guide and sorted it.  The NAS now loads at startup.

Thanks for all your help.  If i can find out how to mark this solved I'll end it.

Phil B

---

### Post by Phil Binner on 2013-04-23
Not sure what's happening here. I replied to this thread but it got lost.

Anyway, it's all sorted now.  The NAS mounts at startup using cifs.

Thanks for all help.

Phil B

---

