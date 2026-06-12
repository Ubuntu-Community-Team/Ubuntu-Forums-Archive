---
title: "Function to execute a binary incase of code."
date: 2013-01-15
forum: Programming Talk
---

### Post by akshay.sulakhe on 2013-01-15
Hello friends,  
             I am working currently in C programming. For some reasons, in the code, i have to give a path to the binary(executable), which can be directly used instead of any code. 
For eg :-
if(condition_satisfied){
execve'absolute_path_to_executable_file'
}
 With this, it should execute this binary file. Is this possible? If yes, Kindly let me know. Thank you for your time.  :-) ):P

---

### Post by PaulM1985 on 2013-01-15
I think you can use the exec() function for this.

Paul

---

### Post by rnerwein on 2013-01-15
> **akshay.sulakhe said:**
> Hello friends,  
             I am working currently in C programming. For some reasons, in the code, i have to give a path to the binary(executable), which can be directly used instead of any code. 
For eg :-
if(condition_satisfied){
execve'absolute_path_to_executable_file'
}
 With this, it should execute this binary file. Is this possible? If yes, Kindly let me know. Thank you for your time.  :-) ):P
hi
you can use any kind of exec calls  try: man -k exec to see the different calls. i am sure one of the will satisfy your claim. the normal exec is ok too.
ciao

---

### Post by Bachstelze on 2013-01-15
> **akshay.sulakhe said:**
> 
 With this, it should execute this binary file. Is this possible?

You have the code written, how about you try it and find out?

---

### Post by jwbrase on 2013-01-17
Keep in mind that if you just use exec(), your program will be replaced by the program you exec(), so any code after the exec() in your program won't get executed.

For example:

```


foo=bar;

if(condition)
{
    exec(program);
}

foo=baz; //If "condition" is true, you'll never get to this line. 


```

---

