---
title: "how do I recognize voice using C++?"
date: 2010-02-15
forum: Programming Talk
---

### Post by shababhsiddique on 2010-02-15
Can anyone tell me how to recognize voice/speech and convert to string?

I need a program to get a string as input through microphone. Using ubuntu and C++. used espeak to speek out at text. need the reverse.

---

### Post by night_fox on 2010-02-15
Do you want a speech recognition API, or do you want to know how to do it yourself in c++?

---

### Post by Ferrat on 2010-02-15
Speech2text is a hard nut to crack and totally different from text2speech. 

What you need is first a input, that means a codec and a sampler that can put what is said in to a temporary file and that's the "easy" part, now for the hard one, you now need to build a workable pattern recognition software that can find and isolate different parts of the sample in the temp file and this is probably one of the hardest things you can do, if it's just for you then it's easier but not easy, then you can use predetermined samples and maybe work from that but if you want wide usage for multiple users you need to have a very good understanding of patter recognition, sound handling as well as some AI since the program often will have to venture a guess based on the pattern.

---

### Post by shababhsiddique on 2010-02-15
> **Ferrat said:**
> Speech2text is a hard nut to crack and totally different from text2speech. 

What you need is first a input, that means a codec and a sampler that can put what is said in to a temporary file and that's the "easy" part, now for the hard one, you now need to build a workable pattern recognition software that can find and isolate different parts of the sample in the temp file and this is probably one of the hardest things you can do, if it's just for you then it's easier but not easy, then you can use predetermined samples and maybe work from that but if you want wide usage for multiple users you need to have a very good understanding of patter recognition, sound handling as well as some AI since the program often will have to venture a guess based on the pattern.

thanks for the reply. Yes i have guessed that would be difficult. But I do not wish to concentrate in the conversion. I need a ready library as fox said. So can you help me out finding one? do you know any library that I can use? is there any?

---

### Post by shababhsiddique on 2010-02-15
> **night_fox said:**
> Do you want a speech recognition API, or do you want to know how to do it yourself in c++?

If the API can be used in C program then its good to use API. If I cannot then do-it-yourself is my choice. Help me out in both.

---

### Post by Ferrat on 2010-02-15
Java has one that seems free and open but for C/C++ it's harder, found [http://www.lumenvox.com/company/edu/](http://www.lumenvox.com/company/edu/) might be worth a look at least if not fully helpful so at least some more information on S2T :)

---

### Post by shababhsiddique on 2010-02-15
> **Ferrat said:**
> Java has one that seems free and open but for C/C++ it's harder, found [http://www.lumenvox.com/company/edu/](http://www.lumenvox.com/company/edu/) might be worth a look at least if not fully helpful so at least some more information on S2T :)

can you tell me the guide on java? can not understand the link u gave

---

### Post by Ferrat on 2010-02-15
[http://java.sun.com/products/java-media/speech/forDevelopers/jsapi-guide/Recognition.html](http://java.sun.com/products/java-media/speech/forDevelopers/jsapi-guide/Recognition.html)

Just look around the site I linked to, has tips, information and so on about speech recognition

---

### Post by shababhsiddique on 2010-02-26
bump

---

### Post by shababhsiddique on 2010-02-27
bump

---

### Post by Tony Flury on 2010-02-28
I don't understand why you are bumping - Ferrat gave you a link to investigate - if you have a specific question about the details on that site, then ask them. Just bumping is not helping.

---

### Post by shababhsiddique on 2010-03-04
> **Ferrat said:**
> Speech2text is a hard nut to crack and totally different from text2speech. 

What you need is first a input, that means a codec and a sampler that can put what is said in to a temporary file and that's the "easy" part, now for the hard one, you now need to build a workable pattern recognition software that can find and isolate different parts of the sample in the temp file and this is probably one of the hardest things you can do, if it's just for you then it's easier but not easy, then you can use predetermined samples and maybe work from that but if you want wide usage for multiple users you need to have a very good understanding of patter recognition, sound handling as well as some AI since the program often will have to venture a guess based on the pattern.

can some one help me out with this-  "julius-3.5.2"

i think this is what I need... but cant seem to get it work... does not understand any of my words.

---

### Post by WitchCraft on 2010-03-05
> **shababhsiddique said:**
> Can anyone tell me how to recognize voice/speech and convert to string?

I need a program to get a string as input through microphone. Using ubuntu and C++. used espeak to speek out at text. need the reverse.

If you can seriously get it to work, let me know. I'll congratulate you on becoming a millionaire/billionaire. ;-))

But for the time being: You have to use the amplitude to detect the word ending, then you decompose the voice into several spectrums, checksum all of the spectrum's patterns, then compare  the patterns with a propability functions over all its patterns versus all the patterns saved in the voice recognition database.

Then you'll have a list of words that might correspond to the spoken word, together with the propability of this being so.
You of course choose the word with the highest propability (unless you find a statistical way to build a second propability, based on the context)
The problem with the context function is of course, that since all the sentence is spoken, you don't have it to begin with.

Of course, you'll also have to adjust for lower/higher voices, faster/slower speech, background noise, and dialects, and speaking and intonation errors.

Then you have to build a HUGHE database first, then you can sell your product, for < 150$ per CD (because else IBM is cheaper), and I would encrypt the database, if you want to stay in business (but basically it doesn't matter, you'll have to include the decryption key somewhere, because else you can't read the data out yourself)...

In other words: Forget it for the next 10 years to come. 
It doesn't work anyway, and that includes the 150$ IBM version.
You have to realize that just because there's a 'simple' way to 'get' from B to A, that doesn't necessarely mean the way from A to B is just that simple, too.
It's mathematics, not every function is uniquely invertible, that's a fact of nature.

---

### Post by shababhsiddique on 2010-03-05
> **WitchCraft said:**
> If you can seriously get it to work, let me know. I'll congratulate you on becoming a millionaire/billionaire. ;-))

But for the time being: You have to use the amplitude to detect the word ending, then you decompose the voice into several spectrums, checksum all of the spectrum's patterns, then compare  the patterns with a propability functions over all its patterns versus all the patterns saved in the voice recognition database.

Then you'll have a list of words that might correspond to the spoken word, together with the propability of this being so.
You of course choose the word with the highest propability (unless you find a statistical way to build a second propability, based on the context)
The problem with the context function is of course, that since all the sentence is spoken, you don't have it to begin with.

Of course, you'll also have to adjust for lower/higher voices, faster/slower speech, background noise, and dialects, and speaking and intonation errors.

Then you have to build a HUGHE database first, then you can sell your product, for < 150$ per CD (because else IBM is cheaper), and I would encrypt the database, if you want to stay in business (but basically it doesn't matter, you'll have to include the decryption key somewhere, because else you can't read the data out yourself)...

In other words: Forget it for the next 10 years to come. 
It doesn't work anyway, and that includes the 150$ IBM version.
You have to realize that just because there's a 'simple' way to 'get' from B to A, that doesn't necessarely mean the way from A to B is just that simple, too.
It's mathematics, not every function is uniquely invertible, that's a fact of nature.


you have really frightened me...! come on,,, dont make me cry.. I know that speech to text is not that simple(10000000xtimes harder),,, but nothing is impossible with a crowd of developers! 

I have used win vista speech recognition it is really good.. .. ..  so i cant agree that it would take 10 years more for us to develop one . . . there are some already,,, 

looks like you have a great idea of spectrums  . . . you can help me out with julian...
it would be very nice,,,,

julian is almost done with the technique.... plz download and tell me if you understad anything..

---

### Post by shababhsiddique on 2010-03-05
> **Tony Flury said:**
> I don't understand why you are bumping - Ferrat gave you a link to investigate - if you have a specific question about the details on that site, then ask them. Just bumping is not helping.

if you read throughout the link and my post you would realize... my question was on C++


the link was for java . . .i told him to give it just in  case anyone is helped by it

---

