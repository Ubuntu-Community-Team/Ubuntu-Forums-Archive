---
title: "Connect Kubuntu 16.04 laptop to usb printer in a windows 7 wireless home network"
date: 2017-02-24
forum: New to Ubuntu
---

### Post by cackerso on 2017-02-24
The home (wired/wireless) network is based on a windows 7 desktop.  The priner is connected to a usb port on the desktop.  The laptop is running Kubuntu 16.04.  I installed Samba on the laptop and configured the printer section of smb.conf

code
```

                     [INDENT]# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
;[profiles]
;  comment = Users profiles
;  path = /home/samba/profiles
;  guest ok = no
;  browseable = no
;  create mask = 0600
;  directory mask = 0700

[printers]
  comment = All Printers
  browseable = yes
  path = /var/spool/samba
  printable = yes
  guest ok = yes
  read only = yes
  create mask = 0700

# Windows clients look for this share name as a source of downloadable
# printer drivers
[print$]
  comment = Printer Drivers
  path = /var/lib/samba/printers
  browseable = yes
  read only = yes
  guest ok = yes
# Uncomment to allow remote administration of Windows print drivers.
# You may need to replace 'lpadmin' with the name of the group your
# admin users are members of.
# Please note that you also need to set appropriate Unix permissions
# to the drivers directory for these users to have write rights in it
;  write list = root, @lpadmin

/code

When I try to add a printer under KDE system settings,  printer --the printer isn't listed.  When I run testparm I get

code

                      [INDENT]landk@notX200:~$ sudo testparm 
[sudo] password for landk: *
Load smb config files from /etc/samba/smb.conf 
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384) 
WARNING: The "syslog" option is deprecated 
Processing section "[printers]" 
Processing section "[print$]" 
Loaded services file OK. 
Server role: ROLE_STANDALONE 

Press enter to see a dump of your service definitions 

# Global parameters 
[global] 
server string = %h server (Samba, Ubuntu) 
server role = standalone server 
map to guest = Bad User 
obey pam restrictions = Yes 
pam password change = Yes 
passwd program = /usr/bin/passwd %u 
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssu
ccessfully* . 
unix password sync = Yes 
syslog = 0 
log file = /var/log/samba/log.%m 
max log size = 1000 
dns proxy = No 
usershare allow guests = Yes 
panic action = /usr/share/samba/panic-action %d 
idmap config * : backend = tdb 

[printers] 
comment = All Printers 
path = /var/spool/samba 
create mask = 0700 
guest ok = Yes 
printable = Yes 
browseable = No 

[print$] 
comment = Printer Drivers 
path = /var/lib/samba/printers 
guest ok = Yes 
landk@notX200:~$

[/INDENT]
/code


[/INDENT]
```

---

### Post by SeijiSensei on 2017-02-24
You don't need to install Samba to connect to a shared Windows printer.  Samba makes the Linux machine into a Windows-style server.  Instead, you should be able simply to open a browser on Kubuntu and point it to [http://localhost:631/](http://localhost:631/).  Next choose "Adding Printers and Classes" and push the "Add Printer" button.  Enter your login name and password when prompted.  You'll see an entry for "Windows Printer via SAMBA".  Choose that and continue forward.

---

### Post by cackerso on 2017-02-27
Thanks, I got as far as a screen that asks for connection information and asks that I provide a URL for the printer.  Not knowing how to do that means I'm stuck.

---

### Post by SeijiSensei on 2017-03-01
Use
```
smb://ip.addr.of.printer/printer_share_name
```
So if the Windows machine is at 192.168.1.10 and shares the printer as something like "HP", then you'd use
```
smb://192.168.1.10/HP
```

Make sure the Windows machine has a fixed IP address.  You should use static addresses for anything running as a server so those machines will always be available at the same address.

---

### Post by cackerso on 2017-03-20
It seems like I'm either getting the IP address of the windows machine wrong or the name of the printer.  When I check "view network connections" in Windows I get 192.168.0.1.  I've also tried getting the IP address various other ways like using the command line (ipconfig).  There are variations listed for each network adapter.  I tried all of these (for IPv4) .  I also tried getting the IP address using Google. The name of the printer is in my case "HP LaserJet P2015 PCL6"  So in the connection box I put:

```


smb://192.168.0.1/HP LaserJet P2015 PCL6


```

I get:  "Bad Device-uri"

I tried all the different IP addresses I found.  For the printer name I also tried the printer name adding "on + (the name of my computer)"  

I always get the same error message.  What am I doing wrong?

---

### Post by mastablasta on 2017-03-20
the printer name is wrong (or at last not how it is seen outside of the windows machine). IP is probably correct.

there also used to be a command in linux smbtree or something like that that printed out the addresses as well as printer name. if you installed samba it should probably be there. it is part of smbclient package: 
[https://www.samba.org/samba/docs/man/manpages/smbtree.1.html](https://www.samba.org/samba/docs/man/manpages/smbtree.1.html)

it is similar to windows "network neighbourhood"


if you still can't locate it try changing the device name to something like HPLJP2015 or something.

if you still think IP is the issue you, can you post IPconfig (from win 7 cmd interface - mark, right click, copy, then paste here)

---

### Post by SeijiSensei on 2017-03-20
If you can change the name of the share in Windows so it has no embedded spaces, do that and try again.

If not, you might be able to replace the spaces with the %20 representation in the URL:

```
smb://192.168.0.1/HP%20LaserJet%20P2015%20PCL6
```

That's the standard for spaces in a URL.  If that doesn't work, try "escaping" the spaces with the backslash character:

```
smb://192.168.0.1/HP\ LaserJet\ P2015\ PCL6
```

In general, embedded spaces can cause various problems, especially on *nix systems since the space constitutes a delimiter in shells like bash.  I avoid embedded spaces whenever possible.

---

### Post by cackerso on 2017-06-03
Thanks for all the help.  I gave up.  It was an old printer and so I replaced it with a printer that I could connect to my router.  With a little fiddling that worked.

---

