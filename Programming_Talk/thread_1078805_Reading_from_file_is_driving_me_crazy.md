---
title: "Reading from file is driving me crazy"
date: 2009-02-23
forum: Programming Talk
---

### Post by LasherHN on 2009-02-23
I'm trying to understand how reading from a file works, I'm trying the following code:

```
#include <cstdlib>
#include <cstdio>
#include <iostream>

using namespace std;

int main(int argc, char *argv[]){
   int *m,*n;
   m = (int*) malloc (sizeof(int));
   n = (int*) malloc (sizeof(int));
   FILE *infileptr;
   infileptr = fopen(argv[1], "r");
   fread(m, sizeof(int), 1, infileptr);
   fread(n, sizeof(int), 1, infileptr);
   cout<<*m<<"         "<<*n<<endl;
   
}
```

I'm compiling it with ```
g++ -o filetest filetest.cpp
```
then running it with ```
./filetest a.txt
```
a.txt has one line:
```
1 2
```

The output is:
```
171057201         0
```
something is clearly wrong :(

---

### Post by cabalas on 2009-02-23
The numbers in the file are stored as text each one being the ascii value for that specific character.  However when you are reading in from the file you are reading in an integers worth of bytes (which can vary between computers) in this case I think you are probably getting all the data on the first read and there being none left for the second read.

You do get the right output for the code you have, it just appears to not be the code you want.  Try reading the file in as strings and then converting it to integers.

---

### Post by LasherHN on 2009-02-23
That worked alright, it still bothers me a little that I have a file that I got from a text book that reads the numbers as ints from the beginning (but when I actually try to run it gives me a segmentation fault).

---

### Post by dwhitney67 on 2009-02-23
It appears that you are attempting basic file operations, hence the question that begs to be asked is... "Why are you using the C-library to open a file and read in data?"

```

#include <fstream>
#include <iostream>

int main(int argc, char** argv)
{
  int m = 0;
  int n = 0;
  std::fstream infile(argv[1], std::ios::in);

  infile >> m >> n;
  std::cout << m << ", " << n << std::endl;
}

```

---

