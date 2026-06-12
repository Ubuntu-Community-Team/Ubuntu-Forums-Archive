---
title: "Replacing words in document using sed"
date: 2013-05-07
forum: Programming Talk
---

### Post by stRunF on 2013-05-07
Hello there, my question would be the following:
How would you replace, let's say the 2nd word of a document(eg. for document: "one two three four") with another word?
Idea is to replace the 2nd(or an Xth word, not relevant) word, not *sed 's/two/somethingelse/g' document*

Thanks in advance :)

---

### Post by schragge on 2013-05-07
```
echo one two three four|awk '$2="somethingelse"'
```
This will replace the second word *in each line*. If, however, all you want is to replace the second word of *the whole document* then try
```
echo one two three four | perl -0pe 's/\S+\s+\K\S+/somethingelse/'
```
Doing it with sed is rather tricky unless you have sed 4.2.2 which is not yet in Ubuntu
```
echo one two three four | sed -n '1h;1!H;${g;s/[^[:space:]]\+/somethingelse/2p}'
```
But with GNU sed 4.2.2, it's a no-brainer
```
echo one two three four|sed -z 's/\S\+/somethingelse/2'
```

---

### Post by stRunF on 2013-05-09
Thank you :)

---

