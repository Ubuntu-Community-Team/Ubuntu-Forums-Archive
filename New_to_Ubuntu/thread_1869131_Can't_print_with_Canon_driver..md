---
title: "Can't print with Canon driver."
date: 2011-10-25
forum: New to Ubuntu
---

### Post by 2CV67 on 2011-10-25
For several years, I used my Canon iP4300 with drivers from Canon Australia & Canon Europe (cnijfilter-common_2.70-2_i386.deb & cnijfilter-ip4300_2.70-3_i386.deb etc).

According to SynApt, I have the latest versions currently installed.
Somewhere around the upgrade to 11.04 this driver stopped working, but as I could continue with Cups/Gutenprint, I forgot about the Canon driver.

Recently, in reinstalling the printer via localhost631, I found the prefered driver was now OEM Canon Ver.2.70 so I tried it again.

An interesting feature is it now offers printing at 600/1200/2400/4800dpi whereas Gutenprint sticks at 600dpi max.

Unfortunately, I can't get the printer to work with the latest Canon driver.
Trying to Print a Test Page sees the job appear briefly in the job list, then disappear with no trace & no reaction from the printer.
Doing the same from the browser in localhost631 produces the same result, & the job appears as "completed".
No error messages anywhere, as far as I know.

Anybody have any idea where to start looking?

Thanks!

---

### Post by jnorthr on 2011-10-25
think i would try looking into the system log messages immediately after doing a print. you can reach these msgs from a terminal console window (think it's menu>accessories>terminal) using the command dmesg
this should display / may show if there are any internal system errors detecged by the kernal while doing i/o to the printer. Is it possible to do a screen print or perhaps try printing anything from gedit or libreoffice ? 

would also see if this is a permissions issue. some drivers may have been installed by 'user' rather than 'root' owner which might give the driver a lower level of authority than it needs to do it's job. Where to look ? Guess we would need to find out which folder contains your driver. Do you know ?

---

### Post by 2CV67 on 2011-10-25
Thanks VERY much for your interest!

This is output from dmesg, covering:
Turn on printer
Turn off printer
Turn on printer

```
[ 1658.808259] usb 1-2.4: new high speed USB device using ehci_hcd and address 6
[ 1660.945988] usblp0: USB Bidirectional printer dev 6 if 0 alt 0 proto 2 vid 0x04A9 pid 0x10B6
[ 1660.946284] usbcore: registered new interface driver usblp
[ 1662.016184] usb 1-2.4: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[ 2096.584546] usb 1-2.4: USB disconnect, address 6
[ 2096.584771] usblp0: removed
[ 2215.040296] usb 1-2.4: new high speed USB device using ehci_hcd and address 7
[ 2215.136923] usblp0: USB Bidirectional printer dev 7 if 0 alt 0 proto 2 vid 0x04A9 pid 0x10B6
[ 2216.543898] usb 1-2.4: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
```

In between, I tried "Print Test Page" several times from inside "Printing > Properties" but that did not change the message log at all.

I don't yet know which folder contains the driver.
I will post back when I find it...

Thanks again!

---

### Post by jnorthr on 2011-10-25
just checked your blog - Parting thot: "Language is the source of misunderstandings." - Antoine de Saint-Exupery 
which applies to programming languages as well, but for everyday use, i prefer the vulcan mind-meld so as to avoid misunderstandings :)

ok, thanx for that dmesg, we can now rule out the permissions issue as we can see that the kernel does indeed recognize and even assigns an address to your printer as lp0 and since it's a usb printer we get usblp0
let me just google this for a mo......

see your prev. discussion here: [http://ubuntuforums.org/showthread.php?p=11386838](http://ubuntuforums.org/showthread.php?p=11386838) 
did this not work as you expected ?

also did you see this guide on ip4300 printers ? [http://www.erlandertervueren.com/ubuntu/ip4300_guide/](http://www.erlandertervueren.com/ubuntu/ip4300_guide/)

---

### Post by 2CV67 on 2011-10-26
> **jnorthr said:**
> 
see your prev. discussion here: [http://ubuntuforums.org/showthread.php?p=11386838](http://ubuntuforums.org/showthread.php?p=11386838) 
did this not work as you expected ?
Yes - that was getting the same physical printer to work with Cups/Gutenprint driver from remote netbook over wifi network.

Todays problem is getting the printer to work with Canon driver directly from desktop PC via USB cable.

Tomorrows problem may be getting the printer to work with Canon driver from netbook over wifi - but that can wait!
> also did you see this guide on ip4300 printers ? [http://www.erlandertervueren.com/ubuntu/ip4300_guide/](http://www.erlandertervueren.com/ubuntu/ip4300_guide/)
Yes, thanks!
Also my own previous thread:
[http://ubuntuforums.org/showthread.php?t=892340](http://ubuntuforums.org/showthread.php?t=892340)

But both are now rather out of date & anyway I don't really want to re-install everything from scratch (especially with outdated instructions).
I would like to be able to troubleshoot what is probably a small problem somewhere.

---

### Post by jnorthr on 2011-10-26
ok, so i'm looking for clues of other people's issues with ip4300 printers. Found this: [https://wiki.archlinux.org/index.php/Canon_iP4300](https://wiki.archlinux.org/index.php/Canon_iP4300) which sounds a bit drastic to 1)start cups 2)remove current printer 3)re-install printer with gutenprint. This sounds similar to what you've done. 
Now i think we've eliminated the possible problems due to permissions, and it does sound like you have had this printer working before, so assume the printer itself is in good order.

So i'm thinking is this could be an issue with the fonts for your printer not being found from your PC. So, with your printer attached and turned on,  we can check your known usb devices with 
sudo lsusb
from terminal. see here: [http://manpages.ubuntu.com/manpages/hardy/man8/lsusb.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/lsusb.8.html)  for further details. This will not tell us about missing fonts etc. I would expect dmesg list would show us that if it were the case.

Do you have ghostscript installed ? Think this is needed to print PDF documents, which you might/or not need.

Also i'm reading this: [http://www.cups.org/doc-1.1/sum.html](http://www.cups.org/doc-1.1/sum.html)  to see how we can suss which fonts you have on your PC - ubuntu 11.04 was it ?

---

### Post by mosaic2s on 2011-10-26
i used canon ix4000 earlier thru network and now using canon lbp1210 using capt drivers.
At all occasions, 10.04 and previously 8.04 worked effortlessly while other in between but latest created issues.
Stick to LTS versions if you want to print and use network and other hardware.

---

### Post by 2CV67 on 2011-10-26
> **jnorthr said:**
> Found this: [https://wiki.archlinux.org/index.php/Canon_iP4300](https://wiki.archlinux.org/index.php/Canon_iP4300) which sounds a bit drastic to 1)start cups 2)remove current printer 3)re-install printer with gutenprint. This sounds similar to what you've done. Thanks very much for your continuing interest!

As you say, I have had the printer working with Canon driver previously & it now works OK with Gutenprint.
It also works OK with Canon driver in XP on the same PC.
*Edit: It works much, much better in XP than it has ever worked in Ubuntu - including silent mode & ink-level indicator which pops up automatically when ink starts to get low. End edit*
> Now i think we've eliminated the possible problems due to permissions, and it does sound like you have had this printer working before, so assume the printer itself is in good order.
I believe so - see above.
> So i'm thinking is this could be an issue with the fonts for your printer not being found from your PC. So, with your printer attached and turned on,  we can check your known usb devices with 
sudo lsusb
Here is the output from sudo lsusb:
~$ sudo lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1019:0c55 Elitegroup Computer Systems (ECS) Flash Reader, Desknote UCR-61S2B
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 04a9:10b6 Canon, Inc. PIXMA iP4300 Printer
Bus 001 Device 005: ID 045e:0029 Microsoft Corp. IntelliMouse Optical
Bus 001 Device 004: ID 152d:2339 JMicron Technology Corp. / JMicron USA Technology Corp. 
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
> Do you have ghostscript installed ? Think this is needed to print PDF documents, which you might/or not need.
I do have ghostscript installed - 9.01~dfsg-1ubuntu5
I would need to print pdf, but that is not the current concern.
Printing a test page would be a good start...
Or getting an error message when it fails to print!
> Also i'm reading this: [http://www.cups.org/doc-1.1/sum.html](http://www.cups.org/doc-1.1/sum.html)  to see how we can suss which fonts you have on your PC - ubuntu 11.04 was it ?
Yes - the main PC is running 11.04.

---

### Post by 2CV67 on 2011-10-26
Ah!...

I found this, which includes debuggung methods:
[https://wiki.ubuntu.com/DebuggingPrintingProblems](https://wiki.ubuntu.com/DebuggingPrintingProblems)

So I went to Printing > Server > Settings & checked the box for "Save debugging information for troubleshooting".
Then tried to Print a Test Page.
Then looked in /var/log/cups/error_log

Very long output, below, which I can't follow yet, but probably contains vital clues for anybody sufficiently clued-up?
```
E [26/Oct/2011:10:28:16 +0200] Failed to update TXT record for Canon iP4300via631 @ DESKTOP: -2
E [26/Oct/2011:10:28:16 +0200] Failed to update TXT record for iP43003cups @ DESKTOP: -2
E [26/Oct/2011:13:15:39 +0200] Failed to update TXT record for Canon iP4300via631 @ DESKTOP: -2
E [26/Oct/2011:13:15:39 +0200] Failed to update TXT record for iP43003cups @ DESKTOP: -2
I [26/Oct/2011:14:02:53 +0200] Listening to 0.0.0.0:631 (IPv4)
I [26/Oct/2011:14:02:53 +0200] Listening to [v1.::]:631 (IPv6)
I [26/Oct/2011:14:02:53 +0200] Listening to /var/run/cups/cups.sock (Domain)
I [26/Oct/2011:14:02:53 +0200] Remote access is enabled.
D [26/Oct/2011:14:02:53 +0200] Added auto ServerAlias DESKTOP
I [26/Oct/2011:14:02:53 +0200] Loaded configuration file "/etc/cups/cupsd.conf"
I [26/Oct/2011:14:02:53 +0200] Using default TempDir of /var/spool/cups/tmp...
I [26/Oct/2011:14:02:53 +0200] Configured for up to 100 clients.
I [26/Oct/2011:14:02:53 +0200] Allowing up to 100 client connections per host.
I [26/Oct/2011:14:02:53 +0200] Using policy "default" as the default!
D [26/Oct/2011:14:02:53 +0200] load_ppd: Loading /var/cache/cups/Canon_iP43004.ipp4...
D [26/Oct/2011:14:02:53 +0200] cupsdRegisterPrinter(p=0x21781f80(Canon_iP43004))
D [26/Oct/2011:14:02:53 +0200] Registering Avahi printer Canon_iP43004 with name "Canon iP4300via631 @ DESKTOP" and type "_ipp._tcp"
D [26/Oct/2011:14:02:53 +0200] load_ppd: Loading /var/cache/cups/iP43003cups.ipp4...
D [26/Oct/2011:14:02:53 +0200] cupsdRegisterPrinter(p=0x21786bd0(iP43003cups))
D [26/Oct/2011:14:02:53 +0200] Registering Avahi printer iP43003cups with name "iP43003cups @ DESKTOP" and type "_ipp._tcp"
D [26/Oct/2011:14:02:53 +0200] cupsdMarkDirty(---p--)
D [26/Oct/2011:14:02:53 +0200] cupsdSetBusyState: Dirty files
I [26/Oct/2011:14:02:53 +0200] Partial reload complete.
I [26/Oct/2011:14:02:53 +0200] Listening to 0.0.0.0:631 on fd 5...
I [26/Oct/2011:14:02:53 +0200] Listening to [v1.::]:631 on fd 7...
I [26/Oct/2011:14:02:53 +0200] Listening to /var/run/cups/cups.sock on fd 8...
I [26/Oct/2011:14:02:53 +0200] Resuming new connection processing...
D [26/Oct/2011:14:02:53 +0200] cupsdRegisterPrinter(p=0x21781f80(Canon_iP43004))
E [26/Oct/2011:14:02:53 +0200] Failed to update TXT record for Canon iP4300via631 @ DESKTOP: -2
D [26/Oct/2011:14:02:53 +0200] Registering Avahi printer Canon_iP43004 with name "Canon iP4300via631 @ DESKTOP" and type "_ipp._tcp"
D [26/Oct/2011:14:02:53 +0200] cupsdRegisterPrinter(p=0x21786bd0(iP43003cups))
E [26/Oct/2011:14:02:53 +0200] Failed to update TXT record for iP43003cups @ DESKTOP: -2
D [26/Oct/2011:14:02:53 +0200] Registering Avahi printer iP43003cups with name "iP43003cups @ DESKTOP" and type "_ipp._tcp"
D [26/Oct/2011:14:02:53 +0200] Discarding unused server-restarted event...
D [26/Oct/2011:14:02:54 +0200] cupsdAcceptClient: 13 from localhost (Domain)
D [26/Oct/2011:14:02:54 +0200] Report: clients=1
D [26/Oct/2011:14:02:54 +0200] Report: jobs=20
D [26/Oct/2011:14:02:54 +0200] Report: jobs-active=0
D [26/Oct/2011:14:02:54 +0200] Report: printers=2
D [26/Oct/2011:14:02:54 +0200] Report: printers-implicit=0
D [26/Oct/2011:14:02:54 +0200] Report: stringpool-string-count=72251
D [26/Oct/2011:14:02:54 +0200] Report: stringpool-alloc-bytes=14376
D [26/Oct/2011:14:02:54 +0200] Report: stringpool-total-bytes=1338552
D [26/Oct/2011:14:02:56 +0200] cupsdNetIFUpdate: "lo" = localhost:631
D [26/Oct/2011:14:02:56 +0200] cupsdNetIFUpdate: "wlan0" = 192.168.1.2:631
D [26/Oct/2011:14:02:56 +0200] cupsdNetIFUpdate: "lo" = localhost:631
D [26/Oct/2011:14:02:56 +0200] cupsdNetIFUpdate: "wlan0" = [v1.fe80::21f:1fff:fe05:e56e+wlan0]:631
D [26/Oct/2011:14:03:00 +0200] Avahi entry group established for Canon iP4300via631 @ DESKTOP
D [26/Oct/2011:14:03:01 +0200] Avahi entry group established for iP43003cups @ DESKTOP
D [26/Oct/2011:14:03:23 +0200] cupsdAcceptClient: 14 from localhost (Domain)
I [26/Oct/2011:14:03:23 +0200] Generating printcap /var/run/cups/printcap...
D [26/Oct/2011:14:03:23 +0200] cupsdSetBusyState: Not busy
D [26/Oct/2011:14:03:23 +0200] cupsdReadClient: 14 POST / HTTP/1.1
D [26/Oct/2011:14:03:23 +0200] cupsdSetBusyState: Active clients
D [26/Oct/2011:14:03:23 +0200] cupsdAuthorize: No authentication data provided.
D [26/Oct/2011:14:03:23 +0200] cupsdReadClient: 14 1.1 Get-Printer-Attributes 1
D [26/Oct/2011:14:03:23 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon_iP43004
D [26/Oct/2011:14:03:23 +0200] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Canon_iP43004) from localhost
D [26/Oct/2011:14:03:23 +0200] cupsdSetBusyState: Not busy
D [26/Oct/2011:14:03:26 +0200] cupsdAcceptClient: 15 from localhost (Domain)
D [26/Oct/2011:14:03:26 +0200] cupsdReadClient: 15 POST /printers/Canon_iP43004 HTTP/1.1
D [26/Oct/2011:14:03:26 +0200] cupsdSetBusyState: Active clients
D [26/Oct/2011:14:03:26 +0200] cupsdAuthorize: No authentication data provided.
D [26/Oct/2011:14:03:26 +0200] cupsdReadClient: 15 1.1 Print-Job 1
D [26/Oct/2011:14:03:26 +0200] Print-Job ipp://localhost/printers/Canon_iP43004
D [26/Oct/2011:14:03:26 +0200] [Job ???] Auto-typing file...
I [26/Oct/2011:14:03:26 +0200] [Job ???] Request file type is application/postscript.
D [26/Oct/2011:14:03:26 +0200] cupsdMarkDirty(----J-)
D [26/Oct/2011:14:03:26 +0200] cupsdSetBusyState: Active clients and dirty files
D [26/Oct/2011:14:03:26 +0200] add_job: requesting-user-name="chris"
D [26/Oct/2011:14:03:26 +0200] Adding default job-sheets values "none,none"...
I [26/Oct/2011:14:03:26 +0200] [Job 30] Adding start banner page "none".
D [26/Oct/2011:14:03:26 +0200] cupsdMarkDirty(-----S)
D [26/Oct/2011:14:03:26 +0200] cupsdMarkDirty(----J-)
I [26/Oct/2011:14:03:26 +0200] [Job 30] Adding end banner page "none".
I [26/Oct/2011:14:03:26 +0200] [Job 30] File of type application/postscript queued by "chris".
D [26/Oct/2011:14:03:26 +0200] [Job 30] hold_until=0
I [26/Oct/2011:14:03:26 +0200] [Job 30] Queued on "Canon_iP43004" by "chris".
D [26/Oct/2011:14:03:26 +0200] cupsdMarkDirty(----J-)
D [26/Oct/2011:14:03:26 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [26/Oct/2011:14:03:26 +0200] cupsdMarkDirty(-----S)
D [26/Oct/2011:14:03:26 +0200] [Job 30] job-sheets=none,none
D [26/Oct/2011:14:03:26 +0200] [Job 30] argv[0]="Canon_iP43004"
D [26/Oct/2011:14:03:26 +0200] [Job 30] argv[1]="30"
D [26/Oct/2011:14:03:26 +0200] [Job 30] argv[2]="chris"
D [26/Oct/2011:14:03:26 +0200] [Job 30] argv[3]="Test Page"
D [26/Oct/2011:14:03:26 +0200] [Job 30] argv[4]="1"
D [26/Oct/2011:14:03:26 +0200] [Job 30] argv[5]="PageSize=A4 job-uuid=urn:uuid:7b008bc6-21c9-33bb-7223-87eda28f1d77 job-originating-host-name=localhost time-at-creation=1319630606 time-at-processing=1319630606 AP_D_InputSlot="
D [26/Oct/2011:14:03:26 +0200] [Job 30] argv[6]="/var/spool/cups/d00030-001"
D [26/Oct/2011:14:03:26 +0200] [Job 30] envp[0]="CUPS_CACHEDIR=/var/cache/cups"
D [26/Oct/2011:14:03:26 +0200] [Job 30] envp[1]="CUPS_DATADIR=/usr/share/cups"
D [26/Oct/2011:14:03:26 +0200] [Job 30] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
D [26/Oct/2011:14:03:26 +0200] [Job 30] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
D [26/Oct/2011:14:03:26 +0200] [Job 30] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
D [26/Oct/2011:14:03:26 +0200] [Job 30] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
D [26/Oct/2011:14:03:26 +0200] [Job 30] envp[6]="CUPS_SERVERROOT=/etc/cups"
D [26/Oct/2011:14:03:26 +0200] [Job 30] envp[7]="CUPS_STATEDIR=/var/run/cups"
D [26/Oct/2011:14:03:26 +0200] [Job 30] envp[8]="HOME=/var/spool/cups/tmp"
D [26/Oct/2011:14:03:26 +0200] [Job 30] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
D [26/Oct/2011:14:03:26 +0200] [Job 30] envp[10]="SERVER_ADMIN=root@DESKTOP"
D [26/Oct/2011:14:03:26 +0200] [Job 30] envp[11]="SOFTWARE=CUPS/1.4.6"
D [26/Oct/2011:14:03:26 +0200] [Job 30] envp[12]="TMPDIR=/var/spool/cups/tmp"
D [26/Oct/2011:14:03:26 +0200] [Job 30] envp[13]="USER=root"
D [26/Oct/2011:14:03:26 +0200] [Job 30] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
D [26/Oct/2011:14:03:26 +0200] [Job 30] envp[15]="CUPS_ENCRYPTION=IfRequested"
D [26/Oct/2011:14:03:26 +0200] [Job 30] envp[16]="IPP_PORT=631"
D [26/Oct/2011:14:03:26 +0200] [Job 30] envp[17]="CHARSET=utf-8"
D [26/Oct/2011:14:03:26 +0200] [Job 30] envp[18]="LANG=en_IE.UTF-8"
D [26/Oct/2011:14:03:26 +0200] [Job 30] envp[19]="PPD=/etc/cups/ppd/Canon_iP43004.ppd"
D [26/Oct/2011:14:03:26 +0200] [Job 30] envp[20]="RIP_MAX_CACHE=auto"
D [26/Oct/2011:14:03:26 +0200] [Job 30] envp[21]="CONTENT_TYPE=application/postscript"
D [26/Oct/2011:14:03:26 +0200] [Job 30] envp[22]="DEVICE_URI=usb://Canon/iP4300"
D [26/Oct/2011:14:03:26 +0200] [Job 30] envp[23]="PRINTER_INFO=Canon iP4300via631"
D [26/Oct/2011:14:03:26 +0200] [Job 30] envp[24]="PRINTER_LOCATION="
D [26/Oct/2011:14:03:26 +0200] [Job 30] envp[25]="PRINTER=Canon_iP43004"
D [26/Oct/2011:14:03:26 +0200] [Job 30] envp[26]="CUPS_FILETYPE=document"
D [26/Oct/2011:14:03:26 +0200] [Job 30] envp[27]="FINAL_CONTENT_TYPE=printer/Canon_iP43004"
I [26/Oct/2011:14:03:26 +0200] [Job 30] Started filter /usr/lib/cups/filter/pstops (PID 2142)
I [26/Oct/2011:14:03:26 +0200] [Job 30] Started filter /usr/lib/cups/filter/pstocanonij (PID 2143)
I [26/Oct/2011:14:03:26 +0200] [Job 30] Started backend /usr/lib/cups/backend/usb (PID 2144)
D [26/Oct/2011:14:03:26 +0200] cupsdMarkDirty(-----S)
D [26/Oct/2011:14:03:26 +0200] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/Canon_iP43004) from localhost
D [26/Oct/2011:14:03:26 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [26/Oct/2011:14:03:26 +0200] [Job 30] Page = 595x842; 10,14 to 586,833
D [26/Oct/2011:14:03:26 +0200] [Job 30] pstocanonij start.
D [26/Oct/2011:14:03:26 +0200] cupsdAcceptClient: 19 from localhost (Domain)
D [26/Oct/2011:14:03:26 +0200] cupsdReadClient: 19 POST / HTTP/1.1
D [26/Oct/2011:14:03:26 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [26/Oct/2011:14:03:26 +0200] cupsdAuthorize: No authentication data provided.
D [26/Oct/2011:14:03:26 +0200] cupsdReadClient: 19 1.1 Get-Jobs 1
D [26/Oct/2011:14:03:26 +0200] Get-Jobs ipp://localhost/printers/
D [26/Oct/2011:14:03:26 +0200] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [26/Oct/2011:14:03:26 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [26/Oct/2011:14:03:26 +0200] cupsdReadClient: 19 WAITING Closing on EOF
D [26/Oct/2011:14:03:26 +0200] cupsdCloseClient: 19
D [26/Oct/2011:14:03:26 +0200] [Job 30] STATE: +connecting-to-device
D [26/Oct/2011:14:03:26 +0200] cupsdMarkDirty(-----S)
D [26/Oct/2011:14:03:26 +0200] [Job 30] slow_collate=0, slow_duplex=0, slow_order=0
D [26/Oct/2011:14:03:26 +0200] [Job 30] Before copy_comments - %!PS-Adobe-3.0
D [26/Oct/2011:14:03:26 +0200] [Job 30] %!PS-Adobe-3.0
D [26/Oct/2011:14:03:26 +0200] [Job 30] %%Title: PPR Test Page
D [26/Oct/2011:14:03:26 +0200] [Job 30] %%Pages: 1
D [26/Oct/2011:14:03:26 +0200] [Job 30] %%BoundingBox: 0 0 595 842
D [26/Oct/2011:14:03:26 +0200] [Job 30] %%DocumentNeededResources: font Helvetica
D [26/Oct/2011:14:03:26 +0200] [Job 30] Printer using device file "/dev/usblp0"...
D [26/Oct/2011:14:03:26 +0200] [Job 30] STATE: -connecting-to-device
D [26/Oct/2011:14:03:26 +0200] cupsdMarkDirty(-----S)
D [26/Oct/2011:14:03:26 +0200] [Job 30] backendRunLoop(print_fd=0, device_fd=5, snmp_fd=-1, addr=(nil), use_bc=0, side_cb=0x65a230)
D [26/Oct/2011:14:03:26 +0200] [Job 30] %%EndComments
D [26/Oct/2011:14:03:26 +0200] [Job 30] Before copy_prolog - %%BeginProlog
D [26/Oct/2011:14:03:26 +0200] [Job 30] Before copy_setup - %%BeginSetup
D [26/Oct/2011:14:03:26 +0200] [Job 30] Before page loop - %%Page: 1 1
D [26/Oct/2011:14:03:26 +0200] [Job 30] Copying page 1...
D [26/Oct/2011:14:03:26 +0200] [Job 30] pagew = 576.0, pagel = 819.2
D [26/Oct/2011:14:03:26 +0200] [Job 30] bboxx = 0, bboxy = 0, bboxw = 595, bboxl = 842
D [26/Oct/2011:14:03:26 +0200] [Job 30] PageLeft = 9.6, PageRight = 585.6
D [26/Oct/2011:14:03:26 +0200] [Job 30] PageTop = 833.4, PageBottom = 14.2
D [26/Oct/2011:14:03:26 +0200] [Job 30] PageWidth = 595.0, PageLength = 842.0
D [26/Oct/2011:14:03:26 +0200] [Job 30] pstocanonij: /usr/bin/gs -r600 -g4958x7016 -q -dNOPROMPT -dSAFER -sDEVICE=ppmraw -sOutputFile=- -| /usr/local/bin/cifip4300 --imageres 600 --papersize a4 --media plain --quality 3 --bbox 9,14,585,834 
D [26/Oct/2011:14:03:26 +0200] [Job 30] Wrote 1 pages...
D [26/Oct/2011:14:03:26 +0200] PID 2142 (/usr/lib/cups/filter/pstops) exited with no errors.
D [26/Oct/2011:14:03:26 +0200] [Job 30] /usr/local/bin/cifip4300: error while loading shared libraries: libtiff.so.3: cannot open shared object file: No such file or directory
D [26/Oct/2011:14:03:26 +0200] cupsdAcceptClient: 19 from localhost (Domain)
D [26/Oct/2011:14:03:26 +0200] cupsdReadClient: 19 POST / HTTP/1.1
D [26/Oct/2011:14:03:26 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [26/Oct/2011:14:03:26 +0200] cupsdAuthorize: No authentication data provided.
D [26/Oct/2011:14:03:26 +0200] cupsdReadClient: 19 1.1 Get-Notifications 1
D [26/Oct/2011:14:03:26 +0200] Get-Notifications /
D [26/Oct/2011:14:03:26 +0200] cupsdIsAuthorized: requesting-user-name="chris"
D [26/Oct/2011:14:03:26 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [26/Oct/2011:14:03:26 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [26/Oct/2011:14:03:26 +0200] cupsdReadClient: 14 POST / HTTP/1.1
D [26/Oct/2011:14:03:26 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [26/Oct/2011:14:03:26 +0200] cupsdAuthorize: No authentication data provided.
D [26/Oct/2011:14:03:26 +0200] cupsdReadClient: 14 1.1 Get-Printer-Attributes 1
D [26/Oct/2011:14:03:26 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon_iP43004
D [26/Oct/2011:14:03:26 +0200] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Canon_iP43004) from localhost
D [26/Oct/2011:14:03:26 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [26/Oct/2011:14:03:26 +0200] cupsdAcceptClient: 20 from localhost (Domain)
D [26/Oct/2011:14:03:26 +0200] cupsdReadClient: 14 POST / HTTP/1.1
D [26/Oct/2011:14:03:26 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [26/Oct/2011:14:03:26 +0200] cupsdAuthorize: No authentication data provided.
D [26/Oct/2011:14:03:26 +0200] cupsdReadClient: 14 1.1 Get-Printer-Attributes 1
D [26/Oct/2011:14:03:26 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon_iP43004
D [26/Oct/2011:14:03:26 +0200] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Canon_iP43004) from localhost
D [26/Oct/2011:14:03:26 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [26/Oct/2011:14:03:26 +0200] cupsdReadClient: 14 POST / HTTP/1.1
D [26/Oct/2011:14:03:26 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [26/Oct/2011:14:03:26 +0200] cupsdAuthorize: No authentication data provided.
D [26/Oct/2011:14:03:26 +0200] cupsdReadClient: 14 1.1 Get-Printer-Attributes 1
D [26/Oct/2011:14:03:26 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon_iP43004
D [26/Oct/2011:14:03:26 +0200] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Canon_iP43004) from localhost
D [26/Oct/2011:14:03:26 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [26/Oct/2011:14:03:26 +0200] cupsdReadClient: 19 WAITING Closing on EOF
D [26/Oct/2011:14:03:26 +0200] cupsdCloseClient: 19
D [26/Oct/2011:14:03:26 +0200] cupsdAcceptClient: 19 from localhost (Domain)
D [26/Oct/2011:14:03:26 +0200] cupsdReadClient: 19 POST / HTTP/1.1
D [26/Oct/2011:14:03:26 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [26/Oct/2011:14:03:26 +0200] cupsdAuthorize: No authentication data provided.
D [26/Oct/2011:14:03:26 +0200] cupsdReadClient: 19 1.1 CUPS-Get-Printers 1
D [26/Oct/2011:14:03:26 +0200] CUPS-Get-Printers
D [26/Oct/2011:14:03:26 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [26/Oct/2011:14:03:26 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [26/Oct/2011:14:03:26 +0200] cupsdReadClient: 19 POST / HTTP/1.1
D [26/Oct/2011:14:03:26 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [26/Oct/2011:14:03:26 +0200] cupsdAuthorize: No authentication data provided.
D [26/Oct/2011:14:03:26 +0200] cupsdReadClient: 19 1.1 CUPS-Get-Classes 1
D [26/Oct/2011:14:03:26 +0200] CUPS-Get-Classes
D [26/Oct/2011:14:03:26 +0200] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [26/Oct/2011:14:03:26 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [26/Oct/2011:14:03:26 +0200] cupsdReadClient: 19 POST / HTTP/1.1
D [26/Oct/2011:14:03:26 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [26/Oct/2011:14:03:26 +0200] cupsdAuthorize: No authentication data provided.
D [26/Oct/2011:14:03:26 +0200] cupsdReadClient: 19 1.1 CUPS-Get-Default 1
D [26/Oct/2011:14:03:26 +0200] CUPS-Get-Default
D [26/Oct/2011:14:03:26 +0200] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [26/Oct/2011:14:03:26 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [26/Oct/2011:14:03:27 +0200] cupsdAcceptClient: 21 from localhost (Domain)
D [26/Oct/2011:14:03:27 +0200] cupsdAcceptClient: 22 from localhost (Domain)
D [26/Oct/2011:14:03:27 +0200] cupsdReadClient: 22 POST / HTTP/1.1
D [26/Oct/2011:14:03:27 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [26/Oct/2011:14:03:27 +0200] cupsdAuthorize: No authentication data provided.
D [26/Oct/2011:14:03:27 +0200] cupsdReadClient: 22 1.1 Create-Printer-Subscription 1
D [26/Oct/2011:14:03:27 +0200] Create-Printer-Subscription /
D [26/Oct/2011:14:03:27 +0200] cupsdCreateSubscription(con=0x21ad5120(22), uri="/")
D [26/Oct/2011:14:03:27 +0200] pullmethod="ippget"
D [26/Oct/2011:14:03:27 +0200] notify-lease-duration=86400
D [26/Oct/2011:14:03:27 +0200] notify-time-interval=0
D [26/Oct/2011:14:03:27 +0200] cupsdAddSubscription(mask=1798f, dest=(nil)(), job=(nil)(0), uri="(null)")
D [26/Oct/2011:14:03:27 +0200] Added subscription 306 for server
D [26/Oct/2011:14:03:27 +0200] cupsdMarkDirty(-----S)
D [26/Oct/2011:14:03:27 +0200] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost
D [26/Oct/2011:14:03:27 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [26/Oct/2011:14:03:27 +0200] cupsdReadClient: 22 POST / HTTP/1.1
D [26/Oct/2011:14:03:27 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [26/Oct/2011:14:03:27 +0200] cupsdAuthorize: No authentication data provided.
D [26/Oct/2011:14:03:27 +0200] cupsdReadClient: 22 1.1 CUPS-Get-Printers 1
D [26/Oct/2011:14:03:27 +0200] CUPS-Get-Printers
D [26/Oct/2011:14:03:27 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [26/Oct/2011:14:03:27 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [26/Oct/2011:14:03:27 +0200] cupsdReadClient: 22 POST / HTTP/1.1
D [26/Oct/2011:14:03:27 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [26/Oct/2011:14:03:27 +0200] cupsdAuthorize: No authentication data provided.
D [26/Oct/2011:14:03:27 +0200] cupsdReadClient: 22 1.1 CUPS-Get-Printers 1
D [26/Oct/2011:14:03:27 +0200] CUPS-Get-Printers
D [26/Oct/2011:14:03:27 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [26/Oct/2011:14:03:27 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [26/Oct/2011:14:03:27 +0200] cupsdAcceptClient: 23 from localhost (Domain)
D [26/Oct/2011:14:03:27 +0200] cupsdReadClient: 23 POST / HTTP/1.1
D [26/Oct/2011:14:03:27 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [26/Oct/2011:14:03:27 +0200] cupsdAuthorize: No authentication data provided.
D [26/Oct/2011:14:03:27 +0200] cupsdReadClient: 23 1.1 Get-Printer-Attributes 1
D [26/Oct/2011:14:03:27 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon_iP43004
D [26/Oct/2011:14:03:27 +0200] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Canon_iP43004) from localhost
D [26/Oct/2011:14:03:27 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [26/Oct/2011:14:03:27 +0200] cupsdReadClient: 23 WAITING Closing on EOF
D [26/Oct/2011:14:03:27 +0200] cupsdCloseClient: 23
D [26/Oct/2011:14:03:27 +0200] cupsdAcceptClient: 23 from localhost (Domain)
D [26/Oct/2011:14:03:27 +0200] cupsdReadClient: 23 POST / HTTP/1.1
D [26/Oct/2011:14:03:27 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [26/Oct/2011:14:03:27 +0200] cupsdAuthorize: No authentication data provided.
D [26/Oct/2011:14:03:27 +0200] cupsdReadClient: 23 1.1 Get-Printer-Attributes 1
D [26/Oct/2011:14:03:27 +0200] Get-Printer-Attributes ipp://localhost/printers/iP43003cups
D [26/Oct/2011:14:03:27 +0200] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/iP43003cups) from localhost
D [26/Oct/2011:14:03:27 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [26/Oct/2011:14:03:27 +0200] cupsdReadClient: 23 WAITING Closing on EOF
D [26/Oct/2011:14:03:27 +0200] cupsdCloseClient: 23
D [26/Oct/2011:14:03:27 +0200] cupsdReadClient: 22 WAITING Closing on EOF
D [26/Oct/2011:14:03:27 +0200] cupsdCloseClient: 22
D [26/Oct/2011:14:03:27 +0200] cupsdAcceptClient: 22 from localhost (Domain)
D [26/Oct/2011:14:03:27 +0200] cupsdReadClient: 22 POST / HTTP/1.1
D [26/Oct/2011:14:03:27 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [26/Oct/2011:14:03:27 +0200] cupsdAuthorize: No authentication data provided.
D [26/Oct/2011:14:03:27 +0200] cupsdReadClient: 22 1.1 Get-Jobs 1
D [26/Oct/2011:14:03:27 +0200] Get-Jobs ipp://localhost/printers/
D [26/Oct/2011:14:03:27 +0200] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [26/Oct/2011:14:03:27 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [26/Oct/2011:14:03:27 +0200] cupsdAcceptClient: 23 from localhost (Domain)
D [26/Oct/2011:14:03:27 +0200] cupsdReadClient: 23 POST / HTTP/1.1
D [26/Oct/2011:14:03:27 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [26/Oct/2011:14:03:27 +0200] cupsdAuthorize: No authentication data provided.
D [26/Oct/2011:14:03:27 +0200] cupsdReadClient: 23 1.1 Get-Printer-Attributes 1
D [26/Oct/2011:14:03:27 +0200] Get-Printer-Attributes ipp://DESKTOP:631/printers/Canon_iP43004
D [26/Oct/2011:14:03:27 +0200] Returning IPP successful-ok for Get-Printer-Attributes (ipp://DESKTOP:631/printers/Canon_iP43004) from localhost
D [26/Oct/2011:14:03:27 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [26/Oct/2011:14:03:27 +0200] cupsdReadClient: 23 WAITING Closing on EOF
D [26/Oct/2011:14:03:27 +0200] cupsdCloseClient: 23
D [26/Oct/2011:14:03:27 +0200] cupsdAcceptClient: 23 from localhost (Domain)
D [26/Oct/2011:14:03:27 +0200] cupsdReadClient: 23 POST / HTTP/1.1
D [26/Oct/2011:14:03:27 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [26/Oct/2011:14:03:27 +0200] cupsdAuthorize: No authentication data provided.
D [26/Oct/2011:14:03:27 +0200] cupsdReadClient: 23 1.1 Get-Job-Attributes 1
D [26/Oct/2011:14:03:27 +0200] Get-Job-Attributes ipp://localhost/jobs/30
D [26/Oct/2011:14:03:27 +0200] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/30) from localhost
D [26/Oct/2011:14:03:27 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [26/Oct/2011:14:03:27 +0200] cupsdReadClient: 23 WAITING Closing on EOF
D [26/Oct/2011:14:03:27 +0200] cupsdCloseClient: 23
D [26/Oct/2011:14:03:27 +0200] cupsdReadClient: 22 WAITING Closing on EOF
D [26/Oct/2011:14:03:27 +0200] cupsdCloseClient: 22
D [26/Oct/2011:14:03:28 +0200] cupsdAcceptClient: 22 from localhost (Domain)
D [26/Oct/2011:14:03:28 +0200] cupsdReadClient: 22 POST / HTTP/1.1
D [26/Oct/2011:14:03:28 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [26/Oct/2011:14:03:28 +0200] cupsdAuthorize: No authentication data provided.
D [26/Oct/2011:14:03:28 +0200] cupsdReadClient: 22 1.1 Get-Jobs 1
D [26/Oct/2011:14:03:28 +0200] Get-Jobs ipp://localhost/printers/
D [26/Oct/2011:14:03:28 +0200] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost
D [26/Oct/2011:14:03:28 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [26/Oct/2011:14:03:28 +0200] cupsdReadClient: 22 WAITING Closing on EOF
D [26/Oct/2011:14:03:28 +0200] cupsdCloseClient: 22
D [26/Oct/2011:14:03:29 +0200] cupsdAcceptClient: 22 from localhost (Domain)
D [26/Oct/2011:14:03:29 +0200] cupsdReadClient: 22 POST / HTTP/1.1
D [26/Oct/2011:14:03:29 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files
D [26/Oct/2011:14:03:29 +0200] cupsdAuthorize: No authentication data provided.
D [26/Oct/2011:14:03:29 +0200] cupsdReadClient: 22 1.1 Get-Notifications 1
D [26/Oct/2011:14:03:29 +0200] Get-Notifications /
D [26/Oct/2011:14:03:29 +0200] cupsdIsAuthorized: requesting-user-name="chris"
D [26/Oct/2011:14:03:29 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [26/Oct/2011:14:03:29 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [26/Oct/2011:14:03:29 +0200] cupsdReadClient: 22 WAITING Closing on EOF
D [26/Oct/2011:14:03:29 +0200] cupsdCloseClient: 22
D [26/Oct/2011:14:03:29 +0200] PID 2143 (/usr/lib/cups/filter/pstocanonij) exited with no errors.
D [26/Oct/2011:14:03:29 +0200] PID 2144 (/usr/lib/cups/backend/usb) exited with no errors.
D [26/Oct/2011:14:03:29 +0200] cupsdMarkDirty(-----S)
I [26/Oct/2011:14:03:29 +0200] [Job 30] Job completed.
D [26/Oct/2011:14:03:29 +0200] cupsdMarkDirty(----J-)
D [26/Oct/2011:14:03:29 +0200] cupsdMarkDirty(-----S)
D [26/Oct/2011:14:03:29 +0200] cupsdAcceptClient: 17 from localhost (Domain)
D [26/Oct/2011:14:03:29 +0200] cupsdAcceptClient: 22 from localhost (Domain)
D [26/Oct/2011:14:03:29 +0200] cupsdReadClient: 17 POST / HTTP/1.1
D [26/Oct/2011:14:03:29 +0200] cupsdSetBusyState: Active clients and dirty files
D [26/Oct/2011:14:03:29 +0200] cupsdAuthorize: No authentication data provided.
D [26/Oct/2011:14:03:29 +0200] cupsdReadClient: 22 POST / HTTP/1.1
D [26/Oct/2011:14:03:29 +0200] cupsdAuthorize: No authentication data provided.
D [26/Oct/2011:14:03:29 +0200] cupsdReadClient: 17 1.1 Get-Notifications 1
D [26/Oct/2011:14:03:29 +0200] Get-Notifications /
D [26/Oct/2011:14:03:29 +0200] cupsdIsAuthorized: requesting-user-name="chris"
D [26/Oct/2011:14:03:29 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [26/Oct/2011:14:03:29 +0200] cupsdReadClient: 22 1.1 Get-Notifications 1
D [26/Oct/2011:14:03:29 +0200] Get-Notifications /
D [26/Oct/2011:14:03:29 +0200] cupsdIsAuthorized: requesting-user-name="chris"
D [26/Oct/2011:14:03:29 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost
D [26/Oct/2011:14:03:29 +0200] cupsdReadClient: 14 POST / HTTP/1.1
D [26/Oct/2011:14:03:29 +0200] cupsdAuthorize: No authentication data provided.
D [26/Oct/2011:14:03:29 +0200] cupsdReadClient: 14 1.1 Get-Printer-Attributes 1
D [26/Oct/2011:14:03:29 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon_iP43004
D [26/Oct/2011:14:03:29 +0200] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Canon_iP43004) from localhost
D [26/Oct/2011:14:03:29 +0200] cupsdAcceptClient: 23 from localhost (Domain)
D [26/Oct/2011:14:03:29 +0200] cupsdSetBusyState: Dirty files
D [26/Oct/2011:14:03:29 +0200] cupsdReadClient: 23 POST / HTTP/1.1
D [26/Oct/2011:14:03:29 +0200] cupsdSetBusyState: Active clients and dirty files
D [26/Oct/2011:14:03:29 +0200] cupsdAuthorize: No authentication data provided.
D [26/Oct/2011:14:03:29 +0200] cupsdReadClient: 23 1.1 Get-Printer-Attributes 1
D [26/Oct/2011:14:03:29 +0200] Get-Printer-Attributes ipp://DESKTOP:631/printers/Canon_iP43004
D [26/Oct/2011:14:03:29 +0200] Returning IPP successful-ok for Get-Printer-Attributes (ipp://DESKTOP:631/printers/Canon_iP43004) from localhost
D [26/Oct/2011:14:03:29 +0200] cupsdSetBusyState: Dirty files
D [26/Oct/2011:14:03:29 +0200] cupsdReadClient: 17 WAITING Closing on EOF
D [26/Oct/2011:14:03:29 +0200] cupsdCloseClient: 17
D [26/Oct/2011:14:03:29 +0200] cupsdReadClient: 22 WAITING Closing on EOF
D [26/Oct/2011:14:03:29 +0200] cupsdCloseClient: 22
D [26/Oct/2011:14:03:30 +0200] cupsdReadClient: 19 POST / HTTP/1.1
D [26/Oct/2011:14:03:30 +0200] cupsdSetBusyState: Active clients and dirty files
D [26/Oct/2011:14:03:30 +0200] cupsdAuthorize: No authentication data provided.
D [26/Oct/2011:14:03:30 +0200] [Job 30] Unloading...
D [26/Oct/2011:14:03:30 +0200] cupsdReadClient: 19 1.1 CUPS-Get-Printers 1
D [26/Oct/2011:14:03:30 +0200] CUPS-Get-Printers
D [26/Oct/2011:14:03:30 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost
D [26/Oct/2011:14:03:30 +0200] cupsdSetBusyState: Dirty files
D [26/Oct/2011:14:03:30 +0200] cupsdReadClient: 19 POST / HTTP/1.1
D [26/Oct/2011:14:03:30 +0200] cupsdSetBusyState: Active clients and dirty files
D [26/Oct/2011:14:03:30 +0200] cupsdAuthorize: No authentication data provided.
D [26/Oct/2011:14:03:30 +0200] cupsdReadClient: 19 1.1 CUPS-Get-Classes 1
D [26/Oct/2011:14:03:30 +0200] CUPS-Get-Classes
D [26/Oct/2011:14:03:30 +0200] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost
D [26/Oct/2011:14:03:30 +0200] cupsdSetBusyState: Dirty files
D [26/Oct/2011:14:03:30 +0200] cupsdReadClient: 19 POST / HTTP/1.1
D [26/Oct/2011:14:03:30 +0200] cupsdSetBusyState: Active clients and dirty files
D [26/Oct/2011:14:03:30 +0200] cupsdAuthorize: No authentication data provided.
D [26/Oct/2011:14:03:30 +0200] cupsdReadClient: 19 1.1 CUPS-Get-Default 1
D [26/Oct/2011:14:03:30 +0200] CUPS-Get-Default
D [26/Oct/2011:14:03:30 +0200] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost
D [26/Oct/2011:14:03:30 +0200] cupsdSetBusyState: Dirty files
I [26/Oct/2011:14:03:57 +0200] Saving job cache file "/var/cache/cups/job.cache"...
I [26/Oct/2011:14:03:57 +0200] Saving subscriptions.conf...
D [26/Oct/2011:14:03:57 +0200] cupsdSetBusyState: Not busy
D [26/Oct/2011:14:03:57 +0200] Report: clients=7
D [26/Oct/2011:14:03:57 +0200] Report: jobs=21
D [26/Oct/2011:14:03:57 +0200] Report: jobs-active=0
D [26/Oct/2011:14:03:57 +0200] Report: printers=2
D [26/Oct/2011:14:03:57 +0200] Report: printers-implicit=0
D [26/Oct/2011:14:03:57 +0200] Report: stringpool-string-count=72683
D [26/Oct/2011:14:03:57 +0200] Report: stringpool-alloc-bytes=15336
D [26/Oct/2011:14:03:57 +0200] Report: stringpool-total-bytes=1347856
D [26/Oct/2011:14:03:59 +0200] cupsdNetIFUpdate: "lo" = localhost:631
D [26/Oct/2011:14:03:59 +0200] cupsdNetIFUpdate: "wlan0" = 192.168.1.2:631
D [26/Oct/2011:14:03:59 +0200] cupsdNetIFUpdate: "lo" = localhost:631
D [26/Oct/2011:14:03:59 +0200] cupsdNetIFUpdate: "wlan0" = [v1.fe80::21f:1fff:fe05:e56e+wlan0]:631
D [26/Oct/2011:14:04:00 +0200] cupsdAcceptClient: 17 from localhost (Domain)
D [26/Oct/2011:14:04:00 +0200] cupsdReadClient: 17 GET /admin/conf/cupsd.conf HTTP/1.1
D [26/Oct/2011:14:04:00 +0200] cupsdSetBusyState: Active clients
D [26/Oct/2011:14:04:00 +0200] cupsdAuthorize: No authentication data provided.
D [26/Oct/2011:14:04:00 +0200] cupsdIsAuthorized: username=""
D [26/Oct/2011:14:04:00 +0200] cupsdSendHeader: 17 WWW-Authenticate: Basic realm="CUPS", trc="y"
D [26/Oct/2011:14:04:00 +0200] cupsdCloseClient: 17
D [26/Oct/2011:14:04:00 +0200] cupsdSetBusyState: Not busy
D [26/Oct/2011:14:04:00 +0200] cupsdAcceptClient: 17 from localhost (Domain)
D [26/Oct/2011:14:04:00 +0200] cupsdReadClient: 17 GET /admin/conf/cupsd.conf HTTP/1.1
D [26/Oct/2011:14:04:00 +0200] cupsdSetBusyState: Active clients
D [26/Oct/2011:14:04:00 +0200] cupsdAuthorize: Authorized as chris using PeerCred
D [26/Oct/2011:14:04:00 +0200] cupsdIsAuthorized: username="chris"
D [26/Oct/2011:14:04:00 +0200] cupsdSetBusyState: Not busy
D [26/Oct/2011:14:04:16 +0200] cupsdReadClient: 17 PUT /admin/conf/cupsd.conf HTTP/1.1
D [26/Oct/2011:14:04:16 +0200] cupsdSetBusyState: Active clients
D [26/Oct/2011:14:04:16 +0200] cupsdAuthorize: Authorized as chris using PeerCred
D [26/Oct/2011:14:04:16 +0200] cupsdIsAuthorized: username="chris"
I [26/Oct/2011:14:04:16 +0200] Installing config file "/etc/cups/cupsd.conf"...
D [26/Oct/2011:14:04:16 +0200] cupsdSetBusyState: Not busy
D [26/Oct/2011:14:04:16 +0200] cupsdCloseClient: 13
D [26/Oct/2011:14:04:16 +0200] cupsdCloseClient: 14
D [26/Oct/2011:14:04:16 +0200] cupsdCloseClient: 15
D [26/Oct/2011:14:04:16 +0200] cupsdCloseClient: 20
D [26/Oct/2011:14:04:16 +0200] cupsdCloseClient: 19
D [26/Oct/2011:14:04:16 +0200] cupsdCloseClient: 21
D [26/Oct/2011:14:04:16 +0200] cupsdCloseClient: 23
D [26/Oct/2011:14:04:16 +0200] cupsdCloseClient: 17
D [26/Oct/2011:14:04:16 +0200] cupsdDeregisterPrinter(p=0x21781f80(Canon_iP43004), removeit=1)
D [26/Oct/2011:14:04:16 +0200] cupsdDeregisterPrinter(p=0x21786bd0(iP43003cups), removeit=1)
I [26/Oct/2011:14:04:16 +0200] Listening to 0.0.0.0:631 (IPv4)
I [26/Oct/2011:14:04:16 +0200] Listening to [v1.::]:631 (IPv6)
I [26/Oct/2011:14:04:16 +0200] Listening to /var/run/cups/cups.sock (Domain)
I [26/Oct/2011:14:04:16 +0200] Remote access is enabled.
D [26/Oct/2011:14:04:16 +0200] Added auto ServerAlias DESKTOP
I [26/Oct/2011:14:04:16 +0200] Loaded configuration file "/etc/cups/cupsd.conf"
I [26/Oct/2011:14:04:16 +0200] Using default TempDir of /var/spool/cups/tmp...
I [26/Oct/2011:14:04:16 +0200] Configured for up to 100 clients.
I [26/Oct/2011:14:04:16 +0200] Allowing up to 100 client connections per host.
I [26/Oct/2011:14:04:16 +0200] Using policy "default" as the default!
D [26/Oct/2011:14:04:16 +0200] load_ppd: Loading /var/cache/cups/Canon_iP43004.ipp4...
D [26/Oct/2011:14:04:16 +0200] cupsdRegisterPrinter(p=0x21781f80(Canon_iP43004))
D [26/Oct/2011:14:04:16 +0200] Registering Avahi printer Canon_iP43004 with name "Canon iP4300via631 @ DESKTOP" and type "_ipp._tcp"
D [26/Oct/2011:14:04:16 +0200] load_ppd: Loading /var/cache/cups/iP43003cups.ipp4...
D [26/Oct/2011:14:04:16 +0200] cupsdRegisterPrinter(p=0x21786bd0(iP43003cups))
D [26/Oct/2011:14:04:16 +0200] Registering Avahi printer iP43003cups with name "iP43003cups @ DESKTOP" and type "_ipp._tcp"
D [26/Oct/2011:14:04:16 +0200] cupsdMarkDirty(---p--)
D [26/Oct/2011:14:04:16 +0200] cupsdSetBusyState: Dirty files
I [26/Oct/2011:14:04:16 +0200] Partial reload complete.
I [26/Oct/2011:14:04:16 +0200] Listening to 0.0.0.0:631 on fd 5...
I [26/Oct/2011:14:04:16 +0200] Listening to [v1.::]:631 on fd 7...
I [26/Oct/2011:14:04:16 +0200] Listening to /var/run/cups/cups.sock on fd 8...
I [26/Oct/2011:14:04:16 +0200] Resuming new connection processing...
D [26/Oct/2011:14:04:16 +0200] cupsdRegisterPrinter(p=0x21781f80(Canon_iP43004))
E [26/Oct/2011:14:04:16 +0200] Failed to update TXT record for Canon iP4300via631 @ DESKTOP: -2
D [26/Oct/2011:14:04:16 +0200] Registering Avahi printer Canon_iP43004 with name "Canon iP4300via631 @ DESKTOP" and type "_ipp._tcp"
D [26/Oct/2011:14:04:16 +0200] cupsdRegisterPrinter(p=0x21786bd0(iP43003cups))
E [26/Oct/2011:14:04:16 +0200] Failed to update TXT record for iP43003cups @ DESKTOP: -2
D [26/Oct/2011:14:04:16 +0200] Registering Avahi printer iP43003cups with name "iP43003cups @ DESKTOP" and type "_ipp._tcp"
D [26/Oct/2011:14:04:16 +0200] Discarding unused server-restarted event...
D [26/Oct/2011:14:04:17 +0200] cupsdAcceptClient: 13 from localhost (Domain)
D [26/Oct/2011:14:04:23 +0200] Avahi entry group established for Canon iP4300via631 @ DESKTOP
D [26/Oct/2011:14:04:24 +0200] Avahi entry group established for iP43003cups @ DESKTOP
I [26/Oct/2011:14:04:47 +0200] Generating printcap /var/run/cups/printcap...
D [26/Oct/2011:14:04:47 +0200] cupsdSetBusyState: Not busy
D [26/Oct/2011:14:04:59 +0200] Report: clients=1
D [26/Oct/2011:14:04:59 +0200] Report: jobs=21
D [26/Oct/2011:14:04:59 +0200] Report: jobs-active=0
D [26/Oct/2011:14:04:59 +0200] Report: printers=2
D [26/Oct/2011:14:04:59 +0200] Report: printers-implicit=0
D [26/Oct/2011:14:04:59 +0200] Report: stringpool-string-count=72694
D [26/Oct/2011:14:04:59 +0200] Report: stringpool-alloc-bytes=15336
D [26/Oct/2011:14:04:59 +0200] Report: stringpool-total-bytes=1347984
D [26/Oct/2011:14:05:01 +0200] cupsdNetIFUpdate: "lo" = localhost:631
D [26/Oct/2011:14:05:01 +0200] cupsdNetIFUpdate: "wlan0" = 192.168.1.2:631
D [26/Oct/2011:14:05:01 +0200] cupsdNetIFUpdate: "lo" = localhost:631
D [26/Oct/2011:14:05:01 +0200] cupsdNetIFUpdate: "wlan0" = [v1.fe80::21f:1fff:fe05:e56e+wlan0]:631
```

---

### Post by 2CV67 on 2011-10-26
I see there is a built-in troubleshooting function!
Printing > Help > Troubleshoot

You may well ask why I didn't start there.
Me too...

So I tried it & it failed to print a test page.
Then it said:
"Sorry! There is no obvious solution to this problem..."

Diagnostic output produced another long file, below, which again does not make much sense to me, but may to others (I hope!).
```
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dest': <cups.Dest Canon_iP43004>,
 'cups_instance': None,
 'cups_queue': 'Canon_iP43004',
 'cups_queue_listed': True}
Page 3 (Check printer sanity):
{'cups_device_uri_scheme': u'usb',
 'cups_printer_dict': {'device-uri': u'usb://Canon/iP4300',
                       'printer-info': u'Canon iP4300via631',
                       'printer-is-shared': True,
                       'printer-location': u'',
                       'printer-make-and-model': u'Canon iP4300 Ver.2.70',
                       'printer-state': 3,
                       'printer-state-message': u'',
                       'printer-state-reasons': [u'none'],
                       'printer-type': 8425500,
                       'printer-uri-supported': u'ipp://localhost:631/printers/Canon_iP43004'},
 'cups_printer_remote': False,
 'is_cups_class': False,
 'local_cups_queue_attributes': {'auth-info-required': u'none',
                                 'charset-configured': u'utf-8',
                                 'charset-supported': [u'us-ascii', u'utf-8'],
                                 'color-supported': True,
                                 'compression-supported': [u'none', u'gzip'],
                                 'copies-default': 1,
                                 'copies-supported': (1, 9999),
                                 'cups-version': u'1.4.6',
                                 'device-uri': u'usb://Canon/iP4300',
                                 'document-format-default': u'application/octet-stream',
                                 'document-format-supported': [u'application/octet-stream',
                                                               u'application/openofficeps',
                                                               u'application/pdf',
                                                               u'application/postscript',
                                                               u'application/vnd.adobe-reader-postscript',
                                                               u'application/vnd.cups-banner',
                                                               u'application/vnd.cups-pdf',
                                                               u'application/vnd.cups-postscript',
                                                               u'application/vnd.cups-raw',
                                                               u'application/vnd.hp-hpgl',
                                                               u'application/x-cshell',
                                                               u'application/x-csource',
                                                               u'application/x-perl',
                                                               u'application/x-shell',
                                                               u'image/gif',
                                                               u'image/jpeg',
                                                               u'image/png',
                                                               u'image/tiff',
                                                               u'image/x-bitmap',
                                                               u'image/x-photocd',
                                                               u'image/x-portable-anymap',
                                                               u'image/x-portable-bitmap',
                                                               u'image/x-portable-graymap',
                                                               u'image/x-portable-pixmap',
                                                               u'image/x-sgi-rgb',
                                                               u'image/x-sun-raster',
                                                               u'image/x-xbitmap',
                                                               u'image/x-xpixmap',
                                                               u'image/x-xwindowdump',
                                                               u'text/css',
                                                               u'text/html',
                                                               u'text/plain'],
                                 'finishings-default': 3,
                                 'finishings-supported': [3],
                                 'generated-natural-language-supported': [u'en-us'],
                                 'ipp-versions-supported': [u'1.0',
                                                            u'1.1',
                                                            u'2.0',
                                                            u'2.1'],
                                 'ippget-event-life': 15,
                                 'job-creation-attributes-supported': [u'copies',
                                                                       u'finishings',
                                                                       u'ipp-attribute-fidelity',
                                                                       u'job-hold-until',
                                                                       u'job-name',
                                                                       u'job-priority',
                                                                       u'job-sheets',
                                                                       u'media',
                                                                       u'media-col',
                                                                       u'multiple-document-handling',
                                                                       u'number-up',
                                                                       u'output-bin',
                                                                       u'output-mode',
                                                                       u'orientation-requested',
                                                                       u'page-ranges',
                                                                       u'print-quality',
                                                                       u'printer-resolution',
                                                                       u'sides'],
                                 'job-hold-until-default': u'no-hold',
                                 'job-hold-until-supported': [u'no-hold',
                                                              u'indefinite',
                                                              u'day-time',
                                                              u'evening',
                                                              u'night',
                                                              u'second-shift',
                                                              u'third-shift',
                                                              u'weekend'],
                                 'job-k-limit': 0,
                                 'job-page-limit': 0,
                                 'job-priority-default': 50,
                                 'job-priority-supported': [100],
                                 'job-quota-period': 0,
                                 'job-settable-attributes-supported': [u'copies',
                                                                       u'finishings',
                                                                       u'job-hold-until',
                                                                       u'job-name',
                                                                       u'job-priority',
                                                                       u'media',
                                                                       u'media-col',
                                                                       u'multiple-document-handling',
                                                                       u'number-up',
                                                                       u'output-bin',
                                                                       u'output-mode',
                                                                       u'orientation-requested',
                                                                       u'page-ranges',
                                                                       u'print-quality',
                                                                       u'printer-resolution',
                                                                       u'sides'],
                                 'job-sheets-default': (u'none', u'none'),
                                 'job-sheets-supported': [u'none',
                                                          u'classified',
                                                          u'confidential',
                                                          u'secret',
                                                          u'standard',
                                                          u'topsecret',
                                                          u'unclassified'],
                                 'marker-change-time': 0,
                                 'media-bottom-margin-supported': [499, 2650],
                                 'media-col-supported': [u'media-bottom-margin',
                                                         u'media-left-margin',
                                                         u'media-right-margin',
                                                         u'media-size',
                                                         u'media-source',
                                                         u'media-top-margin',
                                                         u'media-type'],
                                 'media-default': u'iso_a4_210x297mm',
                                 'media-left-margin-supported': [639, 340],
                                 'media-right-margin-supported': [630,
                                                                  356,
                                                                  330,
                                                                  343,
                                                                  340,
                                                                  329,
                                                                  323,
                                                                  342,
                                                                  346,
                                                                  352,
                                                                  347,
                                                                  337],
                                 'media-source-supported': [u'switch',
                                                            u'asf',
                                                            u'main'],
                                 'media-supported': [u'na_letter_8.5x11in',
                                                     u'na_legal_8.5x14in',
                                                     u'iso_a5_148x210mm',
                                                     u'iso_a4_210x297mm',
                                                     u'jis_b5_182x257mm',
                                                     u'oe_4-x6_4x6in',
                                                     u'oe_4-x8_4x8in',
                                                     u'oe_5-x7_5x7in',
                                                     u'oe_8-x10_8x10in',
                                                     u'oe_l_3.5x5in',
                                                     u'om_2l_127x178.15mm',
                                                     u'om_postcard_99.83x148.16mm',
                                                     u'om_postdbl_200.02x148.16mm',
                                                     u'om_envelop10p_104.77x241.3mm',
                                                     u'om_envelopdlp_110.06x220.13mm',
                                                     u'om_envj4p_105.12x234.95mm',
                                                     u'om_envj6p_98.07x190.14mm',
                                                     u'om_creditcard_53.97x86.07mm',
                                                     u'om_businesscard_55.03x91.01mm',
                                                     u'om_wide_101.6x180.62mm',
                                                     u'custom_min_54x86mm',
                                                     u'custom_max_8.5x23in'],
                                 'media-top-margin-supported': [299,
                                                                290,
                                                                303,
                                                                317,
                                                                315,
                                                                316,
                                                                313,
                                                                294,
                                                                314,
                                                                307,
                                                                301,
                                                                300],
                                 'media-type-supported': [u'stationery',
                                                          u'prophoto',
                                                          u'superphoto',
                                                          u'doublesidephoto',
                                                          u'photographic-matte',
                                                          u'photographic-glossy',
                                                          u'highres',
                                                          u'ijpostcard',
                                                          u'postcard',
                                                          u'tshirt',
                                                          u'envelope',
                                                          u'otherphoto'],
                                 'multiple-document-handling-supported': [u'separate-documents-uncollated-copies',
                                                                          u'separate-documents-collated-copies'],
                                 'multiple-document-jobs-supported': True,
                                 'multiple-operation-time-out': 300,
                                 'natural-language-configured': u'en-us',
                                 'notify-attributes-supported': [u'printer-state-change-time',
                                                                 u'notify-lease-expiration-time',
                                                                 u'notify-subscriber-user-name'],
                                 'notify-events-default': [u'job-completed'],
                                 'notify-events-supported': [u'job-completed',
                                                             u'job-config-changed',
                                                             u'job-created',
                                                             u'job-progress',
                                                             u'job-state-changed',
                                                             u'job-stopped',
                                                             u'printer-added',
                                                             u'printer-changed',
                                                             u'printer-config-changed',
                                                             u'printer-deleted',
                                                             u'printer-finishings-changed',
                                                             u'printer-media-changed',
                                                             u'printer-modified',
                                                             u'printer-restarted',
                                                             u'printer-shutdown',
                                                             u'printer-state-changed',
                                                             u'printer-stopped',
                                                             u'server-audit',
                                                             u'server-restarted',
                                                             u'server-started',
                                                             u'server-stopped'],
                                 'notify-lease-duration-default': 86400,
                                 'notify-lease-duration-supported': (0,
                                                                     2147483647),
                                 'notify-max-events-supported': [100],
                                 'notify-pull-method-supported': [u'ippget'],
                                 'notify-schemes-supported': [u'dbus',
                                                              u'mailto',
                                                              u'rss'],
                                 'number-up-default': 1,
                                 'number-up-supported': [1, 2, 4, 6, 9, 16],
                                 'operations-supported': [2,
                                                          4,
                                                          5,
                                                          6,
                                                          8,
                                                          9,
                                                          10,
                                                          11,
                                                          12,
                                                          13,
                                                          16,
                                                          17,
                                                          18,
                                                          19,
                                                          20,
                                                          21,
                                                          22,
                                                          23,
                                                          24,
                                                          25,
                                                          26,
                                                          27,
                                                          28,
                                                          34,
                                                          35,
                                                          37,
                                                          38,
                                                          16385,
                                                          16386,
                                                          16387,
                                                          16388,
                                                          16389,
                                                          16390,
                                                          16391,
                                                          16392,
                                                          16393,
                                                          16394,
                                                          16395,
                                                          16396,
                                                          16397,
                                                          16398,
                                                          16399,
                                                          16423],
                                 'orientation-requested-default': None,
                                 'orientation-requested-supported': [3,
                                                                     4,
                                                                     5,
                                                                     6],
                                 'output-bin-default': u'face-down',
                                 'output-bin-supported': [u'face-down'],
                                 'output-mode-default': u'color',
                                 'output-mode-supported': [u'monochrome',
                                                           u'color'],
                                 'page-ranges-supported': True,
                                 'pages-per-minute': 1,
                                 'pages-per-minute-color': 1,
                                 'pdl-override-supported': [u'attempted'],
                                 'port-monitor': u'none',
                                 'port-monitor-supported': [u'none'],
                                 'print-quality-default': 4,
                                 'print-quality-supported': [4],
                                 'printer-commands': [u'AutoConfigure',
                                                      u'Clean',
                                                      u'PrintSelfTestPage'],
                                 'printer-current-time': '(IPP_TAG_DATE)',
                                 'printer-dns-sd-name': u'Canon iP4300via631 @ DESKTOP',
                                 'printer-error-policy': u'retry-job',
                                 'printer-error-policy-supported': [u'abort-job',
                                                                    u'retry-current-job',
                                                                    u'retry-job',
                                                                    u'stop-printer'],
                                 'printer-icons': u'http://localhost:631/icons/Canon_iP43004.png',
                                 'printer-info': u'Canon iP4300via631',
                                 'printer-is-accepting-jobs': True,
                                 'printer-is-shared': True,
                                 'printer-location': u'',
                                 'printer-make-and-model': u'Canon iP4300 Ver.2.70',
                                 'printer-more-info': u'http://localhost:631/printers/Canon_iP43004',
                                 'printer-name': u'Canon_iP43004',
                                 'printer-op-policy': u'default',
                                 'printer-op-policy-supported': [u'authenticated',
                                                                 u'default'],
                                 'printer-resolution-default': '(unknown IPP tag)',
                                 'printer-resolution-supported': ['(unknown IPP tag)',
                                                                  '(unknown IPP tag)',
                                                                  '(unknown IPP tag)',
                                                                  '(unknown IPP tag)'],
                                 'printer-settable-attributes-supported': [u'printer-info',
                                                                           u'printer-location'],
                                 'printer-state': 3,
                                 'printer-state-change-time': 1319631775,
                                 'printer-state-message': u'',
                                 'printer-state-reasons': [u'none'],
                                 'printer-type': 8425500,
                                 'printer-up-time': 1319631965,
                                 'printer-uri-supported': [u'ipp://localhost:631/printers/Canon_iP43004'],
                                 'queued-job-count': 0,
                                 'server-is-sharing-printers': True,
                                 'sides-default': u'one-sided',
                                 'sides-supported': [u'one-sided',
                                                     u'two-sided-long-edge',
                                                     u'two-sided-short-edge'],
                                 'uri-authentication-supported': [u'requesting-user-name'],
                                 'uri-security-supported': [u'none']}}
Page 4 (Check PPD sanity):
{'cups_printer_ppd_defaults': {u'General': {u'CNQuality': u'3',
                                            u'ColorModel': u'rgb',
                                            u'Duplex': u'None',
                                            u'InputSlot': u'switch',
                                            u'MediaType': u'plain',
                                            u'PageRegion': u'A4',
                                            u'PageSize': u'A4',
                                            u'Resolution': u'600'}},
 'cups_printer_ppd_valid': True,
 'missing_pkgs_and_exes': ([], [])}
Page 5 (Local or remote?):
{'printer_is_remote': False}
Page 6 (Choose device):
{'cups_device_dict': {'device-class': u'direct',
                      'device-id': u'MFG:Canon;CMD:BJL,BJRaster3,BSCCe;SOJ:TXT01;MDL:iP4300;CLS:PRINTER;DES:Canon iP4300;VER:1.06;STA:10;FSI:03;HRI:OTH;MSI:AOFF,BOFF,DAT,E3;',
                      'device-info': u'Canon iP4300',
                      'device-location': u'',
                      'device-make-and-model': u'Canon iP4300'}}
Page 7 (Error log checkpoint):
{'cups_server_settings': {'BrowseAddress': '@LOCAL',
                          'BrowseLocalProtocols': 'CUPS dnssd',
                          'BrowseOrder': 'allow,deny',
                          'Browsing': 'On',
                          'DefaultAuthType': 'Basic',
                          'Listen': '/var/run/cups/cups.sock',
                          'LogLevel': 'debug',
                          'MaxLogSize': '0',
                          'Port': '631',
                          'SystemGroup': 'lpadmin',
                          '_debug_logging': '1',
                          '_remote_admin': '1',
                          '_remote_any': '0',
                          '_remote_printers': '0',
                          '_share_printers': '1',
                          '_user_cancel_any': '0'},
 'error_log_checkpoint': 94522L}
Page 8 (Print test page):
{'test_page_attempted': '26/Oct/2011:14:27:15 +0000',
 'test_page_completions': [(31, u'Job completed.')],
 'test_page_job_id': [31],
 'test_page_job_status': [(True,
                           31,
                           'Canon_iP43004',
                           'Test Page',
                           'Completed',
                           {'attributes-charset': u'utf-8',
                            'attributes-natural-language': u'en-ie',
                            'document-count': 0,
                            'document-format': u'application/vnd.cups-banner',
                            'job-hold-until': u'no-hold',
                            'job-id': 31,
                            'job-k-octets': 1,
                            'job-media-progress': 0,
                            'job-media-sheets-completed': 0,
                            'job-more-info': u'ipp://localhost:631/jobs/31',
                            'job-name': u'Test Page',
                            'job-originating-host-name': u'localhost',
                            'job-originating-user-name': u'chris',
                            'job-preserved': False,
                            'job-printer-state-message': u'',
                            'job-printer-state-reasons': [u'none'],
                            'job-printer-up-time': 1319632099,
                            'job-printer-uri': u'ipp://DESKTOP:631/printers/Canon_iP43004',
                            'job-priority': 50,
                            'job-sheets': [u'none', u'none'],
                            'job-state': 9,
                            'job-state-reasons': u'job-completed-successfully',
                            'job-uri': u'ipp://localhost:631/jobs/31',
                            'job-uuid': u'urn:uuid:96c63aaa-fad1-30a8-6a87-c76f58edaf76',
                            'printer-uri': u'ipp://localhost/printers/Canon_iP43004',
                            'time-at-completed': 1319632044,
                            'time-at-creation': 1319632035,
                            'time-at-processing': 1319632035})],
 'test_page_successful': False}
Page 9 (Error log fetch):
{'error_log': ['D [26/Oct/2011:14:26:21 +0200] cupsdSetBusyState: Not busy',
               'D [26/Oct/2011:14:26:21 +0200] cupsdReadClient: 15 POST / HTTP/1.1',
               'D [26/Oct/2011:14:26:21 +0200] cupsdSetBusyState: Active clients',
               'D [26/Oct/2011:14:26:21 +0200] cupsdAuthorize: Authorized as chris using PeerCred',
               'D [26/Oct/2011:14:26:21 +0200] cupsdReadClient: 15 1.1 Get-Jobs 1',
               'D [26/Oct/2011:14:26:21 +0200] Get-Jobs ipp://localhost/printers/',
               'D [26/Oct/2011:14:26:21 +0200] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [26/Oct/2011:14:26:21 +0200] cupsdSetBusyState: Not busy',
               'D [26/Oct/2011:14:26:21 +0200] cupsdReadClient: 15 POST / HTTP/1.1',
               'D [26/Oct/2011:14:26:21 +0200] cupsdSetBusyState: Active clients',
               'D [26/Oct/2011:14:26:21 +0200] cupsdAuthorize: Authorized as chris using PeerCred',
               'D [26/Oct/2011:14:26:21 +0200] cupsdReadClient: 15 1.1 Get-Jobs 1',
               'D [26/Oct/2011:14:26:21 +0200] Get-Jobs ipp://localhost/printers/',
               'D [26/Oct/2011:14:26:21 +0200] [Job 1] Loading attributes...',
               'D [26/Oct/2011:14:26:21 +0200] [Job 7] Loading attributes...',
               'D [26/Oct/2011:14:26:21 +0200] [Job 10] Loading attributes...',
               'D [26/Oct/2011:14:26:21 +0200] [Job 11] Loading attributes...',
               'D [26/Oct/2011:14:26:21 +0200] [Job 13] Loading attributes...',
               'D [26/Oct/2011:14:26:21 +0200] [Job 14] Loading attributes...',
               'D [26/Oct/2011:14:26:21 +0200] [Job 15] Loading attributes...',
               'D [26/Oct/2011:14:26:21 +0200] [Job 16] Loading attributes...',
               'D [26/Oct/2011:14:26:21 +0200] [Job 17] Loading attributes...',
               'D [26/Oct/2011:14:26:21 +0200] [Job 19] Loading attributes...',
               'D [26/Oct/2011:14:26:21 +0200] [Job 20] Loading attributes...',
               'D [26/Oct/2011:14:26:21 +0200] [Job 21] Loading attributes...',
               'D [26/Oct/2011:14:26:21 +0200] [Job 22] Loading attributes...',
               'D [26/Oct/2011:14:26:21 +0200] [Job 23] Loading attributes...',
               'D [26/Oct/2011:14:26:21 +0200] [Job 24] Loading attributes...',
               'D [26/Oct/2011:14:26:21 +0200] [Job 25] Loading attributes...',
               'D [26/Oct/2011:14:26:21 +0200] [Job 26] Loading attributes...',
               'D [26/Oct/2011:14:26:21 +0200] [Job 27] Loading attributes...',
               'D [26/Oct/2011:14:26:21 +0200] [Job 28] Loading attributes...',
               'D [26/Oct/2011:14:26:21 +0200] [Job 29] Loading attributes...',
               'D [26/Oct/2011:14:26:21 +0200] [Job 30] Loading attributes...',
               'D [26/Oct/2011:14:26:21 +0200] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [26/Oct/2011:14:26:21 +0200] cupsdSetBusyState: Not busy',
               'D [26/Oct/2011:14:26:21 +0200] cupsdReadClient: 15 POST / HTTP/1.1',
               'D [26/Oct/2011:14:26:21 +0200] cupsdSetBusyState: Active clients',
               'D [26/Oct/2011:14:26:21 +0200] cupsdAuthorize: Authorized as chris using PeerCred',
               'D [26/Oct/2011:14:26:21 +0200] cupsdReadClient: 15 1.1 Create-Printer-Subscription 1',
               'D [26/Oct/2011:14:26:21 +0200] Create-Printer-Subscription /',
               'D [26/Oct/2011:14:26:21 +0200] cupsdCreateSubscription(con=0x21a14070(15), uri="/")',
               'D [26/Oct/2011:14:26:21 +0200] pullmethod="ippget"',
               'D [26/Oct/2011:14:26:21 +0200] notify-lease-duration=86400',
               'D [26/Oct/2011:14:26:21 +0200] notify-time-interval=0',
               'D [26/Oct/2011:14:26:21 +0200] cupsdAddSubscription(mask=17800, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [26/Oct/2011:14:26:21 +0200] Added subscription 307 for server',
               'D [26/Oct/2011:14:26:21 +0200] cupsdMarkDirty(-----S)',
               'D [26/Oct/2011:14:26:21 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [26/Oct/2011:14:26:21 +0200] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost',
               'D [26/Oct/2011:14:26:21 +0200] cupsdSetBusyState: Dirty files',
               'D [26/Oct/2011:14:26:23 +0200] cupsdReadClient: 15 POST / HTTP/1.1',
               'D [26/Oct/2011:14:26:23 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [26/Oct/2011:14:26:23 +0200] cupsdAuthorize: Authorized as chris using PeerCred',
               'D [26/Oct/2011:14:26:23 +0200] cupsdReadClient: 15 1.1 Get-Notifications 1',
               'D [26/Oct/2011:14:26:23 +0200] Get-Notifications /',
               'D [26/Oct/2011:14:26:23 +0200] cupsdIsAuthorized: username="chris"',
               'D [26/Oct/2011:14:26:23 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [26/Oct/2011:14:26:23 +0200] cupsdSetBusyState: Dirty files',
               'I [26/Oct/2011:14:26:52 +0200] Saving subscriptions.conf...',
               'D [26/Oct/2011:14:26:52 +0200] cupsdSetBusyState: Not busy',
               'D [26/Oct/2011:14:27:04 +0200] cupsdNetIFUpdate: "lo" = localhost:631',
               'D [26/Oct/2011:14:27:04 +0200] cupsdNetIFUpdate: "wlan0" = 192.168.1.2:631',
               'D [26/Oct/2011:14:27:04 +0200] cupsdNetIFUpdate: "lo" = localhost:631',
               'D [26/Oct/2011:14:27:04 +0200] cupsdNetIFUpdate: "wlan0" = [v1.fe80::21f:1fff:fe05:e56e+wlan0]:631',
               'D [26/Oct/2011:14:27:04 +0200] Report: clients=7',
               'D [26/Oct/2011:14:27:04 +0200] Report: jobs=21',
               'D [26/Oct/2011:14:27:04 +0200] Report: jobs-active=0',
               'D [26/Oct/2011:14:27:04 +0200] Report: printers=2',
               'D [26/Oct/2011:14:27:04 +0200] Report: printers-implicit=0',
               'D [26/Oct/2011:14:27:04 +0200] Report: stringpool-string-count=73601',
               'D [26/Oct/2011:14:27:04 +0200] Report: stringpool-alloc-bytes=17776',
               'D [26/Oct/2011:14:27:04 +0200] Report: stringpool-total-bytes=1366248',
               'D [26/Oct/2011:14:27:15 +0200] cupsdAcceptClient: 22 from localhost (Domain)',
               'D [26/Oct/2011:14:27:15 +0200] cupsdReadClient: 22 POST /printers/Canon_iP43004 HTTP/1.1',
               'D [26/Oct/2011:14:27:15 +0200] cupsdSetBusyState: Active clients',
               'D [26/Oct/2011:14:27:15 +0200] cupsdAuthorize: No authentication data provided.',
               'D [26/Oct/2011:14:27:15 +0200] cupsdReadClient: 22 1.1 Print-Job 1',
               'D [26/Oct/2011:14:27:15 +0200] Print-Job ipp://localhost/printers/Canon_iP43004',
               'D [26/Oct/2011:14:27:15 +0200] [Job ???] Auto-typing file...',
               'I [26/Oct/2011:14:27:15 +0200] [Job ???] Request file type is application/vnd.cups-banner.',
               'D [26/Oct/2011:14:27:15 +0200] cupsdMarkDirty(----J-)',
               'D [26/Oct/2011:14:27:15 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [26/Oct/2011:14:27:15 +0200] add_job: requesting-user-name="chris"',
               'D [26/Oct/2011:14:27:15 +0200] Adding default job-sheets values "none,none"...',
               'I [26/Oct/2011:14:27:15 +0200] [Job 31] Adding start banner page "none".',
               'D [26/Oct/2011:14:27:15 +0200] cupsdMarkDirty(-----S)',
               'D [26/Oct/2011:14:27:15 +0200] cupsdMarkDirty(----J-)',
               'I [26/Oct/2011:14:27:15 +0200] [Job 31] Adding end banner page "none".',
               'I [26/Oct/2011:14:27:15 +0200] [Job 31] File of type application/vnd.cups-banner queued by "chris".',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] hold_until=0',
               'I [26/Oct/2011:14:27:15 +0200] [Job 31] Queued on "Canon_iP43004" by "chris".',
               'D [26/Oct/2011:14:27:15 +0200] cupsdMarkDirty(----J-)',
               'D [26/Oct/2011:14:27:15 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [26/Oct/2011:14:27:15 +0200] cupsdMarkDirty(-----S)',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] job-sheets=none,none',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] argv[0]="Canon_iP43004"',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] argv[1]="31"',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] argv[2]="chris"',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] argv[3]="Test Page"',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] argv[4]="1"',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] argv[5]="job-uuid=urn:uuid:96c63aaa-fad1-30a8-6a87-c76f58edaf76 job-originating-host-name=localhost time-at-creation=1319632035 time-at-processing=1319632035 AP_D_InputSlot="',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] argv[6]="/var/spool/cups/d00031-001"',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] envp[0]="CUPS_CACHEDIR=/var/cache/cups"',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] envp[1]="CUPS_DATADIR=/usr/share/cups"',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] envp[4]="CUPS_REQUESTROOT=/var/spool/cups"',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] envp[5]="CUPS_SERVERBIN=/usr/lib/cups"',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] envp[6]="CUPS_SERVERROOT=/etc/cups"',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] envp[7]="CUPS_STATEDIR=/var/run/cups"',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] envp[8]="HOME=/var/spool/cups/tmp"',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] envp[10]="SERVER_ADMIN=root@DESKTOP"',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] envp[11]="SOFTWARE=CUPS/1.4.6"',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] envp[12]="TMPDIR=/var/spool/cups/tmp"',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] envp[13]="USER=root"',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] envp[15]="CUPS_ENCRYPTION=IfRequested"',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] envp[16]="IPP_PORT=631"',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] envp[17]="CHARSET=utf-8"',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] envp[18]="LANG=en_IE.UTF-8"',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] envp[19]="PPD=/etc/cups/ppd/Canon_iP43004.ppd"',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] envp[20]="RIP_MAX_CACHE=auto"',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] envp[21]="CONTENT_TYPE=application/vnd.cups-banner"',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] envp[22]="DEVICE_URI=usb://Canon/iP4300"',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] envp[23]="PRINTER_INFO=Canon iP4300via631"',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] envp[24]="PRINTER_LOCATION="',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] envp[25]="PRINTER=Canon_iP43004"',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] envp[26]="CUPS_FILETYPE=document"',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] envp[27]="FINAL_CONTENT_TYPE=printer/Canon_iP43004"',
               'I [26/Oct/2011:14:27:15 +0200] [Job 31] Started filter /usr/lib/cups/filter/bannertops (PID 2327)',
               'I [26/Oct/2011:14:27:15 +0200] [Job 31] Started filter /usr/lib/cups/filter/pstops (PID 2328)',
               'I [26/Oct/2011:14:27:15 +0200] [Job 31] Started filter /usr/lib/cups/filter/pstocanonij (PID 2329)',
               'I [26/Oct/2011:14:27:15 +0200] [Job 31] Started backend /usr/lib/cups/backend/usb (PID 2330)',
               'D [26/Oct/2011:14:27:15 +0200] cupsdMarkDirty(-----S)',
               'D [26/Oct/2011:14:27:15 +0200] Returning IPP successful-ok for Print-Job (ipp://localhost/printers/Canon_iP43004) from localhost',
               'D [26/Oct/2011:14:27:15 +0200] cupsdSetBusyState: Printing jobs and dirty files',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] STATE: +connecting-to-device',
               'D [26/Oct/2011:14:27:15 +0200] cupsdMarkDirty(-----S)',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] Printer using device file "/dev/usblp0"...',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] STATE: -connecting-to-device',
               'D [26/Oct/2011:14:27:15 +0200] cupsdMarkDirty(-----S)',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] backendRunLoop(print_fd=0, device_fd=5, snmp_fd=-1, addr=(nil), use_bc=0, side_cb=0x668230)',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] pstocanonij start.',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] load_banner(filename="/var/spool/cups/d00031-001")',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] Page = 595x842; 10,14 to 586,833',
               'D [26/Oct/2011:14:27:15 +0200] cupsdAcceptClient: 24 from localhost (Domain)',
               'D [26/Oct/2011:14:27:15 +0200] cupsdReadClient: 24 POST / HTTP/1.1',
               'D [26/Oct/2011:14:27:15 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [26/Oct/2011:14:27:15 +0200] cupsdAuthorize: No authentication data provided.',
               'D [26/Oct/2011:14:27:15 +0200] cupsdAcceptClient: 25 from localhost (Domain)',
               'D [26/Oct/2011:14:27:15 +0200] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [26/Oct/2011:14:27:15 +0200] cupsdAuthorize: No authentication data provided.',
               'D [26/Oct/2011:14:27:15 +0200] cupsdReadClient: 24 1.1 Get-Notifications 1',
               'D [26/Oct/2011:14:27:15 +0200] Get-Notifications /',
               'D [26/Oct/2011:14:27:15 +0200] cupsdIsAuthorized: requesting-user-name="chris"',
               'D [26/Oct/2011:14:27:15 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [26/Oct/2011:14:27:15 +0200] cupsdReadClient: 25 1.1 Get-Notifications 1',
               'D [26/Oct/2011:14:27:15 +0200] Get-Notifications /',
               'D [26/Oct/2011:14:27:15 +0200] cupsdIsAuthorized: requesting-user-name="chris"',
               'D [26/Oct/2011:14:27:15 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [26/Oct/2011:14:27:15 +0200] cupsdReadClient: 25 WAITING Closing on EOF',
               'D [26/Oct/2011:14:27:15 +0200] cupsdCloseClient: 25',
               'D [26/Oct/2011:14:27:15 +0200] cupsdSetBusyState: Printing jobs and dirty files',
               'D [26/Oct/2011:14:27:15 +0200] cupsdReadClient: 24 POST / HTTP/1.1',
               'D [26/Oct/2011:14:27:15 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [26/Oct/2011:14:27:15 +0200] cupsdAuthorize: No authentication data provided.',
               'D [26/Oct/2011:14:27:15 +0200] cupsdReadClient: 24 1.1 Get-Job-Attributes 1',
               'D [26/Oct/2011:14:27:15 +0200] Get-Job-Attributes ipp://localhost/jobs/31',
               'D [26/Oct/2011:14:27:15 +0200] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/31) from localhost',
               'D [26/Oct/2011:14:27:15 +0200] cupsdSetBusyState: Printing jobs and dirty files',
               'D [26/Oct/2011:14:27:15 +0200] cupsdAcceptClient: 25 from localhost (Domain)',
               'D [26/Oct/2011:14:27:15 +0200] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [26/Oct/2011:14:27:15 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [26/Oct/2011:14:27:15 +0200] cupsdAuthorize: No authentication data provided.',
               'D [26/Oct/2011:14:27:15 +0200] cupsdReadClient: 25 1.1 Get-Job-Attributes 1',
               'D [26/Oct/2011:14:27:15 +0200] Get-Job-Attributes ipp://localhost/jobs/31',
               'D [26/Oct/2011:14:27:15 +0200] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/31) from localhost',
               'D [26/Oct/2011:14:27:15 +0200] cupsdSetBusyState: Printing jobs and dirty files',
               'D [26/Oct/2011:14:27:15 +0200] cupsdReadClient: 25 WAITING Closing on EOF',
               'D [26/Oct/2011:14:27:15 +0200] cupsdCloseClient: 25',
               'D [26/Oct/2011:14:27:15 +0200] cupsdAcceptClient: 25 from localhost (Domain)',
               'D [26/Oct/2011:14:27:15 +0200] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [26/Oct/2011:14:27:15 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [26/Oct/2011:14:27:15 +0200] cupsdAuthorize: No authentication data provided.',
               'D [26/Oct/2011:14:27:15 +0200] cupsdReadClient: 25 1.1 Get-Job-Attributes 1',
               'D [26/Oct/2011:14:27:15 +0200] Get-Job-Attributes ipp://localhost/jobs/31',
               'D [26/Oct/2011:14:27:15 +0200] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/31) from localhost',
               'D [26/Oct/2011:14:27:15 +0200] cupsdSetBusyState: Printing jobs and dirty files',
               'D [26/Oct/2011:14:27:15 +0200] cupsdReadClient: 15 POST / HTTP/1.1',
               'D [26/Oct/2011:14:27:15 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [26/Oct/2011:14:27:15 +0200] cupsdAuthorize: Authorized as chris using PeerCred',
               'D [26/Oct/2011:14:27:15 +0200] cupsdReadClient: 25 WAITING Closing on EOF',
               'D [26/Oct/2011:14:27:15 +0200] cupsdCloseClient: 25',
               'D [26/Oct/2011:14:27:15 +0200] cupsdReadClient: 15 1.1 Get-Notifications 1',
               'D [26/Oct/2011:14:27:15 +0200] Get-Notifications /',
               'D [26/Oct/2011:14:27:15 +0200] cupsdIsAuthorized: username="chris"',
               'D [26/Oct/2011:14:27:15 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [26/Oct/2011:14:27:15 +0200] cupsdSetBusyState: Printing jobs and dirty files',
               'D [26/Oct/2011:14:27:15 +0200] cupsdAcceptClient: 25 from localhost (Domain)',
               'D [26/Oct/2011:14:27:15 +0200] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [26/Oct/2011:14:27:15 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [26/Oct/2011:14:27:15 +0200] cupsdAuthorize: No authentication data provided.',
               'D [26/Oct/2011:14:27:15 +0200] cupsdReadClient: 25 1.1 Get-Job-Attributes 1',
               'D [26/Oct/2011:14:27:15 +0200] Get-Job-Attributes ipp://localhost/jobs/31',
               'D [26/Oct/2011:14:27:15 +0200] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/31) from localhost',
               'D [26/Oct/2011:14:27:15 +0200] cupsdSetBusyState: Printing jobs and dirty files',
               'D [26/Oct/2011:14:27:15 +0200] cupsdReadClient: 25 WAITING Closing on EOF',
               'D [26/Oct/2011:14:27:15 +0200] cupsdCloseClient: 25',
               'D [26/Oct/2011:14:27:15 +0200] cupsdReadClient: 24 WAITING Closing on EOF',
               'D [26/Oct/2011:14:27:15 +0200] cupsdCloseClient: 24',
               'D [26/Oct/2011:14:27:15 +0200] cupsdAcceptClient: 24 from localhost (Domain)',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] Page = 595x842; 10,14 to 586,833',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] slow_collate=0, slow_duplex=0, slow_order=0',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] Before copy_comments - %!PS-Adobe-3.0',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] %!PS-Adobe-3.0',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] %%BoundingBox: 10 14 586 833',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] %cupsRotation: 0',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] %%Creator: bannertops/CUPS v1.4.6',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] %%CreationDate: Wed 26 Oct 2011 14:27:15 CEST',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] %%LanguageLevel: 2',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] %%DocumentData: Clean7Bit',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] %%Title: (Test Page)',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] %%For: (chris)',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] %%Pages: 1',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] %%DocumentSuppliedResources: font Monospace',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] %%+ font Monospace-Bold',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] %%+ font Monospace-BoldOblique',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] %%+ font Monospace-Oblique',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] %%EndComments',
               'D [26/Oct/2011:14:27:15 +0200] [Job 31] Before copy_prolog - %%BeginProlog',
               'D [26/Oct/2011:14:27:15 +0200] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [26/Oct/2011:14:27:15 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [26/Oct/2011:14:27:15 +0200] cupsdAuthorize: No authentication data provided.',
               'D [26/Oct/2011:14:27:15 +0200] cupsdReadClient: 13 1.1 CUPS-Get-Printers 1',
               'D [26/Oct/2011:14:27:15 +0200] CUPS-Get-Printers',
               'D [26/Oct/2011:14:27:15 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [26/Oct/2011:14:27:15 +0200] cupsdSetBusyState: Printing jobs and dirty files',
               'D [26/Oct/2011:14:27:15 +0200] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [26/Oct/2011:14:27:15 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [26/Oct/2011:14:27:15 +0200] cupsdAuthorize: No authentication data provided.',
               'D [26/Oct/2011:14:27:15 +0200] cupsdReadClient: 13 1.1 CUPS-Get-Classes 1',
               'D [26/Oct/2011:14:27:15 +0200] CUPS-Get-Classes',
               'D [26/Oct/2011:14:27:15 +0200] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [26/Oct/2011:14:27:15 +0200] cupsdSetBusyState: Printing jobs and dirty files',
               'D [26/Oct/2011:14:27:15 +0200] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [26/Oct/2011:14:27:15 +0200] cupsdSetBusyState: Active clients, printing jobs, and dirty files',
               'D [26/Oct/2011:14:27:15 +0200] cupsdAuthorize: No authentication data provided.',
               'D [26/Oct/2011:14:27:15 +0200] cupsdReadClient: 13 1.1 CUPS-Get-Default 1',
               'D [26/Oct/2011:14:27:15 +0200] CUPS-Get-Default',
               'D [26/Oct/2011:14:27:15 +0200] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [26/Oct/2011:14:27:15 +0200] cupsdSetBusyState: Printing jobs and dirty files',
               'D [26/Oct/2011:14:27:16 +0200] [Job 31] PNG image: 128x128x8, color_type=6 (RGB+ALPHA)',
               'D [26/Oct/2011:14:27:16 +0200] [Job 31] PNG image: 192x128x8, color_type=2 (RGB)',
               'D [26/Oct/2011:14:27:16 +0200] [Job 31] Before copy_setup - %%Page: coverpage 1',
               'D [26/Oct/2011:14:27:16 +0200] [Job 31] Before page loop - %%Page: coverpage 1',
               'D [26/Oct/2011:14:27:16 +0200] [Job 31] Copying page 1...',
               'D [26/Oct/2011:14:27:16 +0200] [Job 31] pagew = 576.0, pagel = 819.2',
               'D [26/Oct/2011:14:27:16 +0200] [Job 31] bboxx = 0, bboxy = 0, bboxw = 595, bboxl = 842',
               'D [26/Oct/2011:14:27:16 +0200] [Job 31] PageLeft = 9.6, PageRight = 585.6',
               'D [26/Oct/2011:14:27:16 +0200] [Job 31] PageTop = 833.4, PageBottom = 14.2',
               'D [26/Oct/2011:14:27:16 +0200] [Job 31] PageWidth = 595.0, PageLength = 842.0',
               'D [26/Oct/2011:14:27:19 +0200] PID 2327 (/usr/lib/cups/filter/bannertops) exited with no errors.',
               'D [26/Oct/2011:14:27:19 +0200] [Job 31] Wrote 1 pages...',
               'D [26/Oct/2011:14:27:19 +0200] PID 2328 (/usr/lib/cups/filter/pstops) exited with no errors.',
               'D [26/Oct/2011:14:27:21 +0200] [Job 31] pstocanonij: /usr/bin/gs -r600 -g4958x7016 -q -dNOPROMPT -dSAFER -sDEVICE=ppmraw -sOutputFile=- -| /usr/local/bin/cifip4300 --imageres 600 --papersize a4 --media plain --quality 3 --bbox 9,14,585,834',
               'D [26/Oct/2011:14:27:22 +0200] [Job 31] /usr/local/bin/cifip4300: error while loading shared libraries: libtiff.so.3: cannot open shared object file: No such file or directory',
               'D [26/Oct/2011:14:27:22 +0200] [Job 1] Unloading...',
               'D [26/Oct/2011:14:27:22 +0200] [Job 7] Unloading...',
               'D [26/Oct/2011:14:27:22 +0200] [Job 10] Unloading...',
               'D [26/Oct/2011:14:27:22 +0200] [Job 11] Unloading...',
               'D [26/Oct/2011:14:27:22 +0200] [Job 13] Unloading...',
               'D [26/Oct/2011:14:27:22 +0200] [Job 14] Unloading...',
               'D [26/Oct/2011:14:27:22 +0200] [Job 15] Unloading...',
               'D [26/Oct/2011:14:27:22 +0200] [Job 16] Unloading...',
               'D [26/Oct/2011:14:27:22 +0200] [Job 17] Unloading...',
               'D [26/Oct/2011:14:27:22 +0200] [Job 19] Unloading...',
               'D [26/Oct/2011:14:27:22 +0200] [Job 20] Unloading...',
               'D [26/Oct/2011:14:27:22 +0200] [Job 21] Unloading...',
               'D [26/Oct/2011:14:27:22 +0200] [Job 22] Unloading...',
               'D [26/Oct/2011:14:27:22 +0200] [Job 23] Unloading...',
               'D [26/Oct/2011:14:27:22 +0200] [Job 24] Unloading...',
               'D [26/Oct/2011:14:27:22 +0200] [Job 25] Unloading...',
               'D [26/Oct/2011:14:27:22 +0200] [Job 26] Unloading...',
               'D [26/Oct/2011:14:27:22 +0200] [Job 27] Unloading...',
               'D [26/Oct/2011:14:27:22 +0200] [Job 28] Unloading...',
               'D [26/Oct/2011:14:27:22 +0200] [Job 29] Unloading...',
               'D [26/Oct/2011:14:27:22 +0200] [Job 30] Unloading...',
               'D [26/Oct/2011:14:27:24 +0200] PID 2329 (/usr/lib/cups/filter/pstocanonij) exited with no errors.',
               'D [26/Oct/2011:14:27:24 +0200] PID 2330 (/usr/lib/cups/backend/usb) exited with no errors.',
               'D [26/Oct/2011:14:27:24 +0200] cupsdMarkDirty(-----S)',
               'I [26/Oct/2011:14:27:24 +0200] [Job 31] Job completed.',
               'D [26/Oct/2011:14:27:24 +0200] cupsdMarkDirty(----J-)',
               'D [26/Oct/2011:14:27:24 +0200] cupsdMarkDirty(-----S)',
               'D [26/Oct/2011:14:27:24 +0200] cupsdAcceptClient: 23 from localhost (Domain)',
               'D [26/Oct/2011:14:27:24 +0200] cupsdReadClient: 23 POST / HTTP/1.1',
               'D [26/Oct/2011:14:27:24 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [26/Oct/2011:14:27:24 +0200] cupsdAuthorize: No authentication data provided.',
               'D [26/Oct/2011:14:27:24 +0200] cupsdReadClient: 23 1.1 Get-Notifications 1',
               'D [26/Oct/2011:14:27:24 +0200] Get-Notifications /',
               'D [26/Oct/2011:14:27:24 +0200] cupsdIsAuthorized: requesting-user-name="chris"',
               'D [26/Oct/2011:14:27:24 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [26/Oct/2011:14:27:24 +0200] cupsdSetBusyState: Dirty files',
               'D [26/Oct/2011:14:27:24 +0200] cupsdAcceptClient: 25 from localhost (Domain)',
               'D [26/Oct/2011:14:27:24 +0200] cupsdAcceptClient: 26 from localhost (Domain)',
               'D [26/Oct/2011:14:27:24 +0200] cupsdReadClient: 25 POST / HTTP/1.1',
               'D [26/Oct/2011:14:27:24 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [26/Oct/2011:14:27:24 +0200] cupsdAuthorize: No authentication data provided.',
               'D [26/Oct/2011:14:27:24 +0200] cupsdReadClient: 26 POST / HTTP/1.1',
               'D [26/Oct/2011:14:27:24 +0200] cupsdAuthorize: No authentication data provided.',
               'D [26/Oct/2011:14:27:24 +0200] cupsdReadClient: 26 1.1 Get-Printer-Attributes 1',
               'D [26/Oct/2011:14:27:24 +0200] Get-Printer-Attributes ipp://DESKTOP:631/printers/Canon_iP43004',
               'D [26/Oct/2011:14:27:24 +0200] Returning IPP successful-ok for Get-Printer-Attributes (ipp://DESKTOP:631/printers/Canon_iP43004) from localhost',
               'D [26/Oct/2011:14:27:24 +0200] cupsdReadClient: 25 1.1 Get-Notifications 1',
               'D [26/Oct/2011:14:27:24 +0200] Get-Notifications /',
               'D [26/Oct/2011:14:27:24 +0200] cupsdIsAuthorized: requesting-user-name="chris"',
               'D [26/Oct/2011:14:27:24 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [26/Oct/2011:14:27:24 +0200] cupsdSetBusyState: Dirty files',
               'D [26/Oct/2011:14:27:24 +0200] cupsdReadClient: 25 WAITING Closing on EOF',
               'D [26/Oct/2011:14:27:24 +0200] cupsdCloseClient: 25',
               'D [26/Oct/2011:14:27:24 +0200] cupsdReadClient: 15 POST / HTTP/1.1',
               'D [26/Oct/2011:14:27:24 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [26/Oct/2011:14:27:24 +0200] cupsdAuthorize: Authorized as chris using PeerCred',
               'D [26/Oct/2011:14:27:24 +0200] cupsdReadClient: 15 1.1 Get-Notifications 1',
               'D [26/Oct/2011:14:27:24 +0200] Get-Notifications /',
               'D [26/Oct/2011:14:27:24 +0200] cupsdIsAuthorized: username="chris"',
               'D [26/Oct/2011:14:27:24 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [26/Oct/2011:14:27:24 +0200] cupsdSetBusyState: Dirty files',
               'D [26/Oct/2011:14:27:24 +0200] cupsdReadClient: 23 WAITING Closing on EOF',
               'D [26/Oct/2011:14:27:24 +0200] cupsdCloseClient: 23',
               'D [26/Oct/2011:14:27:25 +0200] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [26/Oct/2011:14:27:25 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [26/Oct/2011:14:27:25 +0200] cupsdAuthorize: No authentication data provided.',
               'D [26/Oct/2011:14:27:25 +0200] [Job 31] Unloading...',
               'D [26/Oct/2011:14:27:25 +0200] cupsdReadClient: 13 1.1 CUPS-Get-Printers 1',
               'D [26/Oct/2011:14:27:25 +0200] CUPS-Get-Printers',
               'D [26/Oct/2011:14:27:25 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [26/Oct/2011:14:27:25 +0200] cupsdSetBusyState: Dirty files',
               'D [26/Oct/2011:14:27:25 +0200] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [26/Oct/2011:14:27:25 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [26/Oct/2011:14:27:25 +0200] cupsdAuthorize: No authentication data provided.',
               'D [26/Oct/2011:14:27:25 +0200] cupsdReadClient: 13 1.1 CUPS-Get-Classes 1',
               'D [26/Oct/2011:14:27:25 +0200] CUPS-Get-Classes',
               'D [26/Oct/2011:14:27:25 +0200] Returning IPP successful-ok for CUPS-Get-Classes (no URI) from localhost',
               'D [26/Oct/2011:14:27:25 +0200] cupsdSetBusyState: Dirty files',
               'D [26/Oct/2011:14:27:25 +0200] cupsdReadClient: 13 POST / HTTP/1.1',
               'D [26/Oct/2011:14:27:25 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [26/Oct/2011:14:27:25 +0200] cupsdAuthorize: No authentication data provided.',
               'D [26/Oct/2011:14:27:25 +0200] cupsdReadClient: 13 1.1 CUPS-Get-Default 1',
               'D [26/Oct/2011:14:27:25 +0200] CUPS-Get-Default',
               'D [26/Oct/2011:14:27:25 +0200] Returning IPP successful-ok for CUPS-Get-Default (no URI) from localhost',
               'D [26/Oct/2011:14:27:25 +0200] cupsdSetBusyState: Dirty files',
               'I [26/Oct/2011:14:27:46 +0200] Saving job cache file "/var/cache/cups/job.cache"...',
               'I [26/Oct/2011:14:27:46 +0200] Saving subscriptions.conf...',
               'D [26/Oct/2011:14:27:46 +0200] cupsdSetBusyState: Not busy',
               'D [26/Oct/2011:14:28:06 +0200] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [26/Oct/2011:14:28:06 +0200] cupsdCloseClient: 22',
               'D [26/Oct/2011:14:28:06 +0200] cupsdNetIFUpdate: "lo" = localhost:631',
               'D [26/Oct/2011:14:28:06 +0200] cupsdNetIFUpdate: "wlan0" = 192.168.1.2:631',
               'D [26/Oct/2011:14:28:06 +0200] cupsdNetIFUpdate: "lo" = localhost:631',
               'D [26/Oct/2011:14:28:06 +0200] cupsdNetIFUpdate: "wlan0" = [v1.fe80::21f:1fff:fe05:e56e+wlan0]:631',
               'D [26/Oct/2011:14:28:06 +0200] Report: clients=9',
               'D [26/Oct/2011:14:28:06 +0200] Report: jobs=22',
               'D [26/Oct/2011:14:28:06 +0200] Report: jobs-active=0',
               'D [26/Oct/2011:14:28:06 +0200] Report: printers=2',
               'D [26/Oct/2011:14:28:06 +0200] Report: printers-implicit=0',
               'D [26/Oct/2011:14:28:06 +0200] Report: stringpool-string-count=73233',
               'D [26/Oct/2011:14:28:06 +0200] Report: stringpool-alloc-bytes=15624',
               'D [26/Oct/2011:14:28:06 +0200] Report: stringpool-total-bytes=1359672',
               'D [26/Oct/2011:14:28:06 +0200] cupsdAcceptClient: 22 from localhost (Domain)',
               'D [26/Oct/2011:14:28:06 +0200] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [26/Oct/2011:14:28:06 +0200] cupsdSetBusyState: Active clients',
               'D [26/Oct/2011:14:28:06 +0200] cupsdAuthorize: No authentication data provided.',
               'D [26/Oct/2011:14:28:06 +0200] cupsdReadClient: 22 1.1 Create-Printer-Subscription 1',
               'D [26/Oct/2011:14:28:06 +0200] Create-Printer-Subscription /',
               'D [26/Oct/2011:14:28:06 +0200] cupsdCreateSubscription(con=0x21ae0f88(22), uri="/")',
               'D [26/Oct/2011:14:28:06 +0200] pullmethod="ippget"',
               'D [26/Oct/2011:14:28:06 +0200] notify-lease-duration=86400',
               'D [26/Oct/2011:14:28:06 +0200] notify-time-interval=0',
               'D [26/Oct/2011:14:28:06 +0200] cupsdAddSubscription(mask=1798f, dest=(nil)(), job=(nil)(0), uri="(null)")',
               'D [26/Oct/2011:14:28:06 +0200] Added subscription 308 for server',
               'D [26/Oct/2011:14:28:06 +0200] cupsdMarkDirty(-----S)',
               'D [26/Oct/2011:14:28:06 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [26/Oct/2011:14:28:06 +0200] Returning IPP successful-ok for Create-Printer-Subscription (/) from localhost',
               'D [26/Oct/2011:14:28:06 +0200] cupsdSetBusyState: Dirty files',
               'D [26/Oct/2011:14:28:06 +0200] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [26/Oct/2011:14:28:06 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [26/Oct/2011:14:28:06 +0200] cupsdAuthorize: No authentication data provided.',
               'D [26/Oct/2011:14:28:06 +0200] cupsdReadClient: 22 1.1 CUPS-Get-Printers 1',
               'D [26/Oct/2011:14:28:06 +0200] CUPS-Get-Printers',
               'D [26/Oct/2011:14:28:06 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [26/Oct/2011:14:28:06 +0200] cupsdSetBusyState: Dirty files',
               'D [26/Oct/2011:14:28:06 +0200] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [26/Oct/2011:14:28:06 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [26/Oct/2011:14:28:06 +0200] cupsdAuthorize: No authentication data provided.',
               'D [26/Oct/2011:14:28:06 +0200] cupsdReadClient: 22 1.1 CUPS-Get-Printers 1',
               'D [26/Oct/2011:14:28:06 +0200] CUPS-Get-Printers',
               'D [26/Oct/2011:14:28:06 +0200] Returning IPP successful-ok for CUPS-Get-Printers (no URI) from localhost',
               'D [26/Oct/2011:14:28:06 +0200] cupsdSetBusyState: Dirty files',
               'D [26/Oct/2011:14:28:06 +0200] cupsdAcceptClient: 23 from localhost (Domain)',
               'D [26/Oct/2011:14:28:06 +0200] cupsdReadClient: 23 POST / HTTP/1.1',
               'D [26/Oct/2011:14:28:06 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [26/Oct/2011:14:28:06 +0200] cupsdAuthorize: No authentication data provided.',
               'D [26/Oct/2011:14:28:06 +0200] cupsdReadClient: 23 1.1 Get-Printer-Attributes 1',
               'D [26/Oct/2011:14:28:06 +0200] Get-Printer-Attributes ipp://localhost/printers/Canon_iP43004',
               'D [26/Oct/2011:14:28:06 +0200] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/Canon_iP43004) from localhost',
               'D [26/Oct/2011:14:28:06 +0200] cupsdSetBusyState: Dirty files',
               'D [26/Oct/2011:14:28:06 +0200] cupsdReadClient: 23 WAITING Closing on EOF',
               'D [26/Oct/2011:14:28:06 +0200] cupsdCloseClient: 23',
               'D [26/Oct/2011:14:28:06 +0200] cupsdAcceptClient: 23 from localhost (Domain)',
               'D [26/Oct/2011:14:28:06 +0200] cupsdReadClient: 23 POST / HTTP/1.1',
               'D [26/Oct/2011:14:28:06 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [26/Oct/2011:14:28:06 +0200] cupsdAuthorize: No authentication data provided.',
               'D [26/Oct/2011:14:28:06 +0200] cupsdReadClient: 23 1.1 Get-Printer-Attributes 1',
               'D [26/Oct/2011:14:28:06 +0200] Get-Printer-Attributes ipp://localhost/printers/iP43003cups',
               'D [26/Oct/2011:14:28:06 +0200] Returning IPP successful-ok for Get-Printer-Attributes (ipp://localhost/printers/iP43003cups) from localhost',
               'D [26/Oct/2011:14:28:06 +0200] cupsdSetBusyState: Dirty files',
               'D [26/Oct/2011:14:28:06 +0200] cupsdReadClient: 23 WAITING Closing on EOF',
               'D [26/Oct/2011:14:28:06 +0200] cupsdCloseClient: 23',
               'D [26/Oct/2011:14:28:06 +0200] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [26/Oct/2011:14:28:06 +0200] cupsdCloseClient: 22',
               'D [26/Oct/2011:14:28:06 +0200] cupsdAcceptClient: 22 from localhost (Domain)',
               'D [26/Oct/2011:14:28:06 +0200] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [26/Oct/2011:14:28:06 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [26/Oct/2011:14:28:06 +0200] cupsdAuthorize: No authentication data provided.',
               'D [26/Oct/2011:14:28:06 +0200] cupsdReadClient: 22 1.1 Get-Jobs 1',
               'D [26/Oct/2011:14:28:06 +0200] Get-Jobs ipp://localhost/printers/',
               'D [26/Oct/2011:14:28:06 +0200] Returning IPP successful-ok for Get-Jobs (ipp://localhost/printers/) from localhost',
               'D [26/Oct/2011:14:28:06 +0200] cupsdSetBusyState: Dirty files',
               'D [26/Oct/2011:14:28:06 +0200] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [26/Oct/2011:14:28:06 +0200] cupsdCloseClient: 22',
               'D [26/Oct/2011:14:28:07 +0200] cupsdAcceptClient: 22 from localhost (Domain)',
               'D [26/Oct/2011:14:28:07 +0200] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [26/Oct/2011:14:28:07 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [26/Oct/2011:14:28:07 +0200] cupsdAuthorize: No authentication data provided.',
               'D [26/Oct/2011:14:28:07 +0200] cupsdReadClient: 22 1.1 Get-Notifications 1',
               'D [26/Oct/2011:14:28:07 +0200] Get-Notifications /',
               'D [26/Oct/2011:14:28:07 +0200] cupsdIsAuthorized: requesting-user-name="chris"',
               'D [26/Oct/2011:14:28:07 +0200] Returning IPP successful-ok for Get-Notifications (/) from localhost',
               'D [26/Oct/2011:14:28:07 +0200] cupsdSetBusyState: Dirty files',
               'D [26/Oct/2011:14:28:07 +0200] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [26/Oct/2011:14:28:07 +0200] cupsdCloseClient: 22',
               'D [26/Oct/2011:14:28:09 +0200] cupsdAcceptClient: 22 from localhost (Domain)',
               'D [26/Oct/2011:14:28:09 +0200] cupsdReadClient: 22 POST / HTTP/1.1',
               'D [26/Oct/2011:14:28:09 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [26/Oct/2011:14:28:09 +0200] cupsdAuthorize: No authentication data provided.',
               'D [26/Oct/2011:14:28:09 +0200] cupsdReadClient: 22 1.1 Cancel-Subscription 1',
               'D [26/Oct/2011:14:28:09 +0200] Cancel-Subscription /',
               'D [26/Oct/2011:14:28:09 +0200] cupsdIsAuthorized: requesting-user-name="chris"',
               'D [26/Oct/2011:14:28:09 +0200] cupsdMarkDirty(-----S)',
               'D [26/Oct/2011:14:28:09 +0200] Returning IPP successful-ok for Cancel-Subscription (/) from localhost',
               'D [26/Oct/2011:14:28:09 +0200] cupsdSetBusyState: Dirty files',
               'D [26/Oct/2011:14:28:09 +0200] cupsdReadClient: 22 WAITING Closing on EOF',
               'D [26/Oct/2011:14:28:09 +0200] cupsdCloseClient: 22',
               'D [26/Oct/2011:14:28:19 +0200] cupsdReadClient: 15 POST / HTTP/1.1',
               'D [26/Oct/2011:14:28:19 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [26/Oct/2011:14:28:19 +0200] cupsdAuthorize: Authorized as chris using PeerCred',
               'D [26/Oct/2011:14:28:19 +0200] cupsdReadClient: 15 1.1 Get-Job-Attributes 1',
               'D [26/Oct/2011:14:28:19 +0200] Get-Job-Attributes ipp://localhost/jobs/31',
               'D [26/Oct/2011:14:28:19 +0200] [Job 31] Loading attributes...',
               'D [26/Oct/2011:14:28:19 +0200] Returning IPP successful-ok for Get-Job-Attributes (ipp://localhost/jobs/31) from localhost',
               'D [26/Oct/2011:14:28:19 +0200] cupsdSetBusyState: Dirty files',
               'D [26/Oct/2011:14:28:19 +0200] cupsdReadClient: 15 POST / HTTP/1.1',
               'D [26/Oct/2011:14:28:19 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [26/Oct/2011:14:28:19 +0200] cupsdAuthorize: Authorized as chris using PeerCred',
               'D [26/Oct/2011:14:28:19 +0200] cupsdReadClient: 15 1.1 Cancel-Subscription 1',
               'D [26/Oct/2011:14:28:19 +0200] Cancel-Subscription /',
               'D [26/Oct/2011:14:28:19 +0200] cupsdIsAuthorized: username="chris"',
               'D [26/Oct/2011:14:28:19 +0200] cupsdMarkDirty(-----S)',
               'D [26/Oct/2011:14:28:19 +0200] Returning IPP successful-ok for Cancel-Subscription (/) from localhost',
               'D [26/Oct/2011:14:28:19 +0200] cupsdSetBusyState: Dirty files',
               'D [26/Oct/2011:14:28:19 +0200] cupsdAcceptClient: 22 from localhost (Domain)',
               'D [26/Oct/2011:14:28:19 +0200] cupsdReadClient: 22 GET /admin/log/error_log HTTP/1.1',
               'D [26/Oct/2011:14:28:19 +0200] cupsdSetBusyState: Active clients and dirty files',
               'D [26/Oct/2011:14:28:19 +0200] cupsdAuthorize: No authentication data provided.']}
Page 10 (Locale issues):
{'printer_page_size': u'A4',
 'system_locale_lang': None,
 'user_locale_ctype': 'en_IE',
 'user_locale_messages': 'en_IE'}
```
I do notice an error at:
 
```
'D [26/Oct/2011:14:27:22 +0200] [Job 31] /usr/local/bin/cifip4300: error while loading shared libraries: libtiff.so.3: cannot open shared object file: No such file or directory'
```

Is that significant?

---

### Post by 2CV67 on 2011-10-26
Hey - its working! :cool:

Details soon...

---

### Post by jnorthr on 2011-10-26
Thank you for the output of lsusb. We can see from this info. that your 4300 printer is seen by the kernel:
Bus 001 Device 006: ID 04a9:10b6 Canon, Inc. PIXMA iP4300 Printer

That was a wonderful bit of work finding that debugging tool. Yes, it all goes a long way to finding the root cause of your printer issues.

I'll look over the details this afternoon. Hopefully will have a few more ideas tonite.

---

### Post by jnorthr on 2011-10-26
Super :popcorn:

guessing that we were missing credentials for chris using peercred. Since cups is a web server that just happens to serve print files, it normally needs a set of credentials to authorise the flow of data from your PC to the printer, as the ip4300 is not .really. directly connected, it is done by normal i/p communicaations like we use over the internet, hence the need for addressing names like localhost:631 which just tells cups to look on your PC port 631 for printer data to arrive. Does that make any sense ?

---

### Post by 2CV67 on 2011-10-26
How I dunnit (with more than a little help!).

As previously mentioned, there is a Troubleshooter at: System > Administration > Printing > Help > Troubleshoot.

Following the instructions, to print a test page, gave no result & "Sorry! No obvious solution" but no explanation.
But you do get to "Save" the test log.
In my test log, I found a line: 
```
/usr/local/bin/cifip4300: error while loading shared libraries: libtiff.so.3: cannot open shared object file: No such file or directory
```

Googling that, produced several tips about making a soft link like this:
```
sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3
```

I tried that with no success.

Then I looked for my libtiff.so* files & found I had libtiff.so.4 but in usr/lib/i386-linux-gnu folder, not in usr/lib.
So I adapted the advice to:
```
sudo ln -s /usr/lib/i386-linux-gnu/libtiff.so.4 /usr/lib/i386-linux-gnu/libtiff.so.3
```
But still no print...

The troubleshoot file looked just the same.
But it wasn't.
It now said:
```
/usr/local/bin/cifip4300: error while loading shared libraries: libpng.so.3: cannot open shared object file: No such file or directory
```

Now I looked for libpng.so* & found I had /usr/lib/i386-linux-gnu/libpng.so & libpng12.so
So I made a new soft link libpng.so.3
```
sudo ln -s /usr/lib/i386-linux-gnu/libpng.so /usr/lib/i386-linux-gnu/libpng.so.3
```

And that works!

I now notice that erlander's iP4300 Install Guide mentions the problem of libtiff.so.3 & libpng.so.3 but shows them in user/lib folder, which is not the case for me.
He also mentions libxml, so maybe there is more joy ahead.
Wonder what changed, & why?
Who to shoot? (figuratively, of course!)
Has everybody else got this working OK already?

So I am happy to have the printer working & very grateful for all the suggestions, but perplexed as to why all this work has been necessary.

Thanks all!

---

### Post by kurt18947 on 2011-10-26
2CV67, if it's any consolation 11.10 caused problems with my Brother as well.  In my case the problem was documented but was a case of misplaced files.  Something obviously changed in 11.10 re printer installation. I'm glad you were able to sleuth out and solve your problem.

---

### Post by jnorthr on 2011-10-26
suspect we've all learned a lot from this. When someone else has problems with their cannon printer, we'll just point them to our resident guru - you :KS

---

### Post by 2CV67 on 2011-10-27
I have not marked this thread [SOLVED] yet, as there are still some details missing.

One important point is Resolution.

The Canon driver now offers me 600/1200/2400/4800dpi resolutions & High/Normal/Standard/Economy qualities.
Sounds good!

I tried 600-Normal & 1200-High & they work OK.
1200-High prints the Printer Test IEAJ051.pdf better than 600-Normal.

2400 & 4800 don't work yet though.
Jobs appear in the Job List then disappear as "completed" & the printer blinks once or twice, but that's all.

I tried printing at 600 & 4800, then wading through the huge files in /var/log/cups/error-log to compare good & bad runs.
This is where it seems to go wrong:

D [27/Oct/2011:15:08:46 +0200] cupsdSetBusyState: Printing jobs and dirty files
D [27/Oct/2011:15:08:48 +0200] [Job 50] Read 174 bytes of print data...
D [27/Oct/2011:15:08:48 +0200] [Job 50] Wrote 174 bytes of print data...
D [27/Oct/2011:15:08:48 +0200] [Job 50] CIF COMMAND ERROR :memory allocate Error!
D [27/Oct/2011:15:08:48 +0200] [Job 50] Error in ppm_image_raster
D [27/Oct/2011:15:08:48 +0200] [Job 50] err in bjf_image_read_raster
D [27/Oct/2011:15:08:48 +0200] [Job 50] Read 14 bytes of print data...
D [27/Oct/2011:15:08:48 +0200] [Job 50] Wrote 14 bytes of print data...
D [27/Oct/2011:15:08:48 +0200] PID 3303 (/usr/lib/cups/filter/pstocanonij) exited with no errors.
D [27/Oct/2011:15:08:48 +0200] PID 3304 (/usr/lib/cups/backend/usb) exited with no errors.
D [27/Oct/2011:15:08:48 +0200] cupsdMarkDirty(-----S)
I [27/Oct/2011:15:08:48 +0200] [Job 50] Job completed.

CIF COMMAND ERROR :memory allocate Error!.....

Googling has not found anything on that so far.

Any ideas?

---

### Post by 2CV67 on 2011-10-31
OK - I suppose I should call this [SOLVED] & keep the resolution questions on the other thread here:

[http://ubuntuforums.org/showthread.php?t=916648](http://ubuntuforums.org/showthread.php?t=916648)

---

