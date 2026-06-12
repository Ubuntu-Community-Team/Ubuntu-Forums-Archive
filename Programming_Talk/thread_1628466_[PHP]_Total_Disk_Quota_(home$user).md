---
title: "[PHP] Total Disk Quota (/home/$user)"
date: 2010-11-22
forum: Programming Talk
---

### Post by domzz on 2010-11-22
So I am writing a php script and I need to find the total diskspace of a directory. I have used space already. I have a couple of different users with quotas


```
$path = "/home/" . ($_SERVER['PHP_AUTH_USER']);
$used = exec("du -c -a $path");

echo $used; 
```

Will give me the disk space used. But I need total quota for that user.

---

### Post by domzz on 2010-11-22
For example, when I:
```
# quota -u domz
Disk quotas for user domz (uid 1010):
     Filesystem  blocks   quota   limit   grace   files   quota   limit   grace
      /dev/sda2      24  36700160 36864000               7       0       0      
```
I want to get just the 36864000. I know I need to use AWK or grep (but I suck at writing code).

---

### Post by jacob.david on 2010-11-22
try

quota -u domz | tail -n 1 | awk '{print $4}'

---

### Post by domzz on 2010-11-22
> **jacob.david said:**
> try

quota -u domz | tail -n 1 | awk '{print $4}'

php doesn't want to output it? Do i have to give it permission in visudo?

---

### Post by domzz on 2010-11-22
Ok, php is not allowed to grab quotas.. so I just output quotas into tmp ([http://www.afp548.com/article.php?story=20041205173932493](http://www.afp548.com/article.php?story=20041205173932493))

and do "cat /tmp/quotas |  grep domz | tail -n 1 | awk '{print $4}'"

---

