---
title: "gcc/g++ inline assembly with intel syntax"
date: 2008-04-29
forum: Programming Talk
---

### Post by WitchCraft on 2008-04-29
Hi! I have a question.

If I use gcc/g++ inline assembly, the AT&T syntax is very annoying.
So I can switch over to intel syntax as shown in the garbage program below.

Now my question: Is there any way to get rid of the " ... \n".
It's really very annoying. Is there any compiler switch or option?

```

#include <iostream>

int main() 
{
  __asm (
    ".intel_syntax noprefix\n"
    "jmp farlabel\n"
     "mov  EAX,EAX\n"
     "farlabel:\n"
     "mov  EAX,EAX\n"
     ".att_syntax \n"
  );
  return 0;
}

```

---

### Post by WitchCraft on 2008-04-30
Bump.

---

### Post by Zugzwang on 2008-04-30
Don't know of any real solution, but you could build some preprocessor that looks for "__asm(" lines in your codes and formats to following lines accordingly until an ");" on an empty line is discovered. This wouldn't be hard to write and since everyone is using custom makefiles, no problem to put into the build chain. ;-)

---

### Post by WitchCraft on 2008-04-30
> **Zugzwang said:**
> Don't know of any real solution, but you could build some preprocessor that looks for "__asm(" lines in your codes and formats to following lines accordingly until an ");" on an empty line is discovered. This wouldn't be hard to write and since everyone is using custom makefiles, no problem to put into the build chain. ;-)

This is exactly the kind of bricolage I'm trying to avoid.

---

### Post by Wybiral on 2008-04-30
The problem is that in C:

```

"this"
"is"
"on"
"string"

```

Compiles into:

```

"thisisonestring"

```

So your assembly would be all mangled if you didn't have the newlines.

---

### Post by NathanB on 2008-04-30
When your inline asm code becomes extensive enough that the '/n' and quote marks begin to get annoying, then this is a sure sign that you should move all of your asm code _outside_ of the C/C++ sources.  You can either invoke the 'as' assembler to pre-assemble these object files and link them in during C/C++ source compilation or you can send the '.S' asm sources directly to the gcc compiler and let it assemble them, on-the-fly, during the build process.

Nathan.

---

### Post by mssever on 2008-04-30
> **Wybiral said:**
> ```

"this"
"is"
"on"
"string"

``````

"thisisonestring"

```

Awesome. I didn't know that gcc had built in spelling correction. :)

/me runs for cover

---

### Post by Wybiral on 2008-04-30
> **mssever said:**
> Awesome. I didn't know that gcc had built in spelling correction. :)

/me runs for cover

lol :)

---

### Post by WitchCraft on 2008-06-21
> **mssever said:**
> Awesome. I didn't know that gcc had built in spelling correction. :)

/me runs for cover

:lolflag:

MS-VB.NET now has built-in spell correction...
and some kind of grammar test as well...

---

### Post by xuancong on 2010-07-02
[FONT=Arial]Hi,

It's good that GCC support intel inline disassembly syntax, but it cannot even simply address local variables/parameters properly, making itself stupid and essentially useless, look at the following:

int myfunc(float f){
 int x;
 float fa[8];
 asm(".intel_syntax noprefix\n"
  "mov eax, [x]\n"  // compile fail 1
  "movss xmm1,[f]\n"  // compile fail 2
  "fld dword ptr [fa+4]\n" // compile fail 3
  ".att_syntax\n"
 );
}

For compile fail 1, I can resolve using the following stupidly looking AT&T syntax (why stupid: empty instruction field, only preload register value), but it works nonetheless:
""::"a"(x)
though that cannot deal with "mov eax,[x+4]"
For compile fail 2 and 3, I've no idea except resolving to using other registers but apparantly I'm running out of registers in the real application, because I want to translate following Visual C++ code into g++, but it seems not going to work unless I switch all to global variables which will incur massive cache misses,

// Compute posterior for all mixtures
void ComputeGMM( int n_mix, int n_dim, float *pObs,
     float *pMean, float *pDCov,
     float *pGConst,float *pOut ){
 DWORD exp_bias = 127;
 float exp_mul = (float)(-0.5*M_LOG2E);
 float exp_max = 127.999f;
 float exp_min = -126.999f;
 float vout[4];
 /* SSE optimized batch computation
 ESI: c_mix
 EDI: n_dim/4
 */
 __asm{
  // Load exponent multiplier -> xmm7
  movss  xmm7, exp_mul
  unpcklps xmm7, xmm7
  movlhps  xmm7, xmm7
  // Load max exponent -> xmm6
  movss  xmm6, exp_max
  unpcklps xmm6, xmm6
  movlhps  xmm6, xmm6
  // Load min exponent -> xmm5
  movss  xmm5, exp_min
  unpcklps xmm5, xmm5
  movlhps  xmm5, xmm5
  // Load the four exponent bias (DWORD 127) -> xmm4
  movd  xmm4, exp_bias
  unpcklps xmm4, xmm4
  movlhps  xmm4, xmm4
  // Load the four 1 s -> xmm3
  movaps  xmm3, xmm4
  pslld  xmm3, 23
  // Load loop constants
  mov   esi, n_mix
  mov   edi, n_dim
  shr   esi, 2
  mov   ebx, pMean
  mov   edx, pDCov
re2:
  mov   ecx, edi
  mov   eax, pObs
  xorps  xmm2, xmm2
re1:
  movaps  xmm0, [eax]
  subps  xmm0, [ebx]
  add   eax, 16
  mulps  xmm0, xmm0
  add   ebx, 16
  mulps  xmm0, [edx]
  add   edx, 16
  addps  xmm2, xmm0
  loop  re1
  // up to here, dot product results are in xmm2
  // multiply by -0.5*M_LOG2E to convert from e^(-0.5x) to 2^x
  mulps  xmm2, xmm7
  // cast full exponent into range
  maxps  xmm2, xmm5
  minps  xmm2, xmm6
  // extract integer part -> xmm0
  cvtps2dq xmm0, xmm2
  // compute fractional part -> xmm2
  cvtdq2ps xmm1, xmm0
  subps  xmm2, xmm1
  // store fractional part -> vout[4]
  movups  vout, xmm2
  // compute e^(fractional part) -> vout[4]
  fld   dword ptr [vout]
  fld   dword ptr [vout+4]
  fld   dword ptr [vout+8]
  fld   dword ptr [vout+12]
  f2xm1
  fstp  dword ptr [vout+12]
  f2xm1
  fstp  dword ptr [vout+8]
  f2xm1
  fstp  dword ptr [vout+4]
  f2xm1
  fstp  dword ptr [vout]
  // integer exponent add bias 127
  paddd  xmm0, xmm4
  // shift to floating point exponent position
  pslld  xmm0, 23
  // combine(MUL) the 2 exp result -> xmm0, also multiply with GCONST
  mov   ecx, pGConst
  movups  xmm2, vout
  mov   eax, pOut
  movaps  xmm1, [ecx]
  addps  xmm2, xmm3
  add   ecx, 16
  mulps  xmm0, xmm2
  mov   pGConst,ecx
  mulps  xmm0, xmm1
  movaps  [eax], xmm0
  add   eax, 16
  mov   pOut, eax
  dec   esi
  jnz   re2
 }
}

If you have any idea on how to do this, I would appreciate greatly! Also, I hope future versions of GCC can support intel syntax inline assembly better. Thanks!

Best regards,
Wang Xuancong
National University of Singapore[/FONT]

---

### Post by xb12x on 2010-07-03
> **NathanB said:**
> When your inline asm code becomes extensive enough that the '/n' and quote marks begin to get annoying, then this is a sure sign that you should move all of your asm code _outside_ of the C/C++ sources.  You can either invoke the 'as' assembler to pre-assemble these object files and link them in during C/C++ source compilation or you can send the '.S' asm sources directly to the gcc compiler and let it assemble them, on-the-fly, during the build process.

Nathan.

Also, if you do not like the AT&T style of assembly, have a look at NASM, the Netwide Assembler. Anyone familiar with Microsoft-style assembly will feel at home. It's actually better than the M.S. assembler in many ways. And it's open-source.

---

### Post by texaswriter on 2010-07-03
I would have to say that just learning a new nomenclature would have to be easier than virtually any solution other than one that was perfectly pre-made for you. Being that people rarely use inline assembly, the chances of a pre-made solution is somewhat low. 

That said, IF you had to make your own solution to this, you would inevitably have to learn so much about the nomenclature that you might have well done this to begin with yourself and saved yourself the trouble. 

Nothing wrong with learning something.. 

Not trying to be rude, so HTH

---

### Post by snip3r8 on 2011-09-01
Hey guys ,im an assembly noob,in visual studio compiler on windows

```
method(num)
{
   __asm{
            mov eax, num ; i can move num to eax like this
   }
}

```

How do i do this with gcc?

---

### Post by cgroza on 2011-09-01
> **snip3r8 said:**
> Hey guys ,im an assembly noob,in visual studio compiler on windows

```
method(num)
{
   __asm{
            mov eax, num ; i can move num to eax like this
   }
}

```How do i do this with gcc?
Start a new thread. This one is old and dead.

---

