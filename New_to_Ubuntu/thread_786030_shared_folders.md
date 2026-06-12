---
title: "shared folders"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by Matt26 on 2008-05-07
where is the shared folders option in ubuntu 8.04?  i used to have it under System, Preferences in 7.10 but i don't see it there anymore.  thanks.

---

### Post by Monicker on 2008-05-07
Places -> Sharing Options

There is also a small glitch with it.  Read this:

[http://ubuntuforums.org/showthread.php?t=773851]("http://ubuntuforums.org/showthread.php?t=773851")

---

### Post by Matt26 on 2008-05-07
> **Monicker said:**
> Places -> Sharing Options

There is also a small glitch with it.  Read this:

[http://ubuntuforums.org/showthread.php?t=773851]("http://ubuntuforums.org/showthread.php?t=773851")

hmmm.. i don't seem to have that option under my Places menu.. might i have to enable it somewhere?

---

### Post by asrai on 2008-05-07
Try from nautilus - right click on the folder you want to share and towards the bottom there should be 'sharing options'.

---

### Post by Monicker on 2008-05-07
> **Monicker said:**
> Places -> Sharing Options

There is also a small glitch with it.  Read this:

[http://ubuntuforums.org/showthread.php?t=773851]("http://ubuntuforums.org/showthread.php?t=773851")

> **Matt26 said:**
> hmmm.. i don't seem to have that option under my Places menu.. might i have to enable it somewhere?

I know its there on a fresh install.  I think someone who did an upgrade told me they didn't see it there either.  Was yours an upgrade or fresh install?

---

### Post by Matt26 on 2008-05-07
> **asrai said:**
> Try from nautilus - right click on the folder you want to share and towards the bottom there should be 'sharing options'.

thanks, that allowed me to share a folder, but i still cannot see the option for viewing my other existing folder shares in the Places or System menus?

---

### Post by EMCGFX on 2008-05-07
All I due is edit my /etc/samba/smb.conf file manually. Of course other specs in the smb.conf file should be configured correctly for this to work. Like your workgroup.

I just add desired folder:

[Test]
path = /home/test
available = yes
browsable = yes
public = yes
writable = no

---

### Post by asrai on 2008-05-07
I might be totally off base here, but try Places/Network and see if you can see the shares from there.

---

### Post by Matt26 on 2008-05-07
thanks for the suggestions- i guess my question really comes down to: is there still a place to view and manage ubuntu shares?  like before my upgrade to 7.10, i could go to System, Administration menu (might have been Preferences) and there was a Shared Folders option that allowed me to view all my existing folder shares and create new ones or manage the ones i had- does this still exist anywhere?

---

