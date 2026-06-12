---
title: "[SOLVED] copying and preserving folder structure"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by matjaz on 2008-10-31
Hello,

is there a way to use "cp" command and make it create some folders on the fly? Or any other command?

for instance:

cp /a/b/file /my/backup/location/a/b/file
gives me
cp: cannot create regular file `/my/backup/location/a/b/file': No such file or directory

because the directories a/b do not exist in directory location.
I would like that "cp" would create them (and any others that do not exist)
when copying files.
I am using this in a script with a lot of filenames so i just can't "mkdir" every time.

Thank you for taking the time to help

Matjaz

---

### Post by Jeff250 on 2008-10-31
A compromise solution may be to use mkdir -p, as it will create all parent directories needed for a path.  So if /foo is empty and you say mkdir -p /foo/bar/bletch, then it will create bar automatically before creating bletch.  So instead of saying in your script:

```
cp /a/b/file /my/backup/location/a/b/file
```

Perhaps you could say...

```
mkdir -p /my/backup/location/a/b/file
cp /a/b/file /my/backup/location/a/b/file
```

Without seeing your script, it is hard to know how hard this would be, but, for example, if the destination is in a variable, it would be something like:

```
mkdir -p $dest
cp /a/b/file $dest
```

---

### Post by handydan918 on 2008-10-31
> **matjaz said:**
> Hello,

is there a way to use "cp" command and make it create some folders on the fly? Or any other command?

for instance:

cp /a/b/file /my/backup/location/a/b/file
gives me
cp: cannot create regular file `/my/backup/location/a/b/file': No such file or directory

because the directories a/b do not exist in directory location.
I would like that "cp" would create them (and any others that do not exist)
when copying files.
I am using this in a script with a lot of filenames so i just can't "mkdir" every time.

Thank you for taking the time to help

Matjaz

I think that ```
cp -R
``` should do that...

In fact, here is what I just did, without the use of mkdir

```
cp -R Desktop /home/daniel/testdir
```

which created the directory testdir with all of the files formerly  found in Desktop inside it.

HTH!

---

### Post by Jeff250 on 2008-10-31
Hmm, it depends.  Is the OP trying to automatically create parent directories or subdirectories?

---

### Post by matjaz on 2008-10-31
Thanks,

mkdir -p does the job.

cp -R copies all the files in folder structure ( i think ) what is not what i want.

That solves my problem.

But while i was trying to solve that on my own, i figured i would need to know how to input characters such as "/" into terminal. I can't find that info anywhere and i would hate to start a new thread just to find that out, so i will ask you, since you seem to be pretty knowledgeable about terminal commands.
So the question:
how do i pass / as an argument to (in my case sed) an program i call?
I mean in c if i wanted to have a string str = "a/b/c"
i did it with str = "a//b//c".
The double // was needed because / is an escape character.
So is there any similar trick in bash?

for instance:
sed 's/A/B/g' FILE
replaces all A in FILE with B.
How do i accomplish this if A = / ?

Thanks again
Matjaz

---

### Post by matjaz on 2008-12-02
If somebody wants to know how i solved the sed problem:
I found a workaround - if you change the value of IFS bash variable, you can force bash to separate list items with whatever you like.
My advice: take a look at IFS
for instance:
OLDIFS="$IFS"
IFS=$'\n'

---

### Post by matjaz on 2008-12-02
Doubleposted

---

