---
title: "thread-safe conversion from int to char* C"
date: 2009-03-13
forum: Programming Talk
---

### Post by mdecler2 on 2009-03-13
I need to convert an integer into a string, but as far as I know, sprintf is not thread safe.

Help?

---

### Post by monkeyking on 2009-03-13
Do you want char* or string?

---

### Post by WW on 2009-03-13
In plain old C, a 'string' *is* char*.

---

### Post by dyfet on 2009-03-13
> **mdecler2 said:**
> I need to convert an integer into a string, but as far as I know, sprintf is not thread safe.

Help?

The problem is not that sprintf is not thread-safe, but rather that the size of the destination is not specified, and hence if the allocated or static string buffer used to receive the value is smaller than the actual output, it will overflow the allocated space.  For this reason, one should use snprintf.  What you would like to do is perhaps something like:

char string[10];
int myint = ??

snprintf(string, sizeof(string), "%d", myint);

---

### Post by mdecler2 on 2009-03-14
Great! Thanks for the info. I consider this solved.

---

### Post by supirman on 2009-03-15
If you don't want to pre-allocate a fixed size char array, use **asprintf**.  asprintf will allocate memory of the required size for you.  Of course, you'll have to free() it later.

---

### Post by Krupski on 2009-03-15
> **dyfet said:**
> The problem is not that sprintf is not thread-safe, but rather that the size of the destination is not specified, and hence if the allocated or static string buffer used to receive the value is smaller than the actual output, it will overflow the allocated space.  For this reason, one should use snprintf.  What you would like to do is perhaps something like:

char string[10];
int myint = ??

snprintf(string, sizeof(string), "%d", myint);

If I have something like this:

```

    char buffer[BUFSIZ];
    int cores;
    sprintf(buffer, "/sys/devices/system/cpu/cpu%d/cpufreq/cpuinfo_cur_freq", cores);

```

Isn't that safe because "buffer" is "BUFSIZ" long (8192 bytes in this case)?

The worlds longest int couldn't possibly overflow buffer[].

Or, is the SOURCE string "operated on" before the sprintf "copy" takes place?

-- Roger

---

