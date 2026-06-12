---
title: "network printing from ubuntu to windows"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by wizzardxexe on 2008-11-03
I have an ubuntu laptop with 8.10 installed. i have a desktop (running windows xp) that has a printer connected to it. i used to be able to print from my windows laptop to my windows desktop where it would go to the printer and print out, effectively allowing me to print from my laptop from anywher in the house, then i would walk into my office room and pick it up later. how would i do this wireless printing through ubuntu?

also if you can help me join my workgroup

---

### Post by ad_267 on 2008-11-03
You need to install the samba client to connect to windows network. You can install the smbfs and smbclient packages from synaptic or apt-get etc.

Then you can go to System - Administration - Printing - Server - Settings  and tick "Show printers shared by other systems".

See [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba) for more info.

---

### Post by wizzardxexe on 2008-11-03
tank you! i will try this!

---

### Post by ad_267 on 2008-11-03
Sorry I forgot to mention how to change your workgroup. You can press Alt-F2 and then run "shares-admin" and set this in the General Properties tab.

---

### Post by cariboo on 2008-11-03
You do not have to install samba in order to use a printer connected to a windows computer. Smbclient which is installed by default is all you need. The only two things you need to know are:

1. Is the printer supported in Linux
2. Is the workgroup the same on both computers

To find if the printer is supported go here:

[http://www.linuxprinting.org/printer_list.cgi](http://www.linuxprinting.org/printer_list.cgi)

Ubuntu defaults to WORKGROUP for a workgroup name and dpending which version of windows you are running. Windows XP Pro, Vista Office and Ultimate default to WORKGROUP. Win XP Home and all the rest of the Vista version default to MSHOME.

So make sure the workgroups are the same. In XP go to Start-->Control Panel-->System-->Computer Name to change the workgroup name.

In Ubuntu press Alt-F2 and type:

```
gksu gconf-editor
```

Enter your password when asked then click System-->smb, right-click workgroup, select Edit Key
and enter the workgroup to match the other computers on the network.

The final step is  to go to System-->Administration-->Printing, click New, then in the Printer Configuration window select Windows Printer via SAMBA. Next click the browse button, in the Smb Browse window your workgroup should show, click on the arrow nest to the workgroup and select your printer and click OK. Click forward and find your printer manufacurer and click forward. Find your printer model and click forward, Fill in the blanks and click forward, and you should be done.

---

### Post by ad_267 on 2008-11-03
I didn't say to install samba, only the samba client, I didn't realise it was installed by default.

---

