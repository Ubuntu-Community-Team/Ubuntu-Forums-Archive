---
title: "[C] Triple Pointer Allocation"
date: 2009-09-08
forum: Programming Talk
---

### Post by Xender1 on 2009-09-08
I have a function that i am using to allocate (using calloc) triple pointers. this is what i have so far:
```

        double ***temp;
        int i, j;
        temp = (double ***)calloc(xyz_size,sizeof(double));
        for (i=0;i<xyz_size;i++) {
                temp[i] = (double **)calloc(xyz_size,sizeof(double));
                for (j=0;j<xyz_size;j++) {
                        temp[i][j] = (double *)calloc(xyz_size,sizeof(double));
                }
        }

        return temp;

```

i keep getting segmentation faults and i know that it has to be because i am doing this wrong but i just cant wrap my head around what is wrong. any help would be appreciated!

---

### Post by MadCow108 on 2009-09-08
I can't see anything wrong in this snippet
the segfault probably occurs somewhere else

valgrind is very helpful for debugging such things

---

### Post by Arndt on 2009-09-08
> **Xender1 said:**
> I have a function that i am using to allocate (using calloc) triple pointers. this is what i have so far:
```

        double ***temp;
        int i, j;
        temp = (double ***)calloc(xyz_size,sizeof(double));
        for (i=0;i<xyz_size;i++) {
                temp[i] = (double **)calloc(xyz_size,sizeof(double));
                for (j=0;j<xyz_size;j++) {
                        temp[i][j] = (double *)calloc(xyz_size,sizeof(double));
                }
        }

        return temp;

```

i keep getting segmentation faults and i know that it has to be because i am doing this wrong but i just cant wrap my head around what is wrong. any help would be appreciated!

One things that's wrong is that you should use sizeof(double**) and sizeof(double*) for the non-final arrays. But those are either equal to or less than sizeof(double), so it won't be the reason for your errors.

---

### Post by Linteg on 2009-09-08
The allocation seems to be ok but you should, just like Arndt already pointed out, note that sizeof(double) is not necessarily equal to sizeof(double *). It is equal for 64-bit x86_64/amd64 where both are 8 bytes, but not for 32-bit x86 where a pointer is 4 bytes and a double 8.

---

### Post by Xender1 on 2009-09-08
ah yes i checked using gdb and when i now see where my seg fault is. when i pass this triple pointer into another pointer, it now is a quad pointer. when i try and put data into it that is where my seg fault occurs:
```

*matrix[x][y][z] = atof(instring);

```

---

### Post by nvteighen on 2009-09-08
This is clearly a segfault in some place where you access the array... A common mistake is that you were reusing i and j in some place... Remember that after exiting the loop, i and j will be equal to xyz_size and therefore, will cause a segfault "by one".

---

### Post by Xender1 on 2009-09-08
```

		for (z=0;z<*xyz_size;z++) {
		for (x=0;x<*xyz_size;x++) {
		for (y=0;y<*xyz_size;y++) {
			fgets(instring,10,pFile);
			*x_matrix[x][y][z] = atof(instring);
		}}}

```
not sure if i should switch the x and y loops or not, but this is how i am reading in the data because i know what i am reading in....just seg faults... i tried xyz_size-1 too and still got the error

---

### Post by MadCow108 on 2009-09-08
you don't need to make another pointer to the array when passing it into another function because it already is a pointer.

also it seems like your passing xyz_size as a pointer too which is not really necessary as the passing of a pointer by value is equally expensive as passing the integer by value directly (pointers are just unsigned integers)

to see where exactly your problem is we need more code, best would be a complete running example

---

### Post by Linteg on 2009-09-08
> **Xender1 said:**
> ```

*x_matrix[x][y][z] = atof(instring);

```

that is equal to [PHP]*(x_matrix[x][y][z]) = atof(instring);[/PHP] which isn't quite what you want.
[PHP](*x_matrix)[x][y][z] = atof(instring);[/PHP]
should work. But I agree with MadCow108, avoid creating this quad pointer unless you really need to.

---

