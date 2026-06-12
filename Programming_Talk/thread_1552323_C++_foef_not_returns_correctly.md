---
title: "C++ foef not returns correctly"
date: 2010-08-13
forum: Programming Talk
---

### Post by ras123 on 2010-08-13
Hi,
```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <string.h>
#include <string>

lines()
{
    int currentLine;
    char line[1024];
    //string str;
    FILE *stream = fopen("file.txt", "r");    // Open file read only
    if(!stream)
        return FILE_OERR;                   // File open error
    currentLine = 0;
    while(!feof(stream))
    {
        fgets(line, sizeof(line), stream);  // Read a line
        currentLine++;
    }
    return currentLine;
}
```This function returns 7, instead of 6 (no of lines in the file.txt - attached with this), Why ? On debugging, I found that lines array, get two times (6th and 7th looping) the last line of file!!
Please let me know the error

Thanking You
Ras

---

### Post by Bachstelze on 2010-08-13
What happens is that when your program reads the last line of the file, because it stops reading when it meets the newline, it does not know that there is nothing after it. Therefore, it will happily store it into your string, and continue reading, without setting the end-of-file indicator that is used by feof. Only on the next iteration will it see that it has reached the end of the file, and set the indicator accordingly.

---

### Post by dwhitney67 on 2010-08-13
The code is C, not C++.

The cleaner solution, in C, is to use the return value of fgets() within the while-loop's conditional.  For example:
```

...

while(fgets(line, sizeof(line), stream))
{
   ++currentLine;
}

...

```



P.S.  In C++, you could include <fstream> and <string>.

```

#include <fstream>
#include <string>

int lines()
{
   std::fstream stream("file.txt", std::ios::in);

   if (stream)
   {
      int numLines = 0;
      std::string line;

      while (std::getline(stream, line))
      {
         ++numLines;
      }

      return numLines;
   }

   return FILE_OERR;
}

```

---

