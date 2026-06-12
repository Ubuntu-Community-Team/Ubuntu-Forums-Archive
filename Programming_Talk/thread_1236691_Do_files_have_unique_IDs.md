---
title: "Do files have unique IDs?"
date: 2009-08-10
forum: Programming Talk
---

### Post by jamescox84 on 2009-08-10
Just a quick query, do file have unique IDs that can be used to reference them rather than by there filenames.  The reason I ask is I would like to store some information about the some files in a database.  But if the file is moved or renamed I still want to be able to reference them.

Thanks for any advice.

---

### Post by decoherence on 2009-08-10
inodes are probably what you want, though keep in mind that one inode can have more than one link... still, it's multiple links to one file

to find a file's inode
```

ls -i *filename*
```

to find a file based on inode
```

find -inum *inode*
```

for example 

```
decoherence@defectivepart:~$ ls -i xplanet.log 
25144487 xplanet.log
decoherence@defectivepart:~$ find . -inum 25144487
./xplanet.log
```

hope that helps

---

### Post by jamescox84 on 2009-08-10
Wow, super-fast many thanks.

Looks like I can get that magic little number from a call to `stat' in <sys/stat.h>.

[EDIT]
I see you answered this with ```
find -node
```.  But is there a call in the standard library I could use?
[/EDIT]

But is there a way to get the name of the links that point to this inode.  Perhaps this is just a bridge too far.

But many, many thanks!

---

### Post by ajgreeny on 2009-08-10
Every file also has a unique md5sum, as far as I'm aware.  How you can use that to do what you want, I'm not sure, but I did not want you to overlook this possibility.

---

### Post by imbjr on 2009-08-10
> **ajgreeny said:**
> Every file also has a unique md5sum, as far as I'm aware.  How you can use that to do what you want, I'm not sure, but I did not want you to overlook this possibility.

MD5 cannot guarantee a unique id:

[http://www.cryptography.com/cnews/hash.html](http://www.cryptography.com/cnews/hash.html)

---

### Post by stroyan on 2009-08-10
There is no fast way to find all of the links to an inode.
And an inode number is not unique between different file system partitions.
If you have different partitions mounted as /home and /usr then the same inode number can be used as different files on those two mount points.

---

### Post by ssam on 2009-08-11
the inode is not completely stable for a file. editing the file may change it, as some programs use the
write foo.tmp
move foo.tmp -> foo
pattern to update files.

if you edit a text file with gedit the inode changes.

if you moved the file across a filesystem the inode will change.

i would not be surprised if de-fragmenting changed inodes.

backing up a directory and restoring it will change inodes.

if you are counting on the files staying constant, then an MD5sum (or similar) is pretty. the chance of 2 files having the same hash is very small. the chance to 2 files on the same computer colliding is negligible.

i think the maths is roughly the same as the birthday problem, using the approximation on wikipedia, and assuming you have 1e12 files (google indexes 25*1e9)
```

>>>import math
>>>bpa = lambda n,d=365: 1 - math.e ** (-n**2/ 2/d)
>>>bpa(1e12,2**128)
1.4432899320127035e-15

```

though this assumes no one is deliberately trying to cause a collision.

(also note that if you could fit all possible 8 byte files on your hard disk then you would also have a many collisions).

how about your program first checks the original path. if thats not there any more it finds some candidate files, eg:
same inode
same md5sum
similar name, but different folder
and then asks the user which one they want to use.

---

### Post by decoherence on 2009-08-11
great caveats about inodes, ssam and stroyan. i didn't even think of that.

if inodes are not meant to be stable, then they probably shouldn't be used for the purpose of providing stable access to files. I guess i have to change my answer to 'no, at least to my knowledge.'

still it seems to me there should be a way to do this. after all, the system needs to keep track of this... surely the functionality is there to do this at user level? perhaps you'd have to keep tabs on the inode table? but we're out of my depth now (as if we weren't before!)

---

