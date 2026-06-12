---
title: "openfst - can't figure out the first few commands to start coding"
date: 2013-06-05
forum: Programming Talk
---

### Post by DreeDrunk on 2013-06-05
Hi there,

I am using the files from [http://www.openfst.org/twiki/bin/view/FST/WebHome](http://www.openfst.org/twiki/bin/view/FST/WebHome). Running on an Ubuntu 12.04 64bit system. I compile with ```
g++ -I/usr/local/include Example.cxx -L/usr/local/lib -lfst
``` to specify the libraries. I am trying something like the following with an example-file from [http://www.openfst.org/twiki/bin/view/FST/FstQuickTour#OperationExample](http://www.openfst.org/twiki/bin/view/FST/FstQuickTour#OperationExample): (the interesting thing are the first two lines for now)
```
#include <fst/fstlib.h>
using namespace fst;


// A vector FST is a general mutable FST 
StdVectorFst fst;

// Adds state 0 to the initially empty FST and make it the start state. 
fst.AddState();   // 1st state will be state 0 (returned by AddState) 
fst.SetStart(0);  // arg is state ID

// Adds two arcs exiting state 0.
// Arc constructor args: ilabel, olabel, weight, dest state ID. 
fst.AddArc(0, StdArc(1, 1, 0.5, 1));  // 1st arg is src state ID 
fst.AddArc(0, StdArc(2, 2, 1.5, 1)); 

// Adds state 1 and its arc. 
fst.AddState();
fst.AddArc(1, StdArc(3, 3, 2.5, 2));

// Adds state 2 and set its final weight. 
fst.AddState();
fst.SetFinal(2, 3.5);  // 1st arg is state ID, 2nd arg weight
```

Now I do not understand the error messages. Perhaps the problem isn't even openfst-specific?
Thanks in advance,
Greetings,
Dree

---

### Post by dwhitney67 on 2013-06-05
> **DreeDrunk said:**
> 
Now I do not understand the error messages. Perhaps the problem isn't even openfst-specific?
Thanks in advance,
Greetings,
Dree

It would be of immense help if you would post the error messages!

P.S.  Could the errors be related to the incomplete code that you have previously posted?  For example, the code lacks a main() function.

---

### Post by DreeDrunk on 2013-06-05
You're so right! Thanks for the patience.
The following code
```
#include <fst/fstlib.h>
using namespace fst;

int main ()

{
// A vector FST is a general mutable FST 
StdVectorFst fst;

// Adds state 0 to the initially empty FST and make it the start state. 
fst.AddState();   // 1st state will be state 0 (returned by AddState) 
fst.SetStart(0);  // arg is state ID

// Adds two arcs exiting state 0.
// Arc constructor args: ilabel, olabel, weight, dest state ID. 
fst.AddArc(0, StdArc(1, 1, 0.5, 1));  // 1st arg is src state ID 
fst.AddArc(0, StdArc(2, 2, 1.5, 1)); 

// Adds state 1 and its arc. 
fst.AddState();
fst.AddArc(1, StdArc(3, 3, 2.5, 2));

// Adds state 2 and set its final weight. 
fst.AddState();
fst.SetFinal(2, 3.5);  // 1st arg is state ID, 2nd arg weight

return 0;
}
```

produced the following error messages

```
dennis@DePeCe:~/Dokumente/OpenFST$ g++ -I/usr/local/include Example.cxx -L/usr/local/lib -lfst
/usr/local/lib/libfst.so: undefined reference to `dlerror'
/usr/local/lib/libfst.so: undefined reference to `dlopen'
collect2: ld gab 1 als Ende-Status zurück
```

I am german (and so is my system) so I have to translate the last line: "ld returned 1 as final status (or something like that)".

The lack of a main function was in my head already but I didn't see one program with these fst-thingy and so I wasn't sure if there is perhaps some special syntax that can replace a main function. But that was... crap, I think. Thanks again ;).

In case of my english being not as understandable as I hope, every word from a native speaker would be welcome :).

---

### Post by dwhitney67 on 2013-06-05
It's always a pleasure to solve simple problems.  It seems from your error posting that all you need to do is link with libdl.so (which contains the dynamic library loader software).

Try this:
```

g++ -I/usr/local/include Example.cxx -L/usr/local/lib -lfst **-ldl**

```
Note the -ldl at the end of the statement.

---

### Post by DreeDrunk on 2013-06-06
That solved the problem. Cool. ;).

The two statements ```
-lfst -ldl
``` did the job for me. The order is essential. I am not sure, why I have to specify the lib with '-lfst' but I don't have to specify the folder of the header or lib files.

EDIT In the meantime I looked into the README file... ummm. I won't say one more word about that... *shame*

---

