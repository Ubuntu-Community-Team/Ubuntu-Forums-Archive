---
title: "Can I run VB5 in Ubuntu?"
date: 2009-03-07
forum: Programming Talk
---

### Post by col48 on 2009-03-07
I have some hundreds of man-hours invested in a number of programs developed in VB5 under Windows95.  Now that I have switched to Ubuntu8.04 (on a new machine!) I have the source and the .exe files on this machine but no way to develop/debug them further.

Many of these programs run happily via wine in Ubuntu.

But VB5 itself does this
me@me-desktop:~/fromOldPC/oldC/Program Files/VB$ wine vb5.exe
fixme: ole: DllDebugObjectRPCHook stub
fixme:dialog:MSGBOX_DlgProc Help button not supported yet

and quits.
Is this fixable?  Would this be but the first of many such issues?

On the other hand, if I try to install VB5 from the original CD, it gets so far and then tells me it has detected and replaced an old version of Oleaut32.dll and I must reboot Windows (ha!) to continue Setup.  It is clearly lying, as it behaves in exactly the same way next time through.  I am running the setup as me (not root) via wine, ie cd /media/cdrom0 then wine setup.exe.

Has anyone else tried to get VB5 (not VB6) running as a development environment in Ubuntu?  It seems to me it should be doable, but I can't see how to make it happen.

---

### Post by amauk on 2009-03-07
your best bet is probably to use virtualbox (or similar VM app) to run VB5 on Win95 natively

Download virtualbox from here
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Create a new virtual machine, and install Win95 & VB5

---

### Post by Can+~ on 2009-03-07
What about gambas?

---

### Post by cthug on 2009-03-07
can't you run VB with wine?

---

### Post by rye_ on 2009-03-08
I've not tried it myself, but is seems vb6 works through wine once a little tweaking is done (see link).

[link to winehq]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=1325&iTestingId=34165")

---

### Post by col48 on 2009-03-08
> **amauk said:**
> your best bet is probably to use virtualbox (or similar VM app) to run VB5 on Win95 natively

Download virtualbox from here
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

Create a new virtual machine, and install Win95 & VB5

Sounds promising.  Having trouble getting virtualbox to run (issue posted elsewhere).  One day.....

I have the hint from rye_ in mind, too, although winehq makes no comment about vb5.  One day.....

Thanks guys.  I appreciate your support.

---

### Post by RTsagez on 2009-03-28
> **col48 said:**
> I have some hundreds of man-hours invested in a number of programs developed in VB5 under Windows95.  

So do I!

> **col48 said:**
> ... if I try to install VB5 from the original CD, it gets so far and then tells me it has detected and replaced an old version of Oleaut32.dll and I must reboot Windows (ha!) to continue Setup.

I had the same results in ubuntu version 8.10, but all I had to do is to configure wine as "Windows 2000" for the "Default Settings". 

VB5 seems to be working fine (although the software is not in the directory it is supposed to be... mmm...).

Hope it helps!

---

### Post by col48 on 2009-03-30
Thanks RTsagez, that has moved things along a bit, but unfortunately not all the way.  It seems to have let VB5 install from the CD (using cd /media/cdrom then wine setup.exe neither of these as root).  So I restart the computer and try to run VB5
(cd to folder in .wine/drive_c then wine VB5.EXE, again not as root)

But then I get into a loop which seems to revolve around this


```
Backtrace:
=>0 0x7b843a76 in kernel32 (+0x23a76) (0x0033fdc0)
  1 0x7e83b1c6 in ole32 (+0xbb1c6) (0x0033fdf0)
  2 0x7e78a0dc in ole32 (+0xa0dc) (0x0033feb0)
  3 0x010013ac in rpcss (+0x13ac) (0x0033ff08)
  4 0x7b8769c9 in kernel32 (+0x569c9) (0x0033ffe8)
wine: Call from 0x7b843a00 to unimplemented function ole32.dll.I_RemoteMain, aborting
wine: Call from 0x7b843a00 to unimplemented function ole32.dll.I_RemoteMain, aborting
wine: Call from 0x7b843a00 to unimplemented function ole32.dll.I_RemoteMain, aborting
wine: Unimplemented function ole32.dll.I_RemoteMain called at address 0x7b843a00 (thread 00cd), starting debugger...
Unhandled exception: unimplemented function ole32.dll.I_RemoteMain called in 32-bit code (0x7b843a76).

```

The version of OLE32.DLL appears to be the same (date, length) as on my W95 computer, so where do I go from here?

---

