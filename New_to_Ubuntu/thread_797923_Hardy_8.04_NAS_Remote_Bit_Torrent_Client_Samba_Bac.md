---
title: "Hardy 8.04 NAS Remote Bit Torrent Client Samba Backup Windows Login Server"
date: 2008-05-17
forum: New to Ubuntu
---

### Post by cackles on 2008-05-17
This is for XP users that want to build a NAS enclosure out of parts without the overheads of a retail box. 

Basically I couldnt afford a $300-$500 for an enclosure to keep big disks in. So I Googled and got a tut on 

building your own NAS. I made one out an old XBox I had. Next day I took these parts and EVENTUALLY worked out what to do, I think I installed like 10 times.

Duron 900
Old iWill RAID mobo
512MB RAM
64MB something AGP video card
30GB HDD
Ubuntu 8.04 LTS Server Edition

Now all I need are a couple of big disks :) Right now Im thinking 2 x 1TB and I wonder, if this is archived and read 

in 2 years how 2TB total sounds lol.


This is how I have setup a shared resource for torrents and files. Basically you can tell it to download, everyone 

can access it and you can switch any other computers on your network off and leave it to download. Its a NAS, Bit 

Torrent client, webserver and if you add it in RAID/backup. Theres also all the other possibilities that go with 

Ubuntu but heres the quick 'n' dirty NAS BT client version. If you add in a dynamic IP redirect service you could 

queue your torrents from anywhere in the world, even using a mobile phone.



This 'guide' assumes your network is already setup correctly, your client machines are XP and you, like me, have 

little experience with any of this. This is my 2nd day (less than 20hrs) with Ubuntu, so difficulty level is set to 

easy.





I wont go into the basic obvious setup stuff unless its referred to later.



Hostname: The name you want to call your box (I sometimes refer to it as yourboxname).

Guided - Use entire partition.

Username and password: This will be your main account for logging on and doing 'stuff'.

http proxy: if you dunno what it is you prolly dont have one.

We are going to be using Samba share, however at software selection DO NOT SELECT SAMBA SHARE. Only select these two:

LAMP server
Openssh server

MySQL root password: I use a different here than from my username/password earlier.

After reboot login using the Username and password from setup.

Now type these in:

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install samba

Now go download [PuTTY]("http://www.chiark.greenend.org.uk/~sgtatham/putty/").

Start PuTTY and in the Hostname/IP box type the name you gave your box earlier and hit open.

In PuTTY lets make a shared folder called shared that everyone can eventually use:

```
sudo mkdir /shared
sudo chmod 0777 /shared
```

Now lets backup and remake the config file for samba:

```
sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.bak
sudo nano /etc/samba/smb.conf
```
Paste this in:

```
[global]
    ; General server settings
    netbios name = hostname
    server string = ishare
    workgroup = MSHOME
    announce version = 5.0
    socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_$

    passdb backend = tdbsam
    security = user
    null passwords = true
    username map = /etc/samba/smbusers
    name resolve order = hosts wins bcast

    wins support = yes

    printing = CUPS
    printcap name = CUPS

    syslog = 1
    syslog only = yes

; NOTE: If you need access to the user home directories uncomment the
; lines below and adjust the settings to your hearts content.
;[homes]
;    valid users = %S
;    create mode = 0600
;    directory mode = 0755
;    browseable = no
;    read only = no
;    veto files = /*.{*}/.*/mail/bin/

; NOTE: Only needed if you run samba as a primary domain controller.
; Not needed as this config doesn't cover that matter.
;[netlogon]
    ;path = /var/lib/samba/netlogon
    ;admin users = Administrator
    ;valid users = %U
    ;read only = no

; NOTE: Again - only needed if you're running a primary domain controller.
;[Profiles]
    ;path = /var/lib/samba/profiles
    ;valid users = %U
    ;create mode = 0600
    ;directory mode = 0700
    ;writeable = yes
    ;browseable = no

; NOTE: Inside this place you may build a printer driver repository for
; Windows - I'll cover this topic in another HOWTO.
[print$]
    path = /var/lib/samba/printers
    browseable = yes
    guest ok = yes
    read only = yes
    write list = root
    create mask = 0664
    directory mask = 0775

[printers]
    path = /tmp
    printable = yes
    guest ok = yes

; Uncomment if you need to share your CD-/DVD-ROM Drive
;[DVD-ROM Drive]
    ;path = /media/cdrom
    ;browseable = yes
    ;read only = yes
    ;guest ok = yes

[Share Name]
    path = /shared
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
;    force user = yourlogin
;    force group = yourlogin
```


Parts to change

```
[global]
    ; General server settings
    netbios name = hostname		<- The Hostname of your box
    server string = ishare		<- A description for your box
    workgroup = MSHOME			<- The workgroup your computers are on, this is the most common XP

[Share Name]	<------------------------- This is what it will be called on the network			
    path = /shared			<- The shared folder you made
    browseable = yes
    read only = no
    guest ok = no
    create mask = 0644
    directory mask = 0755
;    force user = yourlogin		<- I have these commented out, if at the end yours doesnt work 
;    force group = yourlogin		<- delete both the ; and put your PuTTY/root login name there
```

Press ```
control + x
``` to save then yes etc. to exit.

Restart Samba:

```
sudo invoke-rc.d samba restart
```

Add a pass to your samba root logon details:

```
sudo smbpasswd -L -a yourlogin
sudo smbpasswd -L -e yourlogin
```

Add user logons so everyone/all the computers can get access to the share, replace newuser with the username you 

desire and the new smb password thats requested with one you want:

```
sudo useradd -s /bin/true newuser
sudo smbpasswd -L -a newuser
sudo smbpasswd -L -e newuser
```

Now even with my own computer I have made my own extra, non root connected user details for samba. The reason I 

done this was so that Windows isnt storing my boxes root user details. 

In 'My Computer' goto Tools > Map Network Drive
Pick a letter
In folder enter \\boxhostname\Share Name

Enter one of the users you created details.

And thats your shared space.

Now get the torrent client:

```
sudo apt-get install torrentflux
```

Choose all the default options as they give you them until the MySQL password request. Enter the same password here 

as you did in setup for the MySQL database.

The next box is for a password between Torrentflux and MySQL, you dont need to know it or make it, a random one 

will do.

Restart Apache = Yes.

Now in your browser go to [http://yourboxname/torrentflux](http://yourboxname/torrentflux) obviously with yourboxname as the name of your box.

You can make up a login name and a password here, the first details entered will become the admin account.

The first page after logging in is settings. Change Path from /var/cache/torrentflux/ to the /shared/ directory you 

created earlier.

Change Max Upload Rate to what you would use.

Change Max Upload Connections to something sensible, I have 150, I dunno if its sensible but its better than 4.

Update settings.



You may need to port forward/virtual server any router you have to the IP of your box. I have a D-Link Dir-655 and 

had to add port 80 to virtual server for my web admin and port forward 49000-50000 for what I named 'Torrent1' for 

Torrentflux. I changed my ports for Torrentflux from the default to 49000-50000 in Torrentflux settings page.



For more detailed info on the Samba install I used this for reference 

[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba) however, that method didnt work for me.

For Dynamic IP skip to step 5 in this torrentflux tut [http://ubuntuforums.org/showthread.php?p=1566206#post1566206](http://ubuntuforums.org/showthread.php?p=1566206#post1566206)

Both of those I used to get this working, so thanks to them. But hey, how come Samba doesnt work with a default 

install of it during setup? Maybe its a simple command that needs added but even if its not there its a bug.

Anyways to streamline this method I have?

---

### Post by k420 on 2008-05-18
So you said you used an old xbox.  can you include more steps so we can see how you installed ubuntu on it and added the hdd(was it an xbox hdd or did you add a regular pc hdd, if so how)

---

### Post by cackles on 2008-05-19
I used a solderless mod chip to gain FTP to the XBox. I had already soldered the points on the box to allow TSOP flash. I copied UXE softmod to the XBox because its the only one I could actually get to work. I removed the chip and using the softmod booted the EurAsia flash disk and loaded up the latest cromwell BIOS. Then with Cromwell running I loaded in Xebian. Then removed the DVD, put a molex splitter in and that was that. It was an XBox running xebian, you can install xubuntu too. I also robbed another broken box of its 4 RAM chips, youll want a hot air gun or a torch like I used. That gave it 128MB of RAM total.

Once the TSOP is flashed you can install a normal HDD as the primary and keep the DVD or replace it with a 2nd drive.

---

