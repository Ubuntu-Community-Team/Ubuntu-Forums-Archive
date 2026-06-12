---
title: "Migrating old ubuntu 10.04 to a newer installation"
date: 2013-02-07
forum: New to Ubuntu
---

### Post by Drigo on 2013-02-07
So I formatted a new hard drive where I want to have a new clean ubuntu 10.04 installation. However, an older hard drive has all the parameters that I would like to migrate to the newer one (/usr/local/* /home/* /bin/* etc...). I know I can copy folders such as the /usr/local/* to the newer location but what about the system files such as the /home/* or the variables such as $PATH, etc...? 

Any solutions?

---

### Post by elgordodude on 2013-02-07
home is user data and you may move it wherever you'd like. PATH is stored in /etc/profile, it should work if you move it over but you may get a weird error or two.

---

### Post by Impavidus on 2013-02-07
You can always copy the data to an external drive or put the old hard drive in an adapter and copy files back after you reinstalled. This is not equally desirable for all directories:
/bin: If you copy this to your new disk, you won't have a clean install. Better reinstall all packages you still want. Anyway, there shouldn't be much in here that isn't there on a default install.
/home: Good idea to keep, but you may have to clean up some old configs.
/usr/local: Some files may be fit to keep, especially if you reinstall the same version, but...

The most important thing, why do you want a clean install of 10.04? It's almost out of support, you can better upgrade to 12.04 LTS.

(BTW, your PATH, if not using the default, belongs to your configs in /home. Most people never schange the default though.)

---

### Post by dannyboy79 on 2013-02-07
i would strongly suggest moving to the new LTS release 12.04. If you don't like unity, then go with Xubuntu but then install your favorite gnome apps like Gedit, Nautilus and any other apps that are default in Ubuntu. That's what I did. As far as config files, I would just make a backup of all the directories and sub-directories that have config settings files, perform the new install and then boot to a live cd, mount the 2 different hard drives and copy over the old config files to the new install. just my 2 cents.

---

### Post by fantab on 2013-02-07
First of all 10.04 is nearing its end of life, meaning from sometime April 2013 there won't be any official support for 10.04. So it is recommended that you install 12.04 LTS (supported till 2017).  Since you will be doing a clean, fresh install we'd like to encourage you to opt for 12.04 Lubuntu atleast.

If you opt for 12.04 your original question becomes moot.

---

### Post by dannyboy79 on 2013-02-07
> **fantab said:**
> 
If you opt for 12.04 your original question becomes moot.
I disagree, just because he's moving to a new installation and a newer version of Ubuntu doesn't mean he can't use some of the config files. Special care must be taken however that they config files are reviewed as there may be new settings not in the old config file that are in the new one, so a merely replace of the file may be bad, something like a running a diff on the two files could be done and then just only replacing the settings that are in both files and also leaving the new settings in the newer config files.

some of the files that I always copy over from installs are
/etc/hosts
/etc/samba/smb.conf
/etc/exports
/etc/fstab
/etc/ssh/sshd.config
/etc/logrotate.conf

just to name a few

---

