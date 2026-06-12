---
title: "Is there a system call other than 'open' for opening very large files?"
date: 2009-08-15
forum: Programming Talk
---

### Post by dariyoosh on 2009-08-15
Dear all,


Inside a C program, I want to open a very big file (about 12 GB) in order to read its
content. Here is the code:

```

    /*
          argv[1] contains the path to the file.
    */
    inputFileDescriptor = open(argv[1], O_RDONLY);
    if (inputFileDescriptor < 0)
    {
        fprintf(stderr, "Error: Could not open the input file\n");
        fprintf(stderr, "%s\n", strerror(errno));
        return 1;
    }

```


And it seems that the file is too big, because I receive the following error message:
```

Error: Could not open the input file
Value too large for defined data type

```

Is there any other system call, allowing to open very big files?


Thanks in advance,
Dariyoosh
:)

---

### Post by kjohansen on 2009-08-15
look at the bottom of this page for compiling instructions:

[http://coding.debuntu.org/c-handling-large-files-2g-standard-c](http://coding.debuntu.org/c-handling-large-files-2g-standard-c)

---

### Post by dariyoosh on 2009-08-16
> **kjohansen said:**
> look at the bottom of this page for compiling instructions:

[http://coding.debuntu.org/c-handling-large-files-2g-standard-c](http://coding.debuntu.org/c-handling-large-files-2g-standard-c)



Hello there,


Thank you very much for your help. I'll try this method.


Kind Regards,
Dariyoosh

---

### Post by dwhitney67 on 2009-08-16
> **dariyoosh said:**
> Hello there,


Thank you very much for your help. I'll try this method.


Kind Regards,
Dariyoosh

The method described in the link provided by kjohansen is the preferred way to support the opening of large files.

This information is also available in the man-page for "open" (man 2 open).  If you look for the description of the O_LARGEFILE flag option, it will describe this feature.

---

