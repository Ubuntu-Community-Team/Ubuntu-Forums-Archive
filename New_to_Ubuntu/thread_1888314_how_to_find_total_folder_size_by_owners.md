---
title: "how to find total folder size by owners"
date: 2011-11-29
forum: New to Ubuntu
---

### Post by Unewbeginner on 2011-11-29
Hi, for example I have 100 folders, created either by Jack, Mike & Kevin. How could I get a list like below:

18G Jack
5.3G Mike
1.2G Kevin

Thanks.

---

### Post by johnmay on 2011-11-29
Here is a link that might get you started: [http://www.earthinfo.org/linux-disk-usage-sorted-by-size-and-human-readable/](http://www.earthinfo.org/linux-disk-usage-sorted-by-size-and-human-readable/)

the ls command also has quite a bit of information. Though more details would allow for a more specific answer. 

Are the folders in one directory?

---

### Post by Unewbeginner on 2011-11-29
> **johnmay said:**
> 
Are the folders in one directory?

Yes. They are in one directory. Thanks for your info, but I can't find any solution for the total sizes of individual owners.

---

### Post by mutley89 on 2011-11-29
Something like this should work, as long as the directories you want to total are all at the same level in the directory hierarchy:
```

for name in Jack Mike Kevin ; do echo -n "$name: " ; find  directory_to_search -maxdepth 1 -mindepth 1 -type d -user "$name" -exec du -csh {} + | tail -n1 ;  done

```

---

