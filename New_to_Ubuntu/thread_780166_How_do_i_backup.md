---
title: "How do i backup"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by lucky.developer on 2008-05-03
ok...i wanna start fresh with a frest installation of ubuntu in my system.

i am currently having Gutsy gibbon. i want to back all my installed software and my home folder....i dont want to install and set certain settings again in my fresh ubuntu...

how do i do that...

please help

---

### Post by pro003 on 2008-05-03
ok, i think i now what you mean, but this is what i do when i want to back up appz and updates so i won't have to do that again when i have to reinstall ubuntu.

open: 

```
/var/cache/apt/archive
```  

--> select all --> copy to some ntfs partition...

when i reinstall first thing i do is open nautilus # gksu nautilus  and copy all deb packages from ntfs partition to 


```
/var/cache/apt/archive
```

as for settings... i don't know...

you can also take a look at this:

[https://wiki.ubuntu.com/UbuntuHomeBackup](https://wiki.ubuntu.com/UbuntuHomeBackup)

---

### Post by lswest on 2008-05-03
you can tar your home folder/save it someplace (include hidden files) and your settings will be saved.  To restore just untar/copy back over.  I'd recommend tarring it, as it preserves permissions.

---

### Post by halitech on 2008-05-03
you could use remastersys to backup and then restore just your personal settings

---

### Post by Malta paul on 2008-05-03
I used 'Quickstart' before upgrading works well.
[http://quickstartdownload.pbwiki.com/QuickStart+Help](http://quickstartdownload.pbwiki.com/QuickStart+Help)
Hope this helps :)

---

### Post by mdpalow on 2008-05-10
> **Malta paul said:**
> I used 'Quickstart' before upgrading works well.
[http://quickstartdownload.pbwiki.com/QuickStart+Help](http://quickstartdownload.pbwiki.com/QuickStart+Help)
Hope this helps :)

Thanks Malta :)

However, that link is only to the help file/website.

If you want to download QuickStart, you should go to:

[**http://www.quickstart.freeforums.org/**]("http://www.quickstart.freeforums.org/")

or... click on my link below.

---

