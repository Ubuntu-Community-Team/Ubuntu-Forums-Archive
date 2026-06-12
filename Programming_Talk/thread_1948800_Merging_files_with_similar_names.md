---
title: "Merging files with similar names"
date: 2012-03-28
forum: Programming Talk
---

### Post by xalx on 2012-03-28
Hey all, so I have a folder with text files. They are in the naming format of,

date/age type/user number
e.g. 11-09-adultUser118.txt

The thing is there could also be a 11-08-adultUser118.txt in the folder and this is across the board with each file. One user can have two separate files but for two different dates.

I'm trying to find a way to merge the two files together by scanning the folder, finding the same adultUser118.txt and merge it into one file without the date.

So far I've got,

```
for i in 11-09* ; 
do cat $i >> $(echo $i | sed 's/\(11-09[0-9]*-adult[a-z0-9].txt/') ; 
done
```

but all I get back is a ambiguous redirect error.

Can anyone point me in the right direction?

---

### Post by xalx on 2012-03-29
Actually managed to solve this a totally different way, took a bit longer but got the same result.

Thanks

---

### Post by ofnuts on 2012-03-29
> **xalx said:**
> Actually managed to solve this a totally different way, took a bit longer but got the same result.

Thanks
Wouldn't 
```

# $user=adultUser118
cat *-$user.txt > $user.txt

```

be  enough?

---

