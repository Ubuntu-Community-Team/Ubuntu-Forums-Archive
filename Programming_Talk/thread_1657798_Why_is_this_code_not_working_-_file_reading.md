---
title: "Why is this code not working? - file reading"
date: 2011-01-01
forum: Programming Talk
---

### Post by hakermania on 2011-01-01
This code normally outputs the contents of a file, while numbering the lines!
This is the code
```
#include <stdio.h>

int main( int argc, char* argv[] ) {
if(argc<2){
printf("Usage: %s <filename>\n",argv[0]);
return 2;
}
if(argc>2){
printf("Please use only 1 filename\n");
return 2;
}
        printf("Trying to read %s \n",argv[1]);
        char c = '\n';
        int i = 1;
        scanf("%s",argv[1]);
        FILE * f = fopen(argv[1],"r");
        while (!feof(f)) {
                if (c == '\n')
                        printf("%d ",i++);
                c = fgetc(f);
                putchar(c);
        }
        fclose(f);
        return 0;
}
```Thx in advance for any reply!

---

### Post by MadCow108 on 2011-01-01
why are you reading data into argv[1]?
```

scanf("%s",argv[1]);

```

the loop is wrong, fgetc may arrive at end of stream and return EOF which can't be printed, do an infinite loop and break on an feof(f) after fgetc

line based (fgets, getline) instead of character based input would make this much simpler

---

