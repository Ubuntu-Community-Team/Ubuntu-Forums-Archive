---
title: "Base conversion problem"
date: 2013-06-10
forum: Programming Talk
---

### Post by zobayer1 on 2013-06-10
Is it possible to translate a binary number to any other base (not necessarily standard or bases which are powers of 2) directly without using any standard intermediate base (like binary -> decimal -> any other base) and the opposite operation (i.e. from any other base to directly binary base)? If possible, what will be the algorithm? Thanks in advance.

---

### Post by trent.josephsen on 2013-06-10
Sure, it works the same way in any number system -- use repeated division and collect the remainders. You just have to use the base that your number is in.

E.g. to convert the octal (base 8) number 4567 to base 12, observe that 12 is 14 in base 8, and do the following repeated division in octal:

4567 / 14 = 311 remainder 13
311 / 14 = 20 r 11
20 / 14 = 1 r 4
1 / 14 = 0 r 1

So the digits of the base 12 representation are (1, 4, 11, 13) in octal, which can be looked up in a table or something to yield 149b.

That's working with strings, like you would do using pencil and paper -- if you're considering doing this on a computer, it'll be much faster to do the division with numbers, which means writing a routine to interpret a base 8 number and another routine to generate the base 12 output.

---

### Post by Bachstelze on 2013-06-10
In practice, most programming languages can't do arithmetic in arbitrary bases, so unless you work in octal, decimal or hex, chances are you will need to use one of those as an intermediate step.

---

### Post by zobayer1 on 2013-06-10
Yah, it's probably not straight forward in some languages like C/C++. I wanted to avoid decimal just to skip big integer calculations, I know there are lots of libraries for C/C++ to do big integer calculations, but for small purposes it's really overkill.

So, what I did is split the bits into 8 bit chunks (1 byte = base 256) and then convert it to any other base I like. Not straight forward at all, but reduces significant amount of coding. Is there any better idea?

---

### Post by trent.josephsen on 2013-06-11
Built-in number types aren't decimal, or octal or hex (or even binary, kinda). Those are representations that only affect display. In principle it's possible to write a C compiler for a ternary computer, and any conforming program would work the same way. Mathematical operations like +-*/ and even << >> are defined in terms of *values*, not *representations*.

From the machine's standpoint, there's no particular extra work that goes into reading a string of base 20 digits than goes into reading a string of decimal digits -- take a character, convert it into its digital value, multiply the total-so-far by the radix, and add the new digit. The only difference is for base 20 you may have to write this yourself, whereas with base 10 there is usually a function provided. (C provides strtol() and friends, so you may not even have to do that.) Similarly, there's nothing intrinsically more difficult about generating output in base 20, except that you're more likely to have to write the output routine yourself because languages in general don't provide convenience functions for generating number **representations** in arbitrary bases.

That said, how big are the integers you're dealing with? If you're storing a number as an arbitrary-length list of bytes, you're already essentially doing the work of a bignum library, and if you have to do any kind of calculations with these numbers... yeah, I'd just use the library that already exists. It's not like you can avoid writing the code to do division at least, because that's needed to generate output in an arbitrary base. What's the goal here, just to convert numbers from one base to another or do you have a use case?

---

### Post by zobayer1 on 2013-06-11
> **trent.josephsen said:**
> What's the goal here, just to convert numbers from one base to another or do you have a use case?

What I am doing is convert a bit string (arbitrary number of bytes) (some sort of encrypted message) to a human readable form of fixed length using (say for example) English alphabets (A-Z leaving I and O), and do the reverse operation as well, because all of the encryption and shuffling algorithms are performed on the bit string, not the human readable form.

For example I have written this piece of code that is working fine so far:
```

vector< uint8_t > bytesToStr(const vector< uint8_t > &bytesVector, const string &charSet, size_t strLen) {
    int radix = charSet.size();
    vector< uint8_t > temp, temp2, retStr;

    for(size_t i = 0; i < bytesVector.size(); i++) temp.push_back(bytesVector[i]);

    while(!temp.empty()) {

        int mod = 0, div;
        bool step = false;

        temp2.clear();

        for(size_t i = 0; i < temp.size(); i++) {
            div = ((mod << 8) | temp[i]) / radix;
            mod = ((mod << 8) | temp[i]) % radix;

            // just skipping leading zeroes
            if(!step && div) step = true;
            if(step) temp2.push_back(div);
        }

        retStr.push_back(charSet[mod]);
        temp.clear();

        for(size_t i = 0; i < temp2.size(); i++) temp.push_back(temp2[i]);
    }

    // filling empty remaining empty slots, if any
    for(size_t i = retStr.size(); i < strLen; i++) retStr.push_back(charSet[0]);

    reverse(retStr.begin(), retStr.end());

    return retStr;
}

```

Here, bytesVector is the vector of bytes that needed to be transformed, charSet contains the character mapping, and strLen is the required length of the human readable form.

Basically what I am doing here is literally a big integer operation of a different form (as you have said). Instead of having explicit intermediate base, I just consider base 256 (taking each byte) and then convert it directly as we already know the decimal equivalent of each byte (implicitly I am using an intermediate base. So far this is working fine. Is there any space from improvement?

---

### Post by trent.josephsen on 2013-06-12
Nit: You aren't using any base implicitly (except binary, which is just how your computer works) -- that's just a conversion from base 256 to base N. Decimal doesn't come into play at all.

Since you have a fixed size output, you could easily remove the reverse() by filling the buffer backwards from the end, but that's a minor optimization. I'm not sure exactly what you're doing with "temp", and the uninformative variable name doesn't help any. Apart from that, I think the algorithm is fine.

---

### Post by zobayer1 on 2013-06-12
> **trent.josephsen said:**
> Nit: You aren't using any base implicitly (except binary, which is just how your computer works) -- that's just a conversion from base 256 to base N. Decimal doesn't come into play at all.

Since you have a fixed size output, you could easily remove the reverse() by filling the buffer backwards from the end, but that's a minor optimization. I'm not sure exactly what you're doing with "temp", and the uninformative variable name doesn't help any. Apart from that, I think the algorithm is fine.

Sorry for stupid variable names, I am not quite a software developer guy yet, so I hardly follow naming conventions. Here temp and temp2 are used as buffers for swapping a big integer value, I am sure you have understood that as well, and I will try to name the variables more meaningfully next time.
The algorithm is basically this:
```

while(n > 0) {
    append n % radix
    n /= radix
}

```

Thanks for your help :D

---

### Post by trent.josephsen on 2013-06-12
Call me a software guy and I'll stab you in the face. ;) (Professionally I'm a hardware engineer; I just like to have all my documentation in order.)

There is one other thing I would change if I were doing this: split the division out into its own routine that yields both a quotient and a remainder. That way you can write the while loop almost exactly the way you did in pseudocode; the algorithm will be more clear.

Digression: While thinking about your previous post I began to think about the possibilities for encoding bitstreams into ordinary words, rather than letters -- with the right wordlist you could minimize the chances of mis-reading or mis-hearing one word for another. Plus real words tend to be easier to type than arbitrary character sequences. For an extra sneaky bonus you could even disguise it as a grocery list or something. Just a thought...

---

### Post by zobayer1 on 2013-06-12
> **trent.josephsen said:**
> Digression: While thinking about your previous post I began to think about the possibilities for encoding bitstreams into ordinary words, rather than letters -- with the right wordlist you could minimize the chances of mis-reading or mis-hearing one word for another. Plus real words tend to be easier to type than arbitrary character sequences. For an extra sneaky bonus you could even disguise it as a grocery list or something. Just a thought...

First of all, I also later changed the code and separated the div/mod function.
Second, that's a really great idea, it will be much easier to remember and write (not looking at every letters) if real dictionary words are used. However, I am doing this for a fixed length serial number generator. I think if the number of letter gets smaller, the idea is beautiful. Hashing the bit stream into indices of real words from a list can do the trick, but I guess the system itself will be very tricky...

Thanks again :)

---

