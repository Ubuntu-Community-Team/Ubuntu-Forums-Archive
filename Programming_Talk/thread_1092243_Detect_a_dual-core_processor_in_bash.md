---
title: "Detect a dual-core processor in bash"
date: 2009-03-10
forum: Programming Talk
---

### Post by scifo_dk on 2009-03-10
Hi Guys.

Is there a way to detect if a computer has a singlecore og multicore processor with bash script?

I need it for an if-statement. So if the pc has a dualcore processor, is has to do something, otherwise it should skip it.

Thank you in advance for your help.

Kind regards
// Scifo

---

### Post by tribaal on 2009-03-10
Well the following counts the number of cores (logical processors) on your system:

```
cat /proc/cpuinfo | grep processor | wc -l
```

So if you only need to know if the machine has 2 cores or more (if it's multicore) you can test against this:

```
NUM_CORES=$(cat /proc/cpuinfo | grep processor | wc -l)
if [ $NUM_CORES -lt 2 ] ; then
# single core
else
#multi core
fi

```

There are probably plenty of other ways to find that out, it's just the first one on top of my head :)

**EDIT:** Yet another way if you're sure your machine has only one physical CPU:
 ```
cat /proc/cpuinfo | grep cpu\ cores | head -1 | awk '{print $4}'
```

Hope this helps!

- Trib'

---

### Post by scifo_dk on 2009-03-10
Well, I don't know anything about the computer which will be running the script. So woun't the first snippit be the best one to use?

---

### Post by tribaal on 2009-03-10
Well I guess it depends exactly what you're trying to achieve:

The first snippet gives you how many logical processors the machine has - probably that's what you want to know...
I could immagine if you want to set a maximum number of processes depending on the number of available cores (say, to compile faster), this would be it.

On the other hand, if you want to gather statistics of some kind, you might also be interested in knowing how many physical CPUs the machine has... Or the number of cores per physical CPU. It really depends what you are trying to achieve.

Hope this helps

- Trib'

---

### Post by scifo_dk on 2009-03-10
Well, I want it to change a variable to make it load startup-scripts with both kernels, but it should ofcause only do that, if the pc has a dual-core processor.

This is the code I want to execute:
sudo sed -i 's/^CONCURRENCY=none/CONCURRENCY=shell/' /etc/init.d/rc

---

### Post by tribaal on 2009-03-10
Ah yeah then the first snippet is what you want - you don't really care how many cores above one you have: it's either one or more.

- Trib'

---

### Post by scifo_dk on 2009-03-10
Great!

Ty alot for your help mate. :)

//Scifo

---

### Post by ghostdog74 on 2009-03-10
> **tribaal said:**
> physical CPU:
 ```
cat /proc/cpuinfo | grep cpu\ cores | head -1 | awk '{print $4}'
```

Just awk will do.
```

awk -F":" '/cpu cores/{print $2;exit}' /proc/cpuinfo

```

---

### Post by tribaal on 2009-03-10
Yeah I tend to under use awk ;)

I'll try to loose that suboptimal habit.
Thanks a lot for pointing this out!

- Trib'

---

