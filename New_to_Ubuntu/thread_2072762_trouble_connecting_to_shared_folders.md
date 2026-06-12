---
title: "trouble connecting to shared folders"
date: 2012-10-18
forum: New to Ubuntu
---

### Post by Frank6060 on 2012-10-18
Hello,

I have Ubuntu 12.04 running on a dedicated machine.  I need to share the data in three folders with my small office.
Around 25 PCs - mostly Win 7. The folders 
I have set the folders up as shared with full read/write, add/delete privileges.
I have created the users with the same passwords they use to log onto their own PCs.
No one but myself can log into these shared folders.
Each folder is visible and the log-in dialog appears but the user name or password (or both) are not being accepted.

Any ideas?

Frank

---

### Post by GreenTaurus on 2012-10-18
Frank, you'll need to get an app called SAMBA and then either set up an open share, or one restricted by user.

I prefer terminal and the command line to install, but your mileage may vary...

sudo apt-get install samba

sudo gedit /etc/samba/smb.conf

make sure security = share (not user)

make sure guest account = nobody (yes, exactly like this)

[Fileshare]
        comment = File access share
        path = /path/to/dir/to/share
        browseable = yes
        read only = yes
        guest ok = yes

All of these are case sensitive...so be careful.

---

### Post by Morbius1 on 2012-10-18
** Please post the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by Frank6060 on 2012-10-18
frank@UB1Server1:~$ testparm -s

Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE

[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:
* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb

printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers




frank@UB1Server1:~$ net usershare info --long

[Y_Drive]path=/home/frank/Y_Drivecomment=usershare_acl=Everyone:F,guest_ok=n
[I_Drive]path=/home/frank/I_Drivecomment=usershare_acl=Everyone:F,guest_ok=n
[OA_Data]path=/home/frank/OA_Datacomment=usershare_acl=Everyone:F,guest_ok=n

---

### Post by Morbius1 on 2012-10-18
Your smb.conf looks textbook correct so that brings us to the usershares.

What are the ownership and permissions of these directories? For example:
```
ls -dl /home/frank/Y_Drive
```All of your shares require authentication to gain access. Windows user mary may have the correct credentials for Samba to allow access but unless the Linux permissions allow it she won't get very far.

There are a number of ways to accomplish this:

[1] You could set the Linux permissions allowing everyone access and then use Samba as the gatekeeper allowing only those with correct credentials to pass:
```
chmod 0777 /home/frank/Y_Drive
```[2] You could get fancy and make all these Windows users part of a unique group and then allow only those group members access:
```
chmod 0770 /home/frank/Y_Drive
chown :plugdev /home/frank/Y_Drive

```[COLOR=Blue][I]plugdev is a preexisting group.

[/I][COLOR=Black][3] If you don't care about who has the ability to delete files saved by someone else you can even make all remote users appear to be you:

Add the following line to the [global] section - right uner the workgroup line - in /etc/samba/smb.conf:
[/COLOR][/COLOR]```
force user = frank
```[COLOR=Blue][COLOR=Black]
Then restart samba:
[/COLOR][/COLOR]```
sudo service smbd restart
```[COLOR=Blue][COLOR=Black]
[COLOR=Blue]*The remote users will be asked for credentails and once Samba admits them they will appear to be frank for these shares. *[/COLOR]

It all depends on how much control you want to have over these Windows users.

[COLOR=Blue]**EDIT**[/COLOR]: These Y_Drive and I_Drive folders sound an awfull lot like NTFS mount points to me. If that's true then all this chown and chmod won't work. You would have to adjust the mount parameters in fstab or elsewhere to change the apparent permissions.

[/COLOR][/COLOR]

---

