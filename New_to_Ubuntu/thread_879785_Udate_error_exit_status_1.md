---
title: "Udate error exit status 1"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by nanogeek on 2008-08-04
Hi:

I just did a fresh install of Hardy after swapping hard drives on my 386 machine. Everytime I do an update or try to install a new package I get the following error(s)

E: ufw: subprocess post-installation script returned error exit status 1
E: gdm: subprocess post-installation script returned error exit status 1

The updates or the package seems to be installed properly, but these error messages irk me.

Can someone help me out here?

Nanogeek

---

### Post by dhughes on 2008-08-04
I don't really know but I'm fairly sure an error status of 1 is a good thing, anything other than a 1 means a failure of some sort.

---

### Post by limasierra on 2008-08-04
ufw and gdm are related to your firewall (ufw) and your login window (gdm).
If you are an administrator check the firewall by running the following command in the terminal, without the quotes: "sudo ufw enable"

Also as administrator, go to "Main Menu > System > Administration > Login Window" and edit it to your needs.

If you can do both, i guess you shouldn't worry about it.

---

### Post by Silver Knight on 2010-04-10
I realize this is a rather ancient thread, but I came across this while researching a current issue I'm having with Ubuntu and thought I would point out a small detail in case anyone else finds this thread so that folk will not be misinformed by the comment below.

> **dhughes said:**
> I don't really know but I'm fairly sure an error status of 1 is a good thing, anything other than a 1 means a failure of some sort.

Generally an error status of 0 (zero) is a good thing (no failures/problems), and anything else other than zero is either a failure of some sort, or something has happened that the user (or script receiving the non-zero exit status code) should be aware of.

I only point this small detail out purely in the hopes that it be informative and useful, and I intend no disrespect to the commenter whom I've quoted above.

Regarding the original poster's issue: (again, in case someone finds this while seeking a solution to a similar problem.)

The error message being received means that something in the post-installation script portion of those two packages is failing to complete in a way the script knows how to handle.  I had a similar issue with the Squid web cache.  It was (for some unknown reason) refusing to restart when the post-installation scripts of related packages told it to, and so was giving me that same error.  The workaround in that particular case was to manually stop the Squid daemon before installing related packages, as it would not REstart, but it was entirely willing to START if not already running.  Perhaps something similar is happening with the two packages mentioned above?  ufw and gdm being unable to restart for some reason when told to by the post-installation scripts in related packages?

Well...  That's all the help I have to offer on this post/thread.  Afraid I don't know more'n that about this...  I hope that what I've offered here is useful enough to help someone sometime with something...  ;)

---

