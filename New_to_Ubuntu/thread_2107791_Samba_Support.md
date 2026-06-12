---
title: "Samba Support"
date: 2013-01-22
forum: New to Ubuntu
---

### Post by butt3rs84 on 2013-01-22
Greetings all,

   I am very new to linux and trying to learn as I go along. My problem/question is this. I have a Macbook Pro running OS X 10.8.2 and an HP Mini 210-1170nr. I initially tried to install ubuntu lts 12.04.1 32 bit which would have been appropriate for the specs on the mini. I received an error on attempting to install pertaining to a driver issue. I was able to get lubuntu running however. The actual problem or question is related to configuring SAMBA to share from the mini to my Mac. I have tried reading multiple guides online and haven't really gotten anywhere. I'm not really sure what I am doing wrong. Should I (a.) try a different Linux distro i.e. mint, fedora, etc, (b.) follow a specific guide for sharing from Samba linux to my Mac, or (c.) try to re-install the lubuntu iso to try from scratch again (perhaps my attempts have messed up a config file?) 

   Any help would be greatly appreciated. I can try to list what I have from the samba.conf file if that helps? When I hit apple + k to connect to a server, I can never get it to work.

Regards,
Butt3rs84

---

### Post by bfmetcalf on 2013-01-22
I know it pertains more to ArchLinux than Lubuntu, but there is a lot of good information for the config files and such.  Check this out and see if anything sticks out at you.  It would probably help if you posted your config file too.

[https://wiki.archlinux.org/index.php/Samba](https://wiki.archlinux.org/index.php/Samba)

---

### Post by PowerBarry43 on 2013-01-22
Hi

just a quick thing to try. when connecting to the server try just using the ip address. 

failing that what you may like to try is using webmin to configure samba so you run

```
sudo apt-get install samba samba-common

sudo smbpasswd -a {username}

wget -c http://prdownloads.sourceforge.net/webadmin/webmin_1.600_
all.deb

sudo dpkg -i webmin_1.600_all.deb

sudo apt-get install -f
```

then open up a browser and stick [https://localhost:10000]("http://localhost:10000") in the URL bar, login and you get a nice easy GUI to add and configure shares from. If you run into trouble this is a good guide 

[http://www.linux.com/learn/tutorials/299651:samba-configuration-with-webmin](http://www.linux.com/learn/tutorials/299651:samba-configuration-with-webmin)

last ditch effort you could install ssh on ubuntu with 
sudo apt-get install ssh 
and look into using sftp or sshfs to connect from your mac.

hope this helps!

Barry

---

### Post by cepal on 2013-01-23
I am sorry but this is too little information to help. What exactly is your problem? Installing Samba? In which step it fails? What are the errors/issues? What have you tried?

Don't be afraid to write tons of information, much better than letting others guess. You actually even didn't say if you want to share out files (be a samba server), or connect to other computers shared data (be a client)....

Cheers

> **butt3rs84 said:**
> Greetings all,

   I am very new to linux and trying to learn as I go along. My problem/question is this. I have a Macbook Pro running OS X 10.8.2 and an HP Mini 210-1170nr. I initially tried to install ubuntu lts 12.04.1 32 bit which would have been appropriate for the specs on the mini. I received an error on attempting to install pertaining to a driver issue. I was able to get lubuntu running however. The actual problem or question is related to configuring SAMBA to share from the mini to my Mac. I have tried reading multiple guides online and haven't really gotten anywhere. I'm not really sure what I am doing wrong. Should I (a.) try a different Linux distro i.e. mint, fedora, etc, (b.) follow a specific guide for sharing from Samba linux to my Mac, or (c.) try to re-install the lubuntu iso to try from scratch again (perhaps my attempts have messed up a config file?) 

   Any help would be greatly appreciated. I can try to list what I have from the samba.conf file if that helps? When I hit apple + k to connect to a server, I can never get it to work.

Regards,
Butt3rs84

---

### Post by Morbius1 on 2013-01-23
> I can try to list what I have from the samba.conf file if that helps?That would be helpful and one way to do that is to post the output of the following commands:
```
testparm -s
``````
net usershare info --long
```You might want to post the output of these as well:
```
hostname
``````
smbtree
```

---

### Post by butt3rs84 on 2013-01-23
Hi guys thanks for all the feedback. I've got some time this morning to try your suggestions and will let you know how it goes. I am trying to set up my HP mini as a file server via SAMBA.

To be more specific as requested, yes I was able to install Samba. I actually installed Samba as well as Samba-Gadmin (Does having Samba and Samba-gadmin cause configuration conflicts?). Here's my samba.conf file - (only changes made for this post was to exclude the full ip address.)

"[global]
netbios name = Samba24
server string = Samba file and print server
workgroup = Workgroup
security = user
hosts allow = 127.192.xxx.x.
interfaces = 127.0.x.x/8 192.xxx.x/24
bind interfaces only = yes
remote announce = 192.168.x.xxx
remote browse sync = 192.168.x.xxx
printcap name = cups
load printers = yes
cups options = raw
printing = cups
guest account = smbguest
log file = /var/log/samba/samba.log
max log size = 1000
null passwords = no
username level = 6
password level = 6
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
passdb backend = tdbsam
passwd program = /usr/bin/passwd '%u'
passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
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
valid users = %U
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
locking = no
strict locking = no

[netlogon]
comment = Network Logon Service
path = /var/lib/samba/netlogon
read only = no
available = yes
browseable = yes
writable = no
guest ok = no
public = no
printable = no
locking = no
strict locking = no

[profiles]
comment = User Profiles
path = /var/lib/samba/profiles
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
create mode = 0600
directory mask = 0700
locking = no
strict locking = no

[printers]
comment = All Printers
path = /var/spool/samba
browseable = yes
writable = no
guest ok = no
public = no
printable = yes
locking = no
strict locking = no

[pdf-documents]
path = /var/lib/samba/pdf-documents
comment = Converted PDF Documents
admin users = %U
available = yes
browseable = yes
writeable = yes
guest ok = yes
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

[music]
path = /home/josh/Music
comment = No comment
read only = no
available = yes
browseable = yes
writable = no
guest ok = no
public = no
printable = no
locking = no
strict locking = no"

[B]Here's what I get when I enter testparm -s (again only changes made to exclude full ip address.)
[/B]
"josh@josh-HP-Mini-210-1100:~$ sudo testparm -s
[sudo] password for josh: 
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
WARNING: The "null passwords" option is deprecated
WARNING: The "password level" option is deprecated
Unknown parameter encountered: "update encrypted"
Ignoring unknown parameter "update encrypted"
WARNING: The "idmap uid" option is deprecated
WARNING: The "idmap gid" option is deprecated
Processing section "[homes]"
Processing section "[netlogon]"
Processing section "[profiles]"
Processing section "[printers]"
Processing section "[pdf-documents]"
Processing section "[pdf-printer]"
Processing section "[music]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
	netbios name = SAMBA24
	server string = Samba file and print server
	interfaces = 127.0.x.x/8, 192.168.x.x/24
	bind interfaces only = Yes
	client schannel = No
	server schannel = No
	allow trusted domains = No
	obey pam restrictions = Yes
	guest account = smbguest
	passwd program = /usr/bin/passwd '%u'
	passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
	passwd chat timeout = 120
	username map = /etc/samba/smbusers
	password level = 6
	username level = 6
	unix password sync = Yes
	log file = /var/log/samba/samba.log
	max log size = 1000
	name resolve order = wins lmhosts bcast
	client signing = No
	client use spnego = No
	socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
	printcap name = cups
	machine password timeout = 120
	add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
	delete user script = /usr/sbin/userdel '%u'
	add group script = /usr/sbin/groupadd '%g'
	delete group script = /usr/sbin/groupdel '%g'
	add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
	delete user from group script = /usr/sbin/userdel '%u' '%g'
	add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
	logon script = %G.bat
	logon path = \\%L\profiles\%u
	logon drive = m:
	logon home = \\%L\homes\%u
	os level = 33
	local master = No
	domain master = No
	dns proxy = No
	remote announce = 192.168.x.xxx
	remote browse sync = 192.168.x.xxx
	template shell = /dev/null
	winbind separator = @
	winbind cache time = 360
	winbind use default domain = Yes
	winbind trusted domains only = Yes
	winbind nested groups = No
	winbind nss info = no
	idmap config * : range = 16777216-33554431
	idmap config * : backend = tdb
	hosts allow = 127., 192.xxx.x.
	cups options = raw
	follow symlinks = No

[homes]
	comment = Home Directories
	path = /home
	valid users = %U
	read only = No
	locking = No
	strict locking = No

[netlogon]
	comment = Network Logon Service
	path = /var/lib/samba/netlogon
	locking = No
	strict locking = No

[profiles]
	comment = User Profiles
	path = /var/lib/samba/profiles
	read only = No
	create mask = 0600
	directory mask = 0700
	locking = No
	strict locking = No

[printers]
	comment = All Printers
	path = /var/spool/samba
	printable = Yes
	print ok = Yes
	browseable = No
	locking = No
	strict locking = No

[pdf-documents]
	comment = Converted PDF Documents
	path = /var/lib/samba/pdf-documents
	admin users = %U
	read only = No
	guest ok = Yes
	locking = No
	strict locking = No

[pdf-printer]
	comment = PDF Printer Service
	path = /tmp
	guest ok = Yes
	printable = Yes
	print ok = Yes
	printing = bsd
	print command = /usr/bin/gadmin-samba-pdf %s %u
	lpq command = 
	use client driver = Yes

[music]
	comment = No comment
	path = /home/josh/Music
	locking = No
	strict locking = No
josh@josh-HP-Mini-210-1100:~$ ^C
josh@josh-HP-Mini-210-1100:~$ 

[B]And here's what I get with the command net usershare info --long
[/B]

josh@josh-HP-Mini-210-1100:~$ sudo net usershare info --long
Ignoring unknown parameter "update encrypted"

**Hostname command produces the following output -** 

josh@josh-HP-Mini-210-1100:~$ hostname
josh-HP-Mini-210-1100

**Finally with the smbtree command, I got this confusing output**

josh@josh-HP-Mini-210-1100:~$ smbtree
The program 'smbtree' is currently not installed. You can install it by typing:
sudo apt-get install smbclient
josh@josh-HP-Mini-210-1100:~$ sudo apt-get install smbclient
[sudo] password for josh: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

On a final note, I have noticed in several different tutorials that people enter commands in terminal using either sudo (which I understand to be the root) and # (which I understand to be superuser.) How do you decipher which one should precede a given command prompt? Sorry I know that's probably a lot more information heavy then I'm prepared for, but I thought it might be good to know for the purpose of what I am attempting to do. 

Let me know if you guys have more questions.

---

### Post by butt3rs84 on 2013-01-23
Realized the reason I couldn't install the smbtree package was because I was updating another software package. Now when I enter smbtree in terminal I get - "ignoring unknown parameter "update encrypted"

---

### Post by butt3rs84 on 2013-01-23
Hey Barry,

    Thanks for the help and suggestion about the webmin tool. I got that to run. Now when I attempt to connect from my mac to the linux using apple + K and then entering the following command "smb://127.0.x.x" I get the following error "The file server is available on your computer. Access the volumes and files locally."

---

### Post by Morbius1 on 2013-01-23
You have a number of critical problems:

** You used gadmin-samba.
*Nothing personal but I don't do Gadmin-Samba. Just not worth trying to fix. If somebody else wants to take it on great. I for one wish they would remove it from the repos.*

** You got an error message stating that you needed to install smbclient.
Smbclient has been a part of the base install of every Linux distro since Gereral Eisenhower became President. I don't know how it could not already be there so I'm wondering what other fundamental things are missing.

If it was my machine I would start over - at least with smb.conf:

(1) Make sure the following file exists: **/usr/share/samba/smb.conf**

(2) Make a backup of your current smb.conf
```
sudo mv /etc/samba/smb.conf /etc/samba/smb.conf.bak
```(3) Copy the default to it's new location:
```
sudo cp -a /usr/share/samba/smb.conf /etc/samba/
```(4) Go into smb.conf and fix one mistake:

Find the line:
encrypt passwords = no
and change it to:
encrypt passwords = yes

Then add add the following lines to the [global] section - right under the workgroup line:
```
netbios name = server210
name resolve order = bcast host lmhosts wins
```(5) Add your share to the end of smb.conf:
```
[music]
comment = No comment
path = /home/josh/Music
guest ok = no
```(6) Restart samba
```
sudo service smbd restart
sudo service nmbd restart

```

---

### Post by butt3rs84 on 2013-01-23
Greetings Morbius1,

   Thanks for your assistance. I completed those steps. From there what should I do as far as attempting to connect?

Regards,
Butt3rs84

---

### Post by Morbius1 on 2013-01-24
That should have been it given the state of your install. If you can't see the Linux box from your OSX machine you could use the miracle of avahi ( which is the Linux implementation of Apple's Bonjour ):

[1] Create a file:
```
gksu gedit /etc/avahi/services/samba.service
```[2] Add the following to the file:
```
<?xml version="1.0" standalone='no'?>
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
    <name replace-wildcards="yes">%h SMB</name> ## Display Name
    <service>
        <type>_smb._tcp</type>
        <port>445</port>
    </service>
</service-group>
```[3] Then save the file.

** Make sure avahi is running:
```
sudo service avahi-daemon status
```** And if you have a firewall in the way on Lubuntu disable it or at least make sure ports 445 and 5353 are open.

You should see it in OSX's Finder as "server210 SMB"

---

### Post by butt3rs84 on 2013-01-27
Hi all thanks for your help with everything I am happily copying my music files to my linux computer.

---

