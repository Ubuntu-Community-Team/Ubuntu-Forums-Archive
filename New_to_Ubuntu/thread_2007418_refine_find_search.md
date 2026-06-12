---
title: "refine find search"
date: 2012-06-20
forum: New to Ubuntu
---

### Post by nathanv221 on 2012-06-20
hey i'm looking for a file and when i use a find search i am getting too much information to sift through. i am only looking for a .txt file but and getting a lot of .deb files, how do i refine the search to only look for .txt files?

if it helps what im putting in is "find REQUIRED /home/user/../../var/cache/apt/archives/"

where of course user is my name

---

### Post by CharlesA on 2012-06-20
Why are you searching in /var/cache/apt/archives/ ?

```
find /path/to/directory -name filename.txt -print
```

---

### Post by codemaniac on 2012-06-20
> **nathanv221 said:**
> hey i'm looking for a file and when i use a find search i am getting too much information to sift through. i am only looking for a .txt file but and getting a lot of .deb files, how do i refine the search to only look for .txt files?

if it helps what im putting in is "find REQUIRED /home/user/../../var/cache/apt/archives/"

where of course user is my name
The below would look for only .txt files in the /path/to/search directory .

```
find /path/to/search -name "*.txt" -print
```

<edit>Sorry for the redundant post , guess me and charlsea were minutes apart ;).

However i want to add something for your help , in a find search if you can not remember the exact file name you can always use wildcards and wrap them in double quotes as above .
</edit>

---

### Post by HiImTye on 2012-06-20
you can also pipe to other tools which can give you better or simpler filtering options, such as grep or sed
```
find / -type f 2>/dev/null | grep -iE '.*[0-9]*|\.avfilter|etc\..*$'
```

---

### Post by Kevin McCready on 2012-06-21
thanks
hoping you might be able to spell out exactly what each thing does in that command. when I ran it I got heaps and heaps of results.

---

### Post by greenpeace on 2012-06-21
Might be better to use the -iname flag... just in case the file has the extension .TXT:

[FONT="Courier New"]find /path/to/files/ -iname "*.txt"[/FONT]

then filter your results with grep:

[FONT="Courier New"]find /path/to/files/ -iname "*.txt" | grep -i <thing you're looking for>[/FONT]

What are you looking for in /var/cache/apt/archives/ ?

---

