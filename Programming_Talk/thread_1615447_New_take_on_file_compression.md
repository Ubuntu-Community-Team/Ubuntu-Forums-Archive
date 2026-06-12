---
title: "New take on file compression"
date: 2010-11-07
forum: Programming Talk
---

### Post by Ranko Kohime on 2010-11-07
This is merely a theory that I have, and I have no experiments to back it up, or even enough knowledge of programming to attempt an experiment, so feel free to tell me if I'm full of crap.  :)

My theory revolves around blocks of data, in the same way that BitTorrent handles data.  We'll use a 256KiB block for this theory.

While it's uncommon, statistically speaking a 256KiB block of data must share a checksum with some other block of the exact same size.

My theory is this:  2 blocks, while they may share the checksum of one format, say, CRC, they would not share the checksum of another format, say, MD5.  You can substitute any checksum you wish in the place of those two.

The purpose being, that, once both hashes are calculated for that block, the block can be rebuilt through random or sequential generation, and matched to the checksums.  In the event of multiple blocks of data, the generator would attempt to match to all of the sums until it got a hit, thereby filling in all blocks randomly without having to make more than one random generation pass.

Obviously, this is extremely processor intensive, but it would enable quite significant compression on otherwise incompressible files.

I hope I've explained my theory accurately, and even more so, I hope that someone here with programming experience would be kind enough to test my theory.  :mrgreen:

ETA: The entire purpose behind such a method of compression would be for long-term storage of very large, infrequently-accessed files, and the reduction of disk costs associated with such storage.

---

### Post by NovaAesa on 2010-11-07
Finding a block of data that has a certain checksum is intractable (so yes, you are right in that it would be extremely computationally complex). All you are really doing by adding two checksums to a block of data is inventing a new checksum algorithm that has a double sized checksum.

Also, there is another flaw in your theory: yes, a collision is less likely to occur if you have a two checksums, but it can still occur. There will be more than one block of data that has the same amalgamated checksum (unless the size of the amalgamated checksum is larger than the block of data... but then what's the point?). If you don't believe me, look into the "Pigeon Hole Principal".

---

### Post by worksofcraft on 2010-11-07
Checksums can detect errors, but they have also made error correcting codes. I think one is called "hamming code" which effectively tells you which bit is incorrect. I suppose in the extreme you could get a hamming code that would correct **all** the bits even... if you supplied none but I suspect that the "checksums" would be no smaller than the data that you had missed out :shock:

Basically there is concept of "quantity" of information: In any message there is theoretical a limit to how far you can compress data without loosing any.

Like clearly if you have N bits then you can only code 2^N possible messages. Thus if there are more possibilities then you will lose the ability to distinguish between them.

What you **can** do however is to represent the most likely messages with shorter sequences so that statistically, and on average you need less storage. A well known example is morse code where the most common letter E has the shortest code.

Information theory can be a fascinating subject ;)

---

### Post by NovaAesa on 2010-11-07
> **worksofcraft said:**
> What you **can** do however is to represent the most likely messages with shorter sequences so that statistically, and on average you need less storage.
Another example of this (apart from Morse Code) would be Huffman Encoding (a type of entropy encoding). It's pretty interesting as well, and as I understand, heavily used in the last stages of many compression algorithms.

---

### Post by Ranko Kohime on 2010-11-07
The pigeon-hole theory is quite interesting.

I wish I could program, then I could determine the exact point at which collisions occur for any given pair of checksums.

Any recommendations for a language I could pick up easily?  I've recently picked up the basics of shell scripting, but that's the extent of my knowledge.  :)

---

### Post by ssam on 2010-11-07
you proposed block of 512kB is 4194304 bits (512*8*1024). so there are 2^4194304 possible values it could take.

an MD5 check sum is 128 bits, so there are 2^128 (3*10^38) values it can take. 2^128 is a very big number so the chance of a collision between 2 files is very small.

so you can see that it impossible for each 512kB blocks to have a unique md5sum (you already knew this). in fact as 512kB blocks out number 128bit hashes by 2^4194304 / 2^128 = 2^4194176, then each md5sum must have on average 2^4194176 512kB blocks that would give it.

if you used a hash function with a larger output (eg sha512), or used several hash functions then you just increase the space of possible hashes. so until you hash was 512kB long there would be many collisions.

---

### Post by Finalfantasykid on 2010-11-07
> The purpose being, that, once both hashes are calculated for that block,  the block can be rebuilt through random or sequential generation, and  matched to the checksums.  In the event of multiple blocks of data, the  generator would attempt to match to all of the sums until it got a hit,  thereby filling in all blocks randomly without having to make more than  one random generation pass.

I really like your idea with the hashing, but this is the part that concerns me.  Rebuilding by sequentially going through the hash would most likely take forever to compute, assuming I understood this correctly.

---

### Post by Ranko Kohime on 2010-11-08
> **Finalfantasykid said:**
> I really like your idea with the hashing, but this is the part that concerns me.  Rebuilding by sequentially going through the hash would most likely take forever to compute, assuming I understood this correctly.
Yes, it would.  How long is one of those variables I don't know.  I don't know how many milliseconds it takes to increment a 256KiB block bit-by-bit.  I'd love to find out, though.  :)

---

### Post by Ranko Kohime on 2010-11-08
> **ssam said:**
> you proposed block of 512kB is 4194304 bits (512*8*1024). so there are 2^4194304 possible values it could take.
It was actually a 256KiB block in my example.  :)

Though I am thinking now that perhaps 256KiB is perhaps a little optimistic, I still stubbornly cling to my theory.  I'm hard-headed like that.  :P

If I ever learn how to program, I'll see how well 320 bits of checksum reconstructs 640 bits of data.  Just as a test.

*Ranko cracks open a C++ book

---

### Post by Tony Flury on 2010-11-08
Ok - lets use your example :

640 bits "encoded into" 320 bits

what this will mean that each of your 2^320 checksum value will have 2^320 possible blocks, and no matter how clever your checksum is you will be completely unable to work out which one of those 2^320 blocks you should pick, leaving aside the computational complexity of finding all 2^320 blocks which give that checksum as a result.

Checksum do not compress data - they throw data away, keeping just enough information to be able to check that the original is not corrupted - and they do this by making a simple assumption that when the data is transmitted that a certain low level of corruption only will occur and that it is highly unlikely that a corrupted data block will give the same checksum value as the original.

I really would do some research into Information Theory, so that you understand why what you are suggesting wont work.

---

### Post by Some Penguin on 2010-11-08
> **Ranko Kohime said:**
> Yes, it would.  How long is one of those variables I don't know.  I don't know how many milliseconds it takes to increment a 256KiB block bit-by-bit.  I'd love to find out, though.  :)

To put it in perspective, if you could do 1,000,000,000 increment-AND-compute-checksum operations per second (which is patently ridiculous), for 86,400 seconds per day, per 365.25 days per year, you're talking approximately 2^54.8 such operations per year.

So you're looking at 2^(256,000-54.8) ~ 2^255,045 years for a full scan for a single block, and half that on average (2^255,044)... if you have a ridiculously fast computing setup (the aforementioned 1B increment/test per second).

For comparison, the Sun is expected to go red-giant and devour the four inner planets in about 5B years or so.  Let's say we have 6B years left... well, that's roughly 2^32.4 years or so.

---

### Post by trent.josephsen on 2010-11-08
Come now, you're thinking small.  Let's say in 100 years from now, computers that can check 1 billion increment-and-compute-checksum operations per second are commonplace.  So commonplace, in fact, that it's plausible to carpet the planet Jupiter with them, seven quadrillion (7x10^15) times.  We'll assume they are 1cm by 1cm in size and neglect their height, because it makes the math difficult.  So there are 4.35x10^36 computers, that can each check a billion operations per second; that's 4.35x10^45 ops per second in total.  That brings us up to 2^176.5 per year, leaving only 2^255823 years for the entire operation, a mere 11150000000000000000000000000000000000000000 times the current (estimated) age of the Universe.

(I jest, but it's possible that quantum computers will eventually rid us of the need to check each one manually.  Even so, operating on 256000 qubits is well beyond any technology in the foreseeable future.)

All this is rather moot, since as Tony Flury notes, there's no way to reliably encode N bits into less-than-N bits without losing information.  (You can manage it some of the time, but there are always bit sequences that can't be encoded or else require more than N bits to store.  Random bit sequences defeat all attempts at compression.)

---

