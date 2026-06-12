---
title: "Howto install Kerio mailserver on Ubuntu/Debian"
date: 2007-06-01
forum: Outdated Tutorials &amp; Tips
---

### Post by djieno on 2007-06-01
Hello! I've been trying to install Kerio mailserver on Ubuntu/Debian but somehow I coulnd't find a complete howto. It will start at bootup with a proper bootup script made by Paul McNett. Kerio Mailserver package isn't freeware but costs a fraction of mikey$oft Exchange. AND is is build on rugged opensource Linux.

I really can't see why the most popular linux distribution isn't supported. ](*,)Running a stripped down FC6 was still using 1.1 gig and 260 mb memory for a working KMS. I have Ubuntu server 6.06.1 running it in 600 mb and only 150 mb memory! :-\" I had no stability issues what so ever. Ubuntu Rocks!

This is meant to be a [COLOR="DarkGreen"]copy[/COLOR] / paste howto. Starting from a clean installation of Ubuntu Dapper Drake 6.06.1. x86

# Install openssh server for remote login. Now you copy paste the commands within a shell. Cool
[COLOR="DarkGreen"]sudo apt-get install ssh[/COLOR]

# Ssh to your ubuntu/Debian to be Kerio mailserver machine from a desktop to be able to copy paste if from a console.
ssh your-keriomailserver-ip

# Grand console super user rights.
[COLOR="DarkGreen"]sudo -s[/COLOR]

# Update /etc/apt/sources.list with source.list from[ http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories").  Add the gpg key.
[COLOR="DarkGreen"]wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -
apt-get update
apt-get upgrade[/COLOR]

# First, make a backup of /var/lib/dpkg/status. Alien could break your dpkg database. To be safe copy it!
[COLOR="DarkGreen"]cp /var/lib/dpkg/status /var/lib/dpkg/status.start[/COLOR]

# install alien
[COLOR="DarkGreen"]apt-get install alien[/COLOR]

# Make a deb-file of the rpm [Writing this I'm using version kerio 6.3.1]. alien --scripts Filename.rpm
[COLOR="DarkGreen"]alien --scripts kerio-xxx-i386.rpm[/COLOR]

# Do a "apt-get update" to see if /var/lib/dpkg/status has been broken up. If it has, replace it with the backup from backup copy we made before. "cp /var/lib/dpkg/status.start /var/lib/dpkg/status" I had this once.

# install kerio dependencies libstdc++5
[COLOR="DarkGreen"]apt-get install libstdc++5[/COLOR]

# Install the created kerio_xxx-i386.deb. If you have trouble installing the .deb file with "dpkg -i filename.deb" try "dpkg --unpack filename.deb".
[COLOR="DarkGreen"]dpkg -i kerio_xxx-i386.deb[/COLOR]

# Start kerio configuration script and set your preferences.
[COLOR="DarkGreen"]cd /opt/kerio/mailserver
./cfgwizard[/COLOR]

Now it is time to set proper init script see attached file. Download the file and paste it in /etc/init.d/. The file should be called keriomailserver. so Vi /etc/init.d/keriomailserver should give you this script.

#Set Kerio to start at bootup in rc.d. Do not forget the last dot!
[COLOR="DarkGreen"]update-rc.d keriomailserver start 99 2 3 4 5 . stop 20 0 1 6 .[/COLOR]

Done! Do a reboot and see Kerio mailserver nicely start at bootup.

I've tried to be as clear as I can. If you have any additions please pm me so I can alter this howto to prevent an unclear workflow. I really hate well intended but still bad/incomplete/absolete/unchecked howto's associated with Red Hat look-alikes. People using Ubuntu/Debian try to help out better!

Please do not forget to flare at Kerio for not supporting native use of Ubuntu/Debian! ;)

Djieno! :popcorn:

---

### Post by Poleh on 2007-11-26
Confirmation that the above process works with Ubuntu 7.10 - Please don't forget to over-write the default /etc/init.d/keriomailserver file with the one attached in the previous post, if you don't you can expect to see something like the following output:

```

root@ubuntu-vm:/opt/kerio/mailserver# sudo /etc/init.d/keriomailserver start
/etc/init.d/keriomailserver: line 105: /etc/rc.status: No such file or directory
/etc/init.d/keriomailserver: line 107: rc_reset: command not found
/etc/init.d/keriomailserver: line 111: checkproc: command not found
/etc/init.d/keriomailserver: line 118: startproc: command not found
/etc/init.d/keriomailserver: line 122: checkproc: command not found
/etc/init.d/keriomailserver: line 122: checkproc: command not found
/etc/init.d/keriomailserver: line 122: checkproc: command not found
/etc/init.d/keriomailserver: line 122: checkproc: command not found
/etc/init.d/keriomailserver: line 122: checkproc: command not found
/etc/init.d/keriomailserver: line 122: checkproc: command not found
/etc/init.d/keriomailserver: line 122: checkproc: command not found
/etc/init.d/keriomailserver: line 122: checkproc: command not found
/etc/init.d/keriomailserver: line 122: checkproc: command not found
/etc/init.d/keriomailserver: line 122: checkproc: command not found
Starting Kerio MailServer: /etc/init.d/keriomailserver: line 132: rc_failed: command not found
/etc/init.d/keriomailserver: line 175: rc_exit: command not found

```

---

### Post by avnidv on 2008-03-25
> # Update /etc/apt/sources.list with source.list from[ http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories").  Add the gpg key.
[COLOR="DarkGreen"]wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -
apt-get update
apt-get upgrade[/COLOR] 

I think my question would be why Ubuntu has to be converted into Medibuntu. Is it because yours is a server version? 

What additional packages are needed to install Kerio mailserver and are they possibly included in a Ubuntu standard install? I'd like to install Kerio on a 7.10 standard installation.

Thanks in advance.

---

### Post by sstendal on 2008-03-27
The installation broke my /var/lib/dpkg/status file. Aptitude failes with "E: Unable to parse package file /var/lib/dpkg/status".
I belive the reason is that the section for the package kerio-kms in the file contains more than 500 lines under "Conffiles". To fix this i opened the "/var/lib/dpkg/status" file and removed all lines starting with "/opt/kerio/mailserver/reports/". This solved the problem.

I stored a backup of the status file as it was just after the installation. When I later had to upgrade Kerio, I just replaced the modified status file with my backup before the upgrade and switched back again after the upgrade.
The upgrade was done exactly like the installation using "dpkg -i".

---

### Post by ojee66 on 2008-05-02
> **djieno said:**
> 
# Update /etc/apt/sources.list with source.list from[ http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_add_extra_repositories").  Add the gpg key.
[COLOR="DarkGreen"]wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -
apt-get update
apt-get upgrade


Djieno! :popcorn:

Above i did not do it on my ubuntu 7.10 server.
had to adjust the rigts of the 2 self made files to chmod 755.


Now everything works :)

Tnx

---

### Post by PinkFloyd102489 on 2008-05-02
It is never recommended to perform an apt-get upgrade after adding other repos besides the official Ubuntu ones. Word of caution, you could hose your system if you perform the upgrade. In fact, there's no reason to add the repo in the first place if you're at least on Gutsy.


Also, no need to reboot. Simply issue "sudo /etc/init.d/keriomailserver start".

---

### Post by indymx on 2008-05-02
I'm trying to build the deb package on 8.04 and am running into an error...


~# alien --scripts kerio-kms-6.4.1-3679.linux.i386.rpm 
Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
parsechangelog/debian: warning:     debian/changelog(l7): badly formatted heading line
LINE: Version 6.4.1
parsechangelog/debian: warning:     debian/changelog(l8): badly formatted heading line
LINE: ==================
parsechangelog/debian: warning:     debian/changelog(l10): badly formatted heading line
LINE: Kerio MailServer:
parsechangelog/debian: warning:     debian/changelog(l11): badly formatted heading line
LINE: ------------------
parsechangelog/debian: warning:     debian/changelog(l12): unrecognised line
LINE:  * Forced SSLv3/TLSv1 connections do not use low encryption ciphers.
parsechangelog/debian: warning:     debian/changelog(l13): unrecognised line
LINE:  - Fixed possible crash if an annotation database for certain folder became corrupted.
parsechangelog/debian: warning:     debian/changelog(l14): unrecognised line
LINE:  - Fixed possible crash in PHP language interpreter.
parsechangelog/debian: warning:     debian/changelog(l15): unrecognised line
LINE:  - Fixed potential security problem in attachment filter.
parsechangelog/debian: warning:     debian/changelog(l16): unrecognised line
LINE:  - Multi-line note in contact was converted to a single line during Entourage 2004 synchronization.
parsechangelog/debian: warning:     debian/changelog(l17): unrecognised line
LINE:  - Entourage and Kerio iSync Connector synchronizations might cause a long delay of DirectPush responses in mobile synchronization.
parsechangelog/debian: warning:     debian/changelog(l18): unrecognised line
LINE:  - Certain copy or move operations in Entourage synchronization could cause user mailbox lockout.
parsechangelog/debian: warning:     debian/changelog(l19): unrecognised line
LINE:  - User password change did not take effect on current WebDAV sessions.
parsechangelog/debian: warning:     debian/changelog(l20): unrecognised line
LINE:  - Fixed installation on Windows Vista with disabled UAC.
parsechangelog/debian: warning:     debian/changelog(l21): unrecognised line
LINE:  - Fixed downloading of e-mail attachments on during mobile synchronization certain Nokia phones.
parsechangelog/debian: warning:     debian/changelog(l22): unrecognised line
LINE:  - Changes in calendar events were not synchronized to Palm Treo.
parsechangelog/debian: warning:     debian/changelog(l23): unrecognised line
LINE:  - Mobile devices did not ask for new password after password change on server.
parsechangelog/debian: warning:     debian/changelog(l25): badly formatted heading line
LINE: Kerio WebMail:
parsechangelog/debian: warning:     debian/changelog(l26): badly formatted heading line
LINE: ------------------
parsechangelog/debian: warning:     debian/changelog(l27): unrecognised line
LINE:  - The character "letter S with caron" was lost in sender and recipient name.
parsechangelog/debian: warning:     debian/changelog(l28): unrecognised line
LINE:  - Text didn't fit Settings menu in Substance skin in Internet Explorer(r) 7.
parsechangelog/debian: warning:     debian/changelog(l29): unrecognised line
LINE:  - Sorting of addressbook in phonebook view by full name was wrong for contacts with only company filed.
parsechangelog/debian: warning:     debian/changelog(l30): unrecognised line
LINE:  - Check Names could be activated even if not necessary.
parsechangelog/debian: warning:     debian/changelog(l31): unrecognised line
LINE:  - Freebusy information was not downloaded from remote location for contacts with freebusy URL definition.
parsechangelog/debian: warning:     debian/changelog(l32): unrecognised line
LINE:  - Fixed several small bugs.
parsechangelog/debian: warning:     debian/changelog(l34): badly formatted heading line
LINE: Kerio Administration Console:
parsechangelog/debian: warning:     debian/changelog(l35): badly formatted heading line
LINE: ------------------
parsechangelog/debian: warning:     debian/changelog(l36): unrecognised line
LINE:  - Corrected French translation in DNS blacklist list.
parsechangelog/debian: warning:     debian/changelog(l37): unrecognised line
LINE:  - Corrected translation of Welcome screen.
parsechangelog/debian: warning:     debian/changelog(l39): badly formatted heading line
LINE: Kerio Outlook Connector:
parsechangelog/debian: warning:     debian/changelog(l40): badly formatted heading line
LINE: ------------------
parsechangelog/debian: warning:     debian/changelog(l41): unrecognised line
LINE:  - Some e-mail folders were invisible after upgrade from previous version.
parsechangelog/debian: warning:     debian/changelog(l42): unrecognised line
LINE:  - Contacts in address book could be displayed as empty or as "Corrupted item" after upgrade from previous version.
parsechangelog/debian: warning:     debian/changelog(l43): unrecognised line
LINE:  - Certain meeting invitations might not be displayed properly in Outlook.
parsechangelog/debian: warning:     debian/changelog(l45): badly formatted heading line
LINE: Kerio iSync Connector:
parsechangelog/debian: warning:     debian/changelog(l46): badly formatted heading line
LINE: ------------------
parsechangelog/debian: warning:     debian/changelog(l47): unrecognised line
LINE:  - Disabled Apple Sync Engine was not detected by Kerio iSync Connector.
parsechangelog/debian: warning:     debian/changelog(l48): unrecognised line
LINE:  - Fixed synchronization error about unsupported calendar items.
parsechangelog/debian: warning:     debian/changelog(l49): unrecognised line
LINE:  - Time zone information could be converted to GMT during synchronization to server.
parsechangelog/debian: warning:     debian/changelog(l50): unrecognised line
LINE:  - Fixed several small synchronization issues.
parsechangelog/debian: warning:     debian/changelog(l52): badly formatted heading line
LINE: Version 6.4.0
parsechangelog/debian: warning:     debian/changelog(l53): badly formatted heading line
LINE: ==================
parsechangelog/debian: warning:     debian/changelog(l55): badly formatted heading line
LINE: Kerio MailServer:
parsechangelog/debian: warning:     debian/changelog(l56): badly formatted heading line
LINE: ------------------
parsechangelog/debian: warning:     debian/changelog(l57): unrecognised line
LINE:  + Support for Windows Vista(tm)
parsechangelog/debian: warning:     debian/changelog(l58): unrecognised line
LINE:  + Added support for new devices in ActiveSync(r): Nokia E, Sony Ericsson M600, P990 and DataViz RoadSync client.
parsechangelog/debian: warning:     debian/changelog(l59): unrecognised line
LINE:  + Added support for synchronization of Windows Calendar on Vista (calendar subscribing/publishing).
parsechangelog/debian: warning:     debian/changelog(l60): unrecognised line
LINE:  + Support for intermediate SSL certificates
parsechangelog/debian: warning:     debian/changelog(l61): unrecognised line
LINE:  * ORDB.org DNS blacklist has been closed. ORDB blacklist is removed from configuration on upgrade.
parsechangelog/debian: warning:     debian/changelog(l62): unrecognised line
LINE:  * Updated SpamHaus DNS blacklist configuration.
parsechangelog/debian: warning:     debian/changelog(l63): unrecognised line
LINE:  * Contact birthday and anniversary can be set before 1970.
parsechangelog/debian: warning:     debian/changelog(l64): unrecognised line
LINE:  * Improved Kerio MailServer Engine monitor.
parsechangelog/debian: warning:     debian/changelog(l65): unrecognised line
LINE:  * Improved email delivery to SMTP servers which cannot establish SSL connection.
parsechangelog/debian: warning:     debian/changelog(l66): unrecognised line
LINE:  * Increased performance and speed of WebAdmin user management.
parsechangelog/debian: warning:     debian/changelog(l67): unrecognised line
LINE:  * Enhanced support for multiple CPUs in antivirus checking.
parsechangelog/debian: warning:     debian/changelog(l68): unrecognised line
LINE:  * Added ability to disable SSLv2 and force SSLv3/TLSv1 only in secure connections (see KB article).
parsechangelog/debian: warning:     debian/changelog(l69): unrecognised line
LINE:  * Added support for new Linux versions (see the System Requirements on Kerio website).
parsechangelog/debian: warning:     debian/changelog(l70): unrecognised line
LINE:  * Added support for decoding x-uuencoded attachments.
parsechangelog/debian: warning:     debian/changelog(l71): unrecognised line
LINE:  * LOGIN authentication method supports initial-response parameter for faster authentication.
parsechangelog/debian: warning:     debian/changelog(l72): unrecognised line
LINE:  * Support for subscription of Kerio MailServer calendars from Outlook 2007 via iCal.
parsechangelog/debian: warning:     debian/changelog(l73): unrecognised line
LINE:  * Improved uninstallation process on Mac OS X. Added option to remove configuration files and/or message store during uninstallation.
parsechangelog/debian: warning:     debian/changelog(l74): unrecognised line
LINE:  - KMS had to be restarted after certain Sophos antivirus updates.
parsechangelog/debian: warning:     debian/changelog(l75): unrecognised line
LINE:  - Attachment file name in attachment filter report was not decoded.
parsechangelog/debian: warning:     debian/changelog(l76): unrecognised line
LINE:  - Messages downloaded from POP3 server were forwarded with wrong sender address.
parsechangelog/debian: warning:     debian/changelog(l77): unrecognised line
LINE:  - Certain recurring event might not be displayed properly around daylight saving time change.
parsechangelog/debian: warning:     debian/changelog(l78): unrecognised line
LINE:  - Emails from myspace.com could be rejected due to invalid format.
parsechangelog/debian: warning:     debian/changelog(l79): unrecognised line
LINE:  - It was not possible to delete and create same folder in a short period of time in Entourage 2004.
parsechangelog/debian: warning:     debian/changelog(l80): unrecognised line
LINE:  - Fixed forwarding of DSN reports in email forwarding.
parsechangelog/debian: warning:     debian/changelog(l81): unrecognised line
LINE:  - Some recurring events with exceptions could be lost in Entourage 2004.
parsechangelog/debian: warning:     debian/changelog(l82): unrecognised line
LINE:  - Fixed ability to change calendar properties in Entourage 2004.
parsechangelog/debian: warning:     debian/changelog(l83): unrecognised line
LINE:  - Property X-FILE-AS was not updated during Entourage 2004 synchronization.
parsechangelog/debian: warning:     debian/changelog(l84): unrecognised line
LINE:  - Certain TNEF messages (winmail.dat) could be delivered with a delay.
parsechangelog/debian: warning:     debian/changelog(l85): unrecognised line
LINE:  - Emails forwarded to the archive via remote address could have incorrect line terminators in email headers.
parsechangelog/debian: warning:     debian/changelog(l86): unrecognised line
LINE:  - Spell checking certain words in WebMail could cause high CPU usage.
parsechangelog/debian: warning:     debian/changelog(l87): unrecognised line
LINE:  - Watchkms utility could produce error messages in the watchdog or console log on Mac OS X.
parsechangelog/debian: warning:     debian/changelog(l88): unrecognised line
LINE:  - MailServer sometimes failed to start after upgrade from KMS 5.7.x.
parsechangelog/debian: warning:     debian/changelog(l89): unrecognised line
LINE:  - Attendee could not accept update of meeting request on PDA.
parsechangelog/debian: warning:     debian/changelog(l90): unrecognised line
LINE:  - Updating events with attendees on PDA could cause duplicated items in calendar.
parsechangelog/debian: warning:     debian/changelog(l91): unrecognised line
LINE:  - Calendar events created on Palm Treo 650 might cause high CPU usage.
parsechangelog/debian: warning:     debian/changelog(l92): unrecognised line
LINE:  - Sender address containing some unusual characters might be rejected in SMTP session.
parsechangelog/debian: warning:     debian/changelog(l93): unrecognised line
LINE:  - ActiveSync: DirectPush could report changes in email folder several times which caused frequent device synchronizations.
parsechangelog/debian: warning:     debian/changelog(l94): unrecognised line
LINE:  - ActiveSync: Contact note could be lost during synchronization after editing the contact on mobile device.
parsechangelog/debian: warning:     debian/changelog(l95): unrecognised line
LINE:  - ActiveSync: Fixed big message downloading on Palm Treo 680.
parsechangelog/debian: warning:     debian/changelog(l96): unrecognised line
LINE:  - ActiveSync: Event invitation synchronized to device was always marked as tentative.
parsechangelog/debian: warning:     debian/changelog(l97): unrecognised line
LINE:  - ActiveSync: Accepting meeting update could produce event duplication in calendar.
parsechangelog/debian: warning:     debian/changelog(l98): unrecognised line
LINE:  - ActiveSync: Synchronization of Windows Mobile 2003SE device could end with error 401.
parsechangelog/debian: warning:     debian/changelog(l99): unrecognised line
LINE:  - ActiveSync: Forwarding email to invalid email address was not reported to the error log properly.
parsechangelog/debian: warning:     debian/changelog(l100): unrecognised line
LINE:  - Fixed missing space character in emails with long subject sent to mailing list.
parsechangelog/debian: warning:     debian/changelog(l101): unrecognised line
LINE:  - Email was not parsed correctly if body part boundaries contain special characters.
parsechangelog/debian: warning:     debian/changelog(l102): unrecognised line
LINE:  - Digitally signed email sent to mailing list had invalid signature when viewing in NNTP.
parsechangelog/debian: warning:     debian/changelog(l103): unrecognised line
LINE:  - Kerio MailServer uninstallation on Mac OS X did not remove message store created in non-default location.
parsechangelog/debian: warning:     debian/changelog(l104): unrecognised line
LINE:  - Fixed many small bugs
parsechangelog/debian: warning:     debian/changelog(l106): badly formatted heading line
LINE: Kerio Administration Console:
parsechangelog/debian: warning:     debian/changelog(l107): badly formatted heading line
LINE: ------------------
parsechangelog/debian: warning:     debian/changelog(l108): unrecognised line
LINE:  + Support for Windows Vista(tm)
parsechangelog/debian: warning:     debian/changelog(l109): unrecognised line
LINE:  + Added server certificate validation in remote administration.
parsechangelog/debian: warning:     debian/changelog(l110): unrecognised line
LINE:  * Mail monitor is integrated into the System Preferences on Mac OS(r) X.
parsechangelog/debian: warning:     debian/changelog(l111): unrecognised line
LINE:  * Added help file in PDF format on Linux.
parsechangelog/debian: warning:     debian/changelog(l112): unrecognised line
LINE:  - Fixed size of pie charts in statistics.
parsechangelog/debian: warning:     debian/changelog(l113): unrecognised line
LINE:  - Fixed importing from CSV file in Administration Console on Linux.
parsechangelog/debian: warning:     debian/changelog(l114): unrecognised line
LINE:  - Fixed possible crash in user administration.
parsechangelog/debian: warning:     debian/changelog(l115): unrecognised line
LINE:  - Fixed possible crash in log view.
parsechangelog/debian: warning:     debian/changelog(l116): unrecognised line
LINE:  - Some folder names in Mobile Device Status window were not translated.
parsechangelog/debian: warning:     debian/changelog(l117): unrecognised line
LINE:  - Fixed: Default value in log rotation setting was too low and might cause performance problems.
parsechangelog/debian: warning:     debian/changelog(l118): unrecognised line
LINE:  - Fixed many small bugs
parsechangelog/debian: warning:     debian/changelog(l120): badly formatted heading line
LINE: Kerio WebMail:
parsechangelog/debian: warning:     debian/changelog(l121): badly formatted heading line
LINE: ------------------
parsechangelog/debian: warning:     debian/changelog(l122): unrecognised line
LINE:  + Support for Internet Explorer(r) 7 on Windows Vista
parsechangelog/debian: warning:     debian/changelog(l123): unrecognised line
LINE:  * Redesigned Settings drop-down menu.
parsechangelog/debian: warning:     debian/changelog(l124): unrecognised line
LINE:  * Separated Out-of-office to extra dialog and increased its size.
parsechangelog/debian: warning:     debian/changelog(l125): unrecognised line
LINE:  * Added Apple keys (Command for shortcuts and selections,
parsechangelog/debian: warning:     debian/changelog(l126): found change data where expected next heading or eof
LINE:    Alt for drag'n'drop copy, Backspace for deleting).
Can't locate object method "init" via package "Dpkg::Changelog::Entry" at /usr/share/perl5/Dpkg/Changelog/Debian.pm line 260, <STDIN> line 126.
dpkg-parsechangelog: failure: changelog parser /usr/lib/dpkg/parsechangelog/debian gave error exit status 9
dh_installchangelogs: changelog parse failure
make: *** [binary-arch] Error 1
find: kerio-kms-6.4.1: No such file or directory



I'm really not sure what to make of this. Looks like it's choking on the change log, is there any way to bypass that?

---

### Post by PinkFloyd102489 on 2008-05-02
I got that error when trying to compile the admin console. The mailserver itself went fine.

---

### Post by funga on 2008-05-11
Thanks a lot for this workaround. I came upon the 

```
root@ubuntu-vm:/opt/kerio/mailserver# sudo /etc/init.d/keriomailserver start
/etc/init.d/keriomailserver: line 105: /etc/rc.status: No such file or directory
```

error, searched google and found a nice ini file in here :-)

---

### Post by djieno on 2008-12-14
Hello Kerio fans!

I'll make a new howto for Hardy Heron 8.04 and Kerio mailserver version 6.5.0 patch 1 since it has been running successfully for over 2 months now.

Installing is easier but it's not so generic as on Dapper Drake since the package already made for ubuntu/debian.

Greetings,

Djieno :P

---

