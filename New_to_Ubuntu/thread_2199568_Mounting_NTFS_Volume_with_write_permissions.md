---
title: "Mounting NTFS Volume with write permissions"
date: 2014-01-14
forum: New to Ubuntu
---

### Post by bbourdet on 2014-01-14
Hello 

I have been trying to mount a NTFS share with CIFS. I have been following this guide:[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

I am able to mount the drive, however, I cannot write to it. What am I doing wrong? I have tried to chmod it, but no good. Help!

EDIT: This is my fstab entry: //servername/sharename  /media/windowsshare  cifs  username=msusername,password=mspassword,iocharset=utf8,sec=ntlm  0  0

---

### Post by bab1 on 2014-01-14
> **bbourdet said:**
> Hello 

I have been trying to mount a NTFS share with CIFS. I have been following this guide:[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

I am able to mount the drive, however, I cannot write to it. What am I doing wrong? I have tried to chmod it, but no good. Help!

EDIT: This is my fstab entry: //servername/sharename  /media/windowsshare  cifs  username=msusername,password=mspassword,iocharset=utf8,sec=ntlm  0  0

You need to add your Ubuntu  uid and gid to gain the Linux permissions you want.  The username=msusername,password=mspassword is for Samba,  See the pertinent part of the** mount** man pages```

Mount options for ntfs
       iocharset=name
              Character set to use when returning file names.  Unlike VFAT, NTFS suppresses names
              that contain nonconvertible characters. Deprecated.

       nls=name
              New name for the option earlier called iocharset.

       utf8   Use UTF-8 for converting file names.

       uni_xlate={0|1|2}
              For 0 (or `no' or `false'), do not use escape sequences for unknown Unicode charac&#8208;
              ters.  For 1 (or `yes' or `true') or 2,  use  vfat-style  4-byte  escape  sequences
              starting  with ":". Here 2 give a little-endian encoding and 1 a byteswapped bigen&#8208;
              dian encoding.

       posix=[0|1]
              If enabled (posix=1), the filesystem distinguishes between upper  and  lower  case.
              The  8.3  alias names are presented as hard links instead of being suppressed. This
              option is obsolete.

       uid=value, gid=value and umask=value
              Set the file permission on the filesystem.  The umask value is given in octal.   By
              default, the files are owned by root and not readable by somebody else.


```

---

### Post by Habitual on 2014-01-14
I've had great success with ```
**rw,uid=1000,gid=100,dmask=022,fmask=133 0 0**
```
Your uid and gid will be different.

---

