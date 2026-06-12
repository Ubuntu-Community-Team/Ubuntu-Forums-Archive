---
title: "BASH text editing"
date: 2008-08-26
forum: Programming Talk
---

### Post by hammer v2 on 2008-08-26
Hi guys,
I'm making a metapackage creator script and need some help manipulating text.

I have a txt file like this...

Package: barry
Version: 1.0
Section: unknown
Priority: optional
Maintainer: Superdeb! <superdeb@superdeb.org>
Architecture: i386
Depends: ckermit_211-8ubuntu1, libsocksd_1.1.18-2.1, openbsd-inetd_0.20050402-6
Description: This is the metapackage used to install barry


But i need it to look like this;

Package: barry
Version: 1.0
Section: unknown
Priority: optional
Maintainer: Superdeb! <superdeb@superdeb.org>
Architecture: i386
Depends: [COLOR="Red"]ckermit, libsocksd, openbsd-inetd[/COLOR]
Description: This is the metapackage used to install barry


Any Ideas?

---

### Post by rangalo on 2008-08-26
Hi,

If you are sure you want to drop everything after '_' from a given string.

this code will do it
```

str_var=ckermit_211-8ubuntu1
echo $str_var  # prints ckermit_211-8ubuntu1
echo ${str_var%%_*}  # prints ckermit

```

I hope this helps.

regards,
Hardik

---

### Post by stylishpants on 2008-08-26
```

fhanson@fhanson:/tmp$ perl -pe 's/_[^\s,]*//g if /^Depends:/' input.txt
Package: barry
Version: 1.0
Section: unknown
Priority: optional
Maintainer: Superdeb! <superdeb@superdeb.org>
Architecture: i386
Depends: ckermit, libsocksd, openbsd-inetd
Description: This is the metapackage used to install barry


```

---

### Post by ghostdog74 on 2008-08-27
```

awk '/Depends/{
 for(i=1;i<=NF;i++) {
  if($i ~ "_") {
   split($i,a,"_")
   $i=a[1]","
  }
  sub(/\,$/,"")
 }
 $1=$1
}1' file

```

---

