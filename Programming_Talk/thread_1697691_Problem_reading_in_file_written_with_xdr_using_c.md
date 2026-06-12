---
title: "Problem reading in file written with xdr using c"
date: 2011-03-01
forum: Programming Talk
---

### Post by irva on 2011-03-01
Hello,

I am using ubuntu 10.4 and have two (long) codes in c, one that write a file using xdr, and one that uses this file as input. However, the second code do not manage to read in the written file. Everything looks perfectly fine, it just do not work... Anyone have any idea what is going wrong?

Relevant parts of code 1:

```

    /**
       * create compressed XDR output stream
       */
    
      output_file=open_write_pipe(output_filename);
      xdrstdio_create(&xdrs, output_file, XDR_ENCODE);
    
      /**
       * print material name
       */
    
      if( xdr_string(&xdrs, &name, _POSIX_NAME_MAX) == FALSE )
        xdr_err("xdr_string()");
```Relevant parts of code 2:

```
      /**
       * open data file
       */
    
      input_file=open_data_file(input_filename, "r");
      if( input_file == NULL ){
        ERROR(input_filename);
        exit(EXIT_FAILURE);
      }
      
      /**
       * create input XDR stream
       */
    
      xdrstdio_create(&xdrs, input_file, XDR_DECODE);
    
      /**
       * read material name
       */
    
      if(xdr_string(&xdrs, &name, _POSIX_NAME_MAX) == FALSE)
        XDR_ERR("xdr_string()");
```

---

### Post by gmargo on 2011-03-01
Perhaps you are not closing the xdr stream correctly?

I wrote two simple test programs.  One writes a file, the other reads it.  Seems to work fine for me.  Maybe these will help.

xdr_write.c:
```

#include <stdio.h>
#include <stdlib.h>
#include <errno.h>
#include <rpc/xdr.h>

int main()
{
    char * name = "Hello, World";
    FILE * file;
    XDR xdrs;

    if (NULL == (file = fopen("xdr-data.bin", "wb")))
    {
        fprintf (stderr, "fopen failed %d\n", errno);
        exit (2);
    }
    xdrstdio_create(&xdrs, file, XDR_ENCODE);
                        
    if (0 == xdr_string(&xdrs, &name, _POSIX_NAME_MAX))
    {
        fprintf (stderr, "xdr_string failed\n");
        exit (2);
    }

    xdr_destroy(&xdrs);
    fclose(file);
    return 0;
}

```xdr_read.c:
```

#include <stdio.h>
#include <stdlib.h>
#include <errno.h>
#include <rpc/xdr.h>

int main()
{
    char buffer[_POSIX_NAME_MAX+1];
    char * name = buffer;
    FILE * file;
    XDR xdrs;

    if (NULL == (file = fopen("xdr-data.bin", "rb")))
    {
        fprintf (stderr, "fopen failed %d\n", errno);
        exit (2);
    }
    xdrstdio_create(&xdrs, file, XDR_DECODE);
                        
    *name = '\0';
    if (0 == xdr_string(&xdrs, &name, _POSIX_NAME_MAX))
    {
        fprintf (stderr, "xdr_string failed\n");
        exit (2);
    }
    printf("Read back = \"%s\"\n", name);

    xdr_destroy(&xdrs);
    fclose(file);
    return 0;
}

```

---

