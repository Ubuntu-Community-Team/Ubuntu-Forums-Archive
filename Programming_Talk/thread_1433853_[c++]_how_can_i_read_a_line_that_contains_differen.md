---
title: "[c++] how can i read a line that contains different data types from a file."
date: 2010-03-19
forum: Programming Talk
---

### Post by fasoulas on 2010-03-19
IN c++

What would be the code if i want to read a line from a file and this line contains numbers of different data types.I want to be able to save each number in a variabe of the same data type.

Example:

1.24   345   3442

---

### Post by schauerlich on 2010-03-19
[http://www.cplusplus.com/doc/tutorial/files/](http://www.cplusplus.com/doc/tutorial/files/)

```
ifstream inf;
double d;
int n, m;

inf.open("foo.txt", ios::in);

inf >> d >> n >> m;

inf.close();
```

---

### Post by MindSz on 2010-03-19
Maybe somthing like:```
cin >> myfloat >> myint1 >> myint2
```

---

### Post by fasoulas on 2010-03-19
> **MindSz said:**
> Maybe somthing like:```
cin >> myfloat >> myint1 >> myint2
```

That was what i was thinking but i wasn't sure.

Does c++ has this feature to find different data types in a line?

---

### Post by fasoulas on 2010-03-19
> **schauerlich said:**
> [http://www.cplusplus.com/doc/tutorial/files/](http://www.cplusplus.com/doc/tutorial/files/)

I have already checked that and it didn't help

thanks for replying anyway

---

### Post by MadCow108 on 2010-03-19
what and how the formated operators (<< >>) read is only determined by the type where it should store or output the data. So put a double type on the right side of it and it will read/write doubles

so to read them all into the same type is easy for doubles because an integer is also a valid double representation for streams

double a[3]
somefilestream >> a[0] >> a[1] >> a[2]; // read in any number into doubles
it will also work for other number formats like 3.23e10

the other way round is not valid, if inputed 1.2 when reading ints will read the one and stop at the dot. subsequent integer reads will thus fail when the .2 is not removed from the stream first

---

### Post by dwhitney67 on 2010-03-19
After performing the read operations on the stream, verify that all went well with the good() method (or conversely, with fail()).

```

double d;
int m, n;

mystream >> d >> m >> n;

if (!mystream.good())
{
   // error parsing data
}

```

---

### Post by fasoulas on 2010-03-19
> **dwhitney67 said:**
> After performing the read operations on the stream, verify that all went well with the good() method (or conversely, with fail()).

```

double d;
int m, n;

mystream >> d >> m >> n;

if (!mystream.good())
{
   // error parsing data
}

```

ok thanks i will try it

---

