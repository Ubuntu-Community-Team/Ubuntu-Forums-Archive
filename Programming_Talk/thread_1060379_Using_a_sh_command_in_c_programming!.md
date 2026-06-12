---
title: "Using a sh command in c programming!"
date: 2009-02-04
forum: Programming Talk
---

### Post by Raven30 on 2009-02-04
I have a problem.  I am trying to program a sh command in c.  What I would like to do is:

[PHP]
#include "stdlib.h"

main() {
     int k = 0;
     int i = 1;

     while(k>4) {
          //gpspipe takes 7 lines of input and pastes them into $i.txt
          system("gpspipe -r -n 7 > $i.txt");
          k=k+1;
          i=i+1
     }
}[/PHP]

system() function call doesn't like the $ sign because it is in c.  It runs but doesn't see the $ sign as valid.  
Is there a way to increment the output file?  Any help is appreciated!

If I leave off the $ sign a file will be created but it will be written over when the loop comes back around.  
I need to have individual files that are incremented when it loops back around.  
I thought about using exec() with a script file, but I would need some way of reading in the last log file created 
and incrementing that one to create a new one. 
*shrugs*

---

### Post by snova on 2009-02-04
Use **sprintf**() to change the command before running it:

[PHP]
#include <stdio.h>
#include <string.h>

int main() {
    int i = 1;
    int k;
    for(k = 0; k < 4; k++, i++) {
        char buf[30];
        sprintf(buf, "gpspipe -r -n 7 > %i.txt", i);
        printf("%s\n", buf);
    }
    return 0;
}
[/PHP]

---

### Post by Raven30 on 2009-02-04
Thanks for the post snova.  That is exactly what I needed.  I added system(buf) to the code that you posted and it worked like a charm.  Thanks a million.

---

