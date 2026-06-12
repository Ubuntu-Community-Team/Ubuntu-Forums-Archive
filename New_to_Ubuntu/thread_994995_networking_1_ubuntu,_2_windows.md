---
title: "networking 1 ubuntu, 2 windows"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by ewaynec on 2008-11-27
I am very new to ubuntu. I have 3 PC's networked with wired eithernet. the other 2 are running windows xp. All are connected together through a router to the internet. All 3 will connect to the internet, the 2 windows pcs will connect to each other but not the linux. the linux will not connect to either of the windows pcs. 
  One of the windows pcs has a printer (lexmart 1200 all in one) the other pcs share this printer
  Everything did work on the original installation, until I did an update, the printer quit, I found the network was not working. I tried everything I could, no sucess. Then several days later I did another update, and it started working again. Then later another update and it quit (the network connection) Now I cannot get it to work. I have done 3 updates since it quit, no success. I have read everything I could find that is related, but no help.
  Can you help? 
     Wayne

---

### Post by ashmew2 on 2008-11-28
You using SAMBA ?

---

### Post by Dedoimedo on 2008-11-28
A few questions:

Any firewall software running on these machines?
Do you use Samba?
Did you enable sharing of certain files/folders on relevant machines?
Can you ping the machines (each one the other two)?

Dedoimedo

---

### Post by ewaynec on 2008-11-28
> **Dedoimedo said:**
> A few questions:

Any firewall software running on these machines?
Do you use Samba?
Did you enable sharing of certain files/folders on relevant machines?
Can you ping the machines (each one the other two)?

Dedoimedo

Tried firewall off, and on, no difference.
Yes I am using Samba.
All files are shared on all computers as well as the printer is shared.
Yes I can ping everything from all the computers.

  Please remember, This worked at the install. Linux set up everything and it worked great originally. Whatever caused it to quit was done by one of the updates, about a week ago.

---

### Post by ewaynec on 2008-11-28
> **ashmew2 said:**
> You using SAMBA ?

Yes I am.

---

### Post by Dedoimedo on 2008-11-29
Did you try logging out/in?
Did you try a restart?
Did you try to restart Samba processes?
Dedoimedo

---

### Post by doas777 on 2008-11-29
whats your smb.conf look like?
```
sudo cat /etc/samba/smb.conf
```

---

### Post by ewaynec on 2008-11-29
> **Dedoimedo said:**
> Did you try logging out/in?
Did you try a restart?
Did you try to restart Samba processes?
Dedoimedo

Yes to everything except "restart Samba processes". I don't know how to do that.
  Wayne

---

### Post by ewaynec on 2008-11-29
> **doas777 said:**
> whats your smb.conf look like?
```
sudo cat /etc/samba/smb.conf
```

wayne@albert-e:~$ sudo cat /etc/samba/smb.conf
[sudo] password for wayne: 
[global]
netbios name = Samba24
server string = CAD architects, Stockholm. East 32nd st, 34th floor
workgroup = Workgroup
security = user
hosts allow = 127. 192.168.0.
interfaces = 127.0.0.1/8 192.168.0.0/24 
remote announce = 192.168.0.255
remote browse sync = 192.168.0.255
printcap name = /etc/printcap
load printers = yes
cups options = raw
printing = cups
guest account = smbguest
log file = /var/log/samba/samba.log
max log size = 1000
null passwords = no
username level = 8
password level = 8
encrypt passwords = yes
unix password sync = yes
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
local master = no
domain master = no
preferred master = no
domain logons = no
os level = 33
logon drive = m:
logon home = \\%L\homes\%u
logon path = \\%L\profiles\%u
logon script = %G.bat
time server = no
name resolve order = wins lmhosts bcast
wins support = no
wins server =
wins proxy = no
dns proxy = no
preserve case = yes
short preserve case = yes
client use spnego = no
client signing = no
client schannel = no
server signing = no
server schannel = no
nt pipe support = yes
nt status support = yes
allow trusted domains = no
obey pam restrictions = yes
enable spoolss = yes
client plaintext auth = no
disable netbios = no
follow symlinks = no
update encrypted = yes
pam password change = no
passwd chat timeout = 120
hostname lookups = no
username map = /etc/samba/smbusers
smb passwd file = /etc/samba/smbpasswd
passwd program = /usr/bin/passwd '%u'
passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
add user to group script=/usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
add group script = /usr/sbin/groupadd '%g'
delete user script = /usr/sbin/userdel '%u'
delete user from group script = /usr/sbin/userdel '%u' '%g'
delete group script = /usr/sbin/groupdel '%g'
add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
machine password timeout = 120
idmap uid = 16777216-33554431
idmap gid = 16777216-33554431
template shell = /dev/null
winbind use default domain = yes
winbind separator = @
winbind cache time = 360
winbind trusted domains only = yes
winbind nested groups = no
winbind nss info = no
winbind refresh tickets = no
winbind offline logon = no

[homes]
comment = Home Directories
path = /home
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
share modes = no
locking = no

[netlogon]
comment = Network Logon Service
path = /home/netlogon
read only = no
available = yes
browseable = yes
writable = no
guest ok = no
public = no
printable = no
share modes = no
locking = no

[profiles]
comment = User Profiles
path = /var/samba/profiles
read only = no
available = yes
browseable = no
writable = yes
guest ok = no
public = no
printable = no
locking = no
create mode = 0600
directory mask = 0700

[printers]
comment = All Printers
path = /var/spool/samba
browseable = yes
writable = no
guest ok = no
public = no
printable = yes
share modes = no
locking = no

[pdf-documents]
path = /home/pdf-documents
comment = Converted PDF Documents
available = yes
browseable = yes
writeable = yes
guest ok = yes

[pdf-printer]
path = /tmp
comment = PDF Printer Service
printable = yes
guest ok = yes
use client driver = yes
printing = bsd
print command = /usr/bin/gsambadpdf %s %u
lpq command =
lprm command =
wayne@albert-e:~$ 

  There is no printer connected to this machine.
Did I do that right??
Wayne

---

### Post by Dedoimedo on 2008-11-29
Hello,

To restart service (any):

```
sudo service <name> restart
```

Or on Ubuntu pre 8.10:

```
sudo /etc/init.d/<name> restart
```

In the case of samba, <name> = samba :)

Dedoimedo

---

### Post by ewaynec on 2008-11-29
> **Dedoimedo said:**
> Hello,

To restart service (any):

```
sudo service <name> restart
```

Or on Ubuntu pre 8.10:

```
sudo /etc/init.d/<name> restart
```

In the case of samba, <name> = samba :)

Dedoimedo

  I will do that but, 
  I have been researching this problem, and found this interesting. There is a bug report that describes my problem exactly. 
  Bug # 252245 reported by James on 2008-07-27.
  It seems there are several people having this problem.
  He also suggested a workaround that I tried, and it did not work for me.
      Wayne

  I did like you said to restart samba, here is what I got.  
root@albert-e:/home/wayne# sudo /etc/init.d/samba restart
 * Stopping Samba daemons                                                       start-stop-daemon: warning: failed to kill 4797: No such process
                                                                         [ OK ]
 * Starting Samba daemons                                                [ OK ] 
root@albert-e:/home/wayn

---

### Post by Dedoimedo on 2008-11-30
This means Samba was not running ... You can't stop something that it's running. But it started fine. So apparently, your problem is that Samba is not launching at startup.
Dedoimedo

---

### Post by ewaynec on 2008-11-30
> **Dedoimedo said:**
> This means Samba was not running ... You can't stop something that it's running. But it started fine. So apparently, your problem is that Samba is not launching at startup.
Dedoimedo

OK, But I still don't see the network, I see no difference. Why is Samba not launching at startup?
  The only thing I saw in your last post was a link to your web page, I went there but found noting that could help.
  Is that it?
    Wayne

---

### Post by ewaynec on 2008-12-02
Does anybody read these messages? What happened to the support I was promised? Where are the people who said they would help? Am I left on my own?


  Is anyone out there???????
     Wayne

---

### Post by doas777 on 2008-12-02
ok, try running:
```
sudo /etc/init.d/samba start
```
once you do that, can you see your network?

just a hint, no one promised support. if you want professional support from canonical, you have to pay for it, the same way you do from Microsoft, IBM, Sun, Novell, and most everyone else. heck, I have threads that have been open for months, with 0 replies, except a lonely bump, and occasionally a fellow with the same problem, who wishes to commiserate. but I digress.

to be honest, getting a perfect, stable Samba config going, you have to do a bit of tweaking to your conf file (and yours is huge!) to get it going just so. it can also be affected by your windows configuration (I force NTLMv2 on all my hosts for instance). I'll take another look at your config tommorow. for now, it's bedtime.

best regards,
franklin

---

### Post by ewaynec on 2008-12-05
> **doas777 said:**
> ok, try running:
```
sudo /etc/init.d/samba start
```
once you do that, can you see your network?

just a hint, no one promised support. if you want professional support from canonical, you have to pay for it, the same way you do from Microsoft, IBM, Sun, Novell, and most everyone else. heck, I have threads that have been open for months, with 0 replies, except a lonely bump, and occasionally a fellow with the same problem, who wishes to commiserate. but I digress.

to be honest, getting a perfect, stable Samba config going, you have to do a bit of tweaking to your conf file (and yours is huge!) to get it going just so. it can also be affected by your windows configuration (I force NTLMv2 on all my hosts for instance). I'll take another look at your config tommorow. for now, it's bedtime.

best regards,
franklin

  I ran the command you suggested, It still doesn't work.
  Is there a place I can get information on SAMBA and how to tweak it.
  I will do the work if someone will just point me in the right direction. I am trying to learn enough about a totally new system so I don't have to go back to windows.
  If you read the previous post you will see where everyone that responded, ask me questions, that I answered, but noone has offered any help. There were only two suggestions,(yours and one other). Neither did any good, I still have the same problem, I am getting fustrated,(as you can see)
  Wayne

---

### Post by pdtpatrick on 2008-12-05
if you google samba tutorial, it will give you a good guide.

However you can do these: 

smbtree to view all shares in your network that are visible and are shared.

You can also do smbclient -L to get a list of what services are available. 

You also gotta make sure your .conf files are set correctly so that your windows users can log in which means you have to create a username for them or add their names in the smbusers file under your /etc/samba/ directory .. or the /etc/smb/ directory  --- im coming from Red Hat world so i get some of the names mixed up.

But anyway google samba guide and look for the part that mentions smbpasswd (creating users and password)

Then once this is done and you have added windows users name and such, from you windows box, try connecting to the created shares on the linux and see what happens.

---

