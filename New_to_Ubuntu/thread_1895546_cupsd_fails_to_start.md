---
title: "cupsd fails to start"
date: 2011-12-15
forum: New to Ubuntu
---

### Post by elorden on 2011-12-15
The cups deamon fails to start at reboot.  I started looking into this because the printing application gave the message "Printing service not available.  Start the service on this computer or connect to another server."  The "Start Service" button was grayed out and not selectable. 

So, I set the logging to debug2 in the cupsd.conf file.  I rebooted and below are the last 100 lines of the log.  If anyone can help me, I would appreciate it.  

elorden

tail of log:

d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: application/octet-stream needs 2 filters
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: application/openofficeps needs 4 filters
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: application/pdf needs 3 filters
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: application/postscript needs 3 filters
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: application/rss+xml not supported
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: application/vnd.adobe-reader-postscript needs 2 filters
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: application/vnd.cups-banner needs 4 filters
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: application/vnd.cups-command not supported
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: application/vnd.cups-form not supported
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: application/vnd.cups-pdf needs 2 filters
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: application/vnd.cups-postscript needs 1 filters
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: application/vnd.cups-ppd not supported
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: application/vnd.cups-raster needs 1 filters
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: application/vnd.cups-raw needs 1 filters
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: application/vnd.hp-hpgl not supported
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: application/x-cshell needs 3 filters
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: application/x-csource needs 3 filters
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: application/x-perl needs 3 filters
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: application/x-shell needs 3 filters
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: image/gif needs 2 filters
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: image/jpeg needs 2 filters
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: image/png needs 2 filters
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: image/pwg-raster not supported
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: image/tiff needs 2 filters
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: image/x-alias not supported
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: image/x-bitmap needs 2 filters
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: image/x-icon not supported
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: image/x-photocd needs 2 filters
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: image/x-portable-anymap needs 2 filters
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: image/x-portable-bitmap needs 2 filters
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: image/x-portable-graymap needs 2 filters
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: image/x-portable-pixmap needs 2 filters
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: image/x-sgi-rgb needs 2 filters
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: image/x-sun-raster needs 2 filters
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: image/x-xbitmap needs 2 filters
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: image/x-xpixmap needs 2 filters
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: image/x-xwindowdump needs 2 filters
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: text/css needs 4 filters
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: text/html needs 3 filters
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: text/plain needs 3 filters
d [14/Dec/2011:23:56:47 -0600] add_printer_formats: Lexmark-5600-6600-Series: 32 supported types
D [14/Dec/2011:23:56:47 -0600] Calling DeleteDevice(cups-Lexmark-5600-6600-Series)
D [14/Dec/2011:23:56:47 -0600] failed to DeleteDevice: org.freedesktop.DBus.Error.InvalidArgs:Type of message, `(s)', does not match expected type `(o)'
D [14/Dec/2011:23:56:47 -0600] Using profile id of Lexmark-5600-6600-Series-Gray..
D [14/Dec/2011:23:56:47 -0600] Calling CreateProfile(Lexmark-5600-6600-Series-Gray..,temp)
D [14/Dec/2011:23:56:47 -0600] created profile /org/freedesktop/ColorManager/profiles/Lexmark_5600_6600_Series_Gray__
D [14/Dec/2011:23:56:47 -0600] Using profile id of Lexmark-5600-6600-Series-RGB..
D [14/Dec/2011:23:56:47 -0600] Calling CreateProfile(Lexmark-5600-6600-Series-RGB..,temp)
D [14/Dec/2011:23:56:47 -0600] created profile /org/freedesktop/ColorManager/profiles/Lexmark_5600_6600_Series_RGB__
I [14/Dec/2011:23:56:47 -0600] Registering ICC color profiles for "Lexmark-5600-6600-Series"
D [14/Dec/2011:23:56:47 -0600] Calling CreateDevice(cups-Lexmark-5600-6600-Series,temp)
D [14/Dec/2011:23:56:47 -0600] created device /org/freedesktop/ColorManager/devices/cups_Lexmark_5600_6600_Series
D [14/Dec/2011:23:56:47 -0600] Calling /org/freedesktop/ColorManager/devices/cups_Lexmark_5600_6600_Series:AddProfile(/org/freedesktop/ColorManager/profiles/Lexmark_5600_6600_Series_Gray__) [soft]
D [14/Dec/2011:23:56:47 -0600] Calling /org/freedesktop/ColorManager/devices/cups_Lexmark_5600_6600_Series:AddProfile(/org/freedesktop/ColorManager/profiles/Lexmark_5600_6600_Series_RGB__) [soft]
D [14/Dec/2011:23:56:47 -0600] cupsdRegisterPrinter(p=0xb7e15c08(Lexmark-5600-6600-Series))
D [14/Dec/2011:23:56:47 -0600] cupsdLoadRemoteCache: Not loading remote cache.
I [14/Dec/2011:23:56:47 -0600] Generating printcap /var/run/cups/printcap...
D [14/Dec/2011:23:56:47 -0600] Scanning /var/spool/cups for jobs...
D [14/Dec/2011:23:56:47 -0600] [Job 2] Loading attributes...
D [14/Dec/2011:23:56:47 -0600] [Job 2] Unloading...
D [14/Dec/2011:23:56:47 -0600] [Job 10] Loading attributes...
D [14/Dec/2011:23:56:47 -0600] [Job 10] Unloading...
D [14/Dec/2011:23:56:47 -0600] [Job 1] Loading attributes...
D [14/Dec/2011:23:56:47 -0600] [Job 1] Unloading...
D [14/Dec/2011:23:56:47 -0600] [Job 3] Loading attributes...
D [14/Dec/2011:23:56:47 -0600] [Job 3] Unloading...
D [14/Dec/2011:23:56:47 -0600] [Job 4] Loading attributes...
D [14/Dec/2011:23:56:47 -0600] [Job 4] Unloading...
D [14/Dec/2011:23:56:47 -0600] [Job 9] Loading attributes...
D [14/Dec/2011:23:56:47 -0600] [Job 9] Unloading...
D [14/Dec/2011:23:56:47 -0600] [Job 6] Loading attributes...
D [14/Dec/2011:23:56:47 -0600] [Job 6] Unloading...
D [14/Dec/2011:23:56:47 -0600] [Job 7] Loading attributes...
D [14/Dec/2011:23:56:47 -0600] [Job 7] Unloading...
D [14/Dec/2011:23:56:47 -0600] [Job 8] Loading attributes...
D [14/Dec/2011:23:56:47 -0600] [Job 8] Unloading...
D [14/Dec/2011:23:56:47 -0600] [Job 5] Loading attributes...
D [14/Dec/2011:23:56:47 -0600] [Job 5] Unloading...
I [14/Dec/2011:23:56:47 -0600] Loading NextJobId from job cache file "/var/cache/cups/job.cache"...
D [14/Dec/2011:23:56:47 -0600] cupsdAddSubscription(mask=0, dest=(nil)(), job=(nil)(0), uri="(null)")
I [14/Dec/2011:23:56:47 -0600] Full reload complete.
D [14/Dec/2011:23:56:47 -0600] cupsdCleanFiles(path="/var/spool/cups/tmp", pattern="(null)")
I [14/Dec/2011:23:56:47 -0600] Cleaning out old files in "/var/spool/cups/tmp"...
D [14/Dec/2011:23:56:47 -0600] cupsdCleanFiles(path="/var/cache/cups", pattern="*.ipp")
I [14/Dec/2011:23:56:47 -0600] Cleaning out old files in "/var/cache/cups"...
d [14/Dec/2011:23:56:47 -0600] cupsdCreateProfile(job_id=0) = NULL
d [14/Dec/2011:23:56:47 -0600] cupsdStartListening: 3 Listeners
I [14/Dec/2011:23:56:47 -0600] Listening to [v1.::1]:631 on fd 9...
I [14/Dec/2011:23:56:47 -0600] Listening to 127.0.0.1:631 on fd 10...
E [14/Dec/2011:23:56:47 -0600] Unable to bind socket for address /var/run/cups/cups.sock:631 - Permission denied.
d [14/Dec/2011:23:56:47 -0600] cupsdSetEnv: CUPS_SERVER=localhost
d [14/Dec/2011:23:56:47 -0600] cupsdSetEnv: CUPS_ENCRYPTION=IfRequested
d [14/Dec/2011:23:56:47 -0600] cupsdSetEnv: IPP_PORT=631
I [14/Dec/2011:23:56:47 -0600] Resuming new connection processing...
d [14/Dec/2011:23:56:47 -0600] cupsdResumeListening: Setting input bits...
d [14/Dec/2011:23:56:47 -0600] cupsdAddSelect(fd=9, read_cb=0xb770d940, write_cb=(nil), data=0xb7e06258)
d [14/Dec/2011:23:56:47 -0600] cupsdAddSelect(fd=10, read_cb=0xb770d940, write_cb=(nil), data=0xb7e0a828)
d [14/Dec/2011:23:56:47 -0600] cupsdAddSelect(fd=-1, read_cb=0xb770d940, write_cb=(nil), data=0xb7e0a938)
d [14/Dec/2011:23:56:47 -0600] cupsdAddSelect(fd=11, read_cb=0xb77126d0, write_cb=(nil), data=(nil))
D [14/Dec/2011:23:56:47 -0600] cupsdSetBusyState: newbusy="Not busy", busy="Not busy"
E [14/Dec/2011:23:56:47 -0600] Unable to write pid file

---

### Post by BeMyManikin on 2011-12-15
I'm not like most of the ppl here who actually know what they're doing, but to me it sounds like what this guy had on Ubuntu 10.04 where it wouldn't come up after every reboot.
[http://hardc0l2e.wordpress.com/2010/05/21/cups-not-running-on-boot-ubuntu-10-04/](http://hardc0l2e.wordpress.com/2010/05/21/cups-not-running-on-boot-ubuntu-10-04/)
here's the site that I found were he has a band-aid fix, hope it helps.

(mostly here to get beans lol)

---

### Post by elorden on 2011-12-16
> **BeMyManikin said:**
> I'm not like most of the ppl here who actually know what they're doing, but to me it sounds like what this guy had on Ubuntu 10.04 where it wouldn't come up after every reboot.
[http://hardc0l2e.wordpress.com/2010/05/21/cups-not-running-on-boot-ubuntu-10-04/](http://hardc0l2e.wordpress.com/2010/05/21/cups-not-running-on-boot-ubuntu-10-04/)
here's the site that I found were he has a band-aid fix, hope it helps.

(mostly here to get beans lol)
Thank you BeMyManikin, but, alas, no, that has not fixed my issue.  I think it has to do with the permissions on the socket and the pid file/directory. I just don't know where to go from here to fix it.

---

### Post by Zill on 2011-12-16
elorden:  More information would be useful.

Please advise which release of Ubuntu you are running (10.04, 11.10 etc), indicating if it is standard Ubuntu or a variant such as Kubuntu, Xubuntu, Lubuntu etc.

What is the exact make and model of the printer you are trying to connect.

Is this a new installation and/or has this printer worked previously on this system?  Have you successfully used a different printer on the same system?

ps.  If you enclose terminal output in "code" tags (# button at top of the editing window) then it is much easier to read on the forums as this then fits into a scrollable text box. ;-)

---

### Post by elorden on 2011-12-16
Version of Ubuntu is a standard installation of 11.10 that had been updated using the Update Manager tool.  I believe that my Lexmark x6650 printer had worked before the upgrade.  (I had my system setup dual booting with Windows 7 and was just dabbling in Ubuntu.  Windows 7 died on me not too long ago, so I'm using the free alternative.)  Also, I could not find the source tag at the top of this edit screen.  can I just add the XML code tags?

Thanks much.

---

### Post by Zill on 2011-12-16
> **elorden said:**
> Version of Ubuntu is a standard installation of 11.10 that had been updated using the Update Manager tool.  I believe that my Lexmark x6650 printer had worked before the upgrade...
According to [this webpage]("http://support.lexmark.com/index?locale=en&productCode=LEXMARK_X6650&userlocale=EN_US&segment=DOWNLOAD&os=UBUNTU_10.04&page=downloadsList&oslocale=en_US#1"), the latest version of Ubuntu supported is 10.04.  This apparently provides the following driver:
lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz

It *may* be that this driver will work with 11.10 but you will have to wait for someone else to confirm if this is the case as I don't use Lexmark printers.

Is this the driver you have installed, or a different one?

Regarding the "CODE" tags, these (and others) are produced automatically for the selected text if you click on any of the various icons at the top of the edit box when you post a reply.  If you hover over each icon the appropriate function is displayed in a "tooltip".

---

### Post by elorden on 2011-12-30
Thanks for the response.  I tried this and found that it did not work.  I ended up chucking the Lexmark, getting an HP and installing the 10.04 version of Ubunutu, multiple boot of course.  The cupsd still was not starting.  I will be modifying the config file so that any mention of the lexmark is removed.  I just haven't taken the time to do that yet.  

Thanks.

> **Zill said:**
> According to [this webpage]("http://support.lexmark.com/index?locale=en&productCode=LEXMARK_X6650&userlocale=EN_US&segment=DOWNLOAD&os=UBUNTU_10.04&page=downloadsList&oslocale=en_US#1"), the latest version of Ubuntu supported is 10.04.  This apparently provides the following driver:
lexmark-08z-series-driver-1.0-1.i386.deb.sh.tar.gz

It *may* be that this driver will work with 11.10 but you will have to wait for someone else to confirm if this is the case as I don't use Lexmark printers.

Is this the driver you have installed, or a different one?

Regarding the "CODE" tags, these (and others) are produced automatically for the selected text if you click on any of the various icons at the top of the edit box when you post a reply.  If you hover over each icon the appropriate function is displayed in a "tooltip".

---

