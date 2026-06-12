---
title: "Using sed to remove blocks of text containing"
date: 2009-11-16
forum: Programming Talk
---

### Post by oceanplexian on 2009-11-16
Hi, I'm trying to write a script to clean through some configuration files containing a string of text. I'm actually working with dhcpd so that I can get it to release leases on demand.

lease1 {

blah blah blah
computer number 1040

}

[COLOR="DarkRed"]lease 2 {

blah blah blah
computer number 1041

}
[/COLOR]
Any ideas on how to use sed so that it removes the entire block, so if I passed the variable with value 1041, it would delete lease 2? I tried
```
sed -n '/lease/{N;/1041/!d};/}/,/)\;/{p}'
``` but I think I've got it backwards.



Thanks,
oceanplexian

---

### Post by DaithiF on 2009-11-16
Hi,
something like this would work, assuming line spacing is consistent for all the blocks
```
sed -n '/lease/{N;N;N;N;N;/1041/d;p}' file
```

---

### Post by ghostdog74 on 2009-11-16
use gawk
```

$ var=1041
$ awk -vRS="}" -vn="$var" '$0!~n{print $0RT}' file
lease1 {

blah blah blah
computer number 1040

}


```

---

### Post by ghostdog74 on 2009-11-16
> **DaithiF said:**
> Hi,
something like this would work, assuming line spacing is consistent for all the blocks
```
sed -n '/lease/{N;N;N;N;N;/1041/d;p}' file
```

what if there are many more "blah"s in block lease 2?
```

lease 2 {

blah blah blah
blah
blah
blah
computer number 1041
blah

}


```

---

### Post by oceanplexian on 2009-11-17
Awk works fantastically and removes the correct block, however it strips the trailing } from each *other* block.  

So the output would be, 

```
lease1 {

blah blah blah
computer number 1040


lease 3 {

blah blah blah
computer number 1099

```

I'm still trying to find a way to either fix it or add the } to each block. Also note that the blocks have different sizes contained within the {} so a fixed number of lines before and after wouldn't work. 

Thanks,
oceanplexian

---

### Post by oceanplexian on 2009-11-17
Ok, I solved it with

```
awk -vRS="}" -vn="$var" '$0!~n{print $0RT "}"}'
```

but I end up with a single extra } at the end of the file

```
lease1 {

blah blah blah
computer number 1040
}

lease 3 {

blah blah blah
computer number 1099

}

}
```

This will be easy to clean up though.

Thanks,
oceanplexian

---

### Post by ghostdog74 on 2009-11-17
remove the RT
```

awk -vRS="}" -vn="$var" '$0!~n{print $0 "}"}'

```

---

