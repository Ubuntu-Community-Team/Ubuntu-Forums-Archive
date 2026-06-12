---
title: "AES cipher help"
date: 2011-04-19
forum: Programming Talk
---

### Post by BSOD64 on 2011-04-19
Hi,

   I am trying to write my own 128 bit AES implementation in Java and I'm having trouble learning how AES works. I understand roughly how the cipher works but I don't understand how the key schedule is generated, how mixing the columns works, or how adding the round key works.

I would be glad if someone could explain these three things or show me some example code.

---

### Post by sanguinoso on 2011-04-19
Is this homework? And have you read the wikipedia articles relating to these things ? 

[http://en.wikipedia.org/wiki/Rijndael_key_schedule](http://en.wikipedia.org/wiki/Rijndael_key_schedule)

[http://en.wikipedia.org/wiki/Advanced_Encryption_Standard](http://en.wikipedia.org/wiki/Advanced_Encryption_Standard)

---

### Post by SeijiSensei on 2011-04-19
I would think poring over the [mcrypt]("http://mcrypt.sourceforge.net/") source code might be instructive.

---

### Post by NovaAesa on 2011-04-19
Uni homework I'm guessing? I'm only saying because I got pretty much this exact same assignment last week.

From my experience, to understand the round function better, you really need to find a good textbook. I found that wikipedia didn't quite have enough details. I've got Cryptography and Network Security by Stallings, it's pretty good, I would recommend seeing if your library has a copy.

---

### Post by BSOD64 on 2011-04-19
No this is not homework. I'm a freshman in high school and I don't think they give assignments like that in high school.

A while ago I was listening to a Security Now podcast (#125) and the AES cipher seemed kinda simple...  even weak.

So call me crazy if you like but I'm writing some special code to analyze it and hopefully break it!!!

If someone could find some working example code that I could port to my analyzer library or just answer my question without a bunch of mathematical gibberish like on Wikipedia I'd be very happy.

Update:

***WARNING***
Google says the following site is malicious so use noscript!

I found this: [http://www.hoozi.com/Articles/AESEncryption.htm](http://www.hoozi.com/Articles/AESEncryption.htm)

I'll try to port it.

---

### Post by twisted_steel on 2011-04-19
If you are looking for some example code, Bruce Schneier has the C version of Rijndael on [his website]("http://www.schneier.com/book-applied-source.html").  I do not recall if there were slight modifications to Rijndael for AES, but that would be something you would need to investigate.

As far as the key schedule, there is a flash video that might help if you have not seen it yet: [http://www.cs.bc.edu/~straubin/cs381-05/blockciphers/rijndael_ingles2004.swf](http://www.cs.bc.edu/~straubin/cs381-05/blockciphers/rijndael_ingles2004.swf)

I would look into getting a book from the library if you can find something relevant.  I thought Schneier's Applied Cryptography would have it, but could not find anything in the Table of Contents.

---

### Post by NovaAesa on 2011-04-20
> **BSOD64 said:**
> No this is not homework. I'm a freshman in high school and I don't think they give assignments like that in high school.

A while ago I was listening to a Security Now podcast (#125) and the AES cipher seemed kinda simple...  even weak.

Good to hear that you are doing self directed learning then, we need more motivated people like you :)

You're right, AES is very simple, this doesn't necessarily mean it's weak though (which is very lucky!).

---

### Post by BSOD64 on 2011-04-20
Does anyone know if the code I found is good?

[http://www.hoozi.com/Articles/AESEncryption.htm](http://www.hoozi.com/Articles/AESEncryption.htm)

key = {0x00 ,0x01 ,0x02 ,0x03 ,0x04 ,0x05 ,0x06 ,0x07 ,0x08 ,0x09 ,0x0a ,0x0b ,0x0c ,0x0d ,0x0e ,0x0f}
plaintext = {0x00 ,0x11 ,0x22 ,0x33 ,0x44 ,0x55 ,0x66 ,0x77 ,0x88 ,0x99 ,0xaa ,0xbb ,0xcc ,0xdd ,0xee ,0xff}
ciphertext = 69 c4 e0 d8 6a 7b 04 30 d8 cd b7 80 70 b4 c5 5a

---

### Post by BSOD64 on 2011-08-18
I got the cipher working a while ago.

Now to break it! ;)

Edit:

btw here's what really helped me: [http://www.cs.bc.edu/~straubin/cs381-05/blockciphers/rijndael_ingles2004.swf](http://www.cs.bc.edu/~straubin/cs381-05/blockciphers/rijndael_ingles2004.swf)

---

