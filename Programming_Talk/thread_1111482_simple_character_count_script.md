---
title: "simple character count script"
date: 2009-03-30
forum: Programming Talk
---

### Post by jakupl on 2009-03-30
I want to do a faroese DVORAK keyboard layout, I cant find any list that tells me witch characters are most used, so is there a way of doing a bash script, that can take large amounts of text and count the instances of each letter, and maybe sort them by frequency "not case sensitive"? bear in mind that Faroese contains special letters like Á, Ú, Ó, Í, Ý and Ð

---

### Post by jakupl on 2009-03-31
bump

---

### Post by Arndt on 2009-04-01
> **jakupl said:**
> I want to do a faroese DVORAK keyboard layout, I cant find any list that tells me witch characters are most used, so is there a way of doing a bash script, that can take large amounts of text and count the instances of each letter, and maybe sort them by frequency "not case sensitive"? bear in mind that Faroese contains special letters like Á, Ú, Ó, Í, Ý and Ð

I would do it in C or Perl. Does it have to be a shell script?

Maybe this old thread will help: [http://ubuntuforums.org/showthread.php?t=957610](http://ubuntuforums.org/showthread.php?t=957610)

---

### Post by ghostdog74 on 2009-04-01
there are many of such scripts lying around in the internet. just have to a search on them. 
```

awk 'BEGIN{FS=""}{for(i=1;i<NF;i++)a[$i]++}END{for(o in a) {print a[o],o}}' file

```

---

### Post by jakupl on 2009-04-01
> **ghostdog74 said:**
> there are many of such scripts lying around in the internet. just have to a search on them. 
```

awk 'BEGIN{FS=""}{for(i=1;i<NF;i++)a[$i]++}END{for(o in a) {print a[o],o}}' file

```


I tried to search, but I didn't find anything. Thanks, I will try this when I get home

---

### Post by jakupl on 2009-04-02
This works great. Now I am going to figure out how to get percentages, make it count these letters: Ð, Á, Ú, Í, Ó and ý, I also would like the output arranged in order of what is used the most. And exclude "space", "enter" and "tab", and all the strange letters that are shown as a question mark.

---

