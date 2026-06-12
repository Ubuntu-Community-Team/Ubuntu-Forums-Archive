---
title: "Confused about the logic of public key encryption"
date: 2011-10-04
forum: New to Ubuntu
---

### Post by Cu Rua on 2011-10-04
I've read several books that mention and try to explain public key encryption, but I simply don't get it on a logical level. It seems like publishing a code integral to security is counter-productive, and I don't see what private keys have to do with anything. I'd like an explanation that isn't full of technical details on how to do it; like an analogy that explains how it works and *then* tying the technical stuff in. This is just a mental block, I don't want a tutorial with loads of command-line.

---

### Post by alphacrucis2 on 2011-10-04
> **Cu Rua said:**
> I've read several books that mention and try to explain public key encryption, but I simply don't get it on a logical level. It seems like publishing a code integral to security is counter-productive, and I don't see what private keys have to do with anything. I'd like an explanation that isn't full of technical details on how to do it; like an analogy that explains how it works and *then* tying the technical stuff in. This is just a mental block, I don't want a tutorial with loads of command-line.

The private keys are required to decrypt messages encrypted using the public keys. The system relies on mathemical functions that have inverses that are very difficult to compute in any plausible timeframe. I want to send you a message that only you can read? You send me your public key which I use to encrypt the message. You receive the message and can decrypt it using the private key. If the encryption algorithm is good, no one can derive the private key from the public key.

---

### Post by haqking on 2011-10-04
> **Cu Rua said:**
> I've read several books that mention and try to explain public key encryption, but I simply don't get it on a logical level. It seems like publishing a code integral to security is counter-productive, and I don't see what private keys have to do with anything. I'd like an explanation that isn't full of technical details on how to do it; like an analogy that explains how it works and *then* tying the technical stuff in. This is just a mental block, I don't want a tutorial with loads of command-line.

[http://www.security4noobs.com/pki/pki-101/](http://www.security4noobs.com/pki/pki-101/)

[http://www.security4noobs.com/pki/pki-102/](http://www.security4noobs.com/pki/pki-102/)

---

### Post by Cu Rua on 2011-10-05
So if each public key type has its own algorithm, and it's applied to all the public and private keys of that type, wouldn't cracking that algorithm release all the private keys of that sort, like figuring out a credit card number algorithm? Exactly how much time would it take to crack one? 
Also, if certificates go all the way up to, say, a government agency, wouldn't they automatically have privileged access to all their private keys and therefore any information sent using them? What keeps the top people under control? 
Does the spirit of open source apply to key making? What sort of people/companies supply keys?

---

### Post by Lisiano on 2011-10-05
There is also a element called a "seed", basically some random information that is being manipulated with those algorithms, if you don't know the seed, you can't get the keys.

Also, if you want an analogy, think of SSL. They are more or less the same on the principal (Certificate that you receive from the website is a public key and the cert they keep on their server is the private key)

---

### Post by AskTell on 2011-10-05
Having keys and changing ssh default port to 2222 or something that's not 22 will stop script kiddies from brute forcing

you can password protect your keys giving one extra line of defense for if you lose your unencrypted flash stick or have your key stolen through some other unforeseen event giving your time to make a new key.

I like to think of ssh keys as a jumbo sized password i don't need to enter every time :)

---

### Post by Paddy Landau on 2011-10-05
You want a non-technical analogy? Here you are...

Imagine Alice wants to send a secret message. You post Alice an *unlocked* safe, but only you have the combination. Alice puts her message into the safe, locks it, and posts it back to you.

Now, no one but -- not even Alice -- can open the safe and read it. The message is safe.

Safe =your public key
Combination = your private key

Now, for a complication...

When you receive your safe, how do you know it was Alice who actually wrote the message? Perhaps Bob intercepted the safe, wrote a false message pretending to be Alice, and sent it to you. (This is the "man-in-the-middle attack".)

Hmm...

Well, Alice signs her message using her signature. It's a clever signature that no one else can forge. When you open your safe, you check the signature in a verification book, and see that it really was from Alice.

So, you have received a message that no one but Alice could have sent, and no one but you can read.

Here's the clever bit...

Signature = Alice's private key
Verification book = Alice's public key

Notice how the public and private keys can perform two functions: making a message safe (encryption), and signing a message (signing).

Each message uses both people's private and public keys. Provided that Alice never reveals her private key, and you never reveal yours, you can send messages to each other secure in the knowledge that no one can read your messages to each other, and no one can fake messages from either of you.

It is also possible to sign messages without encrypting them. That's useful when you don't care if other people read your message, but people do care whether or not it is really from you. For example, websites using https use this method.

Complications:
[LIST]
[*]You need a way to verify that the public from Alice is really Alice's (and not Bob's pretending to be Alice).
[*]You must secure your private key carefully.
[/LIST]

HTH

---

### Post by JKyleOKC on 2011-10-05
Paddy's analogy was great. Here's another very similar one:

Instead of a combination lock, the container has a simple hasp that can take an ordinary padlock. You've distributed thousands of padlocks to which only you have the key, for anyone to use in sending messages to you. When Alice wants to send you a note, she finds one of your padlocks and uses it to lock the box.

The padlock is the public key; the physical key is your private one.

What makes it work is something the mathematicians call a "one-way function." These functions involve numbers of astronomical proportions, on the order of 2 to the 1024th power. The specific numbers used are also quite special, in that they are the product of exactly two "prime numbers" (which are numbers that have no factors except themselves and 1, such as 2, 3, 5, 7, 11, and so on) each of which is itself quite large. Those two prime factors are used as the public and private keys for the huge number that's fed into the one-way function to do the encryption.

Without BOTH of the prime factors it's impossible to know exactly what the huge number is, and without that huge number it's impossible to decrypt the message in less than a few thousand years. That's what makes it possible to publish one of them and remain secure. The exact one-way function used is what distinguishes one variety of public-key encryption from another.

---

### Post by matt_symes on 2011-10-05
Hi

Just wanted to say that there are a couple of very good posts in this thread. Well done!

Kind regards

---

### Post by Cu Rua on 2011-10-06
> **matt_symes said:**
> Hi

Just wanted to say that there are a couple of very good posts in this thread. Well done!

Kind regards

Agreed, the analogies made things much clearer, particularly the padlock one. I do still see the phenomenal pace of technology as a security risk, though-- it may take thousands of years to crack the codes with what we've got now, but what we've got now is constantly changing. There's also computers in universities trying to find the next prime number-- one would think it easy enough to switch them around to cracking keys. Or do I have the wrong impression on modern supercomputers?

---

### Post by JKyleOKC on 2011-10-06
The padlock analogy wasn't original with me; I got it from the book that explained the subject to me!

It's possible that technology might catch up in the foreseeable future; the boffins are experimenting with "quantum computing" that might cut the time required down to hundreds of years instead of thousands, but if it's even cut to tens of years that's still pretty secure for all practical purposes.

The number "2 to the 1024th power" is unimaginably huge, being something close to the number of inches in a light-year... At one time, the cosmologists were estimating the number of atoms in the entire universe at only 2 to the 136th!

The underlying problem is that the only known method for determining that a number is prime is the process of trial and error, attempting to divide the number by each known prime in turn until you get a remainder of zero, indicating that the number being tested cannot be prime. You only have to go halfway, though. That's still a huge amount of testing for each number, and each test uses one of the slowest computer algorithms known. Even with such shortcuts as ignoring all even numbers greater than 2, and all numbers whose digits add up to 9 (casting out nines, we used to call that trick), it still takes lots of time and doesn't lend itself to parallel processing very well either...

---

### Post by Paddy Landau on 2011-10-06
Well, even if you had a list of all the prime numbers up to that size, it still wouldn't much help you crack a public key -- you'd need to figure out which two prime numbers were involved, and there are zillions of possible combinations.

If you use military-grade encryption, you will be secure. For example, TrueCrypt allows you to encrypt using three different algorithms on top of each other. GPG and PGP allow you to choose a bit-length of up to 4096, which is an order of magnitude stronger than 2048.

Frankly, if someone were desperate to crack your key, they'd get a court order (if working with the police), torture you (if working for a corrupt government) or hire the Mafia to get it out of you (if unethical). Or, if you are susceptible, get a woman to charm it out of you.

BTW, I also like the padlock analogy. However, I am wondering what analogy would combine both encryption-decryption and signing-verification; the padlock and safe analogies both fall down there.

---

### Post by JKyleOKC on 2011-10-06
> **Paddy Landau said:**
> BTW, I also like the padlock analogy. However, I am wondering what analogy would combine both encryption-decryption and signing-verification; the padlock and safe analogies both fall down there.The more complete analogy, which I sorta mangled from memory, can be found on page 258 in my copy of "The Code Book" by Simon Singh (ISBN 0-385-49532-3) published in 1999 and priced at $14 USD when I bought it several years ago to learn more about the AmerIndian "code talkers" of WW1 and WW2.

It's a bit more complicated than I remembered. When Alice wants to send a note to Bob, she first creates the huge-number key and puts it inside the box, then locks the box with one of her own padlocks and sends it to Bob. When he gets it, of course, he cannot open it because he doesn't have the key to her padlock. He adds his own padlock to the hasp and sends the box back to her. Now she cannot open it either because of the added padlock, but she CAN unlock her own padlock, remove it from the hasp, and send the box back to Bob again. Since now only his own padlock is there, he can open the box, remove the huge-number key inside, and use it for the actual message.

The huge-number key itself does not have to be unique, just very large -- and it can be different for every message, thus becoming as secure as a one-time pad. The double-padlock dance simply serves to keep the actual encryption key secure while being exchanged between Alice and Bob.

Signing-verification simply puts a second box inside the first one together with the huge-number encryption key, with a similar two-lock dance used to open this additional box once the first one is opened. If the second box opens, the signing is verified, since it's locked with the "certification authority" padlock rather than with Alice's and anyone who trusts the signing process **HAS** to trust the CA involved. That was brought home to all of us quite recently when a Dutch CA lost its trustworthiness!

I recommend "The Code Book" quite highly to anyone interested in the whole subject of cryptography. It traces the whole history of the art, from the time of Julius Caesar right up to quantum computing (as it existed in 1999, when it was only a theory and had not yet been achieved to even the tiny degree now known to exist). And it's quite easy to read; any time that any maths are necessary, Singh presents them in clear and simple explanations.

Chapter 6, in particular, deals with public key techniques -- which were independently invented by three different groups (one in the UK and two in the USA), within a few months of each other in the mid-1950s, but two of those groups were kept quiet for decades by national governments.

---

### Post by bspymaster on 2011-10-06
"The Code Book" is definitely a good option. I strongly suggest it if you want to learn about ciphers.

---

### Post by proxy.qtz on 2011-10-06
In essence, and at it's most basic form, public key encryption is needed for street cred. If you don't use it, then you aren't cool.

---

### Post by Cu Rua on 2011-10-06
> **JKyleOKC said:**
> ... That was brought home to all of us quite recently when a Dutch CA lost its trustworthiness!

I recommend "The Code Book" quite highly to anyone interested in the whole subject of cryptography. It traces the whole history of the art, from the time of Julius Caesar right up to quantum computing (as it existed in 1999, when it was only a theory and had not yet been achieved to even the tiny degree now known to exist). And it's quite easy to read; any time that any maths are necessary, Singh presents them in clear and simple explanations.

Chapter 6, in particular, deals with public key techniques -- which were independently invented by three different groups (one in the UK and two in the USA), within a few months of each other in the mid-1950s, but two of those groups were kept quiet for decades by national governments.

What did the Dutch CA do? 
Singh is awesome, is he related to Nirupam Singh? I read most of his operating system book until the bad editing started to get to me... 
Would you mind giving a quick description of those techniques? Besides everything that's already been explained.

---

### Post by Paddy Landau on 2011-10-07
> **JKyleOKC said:**
> It's a bit more complicated than I remembered. When Alice wants to send a note to Bob, she first creates the huge-number key and puts it inside the box, then locks the box with one of her own padlocks and sends it to Bob. When he gets it, of course, he cannot open it because he doesn't have the key to her padlock. He adds his own padlock to the hasp and sends the box back to her. Now she cannot open it either because of the added padlock, but she CAN unlock her own padlock, remove it from the hasp, and send the box back to Bob again. Since now only his own padlock is there, he can open the box, remove the huge-number key inside, and use it for the actual message.
That still doesn't solve the question of a man-in-the-middle attack. There are only three ways around this that I know of:

[LIST=1]
[*]Use a trusted CA, which holds your public keys and which can verify your identity. (That is too expensive and revealing for most people living in dictatorships.)
[*]Hand over the keys personally when you meet, or use a trusted go-between.
[*]PGP (now owned by [Symantec]("http://www.symantec.com/business/theme.jsp?themeid=pgp")) used to have (maybe still does have) a clever device whereby it would create a hash from the public key consisting of words. After you exchange keys, you telephone each other and read each other's hash, thereby confirming that you each have the genuine key. That presumes, of course, that you recognise each other's voice.
[/LIST]

---

### Post by lisati on 2011-10-07
One idea I've read of in connection to the ever-increasing capabilities of technology is that if you choose your keys well, by the time the technology catches up, the need for the keys and privacy won't matter so much.

---

### Post by Paddy Landau on 2011-10-07
> **lisati said:**
> One idea I've read of in connection to the ever-increasing capabilities of technology is that if you choose your keys well, by the time the technology catches up, the need for the keys and privacy won't matter so much.
This is true, provided that the technology continues to increase at its current accelerated rate. However, should there be a quantum leap -- either a new relevant mathematical discovery regarding prime number fractionation, or a new computing technology -- then you are at risk.

There is only one foolproof encryption method so far discovered, and it uses the esoteric properties of quantum mechanics. In this method, an encrypted message can be transmitted exactly once and has a 50% chance (as I recall) of arriving uncorrupted. If it arrives corrupted, the message needs to be re-encrypted and sent again. The message cannot be decrypted by anyone other than the recipient, not even theoretically. Furthermore, the message reveals when a man-in-the-middle attack has taken place. But this technology is all very new and as-yet unavailable outside the laboratory. I confess I do not understand how it works.

---

### Post by JKyleOKC on 2011-10-07
> **Cu Rua said:**
> What did the Dutch CA do?As I recall the events, the CA, DigiNoTar, issued a certificate to someone else (apparently to crackers from Iran or possibly that govenment) in the name of Google. In other words, issued a fake certificate.

Investigation indicated that it was actually done by "crackers" who broke into the site, rather than by the CA's own people, but the event made it clear that no certificate from them could be trusted due to their lack of security.

This was a clear violation of trust, so almost all of the operating systems (Windows, Apple, and most of the *nix distros) removed that CA from their built-in list of CAs to be trusted.

This all happened within the past month or so, becoming public in late August; it was made even more complex since the CA involved was also the CA assuring everyone of the identity of a (required) Dutch-government site!

---

### Post by JKyleOKC on 2011-10-07
> **Paddy Landau said:**
> That still doesn't solve the question of a man-in-the-middle attack.I believe that this is the whole purpose of having CAs; the "web of trust" starts from a top-level certification authority whose address is built into your operating system and thus cannot be faked by a man in the middle. The identity of any subsidiary CA is vouched for by a top-level CA, much as the DNS system delegates the translation of a URL into an IP address starting from the root servers. Eventually, you reach a CA that vouches for the identity of the person or firm you're trying to reach.

That assurance of identity, rather than a huge encryption key, is what's in the second box locked with a CA's public key.

As the DigiNoTar incident(s) have demonstrated, the system does NOT prevent MITM attacks if a top-level CA is breached. However, so far the number of such detected breaches has remained quite small; small enough that the system still is believed to be viable. That can always change, of course. 

So long as greedy humans exist, they will find ways to prey on others. Members of our species, history tells us, are predators by nature, and prey on their fellows as well as other species. A perfect system is impossible to achieve; we have to work with the best we can do even if it's not as good as we would like.

EDIT: Yes, CAs are a bit costly. I've never used one for exactly that reason. However they do work for firms that I do business with, such as my bank or the utility companies that I pay through their web sites. Few of us are really concerned about such matters when it comes to visiting forums, or casual Email contacts...

---

### Post by Paddy Landau on 2011-10-07
> **JKyleOKC said:**
> As I recall the events, the CA, DigiNoTar, issued a certificate...
The real loss of trust was not that they were hacked (everyone is susceptible), but that they covered it up for a significant time instead of telling everyone immediately.

If they had told everyone, patches would have been implemented worldwide within hours.

[There is a thread]("http://ubuntuforums.org/showthread.php?t=1836052") giving more specific information.

---

### Post by Chronon on 2011-10-08
> **Paddy Landau said:**
> This is true, provided that the technology continues to increase at its current accelerated rate. However, should there be a quantum leap -- either a new relevant mathematical discovery regarding prime number fractionation, or a new computing technology -- then you are at risk.

There is only one foolproof encryption method so far discovered, and it uses the esoteric properties of quantum mechanics. In this method, an encrypted message can be transmitted exactly once and has a 50% chance (as I recall) of arriving uncorrupted. If it arrives corrupted, the message needs to be re-encrypted and sent again. The message cannot be decrypted by anyone other than the recipient, not even theoretically. Furthermore, the message reveals when a man-in-the-middle attack has taken place. But this technology is all very new and as-yet unavailable outside the laboratory. I confess I do not understand how it works.
That's not quite how it works.  Quantum key distribution uses transmission of quantum bits to establish a shared set of random, classical bits (a one-time pad).  One time pad is unbreakable by any algorithm, it only requires a random process to generate a sequence of bits that can be shared by two people.  This sequence of bits can be used to encrypt a message by simple bitwise addition.  The original message is recovered by bitwise addition of the same one-time pad.  Security comes from the randomness of the pad.  A cracker may as well run a random number generator and simply hope to get lucky.

The quantum part of quantum key distribution relies on the no-cloning theorem.  An attacker cannot measure the quantum state of a qubit and exactly reproduce the quantum state.  This lack of fidelity will show up as an error rate for qubits that were generated and measured in the same basis (by sender and receiver, respectively).  

The way it works is that Alice (the sender) prepares and sends a stream of qubits to Bob, randomly changing the logical state as well as the basis (polarization of a single photon, for example).  After enough bits have been transmitted, they get on a public, classical channel and Bob reports which basis he used for each measurement.  Alice and Bob keep only the logical values where their choice of basis coincides.  According to theory, there should be perfect correlation between their sets of logical values.  To check for the presence of an attacker they simply sacrifice a small portion of their key (say 100 bits) and announce the logical values over the public channel.  If the error rate is above a certain rate then they know that the channel is compromised and they abort the operation.  If the error rate is below threshold then they know that no attacker is listening and they can use the remaining set of bits as a one-time pad.  Once Alice and Bob share a one-time pad they can use it to securely send any message of equal length.  It's important to recognize that no sensitive data is sent until Alice and Bob are sure that they alone share a specific sequence of random bits.

There are other variations -- for example, by using a source of entangled qubits, Alice and Bob can perform a procedure called entanglement purification to reduce the amount of information possessed by an attacker (Eve), provided the error rate is below a certain level.

---

### Post by Paddy Landau on 2011-10-08
> **Chronon said:**
> That's not quite how it works...
Thanks for the clarification. It seems really complicated. I had read that research had developed a totally unbreakable method, but you're saying that it can (in theory) be cracked. OK, I'm not an expert in this!

---

### Post by Chronon on 2011-10-08
> **Paddy Landau said:**
> Thanks for the clarification. It seems really complicated. I had read that research had developed a totally unbreakable method, but you're saying that it can (in theory) be cracked. OK, I'm not an expert in this!

I'm saying that the technique of quantum key distribution can assure you when the bits you have shared with someone else are secret (because quantum bits cannot be duplicated perfectly).  Once you are confident of this, you can use this one-time pad to encrypt arbitrary data.  This encryption cannot be broken by any algorithm.  There is an infinitesimal probability that an attacker could guess the random bit sequence contained in the one-time pad, but this doesn't represent a tangible security risk and it is absolutely the most secure encryption protocol since it is not subject to attack by any algorithm.

With the second technique involving entangled qubits, Alice and Bob can, additionally, perform entanglement purification until they share a pure state.  I.e., they reduce the amount of information held by Eve to zero.

---

### Post by Cu Rua on 2011-10-09
:-D This stuff is giving me the giggles. 
Still haven't gotten an answer to one question, though: what sorts of people are distributing both keys and certificates? All I've gathered so far is a few big corporate names and a vague impression of government involvement. 
Is any of this similar to the Wikileaks security that prevents anyone from tracing the source of the info sent to their servers? I remember reading something about a world-wide network of computers that the messages randomly bounce around before arriving at the main servers, something akin to money laundering through banks. 
Also, I think it's always been a foregone conclusion that anything one person builds, another can break, so nothing is absolutely airtight--- but it's still fun to see all the ways people try to get around human nature. On that note, wouldn't malicious parties simply monitor everyone who's ever used encryption, find the physical location of their computers, and manually attach a tracking device that relays all activity straight to the bad guys without all the song and dance of cracking quantum algorithms? 
How hard would it be to build a back door into a key program and just use that? How would we know if somebody had done that?

---

### Post by JKyleOKC on 2011-10-09
> **Cu Rua said:**
> Still haven't gotten an answer to one question, though: what sorts of people are distributing both keys and certificates? All I've gathered so far is a few big corporate names and a vague impression of government involvement.When you access a "secure site" in your browser, using "https" instead of simply "http" (or just see the padlock icon or a warning message) there's at least one certificate involved. These are usually issued by some corporation such as Network Solutions Inc. or Thawte, but it's possible to create your own certificate although there's no reason for anyone else to trust a "self-signed" version. The answer to your question, then, is "any sort of person or firm, both honest and dishonest."> **Cu Rua said:**
>  
Is any of this similar to the Wikileaks security that prevents anyone from tracing the source of the info sent to their servers? I remember reading something about a world-wide network of computers that the messages randomly bounce around before arriving at the main servers, something akin to money laundering through banks.The only similarity is that both involve the word "security" and that can mean anything from "use armed guards" to "keep it hidden in plain sight." As for the analogy to money laundering, that "random" bounce is in fact how the internet works; it's not at all random, though. each of its component networks connects to others, so that eventually there's a possible route from you to most anywhere else on the planet -- unless one of the interconnections gets blocked for some reason. That's why security is needed -- at any point along the way, the operators of the current network can copy off any traffic they want to.
> **Cu Rua said:**
> wouldn't malicious parties simply monitor everyone who's ever used encryption, find the physical location of their computers, and manually attach a tracking device that relays all activity straight to the bad guys without all the song and dance of cracking quantum algorithms?That can be and has been done; the hard parts are finding the location, and gaining physical access. The location is usually found by asking the service provider, and the tracking device isn't needed. Just install malware such as a key logger that does the capture. That's easy enough to do over the net with a drive-by download from an infected web site.

The authorities can simply confiscate the computers and in some countries torture the suspect into a confession. In less severe situations, the malicious parties just trick you into giving them the information they want, such as your security passwords.
> **Cu Rua said:**
>  
How hard would it be to build a back door into a key program and just use that? How would we know if somebody had done that?Search Google for Dennis Ritchie's remarks on being awarded the Turing Prize for lifetime achievement. He, along with Ken Thompson, created the original Unix system on which Linux is based and the C programming language with which to do so, and in his acceptance speech, told of doing just that to the original C compiler. He made it create a back door that gave him full access to any program built using that tool. Many folk suspect that some or all of the current "security" solutions have such back doors inserted at the demand of national governments, but none have been outed to public view.

Security is a process, not a bandage. Walls, locks, keys, and encryption don't make things secure; a careful approach and suspicious mind must be added into the mix -- and even then, absolute security isn't achievable. We have to settle for "good enough" which means that my bank account access only needs to stay secret for so long as I still hold that account...

---

### Post by Cu Rua on 2011-10-10
> **JKyleOKC said:**
> Many folk suspect that some or all of the current "security" solutions have such back doors inserted at the demand of national governments, but none have been outed to public view.

To the trained eye, how visible are back doors? Would a hacker be able to take apart whatever bits and pieces they receive to take a look? 
Also, google failed, I can't find any comments on back doors Ritchie put into C.

---

### Post by mastablasta on 2011-10-10
Here is some good explanation abotu public key security...[http://wald.intevation.org/frs/download.php/775/gpg4win-compendium-en-3.0.0-beta1.pdf](http://wald.intevation.org/frs/download.php/775/gpg4win-compendium-en-3.0.0-beta1.pdf)
 
well truecrypt for example uses this public key/&#353;rivate key i believe and you can check on wiki how teams ofg experts tried to break the encription and had to give it up in the end after a couple of months work....
 
[http://en.wikipedia.org/wiki/TrueCrypt](http://en.wikipedia.org/wiki/TrueCrypt)
 
>  
Operation Satyagraha
In July 2008, several TrueCrypt-secured hard drives were seized from a Brazilian banker [Daniel Dantas]("http://en.wikipedia.org/wiki/Daniel_Dantas"), who was suspected of financial crimes. The Brazilian National Institute of Criminology (INC) tried unsuccessfully for five months to obtain access to TrueCrypt-protected disks owned by the banker, after which they enlisted the help of the [FBI]("http://en.wikipedia.org/wiki/FBI"). The FBI used [dictionary attacks]("http://en.wikipedia.org/wiki/Dictionary_attack") against Dantas' disks for over 12 months, but were still unable to decrypt them.[[SIZE=2][34][/SIZE]]("http://en.wikipedia.org/wiki/TrueCrypt#cite_note-Dantas-33")

 
you can also check how it is possible to break the encryptions under certain very specific circumstances.

---

### Post by Paddy Landau on 2011-10-10
Also, install [WOT (Web Of Trust)]("http://www.mywot.com/") in your Firefox or Chromium browser. WOT is a community-driven system. Although it is far from perfect, it has occasionally given me a heads-up when visiting a website.

---

### Post by JKyleOKC on 2011-10-10
> **Cu Rua said:**
> To the trained eye, how visible are back doors? Would a hacker be able to take apart whatever bits and pieces they receive to take a look? 
Also, google failed, I can't find any comments on back doors Ritchie put into C.I goofed; it was Ken Thompson who spoke on "Trusting Trust." And the back door he describes was theoretical, never actually in the compiler. Try this link for the text of his speech: [http://cm.bell-labs.com/who/ken/trust.html](http://cm.bell-labs.com/who/ken/trust.html) Note that he gives sample code for doing this!

By definition, a back door isn't visible at all. Sometimes they can be detected using such tools as Wireshark (formerly called Ethereal), which log all packets sent or received from a system. However normal net use involves thousands of such packets every hour or less, so finding those sent by a back door is like looking for a specific grain of sand at the beach -- assuming that the back door lets them be logged at all.

---

### Post by Cu Rua on 2011-10-12
I see... So what we could really use is a program that learns to recognize a few bits of suspicious code out of some ungodly number of lines and points it out to people and demonstrates how it works, then use that to examine any program we wanted. Theoretically. It doesn't sound very difficult to do, it just would take a while, right?

---

### Post by JKyleOKC on 2011-10-12
We already have such programs -- they're called "anti-virus" packages with heuristic (learning) capabilities. Sometimes they actually work, too. However they tag innocent programs quite often, also. Within the past year there's been at least one incident in which a false positive for an AV program wiped out a critical system file, totally disabling the users' systems.

---

### Post by Cu Rua on 2011-10-14
Wouldn't the best place for a back door be in critical software? Maybe the virus scan behaved exactly the way it was supposed to.

---

### Post by ice60 on 2011-10-14
i haven't read the whole thread and see you're talking about something else now. 

you could try listening to this podcast.
[http://www.grc.com/sn/sn-034.htm](http://www.grc.com/sn/sn-034.htm)

there are probably youtube videos too.

---

### Post by Cu Rua on 2011-10-20
Okay, back on topic: Would a back door be able to log every key made? One would think it a very useful thing to have a database full of keys, both public and private.

---

### Post by Paddy Landau on 2011-10-20
> **Cu Rua said:**
> Would a back door be able to log every key made?
The back-door would do whatever the programmer told it to do. A typical back-door would be to allow someone else to decrypt.

Generally, open source (regardless of whether it is free or not) does not have back doors, because programmers would spot them and publicise the fact. Closed source we have to take on trust. Ubuntu and TrueCrypt are both open source.

---

### Post by Cu Rua on 2011-10-23
Realistically, how many programmers go through program code line by line, looking for nasty bits?

---

### Post by wannabegeek on 2011-10-23
I think it's hard for people and myself,  to imagine that an equation can be generated with ease, that is very hard to factor....you pass out the cypher generating object, but that doesn't help you factor it....

---

