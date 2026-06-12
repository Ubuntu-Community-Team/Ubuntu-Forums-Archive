---
title: "Live &quot;Realtime&quot; Virus Scanner"
date: 2012-04-27
forum: Recurring Discussions
---

### Post by TZSnowboardfreak on 2012-04-27
Hi together,

first i am sorry for my bad english and i hope i am able to describe my problem understandable. 
I tried using google to find a Linux virus scanner which is scanning files that are moving to the file system but without any useful result. I need a virus scanner that scans automatically every file that is copied by USB stick or via Samba share to the hard drive.

Does anyone know such a program or has anyone a good idea to realize this? Thanks in advance for every answer :)

---

### Post by wacky_sung on 2012-04-27
> **TZSnowboardfreak said:**
> Hi together,

first i am sorry for my bad english and i hope i am able to describe my problem understandable. 
I tried using google to find a Linux virus scanner which is scanning files that are moving to the file system but without any useful result. I need a virus scanner that scans automatically every file that is copied by USB stick or via Samba share to the hard drive.

Does anyone know such a program or has anyone a good idea to realize this? Thanks in advance for every answer :)

So far i only known of is using on a browser which i uses [HAVP]("http://www.server-side.de/") + [Clam antivirus]("http://www.clamav.net/lang/en/download/packages/packages-linux/") that will automatic scan when after set with my browser that will scan for virus and alert it pages when found.

---

### Post by rookcifer on 2012-04-27
No point in using AV scanners.

---

### Post by Ms. Daisy on 2012-04-27
> **rookcifer said:**
> No point in using AV scanners. Not true. It's not totally pointless to scan files shared to/from Windows. In fact I'd say that's the main reason for AV in Linux. 
 
I haven't used clamav or avast, but perhaps they can be configured to do what you need.

---

### Post by wacky_sung on 2012-04-27
> **rookcifer said:**
> No point in using AV scanners.

I think lamers will be happy to find people like you.Currently lot of malwares/trojans are moving toward cross platform OS which target at browsers plugins.

---

### Post by rookcifer on 2012-04-27
> **wacky_sung said:**
> I think lamers will be happy to find people like you.Currently lot of malwares/trojans are moving toward cross platform OS which target at browsers plugins.

Flashback would not work with my security settings.

---

### Post by BitShark on 2012-04-27
What are the few seconds it would take to scan a file versus the time you would spend to triage and clean your system after the fact?

---

### Post by OpenSourceRules on 2012-04-28
Are you serious?
So, I need to consider using Clam?

---

### Post by OpSecShellshock on 2012-04-28
> **OpenSourceRules said:**
> Are you serious?
So, I need to consider using Clam?

Doubt it. Even if you do share files between a Linux and Windows system, it's probably more likely that the AV on the Windows system will be better suited to detect malware. AV that's available for Linux tends to exclusively check static files against signatures for matches, whereas those available for Windows also perform heuristic/runtime analysis (with um, varying degrees of effectiveness, of course).

Additionally, you can go to [malwr.com]("http://malwr.com/") to upload suspicious looking files so they can be run to see what happens without affecting your machine locally.

---

### Post by wacky_sung on 2012-04-28
> **rookcifer said:**
> Flashback would not work with my security settings.

Flashback is mainly target for Mac OS.

[Here]("http://www.pcworld.com/businesscenter/article/253649/flashback_mac_malware_one_more_reason_to_switch_to_linux.html") is a very good explanation why malware writers find it hard to target linux.

> Even better, though, is that Linux is so diverse, so users aren't all on a single, common operating system--instead, they're on many, many distinct distributions. That makes it much harder for a malware creator to find a worthwhile segment to target.

---

### Post by OpSecShellshock on 2012-04-28
> **wacky_sung said:**
> Flashback is mainly target for Mac OS.

[Here]("http://www.pcworld.com/businesscenter/article/253649/flashback_mac_malware_one_more_reason_to_switch_to_linux.html") is a very good explanation why malware writers find it hard to target linux.

Thing is, with Linux systems the same sorts of things can be done, just in a different way. Should the installation base become sufficient to merit the effort, there is really nothing stopping similar things from happening at all. And another point about obscurity: Linux desktops are in a lot of cases more obscure to their own users than they are to potential attackers. This makes social engineering in the form of harmful tutorials and trojan scripts even easier in a lot of ways (AV software will still not protect users from either of those things, though).

There's no substitute for vigilance and care on any OS.

---

### Post by Dangertux on 2012-04-28
The bottom line on this is I am very much in agreement with OpSecShellShock (wave btw , haven't seen you around in a while!) 

Linux AV solutions aren't very mature. Whether this is because folks buy into the crap that Linux is "more secure" , or that somehow discretionary access controls protect them from executable files, or sudo saves the day. Heck, maybe they just think you "can't" create malware for Linux. Whatever the case may be those answers are simply not true.

The real answer if you want to protect your Windows boxes with AV is to use Windows host or domain based AV solutions on them. They are far superior to their Linux counterparts and offer the "on-access" scanning that you're looking for. Hope this helps.

P.S : Anti-virus != Security.

---

### Post by wacky_sung on 2012-04-28
> **OpSecShellshock said:**
> Thing is, with Linux systems the same sorts of things can be done, just in a different way. Should the installation base become sufficient to merit the effort, there is really nothing stopping similar things from happening at all. And another point about obscurity: Linux desktops are in a lot of cases more obscure to their own users than they are to potential attackers. This makes social engineering in the form of harmful tutorials and trojan scripts even easier in a lot of ways (AV software will still not protect users from either of those things, though).

There's no substitute for vigilance and care on any OS.

I have no doubt about it.

Antivirus is just another layer of security for known security flaws found.

---

### Post by emiller12345 on 2012-04-28
Although its a bit outdated, I've been looking for a way to get dazukofs functioning for the modern kernel. This would provide "on-access" scanning of files on a linux computer.  Ref: [http://ubuntuforums.org/showthread.php?t=1965395](http://ubuntuforums.org/showthread.php?t=1965395)

---

### Post by CharlesA on 2012-04-28
> **OpSecShellshock said:**
> Doubt it. Even if you do share files between a Linux and Windows system, it's probably more likely that the AV on the Windows system will be better suited to detect malware. AV that's available for Linux tends to exclusively check static files against signatures for matches, whereas those available for Windows also perform heuristic/runtime analysis (with um, varying degrees of effectiveness, of course).

Additionally, you can go to [malwr.com]("http://malwr.com/") to upload suspicious looking files so they can be run to see what happens without affecting your machine locally.
What he said.

I still run BitDefender on my file server cuz I am sharing with Windows boxes.

---

### Post by OpenSourceRules on 2012-04-28
[QUOTE=OpSecShellshock]Doubt it. Even if you do share files between a Linux and Windows system, it's probably more likely that the AV on the Windows system will be better suited to detect malware. AV that's available for Linux tends to exclusively check static files against signatures for matches, whereas those available for Windows also perform heuristic/runtime analysis (with um, varying degrees of effectiveness, of course).

Additionally, you can go to malwr.com to upload suspicious looking files so they can be run to see what happens without affecting your machine locally.[/QUOTE]

At least I don't go for software outside of the repo or Ubuntu Software centre.

---

### Post by wacky_sung on 2012-04-29
> **OpenSourceRules said:**
> At least I don't go for software outside of the repo or Ubuntu Software centre.

Nothing come 100% safe to use. 

Example firefox addon and google chrome extension in which malicious files have been found.

---

### Post by CharlesA on 2012-04-29
> **wacky_sung said:**
> Nothing come 100% safe to use. 

Example firefox addon and google chrome extension in which malicious files have been found.

Indeed. I'd be more worried about a shady addon than having the repos compromised, which can happen, but there are measures in place to prevent it.

---

### Post by rookcifer on 2012-04-29
> **wacky_sung said:**
> Flashback is mainly target for Mac OS.

I know that.  I was merely using it as an example of a trojan that targets *nix.  Theoretically there is no reason Flashback could not target Linux.  In fact, since it was a browser exploit with Java, it should work on any platform provided the author coded it to do so.

I was just saying that with my security settings it would have a very difficult time infecting me and I don't use AV.

---

### Post by OpenSourceRules on 2012-04-29
Is it funny?  I have not used plugins for a long time, except for Flash and Java.

---

### Post by uRock on 2012-04-29
This thread => *Recurring Discussions*

---

### Post by TZSnowboardfreak on 2012-05-02
Thanks for the answers!
Now I tried bit defender, but there is no live scan. 
Then I tried avast, but live scan is only in the avast4server packet available. (I cant download that because its not free)
Then I found the ClamAV (daemon). With the program "clamdtop" I am able to see the performance and activity of the daemon. Now my new problem - The running ClamAV daemon is doing nothing :confused:

Is this correct. I edited the /etc/clamav/clamd.conf but i can't find especially configs for live scan or what happened when a infected file is found.   

Thanks in advance!

---

### Post by SeijiSensei on 2012-05-02
> **TZSnowboardfreak said:**
> Now my new problem - The running ClamAV daemon is doing nothing

How do you know this?  Have you tried downloading an infected file?  The easiest method for testing AV is to use the "eicar.com" file.  All AV scanners include this in their signature lists.

Download eicar.com from here: [http://eicar.org/download/eicar.com](http://eicar.org/download/eicar.com)

---

### Post by Lucradia on 2012-05-02
Flashback I thought was a UNIX virus, not a MacOS Virus >_>

---

### Post by |{urse on 2012-05-02
Well, OSX is Darwin is Unix. Flashback is written for OSX specifically, not Unix in general. I bet IOS is the next target for viruses. @op I highly doubt you have anything to worry about but if you are running a mailserver or are sharing with windows it IS a good idea to rock the clamav, yes it works.

---

### Post by TZSnowboardfreak on 2012-05-03
> How do you know this?  Have you tried downloading an infected file?  The  easiest method for testing AV is to use the "eicar.com" file.  All AV  scanners include this in their signature lists.Exactly, i tried it with this file. I duplicated it in many folders and copied the folders additional fulfilled with other files on many places on my hdd.

I think I've to see in clamdtop which file is currently scanned and it has to stop me duplicating the file or better delete this file. If I am duplicating large files, clamav has to open more threads  or use CPU etc ...

 It is all time looking like this :(

[IMG]http://image-upload.de/image/mCnbsB/4deed35628.png[/IMG]

---

### Post by SeijiSensei on 2012-05-03
Well clamd is exactly what it says it is, a daemon.  You'd need a piece of client software that intervenes when you download a file and passes it to clamd for scanning.  Clamd by itself doesn't do anything but wait for scanning requests.

Now how you'd implement the client side of this, I don't know.  Clamd is usually used to provide [user-level scanning for email]("http://www.linuxquestions.org/questions/linux-general-1/how-to-connect-between-procmail-and-clamav-736906/#post3592917") with procmail and clamdscan.  

I've never used AV software on Linux except to scan email with MailScanner and web objects with SquidClamAV.  Neither of these is a solution designed for ordinary workstations. You could set up a cron job that scans your drives with clamscan periodically and emails you a report.

I've been using Linux for over fifteen years and have never had a problem with viruses or malware. Of course, I know what I'm doing, and I don't visit dodgy sites or download random stuff off the Internet.  ClamAV offers an on-demand scanner for Windows and new product for OS X.  I don't see anything similar for Linux.

---

### Post by TZSnowboardfreak on 2012-05-04
Of course ...  I didn't have a virus or something else on my linux machine and a scanner on this doesn't make scene. This is for an for an Server which is a samba gateway between 2 networks and user can transfer files by dropping it on an samba share. Additional it shall be possible to drop files via usb stick in this network. 

All this work is done but i have to ensure that known virus can not be transfered between the networks or usb ...

---

### Post by SeijiSensei on 2012-05-04
Other than frequently scanning the share with clamscan from Linux and deleting infected files, I don't think there's a way to implement that.  Anyone using the share from Windows would need a Windows-based virus scanner on his or her own machine to implement on-the-fly scanning.

If the share is relatively small, and the delay between when files are uploaded and when they are accessed by others is long enough, scanning from cron every few minutes might be a decent kludge.  A more sophisticated solution would use the find command to identify newly-uploaded files and just scan them.  An even more sophisticated solution would create a write-only quarantine area to handle uploaded files.  You'd then periodically run clamscan against files in the quarantine and release those found to be clean to a read-only share, while notifying the admin of any that have viruses.

On my (relatively fast) machine, I scanned my entire Win7 partition from Linux.  It took 28 minutes to scan 18 GB even with a lot of executables (exe's, dll's, etc.).  You're unlikely to have anywhere near the ratio of executables to total files as a complete Windows installation has, so I'd bet you could scan a gigabyte in less than a minute even without any limitations to the list of files to scan.

---

