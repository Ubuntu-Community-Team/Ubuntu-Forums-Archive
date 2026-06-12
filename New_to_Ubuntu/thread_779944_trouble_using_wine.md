---
title: "trouble using wine"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by fignig on 2008-05-03
so i'm trying to install counter-strike, and to do that i must install steaminstall.msi and i guess the wine isn't familiar w/ the .msi format? how do i install it?

---

### Post by fhmanas on 2008-05-03
you can install msi with 'wine msiexec /i program.msi'.  Check first in WineHQ for compatibility of your app

---

### Post by angelsguitar on 2008-05-03
> **fignig said:**
> so i'm trying to install counter-strike, and to do that i must install steaminstall.msi and i guess the wine isn't familiar w/ the .msi format? how do i install it?

Hi.

To run the .msi program use the msiexec tool with the /i option in a terminal window.  Using steaminstall.msi, it would look like this:

```
msiexec /i steaminstall.msi
```

See this wiki for more info:

[http://wiki.jswindle.com/index.php/Wine_MSI]("http://wiki.jswindle.com/index.php/Wine_MSI")

Hope this helps.

---

### Post by fignig on 2008-05-03
> **angelsguitar said:**
> Hi.

To run the .msi program use the msiexec tool with the /i option in a terminal window.  Using steaminstall.msi, it would look like this:

```
msiexec /i steaminstall.msi
```

See this wiki for more info:

[http://wiki.jswindle.com/index.php/Wine_MSI]("http://wiki.jswindle.com/index.php/Wine_MSI")

Hope this helps.

preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:msi:copy_package_to_temp failed to copy package L"steaminstall.msi"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002 for L"steaminstall.msi"

that is all i keep getting when i put in that. i have the file d/l'd to the desktop.

---

### Post by fignig on 2008-05-03
and btw, how do i check compatability in winehq? i don't think i would need to b/c i saw a screen shot of the game that i wanted. so i'm sure it has to work.

---

### Post by mc4man on 2008-05-03
> preloader: Warning
[http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)
app db
[http://appdb.winehq.org/](http://appdb.winehq.org/)

edit: for wine stuff ck. here [http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

---

### Post by fignig on 2008-05-03
> **mc4man said:**
> [http://wiki.winehq.org/PreloaderPageZeroProblem](http://wiki.winehq.org/PreloaderPageZeroProblem)
app db
[http://appdb.winehq.org/](http://appdb.winehq.org/)

edit: for wine stuff ck. here [http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)



err:msi:copy_package_to_temp failed to copy package L"steaminstall.msi"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002 for L"steaminstall.msi"
 
this is now what it's saying when i put in the msiexec /i steaminstall.msi

---

### Post by mc4man on 2008-05-03
Are you trying to install steam as outlined here - scroll down - worked fine here
[http://appdb.winehq.org/appview.php?versionId=1554](http://appdb.winehq.org/appview.php?versionId=1554)

---

### Post by fignig on 2008-05-03
> **mc4man said:**
> Are you trying to install steam as outlined here - scroll down - worked fine here
[http://appdb.winehq.org/appview.php?versionId=1554](http://appdb.winehq.org/appview.php?versionId=1554)

how exactly do i do this:
and clicking on Install button. If the Gecko engine doesn't download (servers are down) then download wine_gecko.cab to the "/tmp" directory and point Wine to it (save this as-is to the "/tmp/file.reg" then import with command 'regedit /tmp/file.reg':

[HKEY_CURRENT_USER\Software\Wine\MSHTML]
"GeckoUrl"="z:\\tmp\\wine_gecko.cab"

i put the file wine_gecko.cab in the /tmp folder. and how do i point wine to it and save this as-is? i just don't get the wording. or maybe the concept, but i'm trying to learn.

---

### Post by mc4man on 2008-05-05
@fignig
I just installed steam to hardy a few min. ago (have it on a gutsy)
If your having problems post back while it's still fresh in my head.

edit: basically just run ```
wine iexplore http://winehq.org
``` if you get a pop up with install button click it, you'll know it's installed when you have a wine internet explorer window showing winehq page. (if you just get the winehq page then it's _already_ installed) Then dl the installer file and if it's on desktop run 
```
cd Desktop; wine start SteamInstall.msi
```

---

