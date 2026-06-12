---
title: "Can Ubuntu do this?"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by Zeph79 on 2008-10-20
Hey everyone, I work for the local government and I took on a job that is pretty crazy here.   Lots of different departments on workgroups with no domain or anything.


I could go on and on about how messed up this network is but Ill skip it and go right to the question.


Can Ubuntu act as a primary windows domain controller?  If not, could you tell me a version of linux that would do the job?


Nothing real fancy.  I need basic authentication and perhaps DHCP and DNS.   Print server would be nice on it too.


The network I have been thrown into has no domain and many different departments.  They have shared folders everywhere which can be viewed by different departments that I dont want shared like that...   

I don't beleive (from my light reading) that a linux server acting as a windows domain controller has that granular control with things such as group policy.  If I am wrong, please tell me cause that would be the "selling" point for me!   

Have a good day

---

### Post by bodhi.zazen on 2008-10-20
Yes most any version of Linux can do these things. The question is how much time do you wish to spend learning a new OS ?

Options may include Ubuntu, Debian Centos, and perhaps Novell (OpenSUSE).

I would point you here :

[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

[https://help.ubuntu.com/](https://help.ubuntu.com/)

And the respective documentation for other distros.

If you get stuck at any step, let us know.

---

### Post by aeiah on 2008-10-20
you're a little bit limited in terms of active directory and group policy with linux as far as i know, and depending on how much they're paying you, how experienced you are with linux compared with windows server 2003 / 2008, and how much time you have you may be better off just (*gasp!*) using windows server.

i believe SLES and redhat have tools that can replace active directory and group policy completley, but whether those have been translated to CentOS, fedora, opensuse and linux as a whole you'll have to look in to. almost all the time, whatever can be done in one distribution can easily be done in another so it doesnt really matter which distro you choose, although certain things are easier in certain distros.

---

### Post by Zeph79 on 2008-10-20
Thanks a lot!

I dont mind learning an OS.   Of course it will take time and the implementation of this domain controler isn't on a strict timeframe.   

I will read the links you sent me, looks like there is a lot of good stuff in there.  

Ill be sure to hang out and read the forums too about the OS

---

### Post by Iowan on 2008-10-20
Samba has options to be set up as PDC - also is designed to share Windows files - AND control shares by user/group, etc.  Samba should be available on any of the aforementioned Linux variants.  LDAP is another option you can research... in your "spare" time.

---

### Post by igknighted on 2008-10-20
I would strongly recommend using something like SME Server (a centos-based distro), or one of the major RPM distro's (Fedora, Mandriva or OpenSuse).  SME Server has a walk-through wizard that will basically set everything up for you, but if you want something different try fedora-directory-server (on fedora or centos), Mandriva Directory Server (very nice), or whatever Suse's is these days (probably the best graphical tools for this task).

Nothing will beat the ease of a Windows server at this task though, but that could be pricey depending on how many clients you have.  As a government thought I would think you could get steep discounts on the MS software.

---

### Post by HittingSmoke on 2008-10-20
> **igknighted said:**
> I would strongly recommend using something like SME Server (a centos-based distro), or one of the major RPM distro's (Fedora, Mandriva or OpenSuse).  SME Server has a walk-through wizard that will basically set everything up for you, but if you want something different try fedora-directory-server (on fedora or centos), Mandriva Directory Server (very nice), or whatever Suse's is these days (probably the best graphical tools for this task).

Nothing will beat the ease of a Windows server at this task though, but that could be pricey depending on how many clients you have.  As a government thought I would think you could get steep discounts on the MS software.

I would check this last suggestion first. I worked on a military base a while back and we could get MS software for a fraction of the retail price. Might be the same for your office and would save you a lot of time.

---

### Post by jemate18 on 2008-10-20
for dhcp type this in terminal
```
sudo apt-get install dhcp3-server

```

---

