---
title: "Can I use SED to search file and remove txt"
date: 2007-11-24
forum: Programming Talk
---

### Post by mdpalow on 2007-11-24
Hi everyone,

If I use the command:

grep some_special_filtering_word_here some_file_name >somenewfile.txt

It goes in a file, finds the line with the filter word you stipulate and then copies that entire line to another file.

That's exactly what I want to do, but instead of copy, I want to remove that line/txt. I have a unique word that I will put in the line so it can be easily distinguished from all other lines that might be in the file.

How can I _**remove**_ the text and not just copy it.

Is this a sed thing? If so, can anyone show me how this would be done?
-----------------------------------------------------------
Here's an example file with text just to make this easy.

File name is : test.txt  and content is:

This is a test
If this works - Yahoo!
Would be great if I could get this to work


In the test.txt file the line to remove has the key/filter word of Yahoo! 

Thank you in advance...

---

### Post by ghostdog74 on 2007-11-24
> **mdpalow said:**
> 
In the test.txt file the line to remove has the key/filter word of Yahoo! 


```

sed '/Yahoo/d' file > temp
mv temp file

```
or if your sed supports the -i option
```

sed -i '/Yahoo/d' file

```

---

### Post by mdpalow on 2007-11-24
Man, I love this forum! You guys/gals are great.

Thanks VERY much ghostdog74; worked first time.

---

