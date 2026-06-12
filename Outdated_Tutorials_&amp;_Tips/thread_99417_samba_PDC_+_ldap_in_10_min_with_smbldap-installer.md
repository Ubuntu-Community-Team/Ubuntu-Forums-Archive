---
title: "samba PDC + ldap in 10 min with smbldap-installer"
date: 2005-12-05
forum: Outdated Tutorials &amp; Tips
---

### Post by kejar31 on 2005-12-05
I don't know if most of you are aware of this easy installer script. It really makes things very easy. It even sets up roaming profiles for you.

Just download the latest version from one of the mirors on his sight. Extract the contents in a temp directory and type 
"./smbldap all" as root ( or sudo it )

it will apt-get any needed sofware, although you will need to update you repositories with Universe and maybee Multiverse.

here is the link to the site that provides the script.

[http://majen.net/smbldap/](http://majen.net/smbldap/)

---

### Post by chele on 2006-01-03
The script would not accept my domain name, as it is not a full Internet domain name, but simply a local single part name.

---

### Post by quinreis on 2007-11-23
Help! It doesn't work anymore with gutsy.
I just did a fresh install, and when I reboot the server hangs up .
The last message was   " * Starting kernel log daemon...       "
It used to work a treat with feisty.

OK it sort of works- there is something wrong with the init scripts. 
If I boot in maintenence mode and manualy run
     /etc/init.d/slapd start
and then 
     init 2

it seems to boot up. For some reason the ldap server is not starting in time, which screws up all autenticationand I'm too thick to work it all out. I'm going back to feisty for now.

---

### Post by Nevell on 2008-05-11
New version 4.0 is out, but documentation not already yet :(

Maybe somebody write the full how-to, how can create Samba PDC + LDAP server with Samba/LDAP Installer from begin to finish? Because i don't understand what i need doing after installation. PC not included in to the domain with root user, i read the error message: "Username not found". But i loaded phpLDAPadmin and see user root. Something wrong...

Related links:
[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)
[http://ubuntuforums.org/showthread.php?t=708212](http://ubuntuforums.org/showthread.php?t=708212)
[https://help.ubuntu.com/community/LDAP-Samba_PDC_(for_Linux_and_Windows)]("https://help.ubuntu.com/community/LDAP-Samba_PDC_(for_Linux_and_Windows)")

---

