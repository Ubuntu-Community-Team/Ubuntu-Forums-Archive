---
title: "Shared File"
date: 2023-07-17
forum: New to Ubuntu
---

### Post by unbuntunewbie02 on 2023-07-17
Hi,

Basically i cannot understand why this is that difficult basically. I want to create a sharedFolder on my Ubuntu box and let my Windows PC access it. I have created a new user user1 and want this user to access the folder and  let my main user keeps its admin rights on that folder.

It would take me 5mins in Windows but not so quick in Ubuntu I have the sharedfolder created but when I browse as user1 or root it doesn't let me in a permissions error.

Can anyone assist

---

### Post by TheFu on 2023-07-17
30 seconds.

On ubuntu:```

$ sudo apt install ssh fail2ban
$ sudo ufw allow ssh
```

On Windows, install either Filezilla or WinSCP.  
Run either, use sftp mode.  
Point at the mDNS name {hostname.local} or IP address in the URL.  Use your linux userid and password for access.
This is secure enough for use over the internet, but it would be better if you setup ssh-keys and never use a password for login credentials.

Profit!

All OSes that have a network stack support sftp, so this can be used from Android or almost any Linux file manager. Just use sftp:// in the URL.

If you want to use non-standard methods, like samba, things are harder.  Thank MSFT for not producing a standards document, gaining comments from other players in industry, and implementing to the standard, so that interoperability is designed in from the start.  Realize that MSFT makes changes without consulting anyone else and those other people have to bring out their network analyzers to reverse engineer what MSFT did. Sometimes that's easy. Sometimes it take years.

---

### Post by TheFu on 2023-07-17
In short, always prefer standards based protocols over proprietary protocols kept secret by 1 company that isn't known for sharing.

---

### Post by unbuntunewbie02 on 2023-07-17
I would like to use it like Windows as I am going to have a third party program write to that folder and then a another third party program read the log files this is non internet facing i presume samba is the way to go.

---

### Post by TheFu on 2023-07-17
> **unbuntunewbie02 said:**
> I would like to use it like Windows as I am going to have a third party program write to that folder and then a another third party program read the log files this is non internet facing i presume samba is the way to go.

Probably, but when MSFT changed the CIFS protocol in Win10 and Win11, the samba guys and each distro had to make some hard choices about the default compatibility modes. This made it non-trivial to get Samba working with Win11/Win10 from what I can see.

You wanted something fast.  I showed a 30 second solution. Sorry, it isn't exactly what you needed.  BTW, there's also **sshfs** for any Unix system to use to remotely mount storage so it appears as local storage.  I have no idea if sshfs is available for Windows.  [https://superuser.com/questions/1750720/windows-cant-find-sshfs](https://superuser.com/questions/1750720/windows-cant-find-sshfs) seems to say it does work, but it isn't built-into Windows.

If I still used MS-Windows, I'd probably have a samba/CIFS setup working.  Morbius' posts in these forums around samba and whatever version of MS-Windows you are running is where I'd start to figure out what's needed.  I think the only certain way to get it working for Win10 and Win11 is by manually editing the /etc/samba/smbd.conf file and using the IP address in the URL for access.  MSFT changed the discovery protocol used from nmbd to mDNS, I think.  "Browsing"  to a network share won't work anymore.

---

### Post by Morbius1 on 2023-07-17
Please post the output of the following commands so we can all see how you configured samba:
```
testparm -s
```
```
net usershare info --long
```
```
hostname
```

And what version of Windows are you using?

---

### Post by unbuntunewbie02 on 2023-07-18
```


testparm -s
Load smb config files from /etc/samba/smb.confLoaded services file OK.
Weak crypto is allowed


Server role: ROLE_STANDALONE


# Global parameters
[global]
    log file = /var/log/samba/log.%m
    logging = file
    map to guest = Bad User
    max log size = 1000
    obey pam restrictions = Yes
    pam password change = Yes
    panic action = /usr/share/samba/panic-action %d
    passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
    passwd program = /usr/bin/passwd %u
    server role = standalone server
    server string = %h server (Samba, Ubuntu)
    unix password sync = Yes
    usershare allow guests = Yes
    idmap config * : backend = tdb




[printers]
    browseable = No
    comment = All Printers
    create mask = 0700
    path = /var/spool/samba
    printable = Yes




[print$]
    comment = Printer Drivers
    path = /var/lib/samba/printers




[Logs]
    path = /Var/www/html/SupportDesk/Logs
    read only = No
    valid users = @webserver @wupdates



```

```

net usershare info --long
info_fn: file /var/lib/samba/usershares/logs is not a well formed usershare file.
info_fn: Error was Path not allowed.

```

```

hostname
webserver01

```

---

### Post by unbuntunewbie02 on 2023-07-18
Also the Log of the samba file for my test machine:

Windows 11 version 22H2

```

[2023/07/17 16:08:14.182745,  0] ../../source3/param/loadparm.c:3448(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/logs failed. Permission denied
[2023/07/17 16:08:14.357484,  0] ../../source3/param/loadparm.c:3448(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/logs failed. Permission denied
[2023/07/17 16:08:14.599297,  0] ../../source3/param/loadparm.c:3448(process_usershare_file)
  process_usershare_file: stat of /var/lib/samba/usershares/logs failed. Permission denied

```

---

### Post by Morbius1 on 2023-07-18
Looks like you tried to create a samba share form the file manager and it failed for some reason.

You can post the output of the usershare share definition file if you want so we can see why:

```
cat /var/lib/samba/usershares/logs
```

Just as a test of the process though I would suggest going old school with samba. For example:

Create a Test folder:
```
sudo mkdir /Test
```
Take possession of that folder by your main user - using your own user name instead of mine:
```
sudo chown morbius /Test
```
Then edit /etc/samba/smb.conf and at the end of the file add this to it:
```
[Test]
path = /Test
read only = No
guest ok = yes
force user = morbius
```
Save the file and restart samba:
```
sudo service smbd restart
```

[I][COLOR="#0000CD"]Note: If you want this share to be accessible only to the "user1" user you mentioned above change the share definition to this:
```
[Test]
path = /Test
read only = No
guest ok = no
valid users = user1
force user = morbius
```

Just make sure you added user1 to the samba password database:
```
sudo smbpasswd -a user1
```[/COLOR][/I]

Now on the Win11 system address this server and the Test share in explorer:
```
\\webserver01.local\Test
```
Don't forget the .local at the end of the Linux host name when addressing the server.

Note: If you install the wsdd package in Ubuntu Win11 should be able to "discover" your server on it's own through explorer:
```
sudo apt install wsdd
```

---

### Post by unbuntunewbie02 on 2023-07-18
```

cat /var/lib/samba/usershares/logs#VERSION 2
path=/var/www/html/SupportDesk/Logs
comment=
usershare_acl=S-1-1-0:F
guest_ok=n
sharename=Logs

```

---

### Post by unbuntunewbie02 on 2023-07-18
On both of the shares test and logs i get the error: Error Code 0x80070043 The network name cannot be found and in the samba log ake_connection_snum: canonicalize_connect_path failed for service Logs,

---

### Post by unbuntunewbie02 on 2023-07-18
On both of the shares test and logs i get the error: Error Code 0x80070043 The network name cannot be found and in the samba log ake_connection_snum: canonicalize_connect_path failed for service Logs,

---

### Post by Morbius1 on 2023-07-18
I guess you'll have to use the ip address like you were doing.

It appears avahi is either not installed or not running on your system. Since you created your shares from a file manager I assumed you were using desktop ubuntu. If you are using Ubuntu server you need to install avahi:
```
sudo apt install avahi-daemon.
```

Doesn't really matter if you are using an ip address.

[COLOR="#B22222"]EDIT[/COLOR]: misspelled avahi-daemon

---

### Post by TheFu on 2023-07-18
> **unbuntunewbie02 said:**
> On both of the shares test and logs i get the error: Error Code 0x80070043 The network name cannot be found and in the samba log ake_connection_snum: canonicalize_connect_path failed for service Logs,

Just have to ask, did you restart the smbd dæmon using **systemctl**?  Rebooting the machine would do that as well.  I vaguely remember that samba sometimes needed a full reboot, though I've never seen that myself.  My knowledge on samba doesn't include any MS-Windows versions that are currently supported by MSFT.

---

### Post by unbuntunewbie02 on 2023-07-24
Sorry been on annual leave, I can access the share but cannot write anything to the file or create files.

---

