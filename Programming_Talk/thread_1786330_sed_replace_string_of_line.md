---
title: "sed replace string of line"
date: 2011-06-19
forum: Programming Talk
---

### Post by xaitax on 2011-06-19
Hi,

i have a file with lots of lines like that

```
randomstring | randomstring
```

and i want to remove everything until the "|".

Any ideas how to do this with sed/awk?

TIA!

---

### Post by SevenMachines on 2011-06-19
Been a while, would something like this not do it?

test.txt:
```
randomstring | randomstring
randomstring | randomstring
randomstring | randomstring
randomstring | randomstring
randomstring | randomstring

``````
$ sed 's/.*\(|.*\)/\1/g' test.txt

| randomstring
| randomstring
| randomstring
| randomstring
| randomstring

```I'm a little forgetful on the head twisting hieroglyphs of sed though :)

[EDIT] but
 sed -i 's/.*\(|.*\)/\1/g' test.txt
for 'in place' editing obviously

---

### Post by geirha on 2011-06-19
```

awk -F'|' '{print $NF}' file
sed 's/.*|//' file
ed -s file <<< $'g/.*|/s///\nw'

```

The last one edits the file.

---

