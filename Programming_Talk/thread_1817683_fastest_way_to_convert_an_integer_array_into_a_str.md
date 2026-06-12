---
title: "fastest way to convert an integer array into a string"
date: 2011-08-03
forum: Programming Talk
---

### Post by quickk on 2011-08-03
Does anyone know fast methods of converting an array of integers into a string in c?  

I need this to use a minimum perfect hash library (cmph).  Currently I call the hash function from my main code written in fotran.  I use the fortran write command to write to the string as so:

```
write(string,'formatting')int_array
```.

I then call the cmph functions using this string.   The problem is that I need to do this potentially billions of times, and it turns out that this is one of my biggest bottlenecks!   I was thinking perhaps c is faster at doing this, but perhaps not.

---

### Post by Bachstelze on 2011-08-03
Define "string". ;) In particular, does the "string" have to be null-terminated, and does it have to contain ASCII characters only?

---

### Post by ve4cib on 2011-08-03
Do you need a perfect representation of the array as an ASCII string?  By that I mean does the array have to turn into the string "[1,2,3,4,5]"?

If not, then with C you can simply treat the integer array as an array of chars, and do a straight copy of the bytes:

```

char* intArr2string(int[] arr, int length)
{
    char* str = (char*)malloc(length * sizeof(int) + 1); // +1 for the null terminator

    int tmp;
    int i,j;
    int x=0;
    for(i=0; i<length; i++)
    {
        tmp = arr[i];
        for(j=0; j<sizeof(int); j++)
        {
            str[x] = (char)(tmp & 0xff);  // copy 1 byte from tmp
            tmp = tmp >> 8;               // shift tmp down 8 bits
            x++;
        }
    }
    str[x] = '\0';  // add the null terminator
    return str;
}
```

It could be optimized a little more, but you see the general idea.  Each int is basically just 4 chars, so you can copy those bytes over exactly as they are.  You'd need to do some kind of error-checking to eliminate 0x00 bytes that occur within the chars (so you don't wind up with null "terminators" that aren't at the end of the string).  Mangling them by converting them to 0xff or 0x01 might work, but that could result in some collisions.

You could work around the collisions problem by using a 5th byte as a flag to indicate if any of the other 4 were mangled.  0xF* (where * is 0 if there was no mangling, or 0x1-0xf, corresponding to 1s in the positions of the mangled bytes), but that would add some more overhead.  Not a lot, but a little.

---

### Post by Bachstelze on 2011-08-03
ve4cib, you might want to have a look at memcpy(). ;)

---

### Post by ve4cib on 2011-08-03
> **Bachstelze said:**
> ve4cib, you might want to have a look at memcpy(). ;)

It's example code, meant for demonstration purposes only.

I didn't forget about a standard library function that would do exactly what I wanted.  Really.  *shifty eyes*

The down-side to memcpy is that it wouldn't allow you to mangle the 0x00 bytes, which could result in an excess of collisions.  With my longer version it wouldn't be too hard to add an extra few lines to mangle the bytes and track the changes in the fifth dummy byte.

---

### Post by Bachstelze on 2011-08-03
That is true. But since the requirements are not clearly defined, all we can do is wait for quickk to clarify what is needed. I don't know how this particular library works, but if you want to generate the SHA* hash of a chunk of data with the OpenSSL library, it need not be null-terminated, instead you provide a pointer to the data and an integer giving its size.

---

### Post by quickk on 2011-08-03
Thank you everyone for your input.  I'll see if I can implement your suggestions, Bachstelze and ve4cib.  

To answer your questions, I don't think that the string needs to be null terminated.  The library that I am using is this one: [cmph]("http://cmph.sourceforge.net/").  It takes on input a list of strings like so:

```
const char *vector[] = {"aaaaaaaaaa", "bbbbbbbbbb", "cccccccccc", "dddddddddd", "eeeeeeeeee", 
          "ffffffffff", "gggggggggg", "hhhhhhhhhh", "iiiiiiiiii", "jjjjjjjjjj"};
```

and returns a minimal perfect hash function that can assign a unique integer to each of the strings.  

I don't know c very well at all so I call this from my fortran main program.  The things I want ordered are integer arrays like "0,2,3,32,3" that usually have less than 20 items.  However, there can be something like 50000 different arrays that I want to get a unique id for.  

So to call this cmph library from my fortran code, I have to turn my arrays (actually, all held in a big matrix) into strings.   At the moment I do this like so:
```
write(string,formatting)integer_array,char(0)
```
where "string" is the string made of the integers in "integer_array".
(I think that the null character is needed to pass the string from fortran to c).

Anyway, it turns out that this takes roughly 50% of my calculation time (since the program does this so many times)!   I thought that perhaps I could just pass the whole integer array to c and then convert it into a string inside of the c cmph routine (and that this would be more efficient since c is better with strings, I think).

---

### Post by Bachstelze on 2011-08-03
From the look of it, the strings must be null-terminated, because the compiler has no other way to figure out their length. So since you want the id to be unique to each array, you have to eliminate the null bytes in the binary representations without creating collisions. ve4cib's suggestion would work, but I would suggest adding 4 new bytes instead of just one so as to keep everything word-aligned, which will probably give better performance than adding just one (run some tests to see how much). Since the arrays are small, the memory space penalty would be bearable.

---

### Post by david.medine on 2011-08-03
Just came across this on the internet. Werks for me.
```

[COLOR=#000000][COLOR=#0000BB]char    [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000BB]int_to_str[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000BB]int nbr[/COLOR][COLOR=#007700])
{
  [/COLOR][COLOR=#0000BB]int   div[/COLOR][COLOR=#007700];
  [/COLOR][COLOR=#0000BB]int   len[/COLOR][COLOR=#007700];
  [/COLOR][COLOR=#0000BB]int   i[/COLOR][COLOR=#007700];
  [/COLOR][COLOR=#0000BB]char  [/COLOR][COLOR=#007700]*[/COLOR][COLOR=#0000BB]res[/COLOR][COLOR=#007700];

  [/COLOR][COLOR=#0000BB]res [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000BB]xmalloc[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000BB]4 [/COLOR][COLOR=#007700]* [/COLOR][COLOR=#0000BB]sizeof[/COLOR][COLOR=#007700](*[/COLOR][COLOR=#0000BB]res[/COLOR][COLOR=#007700]));
  [/COLOR][COLOR=#0000BB]i [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000BB]0[/COLOR][COLOR=#007700];
  while ([/COLOR][COLOR=#0000BB]i [/COLOR][COLOR=#007700]< [/COLOR][COLOR=#0000BB]3[/COLOR][COLOR=#007700])
    [/COLOR][COLOR=#0000BB]res[/COLOR][COLOR=#007700][[/COLOR][COLOR=#0000BB]i[/COLOR][COLOR=#007700]++] = [/COLOR][COLOR=#DD0000]'\0'[/COLOR][COLOR=#007700];
  [/COLOR][COLOR=#0000BB]res[/COLOR][COLOR=#007700][[/COLOR][COLOR=#0000BB]3[/COLOR][COLOR=#007700]] = [/COLOR][COLOR=#DD0000]'\0'[/COLOR][COLOR=#007700];
  [/COLOR][COLOR=#0000BB]i [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000BB]0[/COLOR][COLOR=#007700];
  [/COLOR][COLOR=#0000BB]div [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000BB]1[/COLOR][COLOR=#007700];
  [/COLOR][COLOR=#0000BB]len [/COLOR][COLOR=#007700]= [/COLOR][COLOR=#0000BB]1[/COLOR][COLOR=#007700];
  while ([/COLOR][COLOR=#0000BB]nbr [/COLOR][COLOR=#007700]/ [/COLOR][COLOR=#0000BB]div [/COLOR][COLOR=#007700]>= [/COLOR][COLOR=#0000BB]10[/COLOR][COLOR=#007700])
    {
      [/COLOR][COLOR=#0000BB]div [/COLOR][COLOR=#007700]*= [/COLOR][COLOR=#0000BB]10[/COLOR][COLOR=#007700];
      [/COLOR][COLOR=#0000BB]len[/COLOR][COLOR=#007700]++;
    }
  while ([/COLOR][COLOR=#0000BB]len[/COLOR][COLOR=#007700])
    {
      [/COLOR][COLOR=#0000BB]res[/COLOR][COLOR=#007700][[/COLOR][COLOR=#0000BB]i[/COLOR][COLOR=#007700]++] = [/COLOR][COLOR=#DD0000]'0' [/COLOR][COLOR=#007700]+ ([/COLOR][COLOR=#0000BB]nbr [/COLOR][COLOR=#007700]/ [/COLOR][COLOR=#0000BB]div[/COLOR][COLOR=#007700]);
      [/COLOR][COLOR=#0000BB]len[/COLOR][COLOR=#007700]--;
      [/COLOR][COLOR=#0000BB]nbr [/COLOR][COLOR=#007700]%= [/COLOR][COLOR=#0000BB]div[/COLOR][COLOR=#007700];
      [/COLOR][COLOR=#0000BB]div [/COLOR][COLOR=#007700]/= [/COLOR][COLOR=#0000BB]10[/COLOR][COLOR=#007700];
    }
  return ([/COLOR][COLOR=#0000BB]res[/COLOR][COLOR=#007700]);
} [/COLOR][/COLOR]

```

---

### Post by david.medine on 2011-08-03
BTW, I don't know what is up with that xmalloc. I changed it to a normal malloc:
```

res = malloc(sizeof(char)*50);[COLOR=#000000][COLOR=#007700][/COLOR][/COLOR]

```

---

