---
title: "wine/msi/lost cause?"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by knmcnulty on 2008-06-17
Hello,
I'm trying to install an msi file through wine and can't seem to get it to work. I don't know if I'm just not doing it correctly or if it simply won't work. It's a virtual classroom that I need in order to work (I tutor for Tutor.com). The file is called "Tutor.com Classroom Setup.msi" The requirements of said file are normally XP with Service Pack 2, Dot Net Framework, and IE. I've never had problems with it in Windows, but have since decided to boot the dual boot and switch completely over to Linux. It seems like I might have to go back to the dual boot to get this classroom to work. I've downloaded it to the desktop and used the code: [COLOR="DarkRed"]msiexec /i Tutor.com Classroom Setup.msi[/COLOR] which tells me it can't be installed and to check the file path (which makes me wonder if I'm simply doing this wrong). Any help would be great! I really don't want to have to have Windows cluttering up my system for one lousy program!

-Kristin

---

### Post by lok on 2008-06-17
To install from msi files with wine you have to install Windows Installer. I'm not sure how easy that is to do manually but Wine-doors can set it up for you automatically. Just install wine-doors and select it from the list.

Sadly this won't allow you to simply double click on the msi(not on my computer anyway) but if you run winefile and navigate to where the file is. Double click on it here and it should run fine.

Hope that helps
Good luck

Edit: actually msiexec seems to work fine here now

---

### Post by joshsmith on 2008-06-17
give us the full input and output of anything done in terminal (you should always do this)
so run the command and give us the output

give us the output of
ls 
too

dont use wine-doors as a first go. this is probably doable without it

---

### Post by mivo on 2008-06-17
An additional problem may be that your software requires the .NET framework. My attempts to get even minimally complex .NET applications to run did not work out. That was prior to the 1.0 RC versions, though.

---

### Post by knmcnulty on 2008-06-17
Okay, when I try to install Windows Installer from Wine-Doors it seems to install fine until I get this at completion:[COLOR="DarkRed"] Package Update Completed--The following errors were reported--Installation Failed--Installing Application--msiexec version 2[/COLOR]

So then I type into terminal with the downloaded msi on my desktop:  [COLOR="DarkRed"]msiexec /i Tutor.com Classroom Setup.msi[/COLOR]
 and get this:
[COLOR="DarkRed"]fixme:spoolsv:serv_main (0 (nil))
err:msi:copy_package_to_temp failed to copy package L"Tutor.com"
fixme:msi:MSI_OpenDatabaseW open failed r = 80030002 for L"Tutor.com"[/COLOR]

When I type in ls here's what I get:
[COLOR="DarkRed"]Desktop    dwhelper  Music     Public     Videos
Documents  Examples  Pictures  Templates[/COLOR]


Which doesn't seem right at all...

---

