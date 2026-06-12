---
title: "Where to start?"
date: 2009-06-13
forum: Programming Talk
---

### Post by jo$h01 on 2009-06-13
First off i'm sorry for being such a n00b this is my first post here. I've heard everyone here is nice and friendly and can't wait to get too know everyone. Though im not good with navigating forums and if i should of posted this somewhere else i apologise. 

I  like compters alot* don't we all?*  I've always liked doing different things with computers being amazed at each new accomplishment. Untill about two years ago though i didn't even understand what an Operating system was. I knew there was Windows and Mac but didn't understood what that ment. I did research and found out about Linux and the free alternative software. I have grown up with windows and always hated how greedy microsoft is with their software. Linux seemed great. And it is. When i got my own computer only months ago(pre-installed with xp) i quickly installed Ubuntu 9.04 from a disc previously burnt at a friends' and had a dual boot setup only an hour and a half later. 

Okay here's my situation: college is comming soon for me and i have always known i wanted to do something with computers and one thing stands out that i want to try still: Programming. I want to give programming a try but need help where to start. I have never done any programming before but have done a lot of research and know the very basics. I'm just clueless about where to start. Can someone give me some help?

P.s. Sorry for the long post.

---

### Post by abhilashm86 on 2009-06-13
go through this ,read all topics, it is real worth:)
[http://ubuntuforums.org/showthread.php?t=1006666](http://ubuntuforums.org/showthread.php?t=1006666)

you find almost all answers to your question..................

---

### Post by abhilashm86 on 2009-06-13
well if you haven't started programming, please do python as it has less syntax and problems, so you can concentrate on logic and reasons for a problem..........others are quiet hard to crack initially:)

---

### Post by jo$h01 on 2009-06-13
ok. i will look at that. thank you very much. Its nice to find ppl that are as nice as the are believed to be. Ive been too many other forums and turned away at how rude ppl were. anyways thnks.

---

### Post by Bodsda on 2009-06-13
> **abhilashm86 said:**
> well if you haven't started programming, please do python as it has less syntax and problems, so you can concentrate on logic and reasons for a problem..........others are quiet hard to crack initially:)

python has less syntax?? 

I dont really agree with that at all. Indentation is a major part of pythons syntax and can screw you up immensely, but in C++ it is not an issue, consider the following.

python[php]
while True:
print "This does not work"
[/php]
C++
[php]
#include <iostream>
using namespace std;
int main()
{
for(;;){
cout << "This will work" << endl;
}
return 0;
}
[/php]

The python example will not work because the indentation level is not correct, but in C++ indentation means nothing, the following python example is correct indentation (assuming indents of 4)
[php]
while True:
    print "This will work"
[/php]

Regards,

Bodsda

p.s: Python is a brilliant beginners language though :)

---

### Post by matmatmat on 2009-06-13
Use python if you're a beginner, then learn C(++) :)
> 
python has less syntax??

I dont really agree with that at all. Indentation is a major part of pythons syntax and can screw you up immensely, but in C++ it is not an issue, consider the following.

but isn't c++ more complicated & there are more things that can "crew you up immensely"

---

### Post by Ariel David Moya Sequeira on 2009-06-13
I grew up with the LOGO programming language, so I recommend it for begginers. It is easy to understand and it is possible to make very complex programs (such as a Morse code "translator" using binary trees or Julia Set plotters) in a very simple way.

Anyway, from where I am, the begginers' languages are PASCAL, SCHEME and LOGO. Not many people learn to program with C++ at first glance. Although, Python is a very good choice.

---

### Post by Bodsda on 2009-06-13
> **matmatmat said:**
> Use python if you're a beginner, then learn C(++) :)

but isn't c++ more complicated & there are more things that can "crew you up immensely"

C++ is more difficult to understand initially yes. My post was no bash on python, more a note on the possible problems it has, and as C++ is my second language I used that as an example. 

I would say unless you have a lot of time and you dont have a short attention span and you also dont have a habit of quitting when things get hard then by all means learn C++. If you want to get stuck in quickly then go for something high level like python.

Regards,

Bodsda

---

### Post by abhilashm86 on 2009-06-13
> **matmatmat said:**
> Use python if you're a beginner, then learn C(++) :)

but isn't c++ more complicated & there are more things that can "crew you up immensely"

yes i agree to you, python is just easy to learn,
[PHP]
>>> a='ubu'
>>> b='ntu'
>>> a+b
'ubuntu'

[/PHP]

well the arthmetic and string handling is much fun and easier........

---

### Post by jo$h01 on 2009-06-13
Thanl you so much for your opinions. i think ill start off with python as everyone is suggesting it. i have been reading the FAQS and i think im set. thank you all very much!

---

### Post by Sinkingships7 on 2009-06-13
> **Bodsda said:**
> python has less syntax?? 

I dont really agree with that at all. Indentation is a major part of pythons syntax and can screw you up immensely, but in C++ it is not an issue, consider the following.

python[php]
while True:
print "This does not work"
[/php]
C++
[php]
#include <iostream>
using namespace std;
int main()
{
for(;;){
cout << "This will work" << endl;
}
return 0;
}
[/php]

The python example will not work because the indentation level is not correct, but in C++ indentation means nothing, the following python example is correct indentation (assuming indents of 4)
[php]
while True:
    print "This will work"
[/php]

Regards,

Bodsda

p.s: Python is a brilliant beginners language though :)

While the person your post replied to didn't give a comparison, you did. But you used C++, which is odd because Python has much less syntax than C++, though not less than other languages. Just because the code example you gave works, that doesn't make it good code, nor does it mean that C++ holds any advantage over Python in any way. In fact, I could say that Python's semi-strict indentation rules are a good thing, because it enforces the way code should be written anyway.

Point: being able to write sloppy C++ code doesn't give it any advantage over Python.

Nice signature, by the way. Reminds me of one I saw not too long ago.... :p

---

### Post by Sinkingships7 on 2009-06-13
> **matmatmat said:**
> 
but isn't c++ more complicated & there are more things that can "crew you up immensely"

Yes. Because C++ tries to be flexible and all-"powerful", it enforces inconsistent design choices among many programmers.

---

### Post by soltanis on 2009-06-13
> **Sinkingships7 said:**
> Yes. Because C++ tries to be flexible and all-"powerful", it enforces inconsistent design choices among many programmers.

Arguably it "allows" you to use whatever design you want, but in truth a multi-paradigm language gives you multi-paradigm code.

---

### Post by Sinkingships7 on 2009-06-13
> **soltanis said:**
> Arguably it "allows" you to use whatever design you want, but in truth a multi-paradigm language gives you multi-paradigm code.

Well said.

---

### Post by Bodsda on 2009-06-13
> **Sinkingships7 said:**
> While the person your post replied to didn't give a comparison, you did. But you used C++, which is odd because Python has much less syntax than C++, though not less than other languages. Just because the code example you gave works, that doesn't make it good code, nor does it mean that C++ holds any advantage over Python in any way. In fact, I could say that Python's semi-strict indentation rules are a good thing, because it enforces the way code should be written anyway.

Point: being able to write sloppy C++ code doesn't give it any advantage over Python.

Nice signature, by the way. Reminds me of one I saw not too long ago.... :p

Never said that it was good code, just pointing out that python syntax can cause headaches just like any other languages syntax can.

ty for the sig compliments, thought that one up all on my own, honest :-\"

---

### Post by ActiveFrost on 2009-06-13
Python is the same as vocabulary - you don't need to know it from A-Z .. learn the basics and you are ready to proceed to other languages/tasks :)

---

