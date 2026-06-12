---
title: "A very simple way to crypt your C++ chars."
date: 2011-01-02
forum: Programming Talk
---

### Post by hakermania on 2011-01-02
Ok, I know that this is really a simple way to crypt a char, but still, it is a way!

Ok, let's say that, via SSL encryption, a program needs to send a password, which is contained into the program as char passwd[]="text" and you have noticed that if you see the executable afterwards, all chars can bee seen as plain text (e.g. nano can see them clearly). So, you don't want this password to be stolen, and this is a nice way to do it:
1) First of all make this program and run it: ```

#include <iostream>
using namespace std;

int main()
{
    char pass[28]="This is an example password";
    for(int u=0; u<27; u++){
    pass[u]++;
    }
    cout << pass << endl;
}
```For this occasion, the output will be:
[COLOR=#000000][FONT=Monospace]```
Uijt!jt!bo!fybnqmf!qbttxpse
``` which doesn't look like "[/FONT][/COLOR]This is an example password" at all!
and now backwards:```

#include <iostream>
using namespace std;
int main()
{
    char pass[28]="[COLOR=#000000][FONT=Monospace]Uijt!jt!bo!fybnqmf!qbttxpse[/FONT][/COLOR]";
    for(int u=0; u<27; u++){
    pass[u]--;
    }
    cout << pass << endl;
}
``` This will output ```
This is an example password
```
Additionally, if somebody is curious to read your program will not see the password's string "This is an example password" but "[COLOR=#000000][FONT=Monospace]Uijt!jt!bo!fybnqmf!qbttxpse"[/FONT][/COLOR]
[COLOR=#000000][FONT=Monospace] :)[/FONT][/COLOR]
[COLOR=#000000][FONT=Monospace]I know that there are possibly better ways on encryption of chars but this is one :D):P
[/FONT][/COLOR]

---

### Post by MadCow108 on 2011-01-02
wow a caesar cipher real new.

besides that it is incredibly easy to break by just looking at it you can also just disassemble the "encryption" key by doing objdump -S on the file...

You can't savely save passwords in a file and still be able to decrypt them using just the information in the file.

---

### Post by MadCow108 on 2011-01-02
double post

---

### Post by ziekfiguur on 2011-01-02
If you want to encrypt anything, especially passwords, you should adhere to Kerckhoffs Law ([http://en.wikipedia.org/wiki/Kerckhoffs_law](http://en.wikipedia.org/wiki/Kerckhoffs_law))

---

### Post by hakermania on 2011-01-02
Ok, I think I was pretty clear that there are better ways of encrypting some text :)

---

### Post by worksofcraft on 2011-01-02
Yes, many encryption algorithms turn text into binary that doesn't look like text any more. Thus the coded message can't be transmitted or processed like the plain text could... e.g. utf-8 streams are no longer valid utf-8.

So your idea of making an encryption that still produces text can be useful in many situations.

Note: Long time ago I did that too and my creteria were as follows:
[LIST=1]
[*]encrypted algorithm is it's own inverse
[*]valid ascii text remains valid ascii text
[*]encryption algorithm controlled by a password
[*]there is no inverse to derive password from a deciphered message
[*]statistics on coded message give no information
[/LIST]

You could make some similar objectives and see if you can modify your simple algorithm to achieve them... and see if anyone can still crack it then!

It's all good fun :popcorn:

---

### Post by ziekfiguur on 2011-01-02
Sure, and if you use this for yourself, that's your problem. 
But i really don't think you should go around encouraging other people to do something like this with their passwords.

However, if you want to do something like this, maybe it would be better to make sure that all output characters are printable (now this won't be the case if you have a ~ in your password)
You could also use the build in program `tr' for this.
If you use ```
tr 'a-zA-Z' 'n-za-mN-ZA-M'
``` you get rot13 encoding

---

### Post by ziekfiguur on 2011-01-02
> **worksofcraft said:**
> 
[LIST=1]
[*]encrypted algorithm is it's own inverse
[*]valid ascii text remains valid ascii text
[*]encryption algorithm controlled by a password
[*]there is no inverse to derive password from a deciphered message
[*]statistics on coded message give no information
[/LIST]

Does the input have to be the same size as the output?
Otherwise, a combination of RC4 (or an other algorithm that's its own inverse) and base64 would work.
(Although RC4 isn't really considered safe enough anymore for most purposes.)

---

### Post by odyniec on 2011-01-02
> **hakermania said:**
> Ok, I think I was pretty clear that there are better ways of encrypting some text :)

You still suggested that your idea offers *some* level of security, which it doesn't, so you shouldn't be surprised that people corrected you.

There's a reason why "ciphers" like this are only used to hide joke punchlines and movie spoilers -- no effort required to "decipher".

---

### Post by worksofcraft on 2011-01-02
> **ziekfiguur said:**
> Does the input have to be the same size as the output?
Otherwise, a combination of RC4 (or an other algorithm that's its own inverse) and base64 would work.
(Although RC4 isn't really considered safe enough anymore for most purposes.)

No, it doesn't have to be the same at all... at the time I just liked it that way so one can use the same program to encrypt and to decrypt. Another advantage is that two people can exchange crypted messages using their own private keys without the other end having to know it:

[LIST]
[*]Person A applies encrytption key A, sends message to person B
[*]Person B applies encryption key B, sends it back to A
[*]Person A removes (applies again) key A, sends to B
[*]Person B removes (applies again) key B and now has the plain text
[/LIST]
Both ends only have to know their own keys so they can be 100% secure. 

In retrospect a proper dual key system would have been better (i.e. one keyword to encrypt and a different one to decrypt). The most important aspect to security was for me the use of a pseudo random sequence, but there are probably alternatives to that too :lolflag:

---

### Post by nvteighen on 2011-01-02
I wonder why would you like to set a hardcoded password, no matter whether you encrypted it with 128-bit RSA or not.

Alternative 1: You want to authenticate the user. So you want to check whether the user knows or not the password.

Solution: Use some hashing algorithm. Store the hashed password and check it against the hash value of whatever the user typed in. That way your program will actually never know your password.

Alternative 2: You want your program automate some login process for you.

Solution: Forget about it. Anyone with access to your program would gain automatic access to whatever you want that password to be used for.

---

### Post by ziekfiguur on 2011-01-02
> **nvteighen said:**
> I wonder why would you like to set a hardcoded password, no matter whether you encrypted it with 128-bit RSA or not.
128-bit RSA is a **very** bad idea. If you use RSA you should have at least 2048 bits keys. I suppose you meant aes.

---

### Post by hakermania on 2011-01-02
> **nvteighen said:**
> I wonder why would you like to set a hardcoded password, no matter whether you encrypted it with 128-bit RSA or not.

Alternative 1: You want to authenticate the user. So you want to check whether the user knows or not the password.

Solution: Use some hashing algorithm. Store the hashed password and check it against the hash value of whatever the user typed in. That way your program will actually never know your password.

Actually, I did this too :)

PS
I knew that I would have such comments but I did the best I could to avoid them... The title says "**very** simple" not just "simple" and I refer it twice, at the start and at the end of the first post, so I really thing that a user that would really liked to store a password that he really needs would not use this "**very simple**" way....

Don't be so negative....:)

---

### Post by nvteighen on 2011-01-03
> **ziekfiguur said:**
> 128-bit RSA is a **very** bad idea. If you use RSA you should have at least 2048 bits keys. I suppose you meant aes.

Oops... Honestly, I thought 128-bit RSA was enough. Thanks for the correction.

> **hakermania said:**
> 
I knew that I would have such comments but I did the best I could to avoid them... The title says "**very** simple" not just "simple" and I refer it twice, at the start and at the end of the first post, so I really thing that a user that would really liked to store a password that he really needs would not use this "**very simple**" way....

Don't be so negative....:)

I know you were quite explicit on that point. My point was that the idea underlying your code is bad, no matter how complex or simple the algorithm you use is. In other words, I wanted to point out that irrespective of your particular implementation, this shouldn't be done this way.

---

### Post by ziekfiguur on 2011-01-03
> **nvteighen said:**
> Oops... Honestly, I thought 128-bit RSA was enough. Thanks for the correction.
RSA encryption relies on the fact that it is very hard to factorize large numbers into their prime components. 
With 128-bit numbers this is far to easy with the computers we have nowadays.

this is what wikipedia has to say about it:
> As of 2010[update], the largest (known) number factored by a general-purpose factoring algorithm was 768 bits long (see RSA-768 ), using a state-of-the-art distributed implementation. RSA keys are typically 1024&#8211;2048 bits long. Some experts believe that 1024-bit keys may become breakable in the near term (though this is disputed); few see any way that 4096-bit keys could be broken in the foreseeable future. Therefore, it is generally presumed that RSA is secure if n is sufficiently large. If n is 300 bits or shorter, it can be factored in a few hours on a personal computer, using software already freely available. Keys of 512 bits have been shown to be practically breakable in 1999 when RSA-155 was factored by using several hundred computers and are now factored in a few weeks using common hardware.[9] A theoretical hardware device named TWIRL and described by Shamir and Tromer in 2003 called into question the security of 1024 bit keys. It is currently recommended that n be at least 2048 bits long.[10]

---

