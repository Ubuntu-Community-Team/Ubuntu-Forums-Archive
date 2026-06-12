---
title: "Assembly System Call oO"
date: 2009-09-02
forum: Programming Talk
---

### Post by brunoskrebs on 2009-09-02
Hi there,

my teacher gave me a homework about system calls in linux, and this homework is about opening/create a file in assembly language.

Since I'm not really good in this low level talk, I'm having trouble to understand how to do that.

First I tried something like this:
```

.data # Sessao de dados inicializados
	O_RDONLY = 0
	STDOUT = 1
	SYS_EXIT = 1
	SYS_READ = 3
	SYS_WRITE = 4
	SYS_OPEN = 5
	SYS_FORK = 2
	O_CREAT = 25
	len = 10
	arquivoA: .string "arqA.txt\0" 	# Arquivo a ser lido
	arquivoB: .string "arqB.txt\0" 	# Arquivo a ser lido
	msg: .string "arquivoA.txt criado!\0" 	# Mensagem a ser escrita em STDOUT
	.comm buf, 512 			# buffer com 512 Bytes
.text # Sessao de codigo
	.global _start

_start:
	# Criar arquivo
	mov $SYS_WRITE, %ecx	# apontador para o buffer
	mov $arquivoB, %ebx 	# Nome do Arquivo
	mov $O_CREAT, %eax 		# Numero da chamada de sistema (open)
	int $0x80 				# Chamada do kernel

	# void _exit(int status)
	mov $0, %ebx # Código do exit
	mov $SYS_EXIT, %eax # Número da chamada de sistema (exit)
	int $0x80 # Chamada do kernel


```

But it didn't work, and now I'm wondering... this SYS_OPEN (and integer that is specified in the unistd_32.h) is really for opening files/devices? Or should I use O_CREAT from fcntl.h?

Furthermore O_CREAT in fcntl.h is equal to 00000100, what number is that? I don't think that this is a base 2 number because in the same fcntl.h file, there is a O_NOCTTY constant equals to 00000400...

So any help would be appreciated.

Bruno Krebs

---

### Post by Lux Perpetua on 2009-09-02
I have no idea what you're trying to do with this little block of code:> **brunoskrebs said:**
> 
```

	# Criar arquivo
	mov $SYS_WRITE, %ecx	# apontador para o buffer
	mov $arquivoB, %ebx 	# Nome do Arquivo
	mov $O_CREAT, %eax 		# Numero da chamada de sistema (open)
	int $0x80 				# Chamada do kernel

```You seem to be extremely confused about how syscalls work. The syscall number goes in %eax. O_CREAT is not a syscall! What you have there makes no sense whatsoever. 

It should help to write the C version of the code first; then it will be much clearer what the assembly code must look like. 

To answer your other question: in C, numerical literals that begin with 0 are octal (base 8), unless they begin with 0x, in which case they are hexadecimal (base 16). C89 (the most widely accepted standard) does not support binary literals. (I'm not sure if C99 does.)

---

### Post by brunoskrebs on 2009-09-02
I was trying to create a file. And well I'm not really confused about it, because I don't understand it. But that's ok I'll try to figure it out...

Edit:

Oh yes, and by the way

are you telling me that 00000100 and 00000400 are in octal base??

---

### Post by Arndt on 2009-09-03
> **brunoskrebs said:**
> I was trying to create a file. And well I'm not really confused about it, because I don't understand it. But that's ok I'll try to figure it out...

Edit:

Oh yes, and by the way

are you telling me that 00000100 and 00000400 are in octal base??

In C syntax (which .h files are in), numbers beginning with a 0 are octal, yes. Someone should have given you that information, if you are supposed to use the contents of the system include files for writing assembly code.

Where does the 25 come from? 25 seems to be number of the 'stime' call. 'creat', if that's what you want to use, has number 8.

The order of things should probably be 1) open or create the file; 2) write to it, if you want something to be in it; 3) close it; 4) exit the program.

---

### Post by brunoskrebs on 2009-09-04
Thanks people now I figured it out...

---

