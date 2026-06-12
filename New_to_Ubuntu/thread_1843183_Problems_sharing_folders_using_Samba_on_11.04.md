---
title: "Problems sharing folders using Samba on 11.04"
date: 2011-09-13
forum: New to Ubuntu
---

### Post by tdlucas on 2011-09-13
Hi,

I seem to have created a situation where I am sharing the entire contents of my Linux desktop (without password protection) on my home network instead of just the two folders I wish to share (with a password).

Posted below is as much detail as I can grab via Terminal that I think is relevent.

I have searched all over for a solution and tried a number of the suggestions in various threads but do not seem to find the answer. If someone could find the time to help and tell me what I'm doing wrong, I would be very grateful.

Cheers


tim@tim-desktop:~$ service smbd status 
smbd start/running, process 721 

- - - - - - - -- - - - - - - -- - - - - - - -- - - - - - - -- - - 

tim@tim-desktop:~$ net usershare info --long 
info_fn: file /var/lib/samba/usershares/fear of a blank planet (v0) is not a well formed usershare file. 
info_fn: Error was Path is not a directory. 
[downloads] 
path=/home/tim/Downloads 
comment= 
usershare_acl=Everyone:R,TIM-DESKTOP\tim:F, 
guest_ok=y 

info_fn: file /var/lib/samba/usershares/deadwing - v0 is not a well formed usershare file. 
info_fn: Error was Path is not a directory. 
[linuxshare] 
path=/home/tim/LinuxShare 
comment= 
usershare_acl=Everyone:R, 
guest_ok=y 

info_fn: file /var/lib/samba/usershares/the incident v0 is not a well formed usershare file. 
info_fn: Error was Path is not a directory. 

- - - - - - - -- - - - - - - -- - - - - - - -- - - - - - - -- - - 

tim@tim-desktop:~$ testparm -s 
Load smb config files from /etc/samba/smb.conf 
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384) 
Processing section "[printers]" 
Processing section "[print$]" 
Processing section "[tim]" 
Processing section "[Downloads]" 
Loaded services file OK. 
Server role: ROLE_STANDALONE 
[global] 
server string = %h server (Samba, Ubuntu) 
map to guest = Bad User 
obey pam restrictions = Yes 
pam password change = Yes 
passwd program = /usr/bin/passwd %u 
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* . 
unix password sync = Yes 
syslog = 0 
log file = /var/log/samba/log.%m 
max log size = 1000 
dns proxy = No 
usershare allow guests = Yes 
panic action = /usr/share/samba/panic-action %d 

[printers] 
comment = All Printers 
path = /var/spool/samba 
create mask = 0700 
printable = Yes 
browseable = No 

[print$] 
comment = Printer Drivers 
path = /var/lib/samba/printers 

[tim] 
path = /home/tim 
guest ok = Yes 

[Downloads] 
path = /home/tim/Downloads 
guest ok = Yes 

- - - - - - - -- - - - - - - -- - - - - - - -- - - - - - - -- - - 

tim@tim-desktop:~$ smbtree 
Enter tim's password:  
WORKGROUP 
\\TIM-DESKTOP     tim-desktop server (Samba, Ubuntu) 
\\TIM-DESKTOP\linuxshare     
\\TIM-DESKTOP\IPC$           IPC Service (tim-desktop server (Samba, Ubuntu)) 
\\TIM-DESKTOP\Downloads       
\\TIM-DESKTOP\tim             
\\TIM-DESKTOP\print$         Printer Drivers

---

### Post by cj13579 on 2011-09-13
From looking at what you have posted the two stand out things to me are these:

> [tim] 
path = /home/tim 
guest ok = Yes 

[Downloads] 
path = /home/tim/Downloads 
guest ok = Yes  

Try editing your /etc/smb.conf file to tweak your configuration. Also, this [link]("https://help.ubuntu.com/community/Samba/SambaServerGuide") is magic for setting stuff up.

---

### Post by Morbius1 on 2011-09-13
In addition to what cj13579 posted you are using 2 completely different methods to create samba shares:

These are Samba Usershares ( created from Nautilus ):
> linuxshare
downloadsThese are Samba Classic Shares:
> tim
downloadsYou will notice that you have "downloads" listed in both methods. It would be best if you removed one or the other of these shares. Also, all of your shares are configured for guest access.

---

