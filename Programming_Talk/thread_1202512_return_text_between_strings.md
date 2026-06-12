---
title: "return text between strings"
date: 2009-07-02
forum: Programming Talk
---

### Post by wrathkeg on 2009-07-02
Hi all,
I have a file containing many lines like the following:
```
<w nite:id="IB4003.A.words2236" starttime="1141.89" endtime="1142.17">Yeah</w>
```
I am trying to find a command which will return just what is between starttime=" and the next " i.e. 1141.89.  Does anyone know how I can do this?  I have spent a while trying out sed commands, but couldn't really get anywhere.
Thanks in advance,
Wrathkeg

---

### Post by cdiem on 2009-07-02
Edited:
You could try with something like:

for starttime:
[PHP]# cat test.txt |  perl -wnl -e'/starttime=.(\d.+). /g and print $1';[/PHP]
(with an empty space after the last dot..)

for endtime:
[PHP]
# cat test.txt |  perl -wnl -e'/endtime=.(.\d.+)"/g and print $1';[/PHP]

where 'test.txt' would be your file. I'm not very good with perl, so maybe hearing also other opinions would be adviseable...

---

### Post by ghostdog74 on 2009-07-02
```

awk 'BEGIN{ FS="starttime=\""}{gsub(/\".*/,"",$2);print $2}' file

```

---

### Post by ghostdog74 on 2009-07-02
> **cdiem said:**
> Edited:
You could try with something like:

for starttime:
[PHP]# cat test.txt |  perl -wnl -e'/starttime=.(\d.+). /g and print $1';[/PHP]
(with an empty space after the last dot..)

for endtime:
[PHP]
# cat test.txt |  perl -wnl -e'/endtime=.(.\d.+)"/g and print $1';[/PHP]

where 'test.txt' would be your file. I'm not very good with perl, so maybe hearing also other opinions would be adviseable...

there's no need to use cat. pass the file to perl
```

perl -wnle "......." file

```

---

### Post by wrathkeg on 2009-07-06
thanks, everyone:  both the perl and the awk suggestions worked.  I wish I had asked earlier!
wrathkeg

---

