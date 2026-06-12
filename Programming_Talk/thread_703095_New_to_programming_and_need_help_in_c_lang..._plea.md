---
title: "New to programming and need help in c lang... please"
date: 2008-02-21
forum: Programming Talk
---

### Post by pjjuang24 on 2008-02-21
Hi I am very new to programming in general and this semester I have to take a C programming class in which I have never seen computer language in my life so I have some questions about my homework if anyone could help me.

So the first one this is what i have so far...but it will not compile I do not know what is wrong with it

//This program that takes three values a, b, and c to
//identify if a triangle can be formed that have the given lengths.  It //also tells you if it is equilateral or not, isosceles or not, and/or right //angled or not

#include <stdio.h>

main()
{
        double a, b, c;
        printf("Enter three values>");
        scanf("%lf, %lf, %lf", &a, &b, &c);

        if ((a>1) (b>1) (c>1))
        {
                if ((a+b>c) && (b+c>a) && (c+a>b))
                {
                        printf("A triangle can be formed with these lengths\n");
                }
                                if ((a==b) && (b==c) && (a==c))
                                {
                                        printf("This is an equilateral triangle\n");
                                }
                                else
                                {
                                        printf("This is not an equilateral triangle\n");
                                }
                                if((a==b) || (b==c) || (c==a))
                                {
                                        printf("This is an isosceles triangle\n");                              
                                }
                                else
                                {
                                        printf("This is not an isosceles triangle\n");
                                }
                        if ((pow(c,2)==pow(a,2)+pow(b,2)) || (pow(a,2)==pow(b,2)+pow(c,2)) || (pow(b,2)==pow(a,2)+pow(c,2)))
                        {
                                printf("This is a right triangle\n");
                        }
                        else
                        {
                                printf("This is not a right triangle\n");
                        }
                else
                {
                        printf("A triangle cannot be formed with these lengths\n");
                }

        }
        else
        {
                printf("These numbers cannot form a triangle\n");
        }
}



The second question is...after I compile the program, then I tried to input negative numbers but the output said command cannot be found.  Is there an "if" function I can put in the program that will also read the negative numbers? or what do I do?

//This program will tell you if three points on a coordinate graph are
//collinear.

#include <stdio.h>

main()
{
        double x1, y1, x2, y2, x3, y3;

        printf("Enter three points>");
        scanf("%lf, %lf, %lf, %lf, %lf, %lf", &x1, &y1, &x2, &y2, &x3, &y3);

        if (((x1==x2) && (x2==x3) && (x1==x3)) || ((y1=y2) && (y2=y3) &&(y1==y3)))
        printf("These points are collinear\n");

        else
        printf("These points are not collinear\n");
}



If you could  help that would be great thank you so much!!

Polly

---

### Post by dwhitney67 on 2008-02-21
Here's the code again... please note the differences, and more importantly that I surrounded the code with PHP tags for better readability.

Btw, your original code had one more "else" statement than was perhaps necessary.  Revisit the logic in your code.

[PHP]#include <stdio.h>
#include <math.h>    // added for pow()

int main()    // main should return an integer status
{
  double a, b, c;
  printf("Enter three values>");
  scanf("%lf, %lf, %lf", &a, &b, &c);

  if ((a>1) && (b>1) && (c>1))    // added the &&s
  {
    if ((a+b>c) && (b+c>a) && (c+a>b))
    {
      printf("A triangle can be formed with these lengths\n");
    }
    if ((a==b) && (b==c) && (a==c))
    {
      printf("This is an equilateral triangle\n");
    }
    else
    {
      printf("This is not an equilateral triangle\n");
    }
    if((a==b) || (b==c) || (c==a))
    {
      printf("This is an isosceles triangle\n");
    }
    else
    {
      printf("This is not an isosceles triangle\n");
    }
    if ((pow(c,2)==pow(a,2)+pow(b,2)) || (pow(a,2)==pow(b,2)+pow(c,2)) || (pow(b,2)==pow(a,2)+pow(c,2)))
    {
      printf("This is a right triangle\n");
    }
    else
    {
      printf("This is not a right triangle\n");
    }
  }
  else
  {
    printf("A triangle cannot be formed with these lengths\n");
  }

  return 0;    // return status of main()
}
// No matching if-statement
//else
//{
//printf("These numbers cannot form a triangle\n");
//}
//}[/PHP]

---

### Post by cb951303 on 2008-02-21
first one: you forgot to include stdio.h and math.h also there is two else for the last if and your first if should include && between conditions

```

[COLOR="Red"]#include <stdio.h>
#include <math.h>[/COLOR]

...

	if ([COLOR="Red"](a>1) && (b>1) && (c>1)[/COLOR]) {
		...
		else {
			printf("This is not a right triangle\n");
		}
                [COLOR="Red"]else...WRONG[/COLOR]
...

```

also please indent your code before posting so that people can read it
cheers

EDIT: sorry for double

---

### Post by pjjuang24 on 2008-02-21
Thank You very much! I tried it and it still did not compile but I'm thinking of just sending in my hw with error because I really cannot find them.  This really did help me though to understand if statements though.  Thank you again!!

---

### Post by pjjuang24 on 2008-02-21
And sorry if I didn't indent if you noticed I still don't really even know how to use internet language -- I don't even know what that's called!

---

### Post by cb951303 on 2008-02-21
> **pjjuang24 said:**
> Thank You very much! I tried it and it still did not compile but I'm thinking of just sending in my hw with error because I really cannot find them.  This really did help me though to understand if statements though.  Thank you again!!

what's the error msg? :)

---

### Post by pjjuang24 on 2008-02-21
This is what is says

[PHP]
Undefined                       first referenced
 symbol                             in file
pow                                 /var/tmp//cck6RheD.o
ld: fatal: Symbol referencing errors. No output written to a.out
collect2: ld returned 1 exit status
[/PHP]

---

### Post by dwhitney67 on 2008-02-21
Ensure that you have included <math.h>

```
#include <math.h>
```

You may also need to link in the math library.  To do this:

```
gcc yourProgram.c -lm
```

---

### Post by Lusst on 2008-02-23
I'm in the same boat as you are - first semester programmer here, and also working on a homework assignment...albeit, mine is a little easier...and it's C++, not C...but I didn't think this problem warranted a new thread.

Here's what I have so far:

```
#include <iostream.h>
#include <iomanip.h>
#include <math.h>
#include <conio.h>
#include <stdio.h>
#include <stdlib.h>

int main()
{

double a,b,c;

cout << setw (50) << "Enter the lengths of the three sides of a triangle..." << endl;
cin >> a >> b >> c;

if ((pow(a,2) == pow(b,2)+ pow(c,2)) || (pow(b,2) == pow(a,2) + pow(c,2)) || (pow(c,2) == pow(a,2) + pow(b,2)));
cout << "This triangle is a right triangle" << endl;

else
cout << "This triange is not a right triangle, but it is still awesome in my book..." << endl;


getch();
return 0;
}
```

Yes, it's heavy on the header files...for some reason, my teacher wants it this way.

Anyhoo, I'm receiving this error when compiling:
> expected primary-expression before "else" 

expected `;' before "else" 

I can't find anything wrong, but I'm thinking that it's something simple that is right under my nose.

---

### Post by LaRoza on 2008-02-23
First, conio.h is not standard. Remove it, and use getchar() instead of getch().

There is a semicolen at the end of the if statement, remove it to fix the error.

(And I hope your instructor didn't say to include those headers.)
[php]
#include <iostream>
#include <cmath>

int main()
{

    double a,b,c;

    std::cout << "Enter the lengths of the three sides of a triangle..." << std::endl;
    std::cin >> a >> b >> c;

    if ((pow(a,2) == pow(b,2)+ pow(c,2)) || (pow(b,2) == pow(a,2) + pow(c,2)) || (pow(c,2) == pow(a,2) + pow(b,2)))
    {
        std::cout << "This triangle is a right triangle" << std::endl;
    }
    else
    {
        std::cout << "This triange is not a right triangle, but it is still awesome in my book..." << std::endl;
    }
    return 0;
}
[/php]

Compile with g++.

See [http://ubuntuprogramming.wikidot.com](http://ubuntuprogramming.wikidot.com) for how to use g++.

---

### Post by Lusst on 2008-02-23
Removing the semi-colon after the if statement did the trick...rawk!

We use Borland's C++ Builder back at the school lab, and for some reason, if one of the five header files our teacher wants (conio, condefs, stdlib, stdio, iostream) aren't there, he takes points off.  

*shrug*

Don't ask me why, that's just how it is.

---

### Post by LaRoza on 2008-02-23
> **Lusst said:**
> Removing the semi-colon after the if statement did the trick...rawk!

We use Borland's C++ Builder back at the school lab, and for some reason, if one of the five header files our teacher wants (conio, condefs, stdlib, stdio, iostream) aren't there, he takes points off.  

*shrug*

Don't ask me why, that's just how it is.

See my code, that is the way it should be.

If your instructor told you to include those headers, it shows a lack of understanding of C++. I hope you are able to learn aside from that.

(See my wiki for C++ references, if you want to keep yourself standard)

---

### Post by slavik on 2008-02-23
> **Lusst said:**
> Removing the semi-colon after the if statement did the trick...rawk!

We use Borland's C++ Builder back at the school lab, and for some reason, if one of the five header files our teacher wants (conio, condefs, stdlib, stdio, iostream) aren't there, he takes points off.  

*shrug*

Don't ask me why, that's just how it is.
tell him to stop living in the early 90s and to get with the ISO standard ... also, dump borland and use soemthing better.

---

### Post by Lusst on 2008-02-23
Yeah...he's been programming since the '60's, and he's set in his ways...which includes sitting at his desk and playing Spider Solitaire all the while ignoring our questions.

Thanks for the help boys...I'll be hanging around here often, I have much to learn.

---

### Post by LaRoza on 2008-02-23
> **Lusst said:**
> Yeah...he's been programming since the '60's, and he's set in his ways.  

Thanks for the help boys...if I hang around here long enough, I'll be learning some cool stuff.

Write it in Fortran.

If you hang around here, you will see some wild stuff. (So brace yourself :-))

Also, you will learn that not all here are male...

---

### Post by slavik on 2008-02-23
seriously though, go to the department head and complain about being taught crap ...

---

### Post by Zwack on 2008-02-23
> **LaRoza said:**
> Write it in Fortran.

If you hang around here, you will see some wild stuff. (So brace yourself :-))

Also, you will learn that not all here are male...

I second all three of those... 

Although my Fortran is mostly Fortran 77 with some Fortran IV pieces...  Fortran 90 is just too recent for me.  :-)

Z.

---

### Post by LaRoza on 2008-02-23
> **Zwack said:**
> I second all three of those... 

Although my Fortran is mostly Fortran 77 with some Fortran IV pieces...  Fortran 90 is just too recent for me.  :-)

Z.

Fortran 77 only, for me.

Fortran 2008 is coming out soon I hear.

---

### Post by yabbadabbadont on 2008-02-24
I learned Fortran 66.... in the early 80's.  (I had a lousy instructor)

I ended up writing the code in (self taught) BASIC and then translating into Fortran.  Probably the worst possible way to have done it.  I learned the proper way of doing it while writing programs for my engineering classes.  The same was true for differential and partial differential equations.  My math classes were easy enough, but I gained true understanding through application to real world problems.

Edit: I should add that I've forgotten most of what I knew about all three.  :D

---

### Post by Lusst on 2008-02-24
Come to think of it, I could probably get on my teacher's good side if I created a program that made Skittles pop out of the A drive.

*hits the books*

> **LaRoza said:**
> Also, you will learn that not all here are male...

I hail from a few message boards, most notably an MMA site that I mod.  There, the rule about gender is clear: "Everyone is male, unless proven otherwise."

---

### Post by LaRoza on 2008-02-24
> **Lusst said:**
> Come to think of it, I could probably get on my teacher's good side if I created a program that made Skittles pop out of the A drive.

*hits the books*

"A drive?" use Linux :-)

---

### Post by pmasiar on 2008-02-24
> **Lusst said:**
>  "Everyone is male, unless proven otherwise."

Not sure how you prove gender? I would think twice (or more) if requirement of membership in a forum was sending my naked pic to admins for approval :-)

Here, we know we do have some  members who happens to be female, and we are proud about being inclusive and welcoming to anyone  willing to learn. Just let you know.

BTW I found that presence of female moderators improves communication. Not sure why tho. Maybe because only above-average smart gals stick around in forums long enough? Or maybe sticking to Ubuntu Code of Conduct disqualifies (in time) jerks? I don't know.

---

### Post by slavik on 2008-02-24
sex is biological, gender is social. :)

---

### Post by LaRoza on 2008-02-24
> **pmasiar said:**
> Not sure how you prove gender? I would think twice (or more) if requirement of membership in a forum was sending my naked pic to admins for approval :-)

Here, we know we do have some  members who happens to be female, and we are proud about being inclusive and welcoming to anyone  willing to learn. Just let you know.

BTW I found that presence of female moderators improves communication. Not sure why tho. Maybe because only above-average smart gals stick around in forums long enough? Or maybe sticking to Ubuntu Code of Conduct disqualifies (in time) jerks? I don't know.

You can't prove gender, in fact, you can't even prove a species (You know, the dog thing)

Please, pmasiar, don't. That would definately earn you an infraction (goes for everyone else too.)

I am LaRoza, for the sake of sanity, you can use any pronoun you desire, just don't assume.

That is an interesting idea. Perhaps it is the thought that the moderator is female, not the actual fact. I didn't know (or even think about) the gender of other mods, but if I were to have to guess based on posts, I wouldn't think that the female/male mods where different. But I never really considered it, so it may be as you say.

---

### Post by pmasiar on 2008-02-24
> **LaRoza said:**
> Please, pmasiar, don't. That would definately earn you an infraction.

Did you missed I joked? I do not feel any urgency to prove my gender here. But from  Lusst's post it seems like female members would possibly to prove their gender on his forum :-) Or maybe they use different more advanced methods. Just curious :-)

---

### Post by LaRoza on 2008-02-24
> **pmasiar said:**
> Did you missed I joked? I do not feel any urgency to prove my gender here. But from  Lusst's post it seems like female members would possibly to prove their gender on his forum :-) Or maybe they use different more advanced methods. Just curious :-)

I was joking as well. :-)

Not aimed at you specifically, just the general though of such "verifications".

(Could be considered later, I will ask the admins)

I could be male, female, bot, or an alien. No way to prove it either way.

---

### Post by yabbadabbadont on 2008-02-24
I saw a quote in another thread that seems appropriate:

"This is the internet, where men are men, women are men, and children are FBI."

:D

Now for something on-topic (gasp): I don't know how it stands these days, but Borland's C++ Builder used to be a very good tool.  We used it for several years at my last job.  It was only the last year or so before I left, that we started migrating to C#.  We were switching a lot of our application suite to be more of a web-services type of thing, and C# was the more appropriate tool.

---

### Post by Zwack on 2008-02-24
In person would be the only way that you could actually prove your sex/gender/species... And even then it would only prove that the being that the moderator met was that sex/gender/species and claimed to be the online entity in question.

Personally, I'm sitting in a room with several other species, including at least two  hybrids...  And I'm going to claim that I don't remember which of those species I am...

Z.

---

