---
title: "filter files and folder in bash based on names?"
date: 2012-12-30
forum: Programming Talk
---

### Post by Ferrat on 2012-12-30
Hi there, 
I have a little problem, I'm trying to create a script that can sort, move and rename files in a directory but can't really find any good information when "googleing" it. 

The idea is this

one folder lets call it SOURCE contains a multitude of video files and folders with video files as well as other types, now what I want to do is sort them based on naming conventions as well as other factors and move the to a more appropriate directory.

SOURCE looks like this (folder in fat CAPS, File names non caps)

```
**SOURCE**
-paris 2001.mkv
-rio 2000.avi
-**CANADA 2006**
--montreal-10/12.mp4
--montreak-11/12.mp4
--quebec-13/12.mp4
-**CANADA.2011**
--montreal-10/12.mp4
--montreak-11/12.mp4
--quebec-13/12.mp4
-trash_file.txt
-**JAPAN(2003)**
--tokyo-1/5.mp4
--tokyo-2/5.mp4
--tokyo-3/5.mp4

```
and so on...


now I want it to look like this
```
**NEW FOLDER**
-**ASIA**
--**JAPAN**
---**2003**
----tokyo-1/5.mp4
----tokyo-2/5.mp4
----tokyo-3/5.mp4
-**NORTH AMERICA**
--**CANADA**
---**2006**
----montreal-10/12.mp4
----montreak-11/12.mp4
----quebec-13/12.mp4
---**2011**
----montreal-10/12.mp4
----montreak-11/12.mp4
----quebec-13/12.mp4
-**OTHERS**
--**PARIS**
---paris 2001.mkv
--**RIO**
---rio 2000.avi

```

and delete everything else.

is this possible in bash if so how? or would python make a better choice and in that case how? :P 

Any help would be very appreciated.

Edit:
Should add my approach right now is to check if it's a file or dir etc but I'm not sure how to drive the file/folder names through a "filter" and get the right response.

---

### Post by Vaphell on 2012-12-30
all unsorted files in root dir follow the same format of location-year? or some do and you want to ignore the rest?

---

### Post by Ferrat on 2012-12-30
Sadly not exactly the same format but generally it's name then year and the movies generally have dates in that form or something similar and I want to try and sort them all if possible. 
Some general rules 
years are separated but can be -2000- or (2000) or .2000. 
names are separated but can be name- name.name_part2- name name_part2- name. name.name_part2. name name_part2. 
dates are separated but can be 12/12 12.12 12-12
looking at python right now, seems more plausible for a solution

---

### Post by Vaphell on 2012-12-30
> dates are separated but can be 12[COLOR="Red"]/[/COLOR]12 12.12 12-12
i don't think so, that's an illegal char, unless you want to create a dir/file thing
besides i don't see in the example why the dates would matter at all.



i managed to sort your example in pure bash

```
#!/bin/bash

dest=./sorted

for r in "[-(][0-9][0-9][0-9][0-9][-)]" "[.[:space:]][0-9][0-9][0-9][0-9]"
do
  for d in *$r/
  do
    x="${d%$r/}"
    y="${d//[^0-9]/}"
    **echo** mkdir -p "$dest/$x/$y"
    **echo** mv "$d"* -t "$dest/$x/$y"
  done
  
  for f in *$r.*
  do
    [ -f "$f" ] || continue
    x=${f%$r.*}
    y="${f//[^0-9]/}"
    **echo** mkdir -p "$dest/${x^^}/$y"
    **echo** mv "$f" -t "$dest/${x^^}/$y"
  done
done
```

```
$ tree
[COLOR="DimGray"].
&#9500;&#9472;&#9472; CANADA.2011
&#9500;&#9472;&#9472; CANADA 2006
&#9500;&#9472;&#9472; dest
&#9474;** &#9500;&#9472;&#9472; CANADA
&#9474;** &#9492;&#9472;&#9472; JAPAN
&#9500;&#9472;&#9472; JAPAN-2003-
&#9500;&#9472;&#9472; sort_crap.sh[/COLOR]
&#9500;&#9472;&#9472; sorted
&#9474;** &#9500;&#9472;&#9472; CANADA
&#9474;** &#9474;** &#9500;&#9472;&#9472; 2006
&#9474;** &#9474;** &#9474;** &#9500;&#9472;&#9472; montreal-10_12.avi
&#9474;** &#9474;** &#9474;** &#9500;&#9472;&#9472; montreal-11_12.avi
&#9474;** &#9474;** &#9474;** &#9492;&#9472;&#9472; quebec-13_12.avi
&#9474;** &#9474;** &#9492;&#9472;&#9472; 2011
&#9474;** &#9474;**     &#9492;&#9472;&#9472; montreal-11_12.avi
&#9474;** &#9500;&#9472;&#9472; JAPAN
&#9474;** &#9474;** &#9492;&#9472;&#9472; 2003
&#9474;** &#9474;**     &#9500;&#9472;&#9472; tokyo-1_4.mp4
&#9474;** &#9474;**     &#9492;&#9472;&#9472; tokyo-2_4.mp4
&#9474;** &#9500;&#9472;&#9472; PARIS
&#9474;** &#9474;** &#9492;&#9472;&#9472; 2001
&#9474;** &#9474;**     &#9492;&#9472;&#9472; paris 2001.mkv
&#9474;** &#9492;&#9472;&#9472; RIO
&#9474;**     &#9492;&#9472;&#9472; 2000
&#9474;**         &#9492;&#9472;&#9472; rio 2000.avi
[COLOR="DimGray"]&#9492;&#9472;&#9472; trash_file.txt[/COLOR]

```


obviously these echos are a safety valve to see if the output looks like anything remotely desirable without actually running mv. Tests on dummy data encouraged.
i don't think that the real world data is as easy to process as the example was - year tag in 3 possible formats always at the end.

---

### Post by Ferrat on 2012-12-30
No it's probably not as easy, will try out your script and push the output to a log file to see what happens but right now I'm thinking python with regular expressions might be a better way to go?

---

