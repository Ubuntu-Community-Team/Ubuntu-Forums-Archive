---
title: "MIPS help"
date: 2008-02-27
forum: Programming Talk
---

### Post by tpluscomb on 2008-02-27
I've been working on a program which reads in a sequence of numbers entered by the user. It's read in as a string and then converted to numbers. Then I am suppose to get the sum of those numbers and report it back. I got most done and I know I'm close (hope!) but I am stuck at trying to get the number to sum up correctly. This is what I have so far:

```

     .data
Prompt1:    .asciiz       "\nPlease enter a list of integers."
newline:	.asciiz		  "\n"
Buffer:		.space		  400

            .globl        main
            .text
main:                                   
		li	  	$v0, 4				# syscall for Print String
		la	  	$a0, Prompt1  		# load address of prompt into $a0
		syscall						# print the prompt

		li	  	$v0, 8		    	# syscall for Read String
		la 	  	$a0, Buffer
		li	  	$a1, 400
		syscall						# read the value of a into $v0
		la    	$s0, Buffer     	# $s0 <= Buffer

		li    	$v0, 4				# output entered string
		la	  	$a0, Buffer
		syscall

		li 		$v0, 4				# output a newline
		la 		$a0, newline
		syscall

		li 	  	$t1, 32         	# set $t1 to ' '
		move 	$s1, $zero			# set value to 0
		move	$s3, $zero			# set temp value to 0

while:
	    lb      $t2, 0($s0)       	# set p*
  		beq  	$t2, $zero, exit	# exit if p* is null
		move	$s2, $zero			# reset current character value
		addi	$s2, $t2, -48		# set current character value

		addi	$s4, $s0, 1			
		lb		$t3, 0($s4)			# set (p+1)*
		
		bne		$t3, $t1, multiply	# Go to multiply if the next character is not whitespace

		add		$s3, $s3, $t2		# temp value = temp value + character value

		add		$s1, $s1, $s3		# value = value + temp value	

		addi	$s0, $s0, 1			# increment pointer p*
		move	$s3, $zero			# reset temp value
		j		while				# go to beginning of while loop


multiply:
		
		sll		$t4, $s3, 3			# x = value multiplied by eight
		sll		$t5, $s3, 1			# y = value multiplied by two
		add		$s3, $t4, $t5		# value = x + y = value * 10

		add		$s3, $s3, $t2		# add the current character to the multiplied value

		addi	$s0, $s0, 1			# increment pointer p*

		j		while				# go to beginning of while loop


exit:
		li 		$v0, 1				# output the value for the sum
		move 	$a0, $s1 
		syscall

		li       $v0, 10           	# terminate run
        syscall                     # return to operating system

```

# note : the teacher said we are not allowed to use mutiplication yet because he hasn't taught us that yet so that is the cause for the shifting.

Any help is appreciated thanks!

---

