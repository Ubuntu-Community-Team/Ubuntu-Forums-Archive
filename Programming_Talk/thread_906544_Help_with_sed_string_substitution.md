---
title: "Help with sed string substitution"
date: 2008-08-31
forum: Programming Talk
---

### Post by MattUK on 2008-08-31
Hi all,

I am trying to remove dates, in the format "(YYYY)" in a string, the only examples i've been able to find are replacing words, not patterns - I can get it to work with [0-9] but not anything else, e.g. \d{4} so I figure i'm doing something seriously wrong here.

This is what I am trying, which isn't doing anything:

```

input_string="Blarp (2008) XYZ"
result=$(echo $input_string | sed -e 's/\(\d{4}\)/*/g')
echo $result

```

Any help greatly appreciated, I've been pulling my hair out for 2 hours already on this one problem!

---

### Post by stylishpants on 2008-08-31
Your problem is that sed doesn't support the special regular expression codes \d, \s, \w.  Those are only part of perl-compatible regular expressions.

You could do it in sed like this:

```
fraser@ged:/tmp$ echo "Blarp (2008) XYZ" | sed -e 's/[0-9]\{4\}//'
Blarp () XYZ

```

However, since \d, \w and friends are so useful, I often abandon sed for more complicated regexps and move to perl:

```
fraser@ged:/tmp$ echo "Blarp (2008) XYZ" | perl -pe 's/\d{4}//'
Blarp () XYZ

```

---

### Post by MattUK on 2008-08-31
Now that makes sense :) I'm with you on the perl thing, thanks a lot for the help!

---

### Post by ghostdog74 on 2008-08-31
```

 # echo $input_string | awk '{gsub(/\([0-9]+\)/,"")}1'
Blarp  XYZ


```

---

### Post by rangalo on 2008-09-01
Hi,

If you want to stick with sed, I recently found out that 
following works
```

echo "Blarp (2008) XYZ" | sed -e  's/[[:digit:]]\{4\}/*/g'

```

---

