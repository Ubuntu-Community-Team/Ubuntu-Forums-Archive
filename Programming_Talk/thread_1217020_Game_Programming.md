---
title: "Game Programming"
date: 2009-07-19
forum: Programming Talk
---

### Post by sam191 on 2009-07-19
Hey guys, 

I was wondering what language is best suited for game programming. I know C++ comes to mind, but it seems like a lot of people dislike C++ here, and I wanted to hear some opinions. 

I know a great deal of libraries and engines are written for C++ and it is the most used language on the game dev scene. 

I will eventually want to create 3D games, and write game engines (for the educational experience... of course :D) Thus the need for a fast compiled language comes into play. 

So I would like to know what you guys recommend. I know this might not be the best forums, but I love this place! You guys are always so helpful. 

Thanks in advance

---

### Post by c0mput3r_n3rD on 2009-07-19
C++ is very prominent in game programming, I love the language, and would definitely recommend it. :D
-That's just me though...

** Just so you know, it will take a lot of learning to to get to where you want to go, so get ready for it. **

---

### Post by AtaiCirno on 2009-07-19
I second C++.  Most code examples, tutorials, and documentation for opengl, sdl, nvidia, ati, etc, are in C/C++.  

Others languages, like C# are not as portable.  Java is portable, but 3D is more difficult to get working cross-platform, in my experience.  Lua is good, but as a scripting engine for a game written in C++.  

SDL/OpenGL/C++ is excellent for starting with 3D game programming. I would recommend a lot of calculus and physics for 3D programming.  Study hard :)

---

### Post by sam191 on 2009-07-19
Thanks for your input!

I am not scared to learn a tough language. A lot of people seem to dismiss a language because it is too difficult, but if it's the best tool for the job then I don't see why not. 

I have the book, "C++ Primer Plus" by Stephen Prata.

Is this book any good? Or should I go out and get "Accelerated C++", or "C++ Primer"? Which book would you recommend?

---

### Post by sam191 on 2009-07-19
> **AtaiCirno said:**
> I second C++.  Most code examples, tutorials, and documentation for opengl, sdl, nvidia, ati, etc, are in C/C++.  

Others languages, like C# are not as portable.  Java is portable, but 3D is more difficult to get working cross-platform, in my experience.  Lua is good, but as a scripting engine for a game written in C++.  

SDL/OpenGL/C++ is excellent for starting with 3D game programming. I would recommend a lot of calculus and physics for 3D programming.  Study hard :)

If there is one thing I like, it's math! And believe it or not, I am dying to put the matrix/vector math to use lol. 

And that's what I was thinking too. Pretty much everything is in C++, and I might use Python for scripting later on. 

I appreciate your help

---

### Post by Kazade on 2009-07-19
I second the SDL/OpenGL/C++ combination. It's really very powerful. The tutorials [here]("http://anomtech.uuuq.com/Tutorials.php") use SDL and OpenGL. Also keep an eye on [NeHe]("http://nehe.gamedev.net") as we are working on new tutorials there. 

If you need a simple math library, myself and the other NeHe maintainer have written one called [Kazmath]("https://code.launchpad.net/~kazmath-developers/kazmath/trunk") which is written in C so it integrates nicely with OpenGL.

If I had any quick tips to learning C++, they would be:

[LIST]
[*]Use std::string (or std::wstring) for strings, never char* 
[*]Learn about smart pointers (std::tr1::shared_ptr or boost::shared_ptr)
[*]Prefer std::vector as your array container (e.g. don't create arrays with the "new" keyword)
[/LIST]

Good luck!

---

### Post by linuxguymarshall on 2009-07-19
> **Kazade said:**
> I second the SDL/OpenGL/C++ combination.

I third it.

---

### Post by Sockerdrickan on 2009-07-19
> **sam191 said:**
> Hey guys, 

I was wondering what language is best suited for game programming. I know C++ comes to mind, but it seems like a lot of people dislike C++ here, and I wanted to hear some opinions. 

I know a great deal of libraries and engines are written for C++ and it is the most used language on the game dev scene. 

I will eventually want to create 3D games, and write game engines (for the educational experience... of course :D) Thus the need for a fast compiled language comes into play. 

So I would like to know what you guys recommend. I know this might not be the best forums, but I love this place! You guys are always so helpful. 

Thanks in advance
You should definitely look into C++0x / OpenGL 3.1 no matter what those script kiddies said.

---

### Post by Yacoby on 2009-07-19
It depends. C++ is the language that is used most commonly.I wouldn't say that means it is the best suited for the task, but it does have the most low level game related libraries.
If I started a game engine, I would be very tempted to pick D, but that is because of my love/hate relationship with C++ and dislike of dynamically typed languages.

There is no reason to dismiss other languages out of hand. I know of several commercial games written in C#, and picking a higher level language will allow you to get the game written faster. A slower written game is better than a faster unfinished game

It is also worth pointing out that just because language X can be faster, doesn't mean it is. You can make stupid mistakes that make the result slower than it would be in a language that stops you making those mistakes. There is no reason why you can't write the performance critical sections of a engine in C, and the rest in something like Python.

---

### Post by CptPicard on 2009-07-19
In this particular case there are certainly good technical reasons for using C++ -- both low-level access and native compilation plus object-abstraction. Although I am not completely certain why one would not just approach the engine-authoring parts in C... I would consider it.

> **Tux0r said:**
> You should definitely look into C++0x / OpenGL 3.1 no matter what those script kiddies said.

... but hey, this is a description I must take issue with. ;) I have philosophical objections to C++ especially as it comes to teaching beginners the important concepts and mindset of programming, and when it comes personally to language level things I "bother" messing with while coding, but I can't recognize a script kiddy in me ;)

---

### Post by C++buntu on 2009-07-19
This book is REALLY good! Do all the end-of-chapter problems and you are on your way! (I'm in chapter 12 right now).

Good reading!

---

### Post by soltanis on 2009-07-19
As a natural contrarian/hater on C++, I would suggest either using C (that's pure C, C99) or using D, if you really need the object-orientation (unfortunately, learning D is very difficult not through any fault of the language, but rather lack of resources).

Both languages are close to the metal and D interoperates well with C libraries -- so SDL, OpenGL, GLU/GLUT and the other fun low-level games libraries are open for use.

If you want to start out slow and easy though, I'm really shocked no one has suggested it yet, python has 3D extensions and isn't that terrible.

---

### Post by Sockerdrickan on 2009-07-19
> **soltanis said:**
> As a natural contrarian/hater on C++, I would suggest either using C (that's pure C, C99) or using D, if you really need the object-orientation (unfortunately, learning D is very difficult not through any fault of the language, but rather lack of resources).
C for games is just wrong when you have C++ available.

---

### Post by Can+~ on 2009-07-19
> **soltanis said:**
> If you want to start out slow and easy though, I'm really shocked no one has suggested it yet, python has 3D extensions and isn't that terrible.

Speaking of which, I just started with Soya3d. Despite the dumb name, it's pretty good. ([basic-1.py]("http://home.gna.org/oomadness/en/soya3d/tutorials/basic_1/index.html"))

It's object oriented, and offers cameras, light, blender importing, etc.

---

### Post by sam191 on 2009-07-19
Thanks for all the replies,

I am going to stick with C++ as the language of choice. I am considering writing my development tools, such as the level editor, in Python at the moment (seems like the logical thing to do) and maybe even use it as the scripting language.

I now just need a book and IDE recommendation. A lot of people like VS 2008, but I find codeblocks to be much cleaner and uncluttered. And I feel like VS forces windows programming on you, and I want my games to be cross platform (so all of you guys can try it out!) 

As for the book, I am liking "Beginning C++ Through Game Programming" by Michael Dawson. I used his other book to learn Python before and liked it. But unlike the Python world, the C++ world has A LOT of books out there. 

Thanks again for all the great feedback!

---

### Post by JordyD on 2009-07-19
> **sam191 said:**
> Thanks for all the replies,

I am going to stick with C++ as the language of choice. I am considering writing my development tools, such as the level editor, in Python at the moment (seems like the logical thing to do) and maybe even use it as the scripting language.

I now just need a book and IDE recommendation. A lot of people like VS 2008, but I find codeblocks to be much cleaner and uncluttered. And I feel like VS forces windows programming on you, and I want my games to be cross platform (so all of you guys can try it out!) 

As for the book, I am liking "Beginning C++ Through Game Programming" by Michael Dawson. I used his other book to learn Python before and liked it. But unlike the Python world, the C++ world has A LOT of books out there. 

Thanks again for all the great feedback!

VIM!!!

Err, sorry. I guess you actually want an IDE? I'd use Code::Blocks, when I used IDEs, that got in the way the least, and provided lots of neat auto-completion and stuff. I still use vim, because I can't live without ggVG=, and I get a lot of ':w' in my code.

---

### Post by sam191 on 2009-07-19
Haha, I haven't tried VIM yet, but I have tried emacs and didn't really put in an effort to set it up. Didn't really like it. 

I just installed Code::Blocks and SDL on my Linux partition, I am really happy that I can code on Ubuntu as opposed to Windows. I feel like it's much more stable, on Windows I feel like I'm on thin ice.. lol.

So I'm using Code::Blocks and the GCC compiler, I have my IDE down.

Who can tell me a good beginner C++ book? (Note, it is not my first language. And I care more about the quality and correctness of the information more than the 'ease' or 'friendliness' of the book).

---

### Post by .Maleficus. on 2009-07-19
If you have access to Windows and VS2008, that's what I would use.  I use it for C# and used VS2005 for VB.NET when I was at school and it's honestly one of the best IDEs I've used.  If you use C++ right, there's no reason that something made with Visual Studio can't be cross platform.  If you don't want VS, my next choice would probably be Netbeans.  IMO, it's less cluttered than Eclipse and has tons of great plugins and built-in features.  You can add Python on to it as well.

---

### Post by JordyD on 2009-07-19
> **.Maleficus. said:**
> If you have access to Windows and VS2008, that's what I would use.  I use it for C# and used VS2005 for VB.NET when I was at school and it's honestly one of the best IDEs I've used.  If you use C++ right, there's no reason that something made with Visual Studio can't be cross platform.  If you don't want VS, my next choice would probably be Netbeans.  IMO, it's less cluttered than Eclipse and has tons of great plugins and built-in features.  You can add Python on to it as well.

Netbeans and Eclipse are slow IMO, Code::Blocks is *very* fast. I wouldn't know about VS; I don't have a Windows box.

---

### Post by c0mput3r_n3rD on 2009-07-19
> **sam191 said:**
> Thanks for your input!

I am not scared to learn a tough language. A lot of people seem to dismiss a language because it is too difficult, but if it's the best tool for the job then I don't see why not. 

I have the book, "C++ Primer Plus" by Stephen Prata.

Is this book any good? Or should I go out and get "Accelerated C++", or "C++ Primer"? Which book would you recommend?

I have the book C Primer Plus and it is a great learning tool.  You'll do fine :)
EDIT: I learned my first language (C) from that book.  By Stephen Prata right?

---

### Post by sam191 on 2009-07-19
Thanks for all the advice.

I've decided on a book and IDE, but I have two questions. 

I am on Ubuntu, and I'm working with two other people. One is on Ubuntu and the other is on Vista. We all have Code::Blocks with the GCC compiler. Will we have problems sharing code and working together? 

Also, are there any limitations to the IDE as far as what you can make? Or is the IDE just a place to organize code, and has no effect on what can be created? (Might be kind of a dumb question, sorry)

Edit: I am also wondering what the limitations are on Linux, since you are using hardware acceleration and have to talk to the graphics cards. (Issues as far as driver support goes).

---

### Post by Oler1s on 2009-07-20
> Will we have problems sharing code and working together? Generally, one issue that tends to come up on text file (e.g. code) created on one OS and viewed on the other is that of line endings. Modern text editors and IDEs are smart about this issue. I can't recall how Code Blocks deals with it -- it should handle it properly and intelligently. You can do a quick test by writing a small code snippet on one OS (in Code Blocks), transferring that file over to the person on the other OS, and check if he can view the file properly. Shouldn't be any problems. And that's really about it.

> Also, are there any limitations to the IDE as far as what you can make? Or is the IDE just a place to organize code, and has no effect on what can be created? (Might be kind of a dumb question, sorry)No limitations. The IDE is just a tool that ties together several existing tools (compiler, editor, debugger, etc.) so you're limited by the underlying tools and what you yourself can do with them.

I think you're anticipating all the wrong issues (which is OK), so my real advice here is to stop worrying...

---

### Post by sam191 on 2009-07-20
> **Oler1s said:**
> 
I think you're anticipating all the wrong issues (which is OK), so my real advice here is to stop worrying...

Haha, I guess I am. What I'm worried about is getting in too far only to find out that something simple doesn't work. 

But I understand now. Less reading, more doing :D

Thanks

---

### Post by nvteighen on 2009-07-20
Hm... I see issues with C++ is when you learn it as your first language (the reasons of this have been discussed a lot and, of course, there are people that disagree with me and do have good reasons... Search the forums; I'm tired :p). 

But, if you already know programming, learning C++ is IMO perfect, even though I hate that language (but that's **me**). And C++ is well-suited for game programming, so you wouldn't be using a wrong tool either...

---

### Post by Sockerdrickan on 2009-07-20
The statement above is true.

---

### Post by JordyD on 2009-07-20
The statement below is false.

---

### Post by Can+~ on 2009-07-20
The statement above is true.

(@JordyD: Edit your post)

---

### Post by ZuLuuuuuu on 2009-07-20
> **sam191 said:**
> What I'm worried about is getting in too far only to find out that something simple doesn't work.

As I read from your posts, the tools you selected (C++, gcc, Code::Blocks etc.) are all powerful enough to code your own Half-Life 2 or Doom 3 (both written using C++ and C together), so don't worry :) The rest looks into your determination, patience and talent.

---

### Post by nvteighen on 2009-07-20
> **ZuLuuuuuu said:**
> As I read from your posts, the tools you selected (C++, gcc, Code::Blocks etc.) are all powerful enough to code your own Half-Life 2 or Doom 3 (both written using C++ and C together), so don't worry :) The rest looks into your determination, patience and talent.
And resources (money...) :)

---

### Post by sam191 on 2009-07-20
> **nvteighen said:**
> 
But, if you already know programming, learning C++ is IMO perfect, even though I hate that language (but that's **me**). And C++ is well-suited for game programming, so you wouldn't be using a wrong tool either...

> **ZuLuuuuuu said:**
> As I read from your posts, the tools you selected (C++, gcc, Code::Blocks etc.) are all powerful enough to code your own Half-Life 2 or Doom 3 (both written using C++ and C together), so don't worry :) The rest looks into your determination, patience and talent.

Thanks for helping me out! This is exactly what I wanted to know. 

Now time for the hardest part, actually starting lol. Seriously though, enough with the jokes. Wish me luck.

And thanks again to everyone who helped me out, I really appreciate it.

---

