---
title: "Wine/steam trouble"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by jjstein on 2008-04-29
I'm trying to install steam with wine but I get this error every time I try to install it:



```

jon@jon-laptop:~/Desktop$ sudo wine SteamInstaller.msi
[sudo] password for jon:
wine: /home/jon/.wine is not owned by you

```

What am I doing wrong? Also, while I'm at it, is it even worth it to attempt to install steam? I know it didn't work in the past (to the best of my knowledge) but does it actually work now?

---

### Post by PmDematagoda on 2008-04-29
Don't use sudo, it's rather silly and in any case is the cause of the problem, just run the command without giving it sudo privileges and you should be fine.

---

### Post by jjstein on 2008-04-29
Thanks but I've encountered a new problem. I got this:
```

jon@jon-laptop:~/Desktop$ wine SteamInstall.msi
wine: could not load L"Z:\\home\\jon\\Desktop\\SteamInstall.msi": Bad EXE format for 
jon@jon-laptop:~/Desktop$ fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetSecurityInfo stub
fixme:wtsapi:WTSEnumerateProcessesA Stub (nil) 0x00000000 0x00000001 0x7e157780 0x7e157784
fixme:wtsapi:WTSFreeMemory Stub (nil)
fixme:spoolsv:serv_main (0 (nil))
fixme:ntdll:NtSetInformationToken 0xb4 12 0x7e157448 4
jon@jon-laptop:~/Desktop$ 

```

Does this mean I need an .exe file? If this is the case, I couldn't find one anywhere. Perhaps I just didn't look right?

---

### Post by PeterJS on 2008-04-29
Try:
```

wine msiexec /i SteamInstal.msi

```
Steam and Source games both run pretty well under wine.

---

### Post by jjstein on 2008-04-29
God. Typed that in and got this:
```
jon@jon-laptop:~$ wine msiexec /i SteamInstall.msi
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetSecurityInfo stub
fixme:advapi:SetSecurityInfo stub
fixme:wtsapi:WTSEnumerateProcessesA Stub (nil) 0x00000000 0x00000001 0x7e14b780 0x7e14b784
fixme:wtsapi:WTSFreeMemory Stub (nil)
fixme:ntdll:NtSetInformationToken 0xb4 12 0x7e14b448 4
fixme:spoolsv:serv_main (0 (nil))
err:msi:copy_package_to_temp failed to copy package L"SteamInstall.msi"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002 for L"SteamInstall.msi"
jon@jon-laptop:~$ fixme:wtsapi:WTSEnumerateProcessesA Stub (nil) 0x00000000 0x00000001 0x7e14b780 0x7e14b784
fixme:wtsapi:WTSFreeMemory Stub (nil)

```

---

### Post by PmDematagoda on 2008-04-29
Perhaps you could use something like [wine-doors]("http://www.wine-doors.org/wordpress/?page_id=3") to install Steam for you. Or maybe you could ask this problem on the [Wine forums]("http://forum.winehq.org/").

---

### Post by jjstein on 2008-04-29
Well I got wine doors but haven't the slightest clue how to use it. I had to download the tarbal because the DEB refused to download so i followed the instructions, and it appeared to install.....now what? I can't find any trace of anything.

---

### Post by PmDematagoda on 2008-04-29
See if you can execute wine-doors with:-
```
wine-doors
```

---

### Post by jjstein on 2008-04-29
Oh my god I finally made this work. I typed 
```
wine start SteamInstall.msi
```
and it is now installing. Thanks for all the help

---

