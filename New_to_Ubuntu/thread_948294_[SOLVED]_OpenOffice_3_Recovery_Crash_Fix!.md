---
title: "[SOLVED] OpenOffice 3 Recovery Crash Fix!"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by randy78 on 2008-10-15
After going around and around in the document recovery loop/crash with the newest OpenOffice (3), I have decided to document my steps and post the resolution in hopes that it will help many of our Linux brethren :)

I went through the following:
Completely uninstalled OpenOffice 2 and the installation of OpenOffice 3
I installed OpenOffice 3 (sudo dpkg -i *.deb) from within the DEBS folder
I then installed desktop integration from the desktop-integration folder

I renamed .openoffice.org2 to openoffice.org2.backup

I deleted the Recovery.xcu file

I did: OOO_FORCE_DESKTOP=gnome

When I'd start OpenOffice from shell (soffice) and (soffice -writer), it immediately went right into Document Recovery mode and gave this output in Bash:
terminate called after throwing an instance of 'com::sun::star::uno::RuntimeException'
terminate called after throwing an instance of 'com::sun::star::uno::RuntimeException'

I also had made sure that the .openoffice and .openoffice2 folders were not owned by root

Finally, I found this post:[http://www.nabble.com/-Linux--OOo3RC2-Installation-Issues-Workaround-td19695985.html]("http://www.nabble.com/-Linux--OOo3RC2-Installation-Issues-Workaround-td19695985.html")

I followed the instructions (deleted .openoffice.org folder and renamed .openoffice.org2.backup back to .openoffice.org2)

*note that these folders are hidden by default in your home directory, so once you're there just press control+h to show the hidden files ;)

Works like a charm now.

WHOOHOOO!

Hope this helps some people!
:guitar:

---

### Post by tone77 on 2008-10-30
worked great for me

---

### Post by randy78 on 2008-10-30
Glad to help!

---

### Post by Maxtorm on 2009-04-06
An alternative, as long as you don't care about any of your settings:
```
rm -rf .openoffice.org
rm -rf .openoffice.org2
```

---

### Post by Frijolie on 2009-09-29
Thanks!

---

### Post by Dngrsone on 2009-11-29
I had to install a copy of OOo 3.1.1 next to an existing 3.1.0 installation (because I suddenly needed the database app) and I ran into this problem when trying to use write, spreadsheet, etc... basically any of the 3.1.0 apps that were already installed.

This fix rectified the situation!  Thanks a bunch.

---

### Post by NoBugs! on 2010-02-27
I also noticed that "recover document" infinite loop with Openoffice 3.1. Installing 3.2 as described [here]("http://www.ubuntugeek.com/how-to-install-openoffice-3-2-in-ubuntu.html") fixed it. However, it also changed the open/save dialogs.

---

### Post by tiggsy on 2010-08-22
None of these methods works, partly perhaps because I'm already on 3.2 

As this is marked solved, I'm starting another thread "Open Office 3 Infinite Recovery/Crash loop" so if you're looking for an answer and this thread doesn't fix it, suggest you look for that one.

---

