---
title: "Bash scripting help - capture variable"
date: 2007-06-04
forum: Programming Talk
---

### Post by crichell on 2007-06-04
Hi everyone,

I have a simple Python script that I need to change to bash.  (Working environment is restricted to bash).  Here is the python code with the variables I want to extract:

```

# Determine amount of memory
a = os.popen('cat /proc/meminfo | grep MemTotal:')
try:
    total_memory = a.readline().strip()
finally:
    a.close()
memory = int(total_memory[15:22])
swap = memory*2

# Determine remaining space in VG
b = os.popen('vgdisplay | grep Free')
try:
    space = b.readline().strip()
finally:
    b.close()
vg_space = int(space[21:28])
vg_mb_space = vg_space*4
```

I'm not well versed in bash scripting or sed.  Thanks for any help.

---

### Post by ghostdog74 on 2007-06-04
example one:
```

memory=$(cat /proc/meminfo  |awk '/MemTotal/{print $2}')
swap=$((memory * 2))
echo $swap
## you will have to do the rest using similar , i  don't have vgdisplay command

```

example two:
```

cat /proc/meminfo  |awk '/MemTotal/{
                                 print "Total memory: " $2
                                 print "Swap: " $2 * 2
                         }'
vgdisplay | awk '/Free/ {
                                print "You will have to complete this yourself"
}

```

---

### Post by crichell on 2007-06-04
Thanks  ghostdog74,  that will get me rolling.

Cheers, Carl

---

