---
title: "[python] wrap-around Caesar cipher"
date: 2010-03-07
forum: Programming Talk
---

### Post by memilanuk on 2010-03-07
Hello all,

Started working my way through Zelle's book (for the second time, got side-tracked), and I'm working on the exercises at the end of Chapter 4.  #9 in particular is giving me some grief.  If someone could nudge me in the right direction, I'd appreciate it.

Basically expanding on a Caesar cipher (previous problem), now the task is to make the values 'wrap around' from z to a rather than 'falling off' when at the end of the alphabet.

I got most of it myself, did a little digging on the 'Net for similar problems and found the rest...  The main thing that is bugging me a bit is that with this implemenation 'a' and 'z' end up having the same character substituted in for them, which could make for some really interesting deciphered text ;)

Here's the code I have thus far:

```

# caesar2.py
#   Ch. 4 Exercise #9
#   Write a program that can encode and decode Caesar ciphers.  The input
#   to the program will be a string of plain-text and the value of the key.
#   The output will be an encoded message where each character in the original
#   message is replaced by shifting it 'key' # of characters in the ASCII
#   character set.  For example, if 'ch' is a character in the string and 'key'
#   is the amount to shift, then the character that replaces 'ch' can be
#   calculated as: chr(ord(ch)+key).
#
#   Expanded to enable circular operation so as to prevent 'dropping off'
#   near the end of the alphabet.
#

import string

def main():
    # inform user of the purpose of the program
    print "This program will take plain-text plus a key and encode the"
    print "text using a Caesar cipher."
    print

    # get input from user
    plaintext = raw_input("Enter the plain-text phrase: ")
    key = input("Enter the key value (i.e. how many characters to shift): ")

    # initiate empty list
    msgList = []

    for ch in plaintext:                    # for each character in plaintext
        code = ord(ch) + key                # convert to ASCII num, add key value
        if ch.isalpha():                    # check if character is letter or other
            if code > ord('z'):             # if ascii num for code value is > ord('z')
                code = code - (ord('z') - ord('a')) # wrap back around to ord('a')
            msgList.append(chr(code))       # then append the shifted char to the list
        else:
            msgList.append(ch)              # if not alpha, don't bother converting

    ciphertext = string.join(msgList,"")    # concatenate all the char in the list

    # output results back to user, using string formatting
    print "The resulting cipher-text would be '%s'." % (ciphertext)

main()


```

If you have any suggestions on a better way to do the wrap-around so 'a' and 'z' don't get mixed up, I'm all ears.

TIA,

Monte

---

### Post by ssam on 2010-03-07
```

code = code - (ord('z') - ord('a'))

```
is a transformation that will map 'z' into 'a'. imagine the letters are numbers from a=1 to z=26.
```

code = code - (26 - 1)

```
will transform 26 (z) into 1 (a).

what you want is to assume a cycle. so that 27 would be 'a' again. so really you need a transform that turns 27 into 1. to express that in your code you could use:
```

code = code - (ord('z') + 1 - ord('a'))

```

---

### Post by memilanuk on 2010-03-07
Cool!  That does seem to have fixed it.

Thanks,

Monte

---

