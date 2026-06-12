---
title: "Calling system functions from C++"
date: 2009-12-03
forum: Programming Talk
---

### Post by MunkyJunky on 2009-12-03
I'm new to developing programs for Ubuntu, so I'm a little lost on where to start. I Googled the topic, but found nothing useful, which makes me think I'm looking for the wrong thing.

I'm trying to make a little tool in C++ that mounts/unmounts a network drive, and displays a notification. I know it would be easier to make a bash script to do it (I'm in fact converting my bash to C++), but it's more for the learning experience than anything. 

I want to be able to call the **mount** command and **notify-send** from a C++ script. I figure I have to include some libraries, but I have no idea what. 

Any help would be appreciated.

---

### Post by johnl on 2009-12-03
For mount, check **man 2 mount**.  If you don't have manpages-dev installed, do that first. 

```

MOUNT(2)                   Linux Programmer's Manual                  MOUNT(2)

NAME
       mount - mount file system

SYNOPSIS
       #include <sys/mount.h>

       int mount(const char *source, const char *target,
                 const char *filesystemtype, unsigned long mountflags,
                 const void *data);

DESCRIPTION
       mount()  attaches the file system specified by source (which is often a
       device name, but can also be a directory name or a dummy) to the direc
       tory specified by target.

```
To send a notification, you would need to use dbus to send a message to notify-osd.  You can use **libdbus** to do this, although I don't have any clue how :).

---

### Post by Can+~ on 2009-12-03
> **johnl said:**
> To send a notification, you would need to use dbus to send a message to notify-osd.  You can use **libdbus** to do this, although I don't have any clue how :).

Or use [libnotify API]("http://library.gnome.org/devel/libnotify/0.4/") (It's a gnome doc, so you should see the html version on Devhelp).

---

### Post by MunkyJunky on 2009-12-03
Thanks, that's got me on my way. Thanks for the help!

---

### Post by endBc on 2009-12-03
```
#include <stdlib.h>

int main(int argc, char *argv[])
{
    system("mount something somewhere");
    system("notify-send message");

    return 0;
}

```

---

### Post by nvteighen on 2009-12-03
> **endBc said:**
> ```
#include <stdlib.h>

int main(int argc, char *argv[])
{
    system("mount something somewhere");
    system("notify-send message");

    return 0;
}

```

It's usually much better to rely on libraries, when possible, than on shell calls like those. Libraries don't make it necessary to install a new application or checking whether the user has the permissions to execute that application.

---

