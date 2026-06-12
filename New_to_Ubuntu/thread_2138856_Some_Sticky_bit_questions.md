---
title: "Some Sticky bit questions"
date: 2013-04-25
forum: New to Ubuntu
---

### Post by clearski on 2013-04-25
**Step one:**

```
mkdir TESTING2
ls -l TESTING2
drwxrwxr-x  2 usr grp       4096 Apr 25 18:28 TESTING2
chmod +t TESTING2
ls -l TESTING2
drwxrwxr-t  2 usr grp       4096 Apr 25 18:28 TESTING2
```

**Step two:**

```
mkdir TESTING3
ls -l TESTING3
drwxrwxr-x  2 usr grp       4096 Apr 25 18:28 TESTING3
chmod o= TESTING3
drwxrwx---  2 usr grp       4096 Apr 25 18:29 TESTING3
chmod +t TESTING3
ls -l TESTING3
drwxrwx--T  2 usr grp       4096 Apr 25 18:29 TESTING3
```

**Step three**

```
ls -l TESTING2
drwxrwxr-t  2 usr grp       4096 Apr 25 18:28 TESTING2
chmod o-r TESTING2
ls -l TESTING2
drwxrwx--t  2 usr grp       4096 Apr 25 18:28 TESTING2
```

**Step four**

```
ls -dl T*[2,3]
drwxrwx--t 2 usr grp 4096 Apr 25 18:28 TESTING2
drwxrwx--T 2 usr grp 4096 Apr 25 18:29 TESTING3
```

In step one, a directory is created with default permissions. A sticky bit attribute is added and confirmed with a long listing as a lower "t".

In step two, another directory is created with default permissions. Permissions for others are removed and a sticky bit attribute is added. A long listing shows a capital "T" instead of lower "t".

In step three, we remove the read attribute for others, which was left at the end of step one, but we still got a lower "t", not a capital "T" (as we can see in step four), as we got in step two, after we removed other's read attribute.

My first question is: what's the difference between capital & lower sticky bit indicators? And the second question is: why TESTING3 got a capital sticky bit indicator, while step two got a lower one? They both have the same attributes at the end.

Any help would be greatly appreciated, since I'm stuck here with my study. I've read everything I could, but the manuals didn't clarify anything, nor did my tests which I posted above.

Thank you!

---

### Post by capscrew on 2013-04-25
The sticky bit, If set, replaces "x" in the others permissions to "t", if others have execute permissions, or to "T" otherwise. Examples:
```
-rwxrwxrwt  -- both others execute and sticky bit are set
-rwxrwxr-T --  sticky bit is set, but others execute is not set
```

---

### Post by clearski on 2013-04-25
> **capscrew said:**
> The sticky bit replaces "x" in the ***others*** permissions to "t".  If ***others*** have execute permissions the indicator is set to "T" otherwise. Examples:
```
-rwxrwxrwt  -- both others execute and sticky bit are set
-rwxrwxr-T --  sticky bit is set, but others execute is not set
```

So with lower "t" others have some execute permissions, except deleting files which don't belong to them.

And with capital "T" they don't have any execute permissions.

Did I understand correctly?

---

### Post by capscrew on 2013-04-25
> **clearski said:**
> So with lower "t" others have some execute permissions, except deleting files which don't belong to them.

And with capital "T" they don't have any execute permissions.

Did I understand correctly?

It's for the user to be able to know whether the execute bit is set of not when looking at the permissions of a particular file or directory.  Since the sticky bit and the execute bit are in the same position on the screen.  Remember there are only 3 positions to display 4 characters (rwx and T).

---

### Post by clearski on 2013-04-25
Yes, but could it be that both sticky bit "T" and execute bit are set at the same time? From the examples above, it doesn't appear so. Only "t" would allow some execute permissions, and if I'm not mistaking that's the way to know if under a sticky bit lies or not another execute permission.

Doesn't it make sense?

---

### Post by capscrew on 2013-04-25
> **clearski said:**
> Yes, but could it be that both sticky bit "T" and execute bit are set at the same time? From the examples above, it doesn't appear so. Only "t" would allow some execute permissions, and if I'm not mistaking that's the way to know if under a sticky bit lies or not another execute permission.

Doesn't it make sense?

You're talking about the same sticky bit.  Whether it's a T or a t it still is the sticky bit.  Anything is possible with the display.  I only use the visual when setting the bit (which is pretty rarely anyway).  I don't think about it too much.  :-)

---

### Post by clearski on 2013-04-25
> **capscrew said:**
> You're talking about the same sticky bit.  Whether it's a T or a t it still is the sticky bit.  Anything is possible with the display.  I only use the visual when setting the bit (which is pretty rarely anyway).  I don't think about it too much.  :-)

I've rapidly done some more  test and yes, even if there's the same bit, there's a difference between  a "t" and a "T". Here's the proof:

```
mkdir test
ls -l
drwxrwxr-x 2 usr grp       4096 Apr 25 19:39 test
chmod +t test
ls -l
drwxrwxr-t 2 usr grp       4096 Apr 25 19:40 test
chmod o-r test
ls -l
drwxrwx--t 2 usr grp       4096 Apr 25 19:40 test #now the execute permission are still set
chmod -t test #verify that execute permissions are still set
ls -l
drwxrwx--x 2 usr grp       4096 Apr 25 19:40 test #confirmed!
chmod +t test
drwxrwx--t 2 usr grp        4096 Apr 25 19:40 test #again we set the sticky bit over the execute permissions
chmod o-x test #we clear the execute permissions
ls -l
drwxrwx--T  2 usr grp       4096 Apr 25 19:40 test #the execute permissions were removed and we have a clean sticky bit set with no other ermissions  for others
```


Thank you very, very much!

---

