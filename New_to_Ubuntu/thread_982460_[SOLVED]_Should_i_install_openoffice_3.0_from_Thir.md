---
title: "[SOLVED] Should i install openoffice 3.0 from Third-Party Source?"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by jack_harper2007 on 2008-11-14
Hi everyone i just installed the latest version of "Ubuntu Tweak" (i got the .deb package from GetDeb) and in the Third-Party Sources list is OpenOffice 3.0, the thing is should i wait until OpenOffice 3.0 is available from the official sources or do you guys think is a good idea to install it from Third-Party sources?

I really want to hear your opinions on this one ;)

Thanks!!

---

### Post by epswinde on 2008-11-14
If you're really keen on using OO.o 3.0, then you can go to their website and download the .deb for it.  Just make sure that you remove 2.4 before you install, or else a Bad Thing will happen to your menus (you'll have to launch 3.0 from the command line - not that its the end of the world, but can be a pain).

---

### Post by PilotJLR on 2008-11-14
It's a question of whether you want the OO.o 3 features...

OO.o 3 won't be included with Ubuntu until the 9.04 release (as far as I am aware), so you won't be normally receiving it with Hardy or Intrepid.

There is a repository for it, though... at least for Intrepid.
[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

I've been using version 3 since it was released, and it's terrific.

---

### Post by binbash on 2008-11-14
ubuntu is not a rolling distro so you cant see new openoffice till next release.

---

### Post by GepettoBR on 2008-11-14
I have both running on my 8.10 laptop, and I honestly can't tell you the difference. Then again, I only use Writer, and the more basic functions of Spreadsheet and Presentation, so you might find something that I didn't.

---

### Post by baruch60610 on 2008-11-15
I recommend that you not install it, unless you've got some compelling need for new features it has.  When you install things without using the official sources, you are inviting problems with dependencies and possibly with failure to make important updates.  When you make all your installations through the package manager, you have most of these tasks automated, meaning there is much less chance of a conflict.

---

### Post by asgard_command on 2008-11-15
I installed it with this third party ppa third party source.

[http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu)

EDIT: Follow the link in PilotJLR's comment for full instructions on using my method.

If you add that to your software sources then you get the open office 3 update via your package manager the same as any other update.

I'm not sure what Ubuntu Tweak uses but it is probably similar.

Open Office 3 is in full release it's not a beta or anything you are not likely to have any problems. I certainly haven't and have been using it since day one of Intrepids release.

---

### Post by swoody on 2008-11-15
> **PilotJLR said:**
> There is a repository for it, though... at least for Intrepid.
[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

Wow! Thanks for that link, it worked perfectly!! :D

---

### Post by jack_harper2007 on 2008-11-15
Thanks everyone for the help i'm going to install OpenOffice, i'm really curious to try out the new features ;)

PilotJLR the link that you provided us was very useful thanks!!!!

> **PilotJLR said:**
> 
There is a repository for it, though... at least for Intrepid.
[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

### Post by Sef on 2008-11-15
OOo 3 should likely be available from the backports, but not sure when it will be.

---

### Post by philinux on 2008-11-15
> **binbash said:**
> ubuntu is not a rolling distro so you cant see new openoffice till next release.


This is slightly misleading since apps like OO3 can be backported and probably will.

[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

