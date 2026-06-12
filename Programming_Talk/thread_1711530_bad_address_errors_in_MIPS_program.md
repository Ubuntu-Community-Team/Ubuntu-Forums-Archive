---
title: "bad address errors in MIPS program"
date: 2011-03-21
forum: Programming Talk
---

### Post by badbaby_87 on 2011-03-21
Hello.  I'm writing a MIPS program for a class assignment.  The user inputs 2 sorted lists of integers, and the program merges them and prints out a list in decreasing order.  

I'm stuck when I try to run the program. There is a Bad Address error at the line
"sw $4t3, 0($s3)" [noted below in the program as well].  I did research on this issue, but I don't understand why it gives this error.  The data is aligned, so I don't think that is the issue.  

Can someone give me a hint to get my program working correctly?  Thanks.

[PHP]#  Merge Program
    #  This program accepts two ordered lists of integers
    #  from the user and merges them together to create
    #  one list in decreasing order.  This merged list is 
    #  then displayed in the console.

        .data
        
Request1:    
    .asciiz "Please enter a list of integers separated by spaces."

Request2:        
    .asciiz "Enter another list."
    
input1:    
    .align 4
    .word 32        #this is to allocate space for the array
input2:    
    .align 4
    .word 32

MergeResult:    
    .word 0
    .asciiz "The 2 lists combined in decreasing order produces:"
        

        .text
        .globl main
main:        
    
#initialization of array pointers
    la    $s0, input1
    la    $s1, input2

    la    $a0, Request1
    li    $v0, 4
    syscall

# loop1 stores values from input1 as an array
loop1:    
    li    $v0,5
    syscall    
    sw    $v0, 0($s0)
    addi    $s0, $s0, 4
    
    la    $s0,  input1
    #I know I need to loop back to loop1 here, just not sure how    

    la    $a0, Request2
    li    $v0, 4
    syscall
loop2:    
    li    $v0,5
    syscall
    sw    $v0, 0($s1)
    addi    $s1, $s1, 4
    
    #need to loop back to loop2
    la    $s1, input2


compare:    
    lw    $t2, 0($s0)    #loads first word of  $s0 into $t2
    lw    $t3, 0($s1)    #$t3 = first word of $s1
    slt    $t4, $t2, $t3   #$t1 is comparison variable
                                #t4 = 1 if $t2<$t3; $t4 =0 if $t2>= $t3
    bnez    $t4, compareB    #if t4 =1, jump to bLoop
    sw    $t3, 0($s3)    #else store word in $t3 into 0($s3)
                               #this is where the error occurs
    addi    $s0, $s0, 4    #increment 
    addi    $s3, $s3, 4    #increment

    # continue through compare loop
    sle    $s2, $s1, $s0        #$s2 is loop control variable
    beqz    $s2, end        


compareB:
    sw    $t2, 0($s3)
    addi    $t0, $t0, 4
    addi    $s3, $s3, 4
    j compare

end:    
    move    $a0, $s3
    la    $a0, MergeResult
    li    $v0, 4
    li    $v0, 10
    syscall[/PHP]

---

### Post by Npl on 2011-03-21
im not fluent with whatever OS this is supposed to represent (syscalls, calling conventions).
But I can tell you a couple things,
first the register s3 doesnt seem to be initialised anywhere, and you use the .align directive wrong, you need to put it **before** the label (and depending on the assembler .align 4 usually means align on 2^4 bytes... which might not be what you intended).

---

### Post by badbaby_87 on 2011-03-21
Thanks for your advice! With me, it's always simple, silly things like that.  I initialized $s3, and put .align 2 in front of the labels, and the program doesn't give any errors.  I am still working with it to get it to do what I want, but I think that's just a matter of logic vs. syntax.

---

### Post by Npl on 2011-03-21
Dont worry, we make mistakes so we can learn from them and make bigger and better mistakes tomorrow.
[SIZE="1"](Not my words but I dont know the source)[/SIZE]

---

### Post by badbaby_87 on 2011-03-22
I have a bigger mistake already, in fact!

I kind of rewrote the program with alignment and some other changes, and now when I get to the end of the program, it seems it doesn't store the user input to the arrays, and will just print out zeros after the string:  "The 2 lists combined...".  I don't see anything in the registers of $s0 or $s1, and I have no idea why.  This is frustrating.  I feel like I'm doing it right, but I don't understand. 

Any additional pointers would be appreciated.  Thank you.

[PHP]#  Merge Program
    #  This program accepts two ordered lists of integers
    #  from the user and merges them together to create
    #  one list in decreasing order.  This merged list is 
    #  then displayed in the console.

        .data
        
Request1:    
    .asciiz "Please enter a list of integers separated by spaces."

Request2:        
    .asciiz "Enter another list."
    
    .align 2
input1:    
    .word 0        #this is to allocate space for the array

    .align 2
input2:    
    .word 0

MergeResult:    
    .asciiz "The 2 lists combined in decreasing order produces:"
    .align 2
result:
    .space 64    

        .text
        .globl main
main:        
    
#initialization of array pointers
    la    $s0, input1   #$a0 points to input1 space    
    
    la    $a0, Request1
    li    $v0, 4
    syscall

    li    $t0, 0        # loop counter
# loops 1 and 2 store values from input1 and input2 as an array
loop1:    
    li    $v0,5            #accept input from user
    syscall    
    sw    $v0, 0($s0)
    addi    $s0, $s0, 4
    
    #ble    $t0, $s0, loop1        #more input, continue loop1, else...

    la    $s0, input1        #$s1 points to input1 space

    la    $a0, Request2
    li    $v0, 4
    syscall

    li    $t0, 0            #loop counter

    la    $s1, input2
loop2:
    li    $v0,5            #accept second input
    syscall
    sw    $v0, 0($s1)        #store this into 1st element of $s1
    addi    $s1, $s1, 4        #increment to next element

    #ble    $t0, $s1, loop2        #if there's more input, read next
    
    la    $s1, input2        # else load array pointer for input2

    
    li    $t6, 0
compare:        
    lw    $t2, 0($s0)    #loads first word of  $s0 into $t2
    lw    $t3, 0($s1)    #$t3 = first word of $s1
    slt    $t4, $t2, $t3   #$t1 is comparison variable
                #t4 = 1 if $t2<$t3; $t4 =0 if $t2>= $t3
    la    $s3, result    
    bnez    $t4, compareB    #if t4 =1, jump to compareB
    sw    $t3, 0($s3)    #else store word in $t3 into 0($s3)
    addi    $s1, $s1, 4    #increment 
    addi    $s3, $s3, 4    #increment
    # continue through compare loop
    
    addi    $t6, $t6, 1
    blt    $t6, 16, compare
    #beqz    $t6, compare
    j merging
                             
compareB:
    sw    $t2, 0($s3)
    addi    $s0, $s0, 4    #increment 2nd array
    addi    $s3, $s3, 4    
    j compare

merging:    
    
    la    $a0, MergeResult
    li    $v0, 4
    syscall    
    

print:
    li    $t5, 0            # $t5 is a loop counter
    lw    $t7, 0($s3)
    move    $a0, $t7        # load element into $a0
    li    $v0, 5            # read int     
    syscall
    li    $v0, 1            #print int
    syscall
    addi    $s3, $s3, 4        #increment array pointer
    addi    $t5, $t5, 1        #increment loop counter

    blt    $t5, 15, print        #max of 16 ints
    
end:
    li    $v0, 10
    syscall[/PHP]

---

