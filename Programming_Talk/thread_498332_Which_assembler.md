---
title: "Which assembler?"
date: 2007-07-11
forum: Programming Talk
---

### Post by LaRoza on 2007-07-11
I just recently started learning assembler. However, in my search for resources, I found two different languages.

One using "as", and one using "nasm". I want to learn one of them first, and am now leaning toward nasm. 

I have no problem learning both, but I want to focus on one at a time. Which one would be better to learn first? (I am thinking this is like a C - C++ difference, and that learning one first will affect how you use the other)

Thanks for your input.

---

### Post by Wybiral on 2007-07-11
Actually this isn't really like two different languages. They are both still assembly, they use the same mnemonics and registers. It's more like the difference between cursive and normal writing... Same language, different form.

So really, it's a matter of preference. I prefer NASM because it's cleaner looking.

But... Some people prefer GAS because it's part of the GCC compiler (meaning you can dump a C program to it)

Both of them can be used to generate object files, meaning either can be used to create code FOR C... But GAS is easier to take C code, compile with the "-s" flag and then you have the actual assembly.

When I say clean, this is what I mean...

NASM
```

push ebp
mov ebp, esp
sub esp, 8

```

GAS
```

pushl %ebp
movl %esp, %ebp
subl $8, %esp

```

You can imagine how all those extra symbols build up...

So, for me, GAS when I need to work with GCC output... NASM when I'm just using assembly.

---

### Post by LaRoza on 2007-07-11
Thanks, I noticed how similar they were and was worried one would lead to bad habits in the other.

---

### Post by slavik on 2007-07-11
I remember reading an acticle where gas is easier for simple command because it is mov source, destination (nasm uses intel syntax and switches the source and destination), but the article mentioned that when doing complex memory lookup gas syntax becomes somewhat confusing ...

---

### Post by Wybiral on 2007-07-12
> **slavik said:**
> I remember reading an acticle where gas is easier for simple command because it is mov source, destination (nasm uses intel syntax and switches the source and destination), but the article mentioned that when doing complex memory lookup gas syntax becomes somewhat confusing ...

Actually, I prefer the intel way of opcode order. I look at it like this...

mov eax, 10  is like...  eax=10

and 

add eax, 10  is like...  eax+=10

I actually find GAS's way confusing sometimes.

And yes, memory addressing in GAS is weirder then NASM because NASM allows for simple equations...

mov [eax+ebx*8], ecx

Whereas GAS uses...

mov %ecx, (%eax, %ebx, $8 )

The NASM way looks much cleaner (and more logical).

---

