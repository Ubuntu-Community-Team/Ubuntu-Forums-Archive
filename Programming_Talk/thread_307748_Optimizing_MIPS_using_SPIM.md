---
title: "Optimizing MIPS using SPIM"
date: 2006-11-27
forum: Programming Talk
---

### Post by utopia14 on 2006-11-27
Hey fellow MIPS users... I'm new to the forums and new to MIPS, so I was hoping someone could help me out with a certain problem I'm having...](*,) 

I have to take the following code and optimize it... I know I can do this without the stack/frame pointers, so I can pretty much scrap all the sw and lw operations.  I also know that I have to rearrange the operations (e.g. putting an operation after a branch, since the next operation is always done regardless if the branch is taken) to make it the most efficient machine that it can be.  Also, the $a registers should be used for the arguments and the solutions stored in $v registers.. Any help would be awesome... thanks guys..

.text
memset:
	addiu	$sp,$sp,-16
	sw	$fp,8($sp)
	move	$fp,$sp
	sw	$a0,16($fp)
	sw	$a1,20($fp)
	sw	$a2,24($fp)
	lw	$v0,20($fp)
	sb	$v0,0($fp)
	lw	$v0,16($fp)
	sw	$v0,4($fp)
L2:
	lw	$v0,24($fp)
	beq	$v0,$0,L3
	lw	$v1,4($fp)
	lbu	$v0,0($fp)
	sb	$v0,0($v1)
	lw	$v0,4($fp)
	addiu	$v0,$v0,1
	sw	$v0,4($fp)
	lw	$v0,24($fp)
	addiu	$v0,$v0,-1
	sw	$v0,24($fp)
	j	L2
L3:
	lw	$v0,16($fp)
	move	$sp,$fp
	lw	$fp,8($sp)
	addiu	$sp,$sp,16
	j	$ra




a_memmove:
	addiu	$sp,$sp,-16
	sw	$fp,8($sp)
	move	$fp,$sp
	sw	$a0,16($fp)
	sw	$a1,20($fp)
	sw	$a2,24($fp)
	lw	$v0,16($fp)
	sw	$v0,0($fp)
	lw	$v0,20($fp)
	sw	$v0,4($fp)
	lw	$v1,4($fp)
	lw	$v0,0($fp)
	sltu	$v0,$v1,$v0
	beq	$v0,$0,L11
	lw	$v1,4($fp)
	lw	$v0,24($fp)
	addu	$v1,$v1,$v0
	lw	$v0,0($fp)
	sltu	$v0,$v0,$v1
	beq	$v0,$0,L11
	lw	$v1,0($fp)
	lw	$v0,24($fp)
	addu	$v0,$v1,$v0
	sw	$v0,0($fp)
	lw	$v1,4($fp)
	lw	$v0,24($fp)
	addu	$v0,$v1,$v0
	sw	$v0,4($fp)
L7:
	lw	$v0,24($fp)
	beq	$v0,$0,L10
	lw	$v0,0($fp)
	addiu	$v0,$v0,-1
	move	$v1,$v0
	sw	$v1,0($fp)
	lw	$v0,4($fp)
	addiu	$v0,$v0,-1
	sw	$v0,4($fp)
	lbu	$v0,0($v0)
	sb	$v0,0($v1)
	lw	$v0,24($fp)
	addiu	$v0,$v0,-1
	sw	$v0,24($fp)
	j	L7
L11:
	lw	$v0,24($fp)
	beq	$v0,$0,L10
	lw	$v1,0($fp)
	addiu	$a0,$fp,4
	lw	$v0,0($a0)
	lbu	$a1,0($v0)
	addiu	$v0,$v0,1
	sw	$v0,0($a0)
	move	$v0,$v1
	sb	$a1,0($v0)
	addiu	$v1,$v1,1
	sw	$v1,0($fp)
	lw	$v0,24($fp)
	addiu	$v0,$v0,-1
	sw	$v0,24($fp)
	j	L11
L10:
	lw	$v0,16($fp)
	move	$sp,$fp
	lw	$fp,8($sp)
	addiu	$sp,$sp,16
	j	$ra




a_strcat:
	addiu	$sp,$sp,-16
	sw	$fp,8($sp)
	move	$fp,$sp
	sw	$a0,16($fp)
	sw	$a1,20($fp)
	sw	$a2,24($fp)
	lw	$v0,16($fp)
	sw	$v0,0($fp)
L15:
	lw	$v0,0($fp)
	lb	$v0,0($v0)
	beq	$v0,$0,L18
	lw	$v0,0($fp)
	addiu	$v0,$v0,1
	sw	$v0,0($fp)
	j	L15
L18:
	lw	$v0,24($fp)
	beq	$v0,$0,L19
	lw	$v0,20($fp)
	lb	$v0,0($v0)
	beq	$v0,$0,L19
	lw	$v1,0($fp)
	addiu	$a0,$fp,20
	lw	$v0,0($a0)
	lbu	$a1,0($v0)
	addiu	$v0,$v0,1
	sw	$v0,0($a0)
	move	$v0,$v1
	sb	$a1,0($v0)
	addiu	$v1,$v1,1
	sw	$v1,0($fp)
	lw	$v0,24($fp)
	addiu	$v0,$v0,-1
	sw	$v0,24($fp)
	j	L18
L19:
	lw	$v0,0($fp)
	sb	$0,0($v0)
	lw	$v0,16($fp)
	move	$sp,$fp
	lw	$fp,8($sp)
	addiu	$sp,$sp,16
	j	$ra

---

