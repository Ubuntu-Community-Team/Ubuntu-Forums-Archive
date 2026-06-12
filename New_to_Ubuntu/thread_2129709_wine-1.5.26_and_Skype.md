---
title: "wine-1.5.26 and Skype"
date: 2013-03-27
forum: New to Ubuntu
---

### Post by Elen on 2013-03-27
Please help. What's the problem?

```
elen@home:~/.wine/drive_c/Program Files/Skype/Phone$ wine ./Skype.exe
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:heap:HeapSetInformation 0x110000 1 (nil) 0
fixme:ole:CoInitializeSecurity (0x464e10,-1,(nil),(nil),6,2,(nil),12352,(nil)) - stub!
fixme:advapi:RegisterEventSourceW ((null),L"SkypeUpdate"): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0001,0x00000064,(nil),0x0000,0x00000000,(nil),(nil)): stub
fixme:advapi:DeregisterEventSource (0xcafe4242) stub
fixme:ole:CoResumeClassObjects stub
err:ole:TLB_ReadTypeLib Loading of typelib L"uc.tlb" failed with error 2
```


And open windows: Error Runtime error 217 at 00543A01

---

### Post by uzumakifahim on 2013-03-27
Why you are trying to run Skype using wine??? Skype has native Ubuntu version, which works great.

---

### Post by mastablasta on 2013-03-27
Skype won't work in wine.

use the Skype for linux version.

---

### Post by Elen on 2013-03-27
I need to run Skype plug-in that works with Skype for Windows

---

### Post by uzumakifahim on 2013-03-27
> **Elen said:**
> I need to run Skype plug-in that works with Skype for Windows

Which Skype plug-in do you want to use?

---

### Post by mpw on 2013-04-21
Hello,

I have the same problem right here.

The point is, with the windows version of Skype, you can connect your Skype account to your Facebook account in order to do Facebook video calls. Until now there is no way to video call someone who has only Facebook.

I guess the most common solution would be, to fix wine to run the Skype Windows version.

Bye
MPW

---

### Post by Impavidus on 2013-04-21
No surprise with Microsoft owning both Skype and part of Facebook. I don't think Microsoft has any intention to make this work in Linux. Be happy that there still *is* Skype for Linux.

---

