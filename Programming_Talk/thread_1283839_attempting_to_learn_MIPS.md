---
title: "attempting to learn MIPS"
date: 2009-10-05
forum: Programming Talk
---

### Post by Xender1 on 2009-10-05
So I am trying to just get a feel for MIPS and playing around with some stuff. I have quite a bit of code done so far but I am really struggling with subroutines and argument registers.

Pretty much I have hard coded two arrays:
mat_a:	.word 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16
mat_b:	.word 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16

In the main function I set up $a0 as mat_a and $a1 as mat_b. From the main function I have a sub routine that goes to a label called matrix_add. This is where I am very confused because I do not know how to go about adding up each element in these arrays. I think that I have to set up a temp register and have it equal to each part like:
lw $t0,0($a0)
lw $t1,0($a1)

But the problem is I have another subroutine called from this routine which does the addition, so that is where I dont understand how to save only $a0 as the first part then go back and then get the second part.

---

### Post by mattyB on 2009-10-06
Have a peak at my solution for adding up the numbers from 1 to 20. See if this gives you some insights into how your code should look and work. Post your code so we can all have peak.

Note: animas is a river in Durango, CO USA ;-)
```

############################################
# Sums up the numbers (words) from 1 to 20 #
# Prints the numbers and then the sum	   #
############################################
.text
.align 2
.globl main

main:
	la $t0, animas
	li $s0, 20
	jal addition
	jal print
	b end
addition:
	lw $t1 ($t0)
	move $a0, $t1
	li $v0, 1
	syscall
	li $v0, 4
	la $a0, comma
	syscall
	add $t3, $t1, $t3
	addi $s0, -1
	addi $t0, 4
	bgt $s0, $zero, addition
	jr $ra
print:
	li $v0, 4
	la $a0, msg
	syscall
	move $a0, $t3
	li $v0, 1
	syscall
	jr $ra
end:

.data
animas: .word 1,2,3,4,5,6,7,8,9,10,11,12,13,14,15,16,17,18,19,20
msg: .asciiz "\nThe sum is: "
comma: .asciiz ","

```

---

