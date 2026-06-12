---
title: "contributing to Universe repository?"
date: 2005-06-01
forum: Packaging and Compiling Programs
---

### Post by jfdill_2 on 2005-06-01
My noble goal is to make a .deb package of [eaccelerator](http://eaccelerator.net/HomeUk) to accompany the egroupware packages from the Universe repository.  I have found .deb packages for eaccelerator vs. PHP5, but egroupware doesn't work with PHP5 as of yet, and I am not sure if that version will work with PHP4 applications (although I expect to find out).  Plus I also want to learn the process.  Since someone has already made .deb I think I can probably hack what they have done to some extent.  Figuring out what the package ought to be called may be the hard part.

Question #1:  Is there an idiot's guide to get started making .deb packages?

Question #2:  Is there a HOWTO on contributing software to the Universe repository?

Thanks in advance.

---

### Post by az on 2005-06-01
By definition, you cannot be an idiot and make a deb package.  You need to read the debian policy manual.  Read the new maintainers guide.  Also, look up the MOTU on the wiki.  They take care of the Universe.

#ubuntu-motu on freenode.


Don't worry, you are not an idiot.  Debian packaging is not so bad.  The reason that deb packages are so good, is that people like you will take a lot of time making sure that nothing can go wrong.  That is why it is so complicated.

---

### Post by jfdill_2 on 2005-06-01
[QUOTE=azz]By definition, you cannot be an idiot and make a deb package.  You need to read the debian policy manual.  Read the new maintainers guide.  Also, look up the MOTU on the wiki.  They take care of the Universe.

#ubuntu-motu on freenode.


Don't worry, you are not an idiot.  Debian packaging is not so bad.  The reason that deb packages are so good, is that people like you will take a lot of time making sure that nothing can go wrong.  That is why it is so complicated.[/QUOTE]
Thanks for the pointers.  I found there is a php4-eaccelerator package in dotdeb which is what I wanted.  If I can find the source package, I think it might not take a whole lot of work to get it ready for Universe, at least not as much work as trying to package something that has never been set up for a deb before.

---

### Post by jfdill_2 on 2005-06-01
[QUOTE=jfdill_2]My noble goal is to make a .deb package of [eaccelerator](http://eaccelerator.net/HomeUk) to accompany the egroupware packages from the Universe repository...[/QUOTE]
Now after all that, I found that [mmcache](http://turck-mmcache.sourceforge.net/index_old.html)  is already in the Universe repository and works pretty well right out of the box!  It's great to keep finding stuff that is in Universe that I didn't know was in there.  But I really am still going to work on something, when I find something that isn't done and I can't find something else that is just as good to do what I need...

Edit: FYI the package name is turck-mmcache

---

### Post by cybergypsy on 2005-10-29
[QUOTE=jfdill_2]Now after all that, I found that [mmcache](http://turck-mmcache.sourceforge.net/index_old.html)  is already in the Universe repository and works pretty well right out of the box!  It's great to keep finding stuff that is in Universe that I didn't know was in there.  But I really am still going to work on something, when I find something that isn't done and I can't find something else that is just as good to do what I need...

Edit: FYI the package name is turck-mmcache[/QUOTE]

Can you tell us what you did to get this running ?

I have apt-get`ted (?) the package , added the extension to both the */etc/php4/cli/php.ini* and */etc/php5/cli/php.ini* files , restarted apache2 and the mmcache.php page still shows it as not installed.

I cannot see any events in apache error.log or syslog

Any help would be appreciated.

cybergypsy

---

### Post by jfdill_2 on 2005-10-30
[QUOTE=cybergypsy]Can you tell us what you did to get this running ?

I have apt-get`ted (?) the package , added the extension to both the */etc/php4/cli/php.ini* and */etc/php5/cli/php.ini* files , restarted apache2 and the mmcache.php page still shows it as not installed.

I cannot see any events in apache error.log or syslog

Any help would be appreciated.

cybergypsy[/QUOTE]
I'm using Hoary with php4 only and apache2.  It was several months ago I don't really remember what I did.  It looks like php.ini is the only thing that I changed.
```
root@nerds:/etc/php4/apache2 # rcsdiff php.ini
===================================================================
RCS file: RCS/php.ini,v
retrieving revision 1.2
diff -r1.2 php.ini
1075a1076,1116
>
> zend_extension="/usr/lib/php4/20020429/mmcache.so"      ; turck-mmcache
> mmcache.shm_size="2"                                    ; turck-mmcache
> mmcache.cache_dir="/var/cache/turck-mmcache"            ; turck-mmcache
> mmcache.enable="1"                                      ; turck-mmcache
> mmcache.optimizer="1"                                   ; turck-mmcache
> mmcache.check_mtime="1"                                 ; turck-mmcache
> mmcache.debug="0"                                       ; turck-mmcache
> mmcache.filter=""                                       ; turck-mmcache
> mmcache.shm_max="0"                                     ; turck-mmcache
> mmcache.shm_ttl="0"                                     ; turck-mmcache
> mmcache.shm_prune_period="0"                            ; turck-mmcache
> mmcache.shm_only="0"                                    ; turck-mmcache
> mmcache.compress="1"                                    ; turck-mmcache
>
> ;extension="eaccelerator.so"
> ;zend_extension="/usr/lib/php4/eaccelerator.so"
> ;zend_extension="/usr/lib/php4/20020429/eaccelerator.so"
> ;zend_extension_ts="/usr/lib/php4/eaccelerator.so"
> ;extension="eaccelerator.dll"
> ;zend_extension_ts="c:\php4\eaccelerator.dll"
> ;zend_extension="c:\php4\eaccelerator.dll"
> ;eaccelerator.shm_size = "1"
> ;eaccelerator.cache_dir = "/tmp/eaccelerator"
> ;eaccelerator.enable = "1"
> ;eaccelerator.optimizer = "1"
> ;eaccelerator.debug = "0"
> ;eaccelerator.check_mtime = "1"
> ;eaccelerator.filter = ""
> ;eaccelerator.shm_max = "0"
> ;eaccelerator.shm_ttl = "0"
> ;eaccelerator.shm_prune_period = "0"
> ;eaccelerator.shm_only = "0"
> ;eaccelerator.compress = "1"
> ;eaccelerator.compress_level = "9"
> ;eaccelerator.keys = "shm_and_disk"
> ;eaccelerator.sessions = "shm_and_disk"
> ;eaccelerator.content = "shm_and_disk"
> ;eaccelerator.admin.name="yourusername"
> ;eaccelerator.admin.password="yourpassword"
> extension=ldap.so

```

---

