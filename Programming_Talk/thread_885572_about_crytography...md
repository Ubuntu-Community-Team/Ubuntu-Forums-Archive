---
title: "about crytography.."
date: 2008-08-10
forum: Programming Talk
---

### Post by MyRedz on 2008-08-10
help i need some concept about it.anyone here to help?
i need to scan some string from a file.this i know..but
then i need to do key function which functions to replace every character by some other one.as stated below..
like a is replaced by c , b is replaced by d and so on...
how to create this key function or file..anyone here to give me some brief intro about it.i need to do it for every char in that string..and publish it as a new file..

---

### Post by thirddeep on 2008-08-10
The easiest place to start is with ROT13.

[http://en.wikipedia.org/wiki/ROT13](http://en.wikipedia.org/wiki/ROT13)

Once you understand that, and can implement it in your required language, you can move on :-).

Thd.

---

### Post by jamescox84 on 2008-08-10
What programming language are you using?

---

### Post by ghostdog74 on 2008-08-10
> **MyRedz said:**
> help i need some concept about it.anyone here to help?
i need to scan some string from a file.this i know..but
then i need to do key function which functions to replace every character by some other one.as stated below..
like a is replaced by c , b is replaced by d and so on...
how to create this key function or file..anyone here to give me some brief intro about it.i need to do it for every char in that string..and publish it as a new file..
this is a caesar cipher. the easiest method to implement this is by associative arrays( dictionaries and hashes ) eg
```

awk 'BEGIN {
 ch["a"]="c"
 ch["b"]="d"
 ch["c"]="e"
 string="abc"
 m=split(string,a,"")
 for(i=1;i<=m;i++){
  printf "%s" ,ch[a[i]]
 } 
}'

```
of course, this is a very simple example only.

---

### Post by nvteighen on 2008-08-10
Search these forums and you'll find a thread started by me asking for the same in C... (it was my first post in the PT).

---

### Post by jamescox84 on 2008-08-10
```

# In Python:
# Takes a the original plain-text string, and the amount each character
# should be shifted by, and return the cipher-text
def caesar(plain, shift=1):
    cipher = ''
    for char in plain:
        cipher += chr(ord(char) + shift)
    return cipher

# Example:
print ceasar('hello, world', 4)
# Result:
# lipps0${svph

```

---

### Post by Lster on 2008-08-10
[http://en.wikipedia.org/wiki/Public_key_cryptography](http://en.wikipedia.org/wiki/Public_key_cryptography)?

---

### Post by ghostdog74 on 2008-08-10
> **Lster said:**
> [http://en.wikipedia.org/wiki/Public_key_cryptography](http://en.wikipedia.org/wiki/Public_key_cryptography)?

that's a different concept to what OP is requesting, although it does fall in the broad category of cryptography

---

### Post by mssever on 2008-08-10
We also had a programming challenge a while back involving the Vigenère cipher, which is a bit more involved than your example. But, it contains lots of example code. Search the forums for 'vigenère' and you'll find it.

---

### Post by tinny on 2008-08-10
We really need to know what language the OP is using. In Java you can use one of many ciphers in just a few lines of code to encrypt data.

As for cryptography concepts:

[Symmetric-key cryptography]("http://en.wikipedia.org/wiki/Cryptography#Symmetric-key_cryptography")
[Public-key cryptography]("http://en.wikipedia.org/wiki/Cryptography#Public-key_cryptography")

Symmetric-key cryptography is probably what you are looking for. (have a look at AES or DES)

---

### Post by lisati on 2008-08-10
Cryptography is a rich field, with possible schemes ranging from simple easily broken codes to more sophisticated stuff.

A simple "XOR" operation can be used without the need for arrays, and the same function to encode a string and decode it. (Down side: Easily broken!)

---

### Post by tinny on 2008-08-10
> **lisati said:**
> Cryptography is a rich field, with possible schemes ranging from simple easily broken codes to more sophisticated stuff.

A simple "XOR" operation can be used without the need for arrays, and the same function to encode a string and decode it. (Down side: Easily broken!)

Yep, if your a complete noob go with a simple [XOR cipher]("http://en.wikipedia.org/wiki/XOR_cipher")

---

### Post by MyRedz on 2008-08-11
> **jamescox84 said:**
> What programming language are you using?

orh i use programming c...
well i use the microsoft visual 6.0 compiler..
can u do some brief example about the code..it need to replace each char with an assigned one...sound of not in C++ language for me...

---

### Post by tinny on 2008-08-11
> **MyRedz said:**
> orh i use programming c...
well i use the microsoft visual 6.0 compiler..
can u do some brief example about the code..it need to replace each char with an assigned one...sound of not in C++ language for me...

Sounds like home work to me.

[http://ubuntuforums.org/showthread.php?t=717011](http://ubuntuforums.org/showthread.php?t=717011)

---

### Post by MyRedz on 2008-08-11
well  i know...i only want to know the basic concepts of doing that program ..is isn't against the rulez coz i is isn't my home works question...
well i just wanna a working example in c++ of that  Vigenère Ciphers...
the rest i will do myself..

---

### Post by jamescox84 on 2008-08-13
C is for Caesar

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

char * caesar(char *plain, char shift)
{
    char *cipher = malloc(strlen(plain) + 1);
    char *ret = cipher;

    while (*plain) {
        *(cipher++) = *(plain++) + shift;
    }
    *cipher = '\0';

    return ret;
}

int main()
{
    char * output = caesar("hello, world", 4);

    printf("%s\n", output);

    free(output);

    return 0;
}
```

---

