---
title: "help me with perl regexp"
date: 2010-11-26
forum: Programming Talk
---

### Post by tisungho on 2010-11-26
Hi

I want to replace the second value of "10-11-25" (in bold font) to "-":

<TD><FONT SIZE=-1><A HREF="10-11-25/all_runs.html">**10-11-25**</A></FONT></TD>

For example, the final result should look like this: 
<TD><FONT SIZE=-1><A HREF="10-11-25/all_runs.html">-</A></FONT></TD>

Here is my solution:
$line is above string
```
$line=~s/(\d+)/-/g
```

But the result is like this :(
<TD><FONT SIZE=--><A HREF="-----/all_runs.html">-----</A></FONT></TD>

Please help me!

Thanks!

---

### Post by Arndt on 2010-11-26
> **tisungho said:**
> Hi

I want to replace the second value of "10-11-25" (in bold font) to "-":

<TD><FONT SIZE=-1><A HREF="10-11-25/all_runs.html">**10-11-25**</A></FONT></TD>

For example, the final result should look like this: 
<TD><FONT SIZE=-1><A HREF="10-11-25/all_runs.html">-</A></FONT></TD>

Here is my solution:
$line is above string
```
$line=~s/(\d+)/-/g
```

But the result is like this :(
<TD><FONT SIZE=--><A HREF="-----/all_runs.html">-----</A></FONT></TD>

Please help me!

Thanks!

```
$line=~s/\[B\]10-11-25\[\/B\]/-/
```

---

### Post by tisungho on 2010-11-26
> **Arndt said:**
> ```
$line=~s/\[B\]10-11-25\[\/B\]/-/
```

Hi,
Thanks for your help, but it doesn't work :(
And also, we shouldn't hardly match it like this way, because the date is gonna be changed

---

### Post by DaithiF on 2010-11-26
```
$line=~s/>\d{2}-\d{2}-\d{2}</>-</g;
```

---

### Post by Arndt on 2010-11-26
> **tisungho said:**
> Hi,
Thanks for your help, but it doesn't work :(
And also, we shouldn't hardly match it like this way, because the date is gonna be changed

It worked when I tried it. What does it do?

When the date changes, you of course change the numbers to something more general.

---

### Post by Arndt on 2010-11-26
> **tisungho said:**
> Hi,
Thanks for your help, but it doesn't work :(
And also, we shouldn't hardly match it like this way, because the date is gonna be changed

I think I know what happened: your bold marks got into my expression. Just remove them.

---

