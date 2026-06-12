---
title: "[sed] regex question"
date: 2011-12-02
forum: Programming Talk
---

### Post by emiller12345 on 2011-12-02
running into an escaping issue...
```
$ echo "something 'once' and again 'here'" | sed -e "s/^\(.*\)'\(.*\)'/\1'+\"'\2'\"+'/"
something 'once' and again '+"'here'"+''
```
it's only catching the last statement, not sure how to get it to catch multiple statements.

any ideas?

---

### Post by ofnuts on 2011-12-02
I think you get caught by the greedy match, your:[FONT=Courier New]** '\(.*\)'**[/FONT] matches anything between quotes, including other quotes. What you want is really [FONT=Courier New]**'\([^']*\)' **[/FONT]i.e.: quote, anything but quote, and quote.

---

### Post by emiller12345 on 2011-12-02
```
$ echo "something 'once' and again 'here'" | sed -e "s/'\([^']*\)'/'+\"'&'\"+'/"
something '+"''once''"+' and again 'here'
$ echo "something 'once' and again 'here'" | sed -e "s/'\([']*\)'/'+\"'&'\"+'/"
something 'once' and again 'here'
$ echo "something 'once' and again 'here'" | sed -e "s/^\(.*\)'\(.*\)'/\1'+\"'\2'\"+'/"
something 'once' and again '+"'here'"+'
$ echo "something 'once' and again 'here'" | sed -e "s/^\(.*\)'\([^']*\)'/\1'+\"'\2'\"+'/"
something 'once' and again '+"'here'"+'
$ echo "something 'once' and again 'here'" | sed -e "s/^'\([^']*\)'\([^']*\)'/\1'+\"'\2'\"+'/"
something 'once' and again 'here'
$ echo "something 'once' and again 'here'" | sed -e "s/'\([^']*\)'/'+\"'\1'\"+'/"
something '+"'once'"+' and again 'here'
```

It seems that none of these are exactly correct. It's close, but not there yet...

---

### Post by Vaphell on 2011-12-03
no idea what the expected output is exactly but
```
$ echo "something 'once' and again 'here'" | sed -r "s/([^']*)'([^']*)'/\1'+\"'\2'\"+'/g"
something '+"'once'"+' and again '+"'here'"+'
```

---

### Post by emiller12345 on 2011-12-03
Ah, i see. yes that is it. thank you.

---

