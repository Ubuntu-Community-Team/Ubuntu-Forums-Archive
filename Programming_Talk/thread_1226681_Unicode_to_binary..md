---
title: "Unicode to binary."
date: 2009-07-29
forum: Programming Talk
---

### Post by Godd on 2009-07-29
I need to be able to convert unicode text to binary for a program I'm writing.

I've looked through the  entire binascii library but I can't find what I need.

I can go through unicode to hex to binary, but the binary comes out to something unusable.

\xf0Y\xfa\xc3_\x8bn/\x8d>\x88\xd7\xe2

Something along the lines of that. What I need is just ones and zeros for on and off status.

I think I can do it by using a list to reference to numerical values but a function would be much nicer and faster.

---

### Post by soltanis on 2009-07-29
You just want to convert unicode text (i.e. \u0065) to the binary number (in 0 and 1 format)?

There is the non-portable C extension to printf using the %b format specifier which prints binary representations of numbers. You could do this with:

```

static char *buffer[1024*5];

char *u2bin(wchar_t *text)
{
        int ctr = 0;

        while (text[ctr] != L'\0') {
                sprintf(buffer+(ctr * sizeof(wchar_t)), "%b", text[ctr]);
                ctr++;
        }
        buffer[ctr] = '\0';

        return buffer;
}

```

I *think*, although there is some type coercion going on there (with the wchar_t to an int, I think, though on UNIX these should be the same).

---

### Post by Godd on 2009-07-30
Ha. I've never even begun to code in C.

I have a friend that may be able to help. But Could someone explain the general idea?

---

### Post by hyperAura on 2009-07-30
so what programming language r u using to write the program? or is it just a shell script u r trying to create?

---

### Post by Godd on 2009-08-02
Sorry bout reanimating a dead thread but I wasn't able to get to my comp for a few days.

I can't believe I didn't post the language I was programming in on the initial post.

That would be python. Sorry about that.

---

### Post by unutbu on 2009-08-02
Is this close?
[PHP]
#!/usr/bin/env python

def bin(num):
    """
    __source__='http://mail.python.org/pipermail/python-list/2000-March/028379.html'
    __author__='wheineman 1wheinemanNOwhSPAM at uconect.net.invalid'
    Returns a string binary representation of a number. For example
    bin(255) returns '11111111'.
    """
    returnValue = ''
    mask = 0
    i = 0
    while(1):
        mask = 1 << i
        if (i != 0) and (mask > num):
            break
        if (mask & num):
            returnValue = '1' + returnValue
        else:
            returnValue = '0' + returnValue
        i = i + 1
    return returnValue

astr=u'Unicode to binary'
bin_list=[bin(ord(elt)) for elt in astr]
print(bin_list)

# ['1010101', '1101110', '1101001', '1100011', '1101111', '1100100', '1100101', '100000', '1110100', '1101111', '100000', '1100010', '1101001', '1101110', '1100001', '1110010', '1111001']

print(''.join(bin_list))
# 101010111011101101001110001111011111100100110010110000011101001101111100000110001011010011101110110000111100101111001
[/PHP]

---

