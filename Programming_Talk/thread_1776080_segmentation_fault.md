---
title: "segmentation fault"
date: 2011-06-05
forum: Programming Talk
---

### Post by muppy80 on 2011-06-05
Hi All,
i'm pretty new to C programming.
In the following i will put the first program i wrote.
If i try to open a file named "bruco.coord" containing a few lines with number the code works fine.
If i try to open named "bruco.coord" containing 81Milions of lines the code gives me the error "segmentation fault".
In both cases structure of bruco.coord is something like

 1 4
 2 5
 5 8
and so on...

Here is my code, any idea on how to solve the problem ?

Thanks,
Andrea

#include <stdio.h>
#include <string.h>
    

    int main ( void )
    {
    char filename[] = "bruco.coord";
    FILE *file ;
    file= fopen (filename,"r");
    if ( file != NULL )
    {
    char line [8260000]; /* or other suitable maximum line size */
    float step=-0.4;
    int i;
    float min=-0.02;
    float max=0.02;
    float a[10000];
    float limit1;
    float limit2;
    while ( fgets ( line, sizeof line, file ) != NULL ) /* read a line */
    {
        sscanf(line,"%f%f", &limit1, &limit2);
    
        if (limit2==11111111)
        {
                                
                int indice0=0;                
                float maxval=0;
                float minval=0;
                for (indice0 = 0 ; indice0 < i ; indice0++) 
                {
                    if (a[indice0] > maxval) 
                    {
                        maxval = a[indice0] ;
                    }
                }
                
                for (indice0 = 0 ; indice0 < i ; indice0++) 
                {
                    if (a[indice0] < minval) 
                    {
                        minval = a[indice0];
                    }
                }
            int passo=0;
            float bin_center[10000];
            int indice2=0;
            int freq_count[10000];
            float freqsize=1000;
            float bin_size=(maxval - minval)/freqsize;
            for (passo=0; passo<freqsize; passo++)
            {    
                for (indice2 = 0; indice2 < i ; indice2++) 
                {
                    if ((a[indice2]>minval+passo*bin_size)&(a[indice2]<minval+(passo+1)*bin_size)) 
                    {
                        freq_count[passo]++;
                        bin_center[passo]=minval+passo*bin_size;                        
                    }
                    else if ((a[indice2]<minval+passo*bin_size))
                    {
                        bin_center[passo]=minval+passo*bin_size;            
                    }
                    else if ((a[indice2]>minval+(passo+1)*bin_size))
                    {
                        bin_center[passo]=minval+passo*bin_size;            
                    }
                }
            }
            int ciao=0;
            for (ciao=0; ciao<freqsize; ciao++)
            {
                printf("%f %f %i\n",step, (bin_center[ciao]*57.32-step), freq_count[ciao]);
                FILE *destinazione;
                destinazione = fopen("file.txt","a+"); /* apend file (add text to a file or create a file if it does not exist.*/
                fprintf(destinazione,"%f %f %i\n",step, (bin_center[ciao]*57.32-step), freq_count[ciao]); /*writes*/
                fclose(destinazione); /*done!*/                
            }
            memset(a, 0, i);
            memset(freq_count, 0, i);
            memset(bin_center, 0, i);
            i=0;
            step=step+0.01;
            
        }
        /* conto il numero di elementi che mi interessa binnare */
        else if ((limit2<max)&(limit2>min))
        {    
            a[i] = limit2;
            i++;
        }
        /* fine del conteggio */            
    }    
    fclose ( file );
    }
    else
    {
    perror ( filename ); /* why didn't the file open? */
    }
    return 0;
    }

---

### Post by simeon87 on 2011-06-05
Try using print statements or a debugger to determine the line on which the segfault occurs. It means you're trying to access memory which isn't part of your program. For example, you could be trying to access data outside of an array, it's hard to say without doing some more debugging.

---

### Post by GeneralZod on 2011-06-05
```

char line [8260000]; /* or other suitable maximum line size */

```

This is a pretty big array to place on the stack.

---

### Post by muppy80 on 2011-06-05
> **GeneralZod said:**
> ```

char line [8260000]; /* or other suitable maximum line size */

```This is a pretty big array to place on the stack.

even decreasing the array size is not solving the problem.

Thanks,
Andrea

---

### Post by Petrolea on 2011-06-05
Seg fault is most likely to be caused by pointers. For example: when functions accepts NULL (empty) pointer as an argument it might throw a seg fault. Try with few more 'if's to see whether some pointers are empty.

---

### Post by JupiterV2 on 2011-06-05
The point he's making is that you should probably allocate it on the heap, not the stack, with malloc().

Your first step should probably be to use gdb to do a backtrace on where segfault occurs to identify the problem. C doesn't do bounds checking so the likely reason is that you're trying to access out-of-bounds memory, maybe by trying to write a segment of memory outside of your array. An example to illustrate this common mistake:

```

int
main (void)
{
  int i;
  int arr[5];
  
  /* this code will segfault on the final iteration because we
     are trying to write to index 5, the sixth element of the
     array, which is out-of-bounds. The maximum index for an
     array of 5 is 4. */
  for (i = 0; i <= 5; i++)
    {
      arr[i] = i;
    }

  return 0;
}
```

Finding this kind of error isn't always arbitrary, so using gdb (GNU DeBugger) is probably your best tool.

---

### Post by muppy80 on 2011-06-05
An update: 

I've a tutorial on the net and used debugger gdb in the following way

from prompt i give the command

gcc -g aa.c

(aa.c is the name of my program)

then i give the command

gdb a.out

A new prompt appears.

I give the command "run" and the following error appears.

```
Starting program: /home/andrea/Desktop/a.out 

Program received signal SIGSEGV, Segmentation fault.
0xb7ec30a2 in fgets () from /lib/i386-linux-gnu/libc.so.6
```

So, in my understanding the error is coming from fgets function. Is this right ?? If yes, how to solve it ??

Best regards,
Andrea

---

### Post by Petrolea on 2011-06-06
> **muppy80 said:**
> An update: 

I've a tutorial on the net and used debugger gdb in the following way

from prompt i give the command

gcc -g aa.c

(aa.c is the name of my program)

then i give the command

gdb a.out

A new prompt appears.

I give the command "run" and the following error appears.

```
Starting program: /home/andrea/Desktop/a.out 

Program received signal SIGSEGV, Segmentation fault.
0xb7ec30a2 in fgets () from /lib/i386-linux-gnu/libc.so.6
```

So, in my understanding the error is coming from fgets function. Is this right ?? If yes, how to solve it ??

Best regards,
Andrea

I don't know about you, but I tried your code and I didn't get any seg faults (I also created the file with some sample input).

Maybe your lines are too long? Can't see any other reason for seg fault. You're storing it in array and fgets function seems good. I think you try to store way too much info in an array and that's why it throws a seg fault.

---

### Post by dwhitney67 on 2011-06-06
As others have pointed out, the following is ridiculous:
```

char line [8260000];

```
If you are reading in a line from a file that may contain the numbers "10 20", or even on a worse case scenario "1000000000 1000000000" (largest int will take up 10 characters), you do not need an array that big.  Consider declaring the array to be:
```

char line [80];   // 21 bytes ought to do, but to be safe, declare 80

```
Now, I cannot understand why you are treating the input data as floats, unless of course you failed to properly disclose your data requirements, and instead of int values, your data file actually contains floating point values.

One other issue that stands out with your code is the following, for which there are other similar cases:
```

for (indice0 = 0 ; indice0 < i ; indice0++)

```
If you pay close attention to your code, you will notice that 'i' (which btw, is a stupid name for a variable), has never been initialized.  Thus when you access the array 'a' (yes, another stupid variable name) using the value of 'indice0', who knows what value it will be.

Fix your code, and re-post it _using CODE tags_ if you have any additional problems.


P.S.  Rename your single-character variable names to be more descriptive of the data they contain/represent.

---

### Post by Arndt on 2011-06-06
> **muppy80 said:**
> An update: 

I've a tutorial on the net and used debugger gdb in the following way

from prompt i give the command

gcc -g aa.c

(aa.c is the name of my program)

then i give the command

gdb a.out

A new prompt appears.

I give the command "run" and the following error appears.

```
Starting program: /home/andrea/Desktop/a.out 

Program received signal SIGSEGV, Segmentation fault.
0xb7ec30a2 in fgets () from /lib/i386-linux-gnu/libc.so.6
```

So, in my understanding the error is coming from fgets function. Is this right ?? If yes, how to solve it ??

Best regards,
Andrea

Yes, and to see the execution chain that leads into fgets, use the gdb command "bt", for "backtrace". You can then use the commands "up" and "down" to walk around in the stack. When you're looking at a stack frame that belongs to your program, you can use the print command "p" to inspect the values of variables.

---

