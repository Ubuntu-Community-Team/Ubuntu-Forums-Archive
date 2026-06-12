---
title: "smbd spawns two instances, but does not work"
date: 2013-11-30
forum: New to Ubuntu
---

### Post by george16 on 2013-11-30
I'm kinda at wits end. Been using Linux since 1993 but almost 100% Slackware. Now tried Ubuntu since it "feels" a lot like OS X. And just built up my third box with 12.04. Pretty much under control, getting the hang of how Debian starts stuff. But hit a brick wall with a samba problem. I have installed/re-installed several times. I see two instances start, parent and child, I suppose...got that part. Cannot browse it from a win box. Both computers see each other fine. Now here's the only clue I have. If I kill off the parent process the original two smbd instances go away, and two new ones start, and the win box can see the samba shares just fine. I have tried to modify the start order in init.d by raising the number from 20smbd to 80smbd. Still starts two processes that don't work. I have tried a script at startup that delays 5 seconds and does killall smbd figuring that will be the same as if I were to do this. That didn't kill it so now I'm out of ideas. I went thru the gadmin-samba setup for server and see nothing obvious. 

What I'm wanting is samba to start even with nobody logged into the pc so it can just sit in the corner and be a file repository for me. 

Anybody have any ideas?

Thanks

George Csahanin
Austin,TX

---

### Post by bab1 on 2013-11-30
> **george16 said:**
> I'm kinda at wits end. Been using Linux since 1993 but almost 100% Slackware. Now tried Ubuntu since it "feels" a lot like OS X. And just built up my third box with 12.04. Pretty much under control, getting the hang of how Debian starts stuff. But hit a brick wall with a samba problem. I have installed/re-installed several times. I see two instances start, parent and child, I suppose...got that part. Cannot browse it from a win box. Both computers see each other fine. Now here's the only clue I have. If I kill off the parent process the original two smbd instances go away, and two new ones start, and the win box can see the samba shares just fine. I have tried to modify the start order in init.d by raising the number from 20smbd to 80smbd. Still starts two processes that don't work. I have tried a script at startup that delays 5 seconds and does killall smbd figuring that will be the same as if I were to do this. That didn't kill it so now I'm out of ideas. I went thru the gadmin-samba setup for server and see nothing obvious. 

What I'm wanting is samba to start even with nobody logged into the pc so it can just sit in the corner and be a file repository for me. 

Anybody have any ideas?

Thanks

George Csahanin
Austin,TX

Put all that init.d settings back to thier defaults.  There should always be 2 ***smbd*** daemons running at minimum.  The daemon that takes care of browsing is ***[COLOR="#0000FF"]nmbd[/COLOR]*** not ***[COLOR="#FF0000"]smbd[/COLOR]***.  You can see both with this command```
pgrep -l mbd
```

When Samba (smbd) is started (or restarted) it announces itself to the network.  That is why you see the shares for awhile.  But it is the ***nmbd*** daemon's job to translate the hostname to a NETBIOS name and manage the tracking of the local Master Browse List (MBL). 

Your problem is a name services problem not a failure of the ***smbd*** daemon at all.

---

### Post by george16 on 2013-12-01
I understand all of that, this is the way it should work. It isn't. I just rebooted the ubuntu box. smbd and nmbd. Two for smbd -F, 855 and 1081, nmbd -D is process 1754. The Win7 boxe(s) cannot see the shares. They indicate an error "the remote device or resource won't accept the connection", drill down, "The device or resource (P470-LINUX2) is not set up to accept connections on port "The File and printer sharing (SMB)" This is after 15 minutes of waiting, which shouldn't be anyhow. 

georgec@georgec-Precision-WorkStation-470:~$ ps aux|grep mbd
root       855  0.0  0.0  21412  4876 ?        Ss   11:15   0:00 smbd -F
root      1081  0.0  0.0  21516  1364 ?        S    11:15   0:00 smbd -F
root      1754  0.0  0.0  13332  1764 ?        Ss   11:15   0:00 nmbd -D

I killed 855. It respawned smbd -F at process 2692 and 2697 and was immediately visible on the Win7 boxes. 

root@georgec-Precision-WorkStation-470:/home/georgec# ps aux |grep mbd
root      1754  0.0  0.0  13332  1764 ?        Ss   11:15   0:00 nmbd -D
root      2692  3.6  0.0  21456  4876 ?        Ss   11:43   0:00 smbd -F
root      2697  0.0  0.0  21560  1248 ?        S    11:43   0:00 smbd -F

So still on my search for an answer or work around. 

Thanks for the quick reply

GeorgeC

---

### Post by bab1 on 2013-12-01
> **george16 said:**
> I understand all of that, this is the way it should work. It isn't. I just rebooted the ubuntu box. smbd and nmbd. Two for smbd -F, 855 and 1081, nmbd -D is process 1754. The Win7 boxe(s) cannot see the shares. They indicate an error "the remote device or resource won't accept the connection", drill down, "The device or resource (P470-LINUX2) is not set up to accept connections on port "The File and printer sharing (SMB)" This is after 15 minutes of waiting, which shouldn't be anyhow. 

With the shares _inaccessible_, please post the output of **ipconfig** from one of the Windows hosts.   From that same Windows host try and connect to the a Samba share via the command line using the IP address of the Samba server (net use X: \\**<IP_Address>**\share_name).  What results do you get?

---

### Post by george16 on 2013-12-01
ipconfig on the nearest client:

Second point first, tried the connection you proposed net use X:\\192.168.1.66\78g no dice. Error: cannot connect to share, etc...

I also removed samba and the helper app, reinstalled just samba and a different "server configuration tool" though the smb.conf is still leftover from earlier installs which used GAMBAS-SAMBA for setup. 

I'm just mystified by why the act of simply killing off the parent smbd process and letting it respawn makes all ok. I tried adding a "killall smbd" to /etc/rc.local but that didn't work, nor did it kill smbd (same PID after)

In reading here (searched on smbd this time, saw someone had a very similar issue a couple of weeks back. Needed to kill smbd to make the linux server able to browse the client, as I recall. 

This computer is going to a location where it will have no keyboard or mouse or monitor. But I can vnc in to start smbd after any reboot. That seems to be the only way I can use this. 

Oh, I also edited the lmhosts file in Win7 (that was a royal pain to do) and added this linux name ("P470-LINUX2") in there. Also modified the name resolver order in smb.conf as you had suggested to that other guy who was needing to restart smb.conf

GeorgeC

[I]Windows IP Configuration


Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . : gateway.2wire.net
   Link-local IPv6 Address . . . . . : fe80::bd27:1639:40c8:57b7%11
   IPv4 Address. . . . . . . . . . . : 192.168.1.84
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.1.254

Tunnel adapter isatap.gateway.2wire.net:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : gateway.2wire.net

Tunnel adapter Teredo Tunneling Pseudo-Interface:

   Connection-specific DNS Suffix  . : 
   IPv6 Address. . . . . . . . . . . : 2001:0:5ef5:79fb:38f8:2770:3f57:feab
   Link-local IPv6 Address . . . . . : fe80::38f8:2770:3f57:feab%13
   Default Gateway . . . . . . . . . : ::[/I]

---

### Post by bab1 on 2013-12-01
> **george16 said:**
> ipconfig on the nearest client:

Second point first, tried the connection you proposed net use X:\\192.168.1.66\78g no dice. Error: cannot connect to share, etc...

What is the exact error message?  This command should work.  I tried it before I suggested it to you.
> 

I also removed samba and the helper app, reinstalled just samba and a different "server configuration tool" though the smb.conf is still leftover from earlier installs which used GAMBAS-SAMBA for setup. 

Are you referring to GADMIN-SAMBA?  If so then you will never get this thing to work.  You need to purge the system of everything GADMIN-SAMBA.  There is no need for any helper apps to administrate Samba3.

Post the contents of the smb.conf file```
cat /etc/samba/smb.conf
```
> 

I'm just mystified by why the act of simply killing off the parent smbd process and letting it respawn makes all ok. I tried adding a "killall smbd" to /etc/rc.local but that didn't work, nor did it kill smbd (same PID after)

In reading here (searched on smbd this time, saw someone had a very similar issue a couple of weeks back. Needed to kill smbd to make the linux server able to browse the client, as I recall. 

My experience is that when The host announces itself to the network when starting (this includes restarting smbd) enough information is provided for a time for all to see the server and it's shares.  All browsing after that requires that the Master Browser be located.  So it is possible to initially see the shares but not be able to access them consistently after that. 
> 

This computer is going to a location where it will have no keyboard or mouse or monitor. But I can vnc in to start smbd after any reboot. That seems to be the only way I can use this. 

I wouldn't give up that fast.  I have 2 Samba servers that have no GUI interface and no direct interface (keyboard or monitor).  These are used everyday by both Windows and Linux clients.  I have a working CentOS samba server that is 10,000 mile from me that I maintain via a simple ssh connection.  This install has Windows clients too.
> 
Oh, I also edited the lmhosts file in Win7 (that was a royal pain to do) and added this linux name ("P470-LINUX2") in there. Also modified the name resolver order in smb.conf as you had suggested to that other guy who was needing to restart smb.conf

What do you mean by "this linux name ("P470-LINUX2")?  The hostname appears to be: *georgec-Precision-WorkStation-470*.  Once I see the smb.conf file I can advise you better, but something doesn't seem correct here.  Not to mention the need to get rid of GADMIN-SAMBA and other "helpers".
> 
```

Windows IP Configuration


Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . : gateway.2wire.net
   Link-local IPv6 Address . . . . . : fe80::bd27:1639:40c8:57b7%11
   IPv4 Address. . . . . . . . . . . : 192.168.1.84
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : 192.168.1.254

Tunnel adapter isatap.gateway.2wire.net:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : gateway.2wire.net

Tunnel adapter Teredo Tunneling Pseudo-Interface:

   Connection-specific DNS Suffix  . : 
   IPv6 Address. . . . . . . . . . . : 2001:0:5ef5:79fb:38f8:2770:3f57:feab
   Link-local IPv6 Address . . . . . : fe80::38f8:2770:3f57:feab%13
   Default Gateway . . . . . . . . . : ::[
```

I guess we need to see all of the config to view the netbios over TCP settings (NBT) for this Windows host.  Post the output of ```
ipconfig /all
```

Let's post some other info so I don't have to keep asking for more postings.  On the Ubuntu host show me the output of these commands```

cat /etc/hosts

hostname

net usershare info --long

smbtree -d3

```

Are there other modifications to Samba that you have tried and left in place?

---

### Post by george16 on 2013-12-02
smb.conf:

[global]
    idmap gid = 16777216-33554431
    passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
    obey pam restrictions = yes
;    preserve case = yes
;    short preserve case = yes
    delete user from group script = /usr/sbin/userdel '%u' '%g'
;    time server = no
    dns proxy = no
    netbios name = P470-Linux2
    cups options = raw
;    printing = cups
    idmap uid = 16777216-33554431
;    disable netbios = no
    logon script = %G.bat
;    winbind refresh tickets = no
    update encrypted = yes
    security = share
    machine password timeout = 120
    add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
    delete user script = /usr/sbin/userdel '%u'
    server schannel = no
    max log size = 1000
    winbind nss info = no
    log file = /var/log/samba/samba.log
;    load printers = yes
;    guest account = nobody
    passwd chat timeout = 120
    delete group script = /usr/sbin/groupdel '%g'
    username level = 6
    socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
    client use spnego = no
    follow symlinks = no
;    null passwords = no
    domain master = no
    winbind trusted domains only = yes
    winbind use default domain = yes
;    passdb backend = tdbsam
    template shell = /dev/null
;    client plaintext auth = no
    bind interfaces only = yes
;    pam password change = no
    enable spoolss = yes
;    domain logons = no
    name resolve order = bcast host lmhosts wins
    client signing = no
;    hostname lookups = no
    remote browse sync = 192.168.1.255
    client schannel = no
    hosts allow = 127. 192.168.0. 192.168.1.
    passwd program = /usr/bin/passwd '%u'
    remote announce = 192.168.1.255
    local master = no
    workgroup = workgroup
    os level = 33
;    server signing = no
    printcap name = cups
    winbind separator = @
;    winbind offline logon = no
    allow trusted domains = no
    add group script = /usr/sbin/groupadd '%g'
;    nt pipe support = yes
    add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
;    nt status support = yes
    logon drive = m:
    interfaces = 127.0.0.1/8 192.168.0.0/24 192.168.1.0/24
    encrypt passwords = no
    logon home = \\%L\homes\%u
;    wins proxy = no
    password level = 6
    server string = Samba file and print server
    winbind nested groups = no
    unix password sync = yes
    logon path = \\%L\profiles\%u
    add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
;    preferred master = no
    winbind cache time = 360
    guest ok = yes

[homes]
    comment = Home Directories
    path = /home
    valid users = %U
    read only = no
;    available = yes
;    browseable = yes
;    guest ok = no
;    printable = no
    locking = no
    strict locking = no

[printers]
    comment = All Printers
    path = /var/spool/samba
;    browseable = yes
;    writable = No
;    guest ok = no
    printable = yes
    locking = no
    strict locking = no

[pdf-printer]
    path = /tmp
    comment = PDF Printer Service
    printable = yes
    guest ok = yes
    use client driver = yes
    printing = bsd
    print command = /usr/bin/gadmin-samba-pdf %s %u
    lpq command = 
    lprm command = 

[78G]
    path = /sda2
    comment = 78 GB
    read only = no
;    available = yes
;    browseable = yes
;    guest ok = no
;    printable = no
    locking = no
    strict locking = no

[154G]
    path = /sda3
    comment = 154GB
    read only = no
;    available = yes
;    browseable = yes
;    guest ok = no
;    printable = no
    locking = no
    strict locking = no

[30GLIN]
    path = /sda5
    comment = 30GB LIN
    read only = no
;    available = yes
;    browseable = yes
;    guest ok = no
;    printable = no
    locking = no
    strict locking = no

[700G]
    path = /sda7
    comment = 700G
    read only = no
;    available = yes
;    browseable = yes
;    guest ok = no
;    printable = no
    locking = no
    strict locking = no

[20GLIN]
    path = /sdb1
    comment = 20GB LIN
    read only = no
;    available = yes
;    browseable = yes
;    guest ok = no
;    printable = no
    locking = no
    strict locking = no

[281GB]
    path = /sdb3
    comment = 281G
    read only = no
;    available = yes
;    browseable = yes
;    guest ok = no
;    printable = no
    locking = no
    strict locking = no

________________________________________________

ipconfig /all from client:

Windows IP Configuration

   Host Name . . . . . . . . . . . . : georgec-PC
   Primary Dns Suffix  . . . . . . . : 
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : gateway.2wire.net

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . : gateway.2wire.net
   Description . . . . . . . . . . . : Intel(R) 82578DM Gigabit Network Connection
   Physical Address. . . . . . . . . : B8-AC-6F-AC-21-F7
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::bd27:1639:40c8:57b7%11(Preferred) 
   IPv4 Address. . . . . . . . . . . : 192.168.1.84(Preferred) 
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Sunday, December 01, 2013 1:51:22 AM
   Lease Expires . . . . . . . . . . : Monday, December 02, 2013 1:51:21 PM
   Default Gateway . . . . . . . . . : 192.168.1.254
   DHCP Server . . . . . . . . . . . : 192.168.1.254
   DHCPv6 IAID . . . . . . . . . . . : 246983791
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-1A-10-DD-5C-B8-AC-6F-AC-21-F7
   DNS Servers . . . . . . . . . . . : 192.168.1.254
   NetBIOS over Tcpip. . . . . . . . : Enabled

Tunnel adapter isatap.gateway.2wire.net:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : gateway.2wire.net
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

Tunnel adapter Teredo Tunneling Pseudo-Interface:

   Connection-specific DNS Suffix  . : 
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No

________________________________________________________________

/home/georgec# cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    georgec-Precision-WorkStation-470

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
______________________________________________

/home/georgec# hostname
georgec-Precision-WorkStation-470


___________________________________________
/home/georgec# net usershare info --long
Ignoring unknown parameter "update encrypted"


______________________________________________

/home/georgec# smbtree -d3
The program 'smbtree' is currently not installed.  You can install it by typing:
apt-get install smbclient
_______________________________________________

"P470-LINUX2" is the name I gave the samba server. 

That long hostname is what ubuntu gave it when it was installing. 

I'll  say that I probably should have stuck with Slackware, that one I know  my way around. But the init system is vastly different and I have almost  no familiarity with the structure of Debian/Ubuntu. So I chose the gui  setup stuff for samba to (I had hoped) eliminate the learnign curve on  editing it. I have a O'Reilly book on Samba somewhere, might be time to  dig it out, but it is about 10 years old and probably not of much use. 

Thanks  for the help, I hope this info gives some clue.Though after killing the  smbd this afternoon it has been fine and I have been able to migrate  files from my old workstation to the new one, which is what this is all  about. 

GeorgeC

---

### Post by bab1 on 2013-12-02
> **george16 said:**
> 


smb.conf:
```

[global]
    idmap gid = 16777216-33554431
    passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
    obey pam restrictions = yes
;    preserve case = yes
;    short preserve case = yes
    delete user from group script = /usr/sbin/userdel '%u' '%g'
;    time server = no
    dns proxy = no
    netbios name = P470-Linux2
    cups options = raw
;    printing = cups
    idmap uid = 16777216-33554431
;    disable netbios = no
    logon script = %G.bat
;    winbind refresh tickets = no
    update encrypted = yes
    security = share
    machine password timeout = 120
    add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
    delete user script = /usr/sbin/userdel '%u'
    server schannel = no
    max log size = 1000
    winbind nss info = no
    log file = /var/log/samba/samba.log
;    load printers = yes
;    guest account = nobody
    passwd chat timeout = 120
    delete group script = /usr/sbin/groupdel '%g'
    username level = 6
    socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
    client use spnego = no
    follow symlinks = no
;    null passwords = no
    domain master = no
    winbind trusted domains only = yes
    winbind use default domain = yes
;    passdb backend = tdbsam
    template shell = /dev/null
;    client plaintext auth = no
    bind interfaces only = yes
;    pam password change = no
    enable spoolss = yes
;    domain logons = no
    name resolve order = bcast host lmhosts wins
    client signing = no
;    hostname lookups = no
    remote browse sync = 192.168.1.255
    client schannel = no
    hosts allow = 127. 192.168.0. 192.168.1.
    passwd program = /usr/bin/passwd '%u'
    remote announce = 192.168.1.255
    local master = no
    workgroup = workgroup
    os level = 33
;    server signing = no
    printcap name = cups
    winbind separator = @
;    winbind offline logon = no
    allow trusted domains = no
    add group script = /usr/sbin/groupadd '%g'
;    nt pipe support = yes
    add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
;    nt status support = yes
    logon drive = m:
    interfaces = 127.0.0.1/8 192.168.0.0/24 192.168.1.0/24
    encrypt passwords = no
    logon home = \\%L\homes\%u
;    wins proxy = no
    password level = 6
    server string = Samba file and print server
    winbind nested groups = no
    unix password sync = yes
    logon path = \\%L\profiles\%u
    add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
;    preferred master = no
    winbind cache time = 360
    guest ok = yes
...

```

```
[COLOR="#FF0000"]WARNING: The "idmap gid" option is deprecated
WARNING: The "idmap uid" option is deprecated
]Unknown parameter encountered: "update encrypted" [/color]<-- this may be why the usershares command is unhappy
[COLOR="#FF0000"]Ignoring unknown parameter "update encrypted"
WARNING: The "password level" option is deprecated
WARNING: The security=share option is deprecated[/COLOR]
```
None of the above from the smb.conf  is good.  Some are worse than others.  Who knows how much GADMIN-SAMBA is still acting upon the configuration.
> 

ipconfig /all from client:
```

...
   DNS Servers . . . . . . . . . . . : 192.168.1.254
   NetBIOS over Tcpip. . . . . . . . : Enabled   [COLOR="#FF0000"]<--- This is what I was looking for.  [/COLOR]

```

________________________________________________________________

```
/home/georgec# cat /etc/hosts
127.0.0.1    localhost
127.0.1.1    georgec-Precision-WorkStation-470

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

```

```
/home/georgec# hostname
georgec-Precision-WorkStation-470

```
That long hostname is what ubuntu gave it when it was installing. 

"P470-LINUX2" is the name I gave the samba server. 

I see the NETBIOS NAME listing in the smb.conf. This and setting the bcast first in the name resolve parameter negates the need to rely on the /etc/hosts and /etc/hostname file information.
> 

```
/home/georgec# net usershare info --long
Ignoring unknown parameter "update encrypted"
```
This should not return an error.  It should either return a usershare listing if one has been created or return to the prompt if there are no usershares. > 

```
/home/georgec# smbtree -d3
The program 'smbtree' is currently not installed.  You can install it by typing:
apt-get install smbclient
```

I think you should install smbclient.  We need it for testing at the very least.
> 

I'll  say that I probably should have stuck with Slackware, that one I know  my way around. But the init system is vastly different and I have almost  no familiarity with the structure of Debian/Ubuntu. So I chose the gui  setup stuff for samba to (I had hoped) eliminate the learnign curve on  editing it. 

Samba should work the same in both OS's.  The only config file for smbd itself is the smb.conf file.
> 
I have a O'Reilly book on Samba somewhere, might be time to  dig it out, but it is about 10 years old and probably not of much use. 

The Samba book you are referring to is for Samba v2.  We should be talking about Samba v3.  They're different in many aspects.
> 
Thanks  for the help, I hope this info gives some clue.Though after killing the  smbd this afternoon it has been fine and I have been able to migrate  files from my old workstation to the new one, which is what this is all  about. 


There are only a few things that need to be changed from the default parameters in the smb.conf file.  I think you should copy the existing smb.conf file to smb.conf.bak and use the default smb.conf file.  If you don't have a copy of the original file I have attached one to this post.  The only change I would make is to add these to the [global] section```

name resolve order = bcast

netbios name = P470-LINUX2
```...and then add your shares.

You should then restart the smbd daemon```
sudo service smbd restart
```

I forgot to ask, is the Windows username also a Linux user and a Samba user?  It's helpful if all 3 are the same.  What's the output of this command```
sudo pdbedit -L
```

I notice that you are logged in as root.  This is a bad idea generally and in specific will give you unexpected results from Samba at the command line.  The only things you need to be root for is pdbedit and to edit the smb.conf file.  Use sudo to become root for the individual commands rather than logging in (su or sudo -i) please.

---

### Post by george16 on 2013-12-03
OK. Got it working...when in doubt...

I uninstalled EVERYTHING smb related. Something conflicting somewhere. Deleted /etc/samba. Fresh /etc/samba with smb.conf you sent added shares and the two lines you suggested. Works like a champ. Thanks for the suggestions. Your comment about Gadmin is what got me thinking. But the package manager may have allowed some conflicts, I don't know since it doesn't tell you exactly what files and executables are being installed, just XXMB more space, etc.

---

