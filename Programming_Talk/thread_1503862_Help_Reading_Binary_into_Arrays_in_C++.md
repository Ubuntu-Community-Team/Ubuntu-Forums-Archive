---
title: "Help Reading Binary into Arrays in C++"
date: 2010-06-07
forum: Programming Talk
---

### Post by smdawson on 2010-06-07
My goal is to read 8, 16, and 32 bit binary numbers into an array. How can I have the user enter the binary number (i.e. 10010110) and have each digit placed into 8 seperate spaces of an array?
 
Also, I would like to know if I could do the same thing with a vector, if that is easier/more possible.

---

### Post by dwhitney67 on 2010-06-07
Read one character of input from the user at a time.  A character '0' is equivalent to the ASCII value of 48; a '1' is 49.  Thus if you require an integer representation of each inputted character, merely subtract 48 from the char value.  If you need to convert the final inputted binary value to decimal, then use the shift operator << to compute the appropriate value for each bit based on it's position in the array.

Using a vector may make things easier for you.  You can (re)size it to the desired size, and then use the [] operator just like you would with a regular array.

---

### Post by smdawson on 2010-06-07
Ok. I was thinking I could just use a vector and use vector.push_back() to make it the appropriate size. (i.e. 8 bit, 16 bit, or 32 bit). 
 
I am actually trying to make a program that will convert two's complement to decimal. My logic is that inside my struct I can use vector.back() to test if the last digit is a 1 or 0 (after the appropriate 1 and 0 flipping and adding of 1). Then if it is a 0 I can just use my regular binary conversion, and if it is a 1 then I can use the two's complement conversion. 
 
It seems to me like seperating the two process will make it easier, or at least more attainable for my skill level. Does this approach sound stable?

---

### Post by dwhitney67 on 2010-06-07
> **smdawson said:**
> Ok. I was thinking I could just use a vector and use vector.push_back() to make it the appropriate size. (i.e. 8 bit, 16 bit, or 32 bit). 

Yep; sounds good.

> **smdawson said:**
> 
I am actually trying to make a program that will convert two's complement to decimal. My logic is that inside my struct I can use vector.back() to test if the last digit is a 1 or 0 (after the appropriate 1 and 0 flipping and adding of 1). Then if it is a 0 I can just use my regular binary conversion, and if it is a 1 then I can use the two's complement conversion. 

I'm not sure what you mean by this.  In the old days, and probably still true today, a two's complement is equivalent to a one's complement + one.  Thus the 2's complement of 0110 would be represented as 1001 + 1, or 1010.

> **smdawson said:**
>  
It seems to me like seperating the two process will make it easier, or at least more attainable for my skill level. Does this approach sound stable?
Always strive to develop modular s/w, thus making the s/w more manageable and easier to change (should it be needed).

It seems that what you are working on is related to school work; if not, you may want to consider the STL [bitset]("http://www.cplusplus.com/reference/stl/bitset/") in lieu of the vector.


P.S.  This is how I would convert a vector of 0's and 1's to decimal:
```

int decimal = 0;

for (size_t i = 0; i < bits.size(); ++i)
{
   decimal += (bits[i] << i);
}

```

---

### Post by smdawson on 2010-06-07
What I mean about the seperate parts is that if an 8 bit two's complement binary number begins with a '0' then you can just use a normal binary to decimal conversion, because the number will be positive and less than 127, which is still in the two's complement 8 bit range (-128 to 127). 
 
01010101 = 85
 
Then if an 8 bit two's complement number begins with a '1' you can swap '0's and '1's, add +1 in binary, convert to decimal and add (-) to the number. 
 
10101010 (invert) 01010101 (add +1) 01010110 = 86 (multiply by -1) = -86
 
 
By modular do you mean OOP with different structs for the different tasks? That way everything isn't interlaced and is easier to edit or debug...right?
 
Although I am in college, this is for my summer internship. So I will look up the STL bitset you mentioned.

---

### Post by MadCow108 on 2010-06-07
note that there is the bitset container which can do exactly what you want (including reading in a string of 1 and 0):
[http://www.cplusplus.com/reference/stl/bitset/](http://www.cplusplus.com/reference/stl/bitset/)

edit: ops, missed that dwhitney already mentioned it ._.

---

### Post by smdawson on 2010-06-07
Nice. The bitset even has a flip() function for the conversion of a two's complement binary string to decimal. This is excatly what I was looking for, thank you.

---

