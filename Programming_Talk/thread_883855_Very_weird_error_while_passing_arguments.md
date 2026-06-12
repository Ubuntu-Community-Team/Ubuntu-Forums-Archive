---
title: "Very weird error while passing arguments"
date: 2008-08-08
forum: Programming Talk
---

### Post by zarqoon on 2008-08-08
I've got a very strange problem.
In a complex c++ project i've got 2 simple functions like this:
```

void func2(double arg,bool arg2){
does something complex
}

void func1(double arg){
func2(arg,true)
}

```

They are both part of the same class.

Now i put a breakpoint into func2 and called it from the main program.
#0  func2 (this=0x828e7e0, 
    arg=2.0742346700585673e-312, arg2=74)
    at file.cc:869
#1  0xb7cd6ff6 in func1 (this=0x828e7e0, 
    arg=1.5707963705062866) at file.cc:865

The Value of arg in frame 1 is set by me. But the value in frame 0 changes randomly each time and looks uninitialised.
Valgrind does not throw any errors while calling the function.

I can not explain why this is happening. It used to work before there where major changes in many places of the Program so I do not know what I changed to make it behave that way.

---

### Post by Sporkman on 2008-08-09
Are the argument types of the function declarations consistent with those you list here in the main bodies?

---

### Post by Lux Perpetua on 2008-08-10
> **zarqoon said:**
> I've got a very strange problem.
In a complex c++ project i've got 2 simple functions like this:
```

void func2(double arg,bool arg2){
does something complex
}

void func1(double arg){
func2(arg,true)
}

```

They are both part of the same class.

Now i put a breakpoint into func2 and called it from the main program.
#0  func2 (this=0x828e7e0, 
    arg=2.0742346700585673e-312, arg2=74)
    at file.cc:869
#1  0xb7cd6ff6 in func1 (this=0x828e7e0, 
    arg=1.5707963705062866) at file.cc:865

The Value of arg in frame 1 is set by me. But the value in frame 0 changes randomly each time and looks uninitialised.
Valgrind does not throw any errors while calling the function.

I can not explain why this is happening. It used to work before there where major changes in many places of the Program so I do not know what I changed to make it behave that way.I think a buffer overflow in func2 could easily be responsible for this. That's all I can say without seeing code.

---

