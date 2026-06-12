---
title: "Is it okay to use C in C++ code"
date: 2011-09-05
forum: Programming Talk
---

### Post by alegomaster on 2011-09-05
I know that C code can mostly be used (some exceptions) in C++ code. I'm joining a local robotics team which uses C++ to code their robots. 

Do you think it will be okay if I use C code because I'm used to it instead of C++ code (Which I never learned), and just use C++  code for parts where they use classes? Would it make a speed difference using C functions instead of C++ functions?


Any opinions would be helpful.

---

### Post by Arndt on 2011-09-05
> **alegomaster said:**
> I know that C code can mostly be used (some exceptions) in C++ code. I'm joining a local robotics team which uses C++ to code their robots. 

Do you think it will be okay if I use C code because I'm used to it instead of C++ code (Which I never learned), and just use C++  code for parts where they use classes? Would it make a speed difference using C functions instead of C++ functions?


Any opinions would be helpful.

The important thing is probably what the rest of the team think about it. I suppose that you won't be able to avoid looking at and understand their C++ code.

---

### Post by alegomaster on 2011-09-05
> **Arndt said:**
> The important thing is probably what the rest of the team think about it. I suppose that you won't be able to avoid looking at and understand their C++ code.

True, but if I write code, I would better off be with C because I know more about it, but I could try to teach myself C++.

On a side note does anybody know a good free online book about learning C++. I am getting a Pocketbook 902 so I could read the book on there.

---

### Post by karlson on 2011-09-05
> **alegomaster said:**
> Do you think it will be okay if I use C code because I'm used to it instead of C++ code (Which I never learned), and just use C++ code for parts where they use classes?


That would be a good question to ask the team this question.

> 
Would it make a speed difference using C functions instead of C++ functions?
Any opinions would be helpful.

I don't know if C code will make any speed difference in the code you write.  You can write code in C that will not perform well and C++ that performs decently and vice versa.

---

### Post by karlson on 2011-09-05
> **alegomaster said:**
> On a side note does anybody know a good free online book about learning C++. I am getting a Pocketbook 902 so I could read the book on there.

[http://www.amazon.com/Accelerated-C-Practical-Programming-Example/dp/020170353X/ref=sr_1_1?ie=UTF8&qid=1315258539&sr=8-1](http://www.amazon.com/Accelerated-C-Practical-Programming-Example/dp/020170353X/ref=sr_1_1?ie=UTF8&qid=1315258539&sr=8-1)
[http://www.amazon.com/Effective-Specific-Improve-Programs-Designs/dp/0321334876/ref=pd_sim_b_1](http://www.amazon.com/Effective-Specific-Improve-Programs-Designs/dp/0321334876/ref=pd_sim_b_1)
[http://www.amazon.com/More-Effective-Improve-Programs-Designs/dp/020163371X/ref=pd_sim_b_1](http://www.amazon.com/More-Effective-Improve-Programs-Designs/dp/020163371X/ref=pd_sim_b_1)

Start with these

---

### Post by alegomaster on 2011-09-05
> **karlson said:**
> [http://www.amazon.com/Accelerated-C-Practical-Programming-Example/dp/020170353X/ref=sr_1_1?ie=UTF8&qid=1315258539&sr=8-1](http://www.amazon.com/Accelerated-C-Practical-Programming-Example/dp/020170353X/ref=sr_1_1?ie=UTF8&qid=1315258539&sr=8-1)
[http://www.amazon.com/Effective-Specific-Improve-Programs-Designs/dp/0321334876/ref=pd_sim_b_1](http://www.amazon.com/Effective-Specific-Improve-Programs-Designs/dp/0321334876/ref=pd_sim_b_1)
[http://www.amazon.com/More-Effective-Improve-Programs-Designs/dp/020163371X/ref=pd_sim_b_1](http://www.amazon.com/More-Effective-Improve-Programs-Designs/dp/020163371X/ref=pd_sim_b_1)

Start with these
I need a free online book, because I don't have enough money for them, and I dont have any interest in C++ other then the robotic team.

I found a free online book for using GAS, there must be something on C++.

---

### Post by nmaster on 2011-09-05
define "book"... i'm sure what a "Pocketbook 902".

you could try this:
[http://www.howtoforge.com/learning-c-cplusplus-step-by-step](http://www.howtoforge.com/learning-c-cplusplus-step-by-step)

---

### Post by cgroza on 2011-09-05
Try reading the official C++ tutorial first. It gives you a good introduction over its capabilities and concepts. That might be all you need to program robotics.

---

### Post by alegomaster on 2011-09-05
> **cgroza said:**
> Try reading the official C++ tutorial first. It gives you a good introduction over its capabilities and concepts. That might be all you need to program robotics.

What is the official C++ tutorial

---

### Post by dwhitney67 on 2011-09-05
Embedded C++...  [http://www.caravan.net/ec2plus/rationale.html](http://www.caravan.net/ec2plus/rationale.html)

Here's a project that employed Embedded C++: [http://en.citizendium.org/wiki/Advanced_Extremely_High_Frequency_%28satellite%29](http://en.citizendium.org/wiki/Advanced_Extremely_High_Frequency_%28satellite%29)

---

### Post by karlson on 2011-09-05
> **alegomaster said:**
> What is the official C++ tutorial

[http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

for example

---

### Post by ve4cib on 2011-09-06
> **alegomaster said:**
> I know that C code can mostly be used (some exceptions) in C++ code. I'm joining a local robotics team which uses C++ to code their robots. 

Do you think it will be okay if I use C code because I'm used to it instead of C++ code (Which I never learned), and just use C++  code for parts where they use classes? Would it make a speed difference using C functions instead of C++ functions?


Any opinions would be helpful.

Personally I don't have much problem with slightly polluted C++ code.  Sometimes all you need is a simple struct to hold a couple of variables, or the odd malloc to dynamically create an array of some primitive type.   But the emphasis should be on "slightly."  C++ is an object-oriented language, and outside of a few rare circumstances you should probably follow that model.

Really though, it's your team's collective opinion that matters more than ours.  Our robotics team also uses C++, but with generous helpings of structs, printf, and malloc calls where necessary, or where it suits a specific programmer's style.  The core robot library we use is entirely object-oriented, but individual projects written for use with the robot will often be written in a looser style.  But we all accept that we have different coding styles, and work around it.  As long as the code is clean, documented, and fairly self-explanatory we don't care too much about the specifics.  But we may be a much more laid-back team than your own.

Best advice: talk to your team and ask them if writing in a more C style is acceptable.

---

### Post by dwhitney67 on 2011-09-06
> **ve4cib said:**
> Personally I don't have much problem with slightly polluted C++ code.  Sometimes all you need is a simple struct to hold a couple of variables, or the odd malloc to dynamically create an array of some primitive type.   But the emphasis should be on "slightly."  C++ is an object-oriented language, and outside of a few rare circumstances you should probably follow that model.

Really though, it's your team's collective opinion that matters more than ours.  Our robotics team also uses C++, but with generous helpings of structs, printf, and malloc calls where necessary, or where it suits a specific programmer's style.  The core robot library we use is entirely object-oriented, but individual projects written for use with the robot will often be written in a looser style.  But we all accept that we have different coding styles, and work around it.  As long as the code is clean, documented, and fairly self-explanatory we don't care too much about the specifics.  But we may be a much more laid-back team than your own.

Best advice: talk to your team and ask them if writing in a more C style is acceptable.

In C++, a class and a struct share only one difference.  Anything declared within a class is private, unless otherwise specified; whereas with a struct, anything declared is public, unless otherwise specified.  All other features that apply to classes also apply to structs.  So don't think of the struct keyword as a C-only type; it is also used in C++

Using malloc() in C++ does not call the constructor for the object being instantiated.  You would also be unable to take advantage of having the object's destructor called when free() is called.  In addition, smart pointers would not be able to do their job properly.

So, if you want to develop in C, then do just that.  If you want to develop in C++, forgo the archaic and superseded features of C.

---

### Post by alegomaster on 2011-09-06
> 

			 		 	 	 [http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

for example 		                   		  		  		 		 			 				__________________
				Regards,

Karlson 			




Thanks this is perfect!

---

### Post by KdotJ on 2011-09-06
I don't know the full details of the situation, but in my opinion I would take this opportunity to learn C++ seeing as this is what they use and I'm sure your team will appreciate it more if you fit in with the project in this way. Also, it's a great way to do it, you have real in-use code to learn from and real projects to code.  

Just my two cents

---

