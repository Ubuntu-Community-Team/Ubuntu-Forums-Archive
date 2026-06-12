---
title: "Boot problems after upgrading to 15.04"
date: 2015-04-30
forum: New to Ubuntu
---

### Post by mla2 on 2015-04-30
[FONT=Arial][SIZE=2]Hi,[/SIZE][/FONT]
[SIZE=2]I am a complete novice user with linux, so excuse my ignorance[/SIZE].

 [SIZE=2]After upgrading to 15.04, during the booting process i received the following:[/SIZE]
[SIZE=2][  0.7439301 ACPI PCC  Probe failed[/SIZE]
[SIZE=2]Starting version 219 [/SIZE] 

 “[SIZE=2][13.4741251 k10temp 000:00:18.3: unreliable CPU thermal sensor; monitoring disabled[/SIZE]
 [SIZE=2]Welcome to emergency mode![/SIZE]
 [SIZE=2]After logging in, type “journalctl -xb” to view system logs, “systemctl  rebout” to rebout, “systemctl default” or ^D to rout@...”[/SIZE]

[SIZE=2]Logging in  “journalctl -xb”  systems logs errors:[/SIZE]

 [SIZE=2]> ACPI PCC probe failed.[/SIZE]
[SIZE=2]> 13.4741251 k10temp 000:00:18.3: unreliable CPU thermal sensor; monitoring disabled.[/SIZE]
[SIZE=2]> fsck failed with error code 4.[/SIZE]
[SIZE=2]> failed to start file system check on boot device.[/SIZE]
[SIZE=2]> name server cannot be used: Temporary failure in name resolution [/SIZE] 

[SIZE=2]PS: Dual boot with windows 7[/SIZE]
[SIZE=2]AMD Phenom Quad-Core[/SIZE]
 [SIZE=2]What should i do?  [/SIZE] 
 [SIZE=2]I need help[/SIZE][FONT=arial]
Thanks in advance  [/FONT]

---

### Post by sandyd on 2015-04-30
Hi, can you boot using a livecd, and follow the instructions at [https://help.ubuntu.com/community/Boot-Info#Standard_method:_from_an_Ubuntu_disc](https://help.ubuntu.com/community/Boot-Info#Standard_method:_from_an_Ubuntu_disc) to produce a report.

Thanks!

---

### Post by naroyce on 2015-05-08
I also have this type of issue: [http://paste.ubuntu.com/11023029/](http://paste.ubuntu.com/11023029/)
Dual-boot with Vista
64-bit Ubuntu

It started with me upgrading 14.10 I think to 15.04. Eventually something borked and when the system restarted, this "emergency-mode" came up.

Then I wiped those partitions and replaced it with a fresh install of 15.04.
I had been installing programs and eventually the system COMPLETELY froze: No window or mouse activity. Even the keyboard lock LED indicators wouldn't turn off/on, so no magic sysreq could happen.
I think even the reset button didn't do anything at first, but holding it a little longer (reset, not power button), the computer shut off.
Once booted back up, it too went into "emergency-mode".

EDIT:
  Cause: fstab
    Commenting out the 2 entries I added to the fstab "fixed" that "emergency-mode" issue I just had. Now I just have to figure out what I did wrong.
    #UUID=425241035240FCE3	/media/wd40	fuseblk	defaults	0	2    #UUID=BCBE82DABE828C98	/media/vista	fuseblk	defaults	0	3
    I created those mount point subdirectories myself just in case, but also deleted them while in emergency-mode, but to no avail.
    I chose "fuseblk" over "ntfs" because that is the "type" "mount" says they currently are.
    I think the "pass" values could have remained "0" from what I read, but didn't think it would hurt to set the order.

---

### Post by mla2 on 2015-05-09
[COLOR=#000000]Thank you all,[/COLOR]

 [COLOR=#000000]I re-installed [/COLOR][COLOR=#000000]Ubuntu 15.04[/COLOR][COLOR=#000000] with a [/COLOR][COLOR=#000000]L[/COLOR]iveDVD and boot error &#8220;seems&#8221; to be solved, but now I have new error with LibreOffice Writer.

 _Strange trouble in LiberOffice Writer with Ubuntu 15.04:_
 
 
 When I select  a bloc text in _Writer _using  _mouse_ or _shift+__arrow keys_  the entire OS freezes completely, and I have to shut down computer with power button or keys Atl+SysRq+B.

 
 
 Then, I tried with a LiveCd 15.04 and same error ocurred, when i selectet text in Writer.

 
 
 So, I check the same type &#8220;select text&#8221; in LibreOffice Writer in Windows and it works fine.
 
 
 
 
 What is the problem in Ubuntu?
 
 
 Wired USB optical mouse and Keyboard

Thank you

---

