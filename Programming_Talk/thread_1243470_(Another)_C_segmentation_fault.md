---
title: "(Another) C segmentation fault"
date: 2009-08-18
forum: Programming Talk
---

### Post by matmatmat on 2009-08-18
I am doing (the third?) "[Beginner] Programming Challenge"
```

#include <stdio.h>

char re[];

void rstart(char a[], int length)
{
    //strips an amount of characters [length] from the start of a string
    //if the length is 3 then it works (if a[] was "1. Hi" that re becomes "Hi" 
    int retval;
    for(retval = 0; a[retval] != '\0'; retval++) {}//get length of array
	int endn = retval - length;
	int i2;
	int b = 0;
	for(i2=0;i2<=retval;i2++){
		if (i2 <= endn){
		}
		else{
			re[b]=a[i2];
			b++;
		}
	}
}

int main(int argc, char** argv)
{
    printf("h");
    FILE *fp;
    fp=fopen("bhaarat.txt", "r");
    char names[30][30];
    int c;
    int i = 0;
    int i2 = 0;
    while ((c = fgetc (fp)) != EOF){
        //read file
        if (c == '\n'){
            printf("c");
            i++;
            i2 = 0;
        }else{
            printf("else");
            names[i][i2] = c;
            ++i2;
        }
        i++;
    }
    int i3;
    for(i3=0; names[i3] != '\0'; i3++){
        rstart(names[i3], 3);
    }
	return 0;
}

```
when run it gives Segmentation fault

---

### Post by MindSz on 2009-08-18
You're no checking to see if the file (bhaarat.txt) has opened successfully. 

Also, what kind of syntax do you expect from this file?

---

### Post by matmatmat on 2009-08-18
[http://ubuntuforums.org/showthread.php?t=884394]("http://ubuntuforums.org/showthread.php?t=884394")

---

### Post by MindSz on 2009-08-18
Since this is a challenge, I don't wan to to give away too much. Just watch out for the return value of fgetc and the variable you're storing it in, or look for another way to get input from the file (remember strings are char chains).

Also, even tho it's not strictly necessary, assign a finite amount of elements to your array (re[]) so you (and the computer) will know how much space it will use.

If you're not doing it, compile with the '-Wall' option so you get all the warnings from the compiler.

As I said, since it's a challenge I'll leave the actual code to you.

good luck!

---

### Post by matmatmat on 2009-08-18
Thanks, I did it in 19 lines by using fscanf

---

### Post by dwhitney67 on 2009-08-18
> **matmatmat said:**
> Thanks, I did it in 19 lines by using fscanf

I hope not to read in a string?  Use fgets() instead.  It is considered a safer operation since the programmer can specify how big the destination buffer will be, and thus prevent possible buffer overruns.

Bear in mind when using fgets(), reading will stop when either a newline is detected or the number of characters desired have been found.  If a newline is found, it is stored in the buffer.  This may not be desirable for the application, so care must be taken to remove it from the string.

---

