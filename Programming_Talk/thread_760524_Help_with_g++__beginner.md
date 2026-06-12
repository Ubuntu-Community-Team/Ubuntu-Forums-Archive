---
title: "Help with g++ : beginner"
date: 2008-04-20
forum: Programming Talk
---

### Post by -RooneY- on 2008-04-20
Hi guys

I am a C++ intermediate and have been doing C++ programming on TC and Visual C++. Recently I switched to Ubuntu and am thus using g++ compiler. But I am facing really lot of problems on account of the different standards and syntax g++ uses. 

For example, I used gets(); in TC for inputting a string which couldnt contain a space. But in g++, gets is not allowed as its depracated. So, I had to use cin but the string gets ended when it encounters a tab or space. Then someone told me a 2 line complex code to do input a string containing spaces. I am sure it cant be that hard to accomplish the most basic of functions. The documentation on GCC website is not all sufficient or understandable keeping in mind the problems. I am also unable to find any guide which moulds me keeping in mind g++. So in 3 basic words -"I am lost".

I know these arent too complex probs but getting stuck at the most basic of levels is really frustating.

Kindly suggest some source or help me out with the prob I have.

Thanks in advance,
Rohil

---

### Post by mike_g on 2008-04-20
gets is depricated because its dangerous, as it allows for buffer overflows. You should be using fgets instead, which restricts the maximum string size that it will accept. Calling fgets is fairly straightforward:
```
fgets(mystring, MAXIMUM_STRING_SIZE, stdin);
```
One thing to note is that it takes the newline(return) character so you might want to chop that off.

Then again, gets and fgets are C style functions. If you are coding C++ you might want to learn about the standard string class.

---

### Post by Martin Witte on 2008-04-20
> **mike_g said:**
> 
Then again, gets and fgets are C style functions. If you are coding C++ you might want to learn about the standard string class.

Fully agree with this, see e.g. [http://www.mindview.net/Books/TICPP/ThinkingInCPP2e.html](http://www.mindview.net/Books/TICPP/ThinkingInCPP2e.html) for a good book on C++, it covers iostream - for input/output of data

---

### Post by Lux Perpetua on 2008-04-20
> **-RooneY- said:**
> For example, I used gets(); in TC for inputting a string which couldnt contain a space. But in g++, gets is not allowed as its depracated. So, I had to use cin but the string gets ended when it encounters a tab or space. Then someone told me a 2 line complex code to do input a string containing spaces. I am sure it cant be that hard to accomplish the most basic of functions. The documentation on GCC website is not all sufficient or understandable keeping in mind the problems. I am also unable to find any guide which moulds me keeping in mind g++. So in 3 basic words -"I am lost"..```
string s;
getline(cin, s);
```and
 ```
char buffer[N];
cin.getline(buffer, N);

```are both functionally equivalent to the code mike_g posted (however, getline does not store the newline character in the buffer, unlike fgets). The first inputs a line of arbitrary length into a C++ string (which I prefer), and the second inputs a line or part of a line (if the line is too long) into an ordinary char array.

This site is a good online reference when you're starting out: [http://www.cppreference.com/](http://www.cppreference.com/)

---

