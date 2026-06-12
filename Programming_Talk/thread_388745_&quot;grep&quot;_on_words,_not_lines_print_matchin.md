---
title: "&quot;grep&quot; on words, not lines? print matching word?"
date: 2007-03-19
forum: Programming Talk
---

### Post by monkeyking on 2007-03-19
I have Alot of files with the following structure
```

12374.1234 2345.431 #5/3 file=/afile1/myfile.data sput
16734.1234 2345.431 #5/6 file=/afile2/myfile.data sput
12334.1234 2345.431 #5/1 file=/afile4/myfile.data sput
12634.1234 2345.431 #5/7 file=/afile6/myfile.data sput
63g34.1234 2345.431 #5/3 file=/afile3/myfile.data sput

```

There a lot of lines, and alot of files.

What I want to do is extracting the
```

file=/afile4/myfile.data

```
part.

I thought I could use grep, but apperantly grep outputs hole lines only?
thanks in advance

---

### Post by simonn on 2007-03-19
```

cat /path/to/file | cut -f4 -d" "

```

---

### Post by ghostdog74 on 2007-03-20
```
awk '{print $4}' file
```

---

### Post by ghostdog74 on 2007-03-20
> **simonn said:**
> ```

cat /path/to/file | cut -f4 -d" "

```

```
cut -f4 -d" "  file
```

---

### Post by Mr. C. on 2007-03-20
> **simonn said:**
> ```

cat /path/to/file | cut -f4 -d" "

```

Simonn,

Read week 11: "Loose Ends", "Using cat unnecessarily"

  [http://cis68b1.mikecappella.com/calendar.php](http://cis68b1.mikecappella.com/calendar.php)

MrC

---

### Post by Cappy on 2007-03-21
Thanks Mr. C, it was a good read.

---

### Post by flip on 2009-07-22
> **monkeyking said:**
> I have Alot of files with the following structure
```

12374.1234 2345.431 #5/3 file=/afile1/myfile.data sput
16734.1234 2345.431 #5/6 file=/afile2/myfile.data sput
12334.1234 2345.431 #5/1 file=/afile4/myfile.data sput
12634.1234 2345.431 #5/7 file=/afile6/myfile.data sput
63g34.1234 2345.431 #5/3 file=/afile3/myfile.data sput

```

There a lot of lines, and alot of files.

What I want to do is extracting the
```

file=/afile4/myfile.data

```
part.

I thought I could use grep, but apperantly grep outputs hole lines only?
thanks in advance

Use --only-matching flag and write regex to match the 'file=...' part.
Sorry it took me so long to reply :)

---

### Post by soltanis on 2009-07-23
> **Mr. C. said:**
> Simonn,

Read week 11: "Loose Ends", "Using cat unnecessarily"

  [http://cis68b1.mikecappella.com/calendar.php](http://cis68b1.mikecappella.com/calendar.php)

MrC

If I didn't use cat unnecessarily, I don't know what I'd use it for at all.

---

### Post by ghostdog74 on 2009-07-23
cat's primary purpose is to concatenate files. using it together with tools such as awk/cut/sed, even the while read loop is "considered" unnecessary as these tools(as well as the while read loop) takes in the file as arguments.(or redirection in the case of while read)

---

### Post by Sockerdrickan on 2009-07-23
yeah split and cat is a great combo

---

### Post by Linfreak on 2010-09-28
Hi flip, Your method works fine with the given example. What if the file has content like the following?

ABCDE_VAR_JOHN_XYZ ABCDE_VAR_JACK_XYZ qwerABCDE_VAR_JACK_XYZ
.
.
similar lines.

And in the first line the "VAR" changes dynamically and also position of the ABCDE_VAR_JACK_XYZ string changes. My goal is to get just one instance of ABCDE_VAR_JACK_XYZ irrespective of how many times or where it is placed in the line?

If I use your and a regexp like "ABCDE.*JACK_XYZ" I will be getting the whole first line since it starts with ABCDE and ends with XYZ.

Thx in advance,
Siva

---

### Post by kurum! on 2010-09-28
why are you resurrecting a 3yrs old thread?

---

### Post by Linfreak on 2010-09-28
To get some answers for my problem thats closely related to this thread title.

Do you have some tips on how I could solve it?

Thx,
Siva

---

