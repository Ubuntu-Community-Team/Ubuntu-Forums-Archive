---
title: "&quot;Long&quot; Multiplication/Ascii conversion in assembly"
date: 2008-08-15
forum: Programming Talk
---

### Post by qikink on 2008-08-15
I'm trying to write (just to learn) a factorial program in assembly, and finally got it working, but very quickly ran up against the significant limitation of register size. I'm using a 64 bit processor, so its not as bad as it could be, but ! has a way of making numbers very big, very fast, and so as a result the program can only calculate up to 20! - not very useful. I'm rewriting it to do all the calculating in memory, which thanks to the distributive property is nice and easy for the multiplication itself, but for the life of me, I can't work out a way to convert a number in memory to ascii. Simple enough in a register to just divide by 10 and take the remainder, but when you can only do 64 bits at a time, this isn't an option. To give an idea, I have 128 bytes set aside for the answer right now, and I'd like to be able to scale that arbitrarily, so any solution loading the number into a bunch of successive registers is doomed to fail somewhere around 50!. Obviously I don't want code (I want to learn :)) but I"m just wondering if there are algorithms out there for this kind of thing (I guess there are obviously, but how tricky are they to hand code?)

Finally, here's my long multiplication algorithm, I'm pretty new to this all, so it'd be great if I could get some critiques on it:

at the beginning, edi points to the first byte of the "big" number I'm multiplying by, rcx has the little number I'm multiplying by (yeah, its a limitation), r8 holds any carryover from the last multiplication, and ebx points to the 8th to last byte of the "big" number.

```

mult_loop:
	mov rax,[edi]
	mul rcx
	add rax,r8
	adc rdx,0
	mov r8,rdx   ;hold on to the "carry"
	mov [edi],rax
	add edi,8
	cmp edi,ebx
	jle mult_loop

```

---

### Post by jinksys on 2008-08-15
Is there a specific reason you are doing it by long division and not by one of the multiplication instructions?

---

### Post by qikink on 2008-08-15
Hm, (keep in mind I have no idea what I'm doing), I haven't heard of a multiplication algorithm to go from binary to ascii, but that would make things work... Off the top of my head, I can't think of a way to do something that is so basically about division with multiplication, but then again, lots of people have had much more time to think about these things, and have probably come up with a way. If you could point me in the direction of such a way ...? Assembly documentation/help seems rather hard to come by these days.

---

### Post by jinksys on 2008-08-15
So, you are trying to convert a number to a string?

If you are looking for a good assembly book, read Dr Carter's Assembly Language Book.
[http://www.drpaulcarter.com/pcasm/](http://www.drpaulcarter.com/pcasm/)

It's free and uses the Intel syntax you are using.

Also, 
Since you said you weren't looking for the answer (wouldn't want to spoil your fun), I'll just point you in the right direction.  It would be helpful to take a look at other programmer's ITOA (integer to ascii) implementations in C.  A google search brings up a bunch.

[http://www.google.com/search?q=itoa.c&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=itoa.c&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

The first hit is pretty good.

Good Luck.

---

