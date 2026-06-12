---
title: "Print from a windows XP freenx client to a local printer"
date: 2006-05-06
forum: Outdated Tutorials &amp; Tips
---

### Post by rvergara on 2006-05-06
Freenx has opened a whole new set of possibilities for deployment of enterprise applications. Any thin client can remotely access enterprise applications running in a central freenx server via Internet and still have good to excellent performance. However in order to fully realize the benefits of this solution, it is required that the remote clients have local printing capability.

Local printing is not functional for Gnome (nor KDE) based Ubuntu freenx servers out of the box but is the intention of this post, to explain how to get this capability set up. The solution is not final and still require fine tuning as I will explain later in this note. I am sure than a more experienced user than I will be able to refine the solution.

I will assume that Freenx is already installed, if not you can follow instructions in the following thread [http://www.ubuntuforums.org/showthread.php?t=97277]("http://www.ubuntuforums.org/showthread.php?t=97277")
It is also assumed that you have previously installed Samba in your system (you specifically need smbfs installed)

1. Configure your windows client to share printer and folders
Open your No Machine client and click on the configure button, go to the services tab and tick the share printer and folders field. click on the add button and you will see a listing of printers and folders that you have previously shared in your windows XP PC. Select the printer that you want to use to print locally and click OK.

2. Install the Linux driver for your local printer
Yes, you need to install the linux driver for the printer that the windows XP client needs for local printing, this may sound a bit ackward but it is absolutely required. Check first if you already have the driver required in your Ubuntu freenx server, if you do not know how to do that just try to install a new printer in System->Administration->Printers and advance until you are asked for a make and model of the printer. If your specific printer is there you do not need to do anything else and you can proceed to step 3. If you did not find your specific driver, do not panic, go to [http://www.linuxprinting.org]("http://www.linuxprinting.org") and click on the driver listing. Find your driver and follow the instructions for installation in your Ubuntu server.

3. Fix the nxnode.conf file

Open a terminal and type the following:

```
gksudo nautilus
```

drill down to ->usr->lib->nx, right click on nxnode.conf and open with gedit (text editor). click on file and save as oldnxnode.conf or any other name of your choosing. This will just be a back up of your original file just in case you need it. go to lines 800, 803 and 833 and delete the option "-noautokill" in each one of those sentences.

Go again to file and save as nxnode.conf, close gedit, right click on nxnode.conf and click on properties, tick execute for user, group and others.

4. Open cups ports
This is the one needing refinement. cups read by default port 631 only. Your freenx sessions use ports 10000 and on. For gnome to listen to these ports and automatically configure your shared windows printer you need to open these ports. using nautilus browse to /etc/cups/cupsd.conf, open it with gedit and enter the following code around line 450 and include one line per port as follows:

```
Port 10000
Port 10001
Port 10002
Port 10003
```

etc.

Since I was planning to have a maximum of 4 different sessions I did not include more ports to be opened. However this is not a good solution, one port should be dynamically opened for every session in order to limit exposure. I am sure that somebody from the Ubuntu community will come up with a smart solution to refine this setting.

5. set setuid for smbmnt and smbumount
Using your gksudo nautilus session opened in step 3, drill down to /usr/bin/smbmnt and smbumount in the same path. Right click on each of both files and click on properties, choose the access tab and tick the setuid box. close the properties windows

6. Reset your cups and samba service
I just go to system->services and untick and tick the cups and samba services, this will force the cups service to read cupsd.conf and the samba access settings again.

You are done, your printer should be now set and it will show up when you select print from any application running in your Ubuntu Freenx server and being accessed from a No Machine windows client. When the newly windows printer is selected, the output will be forwarded automatically to this printer.

Hope this helps.

Regards

Ramiro

---

### Post by sles on 2008-09-03
Hello!

As I see cups is started on server side -
27521 ?        Ss     0:00 /usr/sbin/cupsd -c /home/samba/misc/home/dm/.nx/C-cmterm-1000-5D39F9A1310AC8E32622C5B60D4531F0/cups/cupsd.conf

but I didn't understand trick with driver installation- how FreeNX found which driver use for printer?

---

### Post by Cheba on 2009-09-21
Hi.
 I have a problem printing from WinXP client.

os server: Linux Debian Lenny
FreeNX: 0.7.3
Cups 1.3.8

The problem is that the printer does not appear in gnome.

cat /home/cheba/.nx/C-mynxbox-1000-726A7957CA51927CD3B0C5E505488C9E/cups/error_log 

I [21/Sep/2009:21:23:30 -0300] Listening to /home/cheba/.nx/C-mynxbox-1000-726A7957CA51927CD3B0C5E505488C9E/cups/cups.sock (Domain)
I [21/Sep/2009:21:23:30 -0300] Loaded configuration file "/home/cheba/.nx/C-saas-mza-001-1000-726A7957CA51927CD3B0C5E505488C9E/cups/cupsd.conf"
I [21/Sep/2009:21:23:30 -0300] Configured for up to 100 clients.
I [21/Sep/2009:21:23:30 -0300] Allowing up to 100 client connections per host.
I [21/Sep/2009:21:23:30 -0300] Using policy "default" as the default!
I [21/Sep/2009:21:23:30 -0300] Full reload is required.
I [21/Sep/2009:21:23:30 -0300] Loaded MIME database from '/home/cheba/.nx/C-mynxbox-1000-726A7957CA51927CD3B0C5E505488C9E/cups/': 35 types, 38 filters...
I [21/Sep/2009:21:23:30 -0300] Full reload complete.
I [21/Sep/2009:21:23:30 -0300] Cleaning out old temporary files in "/home/cheba/.nx/C-saas-mza-001-1000-726A7957CA51927CD3B0C5E505488C9E/cups/spool/tmp"...
I [21/Sep/2009:21:23:30 -0300] Listening to /home/cheba/.nx/C-mynxbox-1000-726A7957CA51927CD3B0C5E505488C9E/cups/cups.sock on fd 3...
I [21/Sep/2009:21:23:30 -0300] Resuming new connection processing...
I [21/Sep/2009:21:23:36 -0300] Setting HPLaserJ printer-is-accepting-jobs to 1 (was 0.)
I [21/Sep/2009:21:23:36 -0300] Setting HPLaserJ printer-state to 3 (was 5.)
I [21/Sep/2009:21:23:36 -0300] Saving printers.conf...
I [21/Sep/2009:21:23:36 -0300] New printer "HPLaserJ" added by "anonymous".
I [21/Sep/2009:21:23:36 -0300] Setting HPLaserJ device-uri to "smb://127.0.0.1:4000/HPLaserJ" (was "file:/dev/null".)
I [21/Sep/2009:21:23:36 -0300] Saving printers.conf...
I [21/Sep/2009:21:23:36 -0300] Printer "HPLaserJ" modified by "anonymous".
I [21/Sep/2009:21:23:36 -0300] Saving printers.conf...
I [21/Sep/2009:21:23:36 -0300] Printer "HPLaserJ" modified by "anonymous".
I [21/Sep/2009:21:23:36 -0300] Saving printers.conf...
I [21/Sep/2009:21:23:36 -0300] Saving classes.conf...
I [21/Sep/2009:21:23:36 -0300] Default destination set to "HPLaserJ" by "anonymous".

cat /var/log/cups/access_log

localhost - - [21/Sep/2009:20:44:07 -0300] "POST / HTTP/1.1" 200 179 Get-Jobs successful-ok
localhost - - [21/Sep/2009:21:17:33 -0300] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes client-error-not-found
localhost - - [21/Sep/2009:21:17:33 -0300] "POST / HTTP/1.1" 200 129 CUPS-Get-Classes client-error-not-found
localhost - - [21/Sep/2009:21:23:38 -0300] "POST / HTTP/1.1" 200 179 Get-Jobs successful-ok
localhost - - [21/Sep/2009:21:23:55 -0300] "POST / HTTP/1.1" 200 417 CUPS-Get-Classes client-error-not-found
localhost - - [21/Sep/2009:21:23:58 -0300] "POST / HTTP/1.1" 200 417 CUPS-Get-Classes client-error-not-found
localhost - - [21/Sep/2009:21:23:58 -0300] "POST / HTTP/1.1" 200 417 CUPS-Get-Classes client-error-not

cat /var/log/cups/error_log

cupsdAcceptClient: 29 from localhost (Domain)
D [21/Sep/2009:21:23:38 -0300] Report: clients=1
D [21/Sep/2009:21:23:38 -0300] Report: jobs=0
D [21/Sep/2009:21:23:38 -0300] Report: jobs-active=0
D [21/Sep/2009:21:23:38 -0300] Report: printers=0
D [21/Sep/2009:21:23:38 -0300] Report: printers-implicit=0
D [21/Sep/2009:21:23:38 -0300] Report: stringpool-string-count=172
D [21/Sep/2009:21:23:38 -0300] Report: stringpool-alloc-bytes=6368
D [21/Sep/2009:21:23:38 -0300] Report: stringpool-total-bytes=3768
D [21/Sep/2009:21:23:38 -0300] cupsdReadClient: 29 POST / HTTP/1.1
D [21/Sep/2009:21:23:38 -0300] cupsdAuthorize: No authentication data provided.
D [21/Sep/2009:21:23:38 -0300] Get-Jobs ipp://localhost/jobs/
D [21/Sep/2009:21:23:38 -0300] cupsdProcessIPPRequest: 29 status_code=0 (successful-ok)
D [21/Sep/2009:21:23:38 -0300] cupsdCloseClient: 29
D [21/Sep/2009:21:23:55 -0300] cupsdAcceptClient: 29 from localhost (Domain)
D [21/Sep/2009:21:23:55 -0300] cupsdReadClient: 29 POST / HTTP/1.1
D [21/Sep/2009:21:23:55 -0300] cupsdAuthorize: No authentication data provided.
D [21/Sep/2009:21:23:55 -0300] CUPS-Get-Printers
D [21/Sep/2009:21:23:55 -0300] CUPS-Get-Printers client-error-not-found: No destinations added.
D [21/Sep/2009:21:23:55 -0300] cupsdProcessIPPRequest: 29 status_code=406 (client-error-not-found)
D [21/Sep/2009:21:23:55 -0300] cupsdReadClient: 29 POST / HTTP/1.1
D [21/Sep/2009:21:23:55 -0300] cupsdAuthorize: No authentication data provided.
D [21/Sep/2009:21:23:55 -0300] CUPS-Get-Classes
D [21/Sep/2009:21:23:55 -0300] CUPS-Get-Classes client-error-not-found: No destinations added.
D [21/Sep/2009:21:23:55 -0300] cupsdProcessIPPRequest: 29 status_code=406 (client-error-not-found)
D [21/Sep/2009:21:23:55 -0300] cupsdReadClient: 29 POST / HTTP/1.1
D [21/Sep/2009:21:23:55 -0300] cupsdAuthorize: No authentication data provided.
D [21/Sep/2009:21:23:55 -0300] CUPS-Get-Default
D [21/Sep/2009:21:23:55 -0300] CUPS-Get-Default client-error-not-found: No default printer
D [21/Sep/2009:21:23:55 -0300] cupsdProcessIPPRequest: 29 status_code=406 (client-error-not-found)
D [21/Sep/2009:21:23:55 -0300] cupsdCloseClient: 29
D [21/Sep/2009:21:23:58 -0300] cupsdAcceptClient: 29 from localhost (Domain)
D [21/Sep/2009:21:23:58 -0300] cupsdReadClient: 29 POST / HTTP/1.1
D [21/Sep/2009:21:23:58 -0300] cupsdAuthorize: No authentication data provided.
D [21/Sep/2009:21:23:58 -0300] CUPS-Get-Printers
D [21/Sep/2009:21:23:58 -0300] CUPS-Get-Printers client-error-not-found: No destinations added.
D [21/Sep/2009:21:23:58 -0300] cupsdProcessIPPRequest: 29 status_code=406 (client-error-not-found)
D [21/Sep/2009:21:23:58 -0300] cupsdReadClient: 29 POST / HTTP/1.1
D [21/Sep/2009:21:23:58 -0300] cupsdAuthorize: No authentication data provided.
D [21/Sep/2009:21:23:58 -0300] CUPS-Get-Classes
D [21/Sep/2009:21:23:58 -0300] CUPS-Get-Classes client-error-not-found: No destinations added.
D [21/Sep/2009:21:23:58 -0300] cupsdProcessIPPRequest: 29 status_code=406 (client-error-not-found)
D [21/Sep/2009:21:23:58 -0300] cupsdReadClient: 29 POST / HTTP/1.1
D [21/Sep/2009:21:23:58 -0300] cupsdAuthorize: No authentication data provided.
D [21/Sep/2009:21:23:58 -0300] CUPS-Get-Default
D [21/Sep/2009:21:23:58 -0300] CUPS-Get-Default client-error-not-found: No default printer
D [21/Sep/2009:21:23:58 -0300] cupsdProcessIPPRequest: 29 status_code=406 (client-error-not-found)
D [21/Sep/2009:21:23:58 -0300] cupsdCloseClient: 29
D [21/Sep/2009:21:23:58 -0300] cupsdAcceptClient: 29 from localhost (Domain)
D [21/Sep/2009:21:23:58 -0300] cupsdReadClient: 29 POST / HTTP/1.1
D [21/Sep/2009:21:23:58 -0300] cupsdAuthorize: No authentication data provided.
D [21/Sep/2009:21:23:58 -0300] CUPS-Get-Printers
D [21/Sep/2009:21:23:58 -0300] CUPS-Get-Printers client-error-not-found: No destinations added.
D [21/Sep/2009:21:23:58 -0300] cupsdProcessIPPRequest: 29 status_code=406 (client-error-not-found)
D [21/Sep/2009:21:23:58 -0300] cupsdReadClient: 29 POST / HTTP/1.1
D [21/Sep/2009:21:23:58 -0300] cupsdAuthorize: No authentication data provided.
D [21/Sep/2009:21:23:58 -0300] CUPS-Get-Classes
D [21/Sep/2009:21:23:58 -0300] CUPS-Get-Classes client-error-not-found: No destinations added.
D [21/Sep/2009:21:23:58 -0300] cupsdProcessIPPRequest: 29 status_code=406 (client-error-not-found)
D [21/Sep/2009:21:23:58 -0300] cupsdReadClient: 29 POST / HTTP/1.1
D [21/Sep/2009:21:23:58 -0300] cupsdAuthorize: No authentication data provided.
D [21/Sep/2009:21:23:58 -0300] CUPS-Get-Default
D [21/Sep/2009:21:23:58 -0300] CUPS-Get-Default client-error-not-found: No default printer
D [21/Sep/2009:21:23:58 -0300] cupsdProcessIPPRequest: 29 status_code=406 (client-error-not-found)
D [21/Sep/2009:21:23:58 -0300] cupsdCloseClient: 29


ps -aux | grep cup

Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
root      2524  0.0  0.2  72652  2428 ?        Ss   21:17   0:00 /usr/sbin/cupsd
cheba     4343  0.0  0.2  74172  2872 ?        Ss   21:23   0:00 /usr/sbin/cupsd -c /home/cheba/.nx/C-mynxbox-1000-726A7957CA51927CD3B0C5E505488C9E/cups/cupsd.conf

I need nxcupsd-wrapper?

Thanks!!!, and sorry for my bad english..

---

