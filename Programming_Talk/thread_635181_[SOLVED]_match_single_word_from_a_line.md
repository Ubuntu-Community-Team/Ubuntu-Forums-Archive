---
title: "[SOLVED] match single word from a line"
date: 2007-12-08
forum: Programming Talk
---

### Post by mridkash on 2007-12-08
Hi, I want to count how many hours I spend on computer in a day. 
For that I need to store the uptime value (/proc/uptime) to some file.
The problem is, /proc/uptime contains 2 numbers in a single line like, 16712.70 12775.80 where the first number is what i want to output.
I've tried grep, but it outputs the whole line instead of just 1 number.
Please tell me how to do it.

---

### Post by geirha on 2007-12-08
there are many ways to do it. Here's one:
```
cut -d' ' -f1 /proc/uptime
```

And one using grep:
```
grep -o '^[0-9.]\+' /proc/uptime
```

---

### Post by pmasiar on 2007-12-08
[php]
# Python to the rescue
for line in open('/proc/uptime'):
    num1, num2 = line.split()
    # here you are
[/php]

---

### Post by ghostdog74 on 2007-12-08
```

# awk '{print $1}' /proc/uptime

```
or
```

# set -- $(cat /proc/uptime)
# echo $1

```
or if you are a Python fan
```

# result=$(python -c "print open('/proc/uptime').read().split()[0]")
# echo $result

```

---

### Post by mridkash on 2007-12-08
Thanks guys, I knew that would be simple.

---

