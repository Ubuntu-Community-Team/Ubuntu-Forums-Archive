---
title: "ISO Download failure with wget"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by rraj.be on 2008-07-13
I tried to download arch Linux ISO from

[ftp://cle.linux.org.tw/pub/ArchLinux/iso/0.72/arch-0.7.2.iso]("ftp://cle.linux.org.tw/pub/ArchLinux/iso/0.72/arch-0.7.2.iso")

It took 3 days for my internet connection to download 535.5 MiB of ISO.

But when i had 1.5 MiB of download left it showed the message as 

```
raj@raj-desktop:~$ wget -c -r ftp://cle.linux.org.tw/pub/ArchLinux/iso/0.72/arch-0.7.2.iso
--10:42:00--  ftp://cle.linux.org.tw/pub/ArchLinux/iso/0.72/arch-0.7.2.iso
           => `cle.linux.org.tw/pub/ArchLinux/iso/0.72/.listing'
Resolving cle.linux.org.tw... 140.112.8.136
Connecting to cle.linux.org.tw|140.112.8.136|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/ArchLinux/iso/0.72 ... done.
==> PASV ... done.    ==> LIST ... done.

    [     <=>                             ] 818          216.17B/s             

10:44:21 (216.17 B/s) - `cle.linux.org.tw/pub/ArchLinux/iso/0.72/.listing' saved [818]

Removed `cle.linux.org.tw/pub/ArchLinux/iso/0.72/.listing'.
--10:44:21--  ftp://cle.linux.org.tw/pub/ArchLinux/iso/0.72/arch-0.7.2.iso
           => `cle.linux.org.tw/pub/ArchLinux/iso/0.72/arch-0.7.2.iso'
==> CWD /pub/ArchLinux/iso/0.72 ... done.
==> PASV ... done.    ==> REST 561530056 ... done.    
==> RETR arch-0.7.2.iso ... 
No such file `arch-0.7.2.iso'.


FINISHED --10:44:32--
Downloaded: 0 bytes in 0 files
raj@raj-desktop:~$ 

```

I spent 3 complete days for this and i lost the whole thing due to that 1.5 MiB of download which was left.

Any solution please.

---

### Post by phidia on 2008-07-13
Go to [linux tracker]("http://linuxtracker.org/") and download a torrent. Even if a torrent stops you can resume it and since the torrent app will check the file it's less likely to have corruption.

---

### Post by Cappy on 2008-07-13
From the wget man page:
```
     However, if the file is bigger on the server because it's been
     _changed_, as opposed to just _appended_ to, you'll end up with a
     garbled file.  Wget has no way of verifying that the local file is
     really a valid prefix of the remote file.  You need to be
     especially careful of this when using `-c' in conjunction with
     `-r', since every file will be considered as an "incomplete
     download" candidate.

     Another instance where you'll get a garbled file if you try to use
     `-c' is if you have a lame HTTP proxy that inserts a "transfer
     interrupted" string into the local file.  In the future a
     "rollback" option may be added to deal with this case.

     Note that `-c' only works with FTP servers and with HTTP servers
     that support the `Range' header.
```

Probably the unneeded -r that caused the problem.

---

### Post by rraj.be on 2008-07-13
i tried without -r

but the op is

```
raj@raj-desktop:~$ wget -c  ftp://cle.linux.org.tw/pub/ArchLinux/iso/0.72/arch-0.7.2.iso
--15:47:54--  ftp://cle.linux.org.tw/pub/ArchLinux/iso/0.72/arch-0.7.2.iso
           => `arch-0.7.2.iso'
Resolving cle.linux.org.tw... 140.112.8.136
Connecting to cle.linux.org.tw|140.112.8.136|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/ArchLinux/iso/0.72 ... done.
==> SIZE arch-0.7.2.iso ... done.
==> PASV ... done.    ==> REST 561530056 ... done.    
==> RETR arch-0.7.2.iso ... 
No such file `arch-0.7.2.iso'.

raj@raj-desktop:~$ 


```

---

