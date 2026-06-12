---
title: "Compile any file to &lt; 1KB"
date: 2007-10-16
forum: Programming Talk
---

### Post by dismal_denizen on 2007-10-16
I have come up with a way to compress any file to less than 1KB. I was wondering (before I start coding) if this has already been acheived or if anyone is interested.

By the way, the title of this thread should be "Compress any file to < 1KB".

---

### Post by CptPicard on 2007-10-16
Pray tell, do you have a decompressor too? :)

... bribaetz? cubytes? Is this one of you guys?

---

### Post by dismal_denizen on 2007-10-16
Yes, I believe that decompression should work perfectly.

---

### Post by CptPicard on 2007-10-16
Oh. Care to share this entropy-defying über-compressor with us? :)

---

### Post by mjwood0 on 2007-10-16
Hmm...  Any file?  Glad you've figured out how to remove bits....

:popcorn:

---

### Post by CptPicard on 2007-10-16
*Ssshhh*... :popcorn:

---

### Post by Mathiasdm on 2007-10-16
You might want to read up a bit on [Entropy](http://en.wikipedia.org/wiki/Information_entropy#Data_compression), and related articles on compression.

It's not possible to (losslessly) compress any file to < 1 KB.

---

### Post by CptPicard on 2007-10-16
Come on, don't spoil it. I really wanted to hear the solution ;)

---

### Post by bvanaerde on 2007-10-16
This should be interesting... I'm subscribing to this thread!

---

### Post by pmasiar on 2007-10-16
I read recently some email exchange about "genius" like this one. He compressed files on his disk, and during the exchange he revealed that left decompression program for later (because he compressed only files he did not used daily - and he did not had "motivation" to write decompressing code). Hillarious, but I seems to lost the link, sadly. Anyone recalls it?

---

### Post by CptPicard on 2007-10-16
[IMG]http://www.hackles.org/strips/cartoon310.png[/IMG]

---

### Post by slavik on 2007-10-16
I had a similar idea. My idea revolved around modifying a hashing algorithm to make it easier to reverse and given original file length, it should work.

---

### Post by Wybiral on 2007-10-16
> **CptPicard said:**
> Pray tell, do you have a decompressor too? :)

... bribaetz? cubytes? Is this one of you guys?

lol. I'm with you, I want to hear some more. I'm sure someone will gladly help code this with you if you give us some more details.

> **slavik said:**
> I had a similar idea. My idea revolved around modifying a hashing algorithm to make it easier to reverse and given original file length, it should work.

If the hash is easy enough to reverse, the chances of collision are probably going to be pretty high. How would you plan on preventing that?

---

### Post by slavik on 2007-10-16
> **Wybiral said:**
> lol. I'm with you, I want to hear some more. I'm sure someone will gladly help code this with you if you give us some more details.



If the hash is easy enough to reverse, the chances of collision are probably going to be pretty high. How would you plan on preventing that?
that's the point of also providing the message length, the idea is that there are no collisions for input of same length. it is also possible to include some kind of a "identity" too (a piece of the original file?) so that if the reverse ahsh comes up with collisions to be able to weed out the one you need.

edit, simple hashing (additive)

I give you 13 to compress, you compress it and return 4, you also return 2 (message length), and ^1 (message begins with 1)

undoing 4 will result in 13, 31, 22 but since we know that the message begins with 1, we pick 13. for arbitrary binary files, you would have to include more information.

---

### Post by Wybiral on 2007-10-16
> **slavik said:**
> that's the point of also providing the message length, the idea is that there are no collisions for input of same length. it is also possible to include some kind of a "identity" too (a piece of the original file?) so that if the reverse ahsh comes up with collisions to be able to weed out the one you need.

edit, simple hashing (additive)

I give you 13 to compress, you compress it and return 4, you also return 2 (message length), and ^1 (message begins with 1)

undoing 4 will result in 13, 31, 22 but since we know that the message begins with 1, we pick 13. for arbitrary binary files, you would have to include more information.

I think I see what you're saying, it's just that with larger files the chance of collision would exist even with the same file length. And the number of potential collisions may not reduce enough for a byte or two of the original file accurately determine which was the correct input.

I'm not trying to rain on your parade, I'm just a bit skeptical. But under limited, favorable conditions I can see how this would work if you had the right hashing algorithm. But I'm afraid It would still be pretty unreliable due to the potential of collision (even if it is minimal). You don't want to decompress your file and get a bunch of gibberish because the unlikely collision finally occurred.

---

### Post by CptPicard on 2007-10-16
Hey OP! You can't just leave us hanging like this. We demand to know!!

The possibilities are endless...

---

### Post by slavik on 2007-10-16
> **Wybiral said:**
> I think I see what you're saying, it's just that with larger files the chance of collision would exist even with the same file length. And the number of potential collisions may not reduce enough for a byte or two of the original file accurately determine which was the correct input.

I'm not trying to rain on your parade, I'm just a bit skeptical. But under limited, favorable conditions I can see how this would work if you had the right hashing algorithm. But I'm afraid It would still be pretty unreliable due to the potential of collision (even if it is minimal). You don't want to decompress your file and get a bunch of gibberish because the unlikely collision finally occurred.
right, but if you have a 100MB file, you can include the first megabyte of it, plus the megabyte long hash.

result = 2MB, or compression ration of 2%. Huffman coding is only 12.5% at most optimal situation (same repeating character/byte)

---

### Post by ryno519 on 2007-10-16
I suggest we sticky this post. Clearly this is an important discovery from one of the greatest minds of our time.

---

### Post by CptPicard on 2007-10-16
Seconded. I really, really want to know. Honest.

And I'm not even being nasty, I'm just curious. And it's always learning experience both ways.

---

### Post by aks44 on 2007-10-16
Don't be so impatient people, I'm sure the OP is out to patent it and add it to the [Open Invention Network]("http://www.openinventionnetwork.com/")'s portfolio, before any greedy closed-source corporation steals the invention for its own profit.

Let's wait peacefully... :)

---

### Post by ryanVickers on 2007-10-16
I'd be interested to know how!  Really! ;)

Get my 4GB .dv files into 1KB and I'll, do something... :p

---

### Post by Carl Hamlin on 2007-10-16
I thought at one point that I'd come up with an amazing compression algorithm, and I couldn't figure out for the world why nobody else had thought of it because it was so deceptively simple.

So I wrote it out and put it to the test.

Turned out I had made a bonehead logic error, and I was accounting for a specific factor twice.

For a while I kept at it - the feeling that I'd had a brush with something truly spectacular didn't fade very quickly. I *did* end up writing a compression algorithm, but it was *miles* behind any of the freeware packages available at the time.

Ah, well.

Here's hoping you're really on to something, dismal_denizen; If you're still listening, then know that I know how you feel and I'm rooting for you.

---

### Post by Vox754 on 2007-10-16
> **pmasiar said:**
> I read recently some email exchange about "genius" like this one. He compressed files on his disk, and during the exchange he revealed that left decompression program for later (because he compressed only files he did not used daily - and he did not had "motivation" to write decompressing code). Hillarious, but I seems to lost the link, sadly. Anyone recalls it?

[Better file compressor.](http://ubuntuforums.org/showpost.php?p=3362033&postcount=30)


As always, beware of trolls and trolling.

---

### Post by dismal_denizen on 2007-10-17
OK, a few things:
1. This is still a (good) theory
2. I'm currently working on the code (wish me luck!)
3. Decompression should work
4. I'll post a link to the program once I've finished
5. I'm unsure of whether I should put the program up as open source, freeware or commercial sale if it works. I know that open source is great, but I don't want to miss my chance to make money!

As they say, watch this space (for success or failure).

---

### Post by AZzKikR on 2007-10-17
Good luck, I am very interested in any theory documentation and the implementation.

---

### Post by pmasiar on 2007-10-17
> **Vox754 said:**
> [Better file compressor.](http://ubuntuforums.org/showpost.php?p=3362033&postcount=30)

Thanks, Vox, that was it. Bookmarked now.

---

### Post by jr.gotti on 2007-10-17
They have this already! Its called the delete button.

---

### Post by ilautar on 2007-10-17
> **slavik said:**
> right, but if you have a 100MB file, you can include the first megabyte of it, plus the megabyte long hash.

result = 2MB, or compression ration of 2%. Huffman coding is only 12.5% at most optimal situation (same repeating character/byte)

Well, hash algorithms are irreversible. How will you calculate actual data from that 1 MB hash? Calculate hahs of all possible permutations with given length and see if it is the same?

---

### Post by slavik on 2007-10-17
right, but my thought was to have a reversible hash (if it's possible), note it is only a thought.

I do have semi-working code (compressor/decompressor) that uses huffman coding :P

---

### Post by CptPicard on 2007-10-17
> **slavik said:**
> right, but my thought was to have a reversible hash (if it's possible), note it is only a thought.


Well, perfect hashes are reversible, but the fundamental idea is after all that you're using lesser bits than your universe of data has, so in theory there are just not enough holes for all the pigeons... of course your hash tries to make collisions unlikely. Anyway, you will have hash some pieces of data into the same hash, and then you won't know which one it was.

Denizen, I'm not really all that sure I bother reading through some actual code to figure out what it is doing... if you started this thread in the first place, why not share the general idea with us? :)

---

### Post by olejorgen on 2007-10-17
> **Vox754 said:**
> [Better file compressor.](http://ubuntuforums.org/showpost.php?p=3362033&postcount=30)


As always, beware of trolls and trolling.
lol. Almost too stupid to be true though. But then.. humanity never stops suprising:shock:

---

### Post by dismal_denizen on 2007-10-17
I can tell you that my idea does not contain fractal hocus pocus.

The reason that I haven't posted my theory yet is that I don't want a Bill Gates clone to steal my idea. If you know a wayof protecting my theory, please tell.

---

### Post by Steveway on 2007-10-17
Let me guess.
Your program is several gygabites big and includes a heck of 1 and 0 combinations that are assigned to a number.
Your compressor looks for any of these in the to be compressed file/files and whoop, your compressed file only contains some numbers.
Yes you can compress it to less than 1kb with this method but it is not usable, tell me if I got your idea.

---

### Post by CptPicard on 2007-10-17
To be completely frank, your idea violates so much basic theory that it's 100% certain it's bunk -- as you may have gathered from responses. So, no, you don't need to worry about anyone running with it.

I'm just curious how you approached this. Would love to tell you where you got it wrong.

---

### Post by slavik on 2007-10-17
write the code then publish it and file for a patent.

---

### Post by pmasiar on 2007-10-18
in USA you have one year from publishing your idea to patenting it. So go ahaead and tell us.There is still 0.000001% (of course less that that, but you got the idea) chance you are genius and we (and related scientists) all are wrong, but I am not holding my breath.

---

### Post by Fbot1 on 2007-10-18
Already been done: [http://www.cs.fit.edu/~mmahoney/compression/barf.html](http://www.cs.fit.edu/~mmahoney/compression/barf.html)

What? You say that's cheating? Lies, all lies! YOU DON'T KNOW WHAT YOU'RE TALKING ABOUT! YOU'RE A FOOL, A FOOL I SAY!

---

### Post by Zugzwang on 2007-10-18
Gee, my calendar states that it is'nt April yet, so I wonder...

If you can really compress **any** file to < 1 KB, you would be violating the [_Pigeonhole Principle_]("http://en.wikipedia.org/wiki/Pigeonhole_principle"), which is a mathematical fact (provided that there's a decompression method). :)

---

### Post by Lster on 2007-10-18
Good luck; but I doubt it is practically possible.

---

### Post by jespdj on 2007-10-18
> **dismal_denizen said:**
> I can tell you that my idea does not contain fractal hocus pocus.

The reason that I haven't posted my theory yet is that I don't want a Bill Gates clone to steal my idea. If you know a wayof protecting my theory, please tell.
You're starting to sound a lot like [Jan Sloot](http://www.cs.unimaas.nl/p.spronck/Sloot.htm).

Good luck with breaking the laws of nature... =D>

> **Lster said:**
> Good luck; but I doubt it is practically possible.

I can tell you one thing: You can stop doubting now.

---

### Post by Lster on 2007-10-18
> I can tell you one thing: You can stop doubting now. 

I can.

---

### Post by hod139 on 2007-10-18
> **jespdj said:**
> You're starting to sound a lot like [Jan Sloot]("http://www.cs.unimaas.nl/p.spronck/Sloot.htm").

That was an excellent read!  I only hope the OP reads it.

---

### Post by Steveway on 2007-10-18
> **hod139 said:**
> That was an excellent read!  I only hope the OP reads it.

Yes, I liked it, too.
I bookmarked it.

---

### Post by Fbot1 on 2007-10-18
> **jespdj said:**
> Good luck with breaking the laws of nature... =D>

I'm telling you it's been done before, just look at that link I gave (WHICH IS DEFINITELY IN NO WAY A STUPID CHEAT THAT DOESN'T ACTUALLY COMPRESS THE FILE TO 0 BYTES BUT STORES INFORMATION IN THE FILENAME (LEAVING THE SPACE ON THE FILE SYSTEM NOT AT 0 BYTES). NOPE, NOT THIS COMPRESSOR. IT DEFYS MATH LIKE THAT).

---

### Post by ssam on 2007-10-18
it is impossible to make an algorythm that will compress **any** file to 1KB.

there are 2^1024 possible 1KB files.

there are twice as many 1025 byte files. i could make these 2^1025 files and put them all through your compression program. i would then have 2^1025 1KB files, there for i must have duplicates.

how can 2 identical 1KB files expand to different files?

---

### Post by Fbot1 on 2007-10-18
> **ssam said:**
> 
there are 2^1024 possible 1KB files.

256^1024 actually (similar things apply to the rest of your example), but your point is that it's finite.

> **ssam said:**
> how can 2 identical 1KB files expand to different files?

> **Fbot1 said:**
> Already been done: [http://www.cs.fit.edu/~mmahoney/compression/barf.html](http://www.cs.fit.edu/~mmahoney/compression/barf.html)

What? You say that's cheating? Lies, all lies! YOU DON'T KNOW WHAT YOU'RE TALKING ABOUT! YOU'RE A FOOL, A FOOL I SAY!

---

### Post by aks44 on 2007-10-18
> **Fbot1 said:**
> 8^1024 actually

256^1024 actually... :-\"

---

### Post by Fbot1 on 2007-10-18
> **aks44 said:**
> 256^1024 actually... :-\"

Oh ya, I thought "byte=3 bits" then "byte=4 bits". :oops:

---

### Post by Wybiral on 2007-10-18
> **Fbot1 said:**
> Oh ya, I thought "byte=3 bits" then "byte=4 bits". :oops:

1 byte = 8 bits

---

### Post by ryanVickers on 2007-10-18
doesn't anyone use nibbles any more!?! ;)

---

### Post by aks44 on 2007-10-18
> **ryanVickers said:**
> doesn't anyone use nibbles any more!?! ;)

Oh well, I recently had to use 5-bits (base-32) "digits" so, hell, everything is possible... :p

---

### Post by wolfbone on 2007-10-18
Heh! This reminds me of the New Scientist / Shawyer EMDrive farce I got involved with a while back. What is extraordinary about nonsense like this is the regularity with which it occurs and the number of people who are taken in by it *even after they are shown simple to understand proofs of its absurdity*. And as for the Patent Offices...

 [http://gailly.net/05533051.html](http://gailly.net/05533051.html)

---

### Post by dismal_denizen on 2007-10-18
You guys win. My idea doesn't work. I have concluded that this kind of compression is not possible. Binary is already a very efficient way of storing data.

PS At least I didn't compress all of my files and delete the originals! :)

---

### Post by Wybiral on 2007-10-18
> **dismal_denizen said:**
> You guys win. My idea doesn't work. I have concluded that this kind of compression is not possible. Binary is already a very efficient way of storing data.

PS At least I didn't compress all of my files and delete the originals! :)

Out of curiosity, what was your theory?

---

### Post by CptPicard on 2007-10-18
It sounds like he was trying to make a binary string shorther by moving to... *drum roll* base-3 or something :)

---

### Post by dismal_denizen on 2007-10-18
I accidently double posted!

---

### Post by dismal_denizen on 2007-10-18
1. Read two bytes.
2. Convert to integer by using byte1 * 128 + byte2
3. This integer takes up 15 bits.
4. To reverse: byte1 = integer % 128
if integer < 0
   byte2 = Math.ceil(integer / 128 )
else
   byte1 = Math.floor(integer / 128 )

The problem is that unless you know whether the bytes will have the same sign, you are stuffed. This formula could still be good for encryption with slight modification.

Please don't laugh at me. :)

---

### Post by CptPicard on 2007-10-18
Not laughing at you, but just wondering where you get the idea that as an "integer" two bytes of 16 bits together would be any less than 16 bits, and if they were 15 bits, how it follows that any file can be compressed to less than a KB...

---

### Post by daniel of sarnia on 2007-10-19
> **dismal_denizen said:**
> You guys win. My idea doesn't work. I have concluded that this kind of compression is not possible. Binary is already a very efficient way of storing data.


Wow, really...

---

### Post by mozetti on 2007-10-19
> **dismal_denizen said:**
> 1. Read two bytes.
2. Convert to integer by using byte1 * 128 + byte2
3. This integer takes up 15 bits.
4. To reverse: byte1 = integer % 128
if integer < 0
   byte2 = Math.ceil(integer / 128 )
else
   byte1 = Math.floor(integer / 128 )

The problem is that unless you know whether the bytes will have the same sign, you are stuffed. This formula could still be good for encryption with slight modification.

Please don't laugh at me. :)

You don't have to worry about laughing from me, and probably most others on the forums. So you didn't create an earth-shattering new compression scheme -- who cares? You probably learned a thing or two, and at least you're actually exercising that mass of gray matter sloshing around in your noggin.

---

### Post by CptPicard on 2007-10-19
... and also, props to you for actually admitting you're wrong and not getting all arrogant, as a lot of "geniuses" around here tend to do. You didn't make too much of an idiot of yourself, which is good. Still can't figure out how you came up with that idea though ;)

---

### Post by pmasiar on 2007-10-19
... and you had the integrity to admit mistake and learn from it. Many other "visionaries" cannot do that. Probably too ashamed of themselves... :-)

Anyway, you learned something. Only person who does not try never fails. 

Now, back to regular programming. Nothing more to see here.

---

### Post by sacherjj on 2007-10-19
> **aks44 said:**
> Oh well, I recently had to use 5-bits (base-32) "digits" so, hell, everything is possible... :p

Those are baker's nibbles. :)

---

### Post by kentl on 2007-10-22
This made me remember a quote I liked:
> Good judgement comes with experience. Unfortunately, the experience usually comes from bad judgement.
The point is that you learned something. Trial and error is much better than never trying to think "outside the box" at all.

Also to the guy above in the thread. Who said that it would probably be possible to create a program which has "all" permutations of the most common lengths of bits, and enumerate those and just reference the permutation by its enumeration. It doesn't work in the average case. A friend of mine had that exact idea and made a proof in a discrete mathematics course that it's not possible. Of course. If you say that 1 means "the open office binary", you'll have compressed the OO-binary into 1 byte. ;-)

---

