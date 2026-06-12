---
title: "BASH rm and exclude"
date: 2009-01-06
forum: Programming Talk
---

### Post by Greslore on 2009-01-06
I am stumped on what I thought would be something very easy to script.  

I have some Ubuntu boxes with over 100 users each (LDAP Authentication).  I need to delete everyone's home directory but maintain their .ssh directory.

User home directories get mounted to:
/home/user_initial/username/

This script or line of code would go into rc.local to execute during each reboot.  I did use "rm -rf /home" and no issues.  But, I now need to maintain all the users .ssh directories.

Any ideas on how to do this?  rm doesn't seem to have an "exclude" feature?

---

### Post by ubuser_7 on 2009-01-06
The directories will be something like 
/home/user_initial/username/.ssh
right? 

Your script has to maintain the above path to save the .ssh directory. 

You can try the following code:

**This command will delete everything (although iteratively) in the current directory recursively. Please be VERY careful. **

```

cd /home
rm -ir `find . | grep -v .ssh`

```

Basically you look at all files and directories and exclude the ones which have .ssh in their name. 

I put in the -i option with rm for safety. For automation you should replace it with f, once you are sure and have tested the code.

---

### Post by Greslore on 2009-01-06
> **ubuser_7 said:**
> The directories will be something like 
/home/user_initial/username/.ssh
right? 

Your script has to maintain the above path to save the .ssh directory. 

You can try the following code:

**This command will delete everything (although iteratively) in the current directory recursively. Please be VERY careful. **

```

cd /home
rm -ir `find . | grep -v .ssh`

```

Basically you look at all files and directories and exclude the ones which have .ssh in their name. 

I put in the -i option with rm for safety. For automation you should replace it with f, once you are sure and have tested the code.

Tried it and unfortunately it deleted everything.  (Which is fine as I wipe these machines after every reboot anyways.  I should mention that I have a few days before I need this working hence why I am so laissez fair with deleting the data now for testing. :) )  I typed in exactly:
```

cd /home
rm -rf `find . |grep -v .ssh`

```

Indeed you are correct, the full path will be: 
/home/user_initial/username/.ssh 
for everyone's .ssh dir.

---

### Post by ubuser_7 on 2009-01-06
Ah my bad, I never realised. 

The problem is the -r option. Since find already gets all files, we should not recurse.

If you do a simple rm -f instead of rf as in original one, then follow it by rmdir *, it should work.  It was recursing in the directories and hence deletes the .ssh too. I worked in what i tested a bit here.

I setup a testbed:
```

testuser@desk:64:~/testing/test1$ mkdir user3
testuser@desk:65:~/testing/test1$ mkdir user2
testuser@desk:66:~/testing/test1$ mkdir user1/.ssh
testuser@desk:67:~/testing/test1$ echo testFile > user1/.ssh/testfile
testuser@desk:68:~/testing/test1$ echo testFile > file1
testuser@desk:69:~/testing/test1$ echo testFile > user3/file1
testuser@desk:70:~/testing/test1$ ls -lRa
.:
total 24
drwxr-xr-x 5 testuser testuser 4096 2009-01-06 14:41 .
drwxr-xr-x 9 testuser testuser 4096 2009-01-06 14:15 ..
-rw-r--r-- 1 testuser testuser    9 2009-01-06 14:41 file1
drwxr-xr-x 3 testuser testuser 4096 2009-01-06 14:40 user1
drwxr-xr-x 2 testuser testuser 4096 2009-01-06 14:40 user2
drwxr-xr-x 2 testuser testuser 4096 2009-01-06 14:41 user3

./user1:
total 12
drwxr-xr-x 3 testuser testuser 4096 2009-01-06 14:40 .
drwxr-xr-x 5 testuser testuser 4096 2009-01-06 14:41 ..
drwxr-xr-x 2 testuser testuser 4096 2009-01-06 14:40 .ssh

./user1/.ssh:
total 12
drwxr-xr-x 2 testuser testuser 4096 2009-01-06 14:40 .
drwxr-xr-x 3 testuser testuser 4096 2009-01-06 14:40 ..
-rw-r--r-- 1 testuser testuser    9 2009-01-06 14:40 testfile

./user2:
total 8
drwxr-xr-x 2 testuser testuser 4096 2009-01-06 14:40 .
drwxr-xr-x 5 testuser testuser 4096 2009-01-06 14:41 ..

./user3:
total 12
drwxr-xr-x 2 testuser testuser 4096 2009-01-06 14:41 .
drwxr-xr-x 5 testuser testuser 4096 2009-01-06 14:41 ..
-rw-r--r-- 1 testuser testuser    9 2009-01-06 14:41 file1

```

Now the find and grep work fine: 

```

$find . | grep -v .ssh
.
./file1
./user2
./user3
./user3/file1
./user1

```

Finally executed the above without the 'r' option: 

```

$ rm -f  `find . |grep -v .ssh`

rm: cannot remove directory `.'
rm: cannot remove `./user2': Is a directory
rm: cannot remove `./user3': Is a directory
rm: cannot remove `./user1': Is a directory
testuser@desk:93:~/testing/test1/user1$ rmdir *
rmdir: failed to remove `user1': Directory not empty
testuser@desk:94:~/testing/test1/user1$ ls
user1
testuser@desk:95:~/testing/test1/user1$ cd user1/.ssh/
testuser@desk:96:~/testing/test1/user1/user1/.ssh$ ls
testfile
testuser@desk:97:~/testing/test1/user1/user1/.ssh$ 

```

---

### Post by ghostdog74 on 2009-01-06
in bash you can set extended globbing
```

shopt -s extglob
rm !(*.ssh)

```

---

### Post by skoorbevad on 2009-01-25
> **ghostdog74 said:**
> in bash you can set extended globbing
```

shopt -s extglob
rm !(*.ssh)

```

Or string it all together:

```

(shopt -s extglob; cd /home; for i in *; do cd $i; rm -rf !(^\.ssh); cd -; done)

```

...be careful, of course, since you're rm'ing files.

---

### Post by slavik on 2009-01-25
this should work. :)

```

BASEDIR="/home/"
find $BASEDIR -mindepth 2 -not -name ".ssh" -type d -exec rm -rf {} \;

```

---

### Post by geirha on 2009-01-28
I'd go for
```
find /home/?/* -mindepth 1 -not -regex ".*/\.ssh\(/.*\)?" -delete
```

---

