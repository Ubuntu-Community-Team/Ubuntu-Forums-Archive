---
title: "Help converting an assembly MIPS integer program to floating point program"
date: 2009-11-30
forum: Programming Talk
---

### Post by yaser87 on 2009-11-30
I am writing a program to solve a linear system equations using 
gaussian elimination method by taking the factors and storing them in 
a NxN+1 matrix,

this matrix can take integer numbers as well as floating point numbers
i need help in translating this program to floating point

it's ok to use pseudo code instruction but it's better to use real instruction

one last thing i need to promote the user to:
. choose N
. to choose the name of the input text file to store the matrix

and how to read the stored numbers from a file and converting them from string to single precision.

thanks in advance to you all

this is the code:

  **Assembly Syntax**
 
  
[LIST=1]
[*]Gaussian:
[*]addiu $s0,$Zero,0    #ALU Inst.
[*]addiu $s1,$Zero,0    #Float. Point Inst.
[*]addiu $s2,$Zero,0    #Load&Store Inst.
[*]addiu $s3,$Zero,0    #Branch&Jmp Inst.
[*]xor $t0,$t0,$t0
[*]addiu $t0,$t0,0        #t0=k=0
[*]addiu $s0,$s0,1
[*]addiu $t1,$t1,0        #t1=N
[*]addiu $s0,$s0,1
[*]addiu $t2,$t2,-2    #t2=N-2
[*]addiu $s0,$s0,1
[*]addiu $t3,$t1,-1    #t3=n-1
[*]addiu $s0,$s0,1
[*]For1:
[*]    beq $t0,$t3,Quit
[*]    addiu $s3,$s3,1
[*]For2:
[*]    addiu $t4,$t0,1    #i=k+1
[*]    addiu $s0,$s0,1
[*]    beq $t4,$t1,Quit
[*]    addiu $s3,$s3,1
[*]    addiu $t7,$t1,1        #4k+(n+1)i
[*]    addiu $s0,$s0,1
[*]    mul $t7,$t4
[*]    addiu $s0,$s0,1
[*]    mflo $s4
[*]    addiu $s0,$s0,1
[*]    addiu $t8,$zero,4
[*]    addiu $s0,$s0,1
[*]    mul $t8,$t0
[*]    addiu $s0,$s0,1
[*]    mflo $s5
[*]    addiu $s0,$s0,1
[*]    addiu $s6,$s5,$s4
[*]    addiu $s0,$s0,1
[*]    lw $s7, 0($s6)
[*]    addiu $s2,$s2,1
[*]    mul $t7,$t0    #4k+(n+1)k
[*]    addiu $s0,$s0,1
[*]    mflo $t9
[*]    addiu $s0,$s0,1
[*]    addiu $t9,$s5,$t9
[*]    addiu $s0,$s0,1
[*]    lw $s5, 0($t9)
[*]    addiu $s2,$s2,1
[*]    div $s7,$s5
[*]    addiu $s0,$s0,1
[*]    mflo $s4        # factor=$s4
[*]    addiu $s0,$s0,1
[*]    addiu $t5,$t0,1    #j=k+1
[*]    addiu $s0,$s0,1
[*]    addiu $t6,$t1,1    #t6=N+1
[*]    addiu $s0,$s0,1
[*]    beq $t5,$t6,Quit
[*]    addiu $s3,$s3,1
[*]For3:
[*]    mul $t8,$t5    #4j+(n+1)i
[*]    addiu $s0,$s0,1
[*]    mflo $s5
[*]    addiu $s0,$s0,1
[*]    addiu $s6,$s5,$s4
[*]    addiu $s0,$s0,1
[*]    lw $s5,0($s6)
[*]    addiu $s2,$s2,1
[*]    mul $t7,$t0    #4j+(n+1)k
[*]    addiu $s0,$s0,1
[*]    mflo $s7
[*]    addiu $s0,$s0,1
[*]    addiu $s6,$s5,$s7
[*]    addiu $s0,$s0,1
[*]    lw $s7,0($s6)
[*]    addiu $s2,$s2,1
[*]    mul $s4,$s7
[*]    addiu $s0,$s0,1
[*]    mflo $xx
[*]    addiu $s0,$s0,1
[*]    subu $xx,$s5,$xx
[*]    addiu $s0,$s0,1
[*]    sw $xx,0($s6)
[*]    addiu $s2,$s2,1
[*]    addiu $t0,$t0,1
[*]    addiu $s0,$s0,1
[*]    jmp For1
[*]    addiu $s3,$s3,1
[*]Quit:
[*]    sw $zero,0($s6)
[*]    addiu $s2,$s2,1
[*]    addiu $s2,$s2,1
[*]    addu $s4,$s0,$s1
[*]    addu $s5,$s2,$s3
[/LIST]

---

### Post by Zugzwang on 2009-12-01
Anything related to user I/O depends on the actual environment the code is intended to run in. Without further information there's nothing we can tell you.

BTW, you do know the homework policy, right?

---

### Post by yaser87 on 2009-12-01
a

---

### Post by Zugzwang on 2009-12-01
> **yaser87 said:**
> if you wanna help i appreciate your help , i don't cheat i just wanna know how can i handle this I/O and floating point

As I've already said, that depends on the environment the code is running in. For example, MIPS processors are quite popular (afaik?) in washing machines and printers. There are also computers running Linux on MIPS machines. There might be other operating system working on MIPS machines. User I/O is now a function of the operating system (if existing). So you have to interface it. But you didn't state anything about the environment although the correct answer to the question depends on that. I'm afraid to say that this is a little bit like going to your favourite car mechanic asking "how can I change my brakes" and not answering the question "what car do you have" but still expecting a good answer. ;-)

Despite the fact that this is a Linux board, MIPS machines are mostly used in embedded environments. If this is meant to run in a Linux program, I would suppose that you write a small piece of code in C for the user I/O and then just call your code as a function from it. This is *much* easier than doing it directly.

---

### Post by yaser87 on 2009-12-01
Yes i understand that MIPS processors are used in embedded system and mostly mobile phones and TVs and come second in sale after Intel processors.

but to clarify this to you

i am running this MIPS assembly code on an intel processor computer but i am using a masm simulator to simulate my code

---

### Post by Zugzwang on 2009-12-01
> **yaser87 said:**
> i am running this MIPS assembly code on an intel processor computer but i am using a masm simulator to simulate my code

I've never heard of a "masm simulator" for mips code. I only know "MASM" the Microsoft assembler for x86 architectures. A quick google search for "MASM MIPS simulator" also reveals nothing.

If you want to do input/output with it, you might want to have a look at its documentation as your possibilities depend on what it actually supports.

---

### Post by yaser87 on 2009-12-01
i am sorry i meant Mars tool Mars 3.6 

not masm because i used to program in intel assembly

---

### Post by Zugzwang on 2009-12-01
Ok, so what does its documentation contain about user I/O?

---

