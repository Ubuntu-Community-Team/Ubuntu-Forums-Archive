---
title: "An attempt to make a compression program"
date: 2008-03-15
forum: Programming Talk
---

### Post by WarMonkey on 2008-03-15
What I was trying to do was make a program that changes "helllo" to "he3lo" or "ggggggggg" to "9g". I can get it to work by printing the out put on the screen; with I/O for files, it sort of works, but I have two problems:

1) If test.txt (the input file) is hello, text.txt (the output file) is:
```

he2lo
6

```

2) If test .txt is "fffffffffffffffffffffffffffffffffffffffffffff", text.txt is blank.

Here is my code (please don't laugh :)):
```
#include <iostream>
#include <fstream>
#include <sstream>

using namespace std;

int main(){
char * input;
long size;
ifstream infile ("test.txt",ifstream::binary);
ofstream outfile ("text.txt");
infile.seekg(0,ifstream::end);
size=infile.tellg();
infile.seekg(0);
cout << size;
int a=1;
string c;
char firstarray[2];
int n=-1;

std::ostringstream stm;


char compress[] = { 'H', 'e', 'l', 'l','l', 'o', '\0' };
input = new char [size];
infile.read (input,size);

cout << input;
infile.close();
//engine
while (n<size) {
n++;
while (input[n]==input[n+a]){
a++;
}
if (input[n]==input[n+a-1]){
if (a>1){

cout << a;
stm << a;
std::cout << stm.str();
c=stm.str();
cout << c;
sprintf( firstarray,"%d", a);
outfile.put (firstarray[0]);

}
}
if (input[n]!=input[n+1]){

cout << input[n];

outfile.put (input[n]);
}

}
cout << "\n";

}
```

If you see anyway I can fix one of the two problems, or if you see any way to simplify the code, please tell me what I should do. Thanks.

---

### Post by lloyd_b on 2008-03-15
Ouch - my head hurts :)

Okay, some suggestions. One major problem you have is that you are only initializing "a" to 1 at the start of the program - you really need to initialize it inside of the while() loop (otherwise, it'll go buggy if there's more than one set of duplicate letters).

Second - Here's a quick-n-dirty rewrite of the main loop.  Note: this requires "n" to be initialized to 0, rather than -1:
```


   int n = 0;

   ...
   ...
   ...

// engine.
 while (n < size) {
                a = 1;  // Initialize the "dup counter"

                // count duplicates (if any)
                while (input[n] == input[n + a]) {
                        a++;
                }

                // if dups, then output the number, followed by the letter
                if (a > 1) {
                        cout << a;
                        cout << input[n];
                } else
                        cout << input[n];  // Otherwise, just output the letter
                n += a;  // Advance "n" to the first non-matching letter

   }
   cout << "\n";
```

I left out your output file handling, and a section who's purpose I simply didn't understand.  Here's what I get for output:
```
lloyd@laptop:~/stuff$ cat test.txt
aaabbdddddddddddfjgzzzzzzzzzz
lloyd@laptop:~/stuff$ ./comp
30aaabbdddddddddddfjgzzzzzzzzzz
3a2b11dfjg10z
```
and
```
lloyd@laptop:~/stuff$ cat test.txt
jjjjjjjjjjjjjjj
lloyd@laptop:~/stuff$ ./comp
16jjjjjjjjjjjjjjj
15j
```

Is this more or less what you were looking for?

---

### Post by WarMonkey on 2008-03-15
Thanks for the re-write.

I forgot to take the cout's out. Just ignore them, I was trying to see where I had gone wrong.

---

### Post by mssever on 2008-03-15
What happens if your input file contains digits? :-k

---

### Post by WarMonkey on 2008-03-15
> **mssever said:**
> What happens if your input file contains digits? :-k

I was just thinking about that. Maybe "&*(8)*&"="8"? But that wouldn't really help save memory.

---

### Post by mssever on 2008-03-15
You could escape the digit (aa3333445 => 2a4\32\4\5), but a compression algorithm should probably result in a binary file and factor out larger patterns, too (abcabcabc).

---

### Post by Wybiral on 2008-03-15
> **mssever said:**
> You could escape the digit (aa3333445 => 2a4\32\4\5), but a compression algorithm should probably result in a binary file and factor out larger patterns, too (abcabcabc).

Yes. In fact, you should just use [Huffman]("http://en.wikipedia.org/wiki/Huffman_coding").

---

### Post by Fbot1 on 2008-03-15
If you are really interested in this, you should have a look at this: [http://www.cs.fit.edu/~mmahoney/compression/](http://www.cs.fit.edu/~mmahoney/compression/).

---

### Post by WarMonkey on 2008-03-17
I get this message...

```

main2.cpp: In function &#8216;int main()&#8217;:
main2.cpp:44: error: invalid conversion from &#8216;char*&#8217; to &#8216;char&#8217;
main2.cpp:44: error:   initializing argument 1 of &#8216;std::basic_ostream<_CharT, _Traits>& std::basic_ostream<_CharT, _Traits>::put(_CharT) [with _CharT = char, _Traits = std::char_traits<char>]&#8217;

```

...when 
```

#include <iostream>
#include <fstream>
#include <sstream>

using namespace std;

int main(){
char * input;
long size;
ifstream infile ("test.txt",ifstream::binary);
ofstream outfile ("text.txt");
infile.seekg(0,ifstream::end);
size=infile.tellg();
infile.seekg(0);
cout << size;
int a=1;
string c;
char firstarray[]= { '0', '0', '0', '0','0', '0', '0' };
int n=0;

std::ostringstream stm;


char compress[] = { 'H', 'e', 'l', 'l','l', 'o', '\0' };
input = new char [size];
infile.read (input,size);

cout << input;
infile.close();
// engine.
 while (n < size) {
                a = 1;  // Initialize the "dup counter"

                // count duplicates (if any)
                while (input[n] == input[n + a]) {
                        a++;
                }

                // if dups, then output the number, followed by the letter
                if (a > 1) {
                        
			sprintf( firstarray,"%d", a);
			cout << a;
			[COLOR="Red"]outfile.put (firstarray);[/COLOR]
                        cout << input[n];

                } else
                        cout << input[n];  // Otherwise, just output the letter
		outfile.put (input[n]);
                n += a;  // Advance "n" to the first non-matching letter

   }
   cout << "\n";

}
```

but when the code is like:

```
#include <iostream>
#include <fstream>
#include <sstream>

using namespace std;

int main(){
char * input;
long size;
ifstream infile ("test.txt",ifstream::binary);
ofstream outfile ("text.txt");
infile.seekg(0,ifstream::end);
size=infile.tellg();
infile.seekg(0);
cout << size;
int a=1;
string c;
char firstarray[]= { '0', '0', '0', '0','0', '0', '0' };
int n=0;

std::ostringstream stm;


char compress[] = { 'H', 'e', 'l', 'l','l', 'o', '\0' };
input = new char [size];
infile.read (input,size);

cout << input;
infile.close();
// engine.
 while (n < size) {
                a = 1;  // Initialize the "dup counter"

                // count duplicates (if any)
                while (input[n] == input[n + a]) {
                        a++;
                }

                // if dups, then output the number, followed by the letter
                if (a > 1) {
                        
			sprintf( firstarray,"%d", a);
			cout << a;
			[COLOR="Red"]outfile.put (firstarray[0]);[/COLOR]
                        cout << input[n];

                } else
                        cout << input[n];  // Otherwise, just output the letter
		outfile.put (input[n]);
                n += a;  // Advance "n" to the first non-matching letter

   }
   cout << "\n";

}
```

I get no errors. How would I get around this? I am trying to get the whole character sequence written to "text.txt" but it won't let me.

Also there are some unneeded things in the code, just ignore them. What is important is the red text.

---

### Post by mssever on 2008-03-17
I know very little C++, but it looks like you're trying to cast an array to a string, which I'm guessing must be done explicitly.

C++ does support strings. Is there a reason you're using a char array instead?

---

### Post by Sockerdrickan on 2008-03-17
try &firstarray[0] or *firstarray

---

### Post by Fbot1 on 2008-03-17
I got " error: invalid conversion from `char*' to `char' ". Do you have it set up so you can see the error messages?

---

### Post by Sockerdrickan on 2008-03-17
What's the output supposed to be? I'm getting 0 with this modified code
```
#include <iostream>
#include <fstream>
#include <sstream>

using namespace std;

int main(){
char * input;
long size;
ifstream infile ("test.txt",ifstream::binary);
ofstream outfile ("text.txt");
infile.seekg(0,ifstream::end);
size=infile.tellg();
size+=1;
infile.seekg(0);
cout << size;
int a=1;
string c;
char firstarray[]= { '0', '0', '0', '0','0', '0', '0' };
int n=0;

std::ostringstream stm;


char compress[] = { 'H', 'e', 'l', 'l','l', 'o', '\0' };
input = new char [size];
infile.read (input,size);

cout << input;
infile.close();
// engine.
 while (n < size) {
                a = 1;  // Initialize the "dup counter"

                // count duplicates (if any)
                while (input[n] == input[n + a]) {
                        a++;
                }

                // if dups, then output the number, followed by the letter
                if (a > 1) {
                        
			sprintf( firstarray,"%d", a);
			cout << a;
			outfile.put (*firstarray);
                        cout << input[n];

                } else
                        cout << input[n];  // Otherwise, just output the letter
		outfile.put (input[n]);
                n += a;  // Advance "n" to the first non-matching letter

   }
   cout << "\n";

}

```

---

### Post by WarMonkey on 2008-03-17
> **Tux0r said:**
> What's the output supposed to be? I'm getting 0 with this modified code


text.txt is supposed to be:
```

2eted4cd[COLOR="Red"]42[/COLOR]t

```

if test.txt is

```

eetedccccdtttttttttttttttttttttttttttttttttttttttttt

```

however, I get this for text.txt instead:

```

2eted4cd[COLOR="Red"]4[/COLOR]t

```


In other words, the second output line of the terminal:
```
itzchak@warmonkey:~/Documents/Code/C++/Compressor$ ./a.out
52eetedccccdtttttttttttttttttttttttttttttttttttttttttt
[COLOR="Red"]2eted4cd42t[/COLOR]
```

Is what I want text.txt to be.

---

### Post by supirman on 2008-03-17
don't use outfile.put(), as put take a single char.

Also, you don't need the sprintf, just use 'a' directly.
instead, use 

[PHP]outfile << a;[/PHP]

---

### Post by Fbot1 on 2008-03-17
Almost forgot, C has something called the "null" character that ends the string so you don't need to know the size. So I'd suggest using "while(input[n] != 0)" instead.

---

### Post by supirman on 2008-03-18
There are quite a few other ways to clean the code up, but there is one major thing you need to fix.

[PHP]input = new char [size];[/PHP]

When you 'new' something, you must 'delete' it.

---

