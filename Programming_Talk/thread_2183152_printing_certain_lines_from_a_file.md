---
title: "printing certain lines from a file"
date: 2013-10-23
forum: Programming Talk
---

### Post by sha1sum on 2013-10-23
Say I have a text file: story.txt.

Is there a command that allows me to print on the screen only lines 30 to 35 from this file? The only solution I can think of would be this:

```

$ cat story.txt | head -n 35 | tail -n 5
```

But that isn't really pretty. Is there a better way?

---

### Post by Bachstelze on 2013-10-23
```
cat story.txt | sed -n '30,35 p'
```

---

### Post by sha1sum on 2013-10-23
Thanks!

---

### Post by sisco311 on 2013-10-23
Check out BashFAQ 011 (link in my signature) for some examples. In a script I'd use [ed]("http://wiki.bash-hackers.org/howto/edit-ed"):
```

x=30 y=35
ed -s file << EOF
${x},${y}p
EOF

```

---

### Post by sha1sum on 2013-10-23
Thank you also. :-) Making scripts is something I'm still learning, but I'll definitely keep that in mind too.

---

### Post by sha1sum on 2013-12-01
Update to my own topic, lol. I did some more studying and I found that you can also do it like this:

```
cat story.txt | sed '30,35!d' 
```

or even shorter:

```
sed '30,35!d' story.txt 
```

Basically it tells sed to delete everything, except line 30 to 35.

---

### Post by vasa1 on 2013-12-01
> **sha1sum said:**
> Update to my own topic, lol. I did some more studying and I found that you can also do it like this:

```
cat story.txt | sed '30,35!d' 
```

...
I had done something like that and got [this]("http://partmaps.org/era/unix/award.html#uucaletter"). Ever since then, I've been cautious with cats ;)

---

### Post by sha1sum on 2013-12-02
Did they give you the "Useless Use of Cat Award"? lol. Tell them you gratefully accept and that you've given it an honorable place in /dev/null

Interesting page though. Funny how those kinds of habits sneak in. Thanks for that!

---

### Post by sha1sum on 2013-12-27
New update to my own topic :D  Now I'm studying the use of AWK, and I discovered that in awk you can do it like this:

```

awk '30<=NR && NR<=35' file.txt

```

---

### Post by sha1sum on 2014-01-05
Every time I find a new way to do it, I'm going to update this topic. I found that with awk you can also do it like this:
```
awk 'NR==30,NR==35' file.txt
```
So many possibilities :D

---

### Post by kurum! on 2014-01-07
```

# ruby -ne 'puts $_ if $.>=30 && $.<=35' file

```

---

### Post by kurum! on 2014-01-07
```

ruby -ne 'puts $_ if $.>=30 && $.<=35' file

```

---

