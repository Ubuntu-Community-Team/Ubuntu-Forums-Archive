---
title: "Bad Samba Server Name on WinXP Network"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by robertkent on 2008-10-06
I am runing Samba on 8.04, serving files to a LAN with Windows XP machines.  Samba is also enabled as WINS server.  Samba Server machine is specified as WINS server and also included in Hosts file on all WinXP machines.

The Problem:
When I go to "My Network Places" and "Computers Near Me", I see all of the Windows machines listed, as well as the Ubuntu powered Samba Server, but the Samba Server has a bad machine name/description that seems to be a concatenation of the netbios name (which is also the Host name) and the server string from the smb.conf file as follows:
   netbios name:  ubuntu-server-AMD800
   server string: Ubuntu-Samba-Server
      -> name shown in "Computers Near Me":  
                    UBUNTU-SERVER-AMUbuntu-Samba-Server
Attempting to browse that machine produces the dreaded "not accessible" message.
However, performing a "Search for Computer" on the WinXP box using the correct netbios name (ubuntu-server-AMD800) finds the server, lists it under the correct name, and double-clicking it allows browsing of the shared directories.

I have flushed the dnscache on the WinXP boxes, rebooted all machines on the network, performed a global search on the server for the bad contatenated name, made various minor tweaks to the config files on both the WinXP boxes and the Samba Server . . . all with no correction to the problem (changing the server string DOES change the back portion of the concatenated name, which would tend to confirm it as the source of that portion of the bad name).

I have searched the Ubuntu forums, and the internet, in general, but no one seems to have experienced this problem.

Any help would be appreciated.

---

