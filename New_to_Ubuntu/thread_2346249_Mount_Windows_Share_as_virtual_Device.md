---
title: "Mount Windows Share as virtual Device"
date: 2016-12-12
forum: New to Ubuntu
---

### Post by mrcxb on 2016-12-12
Hello,

I wonder if it's possible to mount any windows share as a virtual device on ubuntu server?

I added my shared folder in fstab for automounting and it works well. 

Here is my goal: I need to mount my shared windows sharing folder as a device like sda ,sdb or something else.

I have a specific software that only store data on physical drives. That's why I am not able to use my mounted folders or shared folders.

Here's the line that I added into fstab to mount my shared folder on my ubuntu server automatically:
//192.168.0.10/test /media/test cifs username=test, [COLOR=#333333]username=test,password=123456,iocharset=utf8,sec=ntlm  0  0

So, can I link my shared folder as a drive on ubuntu server? I need somthing like sdb1, sdc1 etc....

Regards

John[/COLOR]

---

### Post by TheFu on 2016-12-13
> **mrcxb said:**
> Hello,

I wonder if it's possible to mount any windows share as a virtual device on ubuntu server?

No. Pre-existing file systems cannot be mounted that way, as far as I know.

> **mrcxb said:**
> I added my shared folder in fstab for automounting and it works well. 
 Exactly, but it doesn't like it when Windows is off. Use autofs to mount as-needed.

> **mrcxb said:**
> 
Here is my goal: I need to mount my shared windows sharing folder as a device like sda ,sdb or something else.
 CIFS shares are NOT block devices.  You might be able to convince Windows to share storage with iSCSI or AoE.  Probably only available from Windows-Server or more expensive NAS devices ... or any Linux. ;)  Just be aware that fast networking is required - at least GigE. No wifi.  I'm amazed at what people try to do over wifi.  Most people would have a decided storage network, not shared for any other purpose.  I physically separate my storage network using separate NICs and a stupid GigE unmanaged switch.

> **mrcxb said:**
> 
I have a specific software that only store data on physical drives. That's why I am not able to use my mounted folders or shared folders.  Ah ... yep. Block device needed.
[https://www.howtoforge.com/iscsi_on_linux](https://www.howtoforge.com/iscsi_on_linux)
[https://technet.microsoft.com/en-us/library/cc772367(v=ws.11).aspx](https://technet.microsoft.com/en-us/library/cc772367(v=ws.11).aspx) - I'm not much of a Windows guy.

There are lots and lots of other block storage methods for Linux. Lots, but they don't play nice with non-Linux OSes running directly on hardware.

---

### Post by mrcxb on 2016-12-14
Thank you TheFu. You helped me much. I guess I need to figure out another solution.
Regards

---

