---
title: "How to install ndisgtk"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by rcmcivor on 2008-10-27
I just installed Ubuntu 8.04 a couple days ago and am trying to get my wireless network card working. AFAIK I need to use ndiswrapper to use windows drivers. In the help I found I needed to install the ndisgtk package first. I went to 'system-administration-synaptic package manager' and was supposed to select ndisgtk from the list but it wasn't there. Some advice I got was to go to the terminal and type (going from memory):

sudo apt-get install ndisgtk

I did that and got an error message saying 'Couldn't find package ndisgtk'.what do I do now? Also when I finally do get this working does it matter what version of the windows driver I use? (i.e. vista, XP)

Thanks,
Ryan

---

### Post by issih on 2008-10-27
I'm guessing your problem is that you have no internet connection. If you can plug in a hardwire ethernet connection briefly to install ndisgtk then you should find that either of the methods you have already tried will work just fine then.

If you can't get an internet connection that way then fish o:ut your ubuntu install cd and pop it into the cd drive. Now open:

System->Administration->Software Sources

In that dialog tick the box below "Installable from cd rom"

then try installing ndisgtk again.

Hope that helps

---

### Post by rcmcivor on 2008-10-27
I tried the second method before I either uprooted the computer to get it closer to the router or drilled a hole through the wall to get a cable through and it worked!!!

Thanks, I owe you a pint! It wasn't as quick and clean as your instructions suggest but it was what I needed to get on the right track. Thanks again. Now onto the next challenge....

---

### Post by issih on 2008-10-28
Nothings ever as simple as the instructions :)

Anyway glad you sorted it out.

---

### Post by mdavidjohnson on 2011-02-26
Using the Synaptic Package Installer, I tried installing ndisgtk from the 10.04 Alternate install disk. It said two dependencies, ndiswrapper-common and ndiswrapper-utils-1.9, would also be installed. When I clicked "Apply" the install failed - it said it couldn't find a couple of the files.

I then went back and installed the files individually in ndiswrapper-common, ndiswrapper-utils-1.9, ndisgtk order and the installs all completed successfully.

---

