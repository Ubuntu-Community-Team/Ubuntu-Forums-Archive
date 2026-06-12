---
title: "[SOLVED] Need Help With Bash Script"
date: 2008-06-05
forum: Programming Talk
---

### Post by OffHand on 2008-06-05
Hi Guys,

I need help with a bash script. Basically what it needs to do is execute the command below on root level but for the user that is currently logged in. It will run on Apple OS X machines but that doesn't really make much difference on command line level. It should do something like 'if user is root then exit else execute the command below for the user that is currently logged in.'

find ~/Library/Cache -name "*AdobeFnt*" -exec rm '{}' \;

Thanks in advance!

---

### Post by geirha on 2008-06-05
```
#!/bin/bash
if [[ "$(id -u)" == "0" ]]; then
    echo "Don't run this as root"
else
    find ~/Library/Cache -name "*AdobeFnt*" -delete
fi

```

or a shorter version
```
[[ "$(id -u)" != "0" ]] && find ~/Library/Cache -name "*AdobeFnt*" -delete
```

---

### Post by OffHand on 2008-06-05
> **geirha said:**
> ```
#!/bin/bash
if [[ "$(id -u)" == "0" ]]; then
    echo "Don't run this as root"
else
    find ~/Library/Cache -name "*AdobeFnt*" -delete
fi

```

or a shorter version
```
[[ "$(id -u)" != "0" ]] && find ~/Library/Cache -name "*AdobeFnt*" -delete
```

The script should run as root (started by launchd at startup) but should remove the files from the user that is currently logged in (which isn't root). All happens in the background so an echo isn't needed.

Does your script still work?

I really appreciate your time and help  :)

Example: User John logs in and all AdobeFnt files will be deleted from /Users/John/Library/Cache

The problem is the relative path ~/ in the script I used. If you run it as root ~ wil point to root's home.

---

### Post by geirha on 2008-06-05
To me that sounds like a very odd thing to do, but I think something similar to this will do it. By similar I mean you'll need to change the find-line to do the deleting. Obviously you should test this first by checking that /tmp/testrun.txt only lists files that should be deleted, and then replace ">>/tmp/testrun.txt" with "-delete" when you feel confident. I've only tested it briefly myself.
```
#!/bin/bash

# this should find all users currently logged in 
users=( `who | awk '{print $1}' | sed '/^root$/d' | uniq` )

echo "...Script started at `date`" >>/tmp/testrun.txt

for user in "${users[@]}"; do
    # find the homedir
    homedir=`sudo -i -u $user xdg-user-dir HOME`
    find $homedir/Library/Cache -name "*AdobeFnt*" >>/tmp/testrun.txt
done

echo "...Script ended at `date`" >>/tmp/testrun.txt

```

---

### Post by OffHand on 2008-06-05
> **geirha said:**
> To me that sounds like a very odd thing to do, but I think something similar to this will do it. By similar I mean you'll need to change the find-line to do the deleting. Obviously you should test this first by checking that /tmp/testrun.txt only lists files that should be deleted, and then replace ">>/tmp/testrun.txt" with "-delete" when you feel confident. I've only tested it briefly myself.
```
#!/bin/bash

# this should find all users currently logged in 
users=( `who | awk '{print $1}' | sed '/^root$/d' | uniq` )

echo "...Script started at `date`" >>/tmp/testrun.txt

for user in "${users[@]}"; do
    # find the homedir
    homedir=`sudo -i -u $user xdg-user-dir HOME`
    find $homedir/Library/Cache -name "*AdobeFnt*" >>/tmp/testrun.txt
done

echo "...Script ended at `date`" >>/tmp/testrun.txt

```


Thank you. I will give that a try tomorrow at work. The mac users at work often have to delete the AdobeFnt files because they can cause issues (they use a lot of fonts - it's a design department). This script will be used as a maintenance script if they log in. Hopefully they will have less issues. I will let you know. Thanks a bunch!

---

### Post by OffHand on 2008-06-06
I tried to run it here at work but I get the following result:

$ /Users/janw/Desktop/clean_font_cache.command; exit
xdg-user-dir: xdg-user-dir: No such file or directory
find: /Library/Cache: No such file or directory
logout
[Process completed]

Even-though the first part of the script does give the right output:

$ who | awk '{print $1}' | sed '/^root$/d' | uniq
janw

Can this be caused by a syntax difference between linux and unix? Help greatly appreciated...

---

### Post by WW on 2008-06-06
I'm using a Mac running OSX 10.4.  A few points:

It appears that you could use the command **users | sed '/^root$/d'** instead of **who | awk '{print $1}' | sed '/^root$/d' | uniq**

I don't have the command **xdg-user-dir**.  Perhaps instead of **homedir=`sudo -i -u $user xdg-user-dir HOME`** you could simply use:
```

    homedir=/Users/$user

```

In my home directory, I have a directory called **Library/Caches**, but not
**Library/Cache**.

---

### Post by OffHand on 2008-06-06
> **WW said:**
> I'm using a Mac running OSX 10.4.  A few points:

It appears that you could use the command **users | sed '/^root$/d'** instead of **who | awk '{print $1}' | sed '/^root$/d' | uniq**

I don't have the command **xdg-user-dir**.  Perhaps instead of **homedir=`sudo -i -u $user xdg-user-dir HOME`** you could simply use:
```

    homedir=/Users/$home

```

In my home directory, I have a directory called **Library/Caches**, but not
**Library/Cache**.

Cache was indeed a typo, it should be Caches like you said. I made the change you suggested (homedir=/Users/$home) but that gives the following result:

$ sudo sh clean_font_cache.sh 
find: /Users//Library/Caches: No such file or directory

---

### Post by OffHand on 2008-06-06
I think I got it:

#!/bin/bash

# this should find all users currently logged in 
users=( `who | awk '{print $1}' | sed '/^root$/d' | uniq` )

echo "...Script started at `date`" >>/tmp/testrun.txt

for user in "${users[@]}"; do
    # find the homedir
    homedir=/Users/${users[@]}
    find $homedir/Library/Caches -name "*AdobeFnt*" >>/tmp/testrun.txt
done

echo "...Script ended at `date`" >>/tmp/testrun.txt

Makes sense?

---

### Post by WW on 2008-06-06
I fixed my previous post (changed /Users/$home to /Users/$user).  Does a loop like this work?
```

for user in $users; do
    find /Users/$user/Library/Caches -name "*AdobeFnt*" >>/tmp/testrun.txt
done

```

---

### Post by OffHand on 2008-06-06
> **WW said:**
> I fixed my previous post (changed /Users/$home to /Users/$user).  Does a loop like this work?
```

for user in $users; do
    find /Users/$user/Library/Caches -name "*AdobeFnt*" >>/tmp/testrun.txt
done

```

I think I got it! Doing some tests now...

I'll report back.

---

### Post by geirha on 2008-06-06
Sorry, it completely missed my mind that this were gonna be run on macs, as I have never touched a mac, I wouldn't now what commands are available or not there (I was on ubuntu in my mind). 

Anyway, you seem to have a version that works now, except that the for-loop will only loop once no matter how many users are logged in. You should change the for-line to read ```
for user in "${users[@]}"; do
```

---

### Post by WW on 2008-06-06
> **geirha said:**
> 

Anyway, you seem to have a version that works now, except that the for-loop will only loop once no matter how many users are logged in. You should change the for-line to read ```
for user in "${users[@]}"; do
```
Why is that?

Here is a similar loop, with files instead of user names, that seems to work fine:

testloop.sh
```

files=$(ls)
for f in $files; do
    echo "file: $f"
done

```
For example,
```

$ ls 
a.dat        b.dat        testloop.sh
$ sh testloop.sh 
file: a.dat
file: b.dat
file: testloop.sh
$ 

```

---

### Post by geirha on 2008-06-06
because users is an array: ```

$ users=( a b c d )
$ echo $users
a
$ echo ${users[1]}
b
$ echo ${users[@]}
a b c d

```

---

### Post by OffHand on 2008-06-06
Hi guys,

First of all... Thanks for your great help. This is the script that works for me:


#!/bin/bash

# this should find all users currently logged in 
users=( `who | awk '{print $1}' | sed '/^root$/d' | uniq` )

echo "...Script started at `date`" >>/tmp/testrun.txt

for user in "${users[@]}"; do
    # find the homedir
    homedir=/Users/${users[@]}
    find $homedir/Library/Caches -name "*AdobeFnt*" >>/tmp/testrun.txt
done

echo "...Script ended at `date`" >>/tmp/testrun.txt

---

### Post by geirha on 2008-06-06
Looks good, except for this one line:
```
    homedir=/Users/${users[@]}
```
which will only work if there is only one user logged in at a time. This should work better:
```
    homedir=/Users/$user
```

---

### Post by WW on 2008-06-06
> **geirha said:**
> because users is an array:

Ah, I missed that.  Thanks.  So if the script didn't put parentheses around the back-quoted command sequence, $users would work.  With the extra parentheses, it is an array, and ${users[@]} is needed.

For the sake of completeness:

testloop2.sh
```

files=( $(ls) )
for f in ${files[@]}; do
    echo "file: $f"
done

```
```

$ ls 
a.dat         b.dat         testloop.sh   testloop2.sh
$ sh testloop2.sh 
file: a.dat
file: b.dat
file: testloop.sh
file: testloop2.sh
$ 

```

---

### Post by geirha on 2008-06-06
> **WW said:**
> Ah, I missed that.  Thanks.  So if the script didn't put parentheses around the back-quoted command sequence, $users would work.  With the extra paretheses, it is an array, and ${users[@]} is needed.


Yes :)

It's a bit better to use patterns instead of ls btw. I.e. files=( * ) instead of files=( $(ls) ). It will handle files with spaces.

---

### Post by WW on 2008-06-06
> **geirha said:**
> 
It's a bit better to use patterns instead of ls btw. I.e. files=( * ) instead of files=( $(ls) ). It will handle files with spaces.
Thanks,  I was just discovering that... :)
```

$ ls -1
A File With Spaces
a.dat
b.dat
testloop.sh
testloop2.sh
$ sh testloop2.sh 
file: A
file: File
file: With
file: Spaces
file: a.dat
file: b.dat
file: testloop.sh
file: testloop2.sh
$ 

```

---

### Post by OffHand on 2008-06-06
> **geirha said:**
> Looks good, except for this one line:
```
    homedir=/Users/${users[@]}
```
which will only work if there is only one user logged in at a time. This should work better:
```
    homedir=/Users/$user
```

I'll give it a go and report back :)

---

### Post by OffHand on 2008-06-06
Confirmed! Removes the Adbove font cache files for every user that is logged in... Awesome :guitar:

---

