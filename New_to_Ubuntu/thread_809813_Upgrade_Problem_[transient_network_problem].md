---
title: "Upgrade Problem [transient network problem]"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Jabz.biz on 2008-05-27
Hi, my update manager says:

"**Not all updates can be installed**"

The updater also gives me various possible reasons for that problem like (among others) "previous upgrade did not complete", or "problems with some of the installed software". ...kinda vast.

When I select "partial upgrade" I get an error as well: 


"**Error authenticating some packages**

It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages."

The list of packages is loooong...


apport
apport-gtk
gdm
gnome-keyring
libgnome-keyring0
libpam-gnome-keyring
linux-backports-modules-2.6.24-17-generic
linux-backports-modules-hardy-generic
linux-headers-2.6.24-17
linux-headers-2.6.24-17-generic
linux-headers-generic
linux-image-2.6.24-17-generic
linux-image-generic
linux-ubuntu-modules-2.6.24-17-generic
python-apport
python-problem-report


I tried to find solutions to that problem on the net...did not really work. 
Any ideas from you guys? 
Thanks for your help. 
J

P.S.: This may also be of help finding a solution: [http://ubuntuforums.org/showthread.php?t=787754](http://ubuntuforums.org/showthread.php?t=787754)

---

### Post by sayakb on 2008-05-27
Well the first problem comes when you have selected all four update checkboxes. The recommended updates may clash with some proposed or unsupported updates. Just check the first two (important and recommended) to avoid such clashes.

---

### Post by Jabz.biz on 2008-05-27
Hey, thanks for the tipp. I`m installing one after another,...it seems to work. Can you explain to me a bit more detailed how you could see/ knew that!? I wanna understand it, in case something similar happens again. Thanks.

---

### Post by Dazed_75 on 2008-05-27
I just had a similar issue.  I upgraded from 7.10 to 8.04 ubuntu one day last week.  The only issue I had was Firefox 3 beta not supporting googlesync.  Hence, I uninstalled it and reinstalled Firefox 2.0.14.  I have been operating for several days with no issues.

Today I had recommended updates and when I went into update manager I also got the box saying:

**"Not All Updates Cane be Installed"**

and giving [probably] the same generic list of potential reasons.  After looking for info and at logs and such, I decided it was probably because I have moved back to an earlier Firefox.  So I canceled the "partial upgrade" and everything seemed fine and still does.

I did however, bring up update manager again and got that same dialog box again.  This time I clicked on the partial upgrade assuming I would be able to cancel it.  That is what I did after shoeing the details of what would have been done.  To my surprise, there was nothing about Firefox listed.  There were some of the linux image and headers like in jabz.biz's post but nothing about apport or python stuff.  I did see some references to graphics libs.  

Anyway, I don't know if this info is any help in figuring this out.  I still canceled the partial upgrade and still see no problems.

---

### Post by Jabz.biz on 2008-05-28
Hmm,.. interesting. I did nothing with firefox 3b. I already develop CSS3 sites and applications and need it. :)

However,  I still have three updates that I cannot install for some reason:

- linux-backports-modules-hardy-generic
- linux-headers-generic
- linux-image-generic

I can see them in the update manager but I cannot mark or download them. :confused:

---

