---
title: "Cannot figure out this bug for the life of me!"
date: 2014-03-12
forum: Programming Talk
---

### Post by bikewrecker on 2014-03-12
Hi guys. I have a question with a program I'm writing for a class. Its supposed to take two words and figure out what the biggest prefix is. Ie if you input "wall" and "wallet" it's supposed to spit out "wall".

It works great for small words but for some reason as soon as i get bigger than 4 letters it gives me some of the right answer but then messes up the last letter and adds on some unique characters to the matching parts.

Should be a straightforward program but I cant find my bug. 

Here's the program :
```

  1 #include <stdio.h>
  2 #include <string.h>

  6 int
  7 main()
  8 {
  9         char w1[256], w2[256], prefix[256];
 10         int i = 0, j = 0;
 11         printf("Enter two words: ");
 12         scanf("%s %s", w1, w2);
 13         if(w1[0] != w2[0])
 14         {
 15                 printf("%s and %s have no common prefix.\n", w1, w2);
 16         return 0;
 17         }
 18         while((w1[i] != '\0')&&(w2[i] != '\0'))
 19         {
 20                 if(w1[i] == w2[i] && !(strlen(prefix) >= strlen(w1)) && !(strlen(prefix) >= strlen(w2)))
 21                 {
 22                         prefix[j] = w1[i];
 23                         j++;
 24                         i++;
 25                 }//If the characters are equal, store the character in prefix.
 26                 else if(w1[i] != w2[i])
 27                 {
 28                         break;
 29                 }//If they are not equal, quit loop.
 30                 else 
 31                 {
 32                         break;
 33                 }//If something else happened, quit loop.
 34         }
 35         printf("The longest common prefix of %s and %s is %s\n", w1, w2, prefix);
 36         return 0;
 37 }       
 
```

Here are some outputs:

```

[drmcb@pc30 ~/Homework7]$ ./prefix.out
Enter two words: aaaa aa
The longest common prefix of aaaa and aa is aa
[drmcb@pc30 ~/Homework7]$ ./prefix.out
Enter two words: aaaaaaaa aaaaa
The longest common prefix of aaaaaaaa and aaaaa is aaaas&#65533;&#65533;F

```

I'm probabaly doing something really dumb but ive been messing with this for like 2 hours now and am tired of looking at it. If its quick to see what i did wrong please let me know. If not, don't worry about it. I'll just work on it again later. 

Thank you!

---

### Post by Vaphell on 2014-03-13
if you see crap after the proper result, that means unterminated string. There is a \0 missing somewhere that should finalize the value of prefix. Just set prefix[j+1] to \0 so you have properly terminated string at all times.

Btw stop using strlen everywhere, just get w1 and w2 length once, pick the lower one and it's your upper bound of i.

---

### Post by Bachstelze on 2014-03-13
In addition to what Vaphell said, two don'ts to keep in mind:

1. [Don't use scanf().]("http://c-faq.com/stdio/scanfprobs.html")
2. Don't write comments which just paraphrase the code. Code should be commented if and only if its meaning is not already obvious.

---

### Post by thisisbasil on 2014-03-13
youre overcomplicating it. 

try doing something like this (pseudocode):

[HTML]
INPUT: str1, str2

if (length(str1) < length(str2)) 
     swap(str1,str2)                 //make str2 the shorter string to save time later

len = length(str2)
while (len > 0)
{
         if (substring(str2,0,len) == substring(str1,0,len))
         {
                  longest_prefix = substring(str1,0,len)
                  break out of loop
         }
         len = len-1
}

if (length(longest_prefix) > 0)
          OUTPUT: longest prefix is longest_prefix
else
          OUTPUT: no common prefix[/HTML]

---

### Post by thisisbasil on 2014-03-13
look into the strstr() function as well

---

### Post by bikewrecker on 2014-03-14
Awesome. Adding the "prefix[j+1] = ' \0';" worked like a charm! Thank you guys so much for helping me out! 

Also thanks for the suggestions on making my coding habits better. 

Thanks again guys. I really appreciate it!

---

