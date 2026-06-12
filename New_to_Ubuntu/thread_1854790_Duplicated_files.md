---
title: "Duplicated files"
date: 2011-10-05
forum: New to Ubuntu
---

### Post by RayArdia on 2011-10-05
Having failed to make any sense of fslint, krusader and kleansweep I decided to give fdupes a try.
My photos are in /home/ray/Photos with folders for each year, subfolders for months and sub-sub folders for days.
I know that there are lots of duplicates, for example in /home/ray/Photos/2010/01/10.
When I try to navigate to this sub-sub folder I get:-

ray@ray-laptop:~$ fdupes -r /home/ray/Photos/2010/01/10
ray@ray-laptop:~$
ie no output at all, what am I doing wrong
Ray

---

### Post by 4llf0rn0t on 2011-10-05
Can you md5sum two files which you think are the same? If they have the same message digest, fdupes should output them.

---

