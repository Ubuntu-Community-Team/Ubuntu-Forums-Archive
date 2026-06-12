---
title: "[all variants] HowTo: Simple Samba share in a Domestic Lan"
date: 2008-08-15
forum: Outdated Tutorials &amp; Tips
---

### Post by dentaku65 on 2008-08-15
I wrote this HowTo in order to get an easy way to manage Samba share in a domestic lan (let's say home or very small office situations), where resides 2, 3 or more machines (with mixed OS contemplated).

Take in consideration that this is a very basic configuration and is not intended for complex or sophisticated network cases/needs.

**The preparation**
First of all, because this guide is intended for all of *ubuntu variants, we need to install an editor valid for all distributions for simplify the following commands explained later in this guide.
```
sudo apt-get install scite
```

Of course we need to install Samba daemon
```
sudo apt-get install samba winbind
```

Now we have to backup the original configuration file and create new one:
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.ORIGINAL
```
```
sudo rm /etc/samba/smb.conf
```
```
sudo touch /etc/samba/smb.conf
```

We need to create a test share/dir for understanding the following samba share operations; this dirs is only needed for testing/demo purpouses of this guide, replace it with your dirs after you understood the mechanism of sharing. Create a read-only test share:
```
mkdir ~/testsmb
```
Adding the user nobody to the group sambashare:
```
sudo usermod -a -G sambashare nobody
```
Create a read/write test share (capable to be in write mode without the needs of the password, let's say a "guest" write share):
```
mkdir ~/testsmbw
```
Changing the group ownership to this directory (**this is needed in every share you want to make in read/write mode**):
```
sudo chgrp -R sambashare ~/testsmbw
```

**The configuration**
Now we need to open the samba configuration file; consider that this file is divided (for the interests of this guide) only in 2 parts
**1 Global**
**2 Share**
Important! Please see the considerations at the end of smb.conf file in order to get explanations of some entries (marked in red) of the configuration file; open the file:
```
sudo scite /etc/samba/smb.conf
```
and copy&paste the following 2 sections:
```
[global]
workgroup = [COLOR="Red"]<your_workgroup>[/COLOR]
netbios name = [COLOR="Red"]<your_machine_hostname>[/COLOR]
preferred master = No
local master = No
domain master = No
hosts allow = [COLOR="Red"]<your_local_network_class>[/COLOR]
announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
passdb backend = tdbsam
null passwords = true
username map = /etc/samba/smbusers
name resolve order = lmhosts bcast wins host
wins support = no
printing = CUPS
printcap name = CUPS
syslog = 1
syslog only = yes
map to guest = Bad Password
```
```
[testsmb]
path = /home/[COLOR="Red"]<you>[/COLOR]/testsmb
guest ok = yes
create mask = 0777

[testsmbw]
path = /home/[COLOR="Red"]<you>[/COLOR]/testsmbw
guest ok = yes
writeable = yes
public = yes
read only = No
force create mode = 0664
force directory mode = 0775
create mask = 0777
directory mask = 0777
force group = sambashare

```
Save and close the file

**The ([COLOR="Red"]red[/COLOR]) considerations**
Important! Please read carefully the following specifications in order to make your Samba working:
> workgroup = [COLOR="Red"]<your_workgroup>[/COLOR] : [COLOR="Red"]<your_workgroup>[/COLOR] must be replaced usually by WORKGROUP, MSHOME or the name of the workgroup of the machine/s of your LAN. Can be also a different name from the one already present in your LAN
> netbios name = [COLOR="Red"]<your_machine_hostname>[/COLOR] : [COLOR="Red"]<your_machine_hostname>[/COLOR] is the name of your linux box; to know it just type in terminal:
```
hostname
```
> hosts allow = [COLOR="Red"]<your_local_network_class>[/COLOR] : in my case the network class is [COLOR="Red"]192.168.1.0/255.255.255.0[/COLOR] put the range of your local network; to know it type in terminal:
```
ifconfig |grep Bcast
```
> path = /home/[COLOR="Red"]<you>[/COLOR]/testsmb : the [COLOR="Red"]you[/COLOR] in the path option must be your home name in the linux box; please consider that when you put the directory for sharing, the path must be complete.

**[COLOR="Red"]The ([COLOR="Black"]black[/COLOR]) considerations[/COLOR]**
Please be aware:
[LIST=1]
[*]The read/write share is not "secure" because with the method described above any user present on any machine of your LAN can read/write/delete files straightforward.
[*]Because for the above consideration be sure to limit the samba share only in you lan configuring the "hots allow" as described previously.
[/LIST]

Now, after you finish the configuration of smb.conf, restart samba daemon:
```
sudo /etc/init.d/samba restart
```

Now you are able with your Ubuntu box to browse and to be browsed the resources in your domestic LAN.

---

### Post by deadland on 2008-09-01
Hi dentaku65,

thanks for your howto. :)


I'm sorry to say, but I have problems to access the shares I made with your guide.

Thats what I see in syslog, when I try to access a share:
```
Sep  1 10:22:54 benq winbindd[5237]: [2008/09/01 10:22:54, 0] nsswitch/idmap.c:idmap_alloc_init(750) 
Sep  1 10:22:54 benq winbindd[5237]:   ERROR: Initialization failed for alloc backend, deferred! 
Sep  1 10:22:54 benq smbd[11161]: [2008/09/01 10:22:54, 0] auth/auth_util.c:create_builtin_administrators(792) 
Sep  1 10:22:54 benq smbd[11161]:   create_builtin_administrators: Failed to create Administrators 
Sep  1 10:22:54 benq winbindd[5237]: [2008/09/01 10:22:54, 0] nsswitch/idmap.c:idmap_alloc_init(750) 
Sep  1 10:22:54 benq winbindd[5237]:   ERROR: Initialization failed for alloc backend, deferred! 
Sep  1 10:22:54 benq smbd[11161]: [2008/09/01 10:22:54, 0] auth/auth_util.c:create_builtin_users(758) 
Sep  1 10:22:54 benq smbd[11161]:   create_builtin_users: Failed to create Users 
Sep  1 10:22:54 benq winbindd[5228]: [2008/09/01 10:22:54, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Sep  1 10:22:54 benq winbindd[5228]:   Possible deadlock: Trying to lookup SID S-1-1-0 with passdb backend 
Sep  1 10:22:54 benq winbindd[5228]: [2008/09/01 10:22:54, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Sep  1 10:22:54 benq winbindd[5228]:   Possible deadlock: Trying to lookup SID S-1-5-2 with passdb backend 
Sep  1 10:22:54 benq smbd[11161]: [2008/09/01 10:22:54, 0] smbd/service.c:make_connection_snum(1003) 
Sep  1 10:22:54 benq smbd[11161]:   '/home/USER/Bilder' does not exist or permission denied when connecting to [Bilder] Error was Permission denied 
```

I read your guide carefully and I guess what you wrote is correct, so there must be a problem with the privileges within my homefolder:

My home folder has in general:
Mode: 700
Owner/Group: USER:USER

The shares with read access have:
Mode: 644
Owner/Group: USER:USER

The share with read/write access has:
Mode: 664
Owner/Group: USER:SAMBASHARE

It would be great, if you could help me.

Thanks in advanced

---

### Post by dentaku65 on 2008-09-01
> **deadland said:**
> Hi dentaku65,

thanks for your howto. :)


I'm sorry to say, but I have problems to access the shares I made with your guide.

Thats what I see in syslog, when I try to access a share:
```
Sep  1 10:22:54 benq winbindd[5237]: [2008/09/01 10:22:54, 0] nsswitch/idmap.c:idmap_alloc_init(750) 
Sep  1 10:22:54 benq winbindd[5237]:   ERROR: Initialization failed for alloc backend, deferred! 
Sep  1 10:22:54 benq smbd[11161]: [2008/09/01 10:22:54, 0] auth/auth_util.c:create_builtin_administrators(792) 
Sep  1 10:22:54 benq smbd[11161]:   create_builtin_administrators: Failed to create Administrators 
Sep  1 10:22:54 benq winbindd[5237]: [2008/09/01 10:22:54, 0] nsswitch/idmap.c:idmap_alloc_init(750) 
Sep  1 10:22:54 benq winbindd[5237]:   ERROR: Initialization failed for alloc backend, deferred! 
Sep  1 10:22:54 benq smbd[11161]: [2008/09/01 10:22:54, 0] auth/auth_util.c:create_builtin_users(758) 
Sep  1 10:22:54 benq smbd[11161]:   create_builtin_users: Failed to create Users 
Sep  1 10:22:54 benq winbindd[5228]: [2008/09/01 10:22:54, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Sep  1 10:22:54 benq winbindd[5228]:   Possible deadlock: Trying to lookup SID S-1-1-0 with passdb backend 
Sep  1 10:22:54 benq winbindd[5228]: [2008/09/01 10:22:54, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Sep  1 10:22:54 benq winbindd[5228]:   Possible deadlock: Trying to lookup SID S-1-5-2 with passdb backend 
Sep  1 10:22:54 benq smbd[11161]: [2008/09/01 10:22:54, 0] smbd/service.c:make_connection_snum(1003) 
Sep  1 10:22:54 benq smbd[11161]:   '/home/USER/Bilder' does not exist or permission denied when connecting to [Bilder] Error was Permission denied 
```

I read your guide carefully and I guess what you wrote is correct, so there must be a problem with the privileges within my homefolder:

My home folder has in general:
Mode: 700
Owner/Group: USER:USER

The shares with read access have:
Mode: 644
Owner/Group: USER:USER

The share with read/write access has:
Mode: 664
Owner/Group: USER:SAMBASHARE

It would be great, if you could help me.

Thanks in advanced

Can you post your smb.conf?
```
cat /etc/samba/smb.conf
```

---

### Post by deadland on 2008-09-01
Thanks for your fast response.

My smb.conf

```
[global]
workgroup = DAHEIM
netbios name = benq
preferred master = No
local master = No
domain master = No
#hosts allow = 192.168.0.0/255.255.255.0
announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
passdb backend = tdbsam
null passwords = true
username map = /etc/samba/smbusers
name resolve order = lmhosts bcast wins host
wins support = no
printing = CUPS
printcap name = CUPS
syslog = 1
syslog only = yes
map to guest = Bad Password


[Dokumente]
path = /home/USER/Dokumente
guest ok = yes
create mask = 0777


[Musik]
path = /home/USER/Musik
guest ok = yes
create mask = 0777


[Bilder]
path = /home/USER/Bilder
guest ok = yes
create mask = 0777

[Videos]
path = /home/USER/Videos
guest ok = yes
create mask = 0777

[Public]
path = /home/USER/Public
guest ok = yes
writeable = yes
public = yes
read only = No
force create mode = 0664
force directory mode = 0775
create mask = 0777
directory mask = 0777
force group = sambashare

```

---

### Post by dentaku65 on 2008-09-01
> **deadland said:**
> Thanks for your fast response.

My smb.conf

```
[global]
workgroup = DAHEIM
netbios name = benq
preferred master = No
local master = No
domain master = No
#hosts allow = 192.168.0.0/255.255.255.0
announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
passdb backend = tdbsam
null passwords = true
username map = /etc/samba/smbusers
name resolve order = lmhosts bcast wins host
wins support = no
printing = CUPS
printcap name = CUPS
syslog = 1
syslog only = yes
map to guest = Bad Password


[Dokumente]
path = /home/USER/Dokumente
guest ok = yes
create mask = 0777


[Musik]
path = /home/USER/Musik
guest ok = yes
create mask = 0777


[Bilder]
path = /home/USER/Bilder
guest ok = yes
create mask = 0777

[Videos]
path = /home/USER/Videos
guest ok = yes
create mask = 0777

[Public]
path = /home/USER/Public
guest ok = yes
writeable = yes
public = yes
read only = No
force create mode = 0664
force directory mode = 0775
create mask = 0777
directory mask = 0777
force group = sambashare

```

Hi deadland,
two questions:
1) did you restart samba?
```
sudo /etc/init.d/samba restart
```
2) the shares you have has been created previously this guide or during the read? If is the first case please create a test dir just to see if is a issue of something done before.

Btw the smb.conf looks correct; did you add the user *nobody* to sambashare group?
```
sudo usermod -a -G sambashare nobody
```

---

### Post by deadland on 2008-09-01
Hi dentaku65,

I followed your suggestions.

This is my new smb.conf:

```
[global]
workgroup = DAHEIM
netbios name = benq
preferred master = No
local master = No
domain master = No
#hosts allow = 192.168.0.0/255.255.255.0
announce version = 5.0
socket options = TCP_NODELAY IPTOS_LOWDELAY SO_KEEPALIVE SO_RCVBUF=8192 SO_SNDBUF=8192
passdb backend = tdbsam
null passwords = true
username map = /etc/samba/smbusers
name resolve order = lmhosts bcast wins host
wins support = no
printing = CUPS
printcap name = CUPS
syslog = 1
syslog only = yes
map to guest = Bad Password


[Dokumente]
path = /home/USER/Dokumente
guest ok = yes
create mask = 0777


[Musik]
path = /home/USER/Musik
guest ok = yes
create mask = 0777


[Bilder]
path = /home/USER/Bilder
guest ok = yes
create mask = 0777

[Videos]
path = /home/USER/Videos
guest ok = yes
create mask = 0777

[Public]
path = /home/USER/Public
guest ok = yes
writeable = yes
public = yes
read only = No
force create mode = 0664
force directory mode = 0775
create mask = 0777
directory mask = 0777
force group = sambashare


[testsmb]
path = /home/USER/testsmb
guest ok = yes
create mask = 0777

[testsmbw]
path = /home/USER/testsmbw
guest ok = yes
writeable = yes
public = yes
read only = No
force create mode = 0664
force directory mode = 0775
create mask = 0777
directory mask = 0777
force group = sambashare

```

I restarted samba and ran:

```
sudo usermod -a -G sambashare nobody
sudo chgrp -R sambashare ~/testsmbw
```

But there are still the same errors:

```
Sep  1 15:15:07 benq smbd[27898]: [2008/09/01 15:15:07, 0] smbd/map_username.c:map_username(107) 
Sep  1 15:15:07 benq smbd[27898]:   can't open username map /etc/samba/smbusers. Error No such file or directory 
Sep  1 15:15:41 benq winbindd[5237]: [2008/09/01 15:15:41, 0] nsswitch/idmap.c:idmap_alloc_init(750) 
Sep  1 15:15:41 benq winbindd[5237]:   ERROR: Initialization failed for alloc backend, deferred! 
Sep  1 15:15:41 benq smbd[27921]: [2008/09/01 15:15:41, 0] auth/auth_util.c:create_builtin_administrators(792) 
Sep  1 15:15:41 benq smbd[27921]:   create_builtin_administrators: Failed to create Administrators 
Sep  1 15:15:41 benq winbindd[5237]: [2008/09/01 15:15:41, 0] nsswitch/idmap.c:idmap_alloc_init(750) 
Sep  1 15:15:41 benq winbindd[5237]:   ERROR: Initialization failed for alloc backend, deferred! 
Sep  1 15:15:41 benq smbd[27921]: [2008/09/01 15:15:41, 0] auth/auth_util.c:create_builtin_users(758) 
Sep  1 15:15:41 benq smbd[27921]:   create_builtin_users: Failed to create Users 
Sep  1 15:15:41 benq winbindd[5228]: [2008/09/01 15:15:41, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Sep  1 15:15:41 benq winbindd[5228]:   Possible deadlock: Trying to lookup SID S-1-1-0 with passdb backend 
Sep  1 15:15:41 benq winbindd[5228]: [2008/09/01 15:15:41, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Sep  1 15:15:41 benq winbindd[5228]:   Possible deadlock: Trying to lookup SID S-1-5-2 with passdb backend 
Sep  1 15:15:41 benq smbd[27921]: [2008/09/01 15:15:41, 0] smbd/service.c:make_connection_snum(1003) 
Sep  1 15:15:41 benq smbd[27921]:   '/home/obertm/testsmb' does not exist or permission denied when connecting to [testsmb] Error was Permission denied 
Sep  1 15:15:43 benq winbindd[5237]: [2008/09/01 15:15:43, 0] nsswitch/idmap.c:idmap_alloc_init(750) 
Sep  1 15:15:43 benq winbindd[5237]:   ERROR: Initialization failed for alloc backend, deferred! 
Sep  1 15:15:43 benq smbd[27937]: [2008/09/01 15:15:43, 0] auth/auth_util.c:create_builtin_administrators(792) 
Sep  1 15:15:43 benq smbd[27937]:   create_builtin_administrators: Failed to create Administrators 
Sep  1 15:15:43 benq winbindd[5237]: [2008/09/01 15:15:43, 0] nsswitch/idmap.c:idmap_alloc_init(750) 
Sep  1 15:15:43 benq winbindd[5237]:   ERROR: Initialization failed for alloc backend, deferred! 
Sep  1 15:15:43 benq smbd[27937]: [2008/09/01 15:15:43, 0] auth/auth_util.c:create_builtin_users(758) 
Sep  1 15:15:43 benq smbd[27937]:   create_builtin_users: Failed to create Users 
Sep  1 15:15:43 benq winbindd[5228]: [2008/09/01 15:15:43, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Sep  1 15:15:43 benq winbindd[5228]:   Possible deadlock: Trying to lookup SID S-1-1-0 with passdb backend 
Sep  1 15:15:43 benq winbindd[5228]: [2008/09/01 15:15:43, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Sep  1 15:15:43 benq winbindd[5228]:   Possible deadlock: Trying to lookup SID S-1-5-2 with passdb backend 
Sep  1 15:15:43 benq winbindd[5228]: [2008/09/01 15:15:43, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Sep  1 15:15:43 benq winbindd[5228]:   Possible deadlock: Trying to lookup SID S-1-5-2 with passdb backend 
Sep  1 15:15:43 benq smbd[27937]: [2008/09/01 15:15:43, 0] smbd/service.c:make_connection_snum(850) 
Sep  1 15:15:43 benq smbd[27937]:   make_connection: connection to testsmbw denied due to security descriptor. 
Sep  1 15:15:45 benq smbd[27943]: [2008/09/01 15:15:45, 0] smbd/map_username.c:map_username(107) 
Sep  1 15:15:45 benq smbd[27943]:   can't open username map /etc/samba/smbusers. Error No such file or directory 
Sep  1 15:15:45 benq winbindd[5228]: [2008/09/01 15:15:45, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Sep  1 15:15:45 benq winbindd[5228]:   Possible deadlock: Trying to lookup SID S-1-1-0 with passdb backend 
Sep  1 15:15:45 benq winbindd[5228]: [2008/09/01 15:15:45, 0] nsswitch/winbindd_passdb.c:sid_to_name(130) 
Sep  1 15:15:45 benq winbindd[5228]:   Possible deadlock: Trying to lookup SID S-1-5-2 with passdb backend 
Sep  1 15:15:45 benq smbd[27943]: [2008/09/01 15:15:45, 0] smbd/service.c:make_connection_snum(1003) 
Sep  1 15:15:45 benq smbd[27943]:   '/home/obertm/testsmbw' does not exist or permission denied when connecting to [testsmbw] Error was Permission denied 
```

Hmmm, you wrote your guide for ubuntu 8.04?

---

### Post by deadland on 2008-09-01
This could be the problem:

```
can't open username map /etc/samba/smbusers. Error No such file or directory
```

---

### Post by deadland on 2008-09-01
I followed this guide to create /etc/samba/smbusers:

[http://www.howtogeek.com/howto/ubuntu/create-a-samba-user-on-ubuntu/]("http://www.howtogeek.com/howto/ubuntu/create-a-samba-user-on-ubuntu/")


And thats my smbusers:

```
nobody = "nobody"
```

But right now I get this message:

```
Sep  1 15:44:55 benq smbd[29152]:   create_builtin_users: Failed to create Users 
```

And I still can't access the shares

---

### Post by deadland on 2008-09-01
More infos:

```
smbclient //benq/testsmb -U nobody
Password: 
Domain=[BENQ] OS=[Unix] Server=[Samba 3.0.28a]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME

```

```

 id nobody
uid=65534(nobody) gid=65534(nogroup) Gruppen=126(sambashare),65534(nogroup)
```

```
sudo pdbedit -L
nobody:65534:nobody
USER:1000:XXXXX XXXXX,,,
smbguest:1001:Samba guest account

```

```
testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[Dokumente]"
Processing section "[Musik]"
Processing section "[Bilder]"
Processing section "[Videos]"
Processing section "[Public]"
Processing section "[testsmb]"
Processing section "[testsmbw]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions
```

---

### Post by dentaku65 on 2008-09-01
> **deadland said:**
> This could be the problem:

```
can't open username map /etc/samba/smbusers. Error No such file or directory
```

Interesting.
Try to comment out this in your smb.conf:
```
username map = /etc/samba/smbusers
```
in this way:
```
; username map = /etc/samba/smbusers
```

Then restart samba
```
sudo /etc/init.d/samba restart
```

---

### Post by talktorishav on 2008-09-01
The most simples how to on samba I have ever read is
[http://techspalace.blogspot.com/2008/08/share-folders-in-linux-for-windows.html](http://techspalace.blogspot.com/2008/08/share-folders-in-linux-for-windows.html)

---

### Post by dentaku65 on 2008-09-01
> **talktorishav said:**
> The most simples how to on samba I have ever read is
[http://techspalace.blogspot.com/2008/08/share-folders-in-linux-for-windows.html](http://techspalace.blogspot.com/2008/08/share-folders-in-linux-for-windows.html)

Yes is nice, but:
the samba share it works in read/write mode from another linux box?

---

### Post by deadland on 2008-09-02
Hi since I used this guide:

[http://www.howtogeek.com/howto/ubuntu/create-a-samba-user-on-ubuntu/]("http://www.howtogeek.com/howto/ubuntu/create-a-samba-user-on-ubuntu/")

I don't get this error any more:

```
can't open username map /etc/samba/smbusers. Error No such file or directory
```

Thats the error message I get right now:

```
Sep  1 15:44:55 benq smbd[29152]:   create_builtin_users: Failed to create Users
```


I tried your suggestion, but it doesn't help.... :(

---

### Post by dentaku65 on 2008-09-02
> **deadland said:**
> Hi since I used this guide:

[http://www.howtogeek.com/howto/ubuntu/create-a-samba-user-on-ubuntu/]("http://www.howtogeek.com/howto/ubuntu/create-a-samba-user-on-ubuntu/")

I don't get this error any more:

```
can't open username map /etc/samba/smbusers. Error No such file or directory
```

Thats the error message I get right now:

```
Sep  1 15:44:55 benq smbd[29152]:   create_builtin_users: Failed to create Users
```


I tried your suggestion, but it doesn't help.... :(

Silly question from what I see on your previous post error logs:

> [Musik]
path = /home/[COLOR="Red"]USER[/COLOR]/Musik
guest ok = yes
create mask = 0777


Do you have /home/[COLOR="Red"]USER[/COLOR] directory under /home?

---

### Post by deadland on 2008-09-03
Okay I solved the problem:

1.) I removed any samba package 
2.) I installed samba: sudo apt-get install samba smbclient
3.) Changed /home/<USER>/Public to

OWNER/GROUP:  <USER>/users
MODE:         770

4.) I used the original smb.conf
5.) I added my shares:

```
[public]
path = /home/<USER>/Public
guest ok = yes
writeable = yes
browseable = yes
create mode = 0660
directory mode = 0770
force user = <USER>
force group = users

[musik]
copy = public
path = /home/<USER>/Musik
writeable = no
write list = <USER2>,@vertraulich

[dokumente]
copy = musik
path = /home/<USER>/Dokumente

[bilder]
copy = musik
path = /home/<USER>/Bilder

[videos]
copy = musik
path = /home/<USER>/Videos
```

---

### Post by jcr1 on 2008-09-04
What is a workgroup?

Why all the mention of guests and forcing users?

There seems so many ways of doing this I am so confused. All I want to do is share 1 folder on 1 machine. I am mounting this 1 share on another machine, but during mounting it says cifs error input/output error.

It keeps doing this randomly over time and every time i struggle to rectify it.

What is the absolute bare minimum to put in the smb.conf?

---

### Post by kv_home on 2008-09-05
I need help settign up a simple netwrok you have described - 

I have one windows XP laptop, and one ubuntu 8.04 desktop
I want to be able to use the ubuntu machine as a file server

What packages do I need to understand to get this working?
What needs to be installed on the windows machine, or is SMB already present ?

The network machines network through a wireless router - which has dynamic addressing - does this make things more complicated - or am I over thinking?

I don't expect a on liner solution - just point me at what I need to read and all do some background.

I think I need to learn about samba, and DNS rules - 
Any help appreciated.

Kevin

---

