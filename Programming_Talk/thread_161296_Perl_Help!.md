---
title: "Perl Help!"
date: 2006-04-16
forum: Programming Talk
---

### Post by garretwp on 2006-04-16
I have what seems what might be a simple fix for others. 

Say for exampe you create an array with a command in it. i.e. @ls = `ls -al`;
Then you go to print the array. i.e. print "@ls\n";

My problem is when you go to print the array the first line is formated ok, but the rest of the lines all have what seems to be a space or should I say a white space. Is there a way to fix this to make them all align right?

Here is what I am talking about:

gwp:/home/gwp/> lstest

```
total 52
 -rwxr-xr-x  1 gwp u  58 Apr  2 07:19 drivesdown2
 -rwxr-xr-x  1 gwp u 473 Apr 16 11:41 getjobids
 -rwxr-xr-x  1 gwp u 206 Oct 12  2005 homerestore
 -rwxr-xr-x  1 gwp u  51 Apr 16 18:01 lstest
 -rwxr-xr-x  1 gwp u 440 Apr 16 14:45 qru
 -rwxr-xr-x  1 gwp u 421 Apr 16 17:33 qru2
 -rwxr-xr-x  1 gwp u 551 Oct 25 10:16 tailhomerestore
```


and if you were to do a normal ls -al:
```

total 52
drwxr-xr-x  2 gwp u 114 Apr 16 18:01 ./
drwxr-xr-x  3 gwp u  89 Apr 16 11:30 ../
-rwxr-xr-x  1 gwp u  58 Apr  2 07:19 drivesdown2*
-rwxr-xr-x  1 gwp u 473 Apr 16 11:41 getjobids*
-rwxr-xr-x  1 gwp u 206 Oct 12  2005 homerestore*
-rwxr-xr-x  1 gwp u  51 Apr 16 18:01 lstest*
-rwxr-xr-x  1 gwp u 440 Apr 16 14:45 qru*
-rwxr-xr-x  1 gwp u 421 Apr 16 17:33 qru2*
-rwxr-xr-x  1 gwp u 551 Oct 25 10:16 tailhomerestore*
```

Any help would be appreciated! Mind you I am only a beginner.

Thanks,

- Garrett

---

### Post by unbuntu on 2006-04-16
Let me see if I can explain this well...

It's actually a common mistake for beginners (I'm one also)
Since "@ls" is using the list in a scalar context, the list is converted to a string separated by a whitespace.  That's what causes the "indented" printout.

Try using @ls in the list context, which is print @ls

EDIT: By the way, if I may add:  there's no need to pad a "\n" after it, since `ls -l` preserves the newline character.

---

### Post by garretwp on 2006-04-16
Thanks I knew it was something so simple. The most pain in the butt issues are the ones that are over looked or very simple to fix! Not adding the newline at the end of the array when you go to print solved the problem!

Thanks again!

Garrett

---

