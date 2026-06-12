---
title: "weird script behaviour"
date: 2009-08-05
forum: Programming Talk
---

### Post by laplace/d on 2009-08-05
i have the following code written on a shell script:
```
pnt=$(cat /etc/mtab | grep vfat)
pnt_real= ${pnt:0:9}
```

if i run each line straight on the shell and then 'echo $pnt_real'
i see the correct value. but when i write down the same to lines on gedit as part of a script it gets strange colours:
[IMG]http://lh6.ggpht.com/_-eMYxH6IV1M/SnnNKoJiOsI/AAAAAAAAAJg/M9zkQNn0U1k/script.png[/IMG]
...and not only that, when i run the script, it doesnt do the job.

is there any other way i can cut the string???
from the line:
```
/dev/sdb1 /media/disk-1 vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0

```
i only want '/dev/sdb1' or whatever it might say instead of sdb1.

---

### Post by djurny on 2009-08-05
if i understand correctly,

```
awk '$3=="vfat" { print $1 }' /etc/mtab
```

will do exactly the same..

what is the shebang you're using? 

```
#!/bin/sh
```
or
```
#!/bin/bash
```
or something else?

---

### Post by laplace/d on 2009-08-05
i am using:
```
#!/bin/bash
```
i also tried bin/sh now that u mentioned, but i get the same result.
i even tried your option, which runs beautifuly on the terminal but not on the script
```
pnt_real= $(awk '$3=="vfat" { print $1 }' /etc/mtab)
```
but following that line, i echo $pnt_real and nothing, the variable is empty.

---

### Post by djurny on 2009-08-06
> **laplace/d said:**
> i am using:
```
#!/bin/bash
```
i also tried bin/sh now that u mentioned, but i get the same result.
i even tried your option, which runs beautifuly on the terminal but not on the script
```
pnt_real= $(awk '$3=="vfat" { print $1 }' /etc/mtab)
```
but following that line, i echo $pnt_real and nothing, the variable is empty.

then just use ```
awk '$3=="vfat" { print $1 }' /etc/mtab
```
or 
```

#!/bin/bash

awk '$3=="vfat" { print $1 }' /etc/mtab | while read a; do
  echo $a
done

# EOF

```

---

### Post by geirha on 2009-08-06
> **laplace/d said:**
> i am using:
```

[CODE]pnt_real= $(awk '$3=="vfat" { print $1 }' /etc/mtab)
```


It's the space between = and $

```
pnt_real=$(...)
```

Bash is picky.

Here's how you can do the same in pure bash:
```

while read fs_spec fs_file fs_vfstype fs_mntops fs_freq fs_passno; do
    if [[ $fs_vfstype == "vfat" ]]; then
        echo "$fs_spec has filesystem $fs_vfstype and is mounted on $fs_file";
    fi
done < /etc/mtab

```

EDIT: Oh and in case you're wondering, I picked those variable names from fstab's man-page (man fstab). They can of course be replaced by whatever variable names you'd like.

---

### Post by laplace/d on 2009-08-06
you r right, it was the space between = and $. that alone did. as for the second part i didnt understand anything... is there any good tutorial out there some sort of "scripting for dummies" kind of thing, cause the syntax seems quite complicated and confusing.
and finally whats the difference between bash and sh?

---

### Post by geirha on 2009-08-07
I recommend this guide for learning bash: [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

As for the difference between /bin/sh and /bin/bash, I think this Wikipedia page explains most of it: [http://en.wikipedia.org/wiki/Bourne_shell](http://en.wikipedia.org/wiki/Bourne_shell)

---

