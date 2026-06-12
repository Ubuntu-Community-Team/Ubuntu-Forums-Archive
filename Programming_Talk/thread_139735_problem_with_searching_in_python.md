---
title: "problem with searching in python"
date: 2006-03-04
forum: Programming Talk
---

### Post by freemanen on 2006-03-04
for line in file("hej.txt","r"):
	if(re.search(r"*\www*\",line))

i would like it to search for everything that contains *www*  but only that string not the whole line. like dfdsfwwwdfdsf or ddsfsdwwwöäåq

---

### Post by LordHunter317 on 2006-03-04
I'm confused.  You'll have to define what you mean by "string" then.  You're delimiting based on lines.  If you want to delimit based on something else instead, you need to do that.  For example, if you want to search based on words, you need to split via whitespace first, then search.

---

### Post by Van_Gogh on 2006-03-05
I'm not really sure what you want either, but if what you want is search for if the string "www" is in a line you can do:

```

for line in file("hej.txt","r"):
    if "www" in line.lower():
        do_something()

```

by using line.lower() above we get positives for both lower mixed and upper cases,  that is "Www", "www" and "WWW" will all be ok. 

If what you want is different than what is above, you'll probably need to be more precise.

---

