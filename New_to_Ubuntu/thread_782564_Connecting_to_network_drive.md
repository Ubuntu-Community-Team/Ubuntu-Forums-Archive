---
title: "Connecting to network drive"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by troublepants on 2008-05-05
This problem has been driving me crazy - any help greatly appreciated. Keep in mind I'm a total n00b - so I may just be missing some essential package, or need some config tweak and need detailed instructions. 


The problem: I can't connect to my network drive through terminal despite being able to connect through nautilus. I need a permanent mount point so I can use amarok etc. The network drive is iomega. 

To connect through nautilus, I go Places->connect to server. I select "windows share" option. I enter only the server name (not ip address) and the folder. The share is not passworded (yes.. I know!). I instantly get the folder on my desktop and can browse it no problem. But amarok and some other programs cannot see it. 

The fix for this is supposed to be to mount it to a folder location through terminal. But no matter what command I use, I can't get it to mount. I am running hardy heron. 

Here is what I am trying

(note; I have replaced my real username with "myusername")

$ sudo mount -t cifs //192.168.1.10 /home/myusername/share -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777

[sudo] password for myusername: 
Mounting the DFS root for a particular server not implemented yet
No ip address specified and hostname not found



The most promising is:

$ sudo mount -t cifs //192.168.1.10/public /home/myusername/share -o username=admin
Password: 
$

There is no response to the last command - which would suggest it was successful - problem is that when I navigate to that folder it appears empty. I shouldn't need a username and password, but since it asks I put in the drive username / password anyway. Once I do this command (and cannot see anything in the directory), I can no longer do "connect to server" with nautilus - it now says 

Can't display location "smb://disk1/public/"


which makes me think something has happened. 

Any help greatly appreciated!

---

### Post by mlentink on 2008-05-05
If you mount a share through nautilus, it usually shows up in /media. Have you checked that? Because if you can see it in nautilus, amaork should be able to see it as /media/iomega (or whatever the name of your drive is)

---

### Post by troublepants on 2008-05-06
thanks for the response - but it's not showing up in the the media folder; when I use "places -> connect to server" it only shows up as an icon on the desktop. as far as i understand it the "connect to server"  option in hardy heron does not actually mount the drive, hence amarok cannot see it. 

i tried this line in fstab
//192.168.1.10/public  /media/MyShare  cifs  guest,utf8  0  0

when i do "sudo mount -a", i get no error, but nothing is shows up in the /media/MyShare directory

help?

---

### Post by troublepants on 2008-05-06
More details of what I am trying.....

$ sudo mount -t cifs //192.168.1.10/public /media/MyShare -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777

$ umount //192.168.1.10/public
umount: //192.168.1.10/public is not mounted (according to mtab)


seems odd - even though mount gave no error, umount says it didn't mount??

would be really great if i could just map the drive, and click a box to reconnect at login!!!! ok - that's the frustration talking. 

help greatly appreciated.


***update - Still no joy. I figured out that i was supposed to umount the ubuntu directory and not the drive, but still have same result.
Also I have this as more info:


$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.10    DISK1          [	WORKGROUP     ]

---

### Post by troublepants on 2008-05-06
bump

---

### Post by Paqman on 2008-05-06
I'm assuming your NAS is designed to work with a Windows network, so it's probably running Samba.

Follow [these instructions](http://ubuntuforums.org/showthread.php?t=288534) and you should be fine. I use them myself. Your  fstab entry would look like:
```

//192.168.1.10/public /home/myusername/share        cifs    credentials=/root/.smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777

```
Since you're using the NAS's IP address, make sure your router is assigning it a static address, otherwise you won't always be able to connect.

---

### Post by troublepants on 2008-05-06
Thanks - but the usual answers I find in the forums aren't working. On the positive side I'm hoping it's not any lack of ability to search the forums or use google! But still I can't get the drive to mount manually or by editing fstab

I put the following line into fstab:

//192.168.1.10/public /media/MyShare cifs user=myusername,pass=mypassword

then doing a sudo mount -a I get no error. 

However a dmesg | tail gives me:

$ dmesg | tail 
[  435.020700]  [<c016e7b0>] __alloc_pages+0x60/0x390
[  435.020711]  [<c03190f0>] do_page_fault+0x0/0x730
[  435.020719]  [<c03178c2>] error_code+0x72/0x80
[  435.020756]  [<c01a3005>] copy_mount_options+0xa5/0x140
[  435.020787]  [<c01a4db7>] sys_mount+0x77/0xb0
[  435.020812]  [<c01043c2>] sysenter_past_esp+0x6b/0xa9
[  435.020869]  =======================
[  435.020870] Code: 0f b7 c0 b9 06 00 00 00 8b 6c 24 20 01 fb 89 da ff 55 08 85 c0 7f ce c6 03 3f 83 c7 01 83 c6 01 3b 34 24 75 ca 89 f8 8b 6c 24 08 <c6> 44 05 00 00 83 c4 0c 89 f8 5b 5e 5f 5d c3 31 ff 31 c0 eb e7 
[  435.020912] EIP: [<f9ea010a>] cifs_strfromUCS_le+0x6a/0x80 [cifs] SS:ESP 0068:f5385b98
[  435.020927] ---[ end trace 5fd98c0b66c93653 ]---


By the way, I did try and reinstall ubuntu - but still having the same problem. 

Help anyone?

---

### Post by Squalo_ch on 2008-06-29
I just brought an iomega network disk and have the same problem...
Any idea?

---

