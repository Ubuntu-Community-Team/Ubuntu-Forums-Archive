---
title: "Help from AWK experts requested"
date: 2011-05-09
forum: Programming Talk
---

### Post by patmagee1024 on 2011-05-09
I have a file that contains rows of data structured like this:

dsc001.jpg,california
dsc001.jpg,bob
dsc001.jpg,betty
dcim_14275.jpg,skating
dcim_14275.jpg,kids
etc.

I am trying to use awk (or bash scripting) to make the data look like this:

dsc001.jpg;3;california,bob,betty
dcim_14275.jpg;2;skating,kids

The target data structure is
filename;tag-count;tag1,tag2,tag3,etc

The tag count is variable and the filenames are not a consistent pattern (random even?) based on the camera used. 

Is there someone familiar with awk or even bash scripting that would mind showing me a complete way of accomplishing this? I have some scripting ability and know enough about awk to get the data into an array but have hit a block and can't figure out how or where to go from here.

I have spent a week in the evenings researching how to do this with minimal success. I figured it was time to request help so I could make progress on this little project. Many thanks and my sincere appreciation. 

Pat

---

### Post by DaithiF on 2011-05-09
Hi,
something like this may give you a start:

```
$ awk -F, '{ tags[$1] = tags[$1] ? tags[$1] "," $2 : $2 } END { for (x in tags) printf "%s;%d;%s\n", x, split(tags[x], _, ","), tags[x]; }' testfile 
dsc001.jpg;3;california,bob,betty
dcim_14275.jpg;2;skating,kids

```

---

### Post by patmagee1024 on 2011-05-09
Thank you DaithiF. It indeed works on the file data I posted. I will start trying to decipher what all the parts do. That was a quick response. My thanks!

---

### Post by patmagee1024 on 2011-05-09
When I ran your awk line against the full data I discovered I had to add 

sed -e 's/\r,/,/g' < $file1 > $file2

to remove the embedded carriage returns. Other than that it worked perfectly! Thank you so much!

---

### Post by cgroza on 2011-05-09
Perl would do that quite easily.

---

