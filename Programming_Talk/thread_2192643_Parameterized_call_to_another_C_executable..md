---
title: "Parameterized call to another C executable."
date: 2013-12-09
forum: Programming Talk
---

### Post by akshay-sulakhe on 2013-12-09
Hello Friends,
                  I am working on some code and I have a C function. It takes 4 parameters. Based on these 4 parameters I have to read a file. File reading is done separately. And depending upon the file read, I have to say 'yes' or 'no'. I better write some pseudo code now.. :P

function x(param1,param2,param3,param4){
         bool val = read_file(param1,param2,param3,param4);
if(val = true){ goto yes;}
else { goto false;}
}
Now as you can see, I want to take this whole read_file operation to another executable file. Just a C executable where I will use a different logic. I was thinking about using fork and exec, but i couldn't get it working. Plus like how to name the file and call from here, and return back the control here. So what I need is
1) Calling a C file, lets say foo.c or its executable(I don't know at this stage which one is possible)
2) How to call it
3) How to return.

I believe this is some tricky code I am trying to do. Kindly lend a hand. Thank you for your time.

---

### Post by ofnuts on 2013-12-09
No, this isn't tricky. This is just calling a function that is defined in another source file.

Typically:


[LIST]
[*]You declare the function in  a header file (readfile.h) 
[*]You include that header:file:
[LIST]
[*] in the source file for the function (readfile.c) (so that any mismatch between the function declaration and its implementation are flagged by the compiler) 
[*]in the source file of any code that calls it 
[/LIST]
  
[*]You get all the code in one executable, in the simple cases you just need to specify both C source files in the same GCC command: 
[/LIST]
```
gcc -o program main.c readfile.c
```

---

### Post by akshay-sulakhe on 2013-12-09
Thank you very much. Will surely Try it. Anyway that can be done without involving the header file and linking the C file.

---

### Post by ofnuts on 2013-12-09
> **akshay-sulakhe said:**
> Thank you very much. Will surely Try it. Anyway that can be done without involving the header file and linking the C file.

That's the easiest way... unless you want to read the file in a separate process, but this isn't going to be any simpler. This separate process with still have to implement the whole readfile function, and your main process will have to use the [fork/exec ritual]("http://www.yolinux.com/TUTORIALS/ForkExecProcesses.html") to start the process that reads the file. But this opens a can of worms:

[LIST]
[*]locating the subprocess executable
[*]dealing with errors when starting the subprocess (executable not here, or no permission)
[*]dealing with errors when the file to read doesn't exist
[/LIST]

---

