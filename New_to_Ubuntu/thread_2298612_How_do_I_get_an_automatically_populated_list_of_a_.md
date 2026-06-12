---
title: "How do I get an automatically populated list of a series of things. (Details inside)"
date: 2015-10-12
forum: New to Ubuntu
---

### Post by triciasurfer on 2015-10-12
How can I get my computer to complete this list?


foo/booster/tang_1.xyz

foo/booster/tang_1a.xyz

...

foo/booster/tang_1h.xyz
foo/booster/tang_2.xyz
foo/booster/tang_2a.xyz
foo/booster/tang_2b.xyz
foo/booster/tang_2h.xyz
foo/booster/tang_3.xyz
...

foo/booster/tang_150h.xyz.



----
As you can see, there are two variables:

[LIST=1]
[*]The number (from 1 to 150) 
[*]What comes after the number, which is either  some letter from &#8220;a&#8221; to &#8220;h&#8221; (e.g. tang_1[SIZE=4][COLOR=#ff0000]**c**[/COLOR][/SIZE].xyz)  or nothing (e.g. tang_1.xyz). 
[/LIST]

What stays the same is everything else:
1. the "[COLOR=#ff0000]**foo/booster/tang[SIZE=4]_[/SIZE]**[/COLOR]" part
2. the "[COLOR=#ff0000]**[SIZE=5].[/SIZE]xyz**[/COLOR]" part
-----


I&#8217;d like the  list to be in a simple plaintext file.

Thank you.




:o:D

---

### Post by steeldriver on 2015-10-12
If by "my computer" you mean a shell command, then you can use bash's brace expansion feature

```

printf '%s\n' foo/booster/tang_{1..150}{,{a..h}}.xyz > somefile

```

---

### Post by triciasurfer on 2015-10-12
Yes, by "my computer", i also am open to shell/terminal. 
I just did the command and it created in in a second. That was fast! Thank you so much!

---

