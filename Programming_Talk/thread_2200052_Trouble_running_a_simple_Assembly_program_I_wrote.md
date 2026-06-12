---
title: "Trouble running a simple Assembly program I wrote"
date: 2014-01-17
forum: Programming Talk
---

### Post by ryanch94 on 2014-01-17
I'm teaching myself Assembly and I'm currently writing a program that is in the book I'm learning from. I have written out the code exactly as the book says and it assembles and links fine but when I try to run the program I get the error 'Segmentation fault (core dumped)'

Could anybody perhaps help me out with this? The program is meant to cycle through a list of predefined numbers and print the largest number as the exit code when I run 'echo $?' in terminal. Here is the code for the program:

```
#PURPOSE:        This program finds the maximum number of a set of data items
#
#
#VARIBALES:        The registers have the following uses:
#                %edi - Holds the index of the data item being examined
#                %ebx - Largest data item found
#                %eax - Current data item being examined
#
#                The following memory locations are used:
#
#                data_items - contains the item data. A 0 is used to terminate the data
#
#

.section .data

data_items:
                .long 3,67,34,222,45,75,54,34,44,33,22,11,66,0                    # These are the data items

.section .text

.globl _start
_start:
                movl $0, %edi                                                    # Move 0 into the index register
                movl data_items(,%edi,4), %eax                                    # Load the first byte of data
                movl %eax, %ebx                                                    # Since this is the first item, %ebx is 
                                                                                # automatically set to %eax which is the
                                                                                # current biggest

start_loop:
                cmpl $0, %ebx                                                    # Check to see if we've reached the end
                je loop_exit
                incl %edi                                                        # Load next value
                movl data_items(,%edi,4), %eax                                    
                cmpl %ebx, %eax                                                    # compare values
                jle start_loop                                                    # jump to beginning of loop if new item isn't
                                                                                # bigger    

                movl %eax, %ebx                                                    # move value as the largest
                jmp start_loop                                                    # jump to loop beginning

loop_exit:
                movl $1, %eax                                                    # move 'exit' system call into %eax
                int $0x80                                                        # call linux kernel
                

```

---

### Post by trent.josephsen on 2014-01-17
Segmentation faults usually occur when you walk outside the bounds of an array, or otherwise try to access memory that isn't yours. That leads me to suspect that your loop isn't terminating when you want it to. Take a closer look at the code that checks the exit condition of the loop.

---

### Post by ryanch94 on 2014-01-17
> **trent.josephsen said:**
> Segmentation faults usually occur when you walk outside the bounds of an array, or otherwise try to access memory that isn't yours. That leads me to suspect that your loop isn't terminating when you want it to. Take a closer look at the code that checks the exit condition of the loop.

Looked over it at the exit check, and I had it set to check ebx instead of eax. Thanks for your help :D

---

### Post by trent.josephsen on 2014-01-17
No problem :) Sometimes it just takes an extra eye

---

