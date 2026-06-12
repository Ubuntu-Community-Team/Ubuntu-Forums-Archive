---
title: "programmatically detect ubuntu operating system"
date: 2010-02-02
forum: Programming Talk
---

### Post by dmlb2000 on 2010-02-02
I was wondering how to detect ubuntu is the OS environment I am running in and what version is it (numeric and by name if possible).

So in RedHat based systems usually the standard is to parse out /etc/redhat-release and for debian they have /etc/debian_version and ubuntu systems have /etc/debian_version but it doesn't reflect the ubuntu version of the system.

Is there a dpkg-* command I can use to get if I'm ubuntu or debian? is there a file I can read to determine what version of ubuntu I'm in?

I'd like to be able to do this for debugging purposed of the application that way I know exactly what environment to setup for the application to start debugging.

I was trying to look through how ubuntu-bug pulls the version information but I'm not sure its actually pulling the version from the OS.

---

### Post by dmlb2000 on 2010-02-02
Oh, also should add that /etc/issue doesn't count. That file is changed (along with /etc/issue.net) by policy for the client (happens to be US DOE) with a standard banner. So I wouldn't count on relying on that file to parse out the version. 

Still looking into the automatic ubuntu-bug creation stuff, it seems to get that information from somewhere.

---

### Post by Meghnaad on 2010-02-02
I am not sure but may be this will help:

Command:

```
cat /proc/version
```

With Output:

```
vinsys@vinsys-server:~/Meghnaad$ cat /proc/version
Linux version 2.6.31-17-generic (buildd@palmer) (gcc version 4.4.1 (Ubuntu 4.4.1-4ubuntu8) ) #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009
```


Edit:

See "daasdingo's" Solution below It's THE CORRECT SOLUTION !

---

### Post by dmlb2000 on 2010-02-02
That's more the kernel version and can be changed rebuilt to whatever I want, could even install a redhat kernel on an ubuntu system and it will boot and run. I'll be collecting that information too but would like to know that the userspace is ubuntu karmic or intrepid or whatever.

---

### Post by daasdingo on 2010-02-02
look into lsb_release
eg
```

daasdingo@daasdingo-laptop:~$ lsb_release -c
Codename:    karmic

```

---

### Post by lisati on 2010-02-02
Edit: Beaten to it by daasdingo

---

### Post by dmlb2000 on 2010-02-02
Thanks, that's it both python bindings and cat /etc/lsb-release. Is it okay to source /etc/lsb-release to get that information into a shell script? or is that not quite supported?

---

