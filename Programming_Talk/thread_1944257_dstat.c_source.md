---
title: "dstat.c source?"
date: 2012-03-21
forum: Programming Talk
---

### Post by conradin on 2012-03-21
hi all, 
Im looking for a dstat.c source file, I found one from the army, but it doesnt look like linux type source,.. and I think its not right. Compling gives errors...

can some one point me to the dstat.c source code?

heres what i have now:
```
// #include "common.h"
 #include <string.h>
 #include <stdlib.h>
 #include <math.h>
 //#include "bio.h"
// #include "bu.h"
 #define IBUFSIZE 1024           /* Max read size */
 double  buf[IBUFSIZE];          /* Input buffer */
 int     verbose = 0;
  
 int main(int argc, char **argv)
 {
     int i, n;
     long        num_values;
     register double *bp;
     double      sum, sum2;
     double      max, min;
     double      mean, var;
     FILE        *fp;
 
     /* check for verbose flag */
     if ( argc > 1 && strcmp(argv[1], "-v") == 0 ) {
         verbose++;
         argv++;
         argc--;
    }
 
     /* look for optional input file */
     if ( argc > 1 ) {
         if ( (fp = fopen(argv[1], "r")) == 0 ) {
             bu_exit(1, "dstat: can't open \"%s\"\n", argv[1] );
         }
         argv++;
         argc--;
     } else
         fp = stdin;
 
     /* check usage */
     if ( argc > 1 || isatty(fileno(fp)) ) {
         bu_exit(1, "Usage: dstat [-v] [file.doubles]\n");
     }
 
     /*
      * Find sum, min, max, mode.
      */
     num_values = 0;
     sum = sum2 = 0;
 #if defined(HUGE_VAL)
     min = HUGE_VAL;
     max = -HUGE_VAL;
 #else
     min = HUGE;
     max = -HUGE;
 #endif
     while ( (n = fread(buf, sizeof(*buf), IBUFSIZE, fp)) > 0 ) {
         num_values += n;
         bp = &buf[0];
         for ( i = 0; i < n; i++ ) {
             sum += *bp;
            sum2 += *bp * *bp;
             if ( *bp < min )
                 min = *bp;
             if ( *bp > max )
                 max = *bp;
             bp++;
         }
     }
     mean = sum/(double)num_values;
     var = sum2/(double)num_values - mean * mean;
 
     /*
      * Display the results.
      */
     printf( "Values  %14ld (%.0f x %.0f)\n", num_values,
             sqrt((double)num_values), sqrt((double)num_values) );
     printf( "Min     %14.6g\n", min );
     printf( "Max     %14.6g\n", max );
     printf( "Mean    %14.6g\n", mean );
     printf( "s.d.    %14.6g\n", sqrt( var ) );
     printf( "Var     %14.6g\n", var );
 
     return 0;
 }


```

---

### Post by CynicRus on 2012-03-21
i fixed you dstat code:
```

// #include "common.h"
 #include <string.h>
 #include <stdlib.h>
 #include <math.h>
 #include <sys/types.h>
#include <fcntl.h>
    #include <stdio.h>
 //#include "bio.h"
// #include "bu.h"
 #define IBUFSIZE 1024           /* Max read size */
 double  buf[IBUFSIZE];          /* Input buffer */
 int     verbose = 0;
  
 int main(int argc, char **argv)
 {
     int i, n;
     long        num_values;
     register double *bp;
     double      sum, sum2;
     double      max, min;
     double      mean, var;
     FILE        *fp;
 
     /* check for verbose flag */
     if ( argc > 1 && strcmp(argv[1], "-v") == 0 ) {
         verbose++;
         argv++;
         argc--;
    }
 
     /* look for optional input file */
     if ( argc > 1 ) {
         if ( (fp = fopen(argv[1], "r")) == 0 ) {
            // bu_exit(1, "dstat: can't open \"%s\"\n", argv[1] );
            printf("dstat: can't open \"%s\"\n", argv[1]);
            exit(1);
         }
         argv++;
         argc--;
     } else
         fp = stdin;
 
     /* check usage */
     if ( argc > 1 || isatty(fileno(fp)) ) {
        // bu_exit(1, "Usage: dstat [-v] [file.doubles]\n");
        printf("Usage: dstat [-v] [file.doubles]\n");
        exit(2);
     }
 
     /*
      * Find sum, min, max, mode.
      */
     num_values = 0;
     sum = sum2 = 0;
 #if defined(HUGE_VAL)
     min = HUGE_VAL;
     max = -HUGE_VAL;
 #else
     min = HUGE;
     max = -HUGE;
 #endif
     while ( (n = fread(buf, sizeof(*buf), IBUFSIZE, fp)) > 0 ) {
         num_values += n;
         bp = &buf[0];
         for ( i = 0; i < n; i++ ) {
             sum += *bp;
            sum2 += *bp * *bp;
             if ( *bp < min )
                 min = *bp;
             if ( *bp > max )
                 max = *bp;
             bp++;
         }
     }
     mean = sum/(double)num_values;
     var = sum2/(double)num_values - mean * mean;
 
     /*
      * Display the results.
      */
     printf( "Values  %14ld (%.0f x %.0f)\n", num_values,
             sqrt((double)num_values), sqrt((double)num_values) );
     printf( "Min     %14.6g\n", min );
     printf( "Max     %14.6g\n", max );
     printf( "Mean    %14.6g\n", mean );
     printf( "s.d.    %14.6g\n", sqrt( var ) );
     printf( "Var     %14.6g\n", var );
 
     return 0;
 }

```




output:
```

cynic@ndc:~$ gcc -c main.c
cynic@ndc:~$ gcc  main.o -o dstat -lm
cynic@ndc:~$ ./dstat
Usage: dstat [-v] [file.doubles]

```

---

### Post by conradin on 2012-03-21
Hm,
I had some trouble with that, when building that code. includinging unisat.h was helpful, but then there was build errors..
this is close, but still not functional. 
```
// A program to store file stat data using dynamically allocated memory
// Compile command: gcc -o dstat -Wall -g dstat.c
#define __USE_BSD
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <errno.h>
#include <sys/stat.h>
#include <sys/types.h>

int main(int argc, char * argv[])
{
	struct stat **s;	// Stat array buffer
	int err, i;			// Error code and counter
	char buf[256];		// Error message buffer

	// Allocate the stat pointer buffer
	s=(struct stat **)malloc(sizof(struct stat *)*( argc-1));
	if (s==NULL) {
		perror("malloc");
		return errno;
	}
	// For every argument
	for (i=1;i<argc;i++) {
		// Allocate memory for this file
		s[i-1]=malloc(sizeof(struct stat));
		if (s[i-1]==NULL) {
			perror("malloc");
			continue;
		}
		// Stat each file
		err=stat(argv[i],s[i-1]);
		// if error
		if (err<0) {
			snprintf(buf,256,"stat(\"%s\")",argv[i]);
			perror(buf);
			// Clean up memory and indicate it's invalid
			free(s[i-1]);
			s[i-1]=NULL;
		}
	}
	// Print inode number and size for each valid stat buffer
	for (i=0;i<argc-1;i++) {
		if (s[i]) {
			printf("%16lu %lu\n",s[i]->st_ino,s[i]->st_size);
		}
	}
	// Free stat structures
	for (i=0;i<argc-1;i++) {
		if (s[i]) free(s[i]);
	}
	// Free stat list
	free(s);
	return 0;
}

```

---

### Post by conradin on 2012-03-21
ARGH! I had a typo:sizof > *sizeof
that change has made everything work as expected!

---

