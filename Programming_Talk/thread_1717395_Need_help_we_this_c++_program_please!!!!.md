---
title: "Need help we this c++ program please!!!!"
date: 2011-03-29
forum: Programming Talk
---

### Post by julian colonia on 2011-03-29
loljkk

---

### Post by Dark_Stang on 2011-03-29
This sounds like homework.

---

### Post by julian colonia on 2011-03-29
it is but i did it i just need someone to tell me what im doing wrong

---

### Post by nice_like_rice on 2011-03-29
Should be in programming. I'm bored I'll help.

First off use cin instead of scanf, this is c++ and not c, cin is safer.

Secondly string.h offers a function append, which is much better than the method you used. Just do word.append("ay");

Have you written this yourself? Or have you been given this and asked to complete the functions yourself. What exactly do you want help with :) ?

---

### Post by julian colonia on 2011-03-29
i did it myself but i think im missing something because i need to input this house is his the output should be ousehay siay ishay

---

### Post by julian colonia on 2011-03-29
this program is switching the ends of the word i just need to move the first character to the end and add ay

---

### Post by nice_like_rice on 2011-03-29
Okay well firstly that bit of code you posted there switches the first and last letters of the word, it doesn't move the first letter to the end.

Also your code at the top doesn't solve the problem at all! If you were to put a sentence in, it treats the whole thing as one word!

Your program must:
1. Get the sentence from input
2. Split the sentence into the individual words
3. Perform the letter switching and "ay"-adding to each word
4. print out the finished sentence

If you break it down into steps it will be much easier.

---

### Post by nice_like_rice on 2011-03-29
int length = strlen(word);
char chr = word[0];
word[0] = word[length-1];
word[length-1] = chr;

Change that to

int length = strlen(word);
char chr = word[0];
for(int i=0;i<length;i++)
{
   word[i]=word[i+1];
}

word[length-1]=chr;

---

### Post by nice_like_rice on 2011-03-29
Can I just point out the line:

//Move the first letter to the end. (Look at the array shift example)

Why don't you look at the example? They are obviously giving you the answers..

---

### Post by julian colonia on 2011-03-29
I did in the part that says void Appendletters(char str[]).

I'm just having trouble placing the first letter of each word at the end of the sentence and adding. I also don't know where to put the code i have so the script could run.

---

### Post by nice_like_rice on 2011-03-29
> **nice_like_rice said:**
> int length = strlen(word);
char chr = word[0];
word[0] = word[length-1];
word[length-1] = chr;

Change that to

int length = strlen(word);
char chr = word[0];
for(int i=0;i<length;i++)
{
   word[i]=word[i+1];
}

word[length-1]=chr;

That will do it. You program also treats the whole sentence as one word.

So "this is a test" will go to "his is a testtay" which is not what you want. I suggest you follow the instructions you were given they seem to have given you quite a clear layout for your program.

---

### Post by julian colonia on 2011-03-29
thank you 
the one you gave me you were missing and int i; 
but i figured out thanks again for your help

---

