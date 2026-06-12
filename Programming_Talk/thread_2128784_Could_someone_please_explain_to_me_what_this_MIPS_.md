---
title: "Could someone please explain to me what this MIPS code does?"
date: 2013-03-24
forum: Programming Talk
---

### Post by s3a on 2013-03-24
Hello everyone.

Could someone please explain to me what the following MIPS code does?:
```
.text
.globl main

main:
	li $11,15
	li $10,32
	li $6,0
main10:
	andi $12, $11, 1
	beq $12, $0, main20
	addi $6, $6, 1
main20:
	srl $11, $11, 1
	addi $10, $10, -1
	bne $10, $0, main10
	li $2,1
	move $4,$6
	syscall
	li $2,10
	syscall

```

If more information is needed from me, ask me and I will give it to you.

Any input would be greatly appreciated!

Edit:
I'm mostly concerned with:
```
.text
.globl main
```

and:

```
syscall
```.

Edit #2:
Also, what is the "goal" of this code?

---

### Post by schragge on 2013-03-24
This looks a lot like a [homework]("http://ww2.cs.mu.oz.au/%7Epjs/297/tute/t03_assembler.answers").

Anyway, I'd rewrite the code like this to be slightly more readable:
```

.text
.globl main

main:
        li $t3,15
        li $t2,32
        li $a2,0
main10:
        andi $t4,$t3,1
        beq $t4,zero, main20
        addi $a2,$a2,1
main20:
        srl $t3,$t3,1
        addi $t2,$t2,-1
        bne $t2,zero, main10
        li $v0,1
        move $a0,$a2
        syscall
        li $a0,10
        syscall

```

According to [this page]("http://logos.cs.uic.edu/366/notes/mips%20quick%20tutorial.htm"), syscall with $v0 set to 1 means *print integer in $a0*

---

### Post by matt_symes on 2013-03-24
> This looks like [homework]("http://ww2.cs.mu.oz.au/%7Epjs/297/tute/t03_assembler.answers").

Agreed. I think schragge is correct. 

Please do not post homework questions here unless you have had a demonstrable,  good attempt at doing it yourself.

---

