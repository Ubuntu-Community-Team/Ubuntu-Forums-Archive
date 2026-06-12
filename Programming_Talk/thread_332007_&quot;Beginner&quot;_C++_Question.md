---
title: "&quot;Beginner&quot; C++ Question"
date: 2007-01-05
forum: Programming Talk
---

### Post by raevin on 2007-01-05
Here's the thing...

I've been programming in C++ on Windows for a few years (at least 5), and am confused on where to start on Linux.

I know there's differences between programming for Windows and Linux, and that's what's really confusing me on where to start.

I know you're probably saying "we can't help if we don't know how far you got on Windows...".  Well...I've dipped in everything from console apps (RPG's and various network tools [mainly like ipconfig]), games (which I do very badly at), and GUI apps (again, mainly like ipconfig, but I've also done file transfer programs, port scanners, etc...).

**edit::**
My question is basically, should I start from the beginning again ("Hello World!" -> simple game -> whatever else), or should I basically port the programs I've already made so they work on Linux flawlessly?

---

### Post by meng on 2007-01-05
Would you mind rephrasing the question? I'm not sure what your question IS.

---

### Post by raevin on 2007-01-05
> **meng said:**
> Would you mind rephrasing the question? I'm not sure what your question IS.

Sure.

My question is basically, should I start from the beginning again ("Hello World!" -> simple game -> whatever else), or should I basically port the programs I've already made so they work on Linux flawlessly?

---

### Post by Verminox on 2007-01-05
If by "console apps" you mean simply using standard input/output, the code should work in linux also, only you will have to compile it separately on linux using a linux compiler... the source will work.

"Games" in SDL or such (perhaps using OpenGL) will work on linux if you have the required libraries (not just download a dll for SDL like you did in Windows).

So basically your source code won't differ much for platform-independent code, just the compiler used and the libraries to be distributed with the executables. (Exceptions are if you have used some compiler other than GCC like the MSVC one containing Windows-specific commands).


Some things that may be windows specific:

If you have any programs using the Windows GUI,... you will need their SDK to compile it (which probably wont work with GCC... I'm not sure), and It won't run on a linux desktop either. Best option is to separate the GUI from working in your program, and replace it with something that will work in Linux. Take a look at GTK+ (What GNOME uses) or Qt (What KDE uses) as toolkits for developing GUI. 

DirectX stuff also doesn't work on Linux natively.



To answer your question dierctly: I would suggest you try porting your program to Linux, because that way each time you encounter problems you will realise what exactly is the difference between Windows and Linux programming.... don't learn Linux programming as if it is a whole new language.

---

### Post by raevin on 2007-01-05
> **Verminox said:**
> 
[...]
Some things that may be windows specific:

If you have any programs using the Windows GUI,... you will need their SDK to compile it (which probably wont work with GCC... I'm not sure), and It won't run on a linux desktop either. Best option is to separate the GUI from working in your program, and replace it with something that will work in Linux. Take a look at GTK+ (What GNOME uses) or Qt (What KDE uses) as toolkits for developing GUI. 

DirectX stuff also doesn't work on Linux natively.



To answer your question dierctly: I would suggest you try porting your program to Linux, because that way each time you encounter problems you will realise what exactly is the difference between Windows and Linux programming.... don't learn Linux programming as if it is a whole new language.

Well, I was thinking for a while I'd just use the console for the projects, so I wouldn't have to mess with the GUI problems (since I was using MFC/Microsoft Foundation Classes for the GUI, and obviously I'd have to rewrite all the GUI code to work for Linux).

Alright, thank you for answering my question :)  I'll take your approach and see what happens :)

---

### Post by pmasiar on 2007-01-05
> **raevin said:**
> I've been programming in C++ on Windows for a few years (at least 5), and am confused on where to start on Linux.

should I start from the beginning again ("Hello World!" -> simple game -> whatever else), or should I basically port the programs I've already made so they work on Linux flawlessly?

Question is, do you want also to try new areas/new languages?

You are reasonably experienced programmer, so you can pick new language quickly. You may want to look at bash (the shell). Adding a scripting language and/or web application development skills might be more interesting than just redo your old apps (unless you are very attached to them). Another idea might be to redo your old apps in new language.

---

### Post by raevin on 2007-01-05
> **pmasiar said:**
> Question is, do you want also to try new areas/new languages?

You are reasonably experienced programmer, so you can pick new language quickly. You may want to look at bash (the shell). Adding a scripting language and/or web application development skills might be more interesting than just redo your old apps (unless you are very attached to them). Another idea might be to redo your old apps in new language.

Well, I've done some bash scripting, to make managing my server easier (simple restart/start/stop), and I've done a lot of PHP/MySQL & ASP/MSSQL work for the joy of it...getting the point of porting some of my C++ programs to PHP.

Probably the biggest reason for me wanting to redo my old programs is because when I did them on Windows, I used different libraries and such than what Linux offers; the Linux libraries also offer a lot more...ability?...to do more, such as ARP work...which, was a pain for me to really do efficiently on Windows.

As for new languages...I can't really think of any languages...I know a lot of people go ape-crazy over ones like Python and Perl, but Perl would seem like the only viable option...which, I've also messed with in the past, and didn't completely like how you had to do certain things (variables, arrays, etc...).

Although, I might give Perl another shot...that was a few years ago that I last did anything with it (v5.0), so it might be different for me now...

Thanks!

---

### Post by pmasiar on 2007-01-05
> **raevin said:**
> As for new languages...I can't really think of any languages...I know a lot of people go ape-crazy over ones like Python and Perl, but Perl would seem like the only viable option.!

Perl is IMHO in [some|big] trouble: perl 6 seems going nowhere, and big part of perl web developers left for greener pastures in ruby/python. Dynamic languages **do** increase your productivity. You might dislike disorderly look/feel of python after C. Python code looks **much** cleaner than perl/php and is as dynamic. Ruby is another hot newcomer in web app area - and web apps is hot on Linux. People may disagree (and they will :twisted:  for sure) but IMHO perl is in final decline. Perl will stay for 10 more years, sure, but IMHO Perl has **no competitive advantages** compared to other popular dynamic languages (only vast CPAN library).

Another hot skill to have is AJAX - dynamic HTML with javascript on client, python/ruby/whatever on server. So called web 2.0 :D

If you want to challenge yourself, try radically different language, like Lisp, Prolog if you are into AI, or Forth if you like be closer to hardware. Forth will blow your mind - I know it did mine (years ago). 

Quite a bit off original question, isn't it? :-)

---

### Post by Wybiral on 2007-01-06
I too made the transition from C++ programming with windows, then took a leap over to linux. Honestly, it's not that much different... A lot of the console programs I wrote compiled as-is and I used to use glut/SDL with openGL in windows... Those programs also compiled as-is. If you plan to use graphics, 2d or 3d, SDL is the way to go.

BTW, pmasiar is right, python is a nice language. Probably the biggest edge learning python will give you is to be able to embed python into your C++ programs, this comes with tons of perks such as userscriptability (let the users add on to your programs using python with plugins and such) and manageability, you can put large portions of your program in the python script, that way you don't have to recompile the C++ portion every time you need to change something... Fixing bugs and upgrading becomes a much less hairy process this way!

---

### Post by slavik on 2007-01-07
yeap, port all of your windows specific code, don't bother with hello world examples, port that ipconfig thing over ... and learn from there :)

---

