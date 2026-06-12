---
title: "Linux assembly programming addition and multipication not getting output"
date: 2015-11-15
forum: Programming Talk
---

### Post by jovin555 on 2015-11-15
I am new to linux assembly language programming and am doing coding with basic addition and multiplication and getting wrong output.Following is my output
> 
jovin@jovin-desktop ~/Documents/Linuxasmpgm/examples/tute4 $ ./runme 
Give us a number:1
2nd number:2
3rd number:3
4th number:4
Sum of ints is 5
1x17 is 0
1-5x2is 0


The following is my code[main.cpp]
```

#include <iostream>

using namespace std;

extern "C" int AddInts(int a,int b,int c,int d);
extern "C" int MulBy17(int b);
extern "C" int Sub5x(int a,int b);

int main()
{
int a,b,c,d;
cout<<"Give us a number:";
cin>>a;
cout<<"2nd number:";
cin>>b;
cout<<"3rd number:";
cin>>c;
cout<<"4th number:";
cin>>d;

cout<<"Sum of ints is "<<AddInts(a,b,c,d)<<endl;
cout<<a<<"x17 is "<<MulBy17(b)<<endl;
cout<<a<<"-5x"<<b<<"is "<<Sub5x(a,b)<<endl;
cout<<endl;

return 0;
}
```

asm.asm
```

global AddInts        
global MulBy17        
global Sub5x        

section .text        
AddInts:        
    mov eax,edi
    add eax,esi
    add eax,ecx
    add eax,edx
    ret
MulBy17:
    imul edi,17
    mov  eax,edi
    ret
Sub5x:
    imul esi,5
    sub  edi,esi
    mov  eax,edi
    ret 


```

makefile
```

runme: main.cpp asm.o
    g++ main.cpp asm.o -o runme

asm.o: asm.asm
    nasm -f elf asm.asm -o asm.o

```

Can anyone let me know what is wrong with my coding?

---

### Post by DaviesX on 2015-11-15
Why do you assume a, b, c, d will be in the register? They should be in the stack if using __std_call. Maybe you should try this if you are in 32 bits platform:

```

mov eax, [esp + 4]
add eax, [esp + 8]
add eax, [esp + 12]
add eax, [esp + 16]
ret

```

---

### Post by jovin555 on 2015-11-15
> **DaviesX said:**
> Why do you assume a, b, c, d will be in the register? They should be in the stack if using __std_call. Maybe you should try this if you are in 32 bits platform:

```

mov eax, [esp + 4]
add eax, [esp + 8]
add eax, [esp + 12]
add eax, [esp + 16]
ret

```

I have tried as you mentioned and i got the correct output for the first case.but how can i solve the second and third case for multiplication and subtraction.?

I was watching a tutorial series and based on that i was doing the coding.The following is the link to the tutorial.Can you explain why in that tutorial the coding is the same as i have mentioned earlier and also getting the right output.The following is the link for the tutorial.

[https://www.youtube.com/watch?v=nDj35pMLBQE](https://www.youtube.com/watch?v=nDj35pMLBQE)

---

### Post by DaviesX on 2015-11-16
Great. I think this link will help: [http://stackoverflow.com/questions/3699283/what-is-stack-frame-in-assembly](http://stackoverflow.com/questions/3699283/what-is-stack-frame-in-assembly) (see the second answer).

When you call a function in C, the gcc will follow CDECL calling convention: parameters are pushed from right to left, so the leftmost parameter is the closest to esp while the rightmost parameter is the farthest.

The reason why the code in the video is different is because he was writing X64 assembly instead of X84. You can install a 64 bit Linux and code in X64 :)

---

