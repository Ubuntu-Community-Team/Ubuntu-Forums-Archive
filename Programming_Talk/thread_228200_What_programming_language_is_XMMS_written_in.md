---
title: "What programming language is XMMS written in?"
date: 2006-08-02
forum: Programming Talk
---

### Post by H.E. Pennypacker on 2006-08-02
I've looked everywhere for the answer to what language XMMS was written in, but I can't find an answer anywhere, including xmms.org.  

Does anyone know?

If necessary, I'll try to learn the language, because I want to make some changes to it.  I suppose I can't learn Python and make changes to XMMS' source code using Python eventhough XMMS is written in another language?  It may be a silly question.  I guess you can't modify one language using another language.

Basically, I want to improve the playlist, remove a few things, and use GTK+2 , and possibly prepare for GTK+3 (whenever it may arrive).  By the way, I know of most XMMS forks, and I am not pleased with any of them.

---

### Post by falcon15500 on 2006-08-02
A quick look at the latest CVS shows that it appears to be written in C.  Good luck!

falc

---

### Post by falcon15500 on 2006-08-02
-- Ignore Dupe --

---

### Post by Engnome on 2006-08-02
> **falcon15500 said:**
> A quick look at the latest CVS shows that it appears to be written in C.  Good luck!

falc

hehe you'll need it, and even more patience.

btw will it be a fork or just patches?

---

### Post by Grey on 2006-08-02
Yup, XMMS is 100% pure C.  I had a look through the source code a while back, as I am making a GPL'd shoutcast client for Nintendo DS.  I didn't actually use much of the code, as my architecture is very different (mine is a lot simpler, but ballooning into something more), but I was actually pretty impressed with what I saw.

Might I suggest working on XMMS2 instead though?  I check on it every now and then, and it seems to be coming along nicely.  And you could write a frontend in whatever language you like.

---

### Post by H.E. Pennypacker on 2006-08-02
> A quick look at the latest CVS shows that it appears to be written in C. Good luck!

Just my luck..C!  The language I had been trying to avoid all this time.  

> hehe you'll need it, and even more patience.

It may be simply easier and faster for me to to program an entirely new media player instead of bothering to learn C.  C, although recommended by many, has the appearance of being such a clumsy language.  Its difficult to learn, takes a while to learn, and is a mess in terms of structure requiring a lot of programming.

I want to spend more time on ideas than programming.

> btw will it be a fork or just patches?

I am learning all the terminology right now, and I am not sure what the difference between a fork and a patch is, but I believe I was thinking more of a fork.  A patch solves one problem or another, I assume, while a fork leads an application into another direction.

> Yup, XMMS is 100% pure C. I had a look through the source code a while back, as I am making a GPL'd shoutcast client for Nintendo DS. I didn't actually use much of the code, as my architecture is very different (mine is a lot simpler, but ballooning into something more), [QUOTE]but I was actually pretty impressed with what I saw.[/QUOTE]

A number of people describe the XMMS source code as being a mess.  Not true?

> 
Might I suggest working on XMMS2 instead though? I check on it every now and then, and it seems to be coming along nicely.

XMMS2 fiercly opposes creating video functionality meaning the player would be a media player, not just audio.  They only want audio.  I am strongly against that.  Video playback is extremely important nowadays.  

> And you could write a frontend in whatever language you like.

I'll have to learn more about frontends, because in the end, I am only trying to make slight changes (better playlist, changes to the GUI, and support for many more media formats - format support amongst many applications is very poor - I need support for MANY more formats).

---

### Post by Grey on 2006-08-03
> **H.E. Pennypacker said:**
> Just my luck..C!  The language I had been trying to avoid all this time.

C is actually a really nice language.  I am an old C++ programmer, but recently decided to learn C, and I find it's actually a lot nicer than C++ in a number of ways.

> **H.E. Pennypacker said:**
> A number of people describe the XMMS source code as being a mess.  Not true?

I actually only looked at a couple of MP3 plugins, and the vorbis plugin, as that was all the code that was essential to me.  So I've never seen the base code.  But the plugin architecture seemed pretty good to me.

> **H.E. Pennypacker said:**
> XMMS2 fiercly opposes creating video functionality meaning the player would be a media player, not just audio.  They only want audio.  I am strongly against that.  Video playback is extremely important nowadays.

I personally am firmly against integrating a video and music player.  I want my video player to be highly specialized in playing video, and my audio player to be highly specialized in playing audio.  But that's my personal preference...

---

### Post by H.E. Pennypacker on 2006-08-03
> C is actually a really nice language. I am an old C++ programmer, but recently decided to learn C, and I find it's actually a lot nicer than C++ in a number of ways.

That is strange, because C++ is supposed to be an improvement of C.  You're going backwards.

> I personally am firmly against integrating a video and music player. I want my video player to be highly specialized in playing video, and my audio player to be highly specialized in playing audio. But that's my personal preference...

I am planning to create this project because I always loved RealOne Player, but the version of RealOne I am talking about is not available for Linux, and probably never will be.  RealOne did everything just fine, and better than other applications.  It handled many media formats, played both audio and video well, and looked decent.

That's my objective here.  I should ask RealNetworks for RealPlayer's source code.  Just kidding...  :)

---

### Post by Grey on 2006-08-03
> **H.E. Pennypacker said:**
> That is strange, because C++ is supposed to be an improvement of C.  You're going backwards.

That's entirely true.  And since I learned C++ first, I always assumed that it actually worked that way as well.  However, when I actually learned C, I discovered that a lot of things that I had assumed that you just couldn't do in C (such as classes), were very possible in C, and likely more efficient to boot.  I just really got off on the raw power of C.

But that being said, there are some things in C++ that C just cannot match, such as templates, ACTUAL classes, operator overloading, and compile time type checking.  I just prefer the more streamlined syntax of C.

> **H.E. Pennypacker said:**
> I am planning to create this project because I always loved RealOne Player, but the version of RealOne I am talking about is not available for Linux, and probably never will be.  RealOne did everything just fine, and better than other applications.  It handled many media formats, played both audio and video well, and looked decent.

That's my objective here.  I should ask RealNetworks for RealPlayer's source code.  Just kidding...  :)

You do realize that RealOne was disavowed because it was a spyware ridden piece of junk, right?  The Helix player was Real's attempt at winning our trust back after the RealOne disaster.

---

### Post by H.E. Pennypacker on 2006-08-03
> But that being said, there are some things in C++ that C just cannot match, such as templates, ACTUAL classes, operator overloading, and compile time type checking. I just prefer the more streamlined syntax of C.

You may know the answer to this question...why don't they take the best of C and put it in C++?  It would make best to take the best of both worlds, drop the worst, and put it into a single language.

> You do realize that RealOne was disavowed because it was a spyware ridden piece of junk, right? The Helix player was Real's attempt at winning our trust back after the RealOne disaster.

I know of all the hate that there is towards RealPlayer/RealOne, but the truth is that not a single player in any world (Windows or Linux) matches the quality of RealPlayer.  It has a thorough library (with lots of values), can be small enough, has a great playlist, and is optimal for streaming.  

I've had poor streaming with many Linux applications, and if an application had great streaming, it was poor in another area (e.g. its play list is not good enough).

---

### Post by ifokkema on 2006-08-04
Possibly slight OT, but in case you'd want to know:
You can check the language by either analysing the package dependencies (it depends on the C libraries) and/or by running 'file' over the package executable :)

---

### Post by wmcbrine on 2006-08-04
> **H.E. Pennypacker said:**
> You may know the answer to this question...why don't they take the best of C and put it in C++?All of C *is* in C++, with a few minor exceptions -- C++ is basically a superset of C. But that's the issue: C is a much simpler language, and -- although it's possible to write a C program and compile it unmodified with a C++ compiler -- the typical style of programming in C++ is somewhat different.

To put it another way: My copy of "The C Programming Language", 2nd edition, by Kernighan and Ritchie is 272 pages. My copy of "The C++ Programming Language", 3rd edition, by Stroustrup is 911 pages.

IMHO C is neither clumsy, nor difficult to learn (though for some people, it does seem difficult to get right). It *is* fairly low-level -- perhaps the lowest-level of the high-level languages; it's been called "portable assembly" -- which is what might lead to larger quantities of code being used than in some other languages, in some cases. But being so low-level also lets you get closer to the machine than anything short of assembly. Nothing else is faster.

I find C elegant.

---

### Post by Harleen on 2006-08-04
> **wmcbrine said:**
> I find C elegant.

While I agree with the rest of you posting, I have to oppose this statement. It's not the programming language that makes the style, it's the programmer. Or as my boss always says: You can program Fortran in any language.

Speaking about elegance, I think, that C (and C++) allows the programmer too much to do. If you only think about all the nasty things you can do with the post and prefix operators (i++) or casts on pointers...
Or look at the following simple and valid code and try to tell, which number is printed when the program is run. So much for elegance and C. ;) 

```
#include <stdio.h>

int main(void)
{
  int x[10];
  int y[10];
  const int z = 2;
  int i;
  
  for (i=0; i<10; ++i)
{
    x[i] = 9-i;
    y[i] = i;
}
 /*
   x = 9 8 7 6 5 4 3 2 1 0
   y = 0 1 2 3 4 5 6 7 8 9
 */
 printf("%d\n", z[y][x]);
 return 0;
}
```

---

### Post by LordHunter317 on 2006-08-05
> **Grey said:**
> However, when I actually learned C, I discovered that a lot of things that I had assumed that you just couldn't do in C (such as classes), were very possible in C,You can't, not without writing what the C++ compiler does for you.  In which case, what is the point?

> and likely more efficient to boot.Actually, almost always less efficent because you cannot make optimizations the compiler can.  It's just simply impossible.

[quote=wmcbrine]IMHO C is neither clumsy, nor difficult to learn (though for some people, it does seem difficult to get right).[/quote]Bullshit.  Write a program to take a string from the user, concatonate it with another string, and write the final string to the user.  And do it correctly, with no bugs and handling all error conditions correctly.  Then write the same thing in virtually any other language.

C is only not clumsy when you're essentially writing "high-level" assembly.

---

### Post by Grey on 2006-08-06
> **LordHunter317 said:**
> You can't, not without writing what the C++ compiler does for you.  In which case, what is the point?

What I didn't realize until learning C was that classes are not essential to actually doing what a class does.  Rather than creating an object,and performing operations on that object, it just works a little differently.  I found that there are ways around this.

1)  You can have private methods and variables by declaring global variables and methods in the module that you are coding.  Just prefix them with the "static" qualifier.  This will make those attributes invisible outside of the c file that you are modifying.

2)  Rather than using dot notation, just use a struct and a few helper functions.

For example, consider the classic point class taught in every C++ class that I've been to.  In C++, you would create an object, and use public methods to access it.  You know the drill, and I don't feel like typing out the test code.  In C, the test code might be more like this:

```

point p1;
point p2;
int dist;

p1.x = 0;
p1.y = 0;

//or, you could use something like... 
POINT_set(&p1, 0, 0);

dist = POINT_get_dist(p1, p2);

printf("Your distance is %d\n", dist);

```

Now is that honestly more complicated than using a C++ class?  And I'm willing to bet that the C way of doing things is faster, although I've not personally done any benchmarking.  As for compiler options, I'm sure the compiler will optimize similarly for both languages.  The real issue is that I highly doubt that any C++ programmers would write a class as I have detailed it above.

> **LordHunter317 said:**
> Bullshit.  Write a program to take a string from the user, concatonate it with another string, and write the final string to the user.  And do it correctly, with no bugs and handling all error conditions correctly.  Then write the same thing in virtually any other language.

Firstly, I just want you to know that I laughed pretty hard when I read this, as it was my first impression of the language as well, when I learned that there was no such thing as the string class in C.  However, I've learned much since then, and discovered that it's actually not so bad.  You just have to meet it with an open mind.

```
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int main() {
	char* s1[80];
	char* s2 = " and this is the second part";
	char* s3 = malloc;
	
	printf("Input the first part of the string: ");
	//this is the only bug I am aware of, in that only 80 bytes are allocated.
	//it can be corrected easily enough by taking in only one character at a
	//time, and allocating memory dynamically.  It would be about a 20 line 
	//function, that you would only have to write once.  But I've never 
	//personally had a need for it.
	scanf("%s", s1);
	printf("string is:\n%s%s\n", s1, s2);
	
	//BONUS method of doing it:
	s3 = malloc(strlen(s1)+strlen(s2)+1);
	strcpy(s3, s1); //copies s1 to s3
	strcat(s3, s2); //concatenates s3 and s2
	
	printf("string is:\n%s\n",s3);
}
```

---

### Post by LordHunter317 on 2006-08-06
> **Grey said:**
> What I didn't realize until learning C was that classes are not essential to actually doing what a class does.This is true, but you can't correctly emulate what they do in C.  Inheritance is impossible without doing what C++ does, for example.  Which brings me back to my original point.

> 1)  You can have private methods and variables by declaring global variables and methods in the module that you are coding.  Just prefix them with the "static" qualifier.  This will make those attributes invisible outside of the c file that you are modifying.This creates drastically different scoping for them, and that is a problem.  It makes ownership issues anywhere from "harder than it has to be" to simply impossible.

> Now is that honestly more complicated than using a C++ class? No, but you picked a poor example.  

> And I'm willing to bet that the C way of doing things is faster, although I've not personally done any benchmarking.Nope.

>  As for compiler options, I'm sure the compiler will optimize similarly for both languages.Nope.  Certain optimizations possible in C++ are impossible in psuedo-C++ in C, like the return value optimization.

> Firstly, I just want you to know that I laughed pretty hard when I read this,And the joke's on you.  Your code is wrong.  In several ways:[list][*]Limited buffers aren't allowed[*]You created a buffer overflow even with the limited buffer[*]Your error checking is insufficent[*]Your code fails to return a required return value.[/list]Like I said, simple tasks in C are simply too difficult.  BTW, reading characters one at a time is not required for arbitrary input.

---

### Post by Harleen on 2006-08-06
Additionally the code contains a memory leak (s3 is never freed). This is one of the things, that you avoid by using C++.
To remove the potential crash using a limited buffer for scanf you can use scanf("%as", &s3). This will allocate just as much memory as needed - but this is an extention of the GNU compiler and not ANSI conforming. For a strictly ANSI-C program I'd use fgets() instead of scanf.

I don't see the point in using C to programm object orientated. If I'm using C, I'm programming procedural, as the language was designed for it. C++ is much better suited for object orientation.

---

### Post by LordHunter317 on 2006-08-06
> **Harleen said:**
> For a strictly ANSI-C program I'd use fgets() instead of scanf.I'd use fgets() anyway.

And FWIW, the code only would leak memory if this wasn't main().  That being said, it's still good practice to make sure every malloc() is matched with free().

---

### Post by Grey on 2006-08-07
> Additionally the code contains a memory leak (s3 is never freed). This is one of the things, that you avoid by using C++.

Yeah, sorry, I was quickly writing that while my GF was rushing me to get out of the house so we could go shopping...  :P  I forgot the "free(s3);".  And I also seem to have a malloc where it doesn't belong, that nobody commented about yet ;).  But C++ would still require you to free the memory.  There's no automatic garbage collection in C++ either, so I hardly see that as a benefit.

But thanks for the tips everyone on how to read input from stdin with a dynamically sized buffer.  I was not aware of this before.  :)  (As I believe I mentioned earlier (apologies if I didn't), I am still learning C).

---

### Post by LordHunter317 on 2006-08-07
> **Grey said:**
>  But C++ would still require you to free the memory.No, it would not.  Memory management would be handled for me by std::string.  I'd only have to do that if I allocated my std::string on the freestore, but there would be no reason to do so here.

---

### Post by Grey on 2006-08-07
> **LordHunter317 said:**
> No, it would not.  Memory management would be handled for me by std::string.  I'd only have to do that if I allocated my std::string on the freestore, but there would be no reason to do so here.

Yes, indeed, sorry, I misread the original post.  I thought Harleen was talking about memory management in general, not strings.  I'm not thinking well today.

Btw, I was meaning to ask you about this, as I am curious:

> This creates drastically different scoping for them, and that is a problem. It makes ownership issues anywhere from "harder than it has to be" to simply impossible.

What exactly are you talking about?  I was under the impression that doing this in C++:

```

//something.h
class Something {
  public:
    int get_something();
  private:
    int do_something_private();
};

```

and...

```

//something.c
static int do_something_private();

int get_something();

```

were more or less equivalent?  I realize that static variables are significantly different, which is why you pass in structs rather than keeping private variables in C...  (sorry about the earlier post, I wasn't thinking... In a project I am working on, I actually am using static variables, but they belong there, and I was thinking about that when I wrote the post).  But as far as methods go, the scoping is fairly similar is it not?  (Sorry, I'm not trying to argue with you, I'm trying to learn, and this is the impression that I got from a webpage I read once).

So far as I know, there's no equivalent to private variables in C.  Which is why when you are doing an object oriented style thing, such as a string or a point, you pass the struct into the member functions.  Correct?  (If there is such a thing as private variables, I would love to know it)

---

### Post by LordHunter317 on 2006-08-07
> **Grey said:**
> What exactly are you talking about?  I was under the impression that doing this in C++:

```

//something.h
class Something {
  public:
    int get_something();
  private:
    int do_something_private();
};

```

and...

```

//something.c
static int do_something_private();

int get_something();

```

were more or less equivalent?For functions, sure[1].  But not for member variables and those are what you really are interested in hiding.

You jsut have to use Smalltalk-esque OOP in C if you choose to go down that route.

> So far as I know, there's no equivalent to private variables in C.Yep.  

> Which is why when you are doing an object oriented style thing, such as a string or a point, you pass the struct into the member functions.Yes, but you do that anyway in C++, you just don't know about it.  The first argument to any member function is a hidden 'this' pointer.

The difference is that in C++, the compiler will do checks to make sure only those member functions use the members declared private[2].  In C, there's no way to specify that or make the compiler do it.

[1]Actually, they're not quite the same due to some really esoteric C++ features.  They're not work talking about about, though.

[2]And friends and such.  However, what the compiler actually checks is that non-member, non-friend functions only use public (or protected for inherited classes) members.

---

### Post by Grey on 2006-08-08
Thank you very much.

You strike me as someone that I would LOVE to have on my team at any job.  You are exactly as harsh as you need to be, and are obviously very knowledgeable and experienced, and share your knowledge freely.  That's just awesome.  Please keep it up.  :)

---

