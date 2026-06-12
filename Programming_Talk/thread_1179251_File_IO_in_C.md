---
title: "File I/O in C"
date: 2009-06-05
forum: Programming Talk
---

### Post by Mirge on 2009-06-05
```

#include <stdio.h>
#include <stdlib.h>
#include <ctype.h> // for isspace()
#include <string.h> // for strlen()

void rtrim(char *str);

int main(int argc, char *argv[]) {
    FILE *fp;
    char buf[257]; // 256 + '\0'
    char filename[26]; // 25 + '\0'

    printf("Enter a filename to read: ");
    fgets(filename, 25, stdin);
    rtrim(filename);

    if((fp = fopen(filename, "r")) == NULL) {
        fprintf(stderr, "Error opening %s for reading.", filename);
        exit(1);
    }

    // Lets read the file.
    while(!feof(fp)) {
        fgets(buf, 256, fp);
        printf("%s", buf);
    }

    fclose(fp);
    return 0;        
}

void rtrim(char *str) {
    int i = 0;
    
    for(i = strlen(str); i >= 0; i--) {
        if(isspace(str[i]) || str[i] == '\n' || str[i] == '\r' || str[i] == '\0') {
            str[i] = '\0';
        } else {
            break;
        }
    }
}

```rtrim() is just something I threw together quick. it's probably not efficient, but it works lol.

Whenever I run the script & read in a file (example: file1.c--the above code).. it always prints an extra character of whatever the last char was, in this case a closing brace }.

Any idea why?

---

### Post by MadCow108 on 2009-06-05
check if fgets is successful:
if (fgets(...) != NULL) printf(...);

otherwise it prints also when fgets fails because it reaches eof.
In that case it prints the last buffer again as it doesn't get overwritten.

this would also do it:
```
while(fgets(buf, 256, fp) != NULL) {
        printf("%s", buf);
    }
if (!feof(fp)) printf("error before eof");
```

---

### Post by Mirge on 2009-06-05
> **MadCow108 said:**
> check if fgets is successful:
if (fgets(...) != NULL) printf(...);

otherwise it prints also if fgets fails, in that case it prints the last buffer.

Bingo :) Thanks a bunch!

---

### Post by dwhitney67 on 2009-06-05
The basic thing to remember is that the EOF flag within the FILE will not be set until you perform a read and there is no more data to be read.

In your example program, with the final line was read (successfully), that contains the curly bracket, technically the EOF had not been reached yet.  Only when you iterated again to perform another fgets() did the EOF flag get set.

---

### Post by Mirge on 2009-06-05
Makes sense, thanks for explaining that :)

---

