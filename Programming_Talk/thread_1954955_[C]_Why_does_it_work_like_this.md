---
title: "[C] Why does it work like this?"
date: 2012-04-09
forum: Programming Talk
---

### Post by t1497f35 on 2012-04-09
Hi,
I was toying around using "write()" instead of "printf()" to write a string directly to STDOUT_FILENO and STDERR_FILENO, however, I noticed that "write" prints the string "hi" to the console even if I write it to STDIN_FILENO! **Why**? Imho it shouldn't print out anything in this case.

```

#include <sys/stat.h>
#include <unistd.h>
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int main(int argc, char *argv[]) {
    
    const char *buf = "hi\n";
    ssize_t count = write(STDIN_FILENO, buf, strlen(buf));
    if(count < 0) {
        perror("Write");
    }
    exit(0);
}


```

---

### Post by GeneralZod on 2012-04-09
Writing to stdin is undefined behaviour, but the last answer here:

[http://stackoverflow.com/questions/7383803/writing-to-stdin-and-reading-from-stdout-unix-linux-c-programming](http://stackoverflow.com/questions/7383803/writing-to-stdin-and-reading-from-stdout-unix-linux-c-programming)

gives a plausible explanation of why this would happen in a UNIX-y console.

---

### Post by t1497f35 on 2012-04-09
Thanks, so I take it it's due to undefined behavior.

---

