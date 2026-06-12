---
title: "organizing a list with varied length strings by their prefix"
date: 2012-05-31
forum: Programming Talk
---

### Post by thatdamkid on 2012-05-31
Working in bash normally using awk and sed.

So I have a list of strings, around 3000, that I awked from an html file.

```
awk "/$employee/"'{getline; print}' ~/employeenumids |
tr -d '\--'|
sort
#cut -f1 -d: |
#xargs

```


Here is the short list
```

    t2070829
    t20716
    t20721
    t9073425
    t9073409
    t24007
    t24005
    t24023
    t24027
    t2078327
    t2078316
    t2078621
    t207801
    t20788
    t2078903
    t2078941

```

Their prefix is always the length of the string minus two. So this means that the length of the prefix can vary depending on the total length of the string.

Prefix explanation

```

    t250705   is   t2507
    t26001    is   t260
    t260441   is   t2604
    t27109    is   t271
    t27321    is   t273
    t27341    is   t273
    t27323    is   t273
    t28009    is   t280
    ...

```
You get the point.

So far I have used sort and organized the file but its very hard to read when I have a column of 3000 id's

I would like to pipe in an awk or only use awk to make the first output from above to look somewhat like this.

  
```

  --t90734--
    t9073425
    t9073409

  --t240--
    t24007
    t24005
    t24023
    t24027

  --t20783--
    t2078327
    t2078316

  --t20789--
    t2078903
    t2078941
```

Kudos if we can not output anything that doesn't have a reoccurring prefix.

Thanks in advance for taking the time to read all of that.

---

### Post by erind on 2012-05-31
One way would be:

```
awk '{ s=$0; sub(/^t/,"",s); key=substr(s,1,length(s)-2); a[key]=a[key] RS $0 }

     END { for( j in a ) print "\n--t" j "--" a[j] }' filename

```Note that the code assumes that the file format is the same as the one given above, and it uses an associative array so the output order is not guaranteed to be the same as the input. 
Also the file *does not have to be sorted before hand* for the code to work. 

[ I added some extra lines in the original file. ]

```
$ cat filename
t2070829
t20716
t20721
t9073425
t9073409
t24007
t24005
t24023
t24027
t2078327
t2078316
t2078621
t207801
t20788
t2078903
t2078941


awk '{ s=$0; sub(/^t/,"",s); key=substr(s,1,length(s)-2); a[key]=a[key] RS $0 }

     END { for( j in a ) print "\n--t" j "--" a[j] }' filename

--t20789--
t2078903
t2078941

--t207--
t20716
t20721
t20788

--t20708--
t2070829

--t2078--
t207801

--t20783--
t2078327
t2078316

--t20786--
t2078621

--t90734--
t9073425
t9073409

--t240--
t24007
t24005
t24023
t24027
```

---

### Post by thatdamkid on 2012-06-01
> **erind said:**
> One way would be:

```
awk '{ s=$0; sub(/^t/,"",s); key=substr(s,1,length(s)-2); a[key]=a[key] RS $0 }

     END { for( j in a ) print "\n--t" j "--" a[j] }' filename

```Note that the code assumes that the file format is the same as the one given above, and it uses an associative array so the output order is not guaranteed to be the same as the input. 
Also the file *does not have to be sorted before hand* for the code to work. 

[ I added some extra lines in the original file. ]

```
$ cat filename
t2070829
t20716
t20721
t9073425
t9073409
t24007
t24005
t24023
t24027
t2078327
t2078316
t2078621
t207801
t20788
t2078903
t2078941


awk '{ s=$0; sub(/^t/,"",s); key=substr(s,1,length(s)-2); a[key]=a[key] RS $0 }

     END { for( j in a ) print "\n--t" j "--" a[j] }' filename

--t20789--
t2078903
t2078941

--t207--
t20716
t20721
t20788

--t20708--
t2070829

--t2078--
t207801

--t20783--
t2078327
t2078316

--t20786--
t2078621

--t90734--
t9073425
t9073409

--t240--
t24007
t24005
t24023
t24027
```

Brilliance!

You have given me a solid launchpad to continue my onto my goal.  this is only a small part in a larger script that I am working on. Effectively I will be sorting, grouping and organizing several tens of thousands strings, and teaching myself code all over again.

---

