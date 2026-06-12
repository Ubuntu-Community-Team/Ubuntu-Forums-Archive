---
title: "script help...how to change timestamp on all files/folders after a certain date"
date: 2013-09-09
forum: Programming Talk
---

### Post by sam_baker2 on 2013-09-09
hi,

I need help on a script that will change the timestamp on all files and folders & sub-files and
sub-folders, that are only after a certain date.

Otherwords, for example, in a folder I may have files and sub-folders with some dates of oct 3, 2009 and some that are 
june 17, 2013. I want to recursely run through this folder and change all of those after ( or equal to & after, don't matter )
 june 17, 2013 to jan 1, 2013.

I think the script may revolve around this, but I don't know how to look for only timestamps of a certain date or latter
I think I would need to cd into the folder first:

```
find .  -exec  touch  -d  '17 Jun 2013 01:01'  {} 
```

Thanks

---

### Post by erind on 2013-09-09
> **sam_baker2 said:**
> hi,

I need help on a script that will change the timestamp on all files and folders & sub-files and
sub-folders, that are only after a certain date.

[...]


You can let '*find*' do the date comparisons, then just '*touch*' the output. Try it first on a test directory. 

```
find . -newermt "June 17 2013" -exec touch -d 'Jan 1 2013 01:01' {} +
```

The other way is creating a template file, then using it as reference when comparing timestamps, with -newer, -anewer options. More info here:

[http://www.gnu.org/software/findutils/manual/html_mono/find.html#Comparing-Timestamps](http://www.gnu.org/software/findutils/manual/html_mono/find.html#Comparing-Timestamps)

---

### Post by sam_baker2 on 2013-09-09
Thanks erind,
that seemed to work. I will try this more some more tonight.

---

