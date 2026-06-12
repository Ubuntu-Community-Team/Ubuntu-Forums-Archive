---
title: "Recursively Rename Files"
date: 2007-09-22
forum: Programming Talk
---

### Post by jerryz on 2007-09-22
Looking for a command line to recursively rename all of my pictures from *.JPG to *.jpg I've figured out I need the find and rename commands but have gotten bogged down in the details. Please help.

---

### Post by bashologist on 2007-09-22
This should work for files recursively, but not going into hidden directories.
```
find <directory> -name '.*' -prune -o -exec rename 's/\.jpg$/\.JPG/i' {} +
```
This will recursively go through every directory including hidden and rename.
```
find <directory> -iname '*.jpg' -exec rename 's/\.jpg$/\.JPG/i' {} +
```
Always test commands on a few files first to make sure. Make sure to specify a directory.

---

### Post by ghostdog74 on 2007-09-22
using xargs instead of -exec would be better.

---

### Post by dwhitney67 on 2007-09-23
> **ghostdog74 said:**
> using xargs instead of -exec would be better.

I've been asked a similar question posed by the OP by my peers, and I have always given them the "long" answer.

'Bashologist' has provided an example that has enlightened me on the usage of the combination of 'wholename', 'iname', and 'rename' using the "find" command.  I'm not sure if it works, but I am willing to give it a try.

You on the other hand have indicated that the usage of 'xargs' is better but have failed to provide an example.  I for one would like to see an example, and more importantly the rationale for why you think it is better.

---

### Post by bashologist on 2007-09-23
Edit: I'll just edit the above post instead of making another.

---

### Post by ghostdog74 on 2007-09-23
> **dwhitney67 said:**
> I
You on the other hand have indicated that the usage of 'xargs' is better but have failed to provide an example.  I for one would like to see an example, and more importantly the rationale for why you think it is better.
i think i do not have to spoon feed you? however, i will give you an explanation since you are too lazy to research.  when you use -exec to say, rm, mv, rename, copy, etc, for each results find  command comes up with ( example 10000 jpgs, ) you run copy, mv, rm etc  10000 times. If you use xargs, it builds up the input into "groups" and run them through the command as few times as possible, thereby speeding things up. you can make a simple test to see what i mean.
```

# time find . -type f -name "*.jpg" -exec ls {} \;
./file10.jpg
./file255.jpg
./file1.jpg
./robin297.jpg
./robin299.jpg
./robin4321.jpg
./robin1.jpg
./file2.jpg

real    0m0.033s
user    0m0.008s
sys     0m0.012s
# time find . -type f -name "*.jpg" | xargs ls
./file1.jpg  ./file10.jpg  ./file2.jpg  ./file255.jpg  ./robin1.jpg  ./robin297.jpg  ./robin299.jpg  ./robin4321.jpg

real    0m0.017s
user    0m0.000s
sys     0m0.004s


```

---

### Post by bashologist on 2007-09-23
> **ghostdog74 said:**
> i think i do not have to spoon feed you? however, i will give you an explanation since you are too lazy to research.  when you use -exec to say, rm, mv, rename, copy, etc, for each results find  command comes up with ( example 10000 jpgs, ) you run copy, mv, rm etc  10000 times. If you use xargs, it builds up the input into "groups" and run them through the command as few times as possible, thereby speeding things up. you can make a simple test to see what i mean.
There's no problem using exec; there's only a problem with how you're using it. Here's an example for you.
```
find ~/ -name '.*' -prune -o -exec echo {} +
```
xargs is actually slower and might not work properly in come cases. If you don't have a solution then you shouldn't even be posting. n_n

---

### Post by ghostdog74 on 2007-09-23
> **bashologist said:**
> There's no problem using exec; there's only a problem with how you're using it. Here's an example for you.
```
find ~/ -name '.*' -prune -o -exec echo {} +
```

Yes, there's no problem using it technically. I am just expressing my views that xargs will be better for OP's problem in terms of performance. And why do you think I would use the example above instead of ls ?
> 
xargs is actually slower and might not work properly in come cases.

you may be right, but once again, you are not on track. 
> 
 If you don't have a solution then you shouldn't even be posting. n_n
My "solution" is a suggestion to  enhance your's, ie to use the xargs in place of exec for OP's problem domain. Please read again post #3if you don't understand.
btw, why don't you try the -exec method on some actual jpgs and compare the results with using xargs and see.?  you might be able to convince me that xargs is indeed slower.

---

### Post by bashologist on 2007-09-24
Here's a test with rename.
```
foo@bar:~$ time find ~/ -name '.*' -prune -o -exec rename -n 's/a/b/' >/dev/null {} +

real    0m0.060s
user    0m0.052s
sys     0m0.008s
foo@bar:~$ time find ~/ -name '.*' -prune -o -print0 | xargs -0 rename -n 's/a/b/' >/dev/null

real    0m0.062s
user    0m0.052s
sys     0m0.016s
foo@bar:~$ 

```
Consistent results are hard to get, sometimes exec faster sometimes xargs. It doesn't matter, exec is fine.

---

