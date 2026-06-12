---
title: "Time Change????"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by fishman78 on 2008-07-22
Hi Everyone

  I have a weird question.  When ever I go back into Windows my time is off by exactly 5 hours.  Even if I boot into Ubuntu just long enough to restart back into windows, my windows time is off by 5 hours.  All my time zones are correct and I've updated the time I don't know how many times.  It's not a huge issue, but it's an annoyance.  Any thoughts on this one?  Thanks!

Fishman78

---

### Post by scragar on 2008-07-22
try toggling if windows retrives time settings from a network, that may be the problem. Other than that nothing I can suggest, other than setting your time 5 hours off in the oposite direction...

---

### Post by fishman78 on 2008-07-22
My Windows syncs it's time with the usual windows.time server.  But not right at boot up.  So the time is wrong until it updates or I change it.  As for changing the time 5 hours back, I tried that too:lolflag: but it doesn't work more than once.  Any other thoughts?  Thanks!

Fishman

---

### Post by northern lights on 2008-07-22
Had this happen last year. Well, time was 9hrs off, but that's probably cause you and me are in different zones.

Your BIOS most likely works with UTC (Coordinated Universal Time) and you're Windows thus assumes it's got to add/subtract those 5 hrs.

Switch clock settings in your BIOS and you should be fine.

---

### Post by fishman78 on 2008-07-22
> **northern lights said:**
> Had this happen last year. Well, time was 9hrs off, but that's probably cause you and me are in different zones.

Your BIOS most likely works with UTC (Coordinated Universal Time) and you're Windows thus assumes it's got to add/subtract those 5 hrs.

Switch clock settings in your BIOS and you should be fine.

Hey Northern Lights,

   I checked the BIOS and it's funny.  The time changes in the BIOS only when I log out of Ubuntu.  Loggin out of Windows, the time doesn't change.  I don't see a UTC option though.  Anything else I might look at?  Thanks!

Fishman78

---

### Post by northern lights on 2008-07-22
mkey.

Most likely then you're windows uses what is called "local time" and your Ubuntu uses "UTC".

To make your Windows calculate its time from the BIOS clock correctly, open the "Run" dialog from the start menu and run "regedit".

Navigate to "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\TimeZoneInformation"

right-click and select "New > DWORD value". Name it "RealTimeIsUniversal" and give it the hexadecimal value "1".

Hopefully fixed.

[EDIT]
If that doesn't solve it, an adequate solution should be found somewheres in [https://help.ubuntu.com/community/UbuntuTime]("https://help.ubuntu.com/community/UbuntuTime")
[/EDIT]

---

### Post by fishman78 on 2008-07-22
> **northern lights said:**
> mkey.

The Ubuntu net installer asks and warns you at setup of this exact problem. 

Really?  See that's what I get for not reading the material first! ](*,):redface:

---

### Post by northern lights on 2008-07-22
> **fishman78 said:**
> Really?  See that's what I get for not reading the material first! ](*,):redface:

Well, the NetInstaller warns you, I'm not too certain the LiveCD does, which is what you probably used.

Anyway, if the registry entry doesn't fix it, the documentation should have several solutions in it.

---

### Post by Oldsoldier2003 on 2008-07-22
> **northern lights said:**
> mkey.

Most likely then you're windows uses what is called "local time" and your Ubuntu uses "UTC".

To make your Windows calculate its time from the BIOS clock correctly, open the "Run" dialog from the start menu and run "regedit".

Navigate to "HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\TimeZoneInformation"

right-click and select "New > DWORD value". Name it "RealTimeIsUniversal" and give it the hexadecimal value "1".

Hopefully fixed.

[EDIT]
If that doesn't solve it, an adequate solution should be found somewheres in [https://help.ubuntu.com/community/UbuntuTime]("https://help.ubuntu.com/community/UbuntuTime")
[/EDIT]

+1. The Url to the wiki page has a download for the reg file. It works just fine last time I checked.

---

### Post by kattman on 2008-07-22
Open /etc/default/rcS in a text editor with root privileges. Find the line that says 'UTC=yes' and change it to 'UTC=no'. Then reboot.

---

### Post by Oldsoldier2003 on 2008-07-22
For a variety of reasons its generally easier and better for you to change windows to use UTC rather than change Ubuntu OS X or any Linux distro to use local.

---

### Post by fishman78 on 2008-07-22
Thank you to all that helped.  Unfortunately the change in Windows didn't work.  It looks like when Ubuntu exits it changes the time in the BIOS.  I didn't even know it could do that.  Anyway, I changed Ubuntu to Local Time and all seems to be fixed.  I supposed when DST comes I'll have to change yet another clock:rolleyes:  Thanks again for all your help!!

Fishman78

---

### Post by northern lights on 2008-07-23
> **fishman78 said:**
> Thank you to all that helped.  Unfortunately the change in Windows didn't work
Wicked. Neither my post nor the apparently downloadable .reg file?
Anyhoo, fair enough if the Ubuntu change did the trick.

> **fishman78 said:**
> I supposed when DST comes I'll have to change yet another clock
That's one of the reasons why Oldsoldier and me advised to make Windows accept UTC rather than Ubuntu local, as UTC switches to and from DST automatically...

---

