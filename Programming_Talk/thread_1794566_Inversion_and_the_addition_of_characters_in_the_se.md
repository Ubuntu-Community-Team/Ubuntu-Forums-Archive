---
title: "Inversion and the addition of characters in the sed"
date: 2011-07-01
forum: Programming Talk
---

### Post by 5ive on 2011-07-01
I have the characters:
```
1
2
3
4
5
```
I want to get in the sed:
```
a
1
b
2
b
3
b
4
b
5
```
I have written:
```
echo -e '1\n2\n3\n4\n5' | sed -n -e '1!G;h;$p' -e '1a a' -e '2,$a b'
```
I received:
```
a
b
b
b
5
4
3
2
1
b
```
Bad result. Help me somebody?

---

### Post by amauk on 2011-07-01
```
echo -e '1\n2\n3\n4\n5' |  sed -e 's|^1$|a\n1|;s|^\([1-4]\)$|\1\nb|'
```If a line is '1', append an 'a' before
If a line is '[1-4]', append a 'b' after

---

### Post by 5ive on 2011-07-01
Thank you.
```
echo -e '1\n2\n3\n4\n5' | sed 's|^|b\n|;$s|b|a|;1!G;h;$!d'
```
Well done?

---

