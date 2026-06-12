---
title: "Need help with an encryption scheme"
date: 2013-06-04
forum: Programming Talk
---

### Post by zobayer1 on 2013-06-04
I am trying to implement an encryption scheme, here is what I am trying to do,

1. I will have several strings (payload) to be encrypted so that only my client program can decrypt it.
2. I need to do it in a way that even if the algorithm is compromised, others cannot generate similar encrypted strings, i.e. ensuring that only those strings will pass the client test which I have encrypted.

These two are the basic requirements.

Now this is what I am trying:

1. Obviously RSA came to mind first, encrypt the payload with a private / public key, and on the client side (many clients, anyone can validate) it will be decrypted using public / private key.
2. Computing CRC wrt a hidden base and generating the string, doesn't seem like a good idea though.

None of these two can ensure the second requirement. Also, there is very little or no randomness in keys, for example, different client cannot use different keys, because any encrypted messages should express the same meaning on every client. We can safely assume that, duplicating situations will never occur, like no two clients will ever try to decrypt the same message at the same time.

Is there any way that payloads can be self authenticating? Like even if someone else forge similar strings using same algorithm, it will still not pass. What information should I include in the payload to ensure this? I thought about salting, but salting doesn't seem like a easily reversible idea unless the client is notified about the salting procedure.

So, please provide any suggestion on how this should be done, or what I need to study. If you need more clarification, I can explain more.

Thanks in advance ;)

---

### Post by sudodus on 2013-06-04
Why is it not enough with the 'standard' pgp encryption and signature system?

a1. You encrypt a message with the receiver's public key.
a2. You sign a message (encrypted or not encrypted) with your private key.

b1. The receiver decrypts a message with her/his private key.
b2. The receiver verifies your signature with your public key.

You need to think about the chain of trust, so that you can trust that it is the public key of the receiver, that you use, and that the receiver can trust that it is signed with your public key. I suggest that you read up about pgp (and gnu pgp, implemented in the program gpg).

---

### Post by zobayer1 on 2013-06-04
Thanks for such a quick reply. Yes, there must be some point where I need to trust the client. I think pgp encryption is almost same thing as RSA (I didn't have any formal course on cryptography, so pardon my dumbness, I just know a few algorithms). This process is fine, except to the point that, it forces all the clients to have the same key, because as I have mentioned earlier, any specific message must produce the same output at every client, I mean, encryption is not specific client targeted, and this imposes a strict dependency (or whatever the actual term might be) with the server program. It will be nice if there is a way through which I could change key pairs time to time, so that even if someone knows the algorithm, wont be able to make fake encrypted strings for any payload.

If it is not possible, then I will have to implement pgp, but please suggest any workaround if we can avoid this sort of hard binding. How about AES with single key?

---

### Post by sudodus on 2013-06-04
How hard would it be to create different encryptions for all customers automatically (using the specific public key of each customer)? It can be done with a shell script.

The decrypted file at each customer could be the same, if that is what you want. Or you could send a different key to each of them.

Maybe you need no course about cryptography, but you could ***read a tutorial about pgp that you find on the internet***, or you can simply read the manual pages of gpg

```
 man gpg
```
```
 info gpg
```

---

### Post by zobayer1 on 2013-06-04
> **sudodus said:**
> How hard would it be to create different encryptions for all customers automatically (using the specific public key of each customer)? It can be done with a shell script.

The decrypted file at each customer could be the same, if that is what you want. Or you could send a different key to each of them.

This is where I am confused. Lets picture this scene,
I have a server called servar1 and three clients client1, client2, client3
Let server's private and public key is Spr and Spb
Similarly, clients private and public keys are {C1pr, C1pb}, {C2pr, C2pb}, {C3pr, C3pb}

Now, lets assume I have two strings:
"hello world"
"I said good day sir"

What I need to do is, server will generate two encrypted strings only, say Str1, Str2.
Now, if C1 gets Str1, it will read the same as if C2 gets Str1 and so on.

Here I am not sending the encrypted string to any particular client. I am just creating a pool of encrypted strings and clients will pull from it, and read whats in it. So how can having different (dynamically generated) key pairs for clients help me here? I can use Spr to encrypt and all the clients will use Spb to decrypt, its the same as having same key value pairs for all the customers.

I hope you don't mind helping a bit more :)

---

### Post by sudodus on 2013-06-04
I think you must explain what kind of service you are running. Are you distributing software, information music or something like that, or is it some kind of game, lottery or something like that?

In the first case it should work to distribute it encoded differently with the public keys of each client. But in the second case it is different. Is it like the clients are drawing cards, and they should not know what card it is until they have drawn it (and turned the face up). But is this case, does it make any difference, if all clients have the same key? They won't see each other's cards anyway unless they show them to each other (playing like teams).

---

### Post by ofnuts on 2013-06-04
If all clients can read the same string encrypted by the server, then just have the server encrypt using its private key and have the client decode using the server's public key.

If you want something secure between clients: on connection each client generates a random key for some symmetric encryption algorithm and encrypts it using the servers public key. The server decodes it using its private keys and uses it with the symmetric encryption during the ensuing exchanges (AFAIK this is what HTTPS does, more or less). One advantage of this is that symmetric algorithms are much less CPU-intensive).

---

### Post by zobayer1 on 2013-06-04
Yes [sudodus]("http://ubuntuforums.org/member.php?u=1499021"), you are correct, its of the second type. And of course there is no difference. I was actually looking for a way to avoid using key based encoding. But I guess that will not be sufficiently secure. Now the only problem is if the key pair is changed, all the remaining string in the pool must be discarded and re-generated with new encryption keys.

Btw, thanks for your help :D

[ofnuts]("http://ubuntuforums.org/member.php?u=1382218"), nope, clients wont communicate among them. But thanks for the idea. :)

---

### Post by sudodus on 2013-06-04
> **ofnuts said:**
> If all clients can read the same string encrypted by the server, then just have the server encrypt using its private key and have the client decode using the server's public key.

If you want something secure between clients: on connection each client generates a random key for some symmetric encryption algorithm and encrypts it using the servers public key. The server decodes it using its private keys and uses it with the symmetric encryption during the ensuing exchanges ([COLOR=#ff0000]AFAIK this is what HTTPS does, more or less[/COLOR]). One advantage of this is that symmetric algorithms are much less CPU-intensive).

*zobayer1*, I think that you can also consider if this would be a good solution for you and your clients: Set it up to only connect via HTTPS (secure connection). At least it should work if the clients use their own computers (maybe not with computers at internet cafés, depending on the time-scale of the game).

---

### Post by trent.josephsen on 2013-06-04
You don't have to combine RSA encryption with RSA signing. You can encrypt the messages using a symmetric (shared-key) algorithm, sign them with the server's private key, and distribute the server's public key to the clients for verification purposes. That way you only have one key pair to worry about (plus whatever you choose for the symmetric encryption) and you don't have to encrypt the same message separately to different clients. Of course, you still have to figure out how to distribute the symmetric key. If that needs to be done securely as well, you're basically reinventing SSL/TLS at that point.

What's the attack vector here? Compromised server, malicious fake server masquerading as the original, eavesdropping? Not much can protect you from a compromised server, unless you can tell the clients how to identify malicious patterns. RSA signing solves the second one. Any modern encryption standard (properly applied) will prevent eavesdropping. What exactly are you protecting against?

---

### Post by zobayer1 on 2013-06-05
Yah, if the server is compromized then those situations are out of my hands. The only major problem here is the source code of the program can get exposed, and thus exposing the private key as well. Can you suggest how the keys can be kept protected even if the source code is exposed? Is storing those data in a database the only solution?

---

### Post by trent.josephsen on 2013-06-05
NEVER EVER store auth data (tokens, keys, passwords, etc.) in code! It's a maintenance problem and a huge security hole.

I tend to put stuff like this in an rc-file, or prompt the user for it on startup. Depends on the application. If you're using PGP, though, you'll probably just invoke the GnuPG binary and let it do its own storage thing (keys saved in ~/.gnupg). The symmetric key can be anything as long as the server and clients all know it.

The fact that you ask the question raises another, though. Can rc-files or databases be any more secure than code? I mean, if you did store the private key in the source code for the server, presumably you wouldn't just hand out the source without deleting the sensitive information, so are you expecting that the source code can be exposed in some way that doesn't compromise the server as a whole? (Of course, if you don't store keys in it, you can put the source on Github or print copies and leave it in public restrooms for all the difference it makes to security.)

---

### Post by zobayer1 on 2013-06-05
> **trent.josephsen said:**
> The fact that you ask the question raises another, though. Can rc-files or databases be any more secure than code? I mean, if you did store the private key in the source code for the server, presumably you wouldn't just hand out the source without deleting the sensitive information, so are you expecting that the source code can be exposed in some way that doesn't compromise the server as a whole?

Yeah, there is a chance that the source code can be exposed without the server being compromised and vice-versa. for my situation, it's very less likely for both being exposed at the same time. So I guess storing these critical information on separate locations like you mentioned should reduce the risk significantly. If both are compromised (i.e. code and database) there is not much can be done anyway. Instead of using separate rc-file, I am storing them in a database right now.

P.S. on a side question, how can I mark the thread as SOLVED, as far as I remember the option was in Thread Tools menu, but can't find it anymore there.

---

### Post by sudodus on 2013-06-06
Edit the first post, go advanced, and change the prefix to SOLVED (I think this work-around is still working)

---

