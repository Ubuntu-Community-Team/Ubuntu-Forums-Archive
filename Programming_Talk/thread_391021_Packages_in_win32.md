---
title: "Packages in win32?"
date: 2007-03-22
forum: Programming Talk
---

### Post by miketime on 2007-03-22
Does anyone know if dpkg (or something similar) has ben ported or written for win32?  Have had a quick google but can't find anything.

Regards, Mike

---

### Post by thingy on 2007-03-22
If you are after a packaging system in Windows, then you are best off sticking with MSI or freeware installers like Nullsoft's [NSIS.]("http://nsis.sourceforge.net/Main_Page")

> [INDENT]Technically you don't need to buy a toolkit to build MSI packages - the    required tools are available in Microsoft's Platform SDK. Even if you are    using one of the tools listed below you should download the Windows Installer    SDK as it includes the latest documentation from Microsoft and usefuls tools    like Orca.
   License: Free
      [IMG]http://www.installsite.org/images/globeicon.gif[/IMG]    [   Microsoft Windows Installer SDK]("http://www.installsite.org/redirect/microsoft-platformsdk-wininst.htm")
 [/INDENT]


I remember a while back, I went looking for a packaging system for windows and I didn't come up with anything...just news group posts about people wanting to start a project about it.

hmm if you find anything..please do post a link here. :-)

---

### Post by j_g on 2007-03-22
The way to go is with Microsoft Windows Installer (ie, MSI), as mentioned above. This supports system restore points, and full uninstallation under "Add / Remove Programs", as well as other Windows specific support that endusers expect.

Go to Microsoft's website at [http://msdn2.microsoft.com/en-us/library/aa370566.aspx](http://msdn2.microsoft.com/en-us/library/aa370566.aspx) and you can read all the details on this.

To download the installer SDK, see this page:

[http://msdn2.microsoft.com/en-us/library/aa370834.aspx](http://msdn2.microsoft.com/en-us/library/aa370834.aspx)

In particular, you'll want to investigate the Orca.exe tool since this graphical tool helps you create your MSI (install file).

---

