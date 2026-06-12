---
title: "regular expr help"
date: 2006-07-19
forum: Programming Talk
---

### Post by Peter76 on 2006-07-19
Hi, I'm trying to convert the following file name:

The Doors - 20 - The Palace Of Exile.mp3

to:

The_Doors_20_The_Palace_Of_Exile.mp3

I can do this now in 3 steps:

#1 for i in *.mp3; do mv "$i" `echo $i | tr ' ' '_'`; done
#2 for i in *.mp3; do mv "$i" `echo $i | tr '-' '_'`; done  
#3 for i in *.mp3; do mv "$i" `echo $i | tr -s '_'`; done

Now this is probably possible with one command... Anyone know how to do this?

---

### Post by toojays on 2006-07-19
Well, it's arguably still three commands, but it's only one move:```

for i in *.mp3; do mv "$i" $(echo "$i" | sed -e 's/[-_ ]\+/_/g'); done
```

The sed expression means "swap any sequence of one or more hyphen or underscore or space characters with an underscore".

Edit: had to modify the regex a couple of times to get it right; for some reason the location of the space in the character class is important.

---

