---
title: "Copying files one character at a time in C++"
date: 2009-02-19
forum: Programming Talk
---

### Post by kapok on 2009-02-19
i am writting a program in c++ to evaluate some data i got from a light sensor thing. (which includes coding the ability to find peaks in data; i'll do that later.) and i am a fairly new programmer.

i'm writing in C++ and have the following:

```
#include <iostream>
#include <fstream>
using namespace std;

int main()
{
char x ;
ifstream input ("./file_input.txt");
ofstream output ("./file_output.txt");

do
{
input >> x ;
output << x ;
} while ( input != '\0' );
}  
```

it works fine, except for one problem. it skips spaces. are spaces qualified as NULL in c++?
if they are, than how do i stop at the end of a file without stopping at every space?

oh and when i try 
> while ( input != '\0' && input != " " )
it tells me

no match for &#8216;operator!=&#8217; in &#8216;input != " "&#8217;

even though i used the '!=' sucesfully once already in the same line. >.>

---

### Post by Krupski on 2009-02-19
> **kapok said:**
> i am writting a program in c++ to evaluate some data i got from a light sensor thing. (which includes coding the ability to find peaks in data; i'll do that later.) and i am a fairly new programmer.

i'm writing in C++ and have the following:


Why not just use fgetc()?

---

### Post by kapok on 2009-02-19
hmm. i forgot about that.
thanks.

---

### Post by kapok on 2009-02-19
program is:
```

#include <iostream>
#include <fstream>
#include <cstdio>
using namespace std;

int main()
{
char x ;
ifstream input ("./file_input.txt");
ofstream output ("./file_output.txt");

do
{
x = fgetc( input );
output << x ;
} while ( input.eof() !=  1 );
}
```

error is:
> while_file.cc: In function ‘int main()’:
while_file.cc:14: error: invalid conversion from ‘void*’ to ‘FILE*’
while_file.cc:14: error:   initializing argument 1 of ‘int fgetc(FILE*)’


it says i convert it from a void pointer to a file pointer invalidly, but when i declare it as 'FILE *input ("file location")', it says "invalid conversion for char* for FILE*".
i'm very lost. 
and i'm feeling more like a noob with every second creeping by. :(

---

### Post by tneva82 on 2009-02-19
> **kapok said:**
> it says i convert it from a void pointer to a file pointer invalidly, but when i declare it as 'FILE *input ("file location")', it says "invalid conversion for char* for FILE*".
i'm very lost. 
and i'm feeling more like a noob with every second creeping by. :(

Try FILE *input=fopen("file location", "r");

---

### Post by eye208 on 2009-02-20
Do not mix C and C++ I/O functions. It looks ugly.

To keep the input stream from skipping whitespace, insert this:
```
input >> noskipws;
```
Also note that if you just want to copy the whole file, doing it one char at a time will be awfully slow. There's a better way:
```
#include <fstream>
using namespace std;

int main() {
        ifstream input("file_input.txt");
        ofstream output("file_output.txt");
        output << input.rdbuf();
        return 0;
}
```

---

### Post by uljanow on 2009-02-20
```
#include <algorithm>
#include <fstream>

int main() 
{
    std::ifstream in("./file_input.txt");
    std::ofstream out("./file_output.txt");
    std::copy(std::istreambuf_iterator<char>(in), std::istreambuf_iterator<char>(), std::ostreambuf_iterator<char>(out));
}
``` In C++ this can be done in just 3 lines.

---

### Post by kapok on 2009-02-21
=D

fantastic.
thanks to everyone.
but especially eye208 for the *.rdbuf() function.

---

