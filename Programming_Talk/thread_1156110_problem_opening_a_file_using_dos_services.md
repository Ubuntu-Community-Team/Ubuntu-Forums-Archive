---
title: "problem opening a file using dos services"
date: 2009-05-11
forum: Programming Talk
---

### Post by johnny_b_30 on 2009-05-11
I write a program in C but i have not the right to use the standard library. I want to open a file so i use an assembly procedure that i have write, open_file. Here is what i mean:
At C code part: int fp;
                    int open_file(char* filename);
                ....
                   fp = open_file(filename);

Assembly part: 
                 ....
 global open_file

    open_file:

         push bp
        mov bp,sp
        push bx
        push dx

        mov ah, 0x3d

        mov al, 0x00        ; read-only

        mov bx, [bp + 4]    ; file_name segment in DS

        mov ds, bx

        mov dx, [bp + 6]    ; file_name offset in DX

        int 0x21        ; open file




        jc open_error    ; if carry is set file could not open
        mov  handler, ax
        pop       dx
        pop        bx
        pop        bp
        ret        4

  open_error:

        mov ah,1
        pop dx
        pop bx
        pop bp

        ret        4



The problem is that when i execute my program, when it comes to the part of opening the file it aborts. What do you think is wrong? Other  functions that i wrote in such a way, for example function that prints a string or clear the monitor, works well. 

I would appreciate your help. Thanks a lot for your time

---

### Post by Zugzwang on 2009-05-11
[LIST]
[*]So you do run the program in a Dos environment and compile it using a DOS compiler and have made sure that your calling convention matches the compiler's/linker's calling convention?
[*]Then try a debugger and examine the register contents immediately before the call to interrupt 21h. Check if the address given is correct (by examining what it points to) and examine the result of the call. Check against your DOS function documentation that all registers are filled with the necessary information.
[/LIST]

---

### Post by johnny_b_30 on 2009-05-20
please if anyone knows assembly language , i would appreciate his/her help

---

