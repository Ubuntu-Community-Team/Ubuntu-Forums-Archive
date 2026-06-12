---
title: "istream::getline segmentation fault (x86-64)"
date: 2008-12-20
forum: Packaging and Compiling Programs
---

### Post by Dr. Kylstein on 2008-12-20
The following code consistently results in a segfault. Removing the getline statement removes the error.
```

#include <iostream>
#include <fstream>

int main(int argc, char **argv) {
    std::ifstream stream;
    stream.open("ayb2.txt");
    char* line;
    stream.getline(line, 256);
    stream.close();
    return 0;
}

```

---

### Post by lensman3 on 2008-12-21
> **Dr. Kylstein said:**
> The following code consistently results in a segfault. Removing the getline statement removes the error.
```

#include <iostream>
#include <fstream>

int main(int argc, char **argv) {
    std::ifstream stream;
    stream.open("ayb2.txt");
//    char* line;

You need to allocate memory for line.  char* line; just indicates that it will be pointer to the line but no memory is allocated for the data. Since the next line reads 256 bytes of char memory, then you need to allocate at least 257 bytes (+1 for end of string /0).
    

    stream.getline(line, 256);
    stream.close();
    return 0;
}

```

You need to allocate memory for line.  char* line; just indicates that it will be pointer to the line but no memory is allocated for the data. Since the next line reads 256 bytes of char memory, then you need to allocate at least 257 bytes (+1 for end of string /0).

---

### Post by Dr. Kylstein on 2008-12-22
I didn't realize I was that out of touch. I'm glad it it's me and not the libraries.

---

