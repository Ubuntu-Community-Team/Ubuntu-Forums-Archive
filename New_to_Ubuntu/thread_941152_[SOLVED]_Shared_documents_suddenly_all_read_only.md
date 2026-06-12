---
title: "[SOLVED] Shared documents suddenly all read only?????"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by Kellemora on 2008-10-07
Hi Gang

I have been sharing documents all month, no problems.

I went to edit the ones I sent this evening and ALL of them are read only on the Ubuntu end of the share.  Not on the originating end.

The only thing I did differently was instead of placing them on the originating ends shared folder, I saved them directly to the Ubuntu machines shared folder.  But I have done this in the past no problems either.

I've done at least 10 searches and the only things relevant or Samba and I don't have an issue with Samba configuration settings.

I have resent tonights documents both ways now, direct to Ubuntu Shared Folder and also pulled from originating computers shared folder.  Same problem.

The only changes tonight were a Nautilus upgrade we all probably received.

Any ideas?????

Thanks
Gary

---

### Post by Ripfox on 2008-10-07
I have been using a program called Lanshark with no problems (AT ALL)

It's on getdeb.net

---

### Post by gpsmikey on 2008-10-07
Two things come to mind -- 1) you didn't by chance save them as a different user on the server and you are hitting ownership issues or 2) somehow the file system has been mounted read only or 3) you changed a password and are running into ownership/credential validation issues (yeah, I know that was three, but what the heck :) )

mikey

---

### Post by Kellemora on 2008-10-08
Hi Gang
After facing this problem this morning after a good nights sleep, I finally tracked down what caused it and fixed it.  Only took about 5 hours of work before I found a simpler solution, hi hi............

One CANNOT place a file in the shared folder residing on another machine, else it belongs to NOBODY!  Going into Root can allow you to redo the Permissions, one document at a time.  Doing the folder has no affect on the documents in it.

The quick n easy solution, ONLY put shared documents in the shared folders on the originating computer and then DRAW those documents from there and put them on the machine you want them on, then all permsissions stay intact.

Personally I would consider this problem a BUG in Ubuntu, because it does not happen on Debian, CentOS or RedHat.  And once you DO send a file to another computer it makes all the files in that folder belonging to NOBODY.

In any case, now that I know WHAT the problem is and how to avoid it, Case Solved!  It's just a SHAME I lost about 12 hours of work trying to figure it out!

TTUL
Gary

---

