---
title: "BASH substition -- no workee?"
date: 2009-03-30
forum: Programming Talk
---

### Post by lykwydchykyn on 2009-03-30
According to everything I've read, this:
```

echo ${hotdog/dog/foot}

```
...should output the word "hotfoot".
But it outputs nothing on my machine.

and any of these:
```

echo ${hot.dog/dog/foot}
echo ${"hot.dog"/dog/foot}
echo ${hot.dog%dog}foot

```
Should output "hot.foot".  But all I ever get is a "bad substitution" error.

Some things I've read suggest this happens if you're using dash or sh instead of bash, but "echo $0" returns /bin/bash, which is not a symlink to anything.

Am I missing something here?

---

### Post by ghostdog74 on 2009-03-30
you have to declare the variable first
```

# var="hotdog"
# echo ${var/dog/foot}
hotfoot


```

---

### Post by lykwydchykyn on 2009-03-30
Ah yes, that works, thanks!

---

