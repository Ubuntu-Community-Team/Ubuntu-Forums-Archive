---
title: "[SOLVED] Writing float values into files"
date: 2008-06-08
forum: Programming Talk
---

### Post by Zeotronic on 2008-06-08
C++: Basically I want to write a float value into a file... as binary(?) rather than text. I'm not quite sure how to go about doing this, and I haven't a clue on how to find what I'm looking for... so I've came here. **How do I write a float into a file, without using text.** I've never been good with proper term usage... which is why I'm not quite sure how to explain what I want to do... but surely you get it? Keep in mind that I'd like to know how to read this later on (though I'm sure that reading it would be pretty similar to writing it).

---

### Post by LaRoza on 2008-06-08
I don't understand what you mean. It is printed in binary, usually ascii or unicode encoded.

---

### Post by Compyx on 2008-06-08
> **Zeotronic said:**
> C++: Basically I want to write a float value into a file... as binary(?) rather than text. I'm not quite sure how to go about doing this, and I haven't a clue on how to find what I'm looking for... so I've came here. **How do I write a float into a file, without using text.** I've never been good with proper term usage... which is why I'm not quite sure how to explain what I want to do... but surely you get it? Keep in mind that I'd like to know how to read this later on (though I'm sure that reading it would be pretty similar to writing it).

Why?
What you're asking about is non-portable and basically not the 'proper' way to deal with whatever you're trying to do.
But if you really want to write a float to a file:
```

float f = 3.14;
fwrite(&f, sizeof f, 1, fp);

```
where fp is a FILE* you allocated by calling fopen() and checking its return value.

Whoops: You seem to be asking about C++, but my question remains: why would you creat[sic]/read/write a binary file while you could do with a standard text file (keeping with the Unix philosophy)?

---

### Post by Zeotronic on 2008-06-08
> why would you creat[sic]/read/write a binary file while you could do with a standard text file (keeping with the Unix philosophy)?
I do not like using text streams... however what you have presented me with is making me consider using them in this occasion. Fwrite does not seem to be able to place the value in a specified location in the file (for instance I am using fstream to write all of my other information into files).
> I don't understand what you mean. It is printed in binary, usually ascii or unicode encoded.
Ok... let me try this another way. Lets say I veiw the file in GHex... I want to be able to see the value in hex, and have it properly show me the value as a float in it's float area. Acutally, GHex being mentioned, I think I'll look into it's code, that could probably be useful.

---

### Post by dwhitney67 on 2008-06-09
[PHP]#include <fstream>     // for fstream

int main()
{
  float value = 5.5;
  float read_value = 0.0;

  // open and write data to the file
  std::fstream ofs( "MyFile.bin", std::ios::out | std::ios::binary );
  ofs.write( (const char*) &value, sizeof(value) );
  ofs.close();

  // re-open the file, but this time to read from it
  std::fstream ifs( "MyFile.bin", std::ios::in | std::ios::binary );
  ifs.read( (char*) &read_value, sizeof(read_value) );
  ifs.close();

  return 0;
}[/PHP]


There are other permutations of the solution above, so don't feel that what I presented above is the only way.


P.S.  fopen() and fwrite()  -- Yuck!  Maybe when writing C code, but not for C++!

---

### Post by Zeotronic on 2008-06-09
Ok, that will probably work, thank you.

---

### Post by KingTermite on 2008-06-09
> **dwhitney67 said:**
> [PHP]
  // open and write data to the file
  std::fstream ofs( "MyFile.bin", std::ios::out | std::ios::binary );
  ofs.write( (const char*) &value, sizeof(value) );
  ofs.close();
[/PHP]


There are other permutations of the solution above, so don't feel that what I presented above is the only way.


P.S.  fopen() and fwrite()  -- Yuck!  Maybe when writing C code, but not for C++!

dwhitney67 has the right idea. Left only some code in to point out a few things.

The important parts are to open the file in binary mode. When you learn to program they only teach you to open files in text mode, and you never even realize this is another option (at least when *I* was taught).

Then you read and write normally (not forcing it to strings like you would normally do).

---

