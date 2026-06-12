---
title: "Find command speed"
date: 2018-01-05
forum: New to Ubuntu
---

### Post by wrongusername2 on 2018-01-05
Find command returned result too fast so would like to know more about it.

I ran following command, and it returned the result instantaneously. Initial-folder is *root *that is why I am surprised at the speed. In case of Windows if I were to search under C:\ then search will take forever to come back.


```
$> cd /media/abc/drive2
$> find / -name "*Movie*.mp3"
            /media/abc/drive2/something/someMovie12.mp3
```
    


Do you think *find *first searched inside '/media/abc/drive2' and then went to /

I know Locate uses indexed data compared to Find.

My machine config is 
Disk1/drive1 (OS EX4)
Disk2/drive2 (data NTFS)


Thanks

---

### Post by oldos2er on 2018-01-05
If you want find to search all subdirectories under /media/abc/drive2, try ```
find . -name *Movie*.mp3
``` If case doesn't matter ```
find . -iname *Movie*.mp3
```

---

### Post by wrongusername2 on 2018-01-05
Thanks for responding, I wanted to know why find was so fast even though i gave root as starting folder. Link to any online doc will be fine. Thanks

---

### Post by oldos2er on 2018-01-06
As I implied, the command in post #1 is not recursive. See [https://linode.com/docs/tools-reference/tools/find-files-in-linux-using-the-command-line/](https://linode.com/docs/tools-reference/tools/find-files-in-linux-using-the-command-line/)

---

### Post by Holger_Gehrke on 2018-01-06
No,find doesn't search the current directory first. When I did a 'find' for a file in the current directory starting from '/' just now on a freshly booted machine, I got several error messages about being unable to read various subdirectories of '/proc' before it found the file and it took a minute or two. **But** when I repeated the command (and prefaced it with 'time '  to measure how long it takes) it was done in less than 6 seconds. So the disk cache is obviously doing a very good job of keeping data available. I would assume that the cache is also to 'blame' for the high speed on your machine. 

Holger

---

### Post by sisco311 on 2018-01-06
> **wrongusername2 said:**
> Thanks for responding, I wanted to know why find was so fast even though i gave root as starting folder. Link to any online doc will be fine. Thanks

Check out:
[https://superuser.com/questions/638946/why-is-find-running-incredible-fast-if-run-twice](https://superuser.com/questions/638946/why-is-find-running-incredible-fast-if-run-twice)

EDIT: Holger_Gehrke beat me to it! :)

```

[sisco@asrock ~]$ time find / -name foobarfile 2> /dev/null
/home/sisco/foobarfile

real	0m30.284s
user	0m2.440s
sys	0m5.319s
[sisco@asrock ~]$ time find / -name foobarfile 2> /dev/null
/home/sisco/foobarfile

real	0m4.491s
user	0m2.151s
sys	0m2.310s

```

---

### Post by wrongusername2 on 2018-01-06
Thanks every one. It was indeed caching :-)
I cleared the kernel cache and ran the same command and it took lot more time. 

```
//First run of FIND
real    0m57.080s
user    0m0.684s
sys    0m1.240s

//2nd run of FIND
real    0m0.719s
user    0m0.356s
sys    0m0.332s


//Clear the kernel cache using 
   sync
   echo 3 > /proc/sys/vm/drop_caches


#FIND (after clearing cache)
real    1m4.952s
user    0m0.604s
sys    0m1.380s
```

Thanks

---

