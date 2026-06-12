---
title: "Ubuntu 12.04 LTS....Samba.....Crash course...."
date: 2013-03-15
forum: New to Ubuntu
---

### Post by SolomonMan on 2013-03-15
All,
I have two fresh installs of Ubuntu 12.04 which I have installed Samba. 

sudo apt-get install samba 
sudo apt-get install smbfs

Created a share on both machines called Transfer.  (machine names Christopher-Desktop and Chris-Linux-Main)
Created two mount points - Chris-Linux1-Transfer and Chris-Linux2-Transfer.

The smb.conf files are as follows (the rest of the smb.conf files are just default install versions);

#machine chris-linux-main
             
                
[Transfer]
path = /home/christopher/Transfer
comment = Transfer directory
available = yes
browsable = yes
public = yes
writable = yes

#machine christopher-desktop

[Transfer]
path = /home/christopher/Transfer
comment = Transfer directory 
available = yes
browsable = yes
public = yes
writable = yes

I have confirmed that both the smbd and nmbd services are running. (by doing a sudo service smbd restart etc)

I can do a smbclient -L from either machine and get responses similar to ;

(from the chris-linux-main)
 sudo smbclient -L christopher-desktop

Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.6.3]

    Sharename       Type      Comment
    ---------       ----      -------
    print$          Disk      Printer Drivers
    Transfer        Disk      Shared Folder Linux 2
    IPC$            IPC       IPC Service (christopher-desktop)
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.6.3]

    Server               Comment
    ---------            -------
    CHRIS-LINUX-MAI      chris-linux-main
    CHRISTOPHER-DESK     christopher-desktop
    MELISSA-PC           

    Workgroup            Master
    ---------            -------
    BRTSI                BRTWS193
    WORKGROUP            CHRISTOPHER-DESKTOP


(from  the christopher-desktop - smbclient -L chris-linux-main does not work  (NT_STATUS_BAD_NETWORK_NAME) but the IP Address of chris-linux main does  fine.

smbclient -L 192.168.1.67 

Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.6.3]

    Sharename       Type      Comment
    ---------       ----      -------
    print$          Disk      Printer Drivers
     Transfer        Disk      
    IPC$            IPC       IPC Service (chris-linux-main)
    HL-2170W-series Printer   Brother HL-2170W series
    Brother-HL-2170W Printer   Brother HL-2170W
Domain=[WORKGROUP] OS=[Unix] Server=[Samba 3.6.3]
 
    Server               Comment
    ---------            -------
    CHRIS-LINUX-MAIN     chris-linux-main
    CHRISTOPHER-DES      christopher-desktop

    Workgroup            Master
    ---------            -------
     WORKGROUP            CHRISTOPHER-DES

So looking at the above I felt things are going good minus the chris-linux-main ip address problem. 

I did from my web browser (FireFox) commands similar to;

smb://christopher-desktop/Transfer
but smb://chris-linux-main/Transfer did not work but smb://<ip address of chris-linux-main>/Transfer worked fine.

Also  I noticed Nautilus was able to see both shares and able to move files  to and from without issue. So I was feeling more confident.

So I manually mounted both shares on each machine;
sudo mount -t smbfs //christopher-desktop/transfer /home/christopher/Desktop/Chris-Linux2-Transfer
sudo mount -t smbfs //[<IP Address of Chris-linux-main>/transfer]("http://192.168.1.67/transfer") /home/christopher/Desktop/Chris-Linux1-Transfer


The  only thing I noticed is I was not able to specify chris-linux-main but  the IP Address worked fine similar to the web browser and smbclient  approach.

So I decided to do edit my \etc\fstab to have the linux shares mount after a boot up without me running the mount command manually. I also created a created credential files with root ownership etc.

-rw-r--r-- 1 root root 42 Mar 15 12:10 sambapasswords

I tried mounting;
//[<ip address of chris-main-linux/transfer]("http://192.168.1.67/transfer") /home/christopher/Desktop/Chris-Linux1-Transfer smbfs defaults,credentials=/etc/sambapasswords 0 0

I  tested with a mount -a command and it did not report any errors. Then  after a reboot the mounted share showed up as I would expect and  everything moved to and from.

So I tried from the other machine (chris-main-linux)
//christopher-desktop/transfer   /home/christopher/Desktop/Chris-Linux2-Transfer smbfs   defaults,credentials=/etc/sambapasswords 0 0

Tried the mount -a and I received a
mount error(13): Permission denied

did a mount -av and I received the following;
mount: proc already mounted on /proc
mount.cifs  kernel mount options:  ip=192.168.1.74,unc=\\christopher-desktop\Transfer,credentials=/etc/sambapasswords,ver=1,user=christopher,pass=********
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

So now my questions;
Why does chris-linux-main have to be referred by its IP Address?
Why does the mounting through fstab on chris-main-linux not work when mounting the christopher-desktop transfer share?

Thanks,
Chris

---

### Post by SolomonMan on 2013-03-16
All,
I did figure out the chris-linux-main has to use ip address issue....I believe.

I installed winbind and changed the /etc/nsswitch.conf file appropriately by adding wins.

I also updated to cifs (both machines) similar to below in the fstab files;

//christopher-desktop/Transfer  /home/christopher/Desktop/Chris-Linux2-Transfer cifs    credentials=/etc/sambapasswords,iocharset=utf8,file_mode=0777,dir_mode=0777     0       0


Now there are no IP Address being used but still getting;
mount: proc already mounted on /proc
mount.cifs kernel mount options: ip=192.168.1.74,unc=\\christopher-desktop\Transfer,credentials=/etc/sambapasswords,iocharset=utf8,file_mode=0777,dir_mode=0777,ver=1,user=christopher,pass=********
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

Any ideas why I am getting a permissions denied?

Thanks,
Chris

---

### Post by bab1 on 2013-03-16
> **SolomonMan said:**
> All,
I did figure out the chris-linux-main has to use ip address issue....I believe.

I installed winbind and changed the /etc/nsswitch.conf file appropriately by adding wins.

I also updated to cifs (both machines) similar to below in the fstab files;

//christopher-desktop/Transfer  /home/christopher/Desktop/Chris-Linux2-Transfer cifs    credentials=/etc/sambapasswords,iocharset=utf8,file_mode=0777,dir_mode=0777     0       0


Now there are no IP Address being used but still getting;
mount: proc already mounted on /proc
mount.cifs kernel mount options: ip=192.168.1.74,unc=\\christopher-desktop\Transfer,credentials=/etc/sambapasswords,iocharset=utf8,file_mode=0777,dir_mode=0777,ver=1,user=christopher,pass=********
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

Any ideas why I am getting a permissions denied?

Thanks,
Chris

The short answer is the hostname needs to be less than 15 characters or you need to specify a netbios name with less than 15 characters.  Samba converts the machines hostname to a netbios name by default.  If the hostname is longer than 15 characters it will error.  Just like is says   ```
 christopher-desktop - smbclient -L chris-linux-main does not work (**[COLOR="#FF0000"]NT_STATUS_BAD_NETWORK_NAME[/COLOR]** )
```

You need to either use a shorter hostname or define a shorter netbios name in the [global] section of the smb.conf file ```
netbios name = short_name 
```

You should also remove Winbind.  Winbind is for matching Linux user to Window users in a Windows Active Directory environment.  This *will *cause you pain in the future.

---

### Post by SolomonMan on 2013-03-16
All,
I figure out the mount error(13): Permission denied issue.

I needed to add the machine name into the user credentials;
username=\\christopher-desktop\chris

Thanks,
Chris

---

### Post by SolomonMan on 2013-03-16
How do I mark this thread as solved?

The thread tools drop down does not have an option to mark my thread as solved.

Thanks,
Chris

---

