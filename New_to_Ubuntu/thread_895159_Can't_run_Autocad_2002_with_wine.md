---
title: "Can't run Autocad 2002 with wine"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by nomeparece on 2008-08-19
could anyone help me with this problem:

i'm tryng to run autocad 2002 with wine, the installation works fine, but the program doesn't start...
when i try to run the command in the terminal, this is what it says:

diego@guaton:~$ wine "C:\Archivos de programa\AutoCAD 2002\acad.exe"
err:service:validate_service_config Service L"Vxuntrver" has an unknown service type
err:service:scmdatabase_load_services Invalid configuration of service L"Vxuntrver" - skipping
fixme:ntdll:find_reg_tz_info Can't find matching timezone information in the registry for bias 240, std (d/m/y): 30/03/2008, dlt (d/m/y): 12/10/2008
wine: Call from 0x9285ca to unimplemented function MFC42.DLL.6571, aborting
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x6c1195
diego@guaton:~$ 

so.. it looks like there are several errors. does any one know how to fix them? at WineHQ i've read that autocad 2002 works on wine, so it should be possible to install it, right?
also i followed the steps in [_this_]("http://appdb.winehq.org/objectManager.php?sClass=version&iId=1924") tutorial (spanish), but it still doesn't work.
i don't really know how to view the version of Wine, but i installed it from add/remove, so i assume it's the latest.

so.. any help would be grreat.

---

### Post by rossjman1 on 2008-08-19
From [http://appdb.winehq.org/objectManager.php?sClass=version&iId=1924&iTestingId=24290](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1924&iTestingId=24290)
> Requires the following native dlls to be placed in C:\Program Files\System32\ "MSVCIRT.dll" and "MFC42.dll" 

Edit: It's been a while since I even looked at anything Spanish, and I didn't see that it said the same thing.

---

### Post by nicedude on 2008-08-19
I don't use wine so I can't be much help but I thought you should know that the versions in the repository are rarely the newest versions so I would check that. I see that in the repositories is version 1.0.0 but newest at winehq is 1.1.2 in the development stage. But I also found the following regarding Ubuntu and autocad 2002 which may just be your answer you seek :-)



	
RE: AutoCAD 2002 in ubuntu,
by Chris on Wednesday August 29th 2007, 22:52
The Installation/Setup has screwed up the PATH variable in the following registry key

\\HKEY_LOCALE_MACHINE\System\Current Control Set\Control\Session Mananger\Environment\PATH
Fix this by editing directly the value in ~/.wine/system.reg, or by using regedit. Set this value to "C:\Program Files\Common Files\Autodesk Shared"

Also you requires the following windows dlls to be placed in C:\Program Files\System32\
"MSVCIRT.dll" and "MFC42.dll"
Get these files from a windows installation under windows\system32 or get them from the internet.

After doing these two step Autocad 2000 should run.

Here is a link to where I found it
[http://appdb.winehq.org/commentview.php?iAppId=86&iVersionId=1924&iThreadId=19974](http://appdb.winehq.org/commentview.php?iAppId=86&iVersionId=1924&iThreadId=19974)


If you can't find those DLL's then try here
[http://www.dll-files.com/](http://www.dll-files.com/)

Hope that helps, and goodluck

---

