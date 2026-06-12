---
title: "bash scripting question."
date: 2008-09-19
forum: Programming Talk
---

### Post by jbsimon000 on 2008-09-19
Hi, I hope this is a correct forum for this question.

I have a series of bash scripts that periodically run a software build. 

At the end of the build process I get 2 files, one is the log file "build_1.22.log" and the other is the build directory "build1.22"

After each build (if something changes, there is a new set of these files "build1.23.log", "build1.23", etc.

So, when the build runs, I have in script variables the name of the files that I am currently building. What i would like to do when the build succeeds (My script knows if the build passed or not) is delete any old builds that might exist EXCEPT the one I just did... something like
rm build* --except ${BUILD_LOG} ${BUILD}

I looked and don't see any exclude type option on rm, so I assume i need to make my script do the work.

Any ideas as to how to achieve this ?

Thanks !
Joe

---

### Post by ghostdog74 on 2008-09-19
turn on extglob
```

# shopt -s extglob
# var=build1.23.log
# rm !($var)

```

---

### Post by jbsimon000 on 2008-09-23
Thanks,

that works great, and just the way I like it, not alot of scripting ! :)

Thanks !
Joe

---

