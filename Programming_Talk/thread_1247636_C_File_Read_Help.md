---
title: "C File Read Help"
date: 2009-08-23
forum: Programming Talk
---

### Post by matmatmat on 2009-08-23
```

2        |                                                 H|
2        |                                                 H|
2        |                                                 H|
2        |                                                 H|
2        |                                                 H|
2        |                                                 H|

```
& this code to read it in:
```

				        f = fopen("afile", "r");	
				        char *t[100];
				        int i = 0;		
				        int i2 = 0;

					int n = atoi(optarg) - 1;		
					while (fscanf(f, "%s", line) != EOF) {
						if (i != n){
							printf("%s\n", line);
							t[i2] = strdup(line);
							i2++;
						}
						i++;
					}
					t[i2] = '\0';
					i2 = 0;
			       		fclose(f);
					f = fopen("afile", "w");
					fprintf(f, "");
					fclose(f);
					f = fopen("afile", "a");
					for (i2 = 0; t[i2] != '\0'; i2++)
			       		{	
						fprintf(f, "%s", t[i2]);
						free(t[i2]);
					}

```
when run:
```

|
H|
2
|
H|
2
|
H|
2
|
H|
2
|
H|
2
|
H|

```
I expected the output to look like the file, whats wrong?

---

### Post by Arndt on 2009-08-23
> **matmatmat said:**
> ```

2        |                                                 H|
2        |                                                 H|
2        |                                                 H|
2        |                                                 H|
2        |                                                 H|
2        |                                                 H|

```
& this code to read it in:
```

				        f = fopen("afile", "r");	
				        char *t[100];
				        int i = 0;		
				        int i2 = 0;

					int n = atoi(optarg) - 1;		
					while (fscanf(f, "%s", line) != EOF) {
						if (i != n){
							printf("%s\n", line);
							t[i2] = strdup(line);
							i2++;
						}
						i++;
					}
					t[i2] = '\0';
					i2 = 0;
			       		fclose(f);
					f = fopen("afile", "w");
					fprintf(f, "");
					fclose(f);
					f = fopen("afile", "a");
					for (i2 = 0; t[i2] != '\0'; i2++)
			       		{	
						fprintf(f, "%s", t[i2]);
						free(t[i2]);
					}

```
when run:
```

|
H|
2
|
H|
2
|
H|
2
|
H|
2
|
H|
2
|
H|

```
I expected the output to look like the file, whats wrong?

Do you expect fscanf with %s to read one line at the time? It doesn't do that; it reads whitespace-separated pieces. Look at the man page. If you want to read just lines, use fgets.

Do use the debugger in situations like this - you would have seen at once that not a whole line was read.

I'm curious why you open your file first with "w", close it and then open it using "a". Can't you just open it with "w" if you want to write to it and replace the old contents?

---

### Post by rye_ on 2009-08-23
Something v. simple like the code below will work (avoids buffer in using fgets),
  char * t[100] allocates a 2d array - is this what you want?


```

  7         FILE * f;
  8         f = fopen("afile", "r");
  9         if (f == NULL){
 10                 puts("error: exited");
 11                 exit(EXIT_FAILURE); //requires stdlib.h
 12         }
 14 
 15         char got;
 16         while ( (got = getc(f)) != EOF) {
 17                 printf("%c", got);
 18         }

```

---

