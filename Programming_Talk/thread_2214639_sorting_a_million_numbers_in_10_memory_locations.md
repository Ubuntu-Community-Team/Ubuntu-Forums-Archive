---
title: "sorting a million numbers in 10 memory locations"
date: 2014-04-02
forum: Programming Talk
---

### Post by IAMTubby on 2014-04-02
Hello,
 Recently someone asked me if I could sort 1 million random numbers using only 10 memory locations(I think he meant like 10 * sizeof(int)).
 Is it actually possible or is he just playing around with me ?

Some of the questions I have automatically are:
1. Where are you going to save these 1 million numbers, let alone sorting them.
2. Even an in-place algorithm would require 1 million places.

I was reading some post titled, "1mb-sorting" where he talks about the staging area and the circular buffer. Although, I have been able to make very little sense of it, and am just getting back to it, but this is again 1MB.

Thanks.

Edit : Re-collecting the conversation I had with him multiple times, I feel what he meant was only 10 locations should be used for the logic. As in you can assume like 10 locations which would server as the staging area - which would mean a total of **1 million + 10 locations**. I'm just trying to make sense of the question. :)

---

### Post by Nytram on 2014-04-02
Hi

Could your friend mean a simple sort algorithm that only uses 10 bytes of code, such as with machine code/assembler language instructions. A simple 'bubble sort' routine for example, wouldn't require many assembler language commands. The code would only take a relatively small number of bytes, but the actual storage of the 1 million numbers would need its own memory, like you say.

---

### Post by IAMTubby on 2014-04-02
> **Nytram said:**
> Hi

Could your friend mean a simple sort algorithm that only uses 10 bytes of code, such as with machine code/assembler language instructions. A simple 'bubble sort' routine for example, wouldn't require many assembler language commands. The code would only take a relatively small number of bytes, but the actual storage of the 1 million numbers would need its own memory, like you say.
Hey Nytram, 
 No, these numbers have to be saved as well in those 10 memory locations.

Edit : Nytram, I'm sorry. Re-collecting the conversation I had with him multiple times, I feel what he meant was only 10 locations should be used for the logic. As in you can assume like 10 locations which would server as the staging area - which would mean a total of **1 million + 10 locations**. I'm just trying to make sense of the question. :)

---

### Post by trent.josephsen on 2014-04-02
> **IAMTubby said:**
> Hello,
 Recently someone asked me if I could sort 1 million random numbers using only 10 memory locations(I think he meant like 10 * sizeof(int)).
 Is it actually possible or is he just playing around with me ?

Some of the questions I have automatically are:
1. Where are you going to save these 1 million numbers, let alone sorting them.
2. Even an in-place algorithm would require 1 million places.

I was reading some post titled, "1mb-sorting" where he talks about the staging area and the circular buffer. Although, I have been able to make very little sense of it, and am just getting back to it, but this is again 1MB.

No, that post won't extend to sorting one million numbers with less than a hundred bytes (skip to bolded text for caveats) but forgive me if I talk about it anyway, because I think it's a very neat trick and it took me quite a long time to figure out what made it possible when I first saw it.

For reference, [here's](http://preshing.com/20121026/1mb-sorting-explained/) the blog post you're almost certainly talking about, and the [Stack Overflow question](https://stackoverflow.com/questions/12748246/sorting-1-million-8-digit-numbers-in-1mb-of-ram) that prompted it.

The key insight is that your point 2 quoted above is not actually true. In the 1MB problem, you don't start out with a million numbers already in storage and do an in-place sort -- the values are sent to you over the network and you store each one as you collect it. This observation lets you compress the data, because you don't care about what order the numbers came in -- all you care about is how many of each you have.

So you don't have to store every permutation of the input; you just need to represent every possible output. Any possible output is a list of numbers sorted in ascending order. How many possible **unique sorted lists** are there? This is the question that the [multichoose operator](http://mathworld.wolfram.com/Multichoose.html) answers, and the number we're looking for is 10^8 multichoose 10^6 (i.e., given the set of 8 digit numbers, sample it a million times with replacement). Wolfram|Alpha tells us [the result](http://www.wolframalpha.com/input/?i=10^8%20multichoose%2010^6) is on the order of 10^2,436,455 or about 2^8,093,730. That means that in order to represent all the possible outputs, you need around 8.1 million bits -- which, as Nick Cleaton observed in the Stack Overflow link I posted earlier, is less than 1MB when "MB" is defined as 1024*1024 bytes. The 1MB computer therefore has (only) just enough storage to pull this off. The other stuff, including the staging area and the circular buffer, is implementation detail -- how to actually encode all those 2^8093730 states into the available memory, now that you know it can be done.

**Ok, so what?**

Can this principle be applied to sorting a million (large) numbers in only a handful of bytes? No. Assuming we're dealing with the same size integers (i.e. 8 decimal digits), 8093730 bits is minimal for sorting random input -- any solution that uses fewer bits will lose data.

However, I can think of a few semantic loopholes that might allow it:
1_ Define "one memory location" to be a million bits wide. This is obviously cheating, along with similar techniques like defining your processor to have millions of registers or input pins. (I ought to note that a C implementation may be perfectly conforming with a 1 million bit int.)
2_ Severely restrict your input range and do a bucket sort. If you let all your inputs be in the range 0-15, you can simply add 1 to a counter each time you read an input.
3_ Exploit some non-randomness in the input to compress the data beyond what would be possible with purely random input.
4_ Use some form of storage that doesn't qualify as a "memory location", like a hard drive or the network itself.
5_ Let the input be in some form of read-only storage that can be read multiple times, like in ROM. Perhaps it doesn't count as "using a memory location" if the stored numbers aren't modifiable.
6_ Use a Pentium III under the light of the full moon on the first of April.

Let me know if I missed any.

---

### Post by IAMTubby on 2014-04-06
> **trent.josephsen said:**
> So you don't have to store every permutation of the input; you just need to represent every possible output. Any possible output is a list of numbers sorted in ascending order. How many possible **unique sorted lists** are there? This is the question that the [multichoose operator]("http://mathworld.wolfram.com/Multichoose.html") answers, and the number we're looking for is 10^8 multichoose 10^6 (i.e., given the set of 8 digit numbers, sample it a million times with replacement). Wolfram|Alpha tells us [the result]("http://www.wolframalpha.com/input/?i=10^8%20multichoose%2010^6") is on the order of 10^2,436,455 or about 2^8,093,730. That means that in order to represent all the possible outputs, you need around 8.1 million bits -- which, as Nick Cleaton observed in the Stack Overflow link I posted earlier, is less than 1MB when "MB" is defined as 1024*1024 bytes. The 1MB computer therefore has (only) just enough storage to pull this off. The other stuff, including the staging area and the circular buffer, is implementation detail -- how to actually encode all those 2^8093730 states into the available memory, now that you know it can be done.

Thanks trent.josephsen, your explanation regarding the minimum number of bits to pull this off was clear.

[B]I just have one question though, would it be possible to explain to me how the number 2^8,093,730 comes up. 
[/B] I understand it's got to do with the empty boxes and dotted boxes, but I do not understand how we get the number 99999999 which is 9.9 billion, something that's not discussed anywhere in the post, and so I'm not able to understand the multichoose below.
[B][COLOR=#ff8c00]99999999 + 1000000    [/COLOR][COLOR=#0000cd]==[/COLOR][COLOR=#ff8c00]  [/COLOR][COLOR=#008000]2^8,093,730[/COLOR][COLOR=#ff8c00]
       1000000[/COLOR][/B]


[FONT=PT Serif]

[/FONT]Thank you so much.

---

### Post by trent.josephsen on 2014-04-07
100 billion (10^8) is the number of unique 8 digit numbers, starting with 0 and ending with 99999999. That's because the original Stack Overflow post specified "8-digit decimal numbers". That's the number of items in the set you're allowed to pick from; 1 million (10^6) is the number of times you will pick an item from it.

That's why I said that you can make it possible by restricting the input range -- if you have to sort 1 million numbers between 0 and 18, all you need is log2(19 multichoose 10^6) = [307](http://www.wolframalpha.com/input/?i=log2%2819+multichoose+10^6%29) bits, which fits nicely inside the memory needed for 10 32-bit ints.

I have to rush now, but let me know if this isn't clear and I'll revisit it later.

---

### Post by IAMTubby on 2014-04-08
> **trent.josephsen said:**
> That's because the original Stack Overflow post specified "8-digit decimal numbers".
I have to rush now, but let me know if this isn't clear and I'll revisit it later.
Thanks trent.josephsen, I didn't know that.

But I have some more problems understanding this in full. What I'll do is spend some more time on it and try and clear these by myself. If I'm still not able to, I'll come back to you in a couple of days' time. Bye !

---

