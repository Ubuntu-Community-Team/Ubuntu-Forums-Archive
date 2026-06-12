---
title: "Teamviewer starts but has no display"
date: 2015-03-30
forum: New to Ubuntu
---

### Post by Derek_Carr on 2015-03-30
Hi, I've installed Teamviewer with no problem, checked that the daemon is running - it is - and started Teamviewer, from the icon and also from the terminal as root but there is no report and nothing shows at all (checked all three screens). Has anyone any idea what is going on and how to get it to show something, please?

---

### Post by slickymaster on 2015-03-30
See if this can be of some help: [Teamviewer 8 and 9 Won't Show GUI]("http://teamviewerforums.com/index.php?topic=2028.0")

---

### Post by Derek_Carr on 2015-03-30
It was a thought, but I haven't got an Intel processor - it's a rather old AMD one. I have a feeling it might be a wine problem, so I'm installing it again now (it's on a different machine to this) and we'll see how it goes.

Right, so I installed wine, which seem to work OK although there was an error message about fonts. I ran TeamViewer with that from Windows (an old version 9 which I must update later). It ran, but I couldn't connect to it - something about permissions. So I've come to the conclusion that TeamViewer for Linux is broken as far as my system is concerned, and I'll just have to run Windows (XP) and forget about xubuntu for the time being. If TeamViewer bring out a new version, I'll give it another go.

---

### Post by Vladlenin5000 on 2015-03-30
Again, I have never had any problem with Teamviewer. That said here are a few additional comments (but no solution, sorry):

1. Trying an old version might work - as in you have a GUI - but it won't connect to newer versions on the computers you want to access remotely. From experience, we must always run the latest version on both ends.
2. Although Teamviewer is indeed a Windows software wrapped in a standalone WINE (both *.deb and *.rpm versions), using the Windows installer with WINE isn't meant to work. One user reported success that way in slickymaster's link but I doubt he/she really tested the connection (having a GUI is must but isn't enough).

---

### Post by Derek_Carr on 2015-03-31
It's working! From your suggestions, I thought, 'well the GUI comes up with Wine and version 9, even if the connection doesn't work, so perhaps version 9 for linux might work.' So I tried it. I got a 'deb' package I wasn't sure what to do with, so I put that on one side for now, and downloaded and ran the tar.gz version 9, and it worked. So, a bit of research and I found I needed Gdebi to install it. I installed that and it worked. I have version 10 running in Windows 7 and version 9 in xubuntu and they seem quite happy.

So Teamviewer 10 is broken for xubuntu, so should I mark this thread as 'solved' or not? 

Many thanks to you Vladlenin5000 and I hope that answers your question grammy_john.

---

### Post by slickymaster on 2015-03-31
> **Derek_Carr said:**
> It's working! From your suggestions, I thought, 'well the GUI comes up with Wine and version 9, even if the connection doesn't work, so perhaps version 9 for linux might work.' So I tried it. I got a 'deb' package I wasn't sure what to do with, so I put that on one side for now, and downloaded and ran the tar.gz version 9, and it worked. So, a bit of research and I found I needed Gdebi to install it. I installed that and it worked. I have version 10 running in Windows 7 and version 9 in xubuntu and they seem quite happy.

So Teamviewer 10 is broken for xubuntu, so should I mark this thread as 'solved' or not? 

Many thanks to you Vladlenin5000 and I hope that answers your question grammy_john.
Please follow the link in my sig to mark the thread solved.

---

### Post by Derek_Carr on 2015-03-31
So it's not really 'solved' if you have to install an older version, but I see where you are coming from, so perhaps I should.

---

### Post by Vladlenin5000 on 2015-03-31
> **Derek_Carr said:**
> So it's not really 'solved' if you have to install an older version, but I see where you are coming from, so perhaps I should.

+1

I have it installed (current version) in Ubuntu 14.04, 14.10, 15.04. Also in Manjaro with XFCE and KDE so, supposedly, it isn't even a problem with XFCE (or Xubuntu for that matter) but a problem in a particular system.
It should be tested - there are plenty Xubuntu users out there - before assuming it's "broken in Xubuntu".

---

### Post by Derek_Carr on 2015-03-31
No - fair enough - I should say that it's broken in my system with xubuntu and see if anyone jumps in and says otherwise. You're right, one system is not the same as another so you can never say anything quite so categorical. Anyway, we have a work-around which does the job for me.

---

