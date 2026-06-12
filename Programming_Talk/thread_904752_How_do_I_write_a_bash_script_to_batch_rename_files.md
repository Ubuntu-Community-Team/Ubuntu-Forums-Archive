---
title: "How do I write a bash script to batch rename files in a directory?"
date: 2008-08-29
forum: Programming Talk
---

### Post by onytz on 2008-08-29
Hello all, 
I have a directory with file names like the following:

img.bc05.ii.1.gif?
img.bc02.456.2.gif?    
img.bc03.569.1.gif?  
img.bc05.iii.1.gif?

I need to trim the last character off of each filename. I know I can use, for example,

mv img.bc05.ii.1.gif? img.bc05.ii.1.gif

But this will take forever. I also know I can write a shell script. It would go something like:

for files in *
do
[something]
done

I just don't know what the [something] would be...
Any suggestions?
Thanks!
onytz

---

### Post by Fixman on 2008-08-29
```

for i in * ; do mv $i `basename $i ?` ; done ;

```

---

### Post by onytz on 2008-08-29
I tried that one, and I get some puzzling (to me) output:

mv: `img.bc.09.46.1.gif' and `img.bc.09.46.1.gif' are the same file

for each iteration.

I also tried:

for i in *.gif?; do mv --verbose $i ${i%\?}; done

the output was:

mv: `img.bc04.470.1.gif\r' and `img.bc04.470.1.gif\r' are the same file

when I simply rename one file with mv, as in:

mv img.bc03.581_3.gif? img.bc03.581_3.gif

and do an ls, I achieve success!?!

Any further suggestions?

---

### Post by Fixman on 2008-08-29
> **onytz said:**
> I tried that one, and I get some puzzling (to me) output:

mv: `img.bc.09.46.1.gif' and `img.bc.09.46.1.gif' are the same file


That means that some files on the folder didn't finish with '?', and that the program did nothing with them. In other words, if you see no more files with '?', it worked perfectly.

---

### Post by onytz on 2008-08-29
Sorry if I've been unclear in my description, I think I can refine the issue now...

In case (1) before I run the one liner, ls gives me, for example,

 **img.bc03.465.1.gif?**

After I run it, I ls gives me the same:

 **img.bc03.465.1.gif?**

In case (2), before I do anything, ls gives me,

 **img.bc03.465.1.gif?**

After I type in:

**mv  img.bc03.465.1.gif?  img.bc03.465.1.gif**

I get:
 **img.bc03.465.1.gif**

(Also, when the filename has the ? at the end, the dir entry doesn't show in color, but after the manual mv in (2), the same entry shows in color...)

---

### Post by onytz on 2008-08-29
OK! got it!

**for i in *.gif?; do mv --verbose -- "$i" ${i%?}; done**

Thanks for your help!!

---

### Post by ghostdog74 on 2008-08-29
> **onytz said:**
> OK! got it!

**for i in *.gif?; do mv --verbose -- "$i" ${i%?}; done**

Thanks for your help!!
you should escape your question mark
```

for i in *.gif\?

```

---

### Post by s_b on 2008-10-02
Does anybody know how to write a cript that prints the values of the following data of the Linux box?

My username : dalux
My homedirectory : /home/dalux
My hostname: localhost. localdomain
My current dir. : /home/dalux/courses
My shell : /bin/bash
My search path : usr/lib/qt-3.3/bin:/usr/kerberos/bin:/usr/local/bin

And all data to the right of the colon shall be read from the enviroment of my Linux box.

---

### Post by iponeverything on 2008-10-02
> **s_b said:**
> Does anybody know how to write a cript that prints the values of the following data of the Linux box?

My username : dalux
My homedirectory : /home/dalux
My hostname: localhost. localdomain
My current dir. : /home/dalux/courses
My shell : /bin/bash
My search path : usr/lib/qt-3.3/bin:/usr/kerberos/bin:/usr/local/bin

And all data to the right of the colon shall be read from the enviroment of my Linux box.


Most of them can be pulled from local environment.  just type "env"

---

