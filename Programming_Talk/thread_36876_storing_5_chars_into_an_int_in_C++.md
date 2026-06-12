---
title: "storing 5 chars into an int in C++?"
date: 2005-05-25
forum: Programming Talk
---

### Post by jerome bettis on 2005-05-25
i'm helping someone with a program here.  it's a pretty simple spellcheck program that just uses a hash table for the dictionary and checks a document.  we got all that stuff working already.  but the point of the program is to use as little ram as possible.  the dictionary is huge at over 500 000 words.  currently we're just hashing the strings and it works great but it uses a lot of space.  **a lot** more than the profs demo used.  he gave a little hint here:

"There is no way you will get close to my ram usage unless you do not use chars or strings.  You must combine chars into integral types.  For instance, a 32 bit integer will hold 6 lowercase letters with two bits left over. Sean."

right... then someone replied:

"Just out of curiousity, how come you can only fit 6 characters in a 32 bit integer?  You only need 4 bits to represent 26 characters.  Couldn't you fit 8 characters in an integer?"

no chars are 8 bits ...

"No, you cannot represent 26 characters in 4 bits. Four bits can only hold 16 states (2^4 = 16), which is not even enough enough for one letter. Storing A thru Z in lowercase needs 26 states and the closest thing is 5 bits (2^5 = 32). A char is 1 byte or 8 bits. Thus that leaves 3 bits which are basically unused. Sean's hint refers to getting rid of those 3 wasted bits and compacting them. By using only 5 bits per character, you are able to store 6 characters in a 32 bit integer, wasting only 2 bits per 6 characters instead of wasting 3 bits per each character."

so that all makes sense right?

i understand the concept, but i don't know how to actually do that in c++.  i need to take a character, drop the three unused bits, put the 5 into an integer, do this four more times and ignore the lower (or upper?) two bits.  then hash this integer into the table.  a problem i can see coming up later is words that are not 5 characters long and manging the hashing / looking up.  but we'll worry about that after we figure out how to squish them together.

thanks!

---

### Post by vague- on 2005-05-25
You need to use bitwise operations.  Note that the dictionary will be fairly limited if you do not allow for characters other than A to Z.  You can use a mask to specify which character in the integer you are referring to.

For example, the following are the ranges:

```
first  character -> ((integer & (0x1f <<  0)) >>  0) + 'A'
second character -> ((integer & (0x1f <<  5)) >>  5) + 'A'
third  character -> ((integer & (0x1f << 10)) >> 10) + 'A'
fourth character -> ((integer & (0x1f << 15)) >> 15) + 'A'
fifth  character -> ((integer & (0x1f << 20)) >> 20) + 'A' 
sixth  character -> ((integer & (0x1f << 25)) >> 25) + 'A'
```

I am sure you can notice the relation between the decimal constant and the character offset (think exclusively).  Basically, we are just masking out the rest of the integer, moving it down to the 5 least significant bits - then scaling it back into the character range.  Please note that you may wish to use some of your 6 spare encoding results to represent other things (such as the end of the string, so stop parsing after this character - for example).  I'll leave that as an exercise to you.  It may not make much sense if you do not perform checks on the string to be sure it does not contain characters outside of [A-Z].  Having words longer than longer than six characters is trivial - you can implement multiple layers so that you test 6 characters at a time.  You could even use the two most significant bits to help with indications like this.  For example, setting 0x8000000 could be used to signify whether the string is complete or partial.  The constraint is that you have to use length managed buffers instead of null-terminated strings, but that is not difficult - especially if you use those 2 remaining bytes well.

Anyway, I think that works.  I'd check it on paper or something, first.  Have fun.

---

### Post by jerome bettis on 2005-05-28
thanks for your help.  i finally figured it out and it works pretty well.

```
int compress(char *word)  {
    int x = 0;
    for (int i = 0; i < 5; i++)
        x |= ((int) shorten(word[i])) << (i * 6);
    return x;
}

unsigned char shorten(char c)  {
    return (c >= 'A' && c <= 'Z') 
        ? c - 'A' 
        : (c >= 'a' && c <= 'z') 
            ? c - 'a' + 26 
            : 0;
}
```

so that works.  but i've got another problem with this and i can't figure out a quick way to do it.  what i'm doing is splitting the words up into chunks of five, and compressing those five characters into one integer using the functions i posted above.  

so for each word i have an arbitrary number of integers representing it.  originally i was adding these integers together to yield one larger integer that represents the word.  but this didn't work because addition is commutitive.  so a word like abcdefghij in the document would not be marked as misspelled if fghijabcde is in the dictionary.  (abcde = 3, fghij = 7, 3+ 7 = 10 ; 7 + 3 = 10) make sense?

so then i tried subtraction which is not commutitive (3 - 7 != 7 - 3) and this worked much better but a few completely different words coincidentally subtract to the same number (12 - 2 = 10, 15 - 5 = 10).  so that doesn't work.

i need either a) a way to take an arbitrary number of integers and get one unique number from them or b) to store the integers in some sort of collection.  arrays would be good but i need to know how many elements they have.  i could store the size of the arrray in a[0] but the whole point of this is to save space.  having one integer hang around just for that reason is kinda self defeating here.  and i can't for the life of me get vectors or a class i made to cooperate with this hash table (won't compile).  maybe i'm doing something wrong? ...

any ideas?

---

### Post by mendicant on 2005-05-28
If this is for a university level course, you should really be able to figure out how to hash these things yourself and how to resolve hash collisions.   You should even be able to figure out how to use the STL in this situation (if it is allowed).

I don't want to be too preachy, but if it is a university level course, and assuming you (or whoever this is for) were allowed to collaborate (particularly with people outside your course), then you should give credit to vague-, above, and anybody else that helps you.  Anything else could be construed as plagiarism, which is usually a nasty offense in unversity.

Not to leave you high and dry, here are a couple of hints:
- use the STL if you are allowed to do so
- a hash function may also go under other names, with varying speed/space characteristics:
  - checksum, signature
  - there are whole sections of books that look at hash functions; Knuth's searching and sorting book comes to mind
  - googling for a hash function will give you many results (assuming you're allowed to use them); googling for a string hash function will also give you many results, and aren't hard to adapt to your use

---

### Post by DanN on 2005-05-28
Why not Huffman code the characters, you could fit more than 6 Huffman coded 'e's into an int  ;-) .

---

### Post by jerome bettis on 2005-05-28
[QUOTE=DanN]Why not Huffman code the characters, you could fit more than 6 Huffman coded 'e's into an int  ;-) .[/QUOTE]
 funny you mention that as it's just what i'm thinking about right now.  i did huffman coding several years ago, but i don't remember exactly how you build the tree.  i might still have the code i wrote around here somewhere.  i'm definately gonna look into it because it probably is exactly what i want here.  is it cpu intensive at all?

i'm not sure if what i want to do with these N integers is possible to do efficiently.  i'd like to avoid using some sort of cryptography here (md5 etc) but the more i think about it, this seems like the only way to actually do it.  i've tried doing all kinds of different operations at different times but conincidences still occur.  no matter what i do to get one number there could always be another set of numbers that will result in the same one under the same set of operations.  any math people know for sure?

---

### Post by DanN on 2005-05-28
Binary huffman codes are fairly easy to construct:
1 order your symbols by probability
2 lowest two probabilities are leaves of a new node
3 calculate new probability as sum of two leaf probabilities
4 if the sum of those probabilities is not 1, go back to step one
5 label your branches with 1s and 0s and read back along them to determine the code for each symbol

Sorry if thats a poor explanation, I suspect google or wikipedia would be more helpful.

The other thing I wondered, if space is an issue, is why you wouldn't just use an array to store the words, is it a requirement that a hash table be used?  Unless the Hash Table is populated perfectly a normal array will use up less space.

---

### Post by mendicant on 2005-05-28
[QUOTE=jerome bettis]i've tried doing all kinds of different operations at different times but conincidences still occur[/QUOTE]

You can definitely generate a perfect hash for your key set.  Your dictionary has 500K items and 32 bit integers can represent 4294967296 items.  Look at gperf.

---

