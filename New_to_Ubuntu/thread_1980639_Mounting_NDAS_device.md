---
title: "Mounting NDAS device"
date: 2012-05-15
forum: New to Ubuntu
---

### Post by Toporagno on 2012-05-15
First of all let me tell you that I'm Linux-ignorant, I've just started using Ubuntu 12.04.
I've a Freecom II hardwired to the router (thomsonTG585 v7) hardwired to the pc that I can access from XP using the ximeta drivers. When I login to Ubuntu it doesn't appear in my network, windows network, workgroup whereas I'm able to see and act on my wife laptop. I've read a lot of posts (most of them are too complex for my knowledge of linux) and found this workaround on the net, but it isn't working for me :(
This is what I've done

installed smbfs

1) sudo apt-get install smbfs 

created the directory

2) sudo mkdir /media/freecom 

edited the nsswitch.conf

3) sudo nano /etc/nsswitch.conf

hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4

modified as

hosts: files mdns4_minimal [NOTFOUND=return] wins dns mdns4

installed winbind 

4) sudo apt-get install winbind

granted the permission to read and write 

5) sudo nano /root/.smbcredentials 

added these 2 rows:

username=marco
password=*****

6) sudo chmod 700 /root/.smbcredentials

then

7) sudo mount -a

nothing happend. I'm missing somenthing?

---

### Post by Jacobonbuntu on 2012-05-15
There is a pretty good manual [here]("http://www.mattvanstone.com/2007/11/automatically-mounting-windows-smb-shares-in-ubuntu-v3/") that will make your NAS automount. via "Network" you should be able to access your NAS as well, but that is not as handy as automounting.


about your actions:
I think you are making it more complicated than necessary; just installing smbfs, creating the fstab entry (see manual) and making the .cifscredentials file should do, of course you need a mount point, but you can create a folder in your home directory and link to that from the fstab file
----------------------------------------------------------------------------------------------------
3) sudo nano /etc/nsswitch.conf

hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4

modified as

hosts: files mdns4_minimal [NOTFOUND=return] wins dns mdns4

installed winbind 

4) sudo apt-get install winbind

granted the permission to read and write 

5) sudo nano /root/.smbcredentials 

added these 2 rows:

username=marco
password=*****

6) sudo chmod 700 /root/.smbcredentials

then

7) sudo mount -a

------------------------------------------------------------------------------------------------------

---

### Post by gordintoronto on 2012-05-15
Truly, I can't figure out what you are trying to say: "I've a Freecom II hardwired to the router (thomsonTG585 v7) hardwired to the pc that I can access from XP using the ximeta drivers."

---

### Post by Toporagno on 2012-05-16
> **gordintoronto said:**
> Truly, I can't figure out what you are trying to say: "I've a Freecom II hardwired to the router (thomsonTG585 v7) hardwired to the pc that I can access from XP using the ximeta drivers."
Hi gordintoronto, what I was trying to say is that I have a wired connection to the router and the NAS is also wired to the router. Sorry, English is not my first language.

---

### Post by Toporagno on 2012-05-16
Hi Jacobonbuntu, thanks for your reply and the link, it is very easy to read and follow.
I've just a couple of questions:
the guide says "Add the following line to the bottom of the file: //192.168.0.10/SHARENAME /media/Storage cifs auto,iocharset=utf8,uid=USER,gid=users,credentials=/root/.cifscredentials,file_mode=0775,dir_mode=0775 0 0


 You have to change the following information:

Change 192.168.0.10 to the IP address or DNS name of your server
(is this the ip address of the router? because when I launch ipconfig in windows I don't see an ip address for the NAS. Can I use the device ID instead which will be U30V8-DGH7C-M0E2G-***** or the mac address?)

Change SHARENAME to the share you want to mount
(is this the name of the NAS device as I see it in windows? If yes then how I've to write it because in windows it appears as NDAS Device 1 in the NDAS management and as Freecom Classic SL in my computer)
Thanks for your help

---

### Post by Jacobonbuntu on 2012-05-16
> **Toporagno said:**
> Hi jocobubuntu, thanks for your reply and the link, it is very easy to read and follow.
I've just a couple of questions:
the guide says "Add the following line to the bottom of the file: //192.168.0.10/SHARENAME /media/Storage cifs auto,iocharset=utf8,uid=USER,gid=users,credentials=/root/.cifscredentials,file_mode=0775,dir_mode=0775 0 0


 You have to change the following information:

Change 192.168.0.10 to the IP address or DNS name of your server
(is this the ip address of the router? because when I launch ipconfig in windows I don't see an ip address for the NAS. Can I use the device ID instead which will be U30V8-DGH7C-M0E2G-***** or the mac address?)

Change SHARENAME to the share you want to mount
(is this the name of the NAS device as I see it in windows? If yes then how I've to write it because in windows it appears as NDAS Device 1 in the NDAS management and as Freecom Classic SL in my computer)
Thanks for your help

Hi Toporagno,

you can find out the ip address with netdiscover; open a terminal and type "netdiscover". It will not be installed by default, but the terminal will offer you to do that for you. once installed type again "netdiscover and you will see a list of devices, connected to the network, and their ip addresses. 
The share name is usually the shared folder name. as an example, this is the line in my fstab file for the folder "werkmap_documenten" on my LG NAS. (The \040 is the way to deal with spaces):

//192.168.0.103/werkmap_documenten/documenten\040Jacob /home/jacob/Netwerkmap cifs auto,iocharset=utf8,uid=jacob,gid=users,credentials=/root/.cifscredentials,file_mode=0775,dir_mode=0775 0 0

---

### Post by Toporagno on 2012-05-16
Hello Jacobonbuntu,
I've installed and launched netdiscover as suggested, it took quite a while to perform (~6 hours) and this is the result:

    Currently scanning: 10.255.253.0/8   |   Screen View: Unique Hosts             
                                                                                 
  1415 Captured ARP Req/Rep packets, from 4 hosts.   Total size: 84900           
  _____________________________________________________________________________
    IP                               At MAC Address      Count  Len   MAC Vendor                    
  ----------------------------------------------------------------------------- 
  192.168.1.254      08:76:ff:5f:**:**    1340    80400   Unknown vendor            
  10.0.0.138                   08:76:ff:5f:**:**        35    2100     Unknown vendor               
  0.0.0.0                                 00:21:5d:79:**:**       14    840       Intel Corporate               
  192.168.1.64           00:21:5d:79:**:**       26    1560     Intel Corporate              
 *** glibc detected *** netdiscover: free(): invalid pointer: 0x08097120 ***
--------------------------------------------------------------------------------------------------------------------

The two ip address related to the mac address starting with 00: belong to my wife laptop.
The mac address starting with 08: is the mac address of the router (the mac address of my NAS start with 00:01)
I've tried both ip addresses but none works this is the line I've added at the bottom of fstab
//192.168.1.254/Music /media/freecom cifs auto,iocharset=utf8,uid=marco,gid=users,credentials =/root/.cifscredentials,file_mode=0775,dir_mode=0775 0 0
and when tried sudo mount -a I've received [mntent]: line 15 in /etc/fstab is bad

 I don't really know what to do... :confused:

---

### Post by redmk2 on 2012-05-16
> **Toporagno said:**
> ...
 I don't really know what to do... :confused:
The first thing you should do is REMOVE all the references to wins and winbind (e.g return the system back to its default settings).

There is no need to use winbind on a non Active Directory system.  It's really for mapping Linux users with Windows AD attributes.  

The wins reference in nsswitch.conf has nothing to do with winbind.  WINS is to store the NETBIOS names for multiple subnet situations.  Samba recommends NOT using a WINS server in a simple 1 subnet network.  Remove the wins listing in the nsswitch.conf file.

Do you have a Samba user defined on the NAS?

Once these are done we can see what else you need to allow you access to your NAS.

---

### Post by Toporagno on 2012-05-16
Hi Redmk2 thanks for stopping by and helping.

I've removed windbind with sudo apt-get remove winbind and removed the wins listing in the nsswitch.conf file.

Please bear with me, as I said I'm totally new to linux, what you mean by "Do you have a Samba user defined on the NAS?".

---

### Post by gordintoronto on 2012-05-16
The command: arp -a
should list the IP adresses of everything on your network, in a few seconds.

---

### Post by Toporagno on 2012-05-16
> **gordintoronto said:**
> The command: arp -a
should list the IP adresses of everything on your network, in a few seconds.
Hi gordintoronto here the result of arp
marco@marco-Linux-Ubuntu:~$ arp -a
bebox.config (192.168.1.254) at 08:76:ff:5f:**:** [ether] on eth0

---

### Post by redmk2 on 2012-05-16
> **Toporagno said:**
> Hi Redmk2 thanks for stopping by and helping.

I've removed windbind with sudo apt-get remove winbind and removed the wins listing in the nsswitch.conf file.

Please bear with me, as I said I'm totally new to linux, what you mean by "Do you have a Samba user defined on the NAS?".
No problem.  Everyone starts somewhere between noob and expert.  :-)

Is there a admin page for the NAS and have you created a user there?  Samba (on the NAS) requires both a system user and a Samba user.  Usually with the same login and password as on the client.

[COLOR="Blue"]**Edit**:  A quick comment on all this network (arp) info).  It's nice to know but it really doesn't relate to your problem. [/COLOR]  As long as all of your devices are in the same subnet range you are okay.  Yours seem to be in the 192.168.1.0/24 range (e.g. 192.168.1.254 and 192.168.1.64 ).  To see your own IP address you can do this```
ipconfig|grep Bcast
```

This will show your ip address and the brodcsat address and subnet mask.  Mine looks like this```
ipconfig|grep Bcast
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0

```

If all three devices (wife's laptop, your machine and the NAS) are in the same subnet then you can move on to other diagnosis.  You can see the IP address of the NAS on the admin page.  Regardless of what the MAC address is, you can set the IP address to be in your subnet.  Could the IP address 10.0.0.138  be the NAS IP address at the present time?

---

### Post by ecolom1269 on 2012-05-17
hello world.
for the love of the almighty, can someone please tell me that they have saved the contents of ximetas broken link on how to create a driver for their ndas devices.
 
[http://code.ximeta.com/trac-ndas/wiki/HowToBuildDEB](http://code.ximeta.com/trac-ndas/wiki/HowToBuildDEB)
 
please save me from having to connect to the evil xp machine I have at home.
 
down with microsoft!
 
Please help me register my drive to the network.
 
its a netdisk of course connected to a wireless router.
 
 
SORRY, THINK I POSTED THIS IN THE WRONG PLACE..SHOULD BE NDAS not NAS. .NDAS DOESN'T USE IP ADDRESS
 
BUT IF YOU KNOW HOW TO CONFIGURE A NDAS W/OUT XIMETAS LITTLE USELESS ADMIN TOOL 
]PLEASE LET ME KNOW.  I DID INSTALL THE DRIVERS IN UBUNTO 12.04 SUCCESSFULLY.. I JUST DONT
KNOW WHERE TO FIND A TOOL OR CHEAT TO REPLACE XMETA'S ADMIN TOOL SO I CAN REGISTER THE NDAS DEVICE.
 
NDAS REQUIRES YOU SET AND PASS A CODE EVERYTIME TO ACCESS THE DRIVE.

---

### Post by choppyfireballs on 2012-05-17
also somethign that might be preventing you from seeing the drive is if you don't have nfs installed. nfs is network file system so that MIGHT have something to do with it. 

sudo apt-get isntall nfs-common

---

### Post by Toporagno on 2012-05-17
Hi again Redmk2,
here the result of ifconfig

marco@marco-Linux-Ubuntu:~$ ifconfig | grep Bcast
          inet addr:192.168.1.65  Bcast:192.168.1.255  Mask:255.255.255.0

---

### Post by Toporagno on 2012-05-17
[QUOTE]SORRY, THINK I POSTED THIS IN THE WRONG PLACE..SHOULD BE NDAS not NAS. .NDAS DOESN'T USE IP ADDRESS[QUOTE]
My device is a NDAS device in windows *!!! As I said in my first post I use the ximeta drivers in XP.*

---

### Post by Toporagno on 2012-05-17
> **ecolom1269 said:**
> hello world.
for the love of the almighty, can someone please tell me that they have saved the contents of ximetas broken link on how to create a driver for their ndas devices.
 
[http://code.ximeta.com/trac-ndas/wiki/HowToBuildDEB](http://code.ximeta.com/trac-ndas/wiki/HowToBuildDEB)
 
please save me from having to connect to the evil xp machine I have at home.
 
down with microsoft!
 
Please help me register my drive to the network.
 
its a netdisk of course connected to a wireless router.
 
 
SORRY, THINK I POSTED THIS IN THE WRONG PLACE..SHOULD BE NDAS not NAS. .NDAS DOESN'T USE IP ADDRESS
 
BUT IF YOU KNOW HOW TO CONFIGURE A NDAS W/OUT XIMETAS LITTLE USELESS ADMIN TOOL 
]PLEASE LET ME KNOW.  I DID INSTALL THE DRIVERS IN UBUNTO 12.04 SUCCESSFULLY.. I JUST DONT
KNOW WHERE TO FIND A TOOL OR CHEAT TO REPLACE XMETA'S ADMIN TOOL SO I CAN REGISTER THE NDAS DEVICE.
 
NDAS REQUIRES YOU SET AND PASS A CODE EVERYTIME TO ACCESS THE DRIVE.

I've found this but the last release available is for Ubuntu 9.04 and the link to the install instructions doesn't work!!!
[http://linux.iocellnetworks.com/](http://linux.iocellnetworks.com/)

---

### Post by ecolom1269 on 2012-05-18
> **Toporagno said:**
> I've found this but the last release available is for Ubuntu 9.04 and the link to the install instructions doesn't work!!!
[http://linux.iocellnetworks.com/](http://linux.iocellnetworks.com/)
 
THe following file installs fine on ubunto prceise 12.04: 
Ubuntu 9.04 64Bit (by AF): 
[ndas-modules-src_1.1-24_all.deb]("http://linux.iocellnetworks.com/ubuntu/9-10/x64_86/ndas-modules-src_1.1-24_all.deb") 

 
I am at 64 bit and you? 
 
its only the admin tool doesn't work ([ndasadmin_1.1-24_i386.deb]("http://linux.iocellnetworks.com/ubuntu/9-10/x64_86/ndasadmin_1.1-24_amd64.deb") ) because of a dependency problem with libc6 I discovered.  I don't know enough about library files to go on from here but I am not tossing in the towl cuz I love my wire hating wife too much :lolflag:

---

### Post by ecolom1269 on 2012-05-18
Just to be clear.. I installed the deb file for the 9 ver ubunto that was a clean install w/out error.   
 
because I tried the latest files first.. the .tar files at the top and followed the steps to install those and those had too many errors. even after installing the patches.
 
you have to follow these steps to install the latest .tar files
 
wait..let me past the procedure for the tar file below... with the correct ver.
 
[EMAIL="fxb@fxb-ubuntu:~$"]fxb@fxb-ubuntu:~$[/EMAIL] sudo su
[sudo] password for fxb:
[EMAIL="root@fxb-ubuntu:/home/fxb"]root@fxb-ubuntu:/home/fxb[/EMAIL]# apt-get install dpkg-dev debhelper gcc bzip2
fakeroot module-assistant libc6-dev

Télécharger le tarball du driver ndas ici :
[http://code.ximeta.com/dev/current/linux/](http://code.ximeta.com/dev/current/linux/)
         ndas-1.1-24.x86_64.ta
         r.gz
 
 
[EMAIL="root@fxb-ubuntu:/home/fxb"]root@fxb-ubuntu:/home/fxb[/EMAIL]# cd
         ndas-1.1-24.x86_64.ta
         r.gz
 
[EMAIL="root@fxb-ubuntu:/home/fxb/ndas-1.1-24.X86_64"]root@fxb-ubuntu:/home/fxb/ndas-1.1-24.X86_64[/EMAIL]# dpkg-buildpackage -rfakeroot
[EMAIL="root@fxb-ubuntu:~/Bureau"]root@fxb-ubuntu:~/Bureau[/EMAIL]# m-a prepare
[EMAIL="root@fxb-ubuntu:~/Bureau"]root@fxb-ubuntu:~/Bureau[/EMAIL]# m-a auto-install ndas
[EMAIL="root@fxb-ubuntu:~/Bureau"]root@fxb-ubuntu:~/Bureau[/EMAIL]# /usr/sbin/ndasadmin register
xxxxx-xxxxx-xxxxx-xxxxx-xxxxx --name wedigital
[EMAIL="root@fxb-ubuntu:~/Bureau"]root@fxb-ubuntu:~/Bureau[/EMAIL]# cat /proc/ndas/devices/wedigital/slots 1
[EMAIL="root@fxb-ubuntu:~/Bureau"]root@fxb-ubuntu:~/Bureau[/EMAIL]# /usr/sbin/ndasadmin enable -s 1 -o w
Block device /dev/ndas-45818480-0 is ready to use.
[EMAIL="root@fxb-ubuntu:~/Bureau"]root@fxb-ubuntu:~/Bureau[/EMAIL]# blkid
/dev/sda1: UUID="C4071B34071A3DC" TYPE="ntfs"
/dev/sdb1: UUID="587C38D17C38AB9E" LABEL="Documents" TYPE="ntfs"
/dev/sdb2: UUID="B02CCE4A2CCE0B74" LABEL="Documents 2" TYPE="ntfs"
/dev/sdc1: UUID="cdca4622-c209-4723-a88e-8c88757dd046" SEC_TYPE="ext2"
TYPE="ext3"
/dev/sdc5: TYPE="swap" UUID="a3c53547-8257-4218-a7eb-b38648419353"
/dev/ndas-45818480-0p1: UUID="C41E6A0E1E69F9B6" LABEL="BlackBox320"
TYPE="ntfs"
[EMAIL="root@fxb-ubuntu:~/Bureau"]root@fxb-ubuntu:~/Bureau[/EMAIL]# mount -t ntfs-3g /dev/ndas-45818480-0p1 /media/
blackbox -o force
 
 
again i can't run any 'ndasadmin' command because that .tar or deb file doesn't install on precise.

---

### Post by ecolom1269 on 2012-05-18
I think I know whats wrong.. for the nadasadmin file, there is only 32 bit support.. and I have a 64 bit system.  I know this because the same file name is used.
 
damn it.. we can pray someone can write a driver.
 
there is an old link where you can build your own driver but it has since been broken.

---

### Post by ecolom1269 on 2012-05-18
topogarno,
 
qual es tu premer idioma?

---

### Post by ecolom1269 on 2012-05-18
Jacob,
 
You seem like you been around linux for a while.  May I ask you something?
my setup:
I have a wireless router with a security list setup.  meaning I have to register each mac address in the routher as addeded security in order for my wireless devices to work.
**Does this mean I have to list the devices such as my netdisk ndas disk that is physically attached to the router too?**
 
I ask you this because the list is under the section 'wireless'.
and because the normal arp -a command doesn't pick it up.
 
i would install netdiscover as you suggested but I think it would find the **same result as arp? **
 
**thanks**

---

### Post by Toporagno on 2012-05-18
> **ecolom1269 said:**
> topogarno,
 
qual es tu premer idioma?
Italiano ;)

---

### Post by ecolom1269 on 2012-05-18
por los menos los somos primos :)

---

### Post by Toporagno on 2012-05-18
> **ecolom1269 said:**
> I am at 64 bit and you? 

32 bit so it should work for me, (fingers crossed)

---

### Post by Toporagno on 2012-05-18
> **ecolom1269 said:**
> 

Télécharger le tarball du driver ndas ici :
[http://code.ximeta.com/dev/current/linux/](http://code.ximeta.com/dev/current/linux/)
         ndas-1.1-24.x86_64.ta
         r.gz
   
I don't understand what does it mean the link isn't working...

Don't mind I got them from here [http://code.ximeta.com/ximeta/ndas-1.1-24.tar.gz](http://code.ximeta.com/ximeta/ndas-1.1-24.tar.gz)

---

### Post by Toporagno on 2012-05-18
> **ecolom1269 said:**
> 
root@fxb-ubuntu:/home/fxb# cd ndas-1.1-24.x86_64.tar.gz
I've assumed that you meant 
root@fxb-ubuntu:/home/fxb# cd ndas-1.1-24.x86_64
without the extension .tar.gz

I've successfully build the package (of course I'm using the 32 bit package)

> **ecolom1269 said:**
> 
 root@fxb-ubuntu:~/Bureau# m-a prepare
root@fxb-ubuntu:~/Bureau# m-a auto-install ndas
root@fxb-ubuntu:~/Bureau# /usr/sbin/ndasadmin register
xxxxx-xxxxx-xxxxx-xxxxx-xxxxx --name wedigital

Can you explain to me what is Bureau? Is it Desktop?
Also I'm assuming that wedigital is the name you gave your NDAS device.
> **ecolom1269 said:**
> 
root@fxb-ubuntu:~/Bureau# blkid
/dev/sda1: UUID="C4071B34071A3DC" TYPE="ntfs"
/dev/sdb1: UUID="587C38D17C38AB9E" LABEL="Documents" TYPE="ntfs"
/dev/sdb2: UUID="B02CCE4A2CCE0B74" LABEL="Documents 2" TYPE="ntfs"
/dev/sdc1: UUID="cdca4622-c209-4723-a88e-8c88757dd046" SEC_TYPE="ext2"
TYPE="ext3"
/dev/sdc5: TYPE="swap" UUID="a3c53547-8257-4218-a7eb-b38648419353"
/dev/ndas-45818480-0p1: UUID="C41E6A0E1E69F9B6" LABEL="BlackBox320"
TYPE="ntfs"
Do you have your NDAS partitioned to 6? I have only one partition and it is ntfs so what should my line be or the lines are the result of blkid? 
EDIT: Again for the noobs like me blkid will locate and print block device.It  can  determine  the  type  of  content  (e.g. filesystem  or  swap)  that  a  block device holds, and also attributes (tokens, NAME=value pairs) from the content metadata  (e.g.  LABEL  or UUID fields).



And what does it mean the last line?
root@fxb-ubuntu:~/Bureau# mount -t ntfs-3g /dev/ndas-45818480-0p1 /media/
blackbox -o force

---

### Post by Toporagno on 2012-05-20
Right I've managed to understand what m-a is, just for the noobs like me it is the ModuleAssistant.
```
root@marco-Linux-Ubuntu:/home/marco/Desktop# m-a prepare
Getting source for kernel version: 3.2.0-24-generic-pae
Kernel headers available in /usr/src/linux-headers-3.2.0-24-generic-pae
Creating symlink...
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
build-essential set to manually installed.
The following packages were automatically installed and are no longer required:
  language-pack-zh-hans language-pack-kde-en language-pack-kde-zh-hans
  language-pack-kde-en-base kde-l10n-engb kde-l10n-zhcn
  language-pack-zh-hans-base firefox-locale-zh-hans
  language-pack-kde-zh-hans-base
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

Done!

```then I went for the next step
```
root@marco-Linux-Ubuntu:/home/marco/Desktop# m-a auto-install ndas
```with this output
ndas, what is ndas?


It is due to the fact that my ndas folder is in /home/ndas-1.1-24?
I should have launched the m-a prepare in home instead of Desktop?
As always I'm a bit confused...

---

### Post by Jacobonbuntu on 2012-05-20
ooops, please excuse me for the fact that I kind of left this thread alone. a lot happened here since the last time I read ...
I have been away for some days to get my boat ready for summer :) 

I will get back tomorrow, as it is kind of late for me...

---

### Post by Toporagno on 2012-05-21
> **Jacobonbuntu said:**
> 
I have been away for some days to get my boat ready for summer :) 
:tongue:  (envious)


Welcome back Jacobonbuntu hope you can help me I'm stuck... :(

---

### Post by haydaiphat on 2012-05-21
> **Toporagno said:**
> Hi Redmk2 thanks for stopping by and helping.

I've removed windbind with sudo apt-get remove winbind and removed the wins listing in the nsswitch.conf file.

Please bear with me, as I said I'm totally new to linux, what you mean by "Do you have a Samba user defined on the NAS?".

hi
[http://hayusd.blogspot.com]("http://hayusd.blogspot.com")

---

### Post by Toporagno on 2012-05-21
> **haydaiphat said:**
> hi
[http://hayusd.blogspot.com](http://hayusd.blogspot.com)
get lost you idiot

---

### Post by Toporagno on 2012-05-21
I want to start afresh, this is what I have done before:
```
marco@marco-ubuntu:~$ sudo su
[sudo] password for marco:
root@marco-ubuntu:/home/marco# apt-get install dpkg-dev debhelper gcc bzip2
fakeroot module-assistant libc6-dev
root@marco-ubuntu:/home/marco# cd ndas-1.1-24.x86_64.tar.gz
root@marco-ubuntu:/home/marco/ndas-1.1-24.X86_64# dpkg-buildpackage -rfakeroot
root@marco-ubuntu:~/Bureau# m-a prepare
```what should I do to roll back?

---

### Post by ecolom1269 on 2012-05-21
> **Toporagno said:**
> I've assumed that you meant 
root@fxb-ubuntu:/home/fxb# cd ndas-1.1-24.x86_64
without the extension .tar.gz
 
I've successfully build the package (of course I'm using the 32 bit package)
 
 
Can you explain to me what is Bureau? Is it Desktop?
Also I'm assuming that wedigital is the name you gave your NDAS device.
 
Do you have your NDAS partitioned to 6? I have only one partition and it is ntfs so what should my line be or the lines are the result of blkid? 
EDIT: Again for the noobs like me blkid will locate and print block device.It can determine the type of content (e.g. filesystem or swap) that a block device holds, and also attributes (tokens, NAME=value pairs) from the content metadata (e.g. LABEL or UUID fields).
 
 
 
And what does it mean the last line?
root@fxb-ubuntu:~/Bureau# mount -t ntfs-3g /dev/ndas-45818480-0p1 /media/
blackbox -o force
 
 
hey Toporagno, anything in front of the # sign is part of the prompt.. Bureau happens to be the prompt at the time the person listed this solution on one of the forums.  (its not my computer)
 
yes wedgital was the name of his device. I am not familiar with blkid but I imagine it list identification information of hard drives like the UUID? Im also a newbie.
 
I imagine you were able to b uild the package because you are on 32bit and I on 64 bit. I have sinced entered an idea with ubunto for ubunto to have built in support for ndas devices.  We ubunto users shouldn't have to rely on shared window machines to access our ndas drives on the network (thats what I plan on doing with this device since I lost hope that there is currently a 64 bit solution.
 
you are fortunate to have the abiltiy to register the ndas device and use it since you were able to load the package. you are all set. us 64 bit aren't as lucky.

---

### Post by Toporagno on 2012-05-22
> **ecolom1269 said:**
> 
 
I imagine you were able to build the package because you are on 32bit and I on 64 bit.
 
you are fortunate to have the abiltiy to register the ndas device and use it since you were able to load the package. you are all set. Well actually not 
something went wrong I don't know what or why.
Please bear with me and explain me what _**YOU**_ did when you installed the device:
Did you saved the NDAS driver to your /home/user?
Did you then installed the debhelper gcc bzip2 fakeroot module-assistant libc6-dev to your /home/user?
Did you then changed your directory to the NDAS and launched dpkg-buildpackage -rfakeroot?
***Did you then changed directory to Desktop?*** 

I'm asking these questions because, as I said in a previous post, this is what **I** did and after that I launched m-a prepare (which worked fine) and then m-a auto-install ndas and I got the message ```
ndas, what is ndas?
```
and when I tried to register the ndas device
 ```
/usr/sbin/ndasadmin register xxxxx-xxxxx-xxxxx-xxxxx-xxxxx --name MyDisk
``` I got the message ```
No such file or directory
```
I went to investigate and there is not such file in /usr/sbin/ BUT there is an executable with this name in my NDAS folder. So I'm wondering that probably I should have stayed in the NDAS directory.

My other big question is: how do I roll back to the previous state? What happened when I launched m-a prepare, did I installed something that I need to remove or I can just ignore it?

Lot of questions few answers... I want to understand what I'm doing otherwise I would have stayed with windows where you have only to click on a button and everything is done.

---

### Post by ecolom1269 on 2012-05-22
Toporgano,
 
can you open up a terminal and run this command
 
[FONT=Courier New]**ndasadmin register XXXXX-XXXXX-XXXXX-XXXXX-YYYYY -n device**[/FONT]
 
[FONT=Courier New]where xxxx's and yyyys is the id printed number under your ndas device[/FONT]
 
[FONT=Courier New]and device is the name you want to give it.[/FONT]
 
[FONT=Courier New]since you have everything installed all you need to do is register it.. if that is successful then do this as well..[/FONT]
 
**[FONT=Courier New]ndasadmin enable -s 1 -o w[/FONT]**
 
This will turn on the ndas device.
 
to answer your question ndas is a network drive.. unlike nas, it doesn't use tcp/ip. it can't be seen by the 'outside world' and is more secure. ndas drives also require you register them on the network. i can't register mine because ndasadmin.tar is only for 32bit. but you can!
 
 
you may also need to 
[FONT=Courier New]**cat /proc/ndas/devs**[/FONT]
[FONT=Courier New]to get the slot number. above number i am using default of 1.[/FONT]
[FONT=Courier New][/FONT] 
[http://www.techanswerguy.com/2007/02/mount-clntudpcreate-ximeta-ndas-drivers.html](http://www.techanswerguy.com/2007/02/mount-clntudpcreate-ximeta-ndas-drivers.html)
check this out
 
also you will need to mount the device. 
[FONT=courier new][root@demon ~]# mkdir /mnt/ndas
[root@demon ~]# mount -t [COLOR=black]**ext2**[/COLOR] /dev/ndas**-00003630328115** /mnt/ndas[/FONT]

[COLOR=black]**yours may/will be different for example if you are loading a dos drive ext2 will be -t msdos or -tfat32**
[/COLOR] its difficult for me to troubleshoot at this point because I don't have a working ndasadmin tool
read the thread above if you run into trouble.
 
good luck.

---

### Post by Toporagno on 2012-05-22
> **ecolom1269 said:**
> Toporgano,
 
can you open up a terminal and run this command
 
[FONT=Courier New]**ndasadmin register XXXXX-XXXXX-XXXXX-XXXXX-YYYYY -n device**[/FONT]
 
[FONT=Courier New]where xxxx's and yyyys is the id printed number under your ndas device[/FONT]
 
[FONT=Courier New]and device is the name you want to give it.[/FONT]
 
  
Where I should run the command from /home from /desktop or from /ndas???

I just opened a terminal and run the command and the output was

```
sudo: ndasadmin: command not found

```

---

### Post by ecolom1269 on 2012-06-07
Here is a link to the latest .tar file from David of iocellnetworks.com
 
[FONT=Courier][SIZE=2][FONT=Courier][SIZE=2]chose 64 bit or 32 bit.[/SIZE][/FONT]
 
[SIZE=2][FONT=Courier][http://www.iocellnetworks.com/linux/ndas/ndas-3.2-0_x86_64.tar](http://www.iocellnetworks.com/linux/ndas/ndas-3.2-0_x86_64.tar)[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier][http://www.iocellnetworks.com/linux/ndas/ndas-3.2.0_x86.tar](http://www.iocellnetworks.com/linux/ndas/ndas-3.2.0_x86.tar)[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier][FONT=Courier][SIZE=2][FONT=Courier][SIZE=2]instructions[/SIZE][/FONT]
 
[SIZE=2][FONT=Courier]tar -xvf ndas-3.2-0_xXX.tar[/FONT][/SIZE]
[SIZE=2][FONT=Courier]cd ndas-3.2-0[/FONT][/SIZE]
[SIZE=2][FONT=Courier]make[/FONT][/SIZE]
[SIZE=2][FONT=Courier]sudo make install[/FONT][/SIZE]
[SIZE=2][FONT=Courier]sudo /etc/init.d/ndas start[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier]After this, use the ndasadmin tool to register and connect to the [/FONT][/SIZE][/SIZE][/FONT][FONT=Courier][SIZE=2][FONT=Courier][SIZE=2]devices. For the instructions, try:[/SIZE][/FONT]
[/SIZE][/FONT]
[FONT=Courier][SIZE=2][FONT=Courier][SIZE=2]sudo ndasadmin[/SIZE][/FONT]
 
[SIZE=2][FONT=Courier]Once the NetDISK is enabled (connected) to the computer, you can find [/FONT][/SIZE]
[SIZE=2][FONT=Courier]the disk in the devices, or in the disk utility on Ubuntu.[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier]David will be looking into the .deb maker issue later on.[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier]If you have a bug or crash, turn off the netdisk, then hard boot the [/FONT][/SIZE]
[SIZE=2][FONT=Courier]computer and you can remove the install with the purgendas script.[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier]cd ndas-3.2-0[/FONT][/SIZE]
[SIZE=2][FONT=Courier]sudo sh purgendas[/FONT][/SIZE]
 
[/SIZE][/FONT]
Please let me know if you have success with this tar.
for help with registering the device and enabling just write back.
 
 
This tar was tested by david in ubunto 12.04 for 64 and 32 bit. :guitar:
[/FONT][/SIZE][/SIZE][/FONT]

---

### Post by Toporagno on 2012-06-08
> **ecolom1269 said:**
> Here is a link to the latest .tar file from David of iocellnetworks.com
 
[FONT=Courier][SIZE=2][FONT=Courier][SIZE=2]chose 64 bit or 32 bit.[/SIZE][/FONT]
 
[SIZE=2][FONT=Courier][http://www.iocellnetworks.com/linux/ndas/ndas-3.2-0_x86_64.tar](http://www.iocellnetworks.com/linux/ndas/ndas-3.2-0_x86_64.tar)[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier][http://www.iocellnetworks.com/linux/ndas/ndas-3.2.0_x86.tar](http://www.iocellnetworks.com/linux/ndas/ndas-3.2.0_x86.tar)[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier][FONT=Courier][SIZE=2][FONT=Courier][SIZE=2]instructions[/SIZE][/FONT]
 
[SIZE=2][FONT=Courier]tar -xvf ndas-3.2-0_xXX.tar[/FONT][/SIZE]
[SIZE=2][FONT=Courier]cd ndas-3.2-0[/FONT][/SIZE]
[SIZE=2][FONT=Courier]make[/FONT][/SIZE]
[SIZE=2][FONT=Courier]sudo make install[/FONT][/SIZE]
[SIZE=2][FONT=Courier]sudo /etc/init.d/ndas start[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier]After this, use the ndasadmin tool to register and connect to the [/FONT][/SIZE][/SIZE][/FONT][FONT=Courier][SIZE=2][FONT=Courier][SIZE=2]devices. For the instructions, try:[/SIZE][/FONT]
[/SIZE][/FONT]
[FONT=Courier][SIZE=2][FONT=Courier][SIZE=2]sudo ndasadmin[/SIZE][/FONT]
 
[SIZE=2][FONT=Courier]Once the NetDISK is enabled (connected) to the computer, you can find [/FONT][/SIZE]
[SIZE=2][FONT=Courier]the disk in the devices, or in the disk utility on Ubuntu.[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier]David will be looking into the .deb maker issue later on.[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier]If you have a bug or crash, turn off the netdisk, then hard boot the [/FONT][/SIZE]
[SIZE=2][FONT=Courier]computer and you can remove the install with the purgendas script.[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier]cd ndas-3.2-0[/FONT][/SIZE]
[SIZE=2][FONT=Courier]sudo sh purgendas[/FONT][/SIZE]
 
[/SIZE][/FONT]
Please let me know if you have success with this tar.
for help with registering the device and enabling just write back.
 
 
This tar was tested by david in ubunto 12.04 for 64 and 32 bit. :guitar:
[/FONT][/SIZE][/SIZE][/FONT]
Thanks man you're a :KS

Everything went fine  :biggrin:


but when I tried to access the disk I got this message:

```
Error mounting: mount exited with exit code 12: Failed to read last sector (321669431): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/ndas-xxxxxxxx-0p1': Invalid argument
The device '/dev/ndas-xxxxxxxx-0p1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```
the disk is NTFS formatted in just one partition, and when I look at it with GParted it says unallocated 153.38 GiB, any idea?

---

### Post by manlug on 2012-06-08
Hi,
I have sungoo disk (ndas).
Ubuntu 12.04, 3.2.0-24-generic and x86_64.
I donwload ndas-3.2.0.tar from ndas4linux, uncompress, 

test1:
$cd ndas-3.2.0
$make
make: No se hace nada para «ndaslinux».

test2:
$ ndas-3.2.0/script/build/build-x86_64.sh
make[1]: se sale del directorio «/<path>/ndas-3.2.0»
[email]release@ndas4linux.iocellnetworks.com[/email]'s password:

what password ?

Result:
I haven't clue.

---

### Post by Toporagno on 2012-06-09
> **Toporagno said:**
> 

```
Error mounting: mount exited with exit code 12: Failed to read last sector (321669431): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/ndas-xxxxxxxx-0p1': Invalid argument
The device '/dev/ndas-xxxxxxxx-0p1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```the disk is NTFS formatted in just one partition, and when I look at it with GParted it says unallocated 153.38 GiB, any idea?

Ok this is most probably due to the fact that the NDAS disk wasn't properly dismounted in windows, you have to use "remove safely".

Now I'm getting a different error message when I type the following codes:

```
marco@marco-Linux-Ubuntu:~/ndas-3.2.0$ sudo ndasadmin enable -s 1 -o w
[sudo] password for marco: 
enable: Block device /dev/ndas-50043187-0 is already enabled.
marco@marco-Linux-Ubuntu:~/ndas-3.2.0$ sudo ndasadmin disable enabled -s 1 
/dev/ndas-50043187-0 is disabled
marco@marco-Linux-Ubuntu:~/ndas-3.2.0$ sudo ndasadmin enable -s 1 -o r
could not set the scheduler for ndas-50043187-0 
Block device /dev/ndas-50043187-0 is ready to use.
```
```
Error mounting: mount exited with exit code 18: Error opening '/dev/ndas-50043187-0p1': Read-only file system
Failed to mount '/dev/ndas-50043187-0p1': Read-only file system
```

and I cannot see the disk in GParted.

---

### Post by Toporagno on 2012-06-09
Ok after restarting a couple of times and switching off and on the NDAS I can now see the disk in GParted, but it shows it as unallocated and I'm getting the first error message

Error mounting: mount exited with exit code 12: Failed to read last sector (321669431): Invalid argument HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,    or it was not setup correctly (e.g. by not using mdadm --build ...),    or a wrong device is tried to be mounted,    or the partition table is corrupt (partition is smaller than NTFS),    or the NTFS boot sector is corrupt (NTFS size is not valid). Failed to mount '/dev/ndas-xxxxxxxx-0p1': Invalid argument The device '/dev/ndas-xxxxxxxx-0p1' doesn't seem to have a valid NTFS. Maybe the wrong device is used? Or the whole disk instead of a partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

---

### Post by Toporagno on 2012-06-09
Ok I've resized the partition on the NDAS, I've left 1.5 Gb unallocated and now everything works fine.

:guitar:

---

### Post by Toporagno on 2012-06-09
Just a quick digest on how to do it in Precise Pangoline

Here is a link to the latest .tar file from David of iocellnetworks.com
 
[FONT=Courier][SIZE=2][FONT=Courier][SIZE=2]chose 64 bit or 32 bit.[/SIZE][/FONT]
 
[SIZE=2][FONT=Courier][http://www.iocellnetworks.com/linux/...2-0_x86_64.tar]("http://www.iocellnetworks.com/linux/ndas/ndas-3.2-0_x86_64.tar")[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier][http://www.iocellnetworks.com/linux/...-3.2.0_x86.tar]("http://www.iocellnetworks.com/linux/ndas/ndas-3.2.0_x86.tar")[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier][FONT=Courier][SIZE=2][FONT=Courier][SIZE=2]instructions[/SIZE][/FONT]
 
[SIZE=2][FONT=Courier]tar -xvf ndas-3.2-0_xXX.tar[/FONT][/SIZE]
[SIZE=2][FONT=Courier]cd ndas-3.2-0[/FONT][/SIZE]
[SIZE=2][FONT=Courier]make[/FONT][/SIZE]
[SIZE=2][FONT=Courier]sudo make install[/FONT][/SIZE]
[SIZE=2][FONT=Courier]sudo /etc/init.d/ndas start[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier]After this, use the ndasadmin tool to register and connect to the [/FONT][/SIZE][/SIZE][/FONT][FONT=Courier][SIZE=2][FONT=Courier][SIZE=2]devices. For the instructions, type:[/SIZE][/FONT]
[/SIZE][/FONT]
[FONT=Courier][SIZE=2][FONT=Courier][SIZE=2]sudo ndasadmin

It will give you all the available options.

sudo ndasadmin register XXXX-XXXX-XXXX-XXXX-WWWWW -n NDASName
[/SIZE][/FONT]  
sudo ndasadmin enable -s n -o x

where n is the number of the slot and x is the permission for the access mode.

[SIZE=2][FONT=Courier]Once the NetDISK is enabled (connected) to the computer, you can find [/FONT][/SIZE][SIZE=2][FONT=Courier]the disk in the devices, or in the disk utility on Ubuntu.[/FONT][/SIZE]
 

[SIZE=2][FONT=Courier]If you have a bug or crash, turn off the netdisk, then hard boot the [/FONT][/SIZE][SIZE=2][FONT=Courier]computer and you can remove the install with the purgendas script.[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier]cd ndas-3.2-0[/FONT][/SIZE]
[SIZE=2][FONT=Courier]sudo sh purgendas[/FONT][/SIZE][/SIZE][/FONT][/FONT][/SIZE][/SIZE][/FONT]

If you previously mounted the NDAS in Windows be sure to unmount it properly using "safely remove" and also make sure there is some space unallocated in the NDAS.

Enjoy

---

### Post by manlug on 2012-06-10
> **Toporagno said:**
> Just a quick digest on how to do it in Precise Pangoline

Here is a link to the latest .tar file from David of iocellnetworks.com
 
[FONT=Courier][SIZE=2][FONT=Courier][SIZE=2]chose 64 bit or 32 bit.[/SIZE][/FONT]
 
[SIZE=2][FONT=Courier][http://www.iocellnetworks.com/linux/...2-0_x86_64.tar]("http://www.iocellnetworks.com/linux/ndas/ndas-3.2-0_x86_64.tar")[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier][http://www.iocellnetworks.com/linux/...-3.2.0_x86.tar]("http://www.iocellnetworks.com/linux/ndas/ndas-3.2.0_x86.tar")[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier][FONT=Courier][SIZE=2][FONT=Courier][SIZE=2]instructions[/SIZE][/FONT]
 
[SIZE=2][FONT=Courier]tar -xvf ndas-3.2-0_xXX.tar[/FONT][/SIZE]
[SIZE=2][FONT=Courier]cd ndas-3.2-0[/FONT][/SIZE]
[SIZE=2][FONT=Courier]make[/FONT][/SIZE]
[SIZE=2][FONT=Courier]sudo make install[/FONT][/SIZE]
[SIZE=2][FONT=Courier]sudo /etc/init.d/ndas start[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier]After this, use the ndasadmin tool to register and connect to the [/FONT][/SIZE][/SIZE][/FONT][FONT=Courier][SIZE=2][FONT=Courier][SIZE=2]devices. For the instructions, type:[/SIZE][/FONT]
[/SIZE][/FONT]
[FONT=Courier][SIZE=2][FONT=Courier][SIZE=2]sudo ndasadmin

It will give you all the available options.

sudo ndasadmin register XXXX-XXXX-XXXX-XXXX-WWWWW -n NDASName
[/SIZE][/FONT]  
sudo ndasadmin enable -s n -o x

where n is the number of the slot and x is the permission for the access mode.

[SIZE=2][FONT=Courier]Once the NetDISK is enabled (connected) to the computer, you can find [/FONT][/SIZE][SIZE=2][FONT=Courier]the disk in the devices, or in the disk utility on Ubuntu.[/FONT][/SIZE]
 

[SIZE=2][FONT=Courier]If you have a bug or crash, turn off the netdisk, then hard boot the [/FONT][/SIZE][SIZE=2][FONT=Courier]computer and you can remove the install with the purgendas script.[/FONT][/SIZE]
 
[SIZE=2][FONT=Courier]cd ndas-3.2-0[/FONT][/SIZE]
[SIZE=2][FONT=Courier]sudo sh purgendas[/FONT][/SIZE][/SIZE][/FONT][/FONT][/SIZE][/SIZE][/FONT]

If you previously mounted the NDAS in Windows be sure to unmount it properly using "safely remove" and also make sure there is some space unallocated in the NDAS.

Enjoy

Hi, 
the file "ndas-3.2-0/ndas" have a line with "/var/log/messages", in Ubuntu from Natty Narwhal not exits "/var/log/messages". 
Is this correct ?

---

### Post by ecolom1269 on 2012-06-11
> **manlug said:**
> Hi,
I have sungoo disk (ndas).
Ubuntu 12.04, 3.2.0-24-generic and x86_64.
I donwload ndas-3.2.0.tar from ndas4linux, uncompress, 
 
test1:
$cd ndas-3.2.0
$make
make: No se hace nada para «ndaslinux».
 
test2:
$ ndas-3.2.0/script/build/build-x86_64.sh
make[1]: se sale del directorio «/<path>/ndas-3.2.0»
[EMAIL="release@ndas4linux.iocellnetworks.com"]release@ndas4linux.iocellnetworks.com[/EMAIL]'s password:
 
what password ?
 
Result:
I haven't clue.
 
manlug, prefieres el espanol O engleas?
please tell me what type of hardware you have.
you have the wrong steps above.. please follow the steps above beginning
with the tar command after you download. then the commands that follow must be executed in the correct directory.

---

### Post by ecolom1269 on 2012-06-11
> **manlug said:**
> Hi, 
the file "ndas-3.2-0/ndas" have a line with "/var/log/messages", in Ubuntu from Natty Narwhal not exits "/var/log/messages". 
Is this correct ?
 
I got the same thing and my ndas drive is up and running.

---

### Post by ecolom1269 on 2012-06-11
> **Toporagno said:**
> Ok I've resized the partition on the NDAS, I've left 1.5 Gb unallocated and now everything works fine.
 
:guitar:
 
tHANKS!
 
yeah, I had to move data and partition the drive as well.. after that everything works fine..although after testing/comparing speed with windows..i have to admit the penguin is much slower :(...but David is working on a fix for this i think.
 
.  be sure you use either the ethernet on a hub or the usb on a usb hub.  if you use both cables the netdisk will take itself offline and the manual forbids using both. 
 
 I know this because I share my netdisk with my playstation 3.. I am able to do this because I disconnect the ethernet cable and plug in the usb when I use the playstation 3.  
 
but I have a media drive now where i can download all kinds of music with frostwire to the netdrive with my lap top and listen to the music on my sound system and ps3.
 
I wish the write speed was faster than windows tho :)

---

### Post by ecolom1269 on 2012-06-11
> **ecolom1269 said:**
> I got the same thing and my ndas drive is up and running.
 
what i mean is don't worry about this message

---

### Post by ecolom1269 on 2012-06-13
I found the solution if anyone writes back i will post it.

---

### Post by manlug on 2012-07-05
Claramente prefiero el español. Thanks.
But, I need to practice ...

following the steps mentioned, I work well.
I have only one problem when restarting I have to re-run 

> sudo /etc/init.d/ndas start

---

### Post by George Lama on 2012-11-18
This really was a very helpful post and helped me out quite a bit in getting my NDAS Netdisk unit installed under Linux.

I do have one little problem, I installed the drivers correctly and I can mount my drive perfectly, can access the folders and everything BUT I can't write, seems I don't have write presmissions.

On console I fallowed all the steps specified for the access mode, both reading and writing and still can't seem to have permission to write.

When in console using nasadmin, I found this : 

"When device is registered with serial, the device can be only used in read-only mode."

When I mount my NDAS and use the command : cat /proc/ndas/devs

The output shows my slot and also a serial, so I think that this might be the problem, does anyone know how to register the device without serial? if that is my problem.

Any help would be appreciated, I have both windows 7 and XP computers on my home network and they both can connect to the NDAS perfectly with bot read and write permissions, the problem is with Linux.

Any help would be greatly appreciated !

---

