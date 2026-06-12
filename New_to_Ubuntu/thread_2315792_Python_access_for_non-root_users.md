---
title: "Python access for non-root users"
date: 2016-03-02
forum: New to Ubuntu
---

### Post by Matthew_H._Wagner on 2016-03-02
I've got 14.04 and it comes with Python2.7 installed in /usr/lib/python2.7.  Given the following file permissions, what's the correct way to give Python access to users not in the root group?
```

drwxrwxr--  26 root root        12288 Mar  1 16:26 python2.7
```

---

### Post by steeldriver on 2016-03-02
The python2.7 *executable *should be located in /usr/bin, and should have permissions

```

-rwxr-xr-x 1 root root 3345416 Jun 22  2015 /usr/bin/python2.7

```

AFAIK the 'correct' permissions for /usr/lib/python2.7 are

```

drwxr-xr-x 26 root root 24576 Jul 11  2015 /usr/lib/python2.7

```

i.e. others only need x permission (in order to be able to access the directory's contents) - files within the dir need to be readable e.g.

```

$ ls -l /usr/lib/python2.7/abc.py
-rw-r--r-- 1 root root 7145 Jun 22  2015 /usr/lib/python2.7/abc.py

```

---

### Post by Matthew_H._Wagner on 2016-03-02
I don't remember changing the permissions but it does seem reasonable to put them back to the same as the other versions.  Which I did, but now I'm getting:

ImportError: No module named _sysconfigdata_nd

---

### Post by steeldriver on 2016-03-02
Well on my system the module is likely provided by

```

/usr/lib/python2.7/plat-x86_64-linux-gnu/_sysconfigdata_nd.py

```

Perhaps the screwed up permissions go deeper e.g. your /usr/lib/python2.7/plat-x86_64-linux-gnu/ (or equivalent) directory is not executable/accessible to others?

---

### Post by Matthew_H._Wagner on 2016-03-02
Indeed they are all messed up.  I tried reinstalling with:

```

sudo apt-get install --reinstall python2.7
sudo apt-get install --reinstall libpython2.7

```

but that doesn't seem to be updating any of the permissions.  I guess remove and then reinstall?

---

### Post by steeldriver on 2016-03-02
**NO! please do not attempt to remove python**

Let us think about the best way to fix

---

### Post by Matthew_H._Wagner on 2016-03-02
Hehe.  Yeah, I didn't want to do that.  Would have to reinstall pretty much everything.

---

### Post by Matthew_H._Wagner on 2016-03-02
I got it!  Well I [found it]("http://stackoverflow.com/questions/3740152/how-to-set-chmod-for-a-folder-and-all-of-its-subfolders-and-files-in-linux-ubunt") anyway.  Change all the folders to 755 and the *.py files to 644.

```

sudo find /usr/lib/python2.7 -type d -exec chmod 755 {} \;
sudo find /usr/lib/python2.7/*.py -exec chmod 644 {} \; 

```

---

