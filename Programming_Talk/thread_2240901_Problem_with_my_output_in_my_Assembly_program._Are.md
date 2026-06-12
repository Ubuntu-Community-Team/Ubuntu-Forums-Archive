---
title: "Problem with my output in my Assembly program. Area of a Trapezoid."
date: 2014-08-22
forum: Programming Talk
---

### Post by Sina_Amini on 2014-08-22
I'm writing a program that lets the user input the height of a trapezoid and the length of its bases. (top and bottom base)

The program runs fine and gives me the correct outputs accept for the actual numbers. 

[FONT=arial][FONT=arial]**HERE'S THE RUNNING PROGRAM**[/FONT][/FONT]
[FONT=arial]This program is brought to you by Sina Amini [/FONT]
[FONT=arial]Welcome to Areas of Trapezoids[/FONT]
[FONT=arial]Please enter one of the base numbers: 5.8[/FONT]
[FONT=arial]Please enter the other base number: 2.2[/FONT]
[FONT=arial]Please enter the height: 6.5[/FONT]
[FONT=arial]_The area of a trapezoid with sizes 6.500000000000000000, 0.000000000000000000, and 6.500000000000000000 is 6.500000553505093315_[/FONT]
[FONT=arial]Have a nice day. Enjoy your trapezoids.  [/FONT]
[FONT=arial]The return code received by the driver is 3.250000276752546657.  Bye.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]Everything is working fine accept for the underlined sentence. Its supposed to repeat the entered numbers in order (5.8, 2.2, 6.5, and the area). The 3rd number is correct (6.5) as well as the driver code (3.25) but the others are not.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]I'm not sure if it has to do with how I'm doing the math, how I'm passing the numbers, or how its being outputted. 

Here's a part of my program. I can include more of the program but I think this is the only part that matters as far as my issue goes. If you need anymore information I will gladly provide it. [/FONT]

```
;=========== Show the initial message =====================================================================================================================================

mov qword  rax, 0                                           ;No data from SSE will be printed
mov        rdi, stringformat                                ;"%s"
mov        rsi, initialmessage                              ;"Welcome to Areas of Trapezoids"
call       printf                                           ;Call a library function to make the output




;=========== Prompt floating point number for first base ==================================================================================================================


mov qword  rax, 0                                           ;No data from SSE will be printed
mov        rdi, stringformat                                ;"%s"
mov        rsi, promptmessage1                              ;"Please enter one of the base numbers: "
call       printf                                           ;Call a library function to make the output




;===== Obtain a floating point number from the standard input device and store a copy in xmm0 =============================================================================


push qword 0                                                ;Reserve 8 bytes of storage for the incoming number
mov qword  rax, 0                                           ;SSE is not involved in this scanf operation
mov        rdi, eight_byte_format                           ;"%lf"
mov        rsi, rsp                                         ;Give scanf a point to the reserved storage
call       scanf                                            ;Call a library function to do the input work
movsd      xmm0, [rsp]                                      ;Copy the inputted number to xmm0
pop        rax                                              ;Make free the storage that was used by scanf


;=========== Prompt floating point number for second base =================================================================================================================


mov qword  rax, 0                                           ;No data from SSE will be printed
mov        rdi, stringformat                                ;"%s"
mov        rsi, promptmessage2                              ;"Please enter the other base number: "
call       printf                                           ;Call a library function to make the output




;===== Obtain a floating point number from the standard input device and store a copy in xmm1 =============================================================================


push qword 0                                                ;Reserve 8 bytes of storage for the incoming number
mov qword  rax, 0                                           ;SSE is not involved in this scanf operation
mov        rdi, eight_byte_format                           ;"%lf"
mov        rsi, rsp                                         ;Give scanf a point to the reserved storage
call       scanf                                            ;Call a library function to do the input work
movsd      xmm1, [rsp]                                      ;Copy the inputted number to xmm1
pop        rax                                              ;Make free the storage that was used by scanf


;=========== Prompt floating point number for height ======================================================================================================================


mov qword  rax, 0                                           ;No data from SSE will be printed
mov        rdi, stringformat                                ;"%s"
mov        rsi, promptmessageheight                         ;"Please enter the height: "
call       printf                                           ;Call a library function to make the output


;===== Obtain a floating point number from the standard input device and store a copy in xmm2 =============================================================================


push qword 0                                                ;Reserve 8 bytes of storage for the incoming number
mov qword  rax, 0                                           ;SSE is not involved in this scanf operation
mov        rdi, eight_byte_format                           ;"%lf"
mov        rsi, rsp                                         ;Give scanf a point to the reserved storage
call       scanf                                            ;Call a library function to do the input work
movsd      xmm2, [rsp]                                      ;Copy the inputted number to xmm2
pop        rax  


;===== Add the 2 base numbers together ===================================================================================================================================


movsd        xmm3, xmm0                                       ;There are 2 copies of the first base: xmm0 and xmm3
movsd      xmm4, xmm1                            ;There are 2 copies of the second base: xmm1 and xmm4 
addss      xmm3, xmm4                                       ;Adds the copy xmm4 to the copy xmm3
movsd      xmm5, xmm3                                       ;Stores the new value of xmm3 in xmm5


;===== Divide the sum of both bases by a constant =========================================================================================================================


mov        rbx, 0x4000000000000000                          ;Constant 0x4000000000000000 = 2.0 (decimal).  
push       rbx                                              ;Place the constant on the integer stack
divsd      xmm5, [rsp]                                      ;Divide the sum of both bases by the constant
movsd      xmm6, [rsp]                                      ;Copy the divisor to xmm6
pop        rax                                              ;Discard the divisor from the integer stack


;===== Save a copy of the quotient before calling printf ==================================================================================================================


push       qword 0                                          ;Reserve 8 bytes of storage
movsd      [rsp], xmm5                                      ;Place a backup copy of the quotient in the reserved storage


;===== Multiply the quotient by the height ================================================================================================================================


mulsd      xmm5, xmm2                                       ;Multiplies the sum of both bases by the height
movsd      xmm7, xmm5                                       ;Copy the outcome to xmm7


;===== Show the outcome ===================================================================================================================================================


mov        rax, 4                                           ;4 floating point numbers will be outputted
mov        rdi, outputmessage                               ;"The area of a trapezoid with sizes %1.18lf, %1.18lf, and %1.18lf is %1.18lf"
call       printf                                           ;Call a library function to do the hard work




;===== Conclusion message =================================================================================================================================================


mov qword  rax, 0                                           ;No data from SSE will be printed
mov        rdi, stringformat                                ;"%s"
mov        rsi, goodbye                                     ;"Have a nice day. Enjoy your trapezoids."
call       printf                                           ;Call a library function to do the hard work.




;===== Retrieve a copy of the quotient that was backed up earlier =========================================================================================================


pop        r14                                              ;A copy of the quotient is in r14 (temporary storage)


;Now the stack is in the same state as when the application area was entered.  It is safe to leave this application area.



```

---

### Post by trent.josephsen on 2014-08-23
The thing that jumps out at me immediately is that you're using **addss** with **double**-precision floats, which might partially explain the area being wrong.

Also IIRC %lf is the wrong printf format for a double. For [hysterical raisins]("http://c-faq.com/varargs/promos.html"), it's not possible to pass a "C float" (single-precision floating-point number) to printf, because in C such an argument is always promoted to double; so %f works for floats and doubles and %lf is meaningless. I believe some libraries do permit it, though. I don't know whether that's the case for you. This *only applies to printf, not scanf*, because scanf takes pointer arguments, to which the default argument promotions do not apply. [Reference](http://c-faq.com/stdio/scanfvsprintf.html)

*Edit:* I didn't mean to respond to a question about assembly with two links about C. The points I was trying to make are:
1) Don't use addss with doubles.
2) Use %f with printf to print doubles, not %lf. But use %lf, not %f, to read doubles with scanf.

Hope this helps a little.

---

### Post by ofnuts on 2014-08-24
My assembler is rusty and I never used it on Unix. But I wonder how your printf is finding the numbers to format, I don't see anything in your code making me think that printf received its data arguments. The first good number could be a coincidence.

---

### Post by trent.josephsen on 2014-08-24
That was my first thought, too, but the [ABI](http://x86-64.org/documentation/abi.pdf) says that floating point parameters are passed in xmm0 through xmm7. It looks like OP is doing it right, although I haven't walked through it to know for certain which values end up where.

---

