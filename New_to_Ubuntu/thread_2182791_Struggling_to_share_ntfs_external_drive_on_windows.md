---
title: "Struggling to share ntfs external drive on windows network"
date: 2013-10-22
forum: New to Ubuntu
---

### Post by Ant01 on 2013-10-22
I'm about to give up due to absolute frustration. I've been trying to get into Ubuntu but am really getting frustrated in trying to use a external hardrive (ntfs) which has my music and other backup docs on it.

I had it configured correctly once before using ubuntu 11 but I find the latest versions of ubuntu more confusing and more problematic. 

Please can someone give me a simple solution to how I can share my files over the windows network as this is crucial to me using ubuntu. I have followed Nixie video on You Tube using Samba  [http://www.youtube.com/watch?v=-wUfzdiE4m8](http://www.youtube.com/watch?v=-wUfzdiE4m8) which so far has been the best  help and I am able to share my ext files but not my ntfs files. This seems like such a basic thing to be able to do but from my research it seems that a lot of people are having the same problem

Please help.....

---

### Post by Morbius1 on 2013-10-22
Please post the output of the following commands:
```
testparm -s
```
```
net usershare info --long
```

---

### Post by Ant01 on 2013-10-22
antoine@TOVA:~$ testparm -s
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[$AVG]"
Loaded services file OK.
Server role: ROLE_STANDALONE
[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	guest account = antoine
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	username map = /etc/samba/smbusers
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d
	idmap config * : backend = tdb
	guest ok = Yes

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	print ok = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers

[$AVG]
	path = /media/antoine/External/$AVG
	read only = No
antoine@TOVA:~$ ^C

---

### Post by Ant01 on 2013-10-22
antoine@TOVA:~$ net usershare info --long
[$AVG]
path=/media/antoine/External/$AVG
comment=
usershare_acl=Everyone:F,
guest_ok=y

antoine@TOVA:~$

---

### Post by Morbius1 on 2013-10-22
Other than the fact that you are using two different samba methods to share the same folder there doesn't seem to be a problem with the way you are set up assuming you haven't set up any samba users and the client isn't windows. 

I'm not a 100% sure of that "$" in front of the share name though. If it was at the end the share would be invisible to windows but in the front I don't know if that a legitimate character or not.

What is the nature of the problem?
 You can't see the share or you are denied access? 
What is the error message on the client?
Is the client Windows or Linux?

---

### Post by Ant01 on 2013-10-22
Thank you for the help, im really not sure which version of samba i'm using I followed the video link above. As I mentioned I am able to share and access the linux folders via the windows network. I can see the shared ntfs folder /media/antoine/External/$AVG but i cant access it from the windows network. I get a error message; 
[I]windows can't access \\TOVA\$avg
You do not have permission to access \\TOVA\$avg. Contact your network administrator to request access[/I]

---

### Post by Morbius1 on 2013-10-22
I'm making a lot of assumptions here to spare you from asking a whole bunch more questions so give  this a shot:

Edit /etc/samba/smb.conf and add the following line right under the workgroup line towards the top of the file:
```
force user = antoine
```
Then save the file and restart samba:
```
sudo service smbd restart
```
[COLOR=#0000cd]*Note: when you restart smbd the network has a bit of a hissy fit so give it a few minutes then try to access the share again.*[/COLOR]

---

### Post by Ant01 on 2013-10-22
Thank you very much for the help, its working.

I wont be able to use the samba user group as in the video example but its will do at least I can get access to the drive even if the security is not 100%

---

### Post by Morbius1 on 2013-10-22
You wouldn't be able to use the samba user group ( whatever that is ) under any circumstances any way. Run the following command:

```
getfacl -t /media/antoine
```
Linux has a hierarchical file system even when it mounts an ntfs partition. Put up a roadblock anywhere along the path to the target folder to a given user or group and you've stopped access. The output of that command should indicate that the only user besides root that can access anything under /media/antoine is antoine. 

This /media/$USER directory is a new idea and is system generated. It has caused all sorts of confusion and anguish for many.

---

### Post by Ant01 on 2013-10-23
antoine@TOVA:~$ getfacl -t /media/antoine
getfacl: Removing leading '/' from absolute path names
# file: media/antoine
USER   root      rwx     
user   antoine   r-x     
GROUP  root      ---     
mask             r-x     
other            ---     

antoine@TOVA:~$

---

### Post by Ant01 on 2013-10-23
Once again thank you for all the help :guitar:

---

