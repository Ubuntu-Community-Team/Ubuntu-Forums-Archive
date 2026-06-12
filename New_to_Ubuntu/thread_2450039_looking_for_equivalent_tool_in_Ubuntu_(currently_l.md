---
title: "looking for equivalent tool in Ubuntu (currently leaving Windows)"
date: 2020-09-06
forum: New to Ubuntu
---

### Post by marklopez9 on 2020-09-06
Hi,

I'm trying out Ubuntu as I work on leaving Windows. I just have a question though.

So in Windows, there's this sfc /scannow tool used via command prompt to check the OS integrity. It checks the system files for any corruption and attempts to fix it if there are.

Is there an equivalent tool in Ubuntu to do this? I just want to make sure my installation is not corrupted in any way. Thanks in advance.

---

### Post by deadflowr on 2020-09-06
Ubuntu runs file system checks periodically using fsck.
This happens at boot.
Can be done manually.
See: [https://help.ubuntu.com/community/FilesystemTroubleshooting]("https://help.ubuntu.com/community/FilesystemTroubleshooting")

---

### Post by marklopez9 on 2020-09-06
> **deadflowr said:**
> Ubuntu runs file system checks periodically using fsck.
This happens at boot.
Can be done manually.
See: [https://help.ubuntu.com/community/FilesystemTroubleshooting](https://help.ubuntu.com/community/FilesystemTroubleshooting)

Hey there,

Thanks for replying. I've seen a Youtube video about fsck and they described it as somewhat more comparable to the scan disk utility, which checks for disk errors rather than system files (although I'm not so sure if that video uploader is a reliable source).

So to clarify, by file system check you mean a HDD diagnostic check or OS files integrity check?

---

### Post by Holger_Gehrke on 2020-09-06
'fsck' is a check of logical integrity of the file system comparable to 'scandisk' or 'chkdsk'.

If you want to verify that files installed to the system have not been manipulated, there are md5sum files for all installed packages in /var/lib/dpkg/info/ which you can use with for example 'md5sum -c /var/lib/dpkg/info/linux-tools-common.md5sums'. Since the files contain relative paths, you need to have '/' as your current working directory when executing that command. These checksums are installed from the deb-files, they are part of the control-archive in the package.

Holger

---

### Post by SeijiSensei on 2020-09-06
What kind of "corruption" are you concerned about? System files are all stored in directories that ordinary users cannot alter. Unless you actively do something as the root user (in Ubuntu, via the sudo command), nothing in those directories will change.  Updates will obviously alter those files, but you need to run updates as root. And as long as you update from the Ubuntu repositories, those files won't be corrupted.

Are you worried about some type of virus or malware? That's pretty much a non-issue on Linux.

---

### Post by &amp;KyT$0P# on 2020-09-06
For the "check" part, you might read [this thread]("https://ubuntuforums.org/showthread.php?t=2414765") for some ideas.

---

### Post by marklopez9 on 2020-09-07
> **SeijiSensei said:**
> Unless you actively do something as the root user (in Ubuntu, via the sudo command), nothing in those directories will change.  Updates will obviously alter those files, but you need to run updates as root. 

Yes, I plan on actively doing something because I am working on leaving Windows, which means I will be playing with it a lot and most likely break a lot of things along the way. When I do end up breaking something, I'd like to know if there's a utility which can automatically fix it for me so that will be my first go-to solution. I don't really mind researching for a fix when something breaks, but if there's a faster way to reverse any "oops" moment, I'd like to know what it is.

And yes, I am also concerned about files getting corrupted when something goes haywire during updates. And so I asked.

> **SeijiSensei said:**
> Are you worried about some type of virus or malware? That's pretty much a non-issue on Linux.

Although there aren't a lot of Linux malware out there in the wild, they still exist and present some risk. But back to my question, it's not the reason why I asked. Besides, there are mitigation options for that (since you mentioned it) like chkrootkit and rkhunter, which I've read in the guides available at the SANS Institute, along with ClamAV.

---

### Post by marklopez9 on 2020-09-07
> **Holger_Gehrke said:**
> If you want to verify that files installed to the system have not been manipulated, there are md5sum files for all installed packages in /var/lib/dpkg/info/ which you can use with for example 'md5sum -c /var/lib/dpkg/info/linux-tools-common.md5sums'.

Thanks @Holger_Gehrke. This sounds like exactly what I'm looking for. I'll keep this in my notes for future reference. Greatly appreciated. :D

---

### Post by marklopez9 on 2020-09-07
> **halogen2 said:**
> For the "check" part, you might read [this thread]("https://ubuntuforums.org/showthread.php?t=2414765") for some ideas.

I checked out the thread. This also looks useful when the point of failure is right after doing an update. I'll keep this in my notes.

Thanks @halogen2! :KS
I

---

### Post by ActionParsnip on 2020-09-07
Why do you need an equivelent to "sfc /scannow". The command in Windows rarely fixes anything at all. I've been advised by Microsoft engineers numerous times and it's never made a bit of difference.
Why do you have such a burning requirement for a tool like this?

---

### Post by CatKiller on 2020-09-07
> **marklopez9 said:**
> Yes, I plan on actively doing something because I am working on leaving Windows, which means I will be playing with it a lot and most likely break a lot of things along the way. When I do end up breaking something, I'd like to know if there's a utility which can automatically fix it for me so that will be my first go-to solution. I don't really mind researching for a fix when something breaks, but if there's a faster way to reverse any "oops" moment, I'd like to know what it is.

Fiddling with things that you don't understand, and having misaligned intuitions from being conditioned to do things the Windows way, are stages that many users go through, and they do have the potential to break things. Many users here have already passed through that phase.

The potentially-breaking changes that you're going to make, though, are to *text files*. It's trivial to make a copy of them before you fiddle. When things ultimately go pear-shaped, it's a matter of moments to move it back even if you only have a command line or, in really dire circumstances, a live USB to work from, and your machine is magically repaired.

Failing that, a reinstall-and-restore-from-backups takes about 20 minutes.

---

### Post by ActionParsnip on 2020-09-07
[http://manpages.ubuntu.com/manpages/xenial/man1/check-all-the-things.1.html](http://manpages.ubuntu.com/manpages/xenial/man1/check-all-the-things.1.html)

Maybe.....

---

### Post by rsteinmetz70112 on 2020-09-07
If you are actually looking to use Linux and stay with packages in the Ubuntu repositories you should not have any major problems. Depending on the issues you encounter there are lots of tools in Linux to find and fix things, depending on the issue.
I'd suggest diving in and if possible dedicate a computer to Ubuntu and work your way off Windows. I think you'll find Linux has more and better tools than Windows and Linux lets you know what is happening far better that windows. When you have a problem come back here and report the symptoms people are generally very helpful.

---

### Post by SeijiSensei on 2020-09-07
> **marklopez9 said:**
> Yes, I plan on actively doing something because I am working on leaving Windows, which means I will be playing with it a lot and most likely break a lot of things along the way.
For at least the first year or two, you don't want to play with any files that you cannot access as an ordinary user except maybe for configuration files. As CatKiller says, make a backup copy of any file you want to change.  Ordinary users can access their home directories and /tmp.  That's it. There are no other "user-modifiable parts."

The usual refrain applies here: Linux is not Windows.

---

