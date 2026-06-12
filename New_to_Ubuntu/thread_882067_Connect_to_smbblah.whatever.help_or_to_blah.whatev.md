---
title: "Connect to smb://blah.whatever.help or to \\blah.whatever.help"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by ingrid_ozikem on 2008-08-06
I see instructions to this effect at my university.. 
connect to \\blah.whatever.help for windows users and 
smb://blah.whatever.help for Mac Users.

I'm confused what I'm supposed to do using Ubuntu.. I understand SMB stands for Samba which is a Windows way of sharing folders? Or is it a Linux way of doing something??

I tried connecting to both those sites through Nautilus as well as through Places -> Connect to Server.. neither works.

 I'd really appreciate any answers at all and esp. any explanation at all of what I'm doing (being a Sambda client?)

---

### Post by bobnutfield on 2008-08-06
Do you have Samba installed?  Go to System>Aministration>Services.  You will see the samba service there.  Make sure it is enabled.  Samba is Linux program to enable sharing folders and data with Windows machines on a network.  The samba client will enable you to share Windows folders, but you will need the Samba server installed to share Linux files with Windows.  If you do not have Samba installed, you can get it from the Synaptics Package Manager.

---

### Post by Blutack on 2008-08-06
Have you tried clicking Places --> Network --> Windows Network and having a look there?

---

### Post by halitech on 2008-08-06
> **ingrid_ozikem said:**
> I see instructions to this effect at my university.. 
connect to \\blah.whatever.help for windows users and 
smb://blah.whatever.help for Mac Users.

I'm confused what I'm supposed to do using Ubuntu.. I understand SMB stands for Samba which is a Windows way of sharing folders? Or is it a Linux way of doing something??

I tried connecting to both those sites through Nautilus as well as through Places -> Connect to Server.. neither works.

 I'd really appreciate any answers at all and esp. any explanation at all of what I'm doing (being a Sambda client?)

I'm guessing you are trying to connect to a shared folder somewhere on the university network? 

SMB - Server Message Block ( [http://en.wikipedia.org/wiki/Server_Message_Block](http://en.wikipedia.org/wiki/Server_Message_Block) )

when you are trying to use Places - Connect to Server, which option are you selecting from the drop down?


> **bobnutfield said:**
> Do you have Samba installed?  Go to System>Aministration>Services.  You will see the samba service there.  Make sure it is enabled.  Samba is Linux program to enable sharing folders and data with Windows machines on a network.  The samba client will enable you to share Windows folders, but you will need the Samba server installed to share Linux files with Windows.  If you do not have Samba installed, you can get it from the Synaptics Package Manager.

they are trying to connect to a windows share by the sounds of it, they shouldn't need to have the samba server installed to do that

> **Blutack said:**
> Have you tried clicking Places --> Network --> Windows Network and having a look there?

usually works for me :)

---

### Post by loboc on 2008-08-06
Open Nautilus (the Gnome file manager just click on your Home Folder) and in the file menu there is : connect to server

Select the 
Service Type: Windows Share

Server: 

Type the computer name on the network or ip address
(blah.whatever.help)

Share: 

is the named share on the windows box, this you can leave blank unlusess you know it.  Sometimes Windows admins have different names like a compnany might have one for Marketing and One for Engineering

Folder: 
again if you know it type it in otherwise leave blank
like in the UNi gave you host.domain/users/timmah then 
users/timmah would go here

Username:  

If you have to login into the shared computer type your username on that computer here. For a university this migh be your student id or email username Otherwise leave blank for public shares

Domain Name: 
In windows networks users are tied to domain in our comapny example Tim in engineering might be in the sydney domain while Katie in Marketing might be in the Melbourne domain.  At a Uni your domain might be something like students or the name of the department your in. If you dont have info from the uni leave it blank

Bookmark:  
Check it so this will show up in nautilus under the Places menu so you dont have to type it everytime you want to access the share

---

### Post by ingrid_ozikem on 2008-08-06
Thanks for the replies! I'd tried Connect to Server with SSH and some other options but not Windows Share.  Windows Share seems to work better (but I haven't been successful yet -- I suspect I might need to connect through the university's VPN to access this server.. so that's something I'm going to try to set up. Any experience with connecting to Windows VPNs, anyone?)

But your idea seems right, so thanks a lot!

---

### Post by bodhi.zazen on 2008-08-06
If you want to connect to samba from the command line install smbfs :

```
sudo apt-get install smbfs
```

Them mount :

```
sudo mkdir /media/smb
sudo -t cifs //server/share /media/smb -o user=xxx,passwd=yyy
```

---

### Post by loboc on 2008-08-06
> **ingrid_ozikem said:**
> Thanks for the replies! I'd tried Connect to Server with SSH and some other options but not Windows Share.  Windows Share seems to work better (but I haven't been successful yet -- I suspect I might need to connect through the university's VPN to access this server.. so that's something I'm going to try to set up. Any experience with connecting to Windows VPNs, anyone?)

But your idea seems right, so thanks a lot!

If you are off campus you probably need to. google for the vpn settings for you school and select the appropriate network manager plugin probally pptp

---

