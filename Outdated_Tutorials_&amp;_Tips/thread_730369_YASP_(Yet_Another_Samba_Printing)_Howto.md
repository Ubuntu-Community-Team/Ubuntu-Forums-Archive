---
title: "YASP (Yet Another Samba Printing) Howto"
date: 2008-03-20
forum: Outdated Tutorials &amp; Tips
---

### Post by paradexes on 2008-03-20
This HOWTO is aimed at people who want to setup a server that will print to Windows clients, AND push the drivers out to the client as well. 

This tutorial assumes the following:
You have a basic knowledge of unpacking tar files, command line usage and installing deb files using dpkg. Overall a basic knowledge of the linux commandline.
You have SAMBA 3.x installed
You have the latest CUPS installed
You are not looking for a restricted or AD based printing setup. Just a general printing share setup with Windows clients drivers. Restricted SAMBA/CUPS printing is outside of the scope of this document. 

The following server setup was built using Ubuntu server 7.10 If you MUST use a GUI I recommend downloading and installing webmin to manage the samba component (again not covered in this document)

Below is the SMB.conf file used to make this configuration fully push windows drivers out to Windows clients. 

 	[global]
load printers = yes
printing = cups
printcap name = cups
security = share ##Change to user ONLY when installing or updating drivers see step 5 for details##

	[printers]
comment = All Printers
path = /var/spool/samba
browseable = no
public = yes
guest ok = yes
writable = no
printable = yes

	[print$]
comment = Printer Drivers
path = /etc/samba/drivers
browseable = yes
guest ok = yes
read only = yes
write list = root
###Important!! if a print server is ALL you are running then this config will work and be secure enough. It is generally not recommended with most samba setups to have security = share. However for a standalone print server without restrictions this should work just fine. 

1. Setup your CUPS printers (Plenty of CUPS howtos) 

2. Download the CUPS windows drivers [http://www.cups.org/windows/software.php?6.0](http://www.cups.org/windows/software.php?6.0)
You can use alien to convert the RPM to a deb OR use the tar.gz file 

3. use the above smb.conf save it then restart samba 
```
/etc/init.d/samba restart
``` 
(or if you have debian helper scripts installed) 
```
service samba restart 
```

4. add root to your samba setup. 
```
smbpasswd root
``` 
(create your password at the prompt) Do not skip or you will get errors in the next step.
5. IMPORTANT!! Set smb.conf security = share to user or else the command WILL fail. Disconnect the system from the network othereise the next command will likley fail. It is searching for a domain controller.
type cupsaddsmb -H localhost -U root -a -v (enter password set in smbpasswd)
-your output should demonstrate that the files were copied. 
If you are getting errors please post them in this thread.

After all this is done change the line on your smb.conf security =  user back to share and then restart samba. 

Assuming you have printers already setup your windows client should now be able to connect AND get the drivers. If you get a message stating you need to install a driver on the windows side, then something is still wrong. The cupsaddsmb did not work. However these are the configuration steps that worked for me after much research and reading. I hope they also prove useful to others as I am sure I am not the only one dealing with this.

---

### Post by lcpuser on 2009-01-06
This Howto has been very helpful, but I am still having issues with the last step.  When I run

cupsaddsmb -H localhost -U root -a -v

I get No Windows printer drivers are installed!

These steps were followed
1) CUPS is up and running
2) Downloaded drivers (not sure what to do with them, placed them in several places (e.g /etc/samba/drivers)?
3) Restarted samba
4) Added root to samba
4.1 ) changed security = share to security = user
4.2 ) restarted samba
5) cupsaddsmb -H localhost -U root -a -v
 fails with output No Windows printer drivers are installed!

I suspect step two is not complete or some permission issue.  Can you shed an light on this?

---

### Post by lcpuser on 2009-01-07
Ok after much trial and (mostly) error I got this to work!  At least for postscript drivers.  Issues I encountered are detailed below.

from above
Step 2) files should be copied to /usr/share/cups/drivers.  for generic postscript printing these are the files you need to copy at a minimum.  For windows 2K/XP these files need to be lowercase, or it will not work!

ps5ui.dll
pscript5.dll
pscript.hlp
pscript.ntf

cups6.inf
cups6.ini
cups6.ppd (this may be not be needed)
cupsps6.dll
cupsui6.dll

Documentation I read was not very clear, but I think either set will work.  To be sure I copied all 9 of them.  However, when I ran the cupsaddsmb command, I think only the first four were copied.  Its possible that if the windows postscript files were not there, the cups files would have been copied, but I am not sure.  If you are using a VM, this would be a good place to take a snapshot and try it both ways.

step 4)smbpasswd root --if you have never setup a user for this it will be
       smbpasswd -a root ( -a will add the user)


step 5) don't forget to temporarily change 
        security = share to security = user in your smb.conf
        after you have uploaded the drivers you can change it back


        if you are getting this error:
        "Tree connect failed:NT_STATUS_BAD_NETWORK_NAME" you are likely missing /etc/drivers/samba directory, 
        $ sudo mkdir /etc/drivers/samba   will fix this

The following documents were very helpful.  From broad SAMBA drilling down to the CUPS and them specifically cupsaddmsb.  Useful for errors

[http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection)
[http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/CUPS-printing.html](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/CUPS-printing.html)
[http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/CUPS-printing.html#cupsadd-ex](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/CUPS-printing.html#cupsadd-ex)



the log file /var/log/samba may be of some use:D

---

### Post by matiasl on 2009-02-03
I have it working fine with 32bit clients (both vista and xp) but when trying to connect to a printer (and automatically install drivers) with a 64-bit vista client I get following: 
"Windows Cannot connect to the printer. Operation could not be completed (error 0x000003eb)."

If I look in the print$ share there are a folder x64 where there are the drivers. The only thing I notice is that the x64 bit folder is missing the cups6.inf.

Any ideas ?

---

### Post by lcpuser on 2009-02-03
If you are missing files, I think you can just copy the missing files and rerun **cupsaddsmb**.  

32-bit
/usr/share/cups/drivers

64-bit
/usr/share/cups/drivers/x64 


    cups6.inf (from [www.cups.org](www.cups.org))
    cups6.ini (from [www.cups.org](www.cups.org))
    cupsps6.dll (from [www.cups.org](www.cups.org))
    cupsui6.dll (from [www.cups.org](www.cups.org))
    ps5ui.dll (from your Windows system)
    pscript.hlp (from your Windows system)
    pscript.ntf (from your Windows system)
    pscript5.dll (from your Windows system)

[http://www.cups.org/documentation.php/man-cupsaddsmb.html](http://www.cups.org/documentation.php/man-cupsaddsmb.html)

According to the link above, both folders need all the files before the copy.

After cupsaddsmb I think the drivers will show up in
/etc/samba/drivers/W32X86
/etc/samba/drivers/?????? (not sure what the 64-bit folder is)

or whatever folder you specified in the [print%] of smb.comf

---

### Post by matiasl on 2009-02-04
> **lcpuser said:**
> If you are missing files, I think you can just copy the missing files and rerun **cupsaddsmb**.  

32-bit
/usr/share/cups/drivers

64-bit
/usr/share/cups/drivers/x64 


    cups6.inf (from [www.cups.org](www.cups.org))
    cups6.ini (from [www.cups.org](www.cups.org))
    cupsps6.dll (from [www.cups.org](www.cups.org))
    cupsui6.dll (from [www.cups.org](www.cups.org))
    ps5ui.dll (from your Windows system)
    pscript.hlp (from your Windows system)
    pscript.ntf (from your Windows system)
    pscript5.dll (from your Windows system)

[http://www.cups.org/documentation.php/man-cupsaddsmb.html](http://www.cups.org/documentation.php/man-cupsaddsmb.html)

According to the link above, both folders need all the files before the copy.

After cupsaddsmb I think the drivers will show up in
/etc/samba/drivers/W32X86
/etc/samba/drivers/?????? (not sure what the 64-bit folder is)

or whatever folder you specified in the [print%] of smb.comf

Done that and everything seems to show up in the print$ share so I guess that this is caused by yet another vista feature.

---

### Post by paradexes on 2009-02-05
I will edit the howto to reflect the x64 bit aspect. Probably be real handy for environments running x64 bit Windows OSes.

---

### Post by fluxerj on 2009-02-06
With respect to browsing the XP box, I can see XP from the FC3 file browser (appears in network:/// but not in smb:///) and can list default shares using smbclient -L (see output below), but user and printer shares are not visible. When I connect to either a Windows XP machine or the linux box from another windows machine, everything is fine. All machines are configured to be in the same Windows workgroup.

---

### Post by paradexes on 2009-02-17
> **lcpuser said:**
> Ok after much trial and (mostly) error I got this to work!  At least for postscript drivers.  Issues I encountered are detailed below.

from above
Step 2) files should be copied to /usr/share/cups/drivers.  for generic postscript printing these are the files you need to copy at a minimum.  For windows 2K/XP these files need to be lowercase, or it will not work!

ps5ui.dll
pscript5.dll
pscript.hlp
pscript.ntf

cups6.inf
cups6.ini
cups6.ppd (this may be not be needed)
cupsps6.dll
cupsui6.dll

Documentation I read was not very clear, but I think either set will work.  To be sure I copied all 9 of them.  However, when I ran the cupsaddsmb command, I think only the first four were copied.  Its possible that if the windows postscript files were not there, the cups files would have been copied, but I am not sure.  If you are using a VM, this would be a good place to take a snapshot and try it both ways.

step 4)smbpasswd root --if you have never setup a user for this it will be
       smbpasswd -a root ( -a will add the user)


step 5) don't forget to temporarily change 
        security = share to security = user in your smb.conf
        after you have uploaded the drivers you can change it back


        if you are getting this error:
        "Tree connect failed:NT_STATUS_BAD_NETWORK_NAME" you are likely missing /etc/drivers/samba directory, 
        $ sudo mkdir /etc/drivers/samba   will fix this

The following documents were very helpful.  From broad SAMBA drilling down to the CUPS and them specifically cupsaddmsb.  Useful for errors

[http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection)
[http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/CUPS-printing.html](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/CUPS-printing.html)
[http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/CUPS-printing.html#cupsadd-ex](http://us1.samba.org/samba/docs/man/Samba-HOWTO-Collection/CUPS-printing.html#cupsadd-ex)



the log file /var/log/samba may be of some use:D

That error will more often than not come up also because it is trying to connect to a domain controller that the server is not authenticated to.

In my case I forgot to note that I took the system off the network and ran the cupsaddsmb command. That did the trick as well. But you can get it if the drivers are not in the right location as well. So far the setup as posted has worked well for me.

---

