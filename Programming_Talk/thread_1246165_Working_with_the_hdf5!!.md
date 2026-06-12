---
title: "Working with the hdf5!!"
date: 2009-08-21
forum: Programming Talk
---

### Post by anudeep on 2009-08-21
Hi 
I am given a task to do a prog similar to this except that it should have 3 dimension, data of float type.novice and having a problem linking the header hdf5.h to the program.

I can do the task only if I can execute this.

I am a novice    
Can anyone help me please??


```


#include "hdf5.h"
#include <stdio.h>
#include <stdlib.h>

#define FILE            "h5ex_d_compact.h5"
#define DATASET         "DS1"
#define DIM0            4
#define DIM1            7

int
main (void)
{
    hid_t       file, space, dset, dcpl;    /* Handles */
    herr_t      status;
    H5D_layout_t    layout;
    hsize_t     dims[2] = {DIM0, DIM1};
    int         wdata[DIM0][DIM1],          /* Write buffer */
                rdata[DIM0][DIM1],          /* Read buffer */
                i, j;

    /*
     * Initialize data.
     */
    for (i=0; i<DIM0; i++)
        for (j=0; j<DIM1; j++)
            wdata[i][j] = i * j - j;

    /*
     * Create a new file using the default properties.
     */
    file = H5Fcreate (FILE, H5F_ACC_TRUNC, H5P_DEFAULT, H5P_DEFAULT);

    /*
     * Create dataspace.  Setting maximum size to NULL sets the maximum
     * size to be the current size.
     */
    space = H5Screate_simple (2, dims, NULL);

    /*
     * Create the dataset creation property list, set the layout to
     * compact.
     */
    dcpl = H5Pcreate (H5P_DATASET_CREATE);
    status = H5Pset_layout (dcpl, H5D_COMPACT);

    /*
     * Create the dataset.  We will use all default properties for this
     * example.
     */
    dset = H5Dcreate (file, DATASET, H5T_STD_I32LE, space, dcpl);

    /*
     * Write the data to the dataset.
     */
    status = H5Dwrite (dset, H5T_NATIVE_INT, H5S_ALL, H5S_ALL, H5P_DEFAULT,
                wdata[0]);

    /*
     * Close and release resources.
     */
    status = H5Pclose (dcpl);
    status = H5Dclose (dset);
    status = H5Sclose (space);
    status = H5Fclose (file);


    /*
     * Now we begin the read section of this example.
     */

    /*
     * Open file and dataset using the default properties.
     */
    file = H5Fopen (FILE, H5F_ACC_RDONLY, H5P_DEFAULT);
    dset = H5Dopen (file, DATASET);

    /*
     * Retrieve the dataset creation property list, and print the
     * storage layout.
     */
    dcpl = H5Dget_create_plist (dset);
    layout = H5Pget_layout (dcpl);
    printf ("Storage layout for %s is: ", DATASET);
    switch (layout) {
        case H5D_COMPACT:
            printf ("H5D_COMPACT\n");
            break;
        case H5D_CONTIGUOUS:
            printf ("H5D_CONTIGUOUS\n");
            break;
        case H5D_CHUNKED:
            printf ("H5D_CHUNKED\n");
    }

    /*
     * Read the data using the default properties.
     */
    status = H5Dread (dset, H5T_NATIVE_INT, H5S_ALL, H5S_ALL, H5P_DEFAULT,
                rdata[0]);

    /*
     * Output the data to the screen.
     */
    printf ("%s:\n", DATASET);
    for (i=0; i<DIM0; i++) {
        printf (" [");
        for (j=0; j<DIM1; j++)
            printf (" %3d", rdata[i][j]);
        printf ("]\n");
    }

    /*
     * Close and release resources.
     */
    status = H5Pclose (dcpl);
    status = H5Dclose (dset);
    status = H5Fclose (file);

    return 0;
}
```And the errors I'd get are:

new1.c:13:18: error: hdf5.h: No such file or directory
new1.c: In function &#8216;main&#8217;:
new1.c:25: error: &#8216;hid_t&#8217; undeclared (first use in this function)
new1.c:25: error: (Each undeclared identifier is reported only once
new1.c:25: error: for each function it appears in.)
new1.c:25: error: expected &#8216;;&#8217; before &#8216;file&#8217;

and so on...

---

### Post by dwhitney67 on 2009-08-21
Ok, thanks for creating the new thread.


Now, to answer your question... the file you seek, hdf5.h, is not a standard header file that is provided with the C library.  Thus it is probably from a 3rd-party.

Header files, btw, are used when compiling an application to ensure that any definitions, macros, and functions are being used in the appropriate manner as specified in the header file.

When you link the application, it is highly likely you will also require a shared-object or a static library to link with your application.  This library will have implemented the functions that are declared in the header file.

So, the first thing I suggest is that you attempt to locate the header file hdf5.h on your system.  If it cannot be found, then your effort to compile your application will be futile.

You should also attempt to locate the shared-object or static library file; these will have names such as libhdf5.so and/or libhdf5.a.

Please post back if you have found these, and I will be able to provide instructions on how to build your application.

---

### Post by anudeep on 2009-08-21
Yes I do have  libhdf5.a .

They are 3rd party code. They are available for download and I have downloaded them and tried to link them but cldnt...

thnks for the reply!

---

### Post by dwhitney67 on 2009-08-21
Ok, when you are ready to compile/link your application, run a command similar to the following:

```

gcc -I<hdf5.h path> new1.c -L<hdf5 library path> -lhdf5 -o new1

```
where <hdf5.h path> is the full path of the directory where the hdf5.h file resides, and where <hdf5 library path> is the full path of the directory where the hdf5 library (.so or .a) resides.

If you are successful in compiling, there should not be any errors (and preferably no warnings).  The executable, should it be built, will be named "new1".  To run it:
```

./new1

```


P.S.  An example:
```

gcc -I/usr/local/include new1.c -L/usr/local/lib -lhdf5 -o new1

```

---

### Post by anudeep on 2009-08-21
Thanks it did work!

i did this
```
anudeep@ubuntu:~/Desktop$ gcc -I static/include h5ex_d_compact.c -L static/lib h5ex_d_compact.c
 
```

The error it is showing is this!

```
anudeep@ubuntu:~/Desktop$ gcc -I static/include h5ex_d_compact.c -L static/lib h5ex_d_compact.c
/tmp/cclkfRfo.o: In function `main':
h5ex_d_compact.c:(.text+0x0): multiple definition of `main'
/tmp/ccayIa2l.o:h5ex_d_compact.c:(.text+0x0): first defined here
/tmp/ccayIa2l.o: In function `main':
h5ex_d_compact.c:(.text+0x91): undefined reference to `H5check_version'
```

I think that the libraries are not linked correctly yet!
Did I do whatever you told me correctly?


Please get me out of this!

---

### Post by anudeep on 2009-08-21
Also I need to use h5dump.exe in the bin folder how can i do that?

---

### Post by dwhitney67 on 2009-08-21
> **anudeep said:**
> Thanks it did work!

i did this
```
anudeep@ubuntu:~/Desktop$ gcc -I static/include h5ex_d_compact.c -L static/lib h5ex_d_compact.c
 
```

The error it is showing is this!

```
anudeep@ubuntu:~/Desktop$ gcc -I static/include h5ex_d_compact.c -L static/lib h5ex_d_compact.c
/tmp/cclkfRfo.o: In function `main':
h5ex_d_compact.c:(.text+0x0): multiple definition of `main'
/tmp/ccayIa2l.o:h5ex_d_compact.c:(.text+0x0): first defined here
/tmp/ccayIa2l.o: In function `main':
h5ex_d_compact.c:(.text+0x91): undefined reference to `H5check_version'
```
...

I thought your source file was new1.c?

If it is indeed h5ex_d_compact.c, you do not need to specify it twice in the gcc command shown above.  Only specify it once.

If you do not specify an output filename for the executable, gcc will default to creating a file called "a.out".

---

