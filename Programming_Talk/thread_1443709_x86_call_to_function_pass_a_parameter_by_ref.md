---
title: "x86 call to function pass a parameter by ref"
date: 2010-03-31
forum: Programming Talk
---

### Post by Xender1 on 2010-03-31
So I am writing some x86 code for a function that gets called by my C program. What this does is calculates the memory offset of a matrix, and then passes in the value of that matrix to a swap by reference (swap takes two parameters both are pointers). My program is now able to go through the and do the swap, but now in my main code when i try and do a printf M[i][j] i get a seg fault... here is my code

Here is the transpose matrix code: i think the offset i am using is correct (matrix is filled with unsigned ints) 
```

        .text

.globl _transpose_matrix
.globl transpose_matrix

_transpose_matrix:
transpose_matrix:

        # begin code
	pushl	%ebp		
	movl	%esp,%ebp	# Save stack pointer
	pushl	%ebx		

        
        # set up of loops

        movl $0, %eax          #eax = i = 0
i_loop:
        cmpl 12(%ebp), %eax        #if i >= ecx (size)
        jge end_i               #jump too end i loop

        movl $0, %ebx           #ebx = j = 0
j_loop:
        cmpl %eax, %ebx         #if j>=i (eax)
        jge end_j               #jump to end j loop

        movl 8(%ebp), %edi    #edi = matrix A
        #center of loops
        movl %eax,0(%esp)       #store i value
        imull 12(%ebp), %eax    #i * size
        addl %ebx, %eax         #i*size + j
        leal (%edi, %eax, 4), %eax  #eax = &A[4i*size+4j

        movl 8(%ebp), %edi    #edi = matrix A
        movl %ebx, 4(%esp)      #store j value
        imull 12(%ebp), %ebx    #j * size
        addl 0(%esp), %ebx      #j*size + i
        leal (%edi, %ebx, 4), %ebx

        #push values to swap on to stack
        push %ebx
        push %eax
        call swap               #calls swap
        popl %eax
        popl %ebx
        movl 4(%esp), %ebx      #restore j
        movl 0(%esp), %eax      #restore i

        #end center of loops
        inc %ebx                #j++
        jmp j_loop              #jump to j_loop
end_j:
        inc %eax                #i++
        jmp i_loop              #jump to i_loop
end_i:
        # finish code
	movl -4(%ebp), %ebx	#
	movl	%ebp,%esp	# Restore Stack pointer
	popl	%ebp		
	ret

```
before i call this the matrix is
1  2  3  4
5  6  7  8
9  10 11 12
11 12 13 14

after i call this its suppose to be transposed: but its outputting
4  6  140365944 1

can anyone help me figure out why?

---

### Post by pbrane on 2010-03-31
Do you have to use assembly?  In C you could just do this.

```

for (j=0; j < nrows; j++)
  for (k=0; k < ncols; k++)
    transposed[k][j] = original[j][k];

```

---

### Post by Xender1 on 2010-03-31
I am just doing it in assembly because I just want to try and learn more about it and about registers. I feel like my problem my be coming from the amount of memory i am shifting over to get A[i][j] and A[j][i] because this is what im doing now:
```

        movl 8(%ebp), %edi    #edi = matrix A
        movl %ebx, 4(%esp)      #store j value
        imull 12(%ebp), %ebx    #j * size
        addl 0(%esp), %ebx      #j*size + i
        leal (%edi, %ebx, 4), %ebx

```

or maybe set up the push each variable im using at the top where we save the stack pointer
```

	pushl	%edi
	pushl	%esi
	pushl	%ebx
	subl	$16, %esp

```

---

### Post by Lux Perpetua on 2010-03-31
```

        .text

.globl _transpose_matrix
.globl transpose_matrix

_transpose_matrix:
transpose_matrix:

        # begin code
	pushl	%ebp		
	movl	%esp,%ebp	# Save stack pointer
	pushl	%ebx		

```You're not saving %edi here, which you should, since you overwrite it later. The caller might care about that register. Also, you didn't make any space for your local variables, so when you store anything to 0(%esp) or 4(%esp) below, you're actually destroying useful information. 
```
        
        # set up of loops

        movl $0, %eax          #eax = i = 0
i_loop:
        cmpl 12(%ebp), %eax        #if i >= ecx (size)
        jge end_i               #jump too end i loop

        movl $0, %ebx           #ebx = j = 0
j_loop:
        cmpl %eax, %ebx         #if j>=i (eax)
        jge end_j               #jump to end j loop

        movl 8(%ebp), %edi    #edi = matrix A
        #center of loops
        [color=red]movl %eax,0(%esp)       #store i value[/color]
        imull 12(%ebp), %eax    #i * size
        addl %ebx, %eax         #i*size + j
        leal (%edi, %eax, 4), %eax  #eax = &A[4i*size+4j

        movl 8(%ebp), %edi    #edi = matrix A
        [color=red]movl %ebx, 4(%esp)      #store j value[/color]
        imull 12(%ebp), %ebx    #j * size
        addl 0(%esp), %ebx      #j*size + i
        leal (%edi, %ebx, 4), %ebx

        #push values to swap on to stack
        push %ebx
        push %eax
        call swap               #calls swap
        popl %eax
        popl %ebx
        movl 4(%esp), %ebx      #restore j
        movl 0(%esp), %eax      #restore i
        #end center of loops
        inc %ebx                #j++
        jmp j_loop              #jump to j_loop
end_j:
        inc %eax                #i++
        jmp i_loop              #jump to i_loop
end_i:
        # finish code
	movl -4(%ebp), %ebx	#
	movl	%ebp,%esp	# Restore Stack pointer
	popl	%ebp		
	ret

```

---

### Post by Xender1 on 2010-03-31
Hm, I see. I tried just using two other registers to store i into and no matter how i write it it does not work. i fixed me memory allocation at the top and bottom by adding
```
        # begin code
	pushl	%ebp		
	movl	%esp,%ebp	
        pushl %edi
        pushl %ecx
        push %edx
        pushl %esi
	pushl %ebx		
        subl $16, %esp


#### and at the end
        addl $16, %esp
        popl %ebx
        popl %esi
        popl %edi
        popl %ecx
        popl %edi
	popl	%ebp		
	ret

```
since just using other registers to store i into and take it from (tried using movl), how does one go about creating the space for two slots in %esp??

---

### Post by pbrane on 2010-03-31
> **Xender1 said:**
> 
since just using other registers to store i into and take it from (tried using movl), how does one go about creating the space for two slots in %esp??

```

# begin code
pushl	%ebp		
movl	%esp,%ebp	# Save stack pointer
pushl	%ebx
**sub  %esp, stack_size**

```

I think that should do it.

---

### Post by Xender1 on 2010-03-31
stack_size is undefined, and wouldnt it also have to be sub stack_size, %esp

---

### Post by pbrane on 2010-03-31
*stack_size* is whatever you want it to be. And yes in GNU notation it should be **sub stack_size, %esp**.
So if you want the stack to be 32 bytes then stack_size is 0x20.

---

