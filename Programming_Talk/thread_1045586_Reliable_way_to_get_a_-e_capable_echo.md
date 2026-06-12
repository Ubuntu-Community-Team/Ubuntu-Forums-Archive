---
title: "Reliable way to get a -e capable echo"
date: 2009-01-20
forum: Programming Talk
---

### Post by Cracauer on 2009-01-20
Mumble.

In bourne (not bash) shellscripts, what do you do to get an "echo" that is known to support "-e".

If you use /bin/sh's internal echo, then Ubuntu doesn't support -e.

If you use /bin/echo, FreeBSD doesn't support -e.

Calling 
bash -c "echo -en ..."
is expensive and is prone to quote errors on the actual string (remember it will have backslash sequences in it).

Any better solution?

---

### Post by Cracauer on 2009-01-20
Woah, Ubuntu's /bin/sh is actually really broken. It does the "-e" escaping by default but doesn't eat up the -e.  Try this on a couple OSes:
```

#! /bin/sh

echo -e '\nfoo\nend'
/bin/echo -e '\nfoo\nend'

```

(Ubbcode eats the leading newline in the example below)

Debian, Redhat-7.3, FC3:
```


foo
end

foo
end

```

FreeBSD:
```


foo
end
-e \nfoo\nend

```

Ubuntu:
```

-e 
foo
end

foo
end

```

This is all "correct", if annoying, except for Ubuntu. What shell are they using by default, again?

---

### Post by stylishpants on 2009-01-20
Ubuntu's /bin/sh is actually dash by default, for the last few releases.


It's actually dash's behaviour, not bash's, which is correct according to the POSIX standard.  

For portability and more generally consistent behaviour, use printf instead of echo.

---

### Post by Cracauer on 2009-01-20
Hm. Yeah, now I remember.

Posix in their wisdom decided that "-e" behavior is now the default and since the "-e" switch isn't supported it isn't omitted from the output either. And doesn't cause a usage() error either just to ensure that code can't possibly work or be debuggable easily.

printf is fine but it's a full-blown dynamically linked binary that you fork and exec every single time.

---

### Post by Krupski on 2009-01-23
> **stylishpants said:**
> Ubuntu's /bin/sh is actually dash by default, for the last few releases.


It's actually dash's behaviour, not bash's, which is correct according to the POSIX standard.  

For portability and more generally consistent behaviour, use printf instead of echo.

Slightly off topic (I think) but quick Q:

I changed the symlink for "sh" from "dash" to "bash" on my system (with the idea that I want bash to run everything sent to sh).

Did I do wrong and/or something non-compliant?

Thanks!

-- Roger

---

### Post by Cracauer on 2009-01-23
> **Krupski said:**
> Slightly off topic (I think) but quick Q:

I changed the symlink for "sh" from "dash" to "bash" on my system (with the idea that I want bash to run everything sent to sh).

Did I do wrong and/or something non-compliant?

Thanks!

-- Roger

There might be scripts that now echo some stray "-e" around. Whether that happens or not is a good question and if it happens whether it's cosmetic or whether the output is used for something real another good question.

Hopefully all Ubuntu startup scripts are written in a portable manner.

---

### Post by ghostdog74 on 2009-01-23
the best is to use printf instead of echo.

---

### Post by bruce89 on 2009-01-23
Just change the shabang to

```
#!/bin/bash
```

Technially, if you require bash, you should do this.

---

