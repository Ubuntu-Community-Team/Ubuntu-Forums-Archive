---
title: "Samba (smbd) crash issue"
date: 2015-07-14
forum: New to Ubuntu
---

### Post by anoop8 on 2015-07-14
Hi members,
 
I am trying to create samba shared directory named **printShareNew **on my Android device. I am using samba version 4.1.14.
When I try to run smbd through command smbd restart, it crashes giving below mentioned error.
 
**[2015/11/18 06:50:30,  0] ../source3/smbd/server.c:1197(main)**
**  smbd version 4.1.14 started.**
**  Copyright Andrew Tridgell and the Samba Team 1992-2013**
**[2015/11/18 06:50:30.466589,  0] ../source3/param/loadparm.c:3189(lp_do_parameter)**
**  Global parameter map to guest found in service section!**
**[2015/11/18 06:50:30.467206,  0] ../source3/param/loadparm.c:2377(service_ok)**
**  WARNING: No path in service Click here to get started! - making it unavailable!**
**[2015/11/18 06:50:30.469647,  0] ../source3/smbd/server.c:1277(main)**
**  standard input is not a socket, assuming -D option**
**[2015/11/18 06:50:30.481138,  0] ../source3/auth/auth_util.c:786(get_guest_info3)**
**  SamInfo3_for_guest: Unable to locate guest account [nobody]!**
**[2015/11/18 06:50:30.481553,  0] ../source3/auth/auth_util.c:855(make_new_session_info_guest)**
**  get_guest_info3 failed with NT_STATUS_NO_SUCH_USER**
**[2015/11/18 06:50:30.482497,  0] ../source3/smbd/server.c:1441(main)**
**  ERROR: failed to setup guest info.**
 
Here is the configuration in my smb.conf file.
 
[global]
    workgroup = WORKGROUP
    netbios name = Device-000000
    interfaces = xx.xxx.xxx.xx/255.255.252.0 192.168.43.1/255.255.255.0
#    server role = active directory domain controller
    security = user
    map to guest = Bad Password
 
[Click here to get started!]
    path = /sdcard/Share
    guest ok = yes
 
[**printShareNew**]
    path = /data/ **printShareNew**
    comment = samba share
    public = yes
    available = yes
    writable = yes
    printable = no
    create mask = 0755
    browseable = yes
 
Could anybody please let me know how to solve this issue?
I will be really grateful for this kind help.
 
Thanks & regards,
Anoop.

---

