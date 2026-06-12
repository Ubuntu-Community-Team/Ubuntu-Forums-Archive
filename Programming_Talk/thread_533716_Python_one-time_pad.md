---
title: "Python one-time pad"
date: 2007-08-24
forum: Programming Talk
---

### Post by AZzKikR on 2007-08-24
Out of boredom, I created a one-time pad application to encrypt and decrypt **printable** messages. Click [here ]("http://en.wikipedia.org/wiki/One-time_pad")for more information on one-time pads. It's a very easy encryption algorithm, and the decryption is even easier (just make the + a -, and you're finished :D). It's probably fun for beginners in Python (like me) to check what on earth is going on.

Check it out. I'm gonna add more functionality over time. Also, a few things are missing. For instance, a one-time pad requires that the length of the key to encrypt the message equals the message length. In Python words: len(message) == len(key). I made no check for that. It's quite functional though, and if you want extreme secrecy of messages, this is the thing to use :) And oh yeah, newlines/carriage returns do not work either. Gotta find a way for that.

```
"""One-time pad encrypter and decrypter.

These two methods can encrypt printable text message using the specified key.
"""

startchar = ' ' # 32
endchar = '~'   # 126
                # see www.asciitable.com. bytes 32-126 are generally 
                # printable ascii characters
modular = ord(endchar) - ord(startchar) + 1

def encrypt(message, key):
    """Encrypts a message with the specified key.
    
    The message should be any printable text message besides any whitespace characters
    other than the space (0x32). The key is used to encrypt the message with. Note 
    that the length of the message MUST equal the length of the key (due to the 
    requirement of a one-time pad."""
    
    ret = ""
    for i in range(len(message)):
        messagechar = ord(message[i]) - ord(startchar)
        keychar = ord(key[i]) - ord(startchar)
        calculatedchar = (messagechar + keychar) % modular
        convertedchar = chr(calculatedchar + ord(startchar))
        ret += convertedchar
    return ret

def decrypt(message, key):
    """Decrypts the given encrypted message using the specified key.
    
    The message should contain any printable text message besides any whitespace characters
    other than the space (0x32). The key is used to encrypt the message with. Note, like
    in encrypt(message,key), the length of the message MUST equal the length of the key
    as well, and this time because of the one-time pad requirement."""
    
    ret = ""
    for i in range(len(message)):
        messagechar = ord(message[i]) - ord(startchar)
        keychar = ord(key[i]) - ord(startchar)
        calculatedchar = (messagechar - keychar) % modular
        convertedchar = chr(calculatedchar + ord(startchar))
        ret += convertedchar
    return ret
```

Example:
```
text = "Ubuntu > Windows! Well, at least I think so."
key =  "dSF34%^8$4@#@)(2#-=2#4jsVDkljwqhweiuh@Wskjha"

cipher = otp.encrypt(text, key)
original = otp.decrypt(cipher, key)

print "Encrypted:", cipher
print "Decrypted:", original
```

This will output:
```
Encrypted: :6<")z^V$k*q%x &$-two!vs89kYPYe]w/ijQ*F_k^Xo
Decrypted: Ubuntu > Windows! Well, at least I think so.
```

---

