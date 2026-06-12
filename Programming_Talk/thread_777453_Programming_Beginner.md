---
title: "Programming Beginner"
date: 2008-05-01
forum: Programming Talk
---

### Post by Vicfred on 2008-05-01
I'm starting to program but I'm confused I've read some programming tutorials but they just explain some basic syntax and I dont have idea how a complex program should be done so what should i learn next... and next? I don't have idea can you provide me with some links of communities/forums/tutorials? Thanks in advance  ):P

---

### Post by hessiess on 2008-05-01
download some source code and reed through it.

---

### Post by LaRoza on 2008-05-01
> **Vicfred said:**
> I'm starting to program but I'm confused I've read some programming tutorials but they just explain some basic syntax and I dont have idea how a complex program should be done so what should i learn next... and next? I don't have idea can you provide me with some links of communities/forums/tutorials? Thanks in advance  ):P

Link to communities: [http://sillyquestion.php]("http://ubuntuforums.org/forumdisplay.php?f=39")

Link to communities: [http://sillyquestion.php]("http://ubuntuforums.org/forumdisplay.php?f=39")

Link to tutorials: [http://laroza.freehostia.com/home](http://laroza.freehostia.com/home)

---

### Post by howlingmadhowie on 2008-05-01
probably best to decide on a language and then learn to program in that really well. 

i know what you mean however. you start to program by learning syntax for a language (how do i write a loop? how do i write function calls?...) and once you've done that, there's a moment when you just say "now what?". 

here certain basic considerations can help, for example "how can i divide my program up into little bits to make the structure of the program more clear?" and "how can i reuse code?". on ubuntuforums there is a simple coding competition. the current competition is here: [http://ubuntuforums.org/showthread.php?t=772016](http://ubuntuforums.org/showthread.php?t=772016)

read through the wikipedia entry and make sure you understand it, then have a go at implementing it yourself :)

---

### Post by nvteighen on 2008-05-01
Let's see:

What languages have you been looking at? There are some languages that use very few elements but extensible by libraries, so those tutorials may be teaching everything there actually is. It is the case of C: you can learn its syntax and built-in features in just less than an hour, but then you'll have to learn the Standard Library... and then, other libraries if you plan to do some GUI or more complex maths... (and then probably write your own library?)

The best way is to code, so you learn things associated to some need. You take yourself a challenge and search for resources on that specific problem; so "what next?" will mean "what next on **this program**?". (And don't be afraid to fail; you always learn something).

But don't learn <any programming language> just because people tell you, learn it because you have interesting on it... People will recommend you Python, but if you like Assembly (an extreme example), why don't go for it?

---

### Post by JupiterV2 on 2008-05-01
I've come to learn that programming is as much about knowing a language, or many languages, as it is about learning to solve problems creatively. Don't just try and learn a language; try and solve problems, continually write code and find creative solutions to the bugs and issues you encounter. Sometimes the most seemingly mundane tasks can become an incredible learning experience.

Reading other people's code, like hessiess suggested is a good idea too. Pick a language you want to learn based on what type of tasks you want to complete and browse their source. See what kind of solutions people came up with for the problems they were trying to solve.

---

### Post by Tomosaur on 2008-05-02
"Learn by doing" is the only way to learn programming succesfully. You can read and read all you want, but for 99.999999999% of people, actually programming using whatever language is a far faster and more interesting way to do it.

There are no rules, just think of something you'd like to create, then get on with it :P Obviously some things will be way over your head, so start small and build on your skills. Most people tend to start with little 'toys' - say a simple text game, or a maths game, or something like that. In fact, little games like this are probably one of the best ways to learn a new language, because it introduces a fair amount of usefull skills (input, output, converting data types etc etc) in a very short amount of time.

---

### Post by Kadrus on 2008-05-02
> I'm starting to program but I'm confused I've read some programming tutorials but they just explain some basic syntax
What programming language are you learning...or trying to learn?

---

### Post by Vicfred on 2008-05-02
I'm learing C

---

### Post by nvteighen on 2008-05-02
> **Vicfred said:**
> I'm learing C

Well, I'm also in it, but I've some (bad) previous programming experience... including several BASIC dialects, JavaScript, Visual Basic, some SVG and a failed C++ attempt.

C is actually simple, the problem is to learn how to combine those simple elements into a program ;) (remember, I'm also a C-beginner, not an expert). Also, in C you have to spend some good coding time on making your code secure, specially when initializing variables or double-checking what the user's input is like before storing it or writing three functions only to parse data before it is used in a single line... Many don't like that and prefer Python, where things are developed faster... but I really think that in C you invest time learning some good practices, as boring and repetitive they can seem.

---

### Post by pmasiar on 2008-05-02
> **nvteighen said:**
> ....as boring and repetitive they can seem.

You have interesting definition of "fun". :-)

---

### Post by nvteighen on 2008-05-03
> **pmasiar said:**
> You have interesting definition of "fun". :-)
I was referring to tasks like explicitly freeing memory or parsing command line arguments or having to #include <stdio.h> only to have printf() available... Don't forget to check user's input: if not, you'll get a segfault or worse glibc may scream!

The fun comes after having to do all that boring but necessary stuff, when actually implementing your algorithm and making it work (well, in my case, making my code even compile...).

---

### Post by LaRoza on 2008-05-03
> **nvteighen said:**
> I was referring to tasks like explicitly freeing memory or parsing command line arguments or having to #include <stdio.h> only to have printf() available... Don't forget to check user's input: if not, you'll get a segfault or worse glibc may scream!


User input is one of the worst parts of programming. See my wiki under the Python section, there is an article named "Saving Users from themselves" which deals with user input in Python. User input is the curse of all programmers. Elevators have it lucky, they know what they are going to get, imagine if it were open ended and the users had to enter the floor number using a keyboard.

---

### Post by s_raghu20 on 2008-05-03
ignore post.

---

### Post by nvteighen on 2008-05-03
> **LaRoza said:**
> User input is one of the worst parts of programming. See my wiki under the Python section, there is an article named "Saving Users from themselves" which deals with user input in Python. User input is the curse of all programmers. Elevators have it lucky, they know what they are going to get, imagine if it were open ended and the users had to enter the floor number using a keyboard.

Great article!

(We're going offtopic, I fear)

---

### Post by LaRoza on 2008-05-03
> **nvteighen said:**
> Great article!

(We're going offtopic, I fear)

[img]http://www.mysmiley.net/imgs/smile/sign/sign0006.gif[/img]

Off topic? In the PT? How unusual.

However, I do think the OP's question was answered.

---

### Post by Mr.Macdonald on 2008-05-03
I suggest learning python till you have the programming concept down and then move to Java.

Many people will tell you that java is slow but i have't seen it.

Limewire runs off java and thats not slow??


Java also has a lot of guides about it

[javaboutique]("javaboutique.com") has a great games building guide that basically taught me everything i needed to start programming.

Javadocs are basically ammazing and if well written then they will save you.

---

