---
title: "c++: exercuting a program with two files"
date: 2008-04-01
forum: Programming Talk
---

### Post by Suraine on 2008-04-01
Dear c++ guru:

In c++, normally we will call a function as shown below:

```

int funct ()
{
      ...;
}

void main()
{
      funct();
}

```

main will call the function "funct()" which is defined within the same file.

However, in my case, i wish to have the "funct()" on the other file while the "main()" is in a file as shown below:

```

filename: File1.C

void main()
{
      funct(); //funct() from File2.C
}


```

```

filename: File2.C

int funct()
{
      ...;
}


```

Is that possible? How can I achieve that?


Thanks,

Best regards,
Mei Ying

---

### Post by LaRoza on 2008-04-01
```

filename: File1.C

void main()
{
      funct(); //funct() from File2.C
}


```

```

filename: File2.C

int funct()
{
      ...;
}


```

```

g++ File1.c File2.c 

```

You will want to put the declarations in a header file and include that in both files as well.

---

### Post by Suraine on 2008-04-01
Thanks, LaRoza

---

### Post by dwhitney67 on 2008-04-02
When programming in C++, never start thinking in terms of the header file and the implementation file.  Just think of the header file.  This is where your class definition(s) should reside.  Without this, your implementation file is "incomplete".

Many people think that they have the "solution" to a problem before they even _design_ the proper s/w for the problem.

Start with the header file, then a skeleton .cpp (or .C) file.  Both should compile before even one line of implementation code is added to satisfy the design.

P.S.  When implementing methods/functions that return values, return the "false/negative" values expected.

P.S.S.  Some believe in "Code a little; test a little."  YMMV.

---

### Post by Wybiral on 2008-04-02
> **dwhitney67 said:**
> Code a little; test a little.

A better rule: "Code a little; test a LOT." :)

---

