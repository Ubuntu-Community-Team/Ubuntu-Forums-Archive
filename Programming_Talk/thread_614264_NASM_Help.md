---
title: "NASM Help"
date: 2007-11-15
forum: Programming Talk
---

### Post by LaRoza on 2007-11-15
The tutorials for NASM that I have found are incomplete, and I am having trouble advancing.

Could someone tell me how this work, and what the mnemonics mean.

I know what this does, and would like to know how it works.

```

get_len:
    mov edx, 0
    get_len_loop:
        inc edx
        cmp byte [name+edx], 10
    jne get_len_loop
ret

```

It is a function to get the length of a string up until the first newline. I am unfamiliar with certain things, specifically, "inc edx", "cmp byte [name+edx],10". I know what cmp means, just what follows it I don't understand. 

Thanks.

---

### Post by NathanB on 2007-11-15
```

get_len:
    mov edx, 0

```

puts a zero in the 'edx' register
```

    get_len_loop:
        inc edx

```
adds the value 1 to the 'edx' register value
```

        cmp byte [name+edx], 10

```
compares the value at memory location '[name+edx]' to the value 10 and sets the CPU flags accordingly.
```

    jne get_len_loop

```
jumps to the label location if the condition is met (the flag is set)

For a more in-depth understanding, I suggest reading either the Intel or AMD processor documentation.

---

### Post by Wybiral on 2007-11-15
"inc" and "dec" are the increment and decrement mnemonics (like x++ and x-- in C). "cmp" is the comparitive mnemonic that sets the flags for the various jump mnemonics.

When you dereference a pointer using "[]" you can also index it. Similar to "*(x + 5)" in C (or x[5] for that matter). The main difference is that you're dealing with bytes in assembly, so you have to multiply in the size of the data you're using (so the 5th index of a 4-byte integer array in NASM would be [x + 5 * 4]).

Also, for the "mov edx, 0" a more efficient way to do this would be:
```

xor edx, edx

```
Because it's only two bytes, while "mov edx, 0" is five bytes (because it has to store the integer in the file).

---

### Post by LaRoza on 2007-11-15
Thanks! I am understanding it now.

---

### Post by tyoc on 2007-11-15
I think it is skeeping the first character... in other words "\nsome\nhere" will not detect the first \n...

---

### Post by slavik on 2007-11-15
> **Wybiral said:**
> "inc" and "dec" are the increment and decrement mnemonics (like x++ and x-- in C). "cmp" is the comparitive mnemonic that sets the flags for the various jump mnemonics.

When you dereference a pointer using "[]" you can also index it. Similar to "*(x + 5)" in C (or x[5] for that matter). The main difference is that you're dealing with bytes in assembly, so you have to multiply in the size of the data you're using (so the 5th index of a 4-byte integer array in NASM would be [x + 5 * 4]).

Also, for the "mov edx, 0" a more efficient way to do this would be:
```

xor edx, edx

```
Because it's only two bytes, while "mov edx, 0" is five bytes (because it has to store the integer in the file).

there's also sub edx, edx :)

---

### Post by LaRoza on 2007-11-15
> **tyoc said:**
> I think it is skeeping the first character... in other words "\nsome\nhere" will not detect the first \n...

What? I don't know what you mean to say, but it doesn't relate to my question, which was answered.

---

### Post by tyoc on 2007-11-15
Apart from the anterior observation, I think also it is assuming that there exist \n in the string or the "10" in numerical way, there is no check for 0 aka null character...

> What? I don't know what you mean to say, but it doesn't relate to my question, which was answered.The code has errors from my point of view.. aka you are reading "bad sources"/bad info/wrong input XD... hahaha :P.. if that is your code, then you have errors.

mmmm I know you know that in C when doing something like this you check for the character "\n", but also you check the end of line... in that code, there is only 1 compare, only 1 of 2 restrictions done.


Also it doesnt follow a "know" call/return convention, I mean ret alone?? there is no movement to EAX register of the result... only if you are using a "register convention" (not exactly "fast call") and more probably only with asm code, but if you want to call your functions from C code, then you should return "normal results" in EAX not in EDX IIRC.


------------
blah.. if you still not get it... is some like

```

voidExtrange len()
  int i = 0;
  do
    i++;
  while name[i] != \n

```

---

### Post by LaRoza on 2007-11-15
Ok...

The code is part of a snippet I have and it fulfills its use then. It is perfect in its use. It may not be bullet proof for other uses, but it was never intended to be used elsewhere.

It was only part of a small NASM script, C has nothing to do with this.

---

### Post by tyoc on 2007-11-15
I answer with those corrections because you wrote

> The tutorials for NASM that I have found **are incomplete**, and I am having trouble advancing.
Common... also observations that I do don't make it bullet proof... ;), there is at less 1 more thing that you should take care if you want that.

The thing about C is that is 1 of the more near languages that show how you will actually do it in asm thats the point illustration not more, not less. Also the pseudo code with some C/python look is a clear representation of what that asm code do... and you dont need to know mnemonics if you pair the pseudo thingy and the asm code.

---

### Post by LaRoza on 2007-11-15
I am learning ASM for the knowledge of how things work, and because I like to learn. Thanks for the tips!

---

### Post by tyoc on 2007-11-16
If you would like more help, or more focus to asm I suggest look at following boards (haven't been there from some time now)

[http://www.asmcommunity.net/](http://www.asmcommunity.net/) has board
[http://flatassembler.net/](http://flatassembler.net/) has board
and finally [http://www.masm32.com/board/](http://www.masm32.com/board/)

There are other main sites, but at less, those 3 are the ones I remember more in this regard. Yes they are not nasm oriented... the first perhaps accept you quest in nasm, the next maybe but they will try you to switch to FASM :P, and the third perhaps no, but asm, at end is asm... also remember the list of nasm in sf. 

There are others (for win IIRC)  goasm, wasm, poasm, rosasm, lzasm. If you want 64 bits at less  last time I used it nasm didnt support it (don't know now), but YASM support 64 bits and is compatible with major part of nasm source code, or switch to FASM that IIRC it also has 64 bit support.

---

### Post by LaRoza on 2007-11-16
Thanks for the links!

---

### Post by LaRoza on 2007-11-16
> **tyoc said:**
> 

There are others (for win IIRC)  goasm, wasm, poasm, rosasm, lzasm. If you want 64 bits at less  last time I used it nasm didnt support it (don't know now), but YASM support 64 bits and is compatible with major part of nasm source code, or switch to FASM that IIRC it also has 64 bit support.

NASM supports 64 bit processors now: [http://nasm.sourceforge.net/](http://nasm.sourceforge.net/)

---

### Post by happysmileman on 2007-11-16
Also I think for standards compliance he should learn NASM first, then move to GAS, since NASM is easier syntax, and then GAS is used in inline assembly and stuff by GCC AFAIK.

Correct me if I'm wrong here

---

### Post by LaRoza on 2007-11-16
> **happysmileman said:**
> Also I think for standards compliance he should learn NASM first, then move to GAS, since NASM is easier syntax, and then GAS is used in inline assembly and stuff by GCC AFAIK.

Correct me if I'm wrong here

I only am interested in NASM and GAS, and not interested in Windows assembly. (if you were refering to me)

The AT&T and Intel syntaxes are different, but trivail. One is not really easier than the other, for me anyway.

I have already worked on both, and am just resuming my study, after a break into Lisp and Haskell. (I am not a CS student, and only do this for myself, so I can jump around)

---

### Post by NathanB on 2007-11-16
> **LaRoza said:**
> NASM supports 64 bit processors now: [http://nasm.sourceforge.net/](http://nasm.sourceforge.net/)

Shhh...  let's kinda keep that under our hat, shall we?  Although version 0.99.04 is the first "working" 64-bit-support release, the 0.99.xx series is intended primarily as "beta" so that the major bugs can be "worked out" before the 2.xx series starts.  If anyone is testing Nasm on 64-bit machines (Linux or Windows, etc.), please notify the team of any bugs or pecular behaivor via the sourceforge mailing list.

My first suggestion for anyone learning assembly language is to grab a good book like "Programming from the Ground Up" or "Art of Assembly" (both are available as free downloads as well as hardcopy).

Some Nasm-specific resources, examples, and help is available here:
[http://tech.groups.yahoo.com/group/linux-nasm-users/](http://tech.groups.yahoo.com/group/linux-nasm-users/)

---

### Post by LaRoza on 2007-11-16
> **NathanB said:**
> Shhh...  let's kinda keep that under our hat, shall we?  Although version 0.99.04 is the first "working" 64-bit-support release, the 0.99.xx series is intended primarily as "beta" so that the major bugs can be "worked out" before the 2.xx series starts.

My first suggestion for anyone learning assembly language is to grab a good book like "Programming from the Ground Up" or "Art of Assembly" (both are available as free downloads as well as hardcopy).


Ok, even though I don't wear a hat much anymore.

The links are in my wiki for those books. (in case anyone is reading this.)

---

### Post by Wybiral on 2007-11-16
> **slavik said:**
> there's also sub edx, edx :)

Indeed. But, I think an r32-to-r32 XOR is faster by a tick or two (I don't feel like hunting down the manual, but from memory I think it is).

---

