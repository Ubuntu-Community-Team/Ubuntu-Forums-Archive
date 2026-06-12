---
title: "Get author name of files / folders"
date: 2011-05-23
forum: Programming Talk
---

### Post by zobayer1 on 2011-05-23
I am trying to implement "ls" program in C/C++ and wondering how to reflect "--author" option. I have to include the author name of the file when using it with "-l" option. I searched for it but didn't find anything much helpful. Is this always be the same with current user name (I think not necessarily) which could be easily determined. What should I do or look into?

Thanks.

[edit]
For all the cases I have tested with standard "ls -l --author", I found that, the user name, group name and author name fields are always same for a specific file. Is it so?
[/edit]

---

### Post by roccivic on 2011-05-23
Well the user may not be necessarily the same as the group. A user 'foo' may be easily in group 'bar' or even 'root'.

A small snippet from my terminal to illustrate the point:
```
roccivic@roccivic-pc:~$ mkdir foo
roccivic@roccivic-pc:~$ cd foo
roccivic@roccivic-pc:~/foo$ echo abd > file
roccivic@roccivic-pc:~/foo$ ls -l
total 12
-rw-r--r-- 1 roccivic roccivic 4 2011-05-24 00:22 file
roccivic@roccivic-pc:~/foo$ sudo chown roccivic:root file
[sudo] password for roccivic: 
roccivic@roccivic-pc:~/foo$ ls -l
total 12
-rw-r--r-- 1 roccivic root 4 2011-05-24 00:22 file
roccivic@roccivic-pc:~/foo$ 

```

---

### Post by zobayer1 on 2011-06-02
Yes, I've also discovered that later as well, but what can I do?

---

### Post by zobayer1 on 2011-06-12
Sorry to bump, but any idea? anyone? Thanks... :popcorn:

---

### Post by cgroza on 2011-06-12
Take a look at the ls source code. It may help you. It is in the coreutils package.

---

### Post by TwoEars on 2011-06-12
Take a look at this -> [http://www.gnu.org/s/hello/manual/libc/Attribute-Meanings.html](http://www.gnu.org/s/hello/manual/libc/Attribute-Meanings.html)

---

### Post by zobayer1 on 2011-06-19
still no luck :(

---

### Post by zobayer1 on 2011-06-19
Finally, digging through the ls source code I've found that, but got disappointed to see what that does :(

line #3000
```

if (print_author)
    p += format_user (p, f->stat.st_author);

```......
line #2904
```

format_user (char *buffer, uid_t u)
{
  char const *name = (numeric_ids ? NULL : getuser (u));
  if (name)
    sprintf (buffer, "%-8s ", name);
  else
    sprintf (buffer, "%-8lu ", (unsigned long) u);
  return strlen (buffer);
}
```I wasted much time wondering where it comes from :popcorn:

---

