---
title: "Getting to that NTFS partition from remote XP computer"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by makato on 2008-05-02
Hi, this is my first post. Looking forward to familiarizing myself with the Linux terminal environment. 

I started on DOS after all, executing simple commands, like change directory, copy, etc. Mainly to run DOS games like Prince of Persia. :lolflag:
After the years, I lost touch with command based UI with the availability of Windows and now I'm looking forward to migrate to the Ubuntu environment.

I've been fiddling around with LINUX commands now for about a week, setting up a server with my old asus A7N8X rig. I've got 2 SATA harddisk on it. I followed the instructions on "The Perfect Server" through Putty. (Thank god Putty allows me to copy and paste!)
[http://howtoforge.com/perfect-server-ubuntu8.04-lts](http://howtoforge.com/perfect-server-ubuntu8.04-lts)
I assume that during that process, I wiped out one harddisk to make it EXT3. The other still remains as NTFS (I hope I didn't wipe it too!)

The question now is, now what? My end goal is to be able to retrieve those files in my NTFS drive from my other newer window XP computers and also allow some those files on NTFS to be available via FTP from work. Please help out a noob. :(

PS: I'm learning the Active Directory environment at work too! The work server provides emailing, printing and roaming profiles. So I guess something equivalent in Hardy Heron Server would be nice to have at home. :guitar:

---

### Post by Xiong Chiamiov on 2008-05-02
If you're sharing files from Linux to Windows, you'll need Samba. [[guide1]("https://help.ubuntu.com/community/SettingUpSamba")] [[guide2]("http://ubuntuforums.org/showthread.php?t=202605")].

---

### Post by makato on 2008-05-02
Thanks, I knew it's something to do with SAMBA. I've tried samba with openLDAP with :
[http://howtoforge.com/openldap-samba-domain-controller-ubuntu7.10](http://howtoforge.com/openldap-samba-domain-controller-ubuntu7.10)

Not much luck getting ldap to start for some reason. So I reinstalled server with CD. Maybe the versions are different. But I'll try again.

Btw, how do I put stuff from my NTFS harddisk so I can access it via FTP from anywhere?

---

### Post by superprash2003 on 2008-05-02
you could try proftpd .. its quite a good ftp server software.. also install gproftpd.. its the GUI for proftpd.. and it makes it easier for you to configure your FTP server..

---

### Post by makato on 2008-05-03
> This will be my third reinstallation of Ubuntu Hardy Server edition. Wish me luck.

Quite frankly, I'm getting very frustrated. I started with PHP and I learnt it straight away in 3 days. But this is getting tiring. 2 weeks now gone to waste plus a couple of hundred megs of download with apt-get. My own fault for being greedy, I guess. :evil:

From now on, I'm only having ssh, samba and nothing else on my server. I'll start learning from there.

I've now successfully mapped my **homes ~#**share on  my (no monitor, no keyboard) ubuntu server to H: in mapped network drive in Windows XP. Now how do I proceed to get to other hard disk? :confused:

I've got 2 HDD remember?
SCSI A NTFS - storage hdd
SCSI B EXT3 - ubuntu server OS hdd

I got to the ~# directory on SCSI B, how do I access SCSI A from my remote Windows XP?

---

### Post by makato on 2008-05-03
Anyone? I'm sure I'm not the first person to try setting up a linux based file server for home in an XP enviroment. My googling skills fail me this time.

---

