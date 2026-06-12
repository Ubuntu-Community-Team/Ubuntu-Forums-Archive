---
title: "Java: What do you think of my program?"
date: 2014-02-11
forum: Programming Talk
---

### Post by raymond10 on 2014-02-11
Hello (world, and) members of the Ubuntu forums! This is my first post, I just joined this forum a few minutes ago. I am in the process of learning Java and came across the [Programming Challenges from LaRozza]("http://ubuntuforums.org/showthread.php?t=884394").
Of course, that initiative is long gone now, but that won't stop me from using those challenges as a way to practice and learn Java! 

I wanted to show you all what I came up with for the third programming challenge, in the hope that you guys would be kind enough to give me feedback. 
The code for this working program I came up with is now on pastebin, [http://pastebin.com/hCK54avZ](http://pastebin.com/hCK54avZ).

I started learning Java a few months ago by reading Herbert Schildt's "Java: The complete reference" (7th edition), which I finished reading. I understand most of the book, but after having finished studying it the codes didn't exactly start flowing out of my fingers when I start a new project in Eclipse. I am still a beginner, so to get the flow of programming in Java I thought these programming challenges would surely help me!

Please feel free to give me tips and feedback on the program I came up with, so that I can further improve my Java programming skills and soon try and find a job with it.

Ray

---

### Post by ofnuts on 2014-02-11
[LIST]
[*]You are hard-coding many values... what if you need to insert a language in the middle of your list? You should have an array of languages ["Assamese/Asomiya","Bengali/Bangla"","Bodo"...] over which you loop to write it to file (and then a format("%d. %s%n",index,languages[index]") looks useful)
[*]No point in building a big string to write it to file. if you have a BufferedWriter or better a PrintWriter you can write your output line by line with no performance penalty.
[*]Give meaningful names to your variables (not f1,f2,f3...) especially when used far from their declaration/initialization (using i,j as index is OK in a short loop)
[*]Using String.format("%n") just to add a system-dependent line end is  complete overkill. Either you use System.getProperty("line.separator")  (directly or through a small variable, for better readability), or you  use format() for the full thing (use of %n is OK as part of a larger  specification)
[*]Despite what the comment says your code isn't really looking for languages that start with H or S but for languages that contain them
[*]Why add a number prefix to languages when the only thing you do with it is to remove it later?
[/LIST]

---

### Post by raymond10 on 2014-02-12
Hi ofnuts, thanks for the reply! The reason why I used String.format("%n") is because the "\n" function didn't work when outputted to the bharaat.txt file. The words would just be on one line. And I couldn't recall how to put all these strings in an array and use that as output so I just did it this way. The f1 f2 f3 and f4 was just because I was too lazy to come up with neat names for them haha, my bad. The goal of the challenge was to make the list of languages be output to the bharaat.txt file, and let the program look in that text file to pick out the languages that start with H or S and output those in the out.txt file. Then for extra points you could try and make the program number the languages in the out.txt file properly, which I did. 

I don't know what you mean when you say "add number prefix and remove it later" because as far as I can see the program does:

 1. Print the string "source" to the bharaat.txt file, and then print it to the console.
 2. The program goes to find languages that start with capital H or S, I know I used contain there because that was the only thing I could come up with to do this part of the challenge, but it does work because it looks for a language on a new line that starts with H or S.
 3. If the program finds some, it puts the match in the out.txt file, via the f3.write method seen in the while section. This part of the program, from the int index = s.indexOf(" ");, if a match with the capital H or S is found, the program finds the index of the whitespace (that comes after the for example 22. ) and uses that to only print out everything after that whitespace. Also the program 
 does f3.write(i + "." + s.substring(index) ......., meaning it numbers the new found lines for in the out.txt file as the extra points for this challenge wanted me to. By incrementing i afterwards the number for the prefix gets incremented each time a new language is found that starts with an H or S. I don't see what you mean with "remove it later".
4. Then it adds the "23. English" to the bharaat.txt, when all else is complete, like the challenge said.

I also just added in the prints to the console for fun, and so I could see at what point in execution the program is. 
It does indeed output the languages to bharaat.txt, look in that txt file, find the languages that start with H or S, outputs those found languages to out.txt, and numbers those languages properly, and puts them each on a seperate line just for tidiness. So I completed the challenge on my own way with my meager programming skills, didn't I? So yes, I do remove the numbering for the languages found that start with H or S before I put it in out.txt, but that is because I have to number the found languages correctly and not have my out.txt file say:

6. Hindi
17. Sanskrit
18. Santhali
19. Sindhi

We want it to be

1. Hindi
2. Sanskrit
3. Santhali
4. Sindhi

So I use the index of the whitespace between the number and dot and the start of the language name to only output the language, so that I can give it a correct number later in the out.txt file. Is this what you meant when you were asking about removing numbers? Please do explain that bit.

 But do keep in mind that I am still a beginner, and we all program differently (especially a noob like me compared to you), and this is what I came up with to complete the challenge. And the program does work like the challenge wants it to ;-)

---

### Post by ofnuts on 2014-02-12
What I mean is that the numbers you have in bharaat.txt are never used, they even get in the way (since you have code to explicitly remove them when you copy the names to output.txt). Maybe it's part of the exercise, but it's rather artificial. And if it's an exercise, writing lines with hardcoded number in them is side-stepping the problem.

Never be too lazy to name things. Good names make up for 70% of the readability of the code.

I still contend that your code really checks for names that contain H or S, not for names that start with it. It works with your limited data(*), but you are fooling yourself with this comment. Don't take this remark lightly. I maintain Java code for a living, and bugs usually show up where the comments are contradicted by the code. Your code works for the wrong reasons, so to speak.

(*) Assume your list extends to languages outside India, and now contains "Finnish/Suomi".

---

### Post by raymond10 on 2014-02-12
Yeah it was part of the challenge to output the complete list, including the numbers. But I will be less lazy naming my things next time!

Yes the program does only look for stuff that contains H or S, but which language has a capital letter other than the first letter? None that I know off and not in this list. So yeah, I know what I said in the console print about it looking for names that start with it is a bit fake, but I just wanted to make it look like it for myself, of course I wouldn't call that out for any program that is not only for me. 

But if the list would contain "24. Finnish/Suomi", it would print out the following to the console:

[SIZE=2]Çreating "source" string containing 22 languages.

Writing source to "bharaat.txt". 

Here are the languages that "source" contains:  

1. Assamese/Asomiya 
2. Bengali/Bangla 
3. Bodo 
4. Dogri 
5. Gujaratti 
6. Hindi 
7. Kannada 
8. Kashmiri 
9. Konkani 
10. Maithili 
11. Malayam 
12. Manipuri 
13. Marathi 
14. Nepali 
15. Oriya 
16. Punjabi 
17. Sanskrit 
18. Santhali
 19. Sindhi 
20. Tamil 
21. Telugu 
22. Urdu 
24. Finnish/Suomi
 
Finding languages that start with "H" or "S". 
Found the following language(s):  

1. Hindi 
2. Sanskrit 
3. Santhali 
4. Sindhi 
5. Finnish/Suomi 

All languages starting with "H" or "S" have been found and written to "out.txt". 
Writing "23. English" to the end of "bharaat.txt" 
Done! Thanks for using this program!

And guess what, the bharaat.txt contains "24. Finnish/Suomi", and out.txt contains "5. Finnish/Suomi". So it works as it should, innit? What is the hassle about the contains method then if it does find what it is supposed to? Forgive me if I may sound rude, I am just a beginner trying to figure out Java programming.

Anyway, the challenge was partially about finding languages with H or S, and most languages only have the first letter in capital.


[/SIZE]

---

### Post by Vaphell on 2014-02-12
> What is the hassle about the contains method then if it does find what it is supposed to? Forgive me if I may sound rude, I am just a beginner trying to figure out Java programming.

Anyway, the challenge was partially about finding languages with H or S, and most languages only have the first letter in capital.

Your algorithm is fragile and that's it. What if you read data from external source you have no control of and someone tasked with providing the data messes up and goes all caps for whatever reason? Suddenly contains() doesn't cut it.
What if there is some obscure language with a name made of 2 or 3 words?

let's see here..
[http://en.wikipedia.org/wiki/List_of_indigenous_language_names](http://en.wikipedia.org/wiki/List_of_indigenous_language_names)

Fiji Hindi, does it start with F or with H?
What about Basa-Gumna if you were tasked with finding G*?
Frisian (North), Frisian (Saterland), Frisian (West) - are these F* or N*, S*, W*?
Judaeo-Spanish
Miami-Illinois
Michoacán Nahuatl
Min Bei
Min Dong
Min Nan
Min Zhong
Muscogee Creek
Old Church Slavonic
...
i hope you catch my drift.

Always aim to make your code bulletproof, never assume that your data is in a tidy, predictable format, unless your code double-checked it and normalized the records. Being defensive will spare you countless hours of debugging pain in the long run. And never ever trust user input.

---

### Post by raymond10 on 2014-02-17
> **Vaphell said:**
> Your algorithm is fragile and that's it. What if you read data from external source you have no control of and someone tasked with providing the data messes up and goes all caps for whatever reason? Suddenly contains() doesn't cut it.
What if there is some obscure language with a name made of 2 or 3 words?

let's see here..
[http://en.wikipedia.org/wiki/List_of_indigenous_language_names](http://en.wikipedia.org/wiki/List_of_indigenous_language_names)

Fiji Hindi, does it start with F or with H?
What about Basa-Gumna if you were tasked with finding G*?
Frisian (North), Frisian (Saterland), Frisian (West) - are these F* or N*, S*, W*?
Judaeo-Spanish
Miami-Illinois
Michoacán Nahuatl
Min Bei
Min Dong
Min Nan
Min Zhong
Muscogee Creek
Old Church Slavonic
...
i hope you catch my drift.

Always aim to make your code bulletproof, never assume that your data is in a tidy, predictable format, unless your code double-checked it and normalized the records. Being defensive will spare you countless hours of debugging pain in the long run. And never ever trust user input.


Your answer would make sense. But the challenge isn't about all those things you guys are mentioning! The challenge says very clear that your program has to make a list of the given languages, put them in a txt file, let the program look in that txt file for languages that start with H or S, and put those in another txt file with the correct numbering. That is all. I followed those "rules of engagement" precisely and my program now does exactly what the challenge wants it to. Sure the contains method wouldn't work in use with variable input from the user BUT that is NOT what the challenge is about! I set out to complete this challenge with this program exactly as the rules of the challenge state and I completed that on my own way. The contains method in this use works perfectly. If the challenge would be different, like with those Min Dong and Min Nan languages you listed I would've found another way to complete the challenge (if the challenge were for looking for languages that start with M and Min would not be the language name or something), for example I would've written something that would look past the Min part for a capital M or something. I appreciate feedback, but not feedback based on what if situations. I did the challenge, and asked for feedback on how I well I completed the challenge with this program.

---

### Post by Vaphell on 2014-02-17
Ok, ok :-)
Let's say it this way: if the challenge was graded, you wouldn't get A, even though your program is technically correct. If i was a teacher in a programming class, there would be points for style, generality, extensibility, etc and your program would lose some.

You will learn programming faster if you try to come up with elegant solutions that don't work only for a particular input. Just give yourself bonus points, a candy and a pat on the back, if you design a nice, flexible, resilient algorithm :-)

---

### Post by ofnuts on 2014-02-17
> **raymond10 said:**
> Your answer would make sense. But the challenge isn't about all those things you guys are mentioning! The challenge says very clear that your program has to make a list of the given languages, put them in a txt file, let the program look in that txt file for languages that start with H or S, and put those in another txt file with the correct numbering. That is all. I followed those "rules of engagement" precisely and my program now does exactly what the challenge wants it to. Sure the contains method wouldn't work in use with variable input from the user BUT that is NOT what the challenge is about! I set out to complete this challenge with this program exactly as the rules of the challenge state and I completed that on my own way. The contains method in this use works perfectly. If the challenge would be different, like with those Min Dong and Min Nan languages you listed I would've found another way to complete the challenge (if the challenge were for looking for languages that start with M and Min would not be the language name or something), for example I would've written something that would look past the Min part for a capital M or something. I appreciate feedback, but not feedback based on what if situations. I did the challenge, and asked for feedback on how I well I completed the challenge with this program.

There are working programs (WP), and good programs (GP)(*). Of course any GP is a WP, but not the other way around. Your program falls squarely in the WP category only. Our comments are about making it a GP. We assume that if you asked for comments, it was because you felt that it was WP only. If you think it's already GP, and therefore that all our comments are pointless, that's your call. This is your code, not ours. But fear the day you'll have to write a real program, for real users.

(*) A GP takes are of non-functional requirements (aka NFR): maintainability, readability, resilience to unforeseen inputs...

---

### Post by raymond10 on 2014-02-18
> **ofnuts said:**
> There are working programs (WP), and good programs (GP)(*). Of course any GP is a WP, but not the other way around. Your program falls squarely in the WP category only. Our comments are about making it a GP. We assume that if you asked for comments, it was because you felt that it was WP only. If you think it's already GP, and therefore that all our comments are pointless, that's your call. This is your code, not ours. But fear the day you'll have to write a real program, for real users.

(*) A GP takes are of non-functional requirements (aka NFR): maintainability, readability, resilience to unforeseen inputs...

I see.. If I would make a program for real world use and not only to complete a challenge I would definitely try my best to make it a GP, ready for all kinds of weird user input! And of course, I would make the program more general and have more parameters that the user could enter, like through a simple txt file or perhaps through a database. 


> **Vaphell said:**
> Ok, ok :-)
 Let's say it this way: if the challenge was graded, you wouldn't get A, even though your program is technically correct. If i was a teacher in a programming class, there would be points for style, generality, extensibility, etc and your program would lose some.

 You will learn programming faster if you try to come up with elegant solutions that don't work only for a particular input. Just give yourself bonus points, a candy and a pat on the back, if you design a nice, flexible, resilient algorithm :-)

Hmm ok. I did the first and second challenges too, and for the second I just tried making it with Swing and adding in a few more functionalities than the challenge wanted me to, just to test myself :P And especially because it was about user input I tried to be a bit more careful about IO errors. I just thought that with this challenge it didn't state anything about user input so I could make it hardcoded to the string source and make it a simple program that does the job. But you're right, some of the methods I used aren't the cleanest and best way to do the job, but I still did it haha.

---

### Post by ofnuts on 2014-02-18
> **raymond10 said:**
> I see.. If I would make a program for real world use and not only to complete a challenge I would definitely try my best to make it a GP, ready for all kinds of weird user input! 

And you would  fail because you aren't in the habit to do it... you can't have double coding standards. The code you write for yourself (and I include this kind of programming challenge) should be as good as you can because you have time and little pressure. Your real-life code will never be as good as your own private code, because you will have less time and more contingencies.

---

