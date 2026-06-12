---
title: "How can I get egrep to match something that occurs n to m times *but not more*?"
date: 2017-03-28
forum: Programming Talk
---

### Post by s3a on 2017-03-28
If I do

```
egrep "thin[g]{2,3}" ./list.txt
```

, it shows me all the occurrences "thin" followed by 2 or more "g"s.

In other words, the above egrep line seems to do the same thing as the following egrep line.:
```
egrep "thin[g]{2,}" ./list.txt
```.

I understand that, if there are four or more occurrences of the character *g* after *thin*, it can be concluded that are there is subtext that is either [/i]thingg[/i] or *thinggg*, regardless of how many extra "g"s there are, and that that's why egrep is not ignoring the output with more than three consecutive "g"s after "thin", but how can I get it to behave as I intend for this particular case?

Any input would be greatly appreciated!

---

### Post by s3a on 2017-03-28
Technically, it works when I do

```
egrep "thin[g]{2,3}" ./list.txt | egrep -v "[g]{4,}"
```

, but how do I make it work by just using regex, without "piping trickery"?

---

### Post by norobro on 2017-03-28
If the words are each on a single line you can use the end of string anchor "$":
```
egrep  "thing{2,3}$" list.txt
```If the words are embedded in a string use word boundaries "\b":
```
egrep -o '\bthing{2,3}\b' list.txt
```See man egrep for the -o option.

---

### Post by vasa1 on 2017-03-29
Even though it's more convenient and it still works, *egrep* is deprecated and *grep -E* is suggested. *man grep* has this:```
       In  addition,  the variant programs egrep, fgrep and rgrep are the same as
       grep -E,  grep -F,  and  grep -r,  respectively.    These   variants   are
       deprecated, but are provided for backward compatibility.


```

---

### Post by s3a on 2017-03-29
Thank you both! :)

---

