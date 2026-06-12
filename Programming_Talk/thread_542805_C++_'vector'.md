---
title: "C++ 'vector'"
date: 2007-09-04
forum: Programming Talk
---

### Post by Mathiasdm on 2007-09-04
I'm sorry to ask this stupid question, but it's been a while since I've programmed on Linux. I'm trying to make a c++ program (I'm using the IDE Anjuta with Ubuntu Gutsy), but it seems as if the program doesn't recognise what a vector is.

I have this piece of code:
```

#include <vector>
#include "SudokuGrid.h"

```
The second line includes a self-written header file (obviously), but the problem is with the first line.

I get the following error:
```
SudokuGrid.c:22:18: error: vector: File or directory does not exist
```
(In case you're wondering why the line number is so high, it's because there's a license at the top of the file).

I probably forgot to install some synaptic package, but I just can't seem to figure out which one.
I have build-essential installed, by the way. I'll gladly provide any other information you guys/girls request ;)

---

### Post by Jessehk on 2007-09-04
My guess would be that you need to name your file with a C++ extension rather than a C one. That would be .cpp or .cxx rather than .c.

Another possibility is that your using gcc (which is specifically a C compiler), where you want to be using g++ (gcc, but compiles C++ files).

Other than that, I don't know but I'm sure other people can offer more ideas.

---

### Post by Mathiasdm on 2007-09-04
Oh my, that was really stupid of me. I normally always add the cpp extension, but Anjuta added the extension for me this time. Silly mistake, thanks for the help!

---

