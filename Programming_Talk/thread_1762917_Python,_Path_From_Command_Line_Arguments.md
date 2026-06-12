---
title: "Python, Path From Command Line Arguments"
date: 2011-05-19
forum: Programming Talk
---

### Post by cgroza on 2011-05-19
Hello, 
I am developing a program right now and I need it to take arguments from command line which are some file system paths.

I take the arguments, but the provided path argument must be always absolute (starting from the root of the file system), so many times, if I give it a relative path, my program complains it cannot find the file.

Is there a way to handle file path arguments from command line in Python?

Thank you.

---

### Post by StephenF on 2011-05-19
Some pointers.

os.getcwd()
os.path.join()
os.path.realpath()

---

### Post by cgroza on 2011-05-19
Thank you. I will take a look at them.

---

