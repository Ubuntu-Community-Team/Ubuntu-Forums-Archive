---
title: "[SOLVED] Dilemma, file paths and servers."
date: 2008-10-01
forum: New to Ubuntu
---

### Post by fgn89 on 2008-10-01
Well.. I'm just merging all my problems/questions into one thread.

This is my situation right now.

I've just migrated my database server, from windows, to Ubuntu.

I've installed the firebird service, on my Ubuntu server.

And confirmed it works, through the use of FlameRobin. **The database I copied from windows to Ubuntu is accessible.**

But the problem is.. it only works, when I access it, from the server itself.

It doesn't work, through the use of Samba and a shared folder.

Through extensive testing in a windows platform, I've found out.

That the file path, 

```
192.168.0.3:D:\database\test.gdb
```

would work.

But the file path, assuming database is the shared folder.

```
\\192.168.0.3\database\test.gdb
```

would not.

After asking around, I've found out, that the file structure in Linux is not quite the same.

I'm just wondering if there's any way to access the file, in a similarly structured file path?

so far..

I've tested these file paths, which don't work.

```
192.168.0.3:/home/fgn89/Documents/database/TEST.GDB

smb://192.168.0.3/database/TEST.GDB

```

My dad insists, my installation of the Linux is the problem, but I don't really think so. If anyone knows whether a server version installation would make a difference, please let me know?

Thanks, any help is much appreciated.

This thing has me stumped for several days already.

---

### Post by Joeb454 on 2008-10-01
Have you configured samba to share the directory of the database over your network?

If not then that could be your problem, I recommend you search for one of the many guides available to configuring samba on an Ubuntu Server :)

---

### Post by aeiah on 2008-10-01
it seems samba isnt set up correctly. in windows, mapping a network drive to \\sambaserver\file\path\ should work, given that you have set up samba permissions correctly on your server. i havent got a lot of experience with samba, but there are loads of howtos and documentation on the internet.

---

### Post by fgn89 on 2008-10-01
I'm relatively sure my samba setup is working correctly.

The file path works correctly, if I access it as any other share folder. 

Just not when I'm accessing it using database managers, e.g. EMS, SQL Explorer, BDE, etc.

I think it has something to do with the path.

As mentioned, there're 2 ways to access a path in windows.

```
\\192.168.0.3\database\test.gdb
```

or

```
192.168.0.3:D:\database\test.gdb
```

The latter works, but the former doesn't, I'm suspecting that's the case in here too.

I'm just wondering if there's any alternative file path, instead of using, the first.

```
\\192.168.0.3\database\test.gdb
```

Someone mentioned 

```
192.168.0.3:/home/fgn89/Documents/database/test.gdb
```

But that doesn't work in windows?

Hope that's clear enough.

---

