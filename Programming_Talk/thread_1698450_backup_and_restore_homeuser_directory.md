---
title: "backup and restore /home/user directory"
date: 2011-03-02
forum: Programming Talk
---

### Post by cccc on 2011-03-02
Hello

I need a bash scripts to backup and restore /home/user directory include all hidden files.

THX

---

### Post by MadCow108 on 2011-03-02
install grsync (sudo apt-get install grsync) and click all the options you need.
Then Files -> Rsync command line (Alt +R) and you have your simple backup script.

---

### Post by cccc on 2011-03-02
Thx a lot that's a gerat solution, but what I really need are bash scripts: 

1.) to backup the user home directory include all hidden files:

tar cvzf /save/backup.tar.gz /home/my_user

2.) to restore from the backup /save/my_user.tar.gz

cd /home/
tar xvzf my_user.tar.gz; cd -

These scrips should run from a desktop and a normal user should do that.

---

### Post by Shpongle on 2011-03-02
just put the commands in a bash file 

use $HOME for the home directory as its dynamic.

put this in a file called backup.sh , for example

#! /bin/bash

echo 'Backing up home dir'
tar cvzf /save/backup.tar.gz $HOME

make it executable by chmod u+x backup.sh

run it by /path/to/script/backup.sh


now do the same for the other one

see here for more details [http://www.freeos.com/guides/lsst/ch02sec01.html](http://www.freeos.com/guides/lsst/ch02sec01.html)

---

### Post by eerror on 2011-03-02
Personally I like rsync for backups (rather than tar and gz). 
That way only files that changed get copied over.

rsync -avt /srcdir /destdir

The first time you run it it will copy everything.
If you run it 2nd time right away it will not copy anything.
Now change a file in your home directory and run the command again.
Only that changed file will copy over.

---

### Post by cccc on 2011-03-02
I've created these scripte using $HOME parameter:```

#! /bin/bash
echo 'Backing up user home dir'
cd /home
tar cvzf /home/user/save/backup.tar.gz $HOME
```

and now restore:```

#! /bin/bash
echo 'Restore user default settings'
cd /home
tar xvzf /home/user/save/backup.tar.gz
```

then I get /home/user/home/user directory created instead of extracting directly into /home/user/*

Both scripts should by run by a normal user.

---

### Post by cyberslayer on 2011-03-03
> **cccc said:**
> ...

Try "man tar" to see the documentation for tar.  Why do you think it is creating the extra directory?

---

### Post by cccc on 2011-03-03
> **cyberslayer said:**
> Try "man tar" to see the documentation for tar.  Why do you think it is creating the extra directory?

If I run tar xvzf /home/user/save/backup.tar.gz I can see, the extra /home/user/**home/user** will be created, instead of extracting directly into /home/user/*.
That's not what I want.

---

### Post by cccc on 2011-03-03
I still cannot find a solution.

---

### Post by Some Penguin on 2011-03-03
You still aren't reading documentation and thinking things through instead of going to a forum with "I want, I want, I want".

---

### Post by cccc on 2011-03-05
I solved this problem using these scripts:```

#! /bin/bash
echo 'Backing up user home dir'
cd /home
tar cvzf /usr/backup/user_backup.tar.gz **.**
```with a dot at the end

and now restore:```

#! /bin/bash
echo 'Restore user default settings'
cd /home
tar xvzf /usr/backup/user_backup.tar.gz
```

---

