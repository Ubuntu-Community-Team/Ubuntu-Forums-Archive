---
title: "Is this a safe assumption about /proc?"
date: 2010-04-14
forum: Programming Talk
---

### Post by PanP5 on 2010-04-14
I'm writing a program that will display all process ids and names running on a system. I'm going to use dirent.h's scandir() to return all the process "directories" in the /proc folder.

My scandir's selector function is going to look like this:

static int selector (const struct dirent *entry)
{
  //pseudo-code: if entry->d_name[0] is a number, return 1;
  //             else return 0;
}

I'm assuming here that only processes start with a numeral in the /proc directory. Is this a safe assumption?

---

### Post by gmargo on 2010-04-14
See the **proc(5)** man page.

---

### Post by PanP5 on 2010-04-14
> **gmargo said:**
> See the **proc(5)** man page.

Looks like it is. Thanks!

---

