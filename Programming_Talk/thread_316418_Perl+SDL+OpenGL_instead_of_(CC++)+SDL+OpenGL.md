---
title: "Perl+SDL+OpenGL instead of (C/C++)+SDL+OpenGL"
date: 2006-12-10
forum: Programming Talk
---

### Post by slavik on 2006-12-10
I was thinking of switching away from C/C++ when doing my graphics stuff with SDL and OpenGL to Perl. From what I read so far, SDL and OpenGL have bindings (modules) for Perl and it all should be just as fast because both are already precompiled.

My only 'scared of' things are the minute syntax changes (some functions work differenty) and also, there is no GUI that I am aware of that would handle a multi perl script project (does Anjuta do it?).

What do you think?

---

### Post by Mickeysofine1972 on 2006-12-10
Not really sure but you might be interested to know that the Ubuntu Games Developer Resource Wiki is publishing a C++ to Python interface so you can use python functions and C++ stuff in python.

the code for the first half has been made and we're just generating the python to c++ stuff so you might consider learning python instead

This will make Python and C/C++ inter operable for SDL! 

Mike

---

### Post by Choad on 2006-12-10
"just as fast"

not really. perl will never be as fast as c++/c

however sdl is written and compiled in c, the perl bindings just call the c methods. so blitting a surface in perl will have roughly the same cpu cost as blitting a surface in c++, allowing for the overhead of the interpreted function call (minimal)

---

### Post by Snargle on 2006-12-10
As far as I know, there aren't any existing perl-opengl games. The only Perl-SDL game that I know about is Frozen Bubble (not counting the one I'm just starting!).

the SDL-Perl cpan thing has a few basic test scripts you can use:
[http://search.cpan.org/src/DGOEHRIG/SDL_Perl-2.1.3/test/OpenGL/]("http://search.cpan.org/src/DGOEHRIG/SDL_Perl-2.1.3/test/OpenGL/")

---

### Post by Wybiral on 2006-12-10
As far as the python/c++ interface goes, it's always been possible using python.h or Boost, but the one we are working on has a much more natural interface and should be easy to incorporate into your projects. You can use it to easily interface between C++ and python, (C++ can call a python function and collect its return, and python can call a C++ function and collect its return). Like I said, Its always been possible, we are just making it easy.

---

### Post by slavik on 2006-12-10
Perl not being as fast ... how much faster is C/C++ code than Perl code when it comes to calling functions and doing comparisons? What about mathematical operations?

Learn Python? I already know Perl ...

---

### Post by Choad on 2006-12-10
> **slavik said:**
> Perl not being as fast ... how much faster is C/C++ code than Perl code when it comes to calling functions and doing comparisons? What about mathematical operations?

Learn Python? I already know Perl ...
not sure. basically.... if you wanted to do complex 3d physics modeling in your game, you would be shooting yourself in the foot to do it in an interpreted language.

high level game scripting and ai is pretty well suited to an interpreted language tho

it really depends what you want to make. modern cpu's will take up alot of the slack so it affords you some room to use interpreted languages

---

### Post by Wybiral on 2006-12-10
We could test it, someone could make a really CPU intensive OpenGL program exactly the same in each language and see which one runs faster (my vote is on the C++)

---

### Post by slavik on 2006-12-10
no offense, but perl (and I would assume python, ruby, php, etc.) are all as interpreted as java is.

Larry Wall in his Perl Programming book says that before perl code is actually run, it gets compiled into pcode (so does java, sun calls it 'java byte code' but the idea of a VM goes back to P-System: [http://en.wikipedia.org/wiki/UCSD_p-System](http://en.wikipedia.org/wiki/UCSD_p-System) from 1978 ).

java is compiled on the developer side, while perl is compiled on the user side.

Although to be fair, my 1000! perl script runs on my laptop in about 5 seconds while the C equivalent is 0.5 seconds, but in C I preallocate the array to use while in perl it is done dynamically.

---

### Post by Wybiral on 2006-12-10
C++ compilers also do a lot of optimizing in most cases and can really improve the performance of your code. Naturally, this is no excuse not to optimize your code on your own, but a lot of C++ compilers have very effective ways of doing it. Plus, C++ compiles to machine code where it can almost directly be executed by the hardware, unfortunately interpreted languages just aren't able to achieve the level of speed that compiled ones are (in MOST cases, certainly there are exceptions).

I've done some test's with python and c++ code basically running the exact same program translated between them and the c++ code did in-fact have a higher fps. Some of my test's returned nearly identical frame-rates, but then I also considered that I was using the pyOpenGL binding, and I believe that was written in C, so I was basically interfacing a C program... So, would it be faster to write something directly, or interface it? Directly is probably the most logical choice.

So, what I'm saying is... For programs that aren't using a lot of modules and aren't interfacing external programs, interpreted languages probably are equal. But, for programs that are sending a value to a function, that then wraps it into the real C++ function (in such cases as OpenGL and SDL modules) I would highly doubt that the program would be as fast as the C++ version.

Note: In a lot of cases the wrapping function for external modules will be compiled to essentially call the function that it's wrapping it to... This does effectively cut out the middle man function in the wrapper... But this alone is just another example of C++'s compilers doing what they are good at... optimizing.

I vote compiled C++ over interpreted languages.

---

### Post by slavik on 2006-12-11
perl is written in C ... are you saying that Perl cannot be as optimised as C?

Perl:
for ($i=0; $i<100; $i++) { print $i."\n"; }

C++:
for (int i=0; i<100; i++) { std::cout<<i<<"\n"; }

What it will get optimised to (if you choose speed over size):
std::cout<<"0\n";
std::cout<<"1\n";
std::cout<<"2\n";
...

Notice that in both cases you can predict what i is and what you will print.

Could you provide the code you used to test and your results?

---

### Post by Snargle on 2006-12-11
They are both about the same in terms of running speed, since printing to the console would be the bottleneck.

I don't see any need to argue about specific languages. I bet know how much faster it is to get a perl program working than a c/c++ program. If you have any bottleneck algorithms, you can just optimize it later with Inline C or something.

The function SDL::Surface->pixels returns a char pointer to your surface, for c/c++ drawing purposes.

About your IDE question, If you use perl, there's no need to continually skip  to header files when a function needs updated, and perl code is so dense that you won't need many files. For example, Frozen Bubble has just like 3 extra files, including the level editor.

I just use gedit, or sometimes scite.

---

### Post by bfree on 2007-03-16
Although I started off as a C/C++ developer - over the years Perl has become my language of choice:

* When used in an online service (mod_perl/ISAPI), Perl performance approaches that of C/C++, and is usually twice as fast as Java.

* Perl's string handling compliments OpenGL's strength in number crunching.

* It's much easier to port C/C++/Java code to/from Perl than Python/Ruby.

I recently released a new Perl OpenGL (POGL) module: 0.55 - it adds support for 52 new OpenGL extensions.  It's been tested on Windows (NT/XP/Vista) and Linux (Fedora/Ubuntu).

You can find it at graphcomp.com/opengl

BTW - I performed some benchmark tests between Vista, Fedora and Ubuntu - same machine, same nVidia card, same code - and Fedora was 10x as fast as Vista... and and Ubuntu was 15x as fast.

Given that I was using the same nVidia drivers on Fedora and Ubuntu, I was expecting similar results.  Ubuntu is doing _something_ right - Bob Free

---

### Post by pmasiar on 2007-03-16
> **slavik said:**
> I was thinking of switching away from C/C++ when doing my graphics stuff with SDL and OpenGL to Perl. (...) there is no GUI that I am aware of that 

IMHO Python is better choice because is more future-proof than Perl. Perl 6 is being born for a long time and no results, no timeframe for final delivery: [http://en.wikipedia.org/wiki/Perl_6](http://en.wikipedia.org/wiki/Perl_6) Compared to Perl, Python is alive and kicking, sponsored by new rich companies like Google, and gaining marketshare. But Python is still simmilar enough to Perl (dynamic typing) but Python syntax is less quirky and closer to C (no @$% signarures and other "features").

Some people advise against using dynamically typed languages, claiming speed difference. Better idea than "premature optimization" by using compiled language for non-sritical code is IMHO finding where bottleneck (of correcly functioning valid program with stable API) is, and reimplemented those bottleneck features in C as your custom library. Do not guess - measure.

Ubuntu and OLPC uses Python exclusively as development language, and they are not completely stupid, are they?

---

### Post by bfree on 2007-03-20
I hope this doesn't start a flame war - not my intent...

An earlier post mentioned that Perl was slow.  I've launched several high-volume media-sharing sites that perform "realtime" image/video/audio processing - all written in Perl.

I've performed benchmarks at each company, comparing C++, Perl and Java.  C++ is always the fastest in terms of performance, with Perl being nearly as fast, and Java being almost universally twice as slow.

It was mentioned earlier that Perl is an interpretted language.  True - but in a server environment, the interpretter/modules/code can be pre-compiled and cached in memory - allowing your code to run "in-processes".  Both ISAPI/ActivePerl (IIS) and mod_perl (Apache) run Perl code in-processes, and cache loaded modules in memory.

Furthermore, many performance-critical perl modules are written in C (as is POGL), and particularly in the case of OpenGL, most of the crunching happens in GPU... so the real issue is not language, but rather GPU speed and drivers.

As for Python/Ruby - I haven't performed benchmarks on them, so I can't speak to their performance.  My guess is that their performance will be similar, if you are using ISAPI or something equivalent to mod_perl.  It's my understanding that fast-cgi is slower than mod_perl, since it uses a separate process.

My main comment is that if you already have a body of work in Perl, performance is not a reason to switch.  If you are already developing in Python/Ruby, great - as long as your OpenGL modules give you what you need.

---

### Post by Wybiral on 2007-03-20
> **bfree said:**
> I hope this doesn't start a flame war - not my intent...

An earlier post mentioned that Perl was slow.  I've launched several high-volume media-sharing sites that perform "realtime" image/video/audio processing - all written in Perl.

I've performed benchmarks at each company, comparing C++, Perl and Java.  C++ is always the fastest in terms of performance, with Perl being nearly as fast, and Java being almost universally twice as slow.

It was mentioned earlier that Perl is an interpretted language.  True - but in a server environment, the interpretter/modules/code can be pre-compiled and cached in memory - allowing your code to run "in-processes".  Both ISAPI/ActivePerl (IIS) and mod_perl (Apache) run Perl code in-processes, and cache loaded modules in memory.

Furthermore, many performance-critical perl modules are written in C (as is POGL), and particularly in the case of OpenGL, most of the crunching happens in GPU... so the real issue is not language, but rather GPU speed and drivers.

As for Python/Ruby - I haven't performed benchmarks on them, so I can't speak to their performance.  My guess is that their performance will be similar, if you are using ISAPI or something equivalent to mod_perl.  It's my understanding that fast-cgi is slower than mod_perl, since it uses a separate process.

My main comment is that if you already have a body of work in Perl, performance is not a reason to switch.  If you are already developing in Python/Ruby, great - as long as your OpenGL modules give you what you need.

I will agree with you 100% that an interpreted language that leans hard enough on compiled modules will be almost as fast as a C program that uses the same library.

But in terms of 3d programming, *some* of the weight is passed to the GPU, but not enough... The performance of detailed 3d games still leans pretty hard on the actual program itself.

For instance, when you render a 3d level comprised of 1,000's of vertices's no GPU out today will simply render all of it at a usable speed by passing the vertices's straight to it. The program itself must use optimization techniques that in-and-of themselves can be pretty CPU intensive. But they pay off more than just passing the whole level to the GPU.

Take the BSP rendering technique, the level is divided into a tree of planes. You traverse the tree by checking the camera position and determining which side of the plane it is on (it's like a binary tree, but instead of "<" and ">" numerically, it goes by which side of the plane the camera is on). Then when it finds the final node, that node contains the indices's of all of the faces that are visible from there.

So you can imagine how much work the program itself has to do in this situation... Lot's of recursion and vector mathematics... Then lots of memory allocating and freeing (because not every node has the same number of faces, so they must be dynamically allocated).

A language like Java is slightly handicapped in this case because of the way it handles dynamic arrays (it actually checks the bounds every time you access one... This makes things much safer, but obviously puts a damper on the speed in a tight loop like this) and obviously the programmer knows when the memory needs allocated and freed, so GC is an overkill in terms of overhead.

I'm not as certain how perl would handle these kinds of operations because I haven't done enough research into how it handles dynamic memory and array access...

But I am certain that 3d games are NOT dependent on the simply GPU speed alone (I've actually seen software rendered 3d games that have a decent framerate). So while some programs may be just fine and capable of simply putting all the weight on the OpenGL library, detailed games will have a VERY hard time doing this.

---

### Post by bfree on 2007-03-20
> **Wybiral said:**
> But in terms of 3d programming, *some* of the weight is passed to the GPU, but not enough... The performance of detailed 3d games still leans pretty hard on the actual program itself.


Fair enough; good examples!

In terms of performance, I was commenting more on switching from Perl to Java/Python/Ruby than to C/C++.

If all your data is coming in binary form (which is generally the case for games) - C/C++ is the way to go.

However, for online services where data (VRML, X3D, Flash, shader scripts, etc) are uploaded/manipulated in text form, or if you are rendering HTML/forms on a 3D surface, string handling is an essential factor.  And while you can certainly use Boost libs for regex handling, Perl is optimized for string handling.

As for BSP traversing, I'd argue that much of that could/should be done as a GPGPU opertation.  Similarly, recursive vector handling could be done with vertex shaders.  GPU Vertext Arrays allows you to manipulate matrix data (in chunks) without hitting the CPU.

That said, any major CPU-bound calcs can/should be done using binary modules.  Perl has a number of matrix/array math modules.

I know it sounds like I'm promoting Perl - which is not my intent. I truly believe in using the right tool for the need at hand.  When I'm developing, I tend to write first in Perl (I've found Perl development to be much faster than C/C++/Java for me), then (if necessary) port to whatever language makes sense for my target platfrom/audience.

> **Wybiral said:**
> A language like Java is slightly handicapped in this case because of the way it handles dynamic arrays


Agreed.  Perl is not typed, and is very good at managing strings/arrays/garbage-collection; not as good at handling numbers/bits.

If you have a good memory pool manager in C/C++ - that's the best way to go.  If not (and you are just alloc/free'g arrays as needed), then Perl (and probably Python/Ruby) will do a better job.  While I like Java as a language, it's the worst option in terms of memory management (depending on your VM).

> **Wybiral said:**
> So while some programs may be just fine and capable of simply putting all the weight on the OpenGL library, detailed games will have a VERY hard time doing this.

I'm not a game developer, so I'll defer to your opinion on this; I'm mainly focused on providing online 2D/3D/Video services, where Perl has served me well.

Good food for thought!

---

### Post by slavik on 2007-03-20
those are sigils and they make you think how you are accessing the variable ...

in C:
int a[10];
'a' by itself is of type int* ... not a pointer to an array and not an array, it a pointer to an integer ...

in Perl:
@a;
here you know that @a refers to the array as a whole, not as something else.

then you get things like:
for (@a) { do something for every value in @a; }

also, those braces are forces in Perl ...

---

### Post by bfree on 2007-03-24
I've just posted an OpenGL C vs Perl benchmark at [http://graphcomp.com/opengl/bench.html](http://graphcomp.com/opengl/bench.html)

In terms of OpenGL, Perl performs comparably to C - and inexplicably performs better than C on Vista.

---

### Post by Wybiral on 2007-03-24
Well... Yeah. Because they are both just calling the compiled library functions. You will only notice the speed difference when the programs begin to compute things and handle memory, not from just calling pre-compiled functions.

How about doing a benchmark of a 1000 or so particles (with velocity+gravity... same conditions for each program).

Or collision detection between multiple object.

That's when you'll start to see the benchmarks separate.

---

### Post by bfree on 2007-03-25
> **Wybiral said:**
> How about doing a benchmark of a 1000 or so particles (with velocity+gravity... same conditions for each program)

You can easily keep 1000 particles in a vertex array (on the GPU), in which case you'd still see no performance difference.

Similarly, if you load up particles via a texture, the performance will be about the same, as Perl's image loaders (ImageMagick, etc) are all binary.

So - if I take the time to do a particle benchmark, will that be enough to convince you - or should I expect to continue receiving hypotheticals of why Perl *must* have inferior performance  ;^)

---

### Post by crc_canada on 2007-03-25
Hi All;

FreeWRL (vrml/x3d viewer) used to use Perl, calling C to call OpenGL.

I have my notes at work of what speedups did what, but, the end result is that Perl is used for configuration for the build environment; all the rest is written in C. 

In my experience, of years of managing a large Perl<->C project, perl just did not cut it.

The last bit was the VRML parser - moving to C dropped parsing times down from 20 MINUTES to seconds for a large file. Sure, maybe the Perl parser could have been rewritten, too, but, I doubt it could have approached what C can do.

Anyway, just my thoughts from my experiences.

John Stewart
CRC Canada.
[http://www.crc.ca/FreeWRL](http://www.crc.ca/FreeWRL)

---

### Post by Wybiral on 2007-03-25
> **bfree said:**
> You can easily keep 1000 particles in a vertex array (on the GPU), in which case you'd still see no performance difference.

Similarly, if you load up particles via a texture, the performance will be about the same, as Perl's image loaders (ImageMagick, etc) are all binary.

So - if I take the time to do a particle benchmark, will that be enough to convince you - or should I expect to continue receiving hypotheticals of why Perl *must* have inferior performance  ;^)

It's not hypothetical... My point is that the speeds will be the same since they are doing the same thing (executing functions in a precompiled library)

The reason I think _active_ particles would be a good benchmark is that they will require you to update their position each frame, along with having to render them. The rendering won't be the issue, the maintaining of velocity and gravity would be.

Even better then that... How about camera motion. This will require some matrix and vector mathematics. Or collision detection and response? Basically anything that isn't just calling a compiled library.

In fact, if you'd like to benchmark either of these... I'd be willing to help write the C code and you can write equivalent perl code?

Also, how about manually rendering the particles with an array and a loop? That would take some of the pressure off of OpenGL and put more on perl and C.

EDIT:

I'm not trying to be argumentative... I'd just like to see how they compare when actually having to do the math and operations required by a real-world 3d program. Another thing to point out is that even if C is only a TINY bit faster in those benchmarks... Think about the accumulative difference for larger programs, such as a 3d game. That tiny bit will snowball into a huge bit.

---

### Post by bfree on 2007-03-26
> **Wybiral said:**
> I'm not trying to be argumentative

Understood.  However, I think you've been missing my point... I'm not trying to compare C and Perl in terms of general purpose computing - C/C++ is clearly superior.  If I'm writing for a particular platform, and I need a binary (for either performance or IP reasons), I'll always go with C (procedural/stateless) or C++ (object/stateful).

My point is that in terms of OpenGL use, and to the extent that you can leverage the GPU, there's really no performance hit to using Perl.  All of the examples you've given can be done within the GPU or with existing binary modules:

* Load data via textures.
* Process large matrices of data via vertex arrays.
* Perform dynamic particle/collision/gravity/camera calcs via vertex shaders.

Modern vertex shaders support full c-like languages with conditionals/branching/etc that run on the GPU itself - using data that's stored/manipulated on the GPU in the form of vertex arrays.

Think of GPGPU vertex shaders as your code execution engine, textures as r/o memory, vertex arrays as r/w memory; rendering to a screen/framebuffer is fast becoming a secondary GPU task.  In terms of GPGPU processing, you're only using the CPU to handle disk i/o, system functions, ipc and user input.

To implement a benchmark as you've describe it, all you need to do is:

1. Load the GPU with your initial particle/object/camera positions via a texture.

2. Load the GPU's vertex shader with your code/algorithms controlling particle/collision/camera positions; let the GPU do all your particle/collision/gravity/camera/animation calcs - it's better suited for processing arrays of data than your CPU.

3. As the vertex shader calculates the new particle/camera positions for each frame, it then uses a different vertex/frament shader to do the actual particle rendering.

The only thing the C/Perl code needed to do was load the data/code and send it to the GPU, plus some Framebuffer management - all the heavy lifting is done by the GPU.

To summarize - if you are letting your GPU do all the crunching, then all that's left is event handling, which can be done just as well in C/C++/Perl -  or even Java/Python/Ruby, once they add support for GPGPU vertex arrays and modern vertex shader programs.

---

### Post by Wybiral on 2007-03-26
So you're benchmarking... What?

You can stop benchmarking if all you're doing to executing precompiled binaries...
I think anyone could tell you that it's going to be similar.

But a real-world application is going to require more then shaders, especially if you want your engine to run on more then a couple of brands of GPU's.

But I see your point... The GPU is useful and shaders are too, but... Why even benchmark them? They are pre-compiled... They will be the same (if not off be a little).

If you're not benchmarking the language difference, why are you using two languages?

---

### Post by bfree on 2007-03-26
> **Wybiral said:**
> So you're benchmarking... What??

My initial benchmark (posted on [http://graphcomp.com/opengl](http://graphcomp.com/opengl)) was intended to benchmark FBO operations using my new Perl OpenGL module on various platforms - eg. Perl on Windows (NT/XP/Vista) and Linux (Fedora 6, Ubunto/Dapper) - to see which platform I should use for my GPGPU server farm.

I was expecting nvidia's drivers to be more mature/optimized on Windows than the other platforms, as Windows is their largest market.  Instead, I found Fedora to be 10x faster and Vista and Ubuntu 15x faster than Vista.

What blew me away was not that Linux was faster than Vista, but that Ubuntu was so much faster than Fedora - since I was using exactly the same hardware and drivers.

So I decided to do a line-by-line C and Perl FBO benchmark, stripping out all non-essential operations (like UI/text displays) - posted on [http://graphcomp.com/opengl/bench.html](http://graphcomp.com/opengl/bench.html)

The new results were that the Perl and C performance came out about the same on Linux, and the Fedora/Ubuntu numbers fell into line - I suspect that Ubuntu's X11/GLUT rendering is better than Fedora's, which would explain the differences between my first and second benchmarks.

The Vista performance continued to be slower - but this time the Perl performance was better than the C performance on Vista (no clue as to how that could happen).  When I get some free time, my next test will be to do a C benchmark comparing OpenGL and D3D on Vista to test my theory that Vista is reserving GPU cycles for Aero.

> **Wybiral said:**
> If you're not benchmarking the language difference, why are you using two languages?

As for why I posted my C vs Perl OpenGL benchmarks here - some earlier posts on this thread indicated that Perl could never perform as well as C in GPU applications.  These benchmarks serve to demonstrate that there are a number of GPGPU applications where Perl will perform as fast as C - with the added benefit of being more portable.

As for why I would use both C and Perl - I use Perl for fast protoyping (no compiling), and for server-side operations; I use C/C++ for desktop apps in order to obfuscate my IP.

---

### Post by slavik on 2007-03-26
please bear in mind, that the reason why I want to use Perl for ogl is because Perl's text processing is much easier (IMO) than C/C++ and I consider Perl a great language for rapid prototyping.

---

### Post by Game_Ender on 2007-03-26
You don't really have to guess about which is faster. C and C++ will always be faster than the equilvalent Python/Ruby/Perl programmer even if they are using the same underlying library.  At minimum this is due to function call overhead alone (A function is 100x slower in Python than in C and Python is faster than Ruby or Perl).  Whether this speed difference matters or not is the issue.

---

### Post by bfree on 2007-03-28
> **Game_Ender said:**
> You don't really have to guess about which is faster. C and C++ will always be faster than the equilvalent Python/Ruby/Perl programmer

I don't think you've been following this thread  ;^)

You can try out these benchmarks yourself - code and binaries at [http://graphcomp.com/opengl/bench.html](http://graphcomp.com/opengl/bench.html)

The stack overhead is statistically insignificant compared to GPU execution time for a complex model.  While runnning my benchmarks, on _average_ C was _slightly_ faster on Linux, but occasionally Perl ran faster.  On Vista, Perl consistently ran faster than C.

---

### Post by bfree on 2007-06-06
> **pmasiar said:**
> IMHO Python is better choice

I recently posted some [OpenGL benchmarks]("http://graphcomp.com/pogl.cgi?v=0111s3B2") comparing Perl and Python performance; Python is clearly slower, particularly in the area of managing arrays.  I've included a note from PyOpenGL's author explaining why Python is slower.

See OpenGL C vs Perl and Perl vs Python benchmarks at [http://graphcomp.com/opengl/benchmarks](http://graphcomp.com/opengl/benchmarks)

---

### Post by kthakore on 2009-08-03
I have been working on Perl SDL here is the repo for interested individuals.
[http://github.com/kthakore/SDL_perl](http://github.com/kthakore/SDL_perl). Its a work in progress but linux support is very good.

---

### Post by Sockerdrickan on 2009-08-03
[IMG]http://i50.photobucket.com/albums/f327/cesarhaha/forum%20replies/ThreadNecromancer.jpg[/IMG][IMG]http://www.sw-fans.net/imagegallery/data/502/threadnecro.jpg[/IMG][IMG]http://www.sw-fans.net/imagegallery/data/502/threadnecro.jpg[/IMG]

---

### Post by slavik on 2009-08-03
> **kthakore said:**
> I have been working on Perl SDL here is the repo for interested individuals.
[http://github.com/kthakore/SDL_perl](http://github.com/kthakore/SDL_perl). Its a work in progress but linux support is very good.
[http://search.cpan.org/search?query=sdl&mode=all](http://search.cpan.org/search?query=sdl&mode=all)

---

### Post by slavik on 2009-08-03
> **Tux0r said:**
> [IMG]http://i50.photobucket.com/albums/f327/cesarhaha/forum%20replies/ThreadNecromancer.jpg[/IMG][IMG]http://www.sw-fans.net/imagegallery/data/502/threadnecro.jpg[/IMG][IMG]http://www.sw-fans.net/imagegallery/data/502/threadnecro.jpg[/IMG]
Nice!

Thread closed.

---

