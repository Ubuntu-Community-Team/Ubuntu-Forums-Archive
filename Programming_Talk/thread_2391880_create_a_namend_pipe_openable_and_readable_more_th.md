---
title: "create a namend pipe openable and readable more than once"
date: 2018-05-14
forum: Programming Talk
---

### Post by lucio-messina-w on 2018-05-14
**Short question:**
  I have a program that takes in input a file name, opens it and reads  the whole content line by line. When it finishes, it reopens the same  file, and reads it from the scratch again. This happens five or six  times. How can I pass a named pipe to this program, instead of a file name?


  **Long question, with detailed examples and explanations:**

  Here is a stupid minimal example of how that program looks like (file  math.py); it computes the sum and the product of the numbers read from  the input file:

  ```

import sys

if __name__ == "__main__":

    fname = sys.argv[1]
    print ("This is math.py the input file is {}".format(fname))

    fin = open (fname)
    print ("I opened the input file: I'm about reading it line by line for the first time")

    total = 0
    count = 0
    for line in fin:
        total += int(line)
        count += 1

    print ("Finished! The sum of all the {} lines is {}".format(count, total))

    fin = open (fname)
    print ("I opened the input file again: I'm about reading it line by line for the second time")

    product = 1
    count = 0
    for line in fin:
        product *= int(line)
        count += 1

    print ("Finished! The product of all the {} lines is {}".format(count, product))  
```

For many reason, I don't want or I'm not able to modify this program. Here is an example input (file numbers.txt):

  ```

142
375
9577
35
609
7657
963
6324
921
323

```
  It works fine when I pass numbers.txt as input for math.py:

  ```

$ python math.py numbers.txt 
This is math.py the input file is numbers.txt
I opened the input file: I'm about reading it line by line for the first time
Finished! The sum of all the 10 lines is 26926
I opened the input file again: I'm about reading it line by line for the second time
Finished! The product of all the 10 lines is 150790292803437566279613795000  
```


Now, let's suppose I don't have a single file containing the whole  input for math.py I have another program (this one written by me) that  does some computations and then writes a valid input for math.py This is a minimal example (file double.py); it reads some numbers from  stdin and writes their double on stdout:

  ```

import sys

if __name__ == "__main__":

    for line in sys.stdin:
        print (int(line)*2)  
```
I know how to pass the output of double.py as input to math.py in BASH (using a named pipe instead of the filename):

  
```

$ python math.py <(python double.py <numbers.txt)
This is math.py the input file is /dev/fd/63
I opened the input file: I'm about reading it line by line for the first time
Finished! The sum of all the 10 lines is 53852
I opened the input file again: I'm about reading it line by line for the second time
Finished! The product of all the 0 lines is 1  
```
This usually works fine if math.py opens the input file only once.  But if reopens the named pipe again ( in this example /dev/fd/63 ) it  found it empty, as you can see from the last output line.

  So, the question is: can I pass to math.py "something" that can be  opened more than once, and every time produces the same output  (re-executing the code of double.py if necessary)? The solution can use other programming languages other than python and  bash.

  Thank you a lot in advance, I hope the problem is clear. Please don't answer me something like "you can rewrite math.py such  that..." because my goal is not to modify math.py (this is just a stupid  example, the real programs are bigger). I also don't want to write the output of double.py on the disk.

---

### Post by Rocket2DMn on 2018-05-16
Since you haven't received a response, I'll take a stab at this.  AFAIK, what you're asking for violates the concept of a pipe, so that's not the tool you're looking for.  If the math.py script really does re-open the input, then you will have to use a "file."  If it's really just looping over the input twice, you could have the source (e.g., double.py) just produce the output twice, but I gather this isn't what you want.  The reason I put "file" in quotes is because a file is just an abstraction - it doesn't actually have to live on your hard disk.  You might consider using an in-memory file, like one on a tmpfs filesystem.

So for example you can create a temporary file system:
```

mount -t tmpfs -o size=128m tmpfs /mountpoint

```
Also consider that some users choose to use /tmp as a true tmpfs filesystem.

Then you redirect the output of double.py to a file somewhere on /mountpoint and you can read it as many times as you want.  Note that this data will be lost when you reboot the system though.

---

