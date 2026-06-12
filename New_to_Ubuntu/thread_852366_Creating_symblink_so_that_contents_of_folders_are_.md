---
title: "Creating symblink so that contents of folders are linked"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by ben22 on 2008-07-07
Hi,

I want the contents of folder A to be displayed in folder B with the help of a symbolic link.

So what I entered into terminal



```
ln -s /home/user/A /home/user/B
```

It is working half - instead of having the contents of folder A inside of folder be, folder B now contains the folder A.

What command do I need to have contents for folder A to be linked into folder B?

thx,
Ben

---

### Post by jerome1232 on 2008-07-07
the target directory can't exist

ie
```
mkdir backup-test
ln -s ~/backup ~/backup-test
```

produced what you have, a directory containing a symbolic link to backup

so you need to do
```
ln -s /home/user/A /home/user/folder-that-doesn't-exist
```

---

### Post by bumanie on 2008-07-07
I'm no expert on symlinks, but you need to firstly copy /home/user/A to /home/user/B then do the symlink. Also if you do ln -sv the link will be shown in standard out.

---

### Post by ben22 on 2008-07-07
> **jerome1232 said:**
> the target directory can't exist

ie
```
mkdir backup-test
ln -s ~/backup ~/backup-test
```

produced what you have, a directory containing a symbolic link to backup

so you need to do
```
ln -s /home/user/A /home/user/folder-that-doesn't-exist
```


Hm... I need the symlink for linking content from root/B to a subdomain. When creating the subdomain B.domain.com - a folder root/B is created first.

So - is there a workaround for creating the folder first and then linking the contents into the folder?

Thx!

---

### Post by Cypher on 2008-07-07
> **bumanie said:**
> I'm no expert on symlinks, but you need to firstly copy /home/user/A to /home/user/B then do the symlink. Also if you do ln -sv the link will be shown in standard out.

Sorry no, the entire idea of using symlinks is to get around the fact that you want to have 2 directories pointing to the same content. Copying from one directory to another defeats the purpose entirely..

@OP: So if /home/user/A is the directory with contains all files you want to access as /home/user/B, you'd do
```

ln -s /home/user/A /home/user/B

```
Doing a "ls -l" in /home/user will yield
```

A
B -> A

```
Now if you do
```

ls -l /home/user/A/
ls -l /home/user/B/

```
You will get the exact same contents listing. Notice that you HAVE to add the trailing slash to B to get it to show the contents, ignoring the slash will not show you the contents.

---

### Post by bumanie on 2008-07-07
Look at above post. > cp /home/user/A /home/user/B then use the symlink command > ln -sv /home/user/B /home/user/A You may have to do this with sudo in front of the commands. I think what is above will work, but as said, I'm not very experienced with symlinks.

---

### Post by jerome1232 on 2008-07-07
correct me if I'm wrong but the OP's problem is the symlink is getting placed inside of a directory because the link name actually exists as a directory. at least that's what it appears to me.

ie he's creating symlink "/b" that links to the directory "/a", but becuase "/b" exists, the symbolic link is being place inside the directory "/b"

---

### Post by ben22 on 2008-07-07
> **Cypher said:**
> Sorry no, the entire idea of using symlinks is to get around the fact that you want to have 2 directories pointing to the same content. Copying from one directory to another defeats the purpose entirely..

@OP: So if /home/user/A is the directory with contains all files you want to access as /home/user/B, you'd do
```

ln -s /home/user/A /home/user/B

```
Doing a "ls -l" in /home/user will yield
```

A
B -> A

```
Now if you do
```

ls -l /home/user/A/
ls -l /home/user/B/

```
You will get the exact same contents listing. Notice that you HAVE to add the trailing slash to B to get it to show the contents, ignoring the slash will not show you the contents.


@Qipher

my problem is that with ```
ln -s /home/user/A /home/user/B

``` folder B contains folder A not the content of folder A.

So if I open B in "Places" it shows A.

Am I on the completely wrong track here???

---

### Post by Cypher on 2008-07-07
> **ben22 said:**
> @Qipher

my problem is that with ```
ln -s /home/user/A /home/user/B

``` folder B contains folder A not the content of folder A.

So if I open B in "Places" it shows A.

Am I on the completely wrong track here???
Since you want both A and B to essentially have the same "contents", ensure that B doesn't already exist. If it does, the "symlink" command will create a link to A inside B instead of making B a link itself.

So if I have on A and I do
```

ln -s A B

```
When I list the directories I get
```

A
B -> A

```
If I already have a directory C and I do 
```

ln -s A C

```
The directory listing is now
```

A
B -> A
C

```
When I list C I get
```

A -> A

```
The symlink inside C is, of course, useless as it's pointing to itself and will do nothing of value..

Hope that makes sense..

---

### Post by ben22 on 2008-07-07
> **Cypher said:**
> Since you want both A and B to essentially have the same "contents", ensure that B doesn't already exist. If it does, the "symlink" command will create a link to A inside B instead of making B a link itself.

So if I have on A and I do
```

ln -s A B

```
When I list the directories I get
```

A
B -> A

```
If I already have a directory C and I do 
```

ln -s A C

```
The directory listing is now
```

A
B -> A
C

```
When I list C I get
```

A -> A

```
The symlink inside C is, of course, useless as it's pointing to itself and will do nothing of value..

Hope that makes sense..

@Qipher - thanks a lot, u are really helping. 

However, my problem is exactly that B exists.

I need the symlink for linking content from root/B to a subdomain. When creating the subdomain B.domain.com - a folder root/B is created first.

So - is there a workaround for creating the folder first and then linking the contents into the folder?

---

### Post by Cypher on 2008-07-08
OK, so if you have two folders, A and B and all the files in A should be symlinked into B, you cannot just create a top-level symlink as we've found out.

The "workaround" might me to create a symlink for all the top-level files & directories from A into B..

So something like the following Shell script might do the work
```

for file in `ls A`; do ln -s ../A/$file B; done

```
This will create a symlink in B for every file and directory.

---

