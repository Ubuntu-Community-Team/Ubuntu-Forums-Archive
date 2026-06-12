---
title: "Bash: delete characters after colon in specific columns"
date: 2014-02-03
forum: Programming Talk
---

### Post by Muriel_Gros-Baltha on 2014-02-03
Hello !

I have this tab-delimited file :
```

KE339719.1    13    0/0:2,0:2:33:0,33,428       0/0:1,0:1:9:0,9,148
KE332739.1    14    md                          0/0:3,1:4:15:0,15,276
KE336330.1    14    0/1:5,12:17:99:157,0,382    0/1:2,7:9:99:100,0,147
```

In the third and fourth column, I want to delete everything that is after ":", to obtain :
```

KE339719.1    13    0/0    0/0
KE332739.1    14    md     0/0
KE336330.1    14    0/1    0/1
```

I wanted to combine awk and sed but don't manage to find a solution :(

Any help ?

Thanks !

Muriel

---

### Post by Bucky Ball on 2014-02-03
*Thread moved to **Programming Talk**.*

---

### Post by sisco311 on 2014-02-03
This is how you do it in Bash:
```

while read -r f1 f2 f3 f4
do
    printf '%s\t' "$f1" "$f2" "${f3%%:*}" "${f4%%:*}"
    printf '\n'
done < file

```
See: BashFAQ 001 (link in my sig) and
[http://mywiki.wooledge.org/BashGuide/Parameters#Parameter_Expansion](http://mywiki.wooledge.org/BashGuide/Parameters#Parameter_Expansion)

---

### Post by Vaphell on 2014-02-03
```
sed -r 's/:[^ \t]+//g'
```
though it won't necessarily clean up the formatting

```
while read -r c1 c2 c3 c4; do printf "%s\t%s\t%s\t%s\n" "$c1" "$c2" "${c3%%:*}" "${c4%%:*}"; done < file
```


```
$ sed -r 's/:[^ \t]+//g' tab_delim.txt 
KE339719.1    13    0/0       0/0
KE332739.1    14    md                          0/0
KE336330.1    14    0/1    0/1
$ while read -r c1 c2 c3 c4; do printf "%s\t%s\t%s\t%s\n" "$c1" "$c2" "${c3%%:*}" "${c4%%:*}"; done < tab_delim.txt 
KE339719.1	13	0/0	0/0
KE332739.1	14	md	0/0
KE336330.1	14	0/1	0/1
```

---

### Post by Muriel_Gros-Baltha on 2014-02-04
Hello !

Thank you both for your answers.

I tried the sed option and don't have formatting problems so it's perfect !

Mu

---

