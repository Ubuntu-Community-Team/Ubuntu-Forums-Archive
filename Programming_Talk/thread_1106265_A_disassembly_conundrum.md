---
title: "A disassembly conundrum"
date: 2009-03-25
forum: Programming Talk
---

### Post by night_fox on 2009-03-25
I effectively learnt the very basics of how to understand assembly language today, and now I can very slowly go through some functions and work out what they do. I was disassembling a certain file and I stumbled across the following function. As far as I can tell it does nothing useful.


```
push    ecx
lea     ecx, [esp+4]
sub     ecx, eax
sbb     eax, eax
not     eax
and     ecx, eax
mov     eax, esp
and     eax, 0xFFFFF000

second_part:
cmp     ecx, eax
jb      third_part
mov     eax, ecx
pop     ecx
xchg    eax, esp
mov     eax, [eax]
mov     [esp], eax
retn

third_part:
sub     eax, 1000h
test    [eax], eax
jmp     second_part
endp
```


Is there something here that I'm missing? Or is it here as an obfuscation? Can someone please confirm this?

Answers much appreciated!

---

### Post by NathanB on 2009-03-25
It looks like it is simply "walking" a structure which was passed on the stack.

---

### Post by smartbei on 2009-03-26
The pattern of opcodes sub (subtract), sbb (subtract with borrow), and not (~) is a reltively common compler optimization that really just checks if something is bigger than something else.
In this case, unless I am mistaken, the beginning is actually (in a mix of assembly and c):
```

int a;
ecx = &a;
if (ecx < eax) {
    ecx = 0;
}
eax = esp & 0xffff000; // The page base address?

```

The rest of the code is less confusing I think... Try to figure out for yourself :-)

EDIT:
One thing I am not sure about is:
```

test    [eax], eax

```
Since the opcode only sets flags, it seems odd to put it before an unconditional jump, which leads to a place with a cmp...

---

### Post by Frank Kotler on 2009-03-27
Nice analysis, smartbei! Nice puzzle, night_fox! Any "provenance" on this? A little more "context" might help - what's eax supposed to be on entry? Can you tell us what "certain file" this is from?

I, too, am puzzled by the "test [eax], eax"... apparently without using the resulting flags for anything. My thought was, "how do we know [eax] is going to be valid memory?" This might segfault. Then I thought, "maybe that's the idea"...

I'm foggy on this, but as I understand it, our stack is "dynamic". Below the "valid" area is a "guard page" marked not present. An attempt to access it causes a page fault, the handler sees that it's "stack", and responds by mapping in a new page (under our current stack), and presumably protecting it with a guard page below that. I think that's how that works...

I'm gonna take a WAG that this is a routine to safely allocate *large* (over 4k) local variables on the stack. The "test [eax], eax" is just to "touch" the stack (and trigger the page fault?) every 4k. Odd that the "amount to allocate" seems to be passed in eax, rather than on the stack - "fastcall" maybe?

That's my current theory...

Best,
Frank

---

### Post by night_fox on 2009-03-28
Hi everyone, thanks for looking at the routine. I found it by disassembling a commonly used windows program infested with DRM, which I *probably* had no right to do. It was called from the first line of another function, so I'm sorry, I have no idea what eax might be initially!

The function it was called from generated a security cookie (some number stored to make sure the memory was not tampered with during the function). The function called the function I posted even before generating this cookie.

Here is my attempt at decompiling of the rest of it:

```
function unknown(void* argument) {

// From smartbei

    if (argument < eax) {
        argument = 0;
    }

    eax = esp & 0xFFFFF000;

// end of smartbei's bit

    while (eax > argument) {
        eax-=0x1000;
    }

    eax = argument;

    esp=eax;
    *esp=*eax;

}
```

I'm still not sure though. In the first part of the function, sub-sbb-not, surely it subtracts eax from ecx, then subtracts eax from itself, leaving eax=0, then nots it to get 0xFFFFFFFF, then ands it with ecx with no effect? Why do the three lines not become this:

```
    argument-=eax;
    eax=0;
    eax=0xFFFFFFFF;
```

?

Also, why does the memory need to be aligned to the nearest (down) 0xFFFFF000 ?

What generates a page fault? I.E. how far out of the stack can you get before your program bombs out?

---

### Post by NathanB on 2009-03-28
Just a FYI:  Don't talk about "reverse-engineering" here... it is a criminal act in some countries and would be against the TOS here.

As long as your intentions are only the examining of compiled code for educational purposes, we can continue...

> I'm still not sure though. In the first part of the function, sub-sbb-not, surely it subtracts eax from ecx, then subtracts eax from itself, leaving eax=0, then nots it to get 0xFFFFFFFF, then ands it with ecx with no effect?

Are you taking into account the "borrow" attribute of 'sbb'??

[http://www.sesp.cse.clrc.ac.uk/html/SoftwareTools/vtune/users_guide/mergedProjects/analyzer_ec/mergedProjects/reference_olh/mergedProjects/instructions/instructions.htm](http://www.sesp.cse.clrc.ac.uk/html/SoftwareTools/vtune/users_guide/mergedProjects/analyzer_ec/mergedProjects/reference_olh/mergedProjects/instructions/instructions.htm)

> What generates a page fault? I.E. how far out of the stack can you get before your program bombs out?

Read about 'paged memory' systems:

[http://en.wikipedia.org/wiki/Virtual_memory](http://en.wikipedia.org/wiki/Virtual_memory)

> Also, why does the memory need to be aligned to the nearest (down) 0xFFFFF000 ?

Alignment is important for performance reasons:

[http://en.wikipedia.org/wiki/Packed](http://en.wikipedia.org/wiki/Packed)

---

### Post by night_fox on 2009-03-31
Ahhhhhhh thanks! All of that was incredibly useful!

From the intel manual, sbb does this:

DEST &#8592; DEST &#8211; (SRC + CF);

so the result of the SUB, SBB, NOT would be 

```
sub     ecx, eax  //  if eax>ecx, CF=1        ; if ecx>=eax, CF=0
sbb     eax, eax  //  if       eax=0xffffffff ;  eax=0x00000000
not     eax       //  if       eax=0x00000000 ;  eax=0xffffffff
```

Then the result gets anded with ecx, so
```
    if (argument < eax) {
        argument = 0;
    }
```
must be right!

EDIT:
This is what the wikipedia page NathanD linked to says about alignment in this program:
> While the x86 architecture originally did not require aligned memory access and still works without it, SSE2 and x86-64 instructions on x86 CPUs do require the data to be 128-bit (16-byte) aligned and there can be substantial performance advantages from using aligned data on these architectures.

Thanks all!

:popcorn:

---

