---
title: "stdio.h not found.  build-essential installed"
date: 2007-03-09
forum: Programming Talk
---

### Post by reformedgeek on 2007-03-09
Hey,

New to C programming and I have installed build-essential having followed various instructions from older posts.  I have even successfully ./configure and make install progs from source, but when I try to complile a simple c program, I get an error saying it can't find stdio.h??
I know its there, in /usr/include, so why won't gcc find it!
do i have to change my environment variables to include that folder?
please help!

---

### Post by lnostdal on 2007-03-09
post the following:

* source code
* your call(s) to gcc for compilation/linking
* the complete set of messages from gcc

edit:
note that you should in most cases not install software from source .. you should use the ubuntu-repositories to find software .. i'm saying this because there seem to be a lot of people who use linux like it was still 1995 where _everything_ was ./configure && make && make install

---

### Post by phossal on 2007-03-09
> **lnostdal said:**
> edit:
note that **you should in most cases not install software from source **.. you should use the ubuntu-repositories to find software .. i'm saying this because **there seem to be a lot of people who use linux like it was still 1995** where _everything_ was ./configure && make && make install

The trouble is that *not* installing from source leaves you with packaged versions of software *compiled* to 1995. I prefer to *install* like it was 1995, so I can use software *written* in 2007. It has to be compiled at *some* point. Why wouldn't we do it? Why add the unnecessary, and often messy, steps performed by someone else's package?

---

### Post by hod139 on 2007-03-09
> **phossal said:**
> The trouble is that *not* installing from source leaves you with packaged versions of software *compiled* to 1995. I prefer to *install* like it was 1995, so I can use software *written* in 2007. It has to be compiled at *some* point. Why wouldn't we do it? Why add the unnecessary, and often messy, steps performed by someone else's package?
This sounds like you want to use gentoo.  The reason I use ubuntu is for the package management and being more modern than Debian.  If I wanted to compile everything myself I would use Gentoo or BSD.

Installing packages from the repositories is usually easier than having to search for the source tarball online, and manage all the dependencies by hand.  Removing packages is also _much_ easier if you used the repository.  Many of these tarball packages never come with uninstallers.  Lastly, using the repositories means I get the software/security updates automatically, which saves lots of time.

---

### Post by lnostdal on 2007-03-09
phossal: that "discussion" isn't needed here .. either move along - or provide content

---

### Post by phossal on 2007-03-09
> **lnostdal said:**
> phossal: that "discussion" isn't needed here .. either move along - or provide content

You've lost your mind. 

> you should use the ubuntu-repositories to find software .. i'm saying this because there seem to be a lot of people who use linux like it was still 1995 where _everything_ was ./configure && make && make install
There isn't anything convincing in that statement, or perhaps I'd be convinced. It's just an opinion. I'm free to voice mine. Relax, and remember that you're participating in a forum setting.

---

### Post by phossal on 2007-03-09
> **hod139 said:**
> This sounds like you want to use gentoo.  The reason I use ubuntu is for the package management and being more modern than Debian.  If I wanted to compile everything myself I would use Gentoo or BSD.

Installing packages from the repositories is usually easier than having to search for the source tarball online, and manage all the dependencies by hand.  Removing packages is also _much_ easier if you used the repository.  Many of these tarball packages never come with uninstallers.  Lastly, using the repositories means I get the software/security updates automatically, which saves lots of time.

No, the reality is I don't want to compile *everything* myself. It's the third-party, commercial software that's much better installed manually. Even that isn't entirely true. I *often* refer people to your tutorial on installing Java using the package managers - and I usually give credit to the German gentleman who actually *packaged* it. I don't try to *hide* any options for getting and installing the software people need. People can do what they want. I've installed Java hundreds of times now, and I've received *hundreds* of thank yous for the time I've spent helping people get Java from SUN, though, so I'm confident it's a useful method to communicate.

---

### Post by reformedgeek on 2007-03-09
err. guys? Thanks for the responses, but...
I know about package repos and about using apt-get and .deb
but...occasionally one can find certain progs that arent in them. but that's beside the point.
I'm trying to compile this silly little program
#include </usr/include/stdio.h>

void main()
{
    printf("\nHello World\n");
}

output from cpp
simon@entropy:~/progs$ cpp hello.c
# 1 "hello.c"
# 1 "<built-in>"
# 1 "<command line>"
# 1 "hello.c"
hello.c:1:20: error:  stdio.h: No such file or directory

and this:

simon@entropy:~/progs$ gcc hello.c
hello.c: In function ‘main’:
hello.c:4: warning: return type of ‘main’ is not ‘int’


This was taken from
[http://www.physics.drexel.edu/courses/Comp_Phys/General/C_basics/c_tutorial.html](http://www.physics.drexel.edu/courses/Comp_Phys/General/C_basics/c_tutorial.html)

so its gotta be right, right?

---

### Post by phossal on 2007-03-09
~ Added additional post

---

### Post by phossal on 2007-03-09
My source looks like this:

```
#include <stdio.h>

[COLOR="Red"]**int**[/COLOR] main() {
	printf("Hello, World!");
}
```

A blank line follows the closing "}". I name it *hello.c*. I compile it like this:
```
gcc hello.c -o hello
```

And I run it:
```
./hello
```

---

### Post by reformedgeek on 2007-03-09
using your code works...how odd.

so it would seem the code listing below is wrong??

#include < stdio.h>

void main()
{
    printf("\n");
    printf("Hello World");
    printf("\n");
}

simon@entropy:~/progs$ gcc hello1.c
hello1.c:1:20: error:  stdio.h: No such file or directory
hello1.c: In function ‘main’:
hello1.c:5: warning: incompatible implicit declaration of built-in function ‘printf’
hello1.c:4: warning: return type of ‘main’ is not ‘int’

so does that mean that the above article is fundamentally incorrect?

I'm fairly familiar with gnu/Linux and have used it for a few years now, this is my first step into trying to learn c and i get stumped right at the start!

---

### Post by hod139 on 2007-03-09
> **reformedgeek said:**
> 
#include </usr/include/stdio.h>

void main()
{
    printf("\nHello World\n");
}

output from cpp
simon@entropy:~/progs$ cpp hello.c


This was taken from
[http://www.physics.drexel.edu/courses/Comp_Phys/General/C_basics/c_tutorial.html](http://www.physics.drexel.edu/courses/Comp_Phys/General/C_basics/c_tutorial.html)

so its gotta be right, right?

The code you pasted is not the code that is on that website.  Also, you should put all code inside [ code ] .. [ /code ] brackets (without the spaces).  The code from the website is:
```

#include < stdio.h>

void main()
{
    printf("\nHello World\n");
}
```
As phossal pointed out, the compiler is gcc, not cpp, and you must make sure the filename ends with the .c extension.

main really should return an int, but is not required with the old C standard.  You should get into the habit though of always having main return an int, since C++ and newer standards do require it.

---

### Post by hod139 on 2007-03-09
> **reformedgeek said:**
>  
simon@entropy:~/progs$ gcc hello1.c
hello1.c:1:20: error:  stdio.h: No such file or directory


Are you _sure_ you installed the package build-essential?

---

### Post by lnostdal on 2007-03-09
you should also compile with -Wall and -g .. 

-Wall makes gcc give you hints about potential problems in your code

-g makes gcc generate code that helps a debugger help you if something should go wrong

..so like this:

```

gcc -Wall -g hello.c -o hello

```


[quote=phossal]
You've lost your mind. 
[/quote]
right, i am also smarter and a better person than you .. is there anything else you'd like to add?

---

### Post by phossal on 2007-03-09
> **reformedgeek said:**
> [B]using your code works...how odd.
[/B]
so it would seem the code listing below is wrong??

#include <[COLOR="Red"]** s**[/COLOR]tdio.h>

[COLOR="Red"]**void**[/COLOR] main()
{
    printf("\n");
    printf("Hello World");
    printf("\n");
}

simon@entropy:~/progs$ gcc hello1.c
[COLOR="Red"]hello1.c:1:20: error:  stdio.h: No such file or directory
hello1.c: In function ‘main’:
hello1.c:5: warning: incompatible implicit declaration of built-in function ‘printf’
hello1.c:4: warning: return type of ‘main’ is not ‘int’[/COLOR]


1. The return type of the method should be *int* and not *main*.
2. Plus, it appears you have an extra space in this line: #include < stdio>

---

### Post by reformedgeek on 2007-03-09
ok ok, so i think i messed up in the reply.

this is what i initially used as code (copied pasted from the site, so i couldnt have mis-typed it)

```

#include < stdio.h>

void main()
{
    printf("\nHello World\n");
}

```

and this is what happens when i use gcc

simon@entropy:~/progs$ gcc hello1.c
hello1.c:1:20: error:  stdio.h: No such file or directory
hello1.c: In function ‘main’:
hello1.c:5: warning: incompatible implicit declaration of built-in function ‘printf’
hello1.c:4: warning: return type of ‘main’ is not ‘int’

and yes i'm_sure_I installed build-essential
i even apt-get --reinstall install build-essential

Would be it be something to do with using void instead of int?

---

### Post by reformedgeek on 2007-03-09
I checked it again and got rid of the extra space between < stdio.h>
still the same.

simon@entropy:~/progs$ gcc -Wall -g hello1.c
hello1.c:4: warning: return type of ‘main’ is not ‘int’

Is the article wrong on the site?

---

### Post by phossal on 2007-03-09
Dude. Take out *void* and replace it with *int*. lol

---

### Post by hod139 on 2007-03-09
> **phossal said:**
> Dude. Take out *void* and replace it with *int*. lol

That's not the problem.  This is C code, and that is legal (but bad practice).  The problem became apparent after putting his code inside the code blocks, the #include line is wrong, it has a space.
change
```

#include < stdio.h> 

```to```

#include <stdio.h>


``` (no space)

---

### Post by reformedgeek on 2007-03-09
done and it works. thanks.

So excuse my ignorance, but why doesnt it work with "void" ? Or is the article now so outdated that things have changed?

Also could you advise me on a good online resource / tutorial, seeing as the one i quoted seems to be somewhat 'wrong'

---

### Post by phossal on 2007-03-09
> **lnostdal said:**
> right,** i am also smarter and a better person than you **.. is there anything else you'd like to add?
You're certainly more entertaining, if not entirely rooted in reality. All I was trying to communicate was that there are other options outside of the *Ubuntu Way*. It's not an argument of opinion, it's a reality. You can download a packaged version of Sun's .bin file using Synaptic along with all of the code it contains, or you can simply download the .bin file direct. Which you *choose* is up to you, but the fact that those opportunities exist isn't my *opinion*.

---

### Post by phossal on 2007-03-09
> **hod139 said:**
> That's not the problem.  This is C code, and that is legal (but bad practice).  The problem became apparent after putting his code inside the code blocks, the #include line is wrong, it has a space.

Yeah, I highlighted that all in red a few posts ago.

---

### Post by hod139 on 2007-03-09
> **phossal said:**
> Yeah, I highlighted that all in red a few posts ago. I missed that, sorry.

---

### Post by reformedgeek on 2007-03-09
Well thanks for all the advice, I'll keep plugging along with this.

I'm please the ubuntu forum is still as useful as ever!

---

### Post by lnostdal on 2007-03-09
> **phossal said:**
> You're certainly more entertaining, if not entirely rooted in reality. All I was trying ..

..i suggest you stop trying .. or find someone else to try it on

---

### Post by phossal on 2007-03-09
> **lnostdal said:**
> ..i suggest you stop trying .. or find someone else to try it on

Oh, wow, I've never seen you melt down before. Software can be installed lots of ways. What exactly is our argument again?

---

### Post by lnostdal on 2007-03-09
go back and re-read it ..

edit: 
and answer on PM (or MSN, jabber/gtalk .. etc.) .. or start a new thread .. this doesn't belong here

edit2 (answering to post below):
oh, you shouldn't flatter yourself just yet .. edit3: actually; i'll take the rest of what you edited in just now as a compliment

now, again; if you have anything further to say feel free contact me outside this thread

---

### Post by phossal on 2007-03-09
What are you talking about? Hod and I dropped in and helped the OP while I simultaneously thrashed you. lol Our argument doesn't *belong* here, but it was entertainment to see you melt down and try to convince yourself that you're a better, smarter (if not more fragile) person than myself. Hod and I both noted the guy had an extra *space* in his code. You noted that you're a better person. The OP is on his way, and you're still complaining about non-related issues. It's comical. The sad part is that before this, even *I* respected you. I'm not sure what to think now. You're not God, mate. 

[EDIT] I didn't thrash you. I just tried to make a simple point, and you lost control of your emotions. It's weirding me out; it's like talking to my g/f. ;)

---

### Post by phossal on 2007-03-09
> **lnostdal said:**
> if you have anything further to say feel free contact me outside this thread

What? Do you want to meet in the street and have a dance-off? lol You're just getting creepy.

---

### Post by lnostdal on 2007-03-09
> **phossal said:**
> What? Do you want to meet in the street and have a dance-off? lol 

sure .. if you insist

i would have suggested a less public place though .. but you don't seem to understand this

---

### Post by phossal on 2007-03-09
Do you need a hug?

---

### Post by lnostdal on 2007-03-09
do you need attention?

---

### Post by phossal on 2007-03-09
> **lnostdal said:**
> do you need attention?
Yeah, of course! I also need software that doesn't suck, and isn't ten versions out of date, like I'd get if I used the package managers for everything. I also need a resident expert in the forums who can solve the simple problems I have with my c programs who doesn't behave like a child in response to a simple challenge. I thought you could solve at least *one* of those problems, but you're proving me wrong. You're so bent on harassing me that you overlook an easy fix, and write 50 posts threatening me. What's wrong with you today?

---

### Post by lnostdal on 2007-03-09
do you have a problem with me recommending that people use the repositories in most cases? .. let me quote:

[quote=lnostdal]
note that you should in most cases not install software from source .. you should use the ubuntu-repositories to find software 
[/quote]

..or do you find this to be a false statement? yes or no

---

### Post by Wybiral on 2007-03-09
lmao... This thread is weird...

C's main function should always return an integer because it's meant to be the exit status of the program.

---

### Post by hod139 on 2007-03-09
> **Wybiral said:**
> lmao... This thread is weird...

C's main function should always return an integer because it's meant to be the exit status of the program.
This has been an interesting thread.  I agree that C's main function should always return an int; but according to the standard it doesn't have too.  At least with C++ and standards compliant compilers main must return an int.

---

### Post by phossal on 2007-03-09
> **hod139 said:**
> This has been an interesting thread.  I agree that C's main function should always return an int; but according to the standard it doesn't have too.  At least with C++ and standards compliant compilers main must return an int.

I don't know this kind of stuff, but I have a couple questions: 1) By standard, do you mean ANSI standard? 2) Is it true that gcc is *not* an ANSI-standard compiler?

---

### Post by hod139 on 2007-03-09
1) I mean the ISO C standard: [http://www.open-std.org/JTC1/SC22/WG14/](http://www.open-std.org/JTC1/SC22/WG14/)
There is also a C++ standard ([http://www.open-std.org/JTC1/SC22/WG21/](http://www.open-std.org/JTC1/SC22/WG21/))

2) Too my knowledge no compiler is 100% compliant with the standards, but gcc and g++ are considered to be among the more standards compliant compilers.  I don't know of any obvious C examples, but a common C++ example is the lack of support for the export keyword for templates.


Edit:  I should add, that the lack of compliance between compliers is one of the reasons code doesn't always build between compilers.  The code may be perfectly legal according to the standard, but a compiler may not support it.  Or worse, the code may not be correct but one complier may accept it.

Edit 2:  I actually have a pdf of the C++ standard that I can email you if you want.  I don't think it is freely available.

---

### Post by Wybiral on 2007-03-09
> **hod139 said:**
> Edit 2:  I actually have a pdf of the C++ standard that I can email you if you want.  I don't think it is freely available.

I'm actually interested in that if you have time: [email]Wybiral@aol.com[/email]

---

### Post by hod139 on 2007-03-09
> **Wybiral said:**
> I'm actually interested in that if you have time: [EMAIL="Wybiral@aol.com"]Wybiral@aol.com[/EMAIL]

Sent, but it really is a long and boring document.

---

### Post by phossal on 2007-03-09
me too, [email]mail@phossal.com[/email]

---

### Post by hod139 on 2007-03-09
Sent, but it really is boring!!  The committee is actually preparing a new draft, so the version I sent will be obsolete soon.

---

### Post by Wybiral on 2007-03-09
> **hod139 said:**
> Sent, but it really is boring!!  The committee is actually preparing a new draft, so the version I sent will be obsolete soon.

Thanks, this should come in handy.

I wonder why they don't make these more widely available.
Wouldn't that help to standardize things?

---

### Post by phossal on 2007-03-09
Thank you.

---

### Post by hod139 on 2007-03-09
The only people who really need to read this are the compiler writers.  I don't even know why I have that copy.  It was from when I took a course on Generic Software Design and the professor is on the C++ standards committee.  He was all about "concepts", which will probably make the next standard.

Edit:  Talk about hijacking a thread!!!

---

### Post by lnostdal on 2007-03-10
the drafts are freely available and usually good enough btw.:

[list]
[*]C: [http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1124.pdf](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n1124.pdf)
[*]C++: [http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2005/n1905.pdf](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2005/n1905.pdf)
[/list]

---

### Post by phossal on 2007-03-13
I had never considered doing so previously, but you can buy the most recently published catalog of ANSI/ISO standards for less than I paid for Stroustrups windy "The C++ Programming Language". They were revised/updated 3/07. [http://webstore.ansi.org/ansidocstore/default.asp](http://webstore.ansi.org/ansidocstore/default.asp)

---

### Post by reformedgeek on 2007-03-14
wow, who'd have thought my simple newbie question would start a flame war...

Was quite fun reading the back-and-forth.

play nice.

---

### Post by lnostdal on 2007-03-14
yeah, the whole thing is weird

here is a list of software installation-methods sorted by preferred method in ascending order:

§1 install software from the distros software-repositories via its package manager front end(s)
§2 install software from .deb-files .. the more ubuntu and ubuntu-version specific the better
§3 install software from source

.. this list shouldn't be controversial in any way at all .. if this really _is_ what phossal disagrees with(#1) he is wrong on _all points_ both in theory and practice(#2)

now in this case, the OP did not provide any context of what software he installed from source so the most sane and helpful thing to do is to suggest that he/she consider a more preferred method or suggest that there _might_ exist a more preferred method as there is quite a significant number of linux-users who (still) think they need to install _everything_ from source

..the concept of a package-manager and software repositories (§1) is totally foreign to them..

 this is a healthy, helpful and valid suggestion .. it is not controversial at all; i am quite certain i have the majority with me on this .. (not that that matter very much to me; but it is worth mentioning since insanity was brought up back here)

_assuming_ that the user should not or cannot use §1 or even §2 is a _totally wrong approach_ when the OP hasn't provided _any_ context that might indicate this .. we just do not know; none of us do until the OP has informed us .. but, that does _not_ mean we should focus on the _less ideal solutions_ down the list first! always look upwards for the most ideal alternative before searching downwards when given more and more grim/specific information and details

how informing of the _fact_ that using the distros package manager and software repositories _is_ the most sane thing to do in almost _all cases_ (until OP has stated his context) can create a flamewar is totally beyond me .. pretty shocking, and i had a good laugh - even though it was a bit disturbing/annoying


<snip>

#2: what this means is that even if method §1 doesn't exist for some given software (but again; no context was given in this case) in practice the OP should follow the list from §1 to §3 in ascending order when searching for a way to install some software

---

### Post by phossal on 2007-03-14
> **lnostdal said:**
> yeah, the whole thing is weird

here is a list of software installation-methods sorted by preferred method in ascending order:

§1 install software from the distros software-repositories via its package manager front end(s)
§2 install software from .deb-files .. the more ubuntu and ubuntu-version specific the better
§3 install software from source

.. this list shouldn't be controversial in any way at all .. if this really _is_ what phossal disagrees with(#1) he is wrong on _all points_ both in theory and practice(#2)


Preferred? By whom? The way you babble is weird.

It doesn't need to be an argument, it's a simple matter of finding out what is important to the user, and doing your best to accommodate him or her. I much prefer capitalizing on the updates from SUN as soon as they're released. I had Java 6 while there were still plenty of threads filled with discussions of when it would be available. I don't *want* to disagree with you - but you have to make an argument that provides a solution (or is convincing). Why can't you do that?

A good, knowledgeable teacher doesn't cram his opinion down a student's throat. A valid point/argument/method is *convincing* to a reasonable person. 

I don't get you.

---

### Post by ComplexNumber on 2007-03-14
[B]lnostdal
[/B]yes, lets not go there. i've edited your post.

---

### Post by Ragazzo on 2007-03-14
Why do you always have to fight? :roll: 

> **hod139 said:**
> This has been an interesting thread.  I agree that C's main function should always return an int; but according to the standard it doesn't have too.  At least with C++ and standards compliant compilers main must return an int.

According to c-faq.com **void main()** is not portable. Or is the FAQ too old?

[http://c-faq.com/decl/main.html](http://c-faq.com/decl/main.html)
[http://c-faq.com/ansi/voidmain.pjp.html](http://c-faq.com/ansi/voidmain.pjp.html)

---

### Post by hod139 on 2007-03-14
It's not portable because many programs expect an exit signal.  However, it is legal.  I don't want to sound like I'm advocating main return void, I'm not.  It was just a mistake the early standards committee made and we have to accept it.  It is very good practice to always have main return an int.

---

### Post by phossal on 2007-03-15
> **ComplexNumber said:**
> <snip>

Apropos!  :D Nicely done!

I do wish we could all remain friendly. I apologize to Inostdal; I don't have anything to prove.

---

### Post by lnostdal on 2007-03-15
ok, i apologize also .. i was stressed out (i believe there was a pike in activity/questions at the forum at the time + other things at my side) while trying to intensely focus on the OPs problem exclusively when i "attacked" you for bringing focus on (what i viewed as) a somewhat external or unrelated topic/discussion

..it should not have bothered me the way it did..

---

