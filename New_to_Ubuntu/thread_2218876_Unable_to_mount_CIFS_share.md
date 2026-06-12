---
title: "Unable to mount CIFS share"
date: 2014-04-22
forum: New to Ubuntu
---

### Post by doktor-kill-patient on 2014-04-22
Hi All

I am trying to map/mount a shared folder from my Windows Server 2008 R2 machine to a Ubuntu 12.04 LTS server. The server is part of the domain, and my user account (i.e. mydomain\breakaway) has full access to this share, using this guide: [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

Here is my fstab entry:

```
//mydomain.local/Share1/Folder /smb cifs credentials=/breakaway/.smbcredentials,iocharset=utf8,sec=ntlm 0 0
```

Contents of .smbcredentials:

```
username=mydomain/breakaway
password=mypassw0rd
```

When I run mount -a to mount the share, I get this: 

```
# mount -a
mount error(95): Operation not supported
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

Dmesg shows this:

```
[743504.370318] CIFS VFS: Server requires packet signing to be enabled in /proc/fs/cifs/SecurityFlags.
[743504.370533] CIFS VFS: cifs_mount failed w/return code = -95
```

Not having much luck with this -- any ideas on what it could be?

---

### Post by SeijiSensei on 2014-04-22
You probably need to use the "Kerberized" security model via the "sec=" parameter.  See the [mount.cifs manual page](http://www.samba.org/samba/docs/man/manpages-3/mount.cifs.8.html) for details.  It looks like krb5i includes packet signing.

---

### Post by doktor-kill-patient on 2014-04-22
Hello,

I tried a range of security models, none of htem worked -- they produced this error:

ntlmv2i:
```
[777884.882885] Status code returned 0xc000000d NT_STATUS_INVALID_PARAMETER
[777884.882890] CIFS VFS: Send error in SessSetup = -22
[777884.883017] CIFS VFS: cifs_mount failed w/return code = -22
```

ntlmi:
```
[778026.158836] CIFS VFS: cifs_mount failed w/return code = -22
```

Krb5i:
```
[778139.094476] CIFS VFS: Send error in SessSetup = -126
[778139.094618] CIFS VFS: cifs_mount failed w/return code = -126
```

Can someone please verify the contents of my .smbpasswd file that I am using to pass the creds in are correct? I can't find many references to the actual syntax/formatting of this file. It's up in the original post.

---

### Post by SeijiSensei on 2014-04-22
[This article](http://pvalentino.blogspot.com/2007/10/redhat-cifs-mounting-with-fstab-and.html) suggests using 
```

username=yourname
password=yourpass
domain=win_domain

```
in the credentials file rather than including the domain in the username as Windows does.

A little googling indicates the return codes are not well documented.  Errors on the Windows side are [here]("http://msdn.microsoft.com/en-us/library/ee441884.aspx") if that helps.

---

### Post by doktor-kill-patient on 2014-04-23
Alright now we're getting somewhere :)

```
mount.cifs //myserver.mydomain.com/data /smb -o username=breakaway,dom=mydomain,password=mypassw0rd
```

This has worked.

I  was previously using the DFS namespace (i.e.  \\mydomain\namespace\sharename) but now I am pointing it at the server  direct (i.e. \\myserver\sharename). 

A less than ideal solution, but it works for me.

---

