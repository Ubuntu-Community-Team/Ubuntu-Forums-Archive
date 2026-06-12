---
title: "installing updates &amp; printer trouble"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by taylmer on 2008-07-08
Hi,

I have 44 updates which won't install & I'm quite new at ubuntu. It says:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

How do I sort this out? When I go to the Konsole and copy & paste it says that the superuser is the only person who can change it. Who is the superuser?

Also, I have tried to attach my Brother MC-410CN to ubuntu but nothing works and I can't print anything out. Can someone please help me?

Ta muchly,
Tracey

---

### Post by chetan.89 on 2008-07-08
Hi Tracey,
 
When you go to konsole and type those commands, use a "sudo" word before the command which will give you access to the super user.

In your case --> sudo dpkg --configure -a -> in konsole. The super user is like the "Administrator" in windows. The sudo prefix gives the normal users the access to install packages/files.

If you have problems connecting your printer, install the "Printing" software in the Add/Remove applications or any related software. If you have problems finding that software, search for 'printer' in Add/remove applications and you'll get a few packages :).


Regards,
Chetan.


/////////////////////////////////////////////////////////////////////////
Hi,

I have 44 updates which won't install & I'm quite new at ubuntu. It says:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

How do I sort this out? When I go to the Konsole and copy & paste it says that the superuser is the only person who can change it. Who is the superuser?

Also, I have tried to attach my Brother MC-410CN to ubuntu but nothing works and I can't print anything out. Can someone please help me?

Ta muchly,
Tracey
////////////////////////////////////////////////////////////////////////

---

### Post by taylmer on 2008-07-08
Hi Chetan,

Thank you for using "sudo" it seems (hopefully!) to have done the trick!

I forgot to advise I have already tried to install the printer from the disk & it still comes up with problems and doesn't want to install. I keep reading about how to change a command so ubuntu can read the printer but I have no idea how to do that.

Cheers,
Tracey

---

### Post by chetan.89 on 2008-07-08
Try this link --> 
[http://ubuntuforums.org/showthread.php?t=843256](http://ubuntuforums.org/showthread.php?t=843256)

I hope it solves your problem ... :)

Good luck !
Chetan.

---

