---
title: "failed upgrade please advise"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Repus on 2008-04-28
please help

[LIST]
[*]upgrade from 7.10 to 8.04 failed
[*]file browse doesn't work anymore (flashes open and closed on screen several times)
[*]updater doesn't work any more, just says it cant upgrade from hardy to gutsy
[*] synaptics says this -> (E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. E: _cache->open() failed, please report.) unfortunately that command just spews pages of errors.
[*]and the list goes on...
[/LIST]

I would try a reinstall after backup up some directories but I don't know how without using the file browser. If anyone could offer advise on how to fix the above or how to backup my data so I can install from cd I would greatly appreciate it

Thanks in advanced

---

### Post by mapes12 on 2008-04-28
Can you get a terminal open to run command line commands??

---

### Post by Repus on 2008-04-28
> **mapes12 said:**
> Can you get a terminal open to run command line commands??

I can.

---

### Post by OffAxis on 2008-04-28
> updater doesn't work any more, just says it cant upgrade from hardy to gutsy
How did you initiate the upgrade? by editing the sources.list file? by running a sed script? by using the update manager..? 
hardy should be the upgrade; hardy is 8.04 and gutsy is 7.10


you can copy any files you need to backup from the command line with cp. It's either Ctrl + F1 or Alt + F1 to open a terminal (I can't remember at the moment).

```
cp source/path/filename destination/path/name
```

it'll also take the -R switch to copy folders recursively (folders within folders).
```

cp -R /home/mine/ /backup/folder/
```

---

### Post by Repus on 2008-04-28
> **OffAxis said:**
> How did you initiate the upgrade? by editing the sources.list file? by running a sed script? by using the update manager..? 
hardy should be the upgrade; hardy is 8.04 and gutsy is 7.10


Thank you. 

[LIST]
[*]The upgrade was done by hitting the upgrade button on the update manager. It said it was a partial upgrade but didnt suggest that that would be an issue. 
[*]Im currently burning my home dir to disc via dd and backing it up over a network via a share.
[/LIST]

I would prefer to fix the issue rather then reinstall but I dont know where to begin. However this is the computer I work on so time isnt on my side, when everything is done backing up I will just reinstall and hope for the best

Is there anything else I would typically need besides my home directory?

Again, thanks for the help

---

### Post by Repus on 2008-04-28
Well if anyone is curious I lost all my data. The backups I made copied the directory structure but not the files for some unknown reason. I still have all my work data that I back-uped regularly but my home directory stuff is gone. One empty directory after another. I still very much like Linux and will continue to use it but failures like these is why I tell people it is still not ready for the desktop. This is something like 4 versions into ubuntu for me and I haven't had an upgrade not lead to a reinstall yet. Its a little disappointing.

---

### Post by zvacet on 2008-04-28
I know it is probably too late but for backing up read [this.]("http://psychocats.s465.sureserver.com/ubuntu/backup")That is exactly what you need.

```
sudo dpkg --configure -a
```

or

```
sudo apt-get -f install
```

---

