---
title: "Help cleaning up code"
date: 2012-11-17
forum: Programming Talk
---

### Post by MadsRC on 2012-11-17
I wanted to start programming, and decided to pick up on Python.

One day a colleaque of mine was talking about how nice it would be to be able to check against RBL lists for our webserver, which I then decided to solve with a python script.

I've finally finished it and it works. But I got a feeling that it could be done better, as I'm still extremely new.

It's written as a script, and I'm currently researching how to compile and making .debs, but that's a whole other topic.

Now, the actual code is over at [http://github.com/MadsRC/dnsbls](http://github.com/MadsRC/dnsbls)

does anybody have any comments as to the code? Any better way to achieve what the script/programme already does?

---

### Post by Vaphell on 2012-11-17
first thing that caughts the eye is the hardcoded list inside your code. Move the list to external file and make the program load it into dict.

something like

```
listfile = open("list.txt", "r")
L = []
for elem in listfile:
  L.append( elem.strip() )
listfile.close()
```

---

### Post by MadsRC on 2012-11-17
Thank you!

I did think of that (Couldn't find a way to do it) but decieded to not research it too much, as I'd have 2 files then. Being a script that wasn't really an option, but If I compile it, then I guess that's a better way to do it.

---

### Post by KdotJ on 2012-11-17
> **MadsRC said:**
> Thank you!

I did think of that (Couldn't find a way to do it) but decieded to not research it too much, as I'd have 2 files then. Being a script that wasn't really an option, but If I compile it, then I guess that's a better way to do it.

Not really sure what you mean by this?

You would still have two files... as the idea is the data file is external from the code.

---

