---
title: "[Python] Creating new character list."
date: 2011-04-10
forum: Programming Talk
---

### Post by ki4jgt on 2011-04-10
I was wondering if it was possible to impliment a character system of your own in Python. Besides the normal 255 character set. Can someone define a 444 character set, or a 20454 character set?

Read this: [http://regebro.wordpress.com/2011/03/23/unconfusing-unicode-what-is-unicode/](http://regebro.wordpress.com/2011/03/23/unconfusing-unicode-what-is-unicode/)

Is there a way to create more, to handle more contextual data? I would like to be able to set a character to have two other characters. I want the program to be able to convert that text back to two characters instead of one.

---

### Post by Tony Flury on 2011-04-10
What do you mean - contextual data ?

Explain what you mean - there might be a better way of doing what you need.

---

### Post by simeon87 on 2011-04-10
Why do you need a character set? You could define a dictionary such as:

```
{"a": ("b", c")
,"d": ("e", f")}
```

to convert a character ("a") to two characters ("b" and "c").

---

### Post by Arndt on 2011-04-10
> **ki4jgt said:**
> I was wondering if it was possible to impliment a character system of your own in Python. Besides the normal 255 character set. Can someone define a 444 character set, or a 20454 character set?

Read this: [http://regebro.wordpress.com/2011/03/23/unconfusing-unicode-what-is-unicode/](http://regebro.wordpress.com/2011/03/23/unconfusing-unicode-what-is-unicode/)

Is there a way to create more, to handle more contextual data? I would like to be able to set a character to have two other characters. I want the program to be able to convert that text back to two characters instead of one.

Python knows how to handle Unicode, which is much more than 255 characters.

There are glyphs in various languages, which can be said to be a combination of one base character and several secondary ones. Is that what you mean?

---

### Post by ki4jgt on 2011-04-10
OK, in the view of compression. I know that's not how compression works, but still it's an idea. 255 X 255 = 65025 So defining 65025 characters to cover all possible two character combinations would mean that what ever file was compressed using this algorithm, would instantly be half it's original size. Furthermore if it could be shrunk down even further by making 65025 X 65025 = then all files compress would instantly become 1/4 their original size. Again, I know this is not how file compression works, but in the real world, we are not limited by the characters we can make, why are we in the computer world?

---

### Post by simeon87 on 2011-04-10
> **ki4jgt said:**
> OK, in the view of compression. I know that's not how compression works, but still it's an idea. 255 X 255 = 65025 So defining 65025 characters to cover all possible two character combinations would mean that what ever file was compressed using this algorithm, would instantly be half it's original size. Furthermore if it could be shrunk down even further by making 65025 X 65025 = then all files compress would instantly become 1/4 their original size. Again, I know this is not how file compression works, but in the real world, we are not limited by the characters we can make, why are we in the computer world?

Because your approach doesn't work. With one byte you can store one of 256 possible characters. So for a file with two characters you'd need two bytes. To store one of 65025 characters you'd need, for convenience of calculation, 16 bytes (2^16 = 65536). For many two-character combinations that means the file would actually become larger rather than smaller if we'd follow your approach.

---

### Post by ki4jgt on 2011-04-11
> **simeon87 said:**
> Because your approach doesn't work. With one byte you can store one of 256 possible characters. So for a file with two characters you'd need two bytes. To store one of 65025 characters you'd need, for convenience of calculation, 16 bytes (2^16 = 65536). For many two-character combinations that means the file would actually become larger rather than smaller if we'd follow your approach.

I know this. That's why I asked if the character set could be changed or added to. Can we not make another set of characters? Can we not make a virtual set which is then rendered to bianary? Meaning you have 65536 characters each with two binary characters associated with them? Like in real life if I made up a symbol for example if I made up the following symbols (I know I didn't) and gave the the equivilent characters.

! = "wr"
@ = "it"
# = "e "
$ = "a "
& = "bo"
? = "ok"

In this line of thought, !@#$&? = write a book (Which is smaller than the original) I know it is not possible, but my question was can we not create our own character set? So if I created 65536 characters, each having it's own two character combination, not forgetting the 256 already possible characters (For files which have an uneven amount of characters) this would provide a compression which was infact smaller. Just as if I were to interpret 65536 symbols on paper to be a combination of two characters, I would have letter which is half the size of the original letter.

But back to the original question, is it possible?

Is it possible to redefine a unicode type system and then have the program convert it over to binary?

---

### Post by Tony Flury on 2011-04-12
the point that simeon87 is making is if you take your scheme to it's extreme it is not smaller.

Think about this : you want a character set that can represent every possible pair of printable characters as a single "item". We have 26 uppercase and 26 lower case characters, 10 number and say around 33 other punctuation marks - so that is 94 characters.

To represent any possible pair of printable characters it means you need 94*94 glyphs in your new character set.

Your printable only character set would need only 7 bits, your new pairs character set needs 14 bits - i.e. it is same size. 

Yes - for some very limited inputs (such as your example) you can generate an encoding which allows you to "compress" your input - but as I have shown, as you try to extend the scheme you run into problems.

There are some ways to compress data (for instance spotting repeated characters and doing something called run length encoding), or identifying commonly repeated characters sequences - and assigning them a special code.

---

### Post by ki4jgt on 2011-04-12
I get what you're saying. Which is why I asked if new ones could be created so that it would only be 8 bits for 1 character.

So I guess the new question is, could we in programming virtually create a 4 based system, instead of a 2? So 4**8 characters to do this so instead of a 01100101 (Just made that up) system we could have a 13321012 system. This would create 65536 available character instead of 256.

Thus making this very possible. Notice: I did say virtually

---

### Post by Vaphell on 2011-04-13
every encoding under the sun is mapping a range of integers to a range of glyphs. If you want to have 65536 chars, use 16bit integers. But 16bit integer can be constructed with 2 8bit ones ( i[16]=256*i1[8]+i0[8]) - this is the same thing.

besides i hope you realize that 4**8 is 2**16 and you don't need to come up with revolutionary base4 system? :)

---

### Post by Some Penguin on 2011-04-13
File sizes are in bits organized into bytes for the convenience of hardware and software designers, not characters, because characters are merely interpretations of byte sequences.   You're persistently refusing to understand this.  Take your argument to its logical extreme:  could you compactly represent all possible universe with a single tiny bit sequence simply by reinterpreting the bits?

---

### Post by JacksSmith on 2011-04-13
You can use Unicode which universally accepted character set form characters that wont support the other than English language.

---

### Post by Tony Flury on 2011-04-13
> **ki4jgt said:**
> I get what you're saying. Which is why I asked if new ones could be created so that it would only be 8 bits for 1 character.

So I guess the new question is, could we in programming virtually create a 4 based system, instead of a 2? So 4**8 characters to do this so instead of a 01100101 (Just made that up) system we could have a 13321012 system. This would create 65536 available character instead of 256.

Thus making this very possible. Notice: I did say virtually

You do realize that storing something as binary (i.e. 1 & 0s) is not just an arbitary decision made way back when - it is a consquence of the very hardware that we use to do the computations. At it's very basic level that hardware consists of electronic switches which can only ever be on and off (i.e. 1 or zero). On a hard drive your data consists of microscopic magnetic patterns on the surface of the disk which are either on or off.

Even if you wrote code that represnted everything internally as Base 4 (and not base 2) your hardware would still at the most basic level process everything as base 2, and you would save nothing.

To have a device that stored items as Base 4 (for instance) you will have to fundamentally redesign every component in the PC - memory, CPU, Disks, etc etc etc etc.

---

### Post by simeon87 on 2011-04-13
> **Tony Flury said:**
> You do realize that storing something as binary (i.e. 1 & 0s) is not just an arbitary decision made way back when - it is a consquence of the very hardware that we use to do the computations. At it's very basic level that hardware consists of electronic switches which can only ever be on and off (i.e. 1 or zero). On a hard drive your data consists of microscopic magnetic patterns on the surface of the disk which are either on or off.

Even if you wrote code that represnted everything internally as Base 4 (and not base 2) your hardware would still at the most basic level process everything as base 2, and you would save nothing.

To have a device that stored items as Base 4 (for instance) you will have to fundamentally redesign every component in the PC - memory, CPU, Disks, etc etc etc etc.

Even if we'd make base 4 hardware, it would not be more expressive than a binary system. Anything that can be expressed in base 3 or higher can be expressed in base 2 so there's nothing to gain with that approach.

---

### Post by ki4jgt on 2011-04-13
Except for the extra storage space. . . OK, every time I say this, someone else tells me it's impossible b/c we are limited by the 1/0 system. or that I'm trying to put the entire universe in one string of characters. I know you guys are telling me that it's impossible. . . So let's just say, for the sake of theory. . .

A 2**16 bit system wouldn't save any room. there would still need to be 16 1/0 switches. In a 4 based system there would only need to be 8 switches. Thus making the compression 8 bits per character. and give a possibility for each character to represent 2 characters in normal life.

I don't get how "In theory" this system wouldn't work.

Keep in mind: Due to lack of the computer being able to do this, I am using numbers to represent each character I type. This is theory based on a 4 base system and not a two. I will be typing character ascii numbers "4 based system not two" in a 4 based system, you would have 4**8 possible combinations.

character(444) = ae
character(245) = 44

now if you have 4**8 possible switch combinations, you will get characters which can represent, 2 possible input characters.

Theoretically: if each of these 4**8 characters was defined as it's own (One single character as it is with all the 2**8 characters all ready) which the computer interpreted as 2 individual characters, would hard drive space not double? (There is your performance increase) it provides a method of compression, where if you are using a 4 based system, you will instantly get more storage space. It can not take up more room since you are dealing with 8 numbers in the 2 based system and 8 numbers in the 4 based system and since 8 = 8 taking up more space would defy the laws of physics. But providing more options to fill that space would have to provide more space. (Unless I'm missing something)

I was simply asking if it was possible create said extra space with some sort of virtual character set (Via programming). Thanks for your answers on that possibility. For those of you who didn't understand, I can't get much clearer than that.

---

### Post by Simian Man on 2011-04-13
> **ki4jgt said:**
> A 2**16 bit system wouldn't save any room. there would still need to be 16 1/0 switches. In a 4 based system there would only need to be 8 switches. Thus making the compression 8 bits per character. and give a possibility for each character to represent 2 characters in normal life.

I don't get how "In theory" this system wouldn't work.

If you exchange all of the bits in your computer for double-bits that could hold any value 0-3, then yes, obvioulsy you could hold more data.  But doing so would be *much* harder than just doubling your memory.

> **ki4jgt said:**
> I was simply asking if it was possible create said extra space with some sort of virtual character set (Via programming). Thanks for your answers on that possibility. For those of you who didn't understand, I can't get much clearer than that.
If you have 65536 different values, you will need 2 bytes to hold them - there is no getting around that with a different character set.  Look at [Huffman Coding]("http://en.wikipedia.org/wiki/Huffman_coding").  It is similar to what you are talking about, except it actually works :).

---

### Post by Arndt on 2011-04-13
> **Tony Flury said:**
> You do realize that storing something as binary (i.e. 1 & 0s) is not just an arbitary decision made way back when - it is a consquence of the very hardware that we use to do the computations. At it's very basic level that hardware consists of electronic switches which can only ever be on and off (i.e. 1 or zero). On a hard drive your data consists of microscopic magnetic patterns on the surface of the disk which are either on or off.

Even if you wrote code that represnted everything internally as Base 4 (and not base 2) your hardware would still at the most basic level process everything as base 2, and you would save nothing.

To have a device that stored items as Base 4 (for instance) you will have to fundamentally redesign every component in the PC - memory, CPU, Disks, etc etc etc etc.

I think there have been computers built that used ternary logic. Long ago, of course.

---

### Post by Some Penguin on 2011-04-13
> **ki4jgt said:**
> 

I was simply asking if it was possible create said extra space with some sort of virtual character set (Via programming). Thanks for your answers on that possibility. For those of you who didn't understand, I can't get much clearer than that.

We understand; it's you that doesn't.  You've never, ever even heard of Shannon information, have you?  Or studied how compression programs actually work?

---

### Post by Arndt on 2011-04-13
> **ki4jgt said:**
> Except for the extra storage space. . . OK, every time I say this, someone else tells me it's impossible b/c we are limited by the 1/0 system. or that I'm trying to put the entire universe in one string of characters. I know you guys are telling me that it's impossible. . . So let's just say, for the sake of theory. . .


This has lately been about hardware, how information is represented as bits (binary), or something else. But your original question was how to do this in Python. What does that mean? Whatever you do in Python, it's executed by the Python interpreter, which runs on the ordinary hardware. You can simulate all kinds of representations, to be sure, but it will all be done by the usual bits.

---

