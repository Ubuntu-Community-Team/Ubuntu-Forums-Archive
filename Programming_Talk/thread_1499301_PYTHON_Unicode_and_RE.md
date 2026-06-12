---
title: "PYTHON: Unicode and RE"
date: 2010-06-01
forum: Programming Talk
---

### Post by jesuisbenjamin on 2010-06-01
Hi there,

As i thought i had through how to handle unicode strings with python, now using RE i am facing a similar problem again. The info i found online did not help, perhaps because i use the re.split() function.

Here is the code:

[PHP]def cut(string):
    cut_string = re.split(knife, string)
    print cut_string

nagari = "pr&#257;tipadau sa&#7747;&#7779;&#7789;hitau vai dr&#363;vyam"
knife = '([^[au]|[ai]|[o]|[e]|[&#257;]|[&#363;]|[&#299;]|[u]|[i]|[a]]*[[o]|[e]|[&#257;]|[&#363;]|[&#299;]|[u]|[i]|[a]])'
knife = re.compile(knife, re.UNICODE)
cut(nagari)[/PHP]

The result is:
[PHP]>>>[u'pr\u0101tipadau sa\u1e43\u1e63\u1e6dhitau vai dr\u016bvyam'][/PHP]
while i expect:
[PHP]>>>['pr&#257;', 'ti', 'pa', 'dau', ' ', 'sa', '&#7747;&#7779;&#7789;hi', 'tau', 'vai', 'dr&#363;', 'vya', 'm'][/PHP]

I tried several things (adding u or ur in front of my strings or decode('utf-8') etc) but i only get coded results and split fails)

I think i need help on that one once more :(
Thanks

---

