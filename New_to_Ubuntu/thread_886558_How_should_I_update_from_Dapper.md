---
title: "How should I update from Dapper"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by .nedberg on 2008-08-11
I have a Dapper server witch runs NFS, FTP and SSH. All my important files are on a separate disk. I am thinking of updating to Hardy.

Ofcourse I could just backup everything and follow normal updating instructions and hope for the best.

I am however thinking of just unplugging the second disk and plugging it in after the update. If it fails I still have my data and can set up the server once again.

What do you recommend? Backup and update with disk in place, or backup and replugging drive?

---

### Post by hyper_ch on 2008-08-11
I'd do a new install and you should always have backups.

Depending on how much you modified the system you will run into problems. As it seems to be a slightly modified server, I think the upgrade process should work well and not cause any trouble.

---

### Post by .nedberg on 2008-08-11
It is my backup-server, it holds backups of my important files...

Backing up that backup server is not somthing I want to do today. I am thinking of just making sure I have my important data, unplug the drive and update. Than replug the drive and make sure my backup scripts work.

---

### Post by Frenske on 2008-08-11
So Ubuntu is not on the HDD with the import files. I guess there would be no problems with a complete new install unless you put Ubuntu on that HDD by accident, but that would be really stupid. If you want to be sure, just unmount it and mount it later after you are sure that the update went succesfully.

---

### Post by mjwhitfield on 2008-08-11
If it work's, don't mess with it!

---

### Post by .nedberg on 2008-08-30
Well, I just updated the server from Dapper to Hardy.

Everything went just fine and I had no major problems. I followed [this guide]("http://www.ubuntu.com/getubuntu/upgrading#head-e059d5452a24b50d09c64df48058ef2d834eb197-2") to update the server. When running 'do-release-upgrade -d' I got some errors regarding a hash-mismatch. A quick google-search and the answer was to run 'do-release-upgrade' without the -d option. 40 minutes later the machine was updatede and rebooted. Everything seems to be running fine, only thing not running was fail2ban. I chose to keep the existing config-file and that seemed to be the problem. It was easily fixed after a visit to the homepage of fail2ban and reading the documentation of the new version and its new way of doing things.

Oh, and I kept that extra disk pluged in, no problem! If just everything was this simple!:)

---

