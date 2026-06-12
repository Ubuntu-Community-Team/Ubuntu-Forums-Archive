---
title: "Quick makefile question - default included header files"
date: 2010-02-10
forum: Programming Talk
---

### Post by jii on 2010-02-10
I'm using make with gcc on an ARM. I have a header file that I want included in every single compiled C and C++ file (it has common types and things), and I don't want all the developers to actually have to type in #include "Types.h" into each c/cpp file. I want the makefile to automatically include it for me while it compiles each file. I worked on a Wii game where the makefile did this for me, but I don't remember how it was done.

I asked my friend Google how to do it, and when he couldn't spent some time searching online with no luck, and once I hit 30 mins, I decided it was time to post. Sorry if the answer is really easy or something. I don't know very much about make.

---

### Post by night_fox on 2010-02-11
This probably isn't the answer you were looking for, but you could have your makefile run a script for each source file to concatenate the header and the file, then compile, i.e.

for I in $(SRC)
do
cat $INC $I > tmp-$I
gcc $(CFLAGS) ... tmp-$i ...
rm $tmp-$i
done

---

### Post by dwhitney67 on 2010-02-11
jii... there is no way to accomplish what you want with GCC, unless you do something hokey like night_fox recommended.

---

### Post by jii on 2010-02-11
Hey night_fox, great idea. I'll try it. Thanks!

If hokey means to write a simple and useful script to automate something for you, then I'm all for it.

---

### Post by Vox754 on 2010-02-11
> **dwhitney67 said:**
> jii... there is no way to accomplish what you want with GCC, unless you do something hokey like night_fox recommended.

I almost vomited my breakfast in surprise!

According to GCC's manual:
```

-include file
           Process file as if "#include "file"" appeared as the first line of
           the primary source file.  However, the first directory searched for
           file is the preprocessor's working directory instead of the
           directory containing the main source file.  If not found there, it
           is searched for in the remainder of the "#include "..."" search
           chain as normal.

           If multiple -include options are given, the files are included in
           the order they appear on the command line.


```

I thought dwhitney knew everything there is to know about C and C++. I'm baffled.

---

### Post by dwhitney67 on 2010-02-11
> **Vox754 said:**
> 
I thought dwhitney knew everything there is to know about C and C++. I'm baffled.

No, I don't know everything.  But what you found actually works!  I learned something today.  Now to go back to play with the snow.

---

### Post by jii on 2010-02-11
Lol, who would think to check the manual? 

So here's what I added to my makefile:

```

# Automatically include header files for common types, etc
CFLAGS += 	-include "Types.h"
CPPFLAGS +=	-include "Types.h"

```

Thanks Vox754, you're the best!

---

