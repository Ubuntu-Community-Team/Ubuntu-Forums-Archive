---
title: "Creating a patch"
date: 2009-04-23
forum: Programming Talk
---

### Post by shahin on 2009-04-23
Greetings-
   I need to create a patch, and I following the this url:
[http://www.snort.org/archive-7-7264.html](http://www.snort.org/archive-7-7264.html)
The very last post talks about creating a patch, but I get an error message.  Here is the patch:
```

# diff -ubB spo_database.c.orig spo_database.c
--- spo_database.c.orig 2009-04-13 16:03:49.000000000 +0200
+++ spo_database.c 2009-04-13 15:59:53.000000000 +0200
@@ -2798,6 +2798,14 @@
{
result = atoi(data->m_row[0]);
}
+ else
+ {
+ result = 0;
+ }
+ }
+ else
+ {
+ result = 0;
}
}
mysql_free_result(data->m_result);

```

Here is the instructions:

"So place the above text into the file named spopatch.patch (in the same dir as spo_database.c)

next issue this command:

patch < spopatch.patch

This will patch your spo_database.c file so that sql queries will work in base (now base will contain result data)"

I know I am showing that I know very little about how patching works. So if there is any tutorials, I appreciate if you could share with me.  But in interest of time, if you know how to remedy this, please advise.

---

### Post by Arndt on 2009-04-24
> **shahin said:**
> Greetings-
   I need to create a patch, and I following the this url:
[http://www.snort.org/archive-7-7264.html](http://www.snort.org/archive-7-7264.html)
The very last post talks about creating a patch, but I get an error message.  Here is the patch:
```

# diff -ubB spo_database.c.orig spo_database.c
--- spo_database.c.orig 2009-04-13 16:03:49.000000000 +0200
+++ spo_database.c 2009-04-13 15:59:53.000000000 +0200
@@ -2798,6 +2798,14 @@
{
result = atoi(data->m_row[0]);
}
+ else
+ {
+ result = 0;
+ }
+ }
+ else
+ {
+ result = 0;
}
}
mysql_free_result(data->m_result);

```

Here is the instructions:

"So place the above text into the file named spopatch.patch (in the same dir as spo_database.c)

next issue this command:

patch < spopatch.patch

This will patch your spo_database.c file so that sql queries will work in base (now base will contain result data)"

I know I am showing that I know very little about how patching works. So if there is any tutorials, I appreciate if you could share with me.  But in interest of time, if you know how to remedy this, please advise.

But what is the error message?

---

### Post by shahin on 2009-04-24
Sorry about that.  I should have posted the error message.  Here it is:
```

root@thunder:/usr/local/src/snort-2.8.3.2/src/output-plugins# patch < spopatch.patch
patching file spo_database.c
patch: **** malformed patch at line 5: {

```

Basically at the first bracket.  I tried removing these lines:
```
# diff -ubB spo_database.c.orig spo_database.c
--- spo_database.c.orig 2009-04-13 16:03:49.000000000 +0200
+++ spo_database.c 2009-04-13 15:59:53.000000000 +0200
@@ -2798,6 +2798,14 @@ 

```
But I get a different error message.  I do not know the syntax for patch codes.  I do not know what is specific to what the original author posted, and what I need in my patch.

---

### Post by Arndt on 2009-04-25
> **shahin said:**
> Sorry about that.  I should have posted the error message.  Here it is:
```

root@thunder:/usr/local/src/snort-2.8.3.2/src/output-plugins# patch < spopatch.patch
patching file spo_database.c
patch: **** malformed patch at line 5: {

```

Basically at the first bracket.  I tried removing these lines:
```
# diff -ubB spo_database.c.orig spo_database.c
--- spo_database.c.orig 2009-04-13 16:03:49.000000000 +0200
+++ spo_database.c 2009-04-13 15:59:53.000000000 +0200
@@ -2798,6 +2798,14 @@ 

```
But I get a different error message.  I do not know the syntax for patch codes.  I do not know what is specific to what the original author posted, and what I need in my patch.

I have had such problems with 'patch' at times, and not been able to resolve them, so I'm not an expert. It's probably something basic.

However, if the patch is just what you showed, you can apply it by hand: you see the line numbers, the old code and the code to replace it.

---

