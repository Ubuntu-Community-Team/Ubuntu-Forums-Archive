---
title: "Strange C miscalculation/bit shifts"
date: 2010-05-01
forum: Programming Talk
---

### Post by jkxx on 2010-05-01
I've been playing with C (and gcc) a bit lately and wrote a simple SHA-1 hasher as a way to refresh my C a bit. Strangely, the code produces some nonsense results even after following the FIPS to the tee. It seems that either there is a secret syntax to bit shifts that I'm missing or something else is going on.

The test code is at [http://jkansoft.mine.nu/main.c]("http://jkansoft.mine.nu/main.c") and can be compiled/run. The code has a function to rotate bits in a 32 bit integer which looks like this

```
unsigned int SNX(unsigned int n, unsigned int x)
{

    unsigned int out;
    out = ((((x << n)) | (x >> (32-n))));
    return out;
}
```

and from what I've looked into should do the job. However, it doesn't and instead produces a value that is off. Passing this function the padded abc pattern 0x61626380 results in a return value of 0x00c6c4c3 instead of the correct 0x00c7c4c2 when the function is called to shift a single bit to the left. Other operations produce similarly off results.

Am I not declaring something properly here?

---

### Post by MadCow108 on 2010-05-01
I am not familiar with SHA1 implementation so excuse when my answer is unhelpful.

a left rotate of 0x61626380 is 0xc2c4c700 and not 0x00c6c4c3 or 0x00c7c4c2
to me this functions seems to do what you describe it should do (= it returns the correct result 0xc2c4c700)
the problem is probably somewhere else

btw the types in stdint.h are exact width, unlike int and long which can differ from machine to machine (e.g. long is not 64 bits on many machines  but you assume it according to your code).
Its probably better to use these when dealing with bits

---

### Post by jkxx on 2010-05-01
Thanks for the tip! stdint.h is definitely useful for something like this. I already converted all the types to the standardized ones.

However, the left rotate function still returns 0xc3c4c600 (I used little-endian converted values in the original post so my bad there.) Obviously it shouldn't be so I'm still wondering what's up with that code. 

I also tried 2 alternative implementations of same function, both of which produce the above incorrect value.

One was the one from [http://forums.devarticles.com/c-c-help-52/c-code-to-rotate-a-bit-in-a-given-number-50277.html]("http://forums.devarticles.com/c-c-help-52/c-code-to-rotate-a-bit-in-a-given-number-50277.html") and the other from one of the official sha-1 test implementations I downloaded for reference from [http://www.packetizer.com/security/sha1/sha1-c.zip]("http://www.packetizer.com/security/sha1/sha1-c.zip").

The most interesting bit is that the function from the sha-1 package works when compiled as part of that program but reverts to giving the wrong result in mine.

---

### Post by vik_2010 on 2010-05-01
I agree with mad-cow; your function seems to work the way one would expect

also, I think your function suffers from major parenthesis overload. This isn't LISP, no?:popcorn:

---

### Post by gil_johnson on 2010-05-02
No help on your specific problem, but I have found it useful to print out the binary representation of the numbers, right aligned in a field 35 characters wide, one per line. You can see exactly what has happened to your bits. (35 characters leaves room for the binary prefix, plus one space for ease of reading.)
Good luck - Gil

---

