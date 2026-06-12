---
title: "Grep []"
date: 2008-01-14
forum: Programming Talk
---

### Post by dnash29 on 2008-01-14
Hi, some help will be much apreciated.

I am try to grep a log file and pull out [35  ] and [D], I need to use [] as these are part of the logs

        |    [35    ] [D]

Does anyone know how I can grep this information?

Thanks Darren

---

### Post by Thanoulis on 2008-01-14
Try this:
```
cat <the name of the file> | grep \[35\] \[D\]
```

---

### Post by dnash29 on 2008-01-14
unfortunately that didnt work

grep: [D]: No such file or directory

---

### Post by Cappy on 2008-01-14
It thought that [D] was the name of the (optional) filename.
```

grep '\[35\] \[D\]' <the name of the file>
```
will match a line with "[35] [D]" with a space separating the two

If you want lines with [35] OR [D] use
```
grep '\(\[35\]\|\[D\]\)' <the name of the file>
```

If you want lines with [35] AND [D] use
```
grep '\[35\]' <the name of the file> | grep  '\[D\]'
```

---

### Post by ghostdog74 on 2008-01-14
> **dnash29 said:**
> Hi, some help will be much apreciated.

I am try to grep a log file and pull out [35  ] and [D], I need to use [] as these are part of the logs

        |    [35    ] [D]

Does anyone know how I can grep this information?

Thanks Darren
alternatively, you can use awk
```

awk '/\[35\]/ && /\[D\]/' file

```

---

### Post by dnash29 on 2008-01-21
Thank you for help

---

### Post by naugiedoggie on 2008-01-21
> **Thanoulis said:**
> Try this:
```
cat <the name of the file> | grep \[35\] \[D\]
```

AWK!  oh my!

[Useless Use of Cat]("http://partmaps.org/era/unix/award.html")

;-)

Thanks.

mp

---

