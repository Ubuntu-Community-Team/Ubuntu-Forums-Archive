---
title: "major problem"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by flOOi!ghenTM on 2008-07-10
i've been having some hadrware problem that caused my machine to freeze this was casused because one of my HDD was brocken but after i unpluged it my machine gave me this error at boot:

*Checking root file system
1142
fsck 1.40.8 (13-Mar-2008)
/dev/sda1:clean, 128099/398272 files, 682757/1588419 blocks
                                                                        [ok]
*Checking file systems
1142
fsck 1.40.8 (13-Mar-2008)
fsck ext3:unable to resolve 'UUID=62855c17-fadd-4b7c-85eb-8b4d9767ee09'
fsck died with exit status 8
*File system check failed
A log is being saved in /var/log/fsck/chechfs if that location is writable.
Please reapair the filesystem manualy
*A maintanance shell will now be started 
CONTROL-D will terminate this shell and resume system boot
bash:no job control in this shell
bash: groups:command not found 
bash:lessipip:command not found
bash:The:command not found
bash:dircollors:command not found
bash:command:command not found
bash:The:command not found
user@computer

Another problem that i am having is everytime i reinstall my system and update. After it's fiished i get this error:

E: gnome-applets-data: subprocess post-installation script returned error exit status 134
E: gnome-applets: dependency problems - leaving unconfigured
E: update-manager: subprocess post-installation script returned error exit status 134
E: gnome-games-data: subprocess post-installation script returned error exit status 134
E: gnome-games: dependency problems - leaving unconfigured
E: update-notifier: dependency problems - leaving unconfigured

---

### Post by toupeiro on 2008-07-10
> **flOOi!ghenTM said:**
> i've been having some hadrware problem that caused my machine to freeze this was casused because one of my HDD was brocken but after i unpluged it my machine gave me this error at boot:

*Checking root file system
1142
fsck 1.40.8 (13-Mar-2008)
/dev/sda1:clean, 128099/398272 files, 682757/1588419 blocks
                                                                        [ok]
*Checking file systems
1142
fsck 1.40.8 (13-Mar-2008)
fsck ext3:unable to resolve 'UUID=62855c17-fadd-4b7c-85eb-8b4d9767ee09'
fsck died with exit status 8
*File system check failed
A log is being saved in /var/log/fsck/chechfs if that location is writable.
Please reapair the filesystem manualy
*A maintanance shell will now be started 
CONTROL-D will terminate this shell and resume system boot
bash:no job control in this shell
bash: groups:command not found 
bash:lessipip:command not found
bash:The:command not found
bash:dircollors:command not found
bash:command:command not found
bash:The:command not found
user@computer

Another problem that i am having is everytime i reinstall my system and update. After it's fiished i get this error:

E: gnome-applets-data: subprocess post-installation script returned error exit status 134
E: gnome-applets: dependency problems - leaving unconfigured
E: update-manager: subprocess post-installation script returned error exit status 134
E: gnome-games-data: subprocess post-installation script returned error exit status 134
E: gnome-games: dependency problems - leaving unconfigured
E: update-notifier: dependency problems - leaving unconfigured

Its possible your UUID may have changed.  Try following some of the steps in [this thread]("http://ubuntuforums.org/archive/index.php/t-481742.html"), they might be of assistance to you.

---

### Post by Dynaflow on 2008-07-10
What are the outputs from 

```
df
```

and 

```
nano /etc/fstab
```

[The post above is probably a good bet.  Try that first.]

---

### Post by flOOi!ghenTM on 2008-07-10
10x for the replies i fixed the boot problem but i still get the update errors and don't know why?

---

