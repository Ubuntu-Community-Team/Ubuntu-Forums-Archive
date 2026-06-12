---
title: "General file I/O algorithm &amp; design question"
date: 2008-06-01
forum: Programming Talk
---

### Post by HunterSBuntu on 2008-06-01
I'm working on a program that will calculate the greatest common divisor of a series of pairs of numbers.

The requirements of the exercise are that the program reads the number pairs from an input file, and outputs the result to another file.

The low level implementation is not what I'm really pondering at the moment, more the bigger picture flow of the program.

What are your opinions on each of these two methods:

Option A
1 - Open input file
2 - Open output file
3 - Read number pair from input file
4 - Perform calculation
5 - Write result to output file
7 - If not at the last number pair return to step 3
8 - Close input & output files

Option B
1 - Open input file
2 - Read contents of input file into memory
3 - Close input file
4 - Perform calculation on every number pair and store every result in memory
5 - Open output file
6 - Write results data
7 - Close output file

I'm leaning more towards Option B, it just seems to be the more natural solution to me for some reason.  The downside I see to it is that if your input data file is enormous you need lots of memory to store it all rather than storing just the number pair currently being used as in Option A.

I realize that it probably won't make much difference either way as it isn't that complex a program but I'm trying to get in the habit of asking myself these higher level questions before rushing into coding.

What do you think?  What are the pros and cons on each?

---

### Post by slavik on 2008-06-01
The cons of both is that the program might be hard coded to open a specific file, which would be bad (make sure that the file names are given on command line). Once you do that, it doesn't really matter since input will be buffered (unless you want to buffer the stuff yourself).

---

### Post by HunterSBuntu on 2008-06-01
> **slavik said:**
> The cons of both is that the program might be hard coded to open a specific file, which would be bad (make sure that the file names are given on command line). Once you do that, it doesn't really matter since input will be buffered (unless you want to buffer the stuff yourself).

Yeah, it'll definitely be getting the filenames as command line arguments.  I just didn't include it in the pseudo code above cause it wasn't really the main focus of my question.

As for the buffering I'm not sure I understand what you mean in this context. 

The way I'm seeing it is that in Option A I'll read two integers from the input file stream into two integer variables, do the calculation 
on them, output the results to the output file and then read two more integers from file into the variables.

In Option B, I'd read all input data from the input file stream into an array or something before doing any of the processing.  Then I'd calculate all the results in one go withoug going back to the file for each pair. Thn write them all out.

Is that what you meant when you say 'buffer the stuff yourself'?  What would be the alternative to buffering it myself?  I think I may just be misunderstanding the terminology here.

---

### Post by ghostdog74 on 2008-06-01
If you have files in the GB range, use option A. If your files are small, use option B.

---

### Post by slavik on 2008-06-02
> **HunterSBuntu said:**
> Yeah, it'll definitely be getting the filenames as command line arguments.  I just didn't include it in the pseudo code above cause it wasn't really the main focus of my question.

As for the buffering I'm not sure I understand what you mean in this context. 

The way I'm seeing it is that in Option A I'll read two integers from the input file stream into two integer variables, do the calculation 
on them, output the results to the output file and then read two more integers from file into the variables.

In Option B, I'd read all input data from the input file stream into an array or something before doing any of the processing.  Then I'd calculate all the results in one go withoug going back to the file for each pair. Thn write them all out.

Is that what you meant when you say 'buffer the stuff yourself'?  What would be the alternative to buffering it myself?  I think I may just be misunderstanding the terminology here.
when you open a file and read 10 bytes, the filesystem will buffer a few megabytes of the file because it has to read large blocks of the file anyway. So when you read 10 bytes, a meg or two will get buffered into memory (think about reading in a megabyte at a time, but done automatically), so the next 10 bytes will be fast.

---

### Post by Can+~ on 2008-06-02
Option A+B: 
1. Open input file
2. Open output file
3. Read from input file to buffer (memory), until buffer is full, or file ends (if file ends finish = true).
4. Do calculation with buffer.
5. Write buffer to output, buffer clears.
6. If finish == false, go repeat 3.
7. Close input and output.

If filesize is lower than the file of the buffer, it will be equivalent to option B.

---

### Post by slavik on 2008-06-02
What Can is proposing is buffering the file yourself. IMO, I would let the system do it (if you are using C, you can control this).

---

### Post by Can+~ on 2008-06-02
> **slavik said:**
> What Can is proposing is buffering the file yourself. IMO, I would let the system do it (if you are using C, you can control this).

Not necessarily, I'm just talking about the algorithm. If the system already provides it (depending on the language), then the file can be opened and worked normally a la "option B".

---

### Post by ghostdog74 on 2008-06-02
if OP is outputting to just one file, there would be no need to declare output file handle. Let the shell do the outputting, using output redirection.

---

### Post by HunterSBuntu on 2008-06-02
> **ghostdog74 said:**
> if OP is outputting to just one file, there would be no need to declare output file handle. Let the shell do the outputting, using output redirection.

True.

That's actually what the author does originally in the text, the exercise is to modify that program to use C++ file I/O streams rather than piping output.

Basically, just to get familiar with how to use the standard library I/O stuff.  I didn't make that clear in the original post.

---

