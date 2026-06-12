---
title: "Install bacula 5.2.4 to ubuntu 9.10"
date: 2014-12-19
forum: New to Ubuntu
---

### Post by raido2 on 2014-12-19
Hello, 

I need to upgrade my bacula 2.2.x verison that is running in ubuntu 9.10 in order to work with bacula 5.2.4 that is running in other server.

When I ran command:

apt-get remove bacula

apt-get install bacula - it will install again bacula 2.2.x version. I can not do apt-get upgrade because of other software running in server.

How can I upgrade to bacula 5.2.4 version in Ubuntu 9.10 without upgrading the whole system?

---

### Post by raido2 on 2014-12-19
When I try to run bacula backup, I get following error.

[COLOR=#000000][FONT=Tahoma]sserver-dir JobId 6089: Fatal error: Storage daemon rejected Job command: 3915 Bad Job command. stat=-1 CMD: JobId=6089 job=server1_full.2014-12-12_15.44.40.03 job_name=server1_full client_name=sserver-fd type=66 level=70 FileSet=serverall NoAttr=0 SpoolAttr=0 FileSetMD5=S4/Y5VxUc8/09S+Wd1+S9D SpoolData=0 WritePartAfterJob=1 PreferMountedVols=1[/FONT][/COLOR]

---

### Post by monkeybrain20122 on 2014-12-19
Ubuntu 9.10??!! It has reached end of life back in April, 2011 hence all its repositories have been taken down long time ago. Please get an up to date supported version of Ubuntu (12.03, 14.04, 14.10)

---

### Post by raido2 on 2014-12-19
But how to update bacula, when updating ubuntu is not possible?

---

### Post by ajgreeny on 2014-12-19
> **raido2 said:**
> But how to update bacula, when updating ubuntu is not possible?
The simple answer is that you probably can't, or not without putting yourself to a huge amount of trouble, and you will still end up with an OS that can not be kept updated as there are no repos available any more.

Why can you not do a clean install and update to a supported version of Ubuntu, or another of the *ubuntu family if you don't want unity desktop?

---

### Post by monkeybrain20122 on 2014-12-19
Bacular is for backup. Why bother upgrading your backup software while the OS you try to backup with it is grotesquely out of date? :)

---

### Post by raido2 on 2014-12-22
[I]I am not trying to backup ubuntu 9.10.

I have set up bacula sd which is running version 5.2.6. And a long time ago configured bacula dir version 2.2.4. Right now when I try to run backup BaculaSD rejects the job with error:
[/I]sserver-dir JobId 6089: Fatal error: 

Storage daemon rejected Job command: 3915 Bad Job command. stat=-1 CMD: JobId=6089 job=server1_full.2014-12-12_15.44.40.03 job_name=server1_full client_name=sserver-fd type=66 level=70 FileSet=serverall NoAttr=0 SpoolAttr=0 FileSetMD5=S4/Y5VxUc8/09S+Wd1+S9D SpoolData=0 WritePartAfterJob=1 PreferMountedVols=1

Right now it is not possible to upgrade ubuntu 9.10 because of the other software running in this ubuntu version. So I think there may be a way to only uprgade bacula-dir version.

---

