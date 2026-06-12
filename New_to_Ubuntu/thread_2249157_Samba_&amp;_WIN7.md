---
title: "Samba &amp; WIN7"
date: 2014-10-20
forum: New to Ubuntu
---

### Post by Pete_Best on 2014-10-20
Kubuntu
2 * WIN7
WLAN Router

Kubuntu installed. Samba installed. I can browse from Kubuntu (14.04) WIN7 shared folder and read/write.

Problem is I cannot access from WIN7 to Kubuntu. I can ping. But when use //192.168.x.x nothing happens.I cannot see ubuntu computer on networks.

Share work awhile ago, but after playing around (installed some linux firewall GUI, no-ip software : now both should be uninstalled), cannot access. 

Ubuntu folder share should be ok.

What could be the problem and is there step by step to search, what is wrong?

Thanks

---

### Post by sotiris2 on 2014-10-20
I am not familiar with ufw which is the firewall used in ubuntu but what you did amount to this. 

1)You had UFW (uncomplicated firewall) in your systems with default settings that didn't prohibit samba (ufw is included in install)
2) You installed some GUI or else called a front-end which is actually not a firewall, but a graphical tool to change settings in the actuall firewall (uwf)
3) You unistalled the GUI but this doesn't really undo the changes done by it to the firewall settings, ergo problem remains.

Hopefully a lot of people here are good with ufw and samba, so you 'll probably get some help soon.

---

### Post by Pete_Best on 2014-10-20
Thanks for the reply. 
And I think there will be at least some way to check (some command) that shows, if the problem is because of this firewall.

---

### Post by sotiris2 on 2014-10-20
Well ```
sudo ufw disable
``` will disable the firewall totally. Therefore if you still can't use samba it may not be related. If you suddenly can, well probably firewall is at fault. 

However this is not a temporary change so even if you restart you will have no firewall at all. If you find this risky, you can re-enable it with ```
sudo ufw enable
```

---

### Post by Pete_Best on 2014-10-20
Thank you for this info. Will help to identify if the problem is with firewall.

---

### Post by mr-woof on 2014-10-20
hi,

I've been playing with this as well, as I use Mint 17 on my desktop and have a Windows 7 laptop. Try and disable the firewall first and see what happens, does it ask for any username/password?

What does your smb.conf look like with the share you've created? /etc/samba/smb.conf

---

### Post by Pete_Best on 2014-10-20
This is waht I did : [http://askubuntu.com/questions/488191/how-to-get-network-to-see-14-04-desktop](http://askubuntu.com/questions/488191/how-to-get-network-to-see-14-04-desktop)

Uninstall and reinstall

Firewall disable did not help.

Thank you eveyone

---

### Post by Pete_Best on 2014-10-20
Still problems, cannot see anymore Kubuntu from WIN7

[FONT=Ubuntu Mono]smbstatus
[/FONT]Samba version 4.1.6-Ubuntu
PID     Username      Group         Machine                        
-------------------------------------------------------------------
Failed to initialize session_global: NT_STATUS_ACCESS_DENIED


Service      pid     machine       Connected at
-------------------------------------------------------
Failed to initialize session_global: NT_STATUS_ACCESS_DENIED
Failed to traverse sessions: NT_STATUS_ACCESS_DENIED


No locked files

------------------
petelinux@petelinux-Latitude-D510:/etc/samba$ testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Processing section "[sharedfolder]"
Loaded services file OK.
Server role: ROLE_STANDALONE

There say some problems?

---

### Post by Pete_Best on 2014-10-20
Now moving from Kubuntu to Ubuntu; fresh install. :( :( Too much hitting head on the wall

---

