---
title: "Mapping Win 7 to Ubuntu  (14.04 LTS) drives"
date: 2014-07-13
forum: New to Ubuntu
---

### Post by Lagbehind on 2014-07-13
I want to map my windows 7 pcs to drives on my Ubuntu computer. I am taking the plunge to move over to Ubuntu, but still have a great deal to learn first.  I can't seem to find any straight forward instructions of how to access an Ubuntu folder or drive (share in windows terminology) from a windows pc.  Can anyone one help with some simple terminology and instructions?  I would have thought it was a common problem?

---

### Post by veddox on 2014-07-13
Welcome to Ubuntu! :-)

If I understand you correctly, you have a PC on which you are planning to install only Ubuntu. You want to be able to access files on that PC from other PCs still running Windows over a network. Is that what you mean? If so, you'll find a tutorial [here]("http://www.7tutorials.com/how-access-ubuntu-shared-folders-windows-7").

If you mean that you are dual-booting Windows and Ubuntu, and you want access to your files from both OSs, then you need to move those files to a data partition (NTFS formatted). This partition will show up as D: (or some other letter) in Windows, and you can mount it no problem when working under Ubuntu. (It's also pretty easy to configure your system to automount partitions, if you're interested, read up on FSTAB.)

---

### Post by Lagbehind on 2014-07-13
Yes indeed, I want to dedicate the computer exclusively to Ubuntu etc.  I will need to look at the tutorial.

Many thanks

---

### Post by Lagbehind on 2014-07-13
I read several of the tutorials which were very informative. I installed samba and shared a folder in my "home folder". Alas without success. 

1. changed the work groupname (to match the one we have at home) using sudo gedit etc/samba/smb.conf
2. I created the file share in the "home folder" with appropriate share name and checked "Allow others to create and delete files in this folder" and checked "Guest access (for people without a user account)"
3. Checked network view in Windows 7 but can not see the Ubuntu pc as the notes suggest.

Have I missed anything?

---

### Post by mooreted on 2014-07-13
Here is something more up-to-date:

[http://ubuntuhandbook.org/index.php/2014/05/ubuntu1404-file-sharing-samba/](http://ubuntuhandbook.org/index.php/2014/05/ubuntu1404-file-sharing-samba/)

---

### Post by mooreted on 2014-07-13
From the Windows machine, can you ping the IP address of the Ubuntu machine? If not, what error are you getting?

---

### Post by Lagbehind on 2014-07-13
Thank you.  I read through the notes and typed them to the letter sudo apt-get install samba etc....
Renamed the workgroup always seems to appear in lower case in Ubuntu but upper in windows?  Set the account settings as standard, added a unix user. But still I cannot see the Unbuntu pc from windows 7.  Anyone have any other suggestions to troubleshoot this one please?

---

### Post by yancek on 2014-07-13
> Renamed the workgroup always seems to appear in lower case in Ubuntu but upper in windows?

I don't use samba but, looking at the tutorial in the link posted above I see:

> **Workgroup**. Same to your Windows Workgroup name (case-sensitive).

So change it in Ubuntu to all uppercase and see what happens.

---

### Post by Lagbehind on 2014-07-13
Sorry yancek, I wasn't clear.  I entered the workgroup into Ubuntu (Samba) in upper-case as it is in windows 7. But when I looked at the settings later the workgroup name in Ubuntu displayed in lower-case.  Very odd I think.

---

### Post by Lagbehind on 2014-07-13
Sorry dumb question but I don't know how to ping from Ubuntu and how do you find the ip address (ipconfig in windows) etc?

---

### Post by mooreted on 2014-07-13
To find the IP address open a command prompt and type:

ifconfig

If you know the IP address of the Windows machine you ping it the same way you would in Windows. Open a command prompt an type:

ping <IP address>

Example:

ping 192.168.0.2

---

### Post by veddox on 2014-07-14
> If you know the IP address of the Windows machine you ping it the same way you would in Windows. Open a command prompt an type:

 ping <IP address>

Under Ubuntu, you should add the -c option, otherwise it will go on pinging indefinitely:

```
ping -c 3 <IP address>
```

The "-c 3" tells it to only send three packets (which is usually enough).

---

### Post by Morbius1 on 2014-07-14
In the course of this topic you have been given two different howto's to follow and if you used both now have samba share definitions of the same target folder in two different locations which is generally not a good thing.

You might want to post the output of the following commands just so the folks here can see how you are set up:
```
testparm -s
```
```
net usershare info --long
```

Not being able to see a linux host - at least if you are burdened with Windows guests - in a home lan is generally limited to a small number if issues:

** Services not running - nmbd and smbd
** Firewall on either or both machines are in the way
** Your hostname is too long - seriously 
** And finally the state of one parameter - "name resolve order"

You might want to post the hostname of your Samba server by running this command:
```
hostname
```
It has to be 15 characters or less in length. Easily fixed for samba purposes by adding a line to the [global] section of smb.conf:
```
netbios name = something-less-than-16-characters
```
Side note: Curiously in a home lan the workgroup name really doesn't matter so I wouldn't be too obsessed with it. I have 4 workgroup names at the moment and everyone can see each other just fine.

---

### Post by Lagbehind on 2014-07-14
Many thanks Morbius1.  Please see the listings below:


UBUNTU pc:
**testparm -s**
===========

rd@rd-Precision-WorkStation-390:~$ testparm      -s     
Load smb config      files from /etc/samba/smb.conf     
rlimit_max:      increasing rlimit_max (1024) to minimum Windows limit (16384)     
WARNING: Ignoring      invalid value 'share' for parameter 'security'     
Processing section      "[printers]"     
Processing section      "[print$]"     
Processing section      "[Videos]"     
Processing section      "[Videos]"     
Loaded services      file      OK.     
Server role:      ROLE_STANDALONE     
[global]     
 workgroup =      RAINBOW     
 server string = %h      server (Samba, Ubuntu)     
 server role =      standalone server     
 encrypt passwords      =      No     
 map to guest = Bad      User     
 obey pam      restrictions = Yes     
 guest account =      rdd     
 pam password      change      = Yes     
 passwd program =      /usr/bin/passwd %u     
 passwd chat =      *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n      *password\supdated\ssuccessfully* .     
 unix password sync      = Yes     
 syslog = 0     
 log file =      /var/log/samba/log.%m     
 max log size =      1000     
 dns proxy = No     
 usershare allow      guests = Yes     
 panic action =      /usr/share/samba/panic-action %d     
 idmap config * :      backend = tdb     
 guest ok = Yes     
[printers]     
 comment = All      Printers     
 path =      /var/spool/samba     
 create mask = 0700     
 printable = Yes     
 print ok = Yes     
 browseable = No     
[print$]     
 comment = Printer      Drivers     
 path =      /var/lib/samba/printers     
 valid users = rd,      whoopsie     
 read only = No     
[Videos]     
 path =      /home/rd/Videos     
 valid users = rd     
 read only = No     
rd@rd-Precision-WorkStation-390:~$     




 
 
**net usershare info -&#8211;long       **
==================

rd@rd-Precision-WorkStation-390:~$ net usershare info --long     
WARNING: Ignoring      invalid value 'share' for parameter 'security'     
[UBUNTU_videos]     
path=/home/rd/Videos     
comment=     
usershare_acl=S-1-1-0:F,     
guest_ok=y     
info_fn: file      /var/lib/samba/usershares/spare_room_1 is not a well formed      usershare      file.     
info_fn: Error was      Path is not a directory.     
[Videos]     
path=/home/rd/Videos     
comment=     
usershare_acl=S-1-1-0:F,     
guest_ok=y     

 
**hostname &#8211; Is this too long?**
========================

hostname     
rd-Precision-WorkStation-390     



 
**ifconfig**
=======

rd@rd-Precision-WorkStation-390:~$ ifconfig
 eth0      Link encap:Ethernet  HWaddr 00:1a:a0:1e:c8:66
           inet addr:192.168.1.65  Bcast:192.168.1.255 Mask:255.255.255.0
           inet6 addr: fe80::21a:a0ff:fe1e:c866/64 Scope:Link
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:2792 errors:0 dropped:0 overruns:0 frame:0
           TX packets:2095 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:2439745 (2.4 MB)  TX bytes:292365 (292.3 KB)
           Interrupt:17

 lo        Link encap:Local Loopback
           inet addr:127.0.0.1  Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:65536  Metric:1
           RX packets:370 errors:0 dropped:0 overruns:0 frame:0
           TX packets:370 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
           RX bytes:45282 (45.2 KB)  TX bytes:45282 (45.2 KB)



ping -c 3 192.168.1.73 to Windows pc
========================
[EMAIL="rd@rd-Precision-WorkStation-390:~$"]rd@rd-Precision-WorkStation-390:~$[/EMAIL] ping -c 3 192.168.1.73
 PING 192.168.1.73 (192.168.1.73) 56(84) bytes of data.
 64 bytes from 192.168.1.73: icmp_seq=1 ttl=128 time=0.266 ms
 64 bytes from 192.168.1.73: icmp_seq=2 ttl=128 time=0.239 ms
 64 bytes from 192.168.1.73: icmp_seq=3 ttl=128 time=0.259 ms
 --- 192.168.1.73 ping statistics ---
 3 packets transmitted, 3 received, 0% packet loss, time 1998ms
 rtt min/avg/max/mdev = 0.239/0.254/0.266/0.021 ms
 [EMAIL="rd@rd-Precision-WorkStation-390:~$"]rd@rd-Precision-WorkStation-390:~$[/EMAIL]












Windows pc:


Pinging 192.168.1.65 with 32 bytes of data:
Reply from 192.168.1.65: bytes=32 time<1ms TTL=64
Reply from 192.168.1.65: bytes=32 time<1ms TTL=64
Reply from 192.168.1.65: bytes=32 time<1ms TTL=64
Reply from 192.168.1.65: bytes=32 time<1ms TTL=64
Ping statistics for 192.168.1.65:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms


 
ipconfig /all

Windows IP Configuration
   Host Name . . . . . . . . . . . . : RDD-LEN-PC
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No
   DNS Suffix Search List. . . . . . : home
Ethernet adapter Local Area Connection 2:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Broadcom NetXtreme Gigabit Ethernet #2
   Physical Address. . . . . . . . . : 00-21-86-51-D4-2F
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
Ethernet adapter Local Area Connection:
   Connection-specific DNS Suffix  . : home
   Description . . . . . . . . . . . : Broadcom NetXtreme Gigabit Ethernet
   Physical Address. . . . . . . . . : 00-21-86-51-D4-2E
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::2c52:a1e7:d0dd:9114%10(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.1.73(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : 14 July 2014 17:34:19
   Lease Expires . . . . . . . . . . : 15 July 2014 17:34:19
   Default Gateway . . . . . . . . . : 192.168.1.254
   DHCP Server . . . . . . . . . . . : 192.168.1.254
   DHCPv6 IAID . . . . . . . . . . . : 234889606
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-18-13-2E-0F-00-21-86-51-D4-2E
   DNS Servers . . . . . . . . . . . : 192.168.1.254
   NetBIOS over Tcpip. . . . . . . . : Enabled
Tunnel adapter isatap.home:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : home
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
Tunnel adapter Local Area Connection* 9:
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2001:0:5ef5:79fb:1c15:1a82:926d:2a55(Pref
erred)
   Link-local IPv6 Address . . . . . : fe80::1c15:1a82:926d:2a55%11(Preferred)
   Default Gateway . . . . . . . . . : ::
   NetBIOS over Tcpip. . . . . . . . : Disabled
Tunnel adapter isatap.{F4A5C37B-1AE6-4087-9692-05F55FF72653}:
   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Microsoft ISATAP Adapter #3
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes

---

### Post by Morbius1 on 2014-07-14
**** Edit /etc/samba/smb.conf as root:
```
gksu gedit /etc/samba/smb.conf
```
[1] Find this line:
>   encrypt passwords      =      No     
And change No to Yes:
>   encrypt passwords      = Yes     
[2] Then add two lines - right under the workgroup line that looks like this:
```
netbios name = rd-390
name resolve order = bcast host lmhosts wins
```

****Then restart samba in this order:
```
sudo service smbd restart
```
```
sudo service nmbd restart
```

**** Now go into Nautilus and "unshare" /home/rd/Videos

You have 2 shares in 2 different places and they're different:

This is a classic share:
> [Videos]     
 path =      /home/rd/Videos     
 valid users = rd     
 read only = No     
This is a Samba Usershare:
> [Videos]     
path=/home/rd/Videos     
comment=     
usershare_acl=S-1-1-0:F,     
guest_ok=y     
It's anybody's guess which one Samba will obey so I suggest getting rid of the one you created in nautilus.

**** Now From the Ubuntu machine itself run the following command to see if you can connect to your own share:
```
 nautilus smb://rd-390/vidoes
```
**** Now see if you can connect to it from Windows:
```
\\rd-390\videos
```

[COLOR=#0000cd] **EDIT**: I guess I missed a step - don't know if you did this already or not but just in case make sure you  have added rd to the samba password database:[/COLOR]
```
 sudo smbpasswd -a rd
```

[COLOR=#0000cd]**EDIT2**: One more thing.[/COLOR]
If you are wondering what this is all about:
> WARNING: Ignoring      invalid value 'share' for parameter 'security'     
Samba3 has been warning folks that security = share is deprecated but nobody listened so in Samba4 they got rid of it completely. It should default to users by itself.

---

### Post by Morbius1 on 2014-07-14
Shutting down for the day so if all of that does nothing for you give your samba server a static ip address and connect to it directly and bypass all this Windows nonsense:

```
\\192.168.1.65\videos
```

---

### Post by Lagbehind on 2014-07-14
Morbius I can't thank you enough - this has worked.  I am still trying to digest what has happened, ie why it works and where I went wrong before.  One interesting thing I noted was that there were two shares:  

1. Videos - which did not require a password and took me straight to the test video I had placed in the folder and

2. UBUNTU_video - Which required a login and password and took me to the same location.  

In both cases I was able to play the video.

I guess the best way to understand what I have done in the foregoing is setup some more shares.  I may try this on some of the other drives in the pc.

Thanks again.

---

### Post by Lagbehind on 2014-07-15
One thing that has occurred to me is how do I remove all the shares in Ubuntu (mainly so that I can set it up again and practice)? Also is it possible to share other volumes or dives (or folders in them) on the same pc?

---

### Post by Morbius1 on 2014-07-15
> One thing that has occurred to me is how do I remove all the shares in  Ubuntu (mainly so that I can set it up again and practice)?
You created samba shares using two differnt methods so there are two different methods to remove them.

The samba usershares you can remove by going into Nautilus and right clicking the folder you shared and uncheck "Share this folder". Or you can go into /var/lib/samba/usershares and delete the share definition file you created for that folder.

The samba classic share can be removed with the same utility you used to create it: system-config-samba. Or you can delete the share definition part of smb.conf for that folder.

If you remove a share created by Nautilus no further action is required. If you remove a classic share you need to restart samba.

---

### Post by Lagbehind on 2014-07-15
Thanks again.  I assume setting up shares on other volumes is either not possible or too difficult at this stage.

---

### Post by Morbius1 on 2014-07-16
It's exactly the same only the path differs.

---

### Post by Lagbehind on 2014-07-16
Ok I'll give it a go - once again thanks

---

