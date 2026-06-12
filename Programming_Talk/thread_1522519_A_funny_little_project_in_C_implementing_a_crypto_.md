---
title: "A funny little project in C: implementing a crypto channel with AES"
date: 2010-07-02
forum: Programming Talk
---

### Post by Bachstelze on 2010-07-02
[center][[img]http://img684.imageshack.us/img684/5312/cryptography.png[/img]]("http://xkcd.com/442/")[/center]

So yesterday, a friend of mine who had been taking a C course last semester asked me if I had some ideas of small projects she could work on for practice. I was reading *Practical Cryptography* by Niels Ferguson and Bruce Schneier (an excellent read, by the way), and I remembered in chapter 8, there was a description of a secure data transmission channel using AES (for encryption) and SHA-256 (for authentication) that took roughly three pages of pseudocode. So I said "Hey, you could try implementing that in C, it should be quite challenging but still fun." And since I was kind of bored, I started working on it too.

Among other things, this requires a lot of work with pointers and buffers, as you need to move a lot of data around in memory (and of course since it's supposed to be secure, you have to put a lot of care in what you do and always clear the memory when you're done, so as to avoid leaking information), and some work with crypto libraries since you don't want to implement AES and SHA-256 yourself. And as a bonus, if you decide (like me) to use OpenSSL for that, you also learn a very important thing: how to deal with poorly documented libraries.

It wasn't very challenging for me (pardon the lack of modesty), but it was indeed a lot of fun for both of us (she's far from being done with hers yet, though), so if you are in a similar situation, wanting to use the C knowledge you acquired in class in some (kinda) real-world application, I highly suggest you grab a copy of the book, go to chapter 8, section 4, and start hacking. :)

For those interested, [here]("http://paste.ubuntu.com/459246/")'s mine. Took me roughly six hours, so someone with a semester's worth of C knowledge should be able to do it in at most a couple days.

```
firas@tsukino ~ % cc -lssl -lcrypto -Wall -Werror -pedantic -std=c99 -o securechannel securechannel.c
firas@tsukino ~ % echo 'Hello, world!' > hello.txt
firas@tsukino ~ % ./securechannel
No state file exists, generating a new one.
This may take some time... Done.
I will now write the initial state file to the disk. Make one copy of it before sending any message, and transmit it to the other party over a pre-existing secure channel.
Done.
Are you Alice or Bob? [a/b] ^Z
zsh: suspended  ./securechannel
firas@tsukino ~ % scp csc.state securechannel.c iori:
csc.state                                                                             100%  136     0.1KB/s   00:00    
securechannel.c                                                                       100%   28KB  28.1KB/s   00:00    
firas@tsukino ~ % fg
[1]  + continued  ./securechannel

Are you Alice or Bob? [a/b] a
Welcome, Alice, what do you want to do today?
[Encrypt a (m)essage/Encrypt a (f)ile/(D)ecrypt a file] f
Path of the file to encrypt? hello.txt
Encryption successful. Encrypted file saved as hello.txt.enc.
Writing the new state file to disk... Done.
Cleaning up memory... Done.
Exiting.
firas@tsukino ~ % cat hello.txt.enc 
N?dhg??G?@?)????WE
&#1303;?ZR??I?&F?B?O$??%                                                                                                      
firas@tsukino ~ % scp hello.txt.enc iori:
hello.txt.enc                                                                         100%   50     0.1KB/s   00:00    

firas@iori ~ % cc -lssl -lcrypto -Wall -Werror -pedantic -std=c99 -o securechannel securechannel.c
firas@iori ~ % ./securechannel 
A state file exists, loading the channel data from it.
If you want to create a new channel, delete or move away the existing state file.
Done.
Are you Alice or Bob? [a/b] b
Welcome, Bob, what do you want to do today?
[Encrypt a (m)essage/Encrypt a (f)ile/(D)ecrypt a file] d
Path of the encrypted file? hello.txt.enc
Decryption successful, Decrypted file saved as hello.txt.
Writing the new state file to disk... Done.
Cleaning up memory... Done.
Exiting.
firas@iori ~ % cat hello.txt
Hello, world!

```

---

