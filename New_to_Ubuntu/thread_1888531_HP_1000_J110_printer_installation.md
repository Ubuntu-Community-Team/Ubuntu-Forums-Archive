---
title: "HP 1000 J110 printer installation"
date: 2011-11-29
forum: New to Ubuntu
---

### Post by Miqueridosims on 2011-11-29
Installing an HP 1000 J110 printer.
   
  I have seen that some people are looking for information on how to install a printer like this. ( like myself ).
  After my research I found that there is module that is ready in Ubuntu repositories and it is called HPLIP, so you can install this in the traditional way or using Synaptic.
  As far as I know the module on the repository will work for must of the printers, however for the new printers you might need to install the latest version of HPLIP which is the 3.11.10 version.
   
  What I basically did was to follow the direction from the HP website:
   
  [http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html](http://hplipopensource.com/hplip-web/install/manual/distros/ubuntu.html)
   
  Which at the beginning looks a little scary so I did a couple of practices on a virtual machine then I installed it on my ubuntu server.
   
  As far as I know this module contains more than 2,000 drivers so must likely that your printer&#8217;s driver will be here.
   
  If you need to download the hplip-3.11.10.tar.gz file from the terminal, this is the link that worked for me:
   
  [http://sourceforge.net/projects/hplip/files/hplip/3.11.10/hplip-3.11.10.tar.gz](http://sourceforge.net/projects/hplip/files/hplip/3.11.10/hplip-3.11.10.tar.gz)
   
  This might be useful for those who want to install an HP printer.
   
  This will complete the process for you to use your HP printer on your desktop, you just need to install it by going to the printing option on your system. However, if you need or want to install the printer on a server you need to edit the Samba configuration file (I am using Samba server):
   
  On the printers section I changed:
  
  [FONT=&quot]/etc/samba/smb.conf[/FONT]
  guest ok = yes
  brouseable = yes
   
  like the following:
   
  [FONT=&quot][printers][/FONT]
  [FONT=&quot]comment = Printer in Linux[/FONT]
  [FONT=&quot]path = /var/spool/samba[/FONT]
  [FONT=&quot]guest ok = [/FONT]**[FONT=&quot]Yes[/FONT]**
  [FONT=&quot]printable = Yes[/FONT]
  [FONT=&quot]use client driver = Yes[/FONT]
  [FONT=&quot]browseable = [/FONT]**[FONT=&quot]yes[/FONT]**
  
  This was done accordingly to Ubuntu documentation.
   
  [COLOR=blue]https://help.ubuntu.com/10.04/serverguide/C/samba-printserver.html[/COLOR]
   
  After this was done I was able to print either from Ubuntu and from Windows.
  Hope this works for you guys.


Any feedback is welcome

---

