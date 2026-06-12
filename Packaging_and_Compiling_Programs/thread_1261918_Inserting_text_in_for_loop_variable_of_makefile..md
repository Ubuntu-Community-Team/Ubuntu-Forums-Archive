---
title: "Inserting text in for loop variable of makefile."
date: 2009-09-09
forum: Packaging and Compiling Programs
---

### Post by himanshu18july on 2009-09-09
Hi All,

I'm facing a problem with the for loop variable of makefile.

I want to insert some text at the end of each variable in a list.
For example, I have a list as "first second third" and I want to insert "_july" in all the variables of the list so that list becomes "first_july second_july third_july" and print it in some file.
Now the code I'm using for this is

```

LIST = first second third
    for i in $(LIST); do \
    echo "$$i_july" >> test.txt; \
    done

```

But this piece of code is not working.

Can you people please suggest me the modification required.

Thanks in advance.

---

### Post by korin43 on 2009-09-11
You're putting the variable in in a sort of insane way. I'm not sure of the syntax of makefiles, but just add the two variables together:
```
LIST = first second third
    for i in $(LIST); do \
    echo "$i$_july" >> test.txt; \
    done
```
or
```
LIST = first second third
    for i in $(LIST); do \
    echo $i + $_july >> test.txt; \
    done
```
or if that doesn't work

```
LIST = first second third
    for i in $(LIST); do \
    echo $i >> test.txt \
    echo $_july >> test.txt; \
    done
```

---

