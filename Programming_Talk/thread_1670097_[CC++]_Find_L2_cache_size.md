---
title: "[C/C++] Find L2 cache size"
date: 2011-01-18
forum: Programming Talk
---

### Post by Taak on 2011-01-18
Is there a way to find under a UNIX system, using C++, the size of the L2 cache? 
 
I found this: [http://stackoverflow.com/questions/1922249/c-cache-aware-programming](http://stackoverflow.com/questions/1922249/c-cache-aware-programming)
 
Do you know a safer/alternative way?
 
Any suggestions?
 
Thank you

---

### Post by psusi on 2011-01-18
That would be hardware specific and thus outside the scope of standards like C/C++ and POSIX.

For common desktop Intel/AMD CPUs take a look at the CPUID hardware instruction.

---

### Post by soltanis on 2011-01-18
This probably only works under a Linux system only, as it uses information out of proc. If you check:

```

grep 'cache size' /proc/cpuinfo | cut -d ":" -f 2

```

This will give you the cache size of all your processors (for example, mine is apparently 8192 KB).

In C you can open this file and read the data from it:

```

int cache_size_kb(void)
{
    char line[512], buffer[32];
    int column;
    FILE *cpuinfo;

    if (!(cpuinfo = fopen("/proc/cpuinfo", "r"))) {
        perror("/proc/cpuinfo: fopen");
        return -1;
    }

    while (fgets(line, sizeof(line), cpuinfo)) {
        if (strstr(line, "cache size")) {
            column = strstr(line, ":");
            strncpy(buffer, line + column + 1, sizeof(buffer));
            fclose(cpuinfo);
            return (int)strtol(buffer, NULL, 10);
        }
    }
    fclose(cpuinfo);
    return -1;
}

```

This code only returns the cache size of the first processor it encounters, and assumes that it's in kilobytes (and does other bad things like not check to make sure the string it reads is a number and casts a long int to an int), but it's just an example. You can add checks to make it more robust.

---

### Post by Taak on 2011-01-19
That's good. Thank you.
 
Do main linux projects use /proc/cpuinfo? Ubuntu, Fedora, Gentoo?
 
And when do they estimate the cache size? Only when the OS is installed or every boot?

---

### Post by Taak on 2011-01-19
*Double post, sorry.*

---

### Post by psusi on 2011-01-19
> **Taak said:**
> That's good. Thank you.
 
Do main linux projects use /proc/cpuinfo? Ubuntu, Fedora, Gentoo?
 
And when do they estimate the cache size? Only when the OS is installed or every boot?

/proc is information pulled out of the running kernel, not files stored on disk.

---

### Post by MadCow108 on 2011-01-19
```
sysconf(_SC_LEVEL2_CACHE_SIZE)
```

but thats probably not very portable (its not even documented).

---

### Post by MadCow108 on 2011-01-19
```
sysconf(_SC_LEVEL2_CACHE_SIZE)
```

but thats probably not very portable (its not even documented).

---

### Post by soltanis on 2011-01-19
> **psusi said:**
> /proc is information pulled out of the running kernel, not files stored on disk.

To clarify, /proc is a pseudo-filesystem intended to create a file like interface for querying and modifying running processes (hence "proc"). It has a helpful [Wikipedia page]("https://secure.wikimedia.org/wikipedia/en/wiki/Proc_filesystem") that details what it's useful for and which systems support it. The original idea probably came out of Plan 9 from Bell Labs, an operating system that extended the UNIX concept of "everything is a file" as much as possible to include this kind of functionality.

---

