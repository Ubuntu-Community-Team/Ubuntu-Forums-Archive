---
title: "Linux better OS for Dev Then Windows?"
date: 2006-12-09
forum: Programming Talk
---

### Post by soul814 on 2006-12-09
^ Is linux better or windows, or its the same. o.O

---

### Post by max.diems on 2006-12-09
Linux is better than windows for MOST dev work. There are a few exceptions, like .NET and videogames.

---

### Post by slavik on 2006-12-09
I would disagree.

I have hardware accelaration, so SDL+OpenGL work nicely (I am actually thinking of moving away from C++ in favor of Perl, using SDL and OpenGL still, this will allow my stuff to be truly platform independent) and then there is Mono ... I am not sure how compatible Mono is with .NET

Also, PERL is there when you install Ubuntu, and that allows you to do a lot of things ...

---

### Post by Wybiral on 2006-12-09
I don't think they are MUCH different for developing. I used to do all of my stuff in windows and had a relatively easy time moving to linux. There are different tools for each, so its really hard to compare. I also agree that game development isn't any different, I still use OpenGL, and I still make games/graphics demos with the same amount of ease. One thing I will say is that adjusting from dos/windows style assembly to linux assembly is quite an experience (especially with GAS)!

As far as C++ goes, most the of libraries and files you use in windows, you can find for linux. They pretty much level each other out... While I will admit that using the linux command line to compile is MUCH easier than DOS Though there are a ton of good ide's for linux and windows and most are very similar.

I'd say they both offer about the same ease of use once you get to know the tools in each of them.

---

### Post by max.diems on 2006-12-09
> **slavik said:**
> I would disagree.

If you're disagreeing with my statement that windows is better for vidgame dev (looks like it), just a few clarifications. Windows game dev is often required to be inActiveX, which isn't on Linux. And console games have custom IDEs that are only avalible for Windows.

---

### Post by FryerFox on 2006-12-09
I have been programming for Windows since back when it was called DOS, and have been programming in Linux for only three years.

While I can't say which one is better, the resulting code in Linux is more *beautiful* and elegant to my eyes at least.

Some of the underlying principles of the Linux system (e.g. everything is a file, processes are cheap and fast to start up, config information should be stored in plain ASCII, input and output can be piped from one process to the next, etc.) encourage a different type of programming which appeals to me.

If I had the choice of programming in Windows or Linux, I would very much prefer programming Linux.

---

### Post by Wybiral on 2006-12-09
Why is windows game dev required to be in activeX? And what exactly do you mean by "And console games have custom IDEs that are only avalible for Windows" I'm just curious, I dont know what you mean be custom IDE. You can make console games on linux... With ease...

---

### Post by FryerFox on 2006-12-09
> **max.diems said:**
> Windows game dev is often required to be inActiveX, which isn't on Linux.

I think you mean DirectX. DirectX is actually not better than OpenGL for graphics programming, but it does offer an integrated solution for sound. In Linux, you have to use something else.

---

### Post by Wybiral on 2006-12-09
I've tried directX in Windows, personally I think OpenGL+SDL is way better for game development.

---

### Post by pmasiar on 2006-12-09
Better under Linux, hands down. My old windows PC with 1GB RAM was not able to run MS Visual Studio 2K5 - they recommend 2GB RAM or more. It is perfectly capable ubuntu dev box now. ;-)

VS 2K5 for development suck so badly you will not believe it. I found that if any dev tool is open sourced, and has something annoying, pretty soon someone just dives in and fixes it. Closed source sucks because no matter what annoyance, you just have to put up with it. You can feel MS developers laughing "yes we know it sucks but we need to release it now, so those poor bastards will have to handle the pain  - and they will pay us again to get upgrade, mwahahaha".

I agree that Linux tools have often less eyecandy. But it is for reason - you want tools you can use on remote box over slow connection. Once I needed fix server in remote location over *really* bad link, about 4k max. No remote GUI could handle that, but midnight commander was slow, but fine.

If you do not know midnight commander, you are missing a lot. It is amazing how much visual intuitiveness you can get from a character-only screen. Proven in the frontlines by happy users for 20+ years. 

For task which I do only rarely, give me intuitive GUI (like synaptic to install). But for stuff I do daily, give me (1) plain screen, (2) plenty of keyboard shortcuts (so I don't need to move my hands off keyboard) (3) get the hell out of my way! :-)

As the saying goes, if god wanted us to use mouse for everyday tasks, instead of ten fingers she would give us UBS interface. :-)

---

### Post by lnostdal on 2006-12-10
> **soul814 said:**
> ^ Is linux better or windows, or its the same. o.O

It's better hands down; Windows and its "nifty" tools cannot compete here.

---

### Post by Mickeysofine1972 on 2006-12-10
even when I used to program DOS games in the nineties i used DJGPP which if I remember correctly was a port from linux so that Microsoft's crazy memory architecture could be made flat.

As for easy of use? installing a dev setup is way easier and take much less time. 

Availability and reliability of development tools? no comparison! why do I need to have a DVD's worth of bloat to make programs?

Thats my 2p anyway ;-)

Mike

---

### Post by jordilin on 2006-12-10
Depending on the tools and the programming language. I'm learning C sharp now and developing apps with Mono in Linux is really painful as there is no debugger for MonoDevelop. In Windows there is SharpDevelop that has a good debugger and you know what's going on behind the scenes. There's very few documentation about using GTK# (the gui toolkit for Mono) and is really difficult in comparison to Windows Forms.

---

### Post by Jengu on 2006-12-10
> **FryerFox said:**
> I think you mean DirectX. DirectX is actually not better than OpenGL for graphics programming, but it does offer an integrated solution for sound. In Linux, you have to use something else.

And that's not even going to be true for much longer. DirectSound is dumped in DX10.

---

### Post by pmasiar on 2006-12-10
> **jordilin said:**
> I'm learning C sharp now and developing apps with Mono in Linux is really painful as there is no debugger for MonoDevelop.

Obviously Mono is problematic. It is because most free/opensource programmers would not touch Mono - and for a good reason. It is widely expected Microsoft set up legal minefield, why would one waste time and effort building good tools for a doomed project? And later get sued for independently reinventing something patented by MS? Why would we need reimplement brain-damaged .NYET interfaces? They were made incompatible by design. .NYET knows that Linux is a dangerous competitor (and it is) and tries to defend again Linux making .NYET incompatible and hard to share.

Stupid random decisions, like using backslash instead of forward slash as path separator cause untold pains. Open source is build on sharing code, solutions, and avoiding reimplamenting of the wheel. Closed source is build on making new wobbly incompatible half-assed whell in each new version, and charging users to upgrade.

Don't use C#, use free tools like python or C++. And if you are stuck with C#, obviously use its native proprietary platform. And you obviously also loose access to many superior tools build for development of free software. As RSM famously quipped, using non-free software is not a crime - is is punishment. :-) 

For gods sake, think why java was released under GPL: it was for a reason - to gain access to all free tools, free developers mindshare, to become member of free community. 

As analogy, lets compare Free software community to a village of people making free rope and giving it away to anybody who asks. One day, a bully will come over and ask for free rope so he can hang us. Obviously I am not giving *him* my free rope, right? Why should I?

Linux has better (free) **tools for development of free software**. If microsofties want better tools to develop non-free software, do we (free software community) have to develop it and give away (free) to them? Not only waste of time - it would be foolish to do.

*Free* as in freedom and free speech, not in terms of price.

---

### Post by jordilin on 2006-12-10
> **pmasiar said:**
> Obviously Mono is problematic. It is because most free/opensource programmers would not touch Mono - and for a good reason. It is widely expected Microsoft set up legal minefield, why would one waste time and effort building good tools for a doomed project? And later get sued for independently reinventing something patented by MS? Why would we need reimplement brain-damaged .NYET interfaces? They were made incompatible by design. .NYET knows that Linux is a dangerous competitor (and it is) and tries to defend again Linux making .NYET incompatible and hard to share.

Stupid random decisions, like using backslash instead of forward slash as path separator cause untold pains. Open source is build on sharing code, solutions, and avoiding reimplamenting of the wheel. Closed source is build on making new wobbly incompatible half-assed whell in each new version, and charging users to upgrade.

Don't use C#, use free tools like python or C++. And if you are stuck with C#, obviously use its native proprietary platform. And you obviously also loose access to many superior tools build for development of free software. As RSM famously quipped, using non-free software is not a crime - is is punishment. :-) 

For gods sake, think why java was released under GPL: it was for a reason - to gain access to all free tools, free developers mindshare, to become member of free community. 

As analogy, lets compare Free software community to a village of people making free rope and giving it away to anybody who asks. One day, a bully will come over and ask for free rope so he can hang us. Obviously I am not giving *him* my free rope, right? Why should I?

Linux has better (free) **tools for development of free software**. If microsofties want better tools to develop non-free software, do we (free software community) have to develop it and give away (free) to them? Not only waste of time - it would be foolish to do.

*Free* as in freedom and free speech, not in terms of price.
Yes, there are other languages best suited for Linux, like python. I already know python, and it is one of the best languages out there .NET was invented for great development under Windows, and I see that it is really painful to develop apps under Linux using this technology. Innovation, instead of trying to copy other technologies, is the way to succeed.

---

### Post by Choad on 2006-12-10
on windows i only ever managed to get a console c++ app compiled, and vb.... well vb made me lazy.

i do LOVE c# in vs 2k5 tho. i think that for all microsofts faults, vs2k5 and microsoft office are 2 top notch products

in linux, of course, everything is available and free, the community have helped me learn loads, and i am creating a game in c++ and SDL, not a crappy console app.

linux wins because i am a poor student who doesnt want to spend money on microsoft stuff, only to be forced to spend *more* money later on to upgrade, when the alternative kicks considerable ***

---

### Post by jordilin on 2006-12-10
> **Choad said:**
> on windows i only ever managed to get a console c++ app compiled, and vb.... well vb made me lazy.

i do LOVE c# in vs 2k5 tho. i think that for all microsofts faults, vs2k5 and microsoft office are 2 top notch products

in linux, of course, everything is available and free, the community have helped me learn loads, and i am creating a game in c++ and SDL, not a crappy console app.

linux wins because i am a poor student who doesnt want to spend money on microsoft stuff, only to be forced to spend *more* money later on to upgrade, when the alternative kicks considerable ***
Even if you had money to burn, Linux is by far better than m$.

---

### Post by pmasiar on 2006-12-10
Big companies like Amazon and google prefer open source solutions because that gives *them* control of the technology crucial for the survival. 

Say there is a bug in Windows which makes it fail only  for clusters on 1000 servers or more. Fat chance it is  going to be fixed anytime soon, and if it gets fixed, it will come bundled with yet another useless eyecandy with known exploits. 

With open source, if it is important, you can dive in and fix it, or hire a guru to fix it for you. If a bug can cost you $1M a week, it's a bargain to pay $100K a year for a guru, so twice a year he will fix a bug like that for you.

Are you aware that Google was own Linux distro (for servers) and own filesystem for huge clusters? And they do *not* plan to release it - it is a competitive advantage.

---

### Post by max.diems on 2006-12-11
Yes, DirectX is what I meant. I mean required as in, "You want to work here? You'll program in DirectX."

---

### Post by addicted68098 on 2006-12-11
Linux seems to be easier to use as a devolper, I do not know if its better becaue I still do not have much Linux expirence.

I have never been big on the .net platform, Visual Basic is supposed to be easy to devolope for, I agree, but I really hate the syntax, really its a more complex structure then many languages and it is also a slower structure when it comes down to proformance. C++/C are fine using .Net kits but with my little expirence it seemed to be the same as any OS.

---

### Post by Grey on 2006-12-11
Yes, Linux is much better than Windows for development.

I've been going mad though, as I actually do have to use windows for development.  I am a console game developer.  All my tools and compilers are for Windows only.  (Most notably is the console hardware emulator, which is connected to the PC via USB.  Drivers do not exist for Linux).

---

### Post by Choad on 2006-12-11
> Yes, Linux is much better than Windows for development.

I've been going mad though, as I actually do have to use windows for development. I am a console game developer. All my tools and compilers are for Windows only. (Most notably is the console hardware emulator, which is connected to the PC via USB. Drivers do not exist for Linux).
i am guessing that you are developing for the wii because

no one develops for the gamecube really, you have a sony boycott thing in your sig, and you couldnt possibly expect to develop for xbox on anything except windows

am i right?

---

### Post by sweemeng on 2006-12-11
it really depends. by then i got used to gnu based tools. 

i mean, when i first learn programming in windows, i use gcc, on djgpp and dev-c++. uses gdb. and uses python. for me there is no reason, to use windows(thats why i converted). 

and i think that certain thing can be setup more easily on linux than on windows. for example to setup a lamp stack is easier than setup a wamp stack. or using sqlite for example, 

and not to mention a few tools that not readily available on windows, such as a profiler, linux have gproff. or shell for quick and dirty solution. or perl.

on the other hand windows have an integrated solution, visual studio.net is able to develop for phone for example. but is tied to microsoft product only. and expensive. and force to upgrade sometime.

---

### Post by samjh on 2006-12-12
Linux is better for Linux development, Windows is better for Windows.

That might sound really obvious, but it's true.  You'd have to be a bit strange to think Linux is a better overall development OS than Windows, if your target platform is Windows, and vice versa.

Having said that, I have yet to come across a better IDE than MS Visual Studio, in any platform.  Eclipse is pretty good, but not in the same league or purpose.  Visual Studio is one of the few things I miss about Windows.

---

### Post by Grey on 2006-12-12
> **Choad said:**
> i am guessing that you are developing for the wii because

no one develops for the gamecube really, you have a sony boycott thing in your sig, and you couldnt possibly expect to develop for xbox on anything except windows

am i right?

Yeah.  ;)  I develop for DS and Wii.  It's actually an odd coincidence, considering that I would develop games for ANY platform, as I just love the work.  But it so happens that I develop for the consoles I love.  (I really dislike both Sony and Microsoft).  I do have to admit that the PS3 hardware really appeals to me though.  I would love to develop a PS3 game just so that I could play with it.  It's challenging as hell to develop for, but it's also a prime opportunity to strut your stuff and develop something amazing.

The DS and the Wii are just fun though.  You don't really have to worry about writing some sophisticated monstrosity.  You just write your code, it runs, and everyone's happy.  You don't have to trick the hardware.

---

### Post by David Marrs on 2006-12-12
For configuration and setting up, Windows can be a real nightmare. It also doesn't help that they don't mind changing the rules through upgrades. Linux devs tend to be far more critical of that sort of behaviour. The one place where Linux tends to fall short is autoconf/automake. That stuff can start to get ugly with big projects, but I believe there are other tools emerging that do a better job. I'd say Linux is an order of magnitude easier to use, especially for web development (although you always need IE6 around for design work). Unless you're targeting the Windows platform, or need a tool/lib that's windows-specific, I'd recommend Linux.

---

### Post by bfree on 2007-03-16
I'm a Windows developer, and generally see no significant performance difference between Windows and Linux - the one exception is with OpenGL.

I recently released a new Perl OpenGL (POGL) module, and performed some benchmark tests between Vista, Fedora and Ubuntu - same machine, same nVidia card, same code - and Fedora was 10x as fast as Vista... and and Ubuntu was 15x as fast.

Given that I was using the same nVidia drivers on Fedora and Ubuntu, I was expecting similar results.  Ubuntu is doing _something_ right.

Check it out at [http://graphcomp.com/opengl](http://graphcomp.com/opengl) - Bob Free

---

### Post by yaaarrrgg on 2007-03-16
Personally, I prefer Linux for development.  I think Linux is an OS desiged especially for the programmer. 

But what answer do you expect? You're asking the question on a Linux forum :)   Windows developers, I'm sure, feel that Linux is desperately lacking graphical IDE's, like Visual Studio.

---

### Post by blanky on 2007-03-16
I think that a lot of posts in this thread are biased, but hey what do you expect when asking within a Linux Distribution's Discussion Forums?

Anyways, I'm not going to go deep into this, but I really appreciate the fact that in Linux, a lot of tools are integrated. You don't have to mess around with PATHs and what not, and it's a lot nicer for when developing terminal applications, and documentation is often around (*If you're familiar with reading it*).

However, on Windows, it does have its neat things as well, and some might fight this argument for the sake of Linux, just know I'm not trying to be biased. I bought Visual Studio Standard for windows development a while ago, and it was really a great investment. I really like Visual Studio and it has to be my most favorite IDE of all. I also have to recognize the fact that most of my target audience is on Windows. And some things are only on Windows, such as XNA and some .Net features.

Again, though. I think that for learning how to program, Linux is neat, because everything is pretty much integrated. And many languages start you off by writing terminal applications, and the fact is that terminal applications on Windows are very ugly and bore the learner.

Each have their own things. I go into one when I need something, but usually develop on Windows. I'm writing a game (*The Instagib Project, in my sig*) and it builds on Windows, Mac OS X, Linux, Free/Net/OpenBSD, Solaris, IRIX, and so many other Operating Systems and Architectures. Thanks to Subversion, I can keep up with changes I do and whenever I need to modify something on the Linux side (*For example, a makefile*), I just boot into Ubuntu, change it, commit it, build and run to make sure it all works, and I'm fine.

So fact of the matter is that you'll eventually learn how to make applications cross platform (*If there is a need*), but I suggest beginners shouldn't worry about that, when they do they end up not doing much due to the worry of remaining cross platform.

---

### Post by Darkness3477 on 2007-03-16
I think that Ubuntu is better to develop in simple because I have *every* tool I possibly could ever need at my disposal. sudo apt-get install. 

It was mainly that feature that interested me in linux in the beginning. Having so many great programs in the same area is great. It means I don't have to search around google for half an hour to find the right thing like I used to.

---

### Post by cunawarit on 2007-03-16
> **pmasiar said:**
> Better under Linux, hands down. My old windows PC with 1GB RAM was not able to run MS Visual Studio 2K5 - they recommend 2GB RAM or more. It is perfectly capable ubuntu dev box now. ;-)

Simply false, I run Visual Studio 2005 on a machine with 1GB of ram all the time. In fact, I run 4 or 5 instances of it most of the time. 

> VS 2K5 for development suck so badly you will not believe it. I found that if any dev tool is open sourced, and has something annoying, pretty soon someone just dives in and fixes it. Closed source sucks because no matter what annoyance, you just have to put up with it.

It does have a few issues, true. Some are annoying, true. It still is a damn productive IDE though! 

> You can feel MS developers laughing "yes we know it sucks but we need to release it now, so those poor bastards will have to handle the pain  - and they will pay us again to get upgrade, mwahahaha".

Having met a few MS people before nothing could be further from the truth. They have generally struck me as truly enthusiastic about their products, and very keen on using them too. Ever heard them say "eating our own dog food"??? They truly believe in their products. 

> I agree that Linux tools have often less eyecandy. But it is for reason - you want tools you can use on remote box over slow connection. Once I needed fix server in remote location over *really* bad link, about 4k max. No remote GUI could handle that, but midnight commander was slow, but fine.

If you do not know midnight commander, you are missing a lot. It is amazing how much visual intuitiveness you can get from a character-only screen. Proven in the frontlines by happy users for 20+ years.

Midnight Commander? That's that Norton Commander clone thing... :confused: What's wrong with just using the command line?

> For task which I do only rarely, give me intuitive GUI (like synaptic to install). But for stuff I do daily, give me (1) plain screen, (2) plenty of keyboard shortcuts (so I don't need to move my hands off keyboard) (3) get the hell out of my way! :-)

Once again, why use Synaptic? What's so hard about apt? I agree that Windows is too GUI heavy. But you seem to be too GUI heavy too!

---

### Post by pmasiar on 2007-03-16
> **cunawarit said:**
> Having met a few MS people before nothing could be further from the truth. They have generally struck me as truly enthusiastic about their products, and very keen on using them too. Ever heard them say "eating our own dog food"??? They truly believe in their products.

They never used Visual Basic part of VS. If they did, lots of annoyances would be fixed. But anyway I do not care about "Ms is better than Linux" flamewars. Use what you want. I prefer free software.

> Midnight Commander? That's that Norton Commander clone thing... :confused: What's wrong with just using the command line?

MC is visual without having GUI. Something like that is lost on MS fanboys, but I don't care.

---

### Post by blanky on 2007-03-16
> 
Simply false, I run Visual Studio 2005 on a machine with 1GB of ram all the time. In fact, I run 4 or 5 instances of it most of the time.


Agreed. People are always complaining about it. I run 512 MB and it runs perfectly fine, multiple instances too. Projects that are huge, too, like [this]("http://svn.jorgepena.be/websvn/listing.php?repname=The+Instagib+Project&path=%2Ftrunk%2Ftip%2F").

> 
You can feel MS developers laughing "yes we know it sucks but we need to release it now, so those poor bastards will have to handle the pain - and they will pay us again to get upgrade, mwahahaha".


Biased.

pmasiar, I don't really think he's an anti-Linux, pro-Microsoft type of person, since he seems to be an Ubuntu user and what not. But one thing's true: There's a lot of bias, but what can someone expect from asking in a Linux forum? I use Ubuntu myself, and I like it and appreciate it, and am pretty efficient in Linux. But I'm not anti-Windows type of person. Ironically some people switch over simply because of ***one*** error, never realizing that in Linux they sometimes have to go through 50 more. I'm not saying it's a bad thing, I encourage the use of Linux, but there are certain realizations that have to be made. I personally appreciate both Operating Systems and am neutral. I like the specific things of either, and dislike some things of either. I know how to use each OSes features I like to their fullest.

---

### Post by j_g on 2007-03-17
This is a _tremendously_ biased forum in favor of Linux, so you won't find very informative answers to a question comparing Windows to Linux (just like you won't find a lot of good Windows advice here -- frankly, as a longtime Windows developer, I've seen some really, really bad, incorrect advice/information given to Windows developers in this forum). If you want to know something useful/informative about Windows development, go to a place like [www.codeproject.com](www.codeproject.com) -- not here. Just for enlightenment, post the same question on CodeProject and see the responses. Then you'll know exactly why this is not a forum to get useful advice/information about Windows development, because there, you'll be hearing a majority of _demonstrably different_ opinions from people who have written _lots_ of original Windows software. Try it and see.

I think that MS dev tools are among the best in the business, and they make developing for Windows fairly easy. You'll notice that the negative opinions about Windows development come from people who are using "lowest common denominator" ports of Linux tools to (allegedly) develop on Windows. (I do realize that there are certain people who claim to have "personal experience" with MS dev tools, but in fact, they're totally misrepresenting that). And really, it is the usability of the tools that make just about the biggest difference in whether programming is easy or hard. Pick the best tools on a given platform, and you're already well on your way. Pick the worse tools and you're likely to be stuck at the starting gate for a long time.

---

### Post by bfree on 2007-03-17
I've developed on VMS, MacOS, DOS/Win16/Win32, and various flavors of Unix, including Linux - they all have strengths/weaknesses.  The key is just using the right OS for the job at hand.

For online services, you can build an entirely portable LAMP-based system that will run with the same performance on Linux/Win32/MacOS - but since Linux is free, the choice is obvious.

If your goal is to sell high-volume desktop software, Windows has the largest market.  I wrote a multi-threaded app for Win3.1 (used my own threading engine) - the binary distribution still runs without modification on Vista, and all other 16/32/64 bit versions of Windows.

On Linux, there's no guarantee between RHEL, Fedora, Ubuntu, et. al. what libs/packages are installed - and users often need to build their own binaries - resulting in different configurations/dependencies per user... a potential nightmare for developers of complex apps.

FFMPEG is a good example.  A good video tool with a nice plugin (vhook) architecture that 3rd party developers can create effects filters for.  Unfortunately, every Linux distribution comes with different libs installed (ungif,lame,etc) - so you either install an FFMPEG binary that has been built specifically for your distribution, or you build it yourself.  Meanwhile, there is no way within the vhook plugin to determine at runtime what OS support is there - so you are forced to distribute your plugin source, and therefore your company's trade secrets, IP, etc.

Whereas on Windows - you know what OS services are there; the libs have standard names and a standard method for programatically querying interfaces.  IOWs, you can create a binary plugin and know that it will run on every copy of Windows out there.

So if your goal is to write free/opensource software, or develop online services (both of which I do) Linux is great.  If you want to make a living at developing desktop apps or libs (which I also do), Windows is the way to go.

Not saying that one way is better than the other - just different.

---

### Post by pmasiar on 2007-03-17
BTW discussion is dead not because I agree with you, but because I do not care about flamewars. And I believe that other ppl ignore this thread for same reason. Just to remind readers of this thread: free software is not about price or convenience. It is about your freedom to use, improve, and share your improvements with other people.

And yes, I have bias for freedom. :-)

---

### Post by Tomosaur on 2007-03-17
Linux, hands down. From my relatively short experience for developing anything on Windows, I know for a fact that it just isn't for me. I don't believe for one minute that the Linux dependency issues are that serious, it just reeks of developer laziness. On Windows I have to struggle with lots of different include directories to get programs to compile, I have to link libs from different directories - it's just a nightmare. Linux is more organized, and I'm not relying entirely on one distribution of header files / libraries. Everything goes into /lib, or /include (or some very slight variation, but it's still much easier to get used to) - that's much, much more intuitive than downloading the Windows SDK, finding it doesn't have something you need, downloading a different SDK, messing around combining the bits you want or setting up the paths manually, and then HOPING it will compile and link properly.

Now, I'm not a professional developer - I'm not a super experienced developer and true, I probably went about getting everything set up on Windows the wrong way, but you know what? I go back to Linux and I'm happy. I don't need to concern myself with a stupid API for Linux, I can just get on with creating something. Everything is where I need it to be, it's all automatically found (for the most part - linker errors are much, much less common) at compile time, and there are ways around the dependency issues when the time comes to distribute anything.

It's true that the dependency situation is pretty annoying, but it's not THAT much of a problem, if the distribution uses a sane package management system. We're also getting CNR soon, which will help to alleviate the problem even more. You can set up a package to solve the dependencies yourself, or you can just provide a wget script with your source, or at least provide the user with a configure script so they'll at least KNOW what they need. 

I would argue that those who complain about it are arguing with a brick wall. The development world in Linux is based on principle rather than profit. I wouldn't WANT to develop something which inhibits the end-user, or threatens them with court if they want to change something. That's just my opinion. You CAN make money with Linux - very few of us are against PAYING for software. The reason past efforts have failed is because the developers have tried to restrict users. We just don't want that. We want to be free to modify something if and when we see fit, and we don't want to worry about 'rental' licences. You can't make money on Linux if you target traditionally 'open' people with restrictive licences. You need to trust your target audience, and we will trust you right back. FOSS is a services industry, not a product industry. If you don't want to take part in it, then that's fine - we're quite happy doing our own thing. You won't break it though, because it's principle over profit. That's just the way it is - and you're going to suffer when people grow tired of your endless EULAs and your self-protection. You may experience a fall in profits if you switch to FOSS, but from the FOSS point of view, that's just part of making the industry a better place. 

You've made FOSS less profitable because you charge so goddamn much for software. You put limitations on your users - you don't open your code so you get tons of security risks and people have to keep paying through their noses because they need AV protection and expensive firewalls. People are used to paying all of this money, so you ramp the prices up, and now that FOSS is getting popular, as is Linux, all of these big developers are wincing because they know people don't WANT to pay hundreds of pounds / dollars for a 12 month / 1 computer licence to use something which may or may not work - they've just had no choice in the past. Lower the prices, and treat your customers with respect and trust, and you will see many of the problems disappear. Get rid of the anti-piracy bullshit, and make more people able to afford your product. People do not NATURALLY steal things - they do so because they perceive the legal way of doing something to be unfair, or stupid. Everything on a shop floor is on display - normal people just do not walk right in and pocket everything, do they? Normal people DO pirate software. What does that tell you? There's something wrong with software, not with people.

---

### Post by j_g on 2007-03-18
> On Windows I have to struggle with lots of different include directories to get programs to compile, I have to link libs from different directories

Tom, tom, tom... I keep telling you -- when you need help with Windows development, make sure you ask a _real_ Windows developer -- not a Linux developer who claims he knows all about Windows development.

In order to add an additional include directory to Visual C++, select the "Tools -> Options" menu item. This brings up the "Options" dialog. Flip to the "Directories" page. This shows all the directories that are currently searched for include files. You can add as many new directories as you want to this list. VC will make sure the compiler knows about these. You can also reorder the directories by clicking on the up/down arrow buttons. This listing is a memorized setting. Under "Show directories for", you can also select "Library files". Now the list shows searched lib directories. Again, add more directories if you like. VC will make sure the linker knows about them.

But I find the easiest way to add a particular lib to a particular project... If you've got some third party DLL, and it has a .LIB file with it that you want to link with (ie, because you're using static, rather than dynamic, linking), then select the "Project -> Add to Project -> Files" menu item. This brings up a dialog to pick out files to add to your project. Find the .lib file and select it. It will then appear in VC's listing of files in your project. VC is smart. It knows what a .lib file is, and what it's for. It will rewrite your make file to supply that lib file to the linker (and it doesn't matter what directory it's in, because all that stuff is managed by VC). And if you later decide to not use the .lib, just select it in the list and press the DEL key. VC will remove it and rewrite your make file. With VC, you should never need to handedit a make file, nor manually invoke the compiler/linker from a command line, nor worry about what your current directory is (or you're doing something wrong).

> that's much, much more intuitive than downloading the Windows SDK, finding it doesn't have something you need, downloading a different SDK, messing around combining the bits you want or setting up the paths manually, and then HOPING it will compile and link properly.

See, that's why you should use MS dev tools, and not Linux ports. MS dev tools automatically know when you install various SDKs. I use a variety of SDKs with VC, and have no problems. VC has always found them on its own.

But if you use MSDN for your documentation, every function tells you what header files are needed, and where they come from.

And Tom. All non-system, shared files get installed in "Program Files". If it's a Microsoft product (like the Windows SDK), you'll find it under the "Microsoft" product directory.

---

### Post by Wybiral on 2007-03-18
> **j_g said:**
> In order to add an additional include directory to Visual C++, select the "Tools -> Options" menu item. This brings up the "Options" dialog. Flip to the "Directories" page. This shows all the directories that are currently searched for include files. You can add as many new directories as you want to this list. VC will make sure the compiler knows about these. You can also reorder the directories by clicking on the up/down arrow buttons. This listing is a memorized setting. Under "Show directories for", you can also select "Library files". Now the list shows searched lib directories. Again, add more directories if you like. VC will make sure the linker knows about them.

But I find the easiest way to add a particular lib to a particular project... If you've got some third party DLL, and it has a .LIB file with it that you want to link with (ie, because you're using static, rather than dynamic, linking), then select the "Project -> Add to Project -> Files" menu item. This brings up a dialog to pick out files to add to your project. Find the .lib file and select it. It will then appear in VC's listing of files in your project. VC is smart. It knows what a .lib file is, and what it's for. It will rewrite your make file to supply that lib file to the linker (and it doesn't matter what directory it's in, because all that stuff is managed by VC). And if you later decide to not use the .lib, just select it in the list and press the DEL key. VC will remove it and rewrite your make file. With VC, you should never need to handedit a make file, nor manually invoke the compiler/linker from a command line, nor worry about what your current directory is (or you're doing something wrong).

That's dandy, but it's nothing special... With GCC all I need to add an include or library path is use the "-I" and "-L" flags... No clicking, no "Options->directories->add directory" I just compile with "-I/some/path"

Btw, with GCC I can write software that's easy to port between Windows, Mac, and many linux distro's without having to butcher my code or replace my libraries.

What's best for WINDOWS development? Windows dev tools. What's best for portable development, open source tools like GCC. For most LINUX users, portability is a goal when they are developing software, so WTF would they want to use Windows-only dev tools for?

You're standing around pointing the finger at everyone for being biased, without considering that most Linux developers want their software to be capable of being compiled for Linux too. Are you going to say that Windows dev tools are superior in this sense? I sure hope you aren't that blind.

EDIT:

BTW, in case you're wondering why they want their software Linux compatible... Look around. You're on a LINUX forum. There is no bias here... This is just how it is: MS tools are NOT the best option for cross platform development. Period. MS tools are for MS development.

---

### Post by pmasiar on 2007-03-18
> **j_g said:**
> Tom, tom, tom... I keep telling you -- .

j, j, j, j I keep telling you - you are at the Linux forum. You are biased, and it is OK, but please stop this, you are adding fuel to flamewars. And I really dislike your patronizing tone. I really, really dislike it. Tomosaur is known for wise words, your patronizing is really out of place.

This community prefers free and cross-platform solutions. Get used to it. Don't waste bandwidth and electrons on MS-only solutions - trust me, if anyone cares, can PM you, you are known Windows expert and promoter. Don't troll, it gets boring.

---

### Post by j_g on 2007-03-18
> in case you're wondering why they want their software Linux compatible

Who is "they"??? I was addressing Tom's specific Windows environment issues in what you quoted. Lord knows what you're talking about, but it has nothing whatsoever to do with my quotes. If you're going to argue with your own straw man, then make up your own quote.

---

### Post by j_g on 2007-03-18
> you are adding fuel to flamewars

I was responding to tom's specific Windows development issues, and telling him how to handle them.

You, on the other hand, are interested in only leveling accusations, name-calling, and ironically, starting your own flame war. Typical.

---

### Post by DavidBell on 2007-03-18
> **Wybiral said:**
> MS tools are for MS development.

That's not true, cross platform libraries are more important than the IDE. Only cross platform C++ I've done was with wxwidgets in Vis Studio recompiled in GCC, no problem. You can use GTK & QT in VS too AFAIK.

But really I thought the OP was asking if Linux has any inherent advantages as an OS ... that has nothing to do with IDEs/Tools. The only compelling thing I see in Linux is that realtime threads are now supported out of the box (in theory I don't know how easy they are to use). I reckon COM/OLE is a major plus for Windows, even if you hate it and it's a security hazzard you have to admit it adds a level functionality that requires very little effort from the developer and that I don't see in Linux. I would aslo add stability of the platform for windows - stuff written for Win95 still runs in Vista, I don't think Linux has the same record, Apple definitely not.

DB

---

### Post by ZDemon on 2007-03-18
This forum is certainly biased.

But everyone is comparing IDE's. Linux loses in that sense. MS 2005 is good. But let me lay out why lots of people said "Linux is hands down better". I have experience in writing drivers and software alike for Windows and Linux.

[LIST]
[*]Writing drivers is SO DAMN EASY in Linux. Pain in windows. No contest. I remember interfacing with the parallel port on my 2 week of using Linux.
[*]Compiling using GCC is easy. No need to add header to your project, add library files manually, create "PATHS".
[*]Using apt-get, you can download ANY library you want, then just include the header in your source code and modify your makefile a little.
[*]LibGlade and Glade is so good, it seems like VB is harder. GTK+ rocks.
[*]I have written GUI software using LibGlade that has a size of around 20kB. Using MFC in MS 2005 .Net, it will be around 500kB to 2 MB.
[*]Documentation is available for most if not all libraries, they are the packages with the -doc extension.
[*]The Linux terminal is godsent for debugging compared to the crappy console for windows, The MS 2005 debugger is not always practical and difficult to use.
[/LIST]

I have no experience in OpenGL or SDL though, so i cant comment on that. But again, all you need to do is apt-get the libraries. But i must admit, i play my games on windows.

Im a pansy, please don't flame me... 8-[

---

### Post by cunawarit on 2007-03-18
> **pmasiar said:**
> MC is visual without having GUI. Something like that is lost on MS fanboys, but I don't care.

Its a Norton Commander clone of which there are a bazillion different ones around for just about every OS under the sun, including Windows. 

MC is nothing special. Unless I want to do a lot of file handling I see no reason to use a Norton Commander clone when the command line will do. 

As for the fanboy talk, I really don't know what you are going on about. I am using Debian Etch RC as we speak, I have MonoDevelop open, and I'm tinkering around with XSP... You want to know what I truly think? I think right now Visual Studio is the more mature IDE, MonoDevelop is a terrificly exciting project that is already incredibly useful at only version 0.12/0.13. But seriously, right now, when I am not just tinkering at home if I want to develop something that I am getting paid for I will resort to Visual Studio. That will probably change in the future once MonoDevelop reaches version 1.0, or close to it anyway. 

I like free software, and I like the software that the open source model ends up producing. But I tend to take a more pragmatic approach when choosing the tools I need, if a bit of commercial software will make my life a lot easier and I can afford it, I will go for it.

So for .NET development, I'd go for Windows. But that's to be expected, given that .NET is a Microsoft technology it is not surpricing that Linux is playing catchup. But just choose whatever OS and tools is most appropiate for the task at hand.

---

### Post by Wybiral on 2007-03-18
> **DavidBell said:**
> That's not true, cross platform libraries are more important than the IDE. Only cross platform C++ I've done was with wxwidgets in Vis Studio recompiled in GCC, no problem. You can use GTK & QT in VS too AFAIK.

Well, actually due to lack of standards, a lot of code will only compile on VC++, and since MS is the only platform that supports VC++, it's the only platform that it's practicle to develop in. You ever tried to port a program from MSVC++ to GCC? It usually requires a lot of work.

Now, if you start in GCC, then you don't have to worry about that... GCC is available for most platforms.

BTW, I know what libraries are! My point is that different compilers have different standards and code isn't always portable between them. I guess that's everybody's fault (since no C++ compiler has actually met all of the standards), but the fact still remains that GCC _IS_ available on most platforms, so it makes sense to use GCC over MSVC++ if you plan to port your project.

EDIT:

BTW, just for the record... This has nothing to do with IDE's as you mentioned... They are completely different compilers that DO accept different code.

---

### Post by Tomosaur on 2007-03-18
> **j_g said:**
> Tom, tom, tom... I keep telling you -- when you need help with Windows development, make sure you ask a _real_ Windows developer -- not a Linux developer who claims he knows all about Windows development.

What exacty is a 'real' Windows developer? Someone who's limited to developing on Windows? There is something very wrong with your statement - the majority of people on here, who develop for Linux first and foremost, have at least some experience with development on Windows. The flipside? Well - for the most part, it doesn't exist. It's true that I don't know a huge amount of Windows developers personally - but of those that I DO know, very few have actually used Linux, let alone tried developing with it / for it. Linux developers, or at least the ones I've spoken to, have a lot more valuable experience with a wider range of platforms and tools. They may not know all the ins and outs of development for Windows specifically, but they know a fair amount, and they know a wider range of things. I have yet to meet a Linux developer who claims he knows all about Windows development - but I HAVE met Windows developers who claim to know all about everything, soo....

> 
In order to add an additional include directory to Visual C++, select the "Tools -> Options" menu item. This brings up the "Options" dialog. Flip to the "Directories" page. This shows all the directories that are currently searched for include files. You can add as many new directories as you want to this list. VC will make sure the compiler knows about these. You can also reorder the directories by clicking on the up/down arrow buttons. This listing is a memorized setting. Under "Show directories for", you can also select "Library files". Now the list shows searched lib directories. Again, add more directories if you like. VC will make sure the linker knows about them.

But I find the easiest way to add a particular lib to a particular project... If you've got some third party DLL, and it has a .LIB file with it that you want to link with (ie, because you're using static, rather than dynamic, linking), then select the "Project -> Add to Project -> Files" menu item. This brings up a dialog to pick out files to add to your project. Find the .lib file and select it. It will then appear in VC's listing of files in your project. VC is smart. It knows what a .lib file is, and what it's for. It will rewrite your make file to supply that lib file to the linker (and it doesn't matter what directory it's in, because all that stuff is managed by VC). And if you later decide to not use the .lib, just select it in the list and press the DEL key. VC will remove it and rewrite your make file. With VC, you should never need to handedit a make file, nor manually invoke the compiler/linker from a command line, nor worry about what your current directory is (or you're doing something wrong).

Well, on Linux, all I have to do is....nothing. As long as the files are in the include or lib folders, then everything just works. No clicking or messing around, it just finds everything automatically. I think that's just a tad more friendly than clicking around menus, no?

> 
See, that's why you should use MS dev tools, and not Linux ports. MS dev tools automatically know when you install various SDKs. I use a variety of SDKs with VC, and have no problems. VC has always found them on its own.

But if you use MSDN for your documentation, every function tells you what header files are needed, and where they come from.

And Tom. All non-system, shared files get installed in "Program Files". If it's a Microsoft product (like the Windows SDK), you'll find it under the "Microsoft" product directory.

I don't know why you're calling these tools 'Linux ports'. Most were intended to be cross-platform right from the very beginning. GNU != Linux, and GCC was not written specifically for Linux. The GNU tools are meant to work across a diverse range of platforms.

As for documentation, well, documentation exists for both platforms, so it's really a moot point.

And yes, I'm aware I probably set up the necessary directories and such like incorrectly while using Windows tools - but the point is, Linux is easier. All I have to do, essentially, is type:
```

sudo aptitude install mylib

```

And everything is set up for me, nice and clean. I don't see how that is worse than Windows tools. If anything, it's better.

I really don't want to start a flame war or anything here, but seriously, MS tools are not the be all and end all of development tools. If you want to develop specifically for Windows, using only Windows SDK stuff, then yes, by all means, MSVC is probably the best tool for the job. For anything else, why not just use Linux tools, where everything is clean, easy, and efficient? In *my experience*, however little that may be, developing on Windows is a mess. You may think differently, perhaps I went about it the wrong way, but what I do know is that getting started on Linux is as easy as downloading build-essential.

---

### Post by g3k0 on 2007-03-18
Starting IDE's up just takes too long for me.  My windows IDE's (Borland Developer Studio and Visual Studio 2005) take soooo long to start.  If I am doing something relatively simple I prefer just to create a cpp file and start typing.  Linux seems much more friendly with the command line for this to me.  Thats why I used it in a programming contest the other day.  Plus man pages are nice.... But on the other hand it really depends what platform you are developing for.  As much as I love linux, if I want to benefit people with a program, windows has a much larger user base.  Also my commercial IDE's make life easy with GUI.  The linux IDE's I have tried are ugly and difficult to use.  This is not a debate, this is my opinion.  Don't argue it with me.

---

### Post by Wybiral on 2007-03-18
> **g3k0 said:**
> Starting IDE's up just takes too long for me.  My windows IDE's (Borland Developer Studio and Visual Studio 2005) take soooo long to start.  If I am doing something relatively simple I prefer just to create a cpp file and start typing.  Linux seems much more friendly with the command line for this to me.  Thats why I used it in a programming contest the other day.  Plus man pages are nice.... But on the other hand it really depends what platform you are developing for.  As much as I love linux, if I want to benefit people with a program, windows has a much larger user base.  Also my commercial IDE's make life easy with GUI.  The linux IDE's I have tried are ugly and difficult to use.  This is not a debate, this is my opinion.  Don't argue it with me.

That's a good point... The command line is actually really handy for dev.

I can use a command like this to build all of the ".c" files in my folder to object files:

```
gcc *.c -c
```

Now all I have to do is link them.

---

### Post by pmasiar on 2007-03-18
> **cunawarit said:**
> Its a Norton Commander clone of which there are a bazillion (...)MC is nothing special. Unless I want to do a lot of file handling I see no reason to use a Norton Commander clone when the command line will do. 

MC is AFAIK the only one with character-based interface - not GUI. But it's gui-like interface is still very visual and intuitive. I used it once over really bad dial-up line (4800 baud or less) and it still worked, hardly - I don't think any GUI would survive that. You used  commandline for so many years and forgot how it is to start with terminal. Did you ever used MC or something like that? 

For me, MC was very useful, and IMHO many people might enjoy it and dive into Linux with MC easier than with commandline. Not you, and it's fine too. MC allows me to create my own custom commands, remembers them for me so I don't have to.

BTW Windows experts: if anyone knows about decent MC or Norton Commander clone for Windows, I am interested. I looked at couple and none was good enough.

---

### Post by Tomosaur on 2007-03-18
@pmasiar:

Take a look at [this page](http://homepages.compuserve.de/SiegwardJaekel/mc-gb.htm). I haven't tried it out myself, but could be worth looking at.

---

### Post by pmasiar on 2007-03-18
Thanks Tomosaur - I expected response from our Windows experts, got one from you :-)

Last change in Source code 02/01/2003 - looks pretty dead to me. Couple versions vere released in Linux version since then. No, I am not going to fix it myself :-)

---

### Post by lnostdal on 2007-03-18
I bet Cygwin has MC included.

edit: ..on second though; i _know_ Cygwin has it .. i remember using it not long ago. Cygwin is the first thing I install if I have to work with a Windows-box.

---

### Post by cunawarit on 2007-03-18
Much like Norton Commander, the majority of the clones are text based and can be run at the console. 

The original: [http://en.wikipedia.org/wiki/Norton_Commander](http://en.wikipedia.org/wiki/Norton_Commander)

[IMG]http://upload.wikimedia.org/wikipedia/en/b/bf/Norton_commander.png[/IMG]

---

### Post by cunawarit on 2007-03-18
As far as the IDEs, they can be a double edge sword. On the one hand they do increase productivity, on the other hand some people rely on them too much and this is bad particularly when people are learning to program.

---

### Post by pmasiar on 2007-03-18
As I said MC is NC clone... thanks for the picture, but do you know any usable Windows clone? BTW most Linux clones I looked at are GUI-based.

---

### Post by cunawarit on 2007-03-19
Yes, I've used plenty I would class as usable. Of course, usability is arguably subjective measure. 

Examples, Volkov Commande, UFO... But since you like Midnight Commander and already think it is usable then yes, Midnight Commander is available for Windows.

Not forgetting that Norton Commander is a DOS product that probably still runs A-OK on Vista... It will not do long filenames though... I think... I never tested the last version of it. 

Anyway, this is diverging a little bit from the original question. I think it is safe to say that Linux is far more usable from the command line than Windows. Although, this is changing a little with Windows Power Shell. 

As far as command line file managers, both Linux and Windows are well supported.

---

### Post by pmasiar on 2007-03-19
Talk is cheap, show me the code! 

> **cunawarit said:**
> Yes, I've used plenty I would class as usable. Of course, usability is arguably subjective measure. 

usable - as in "someone is using it, at least it's own single developer". Is your definition of "usable" much different? Does our definition requires anyone actually *using* the program? :evil:

> then yes, Midnight Commander is available for Windows. 

MC for Win: Not changed since 2003. Dead in the water. Why would anyone touch the corpse?

> Not forgetting that Norton Commander is a DOS product that probably still runs A-OK on Vista... It will not do long filenames though... 

Are you seriously suggesting a Windows product which does not support long file names? Should I llaugh or cry? And i found couple of NC closes what promise to run on Win up to 95. Would you seriously suggest using them? 

> As far as command line file managers, both Linux and Windows are well supported.

On Linux: supported and maintained code. On windows: dead links and obsolelete code - and yes I forgot: suported by FUD propaganda about Windows superiority.

Thank you, cunawarit. With your help, **Superioty of free software development model was proved** beyond reasonable doubt - at least in my mind. Apparently developers don't use proprietary tool unless they are forced and paid to use them - they prefer free tools otherwise. QED.

Of course companies love proprietary software. Developers are not interested in running in Windows version upgrade treadmill. They abandoned working products, left users stranded. Business as usual in world of proprietary software.

---

### Post by cunawarit on 2007-03-19
> **pmasiar said:**
> 
Thank you, cunawarit. With your help, **Superioty of free software development model was proved** beyond reasonable doubt

I really can't see what you are arguing about? I personally DO prefer Open Source software. Hence me using it, and actively promoting it. 

If there is a free tool that is as good as I need it to be, I will choose the free tool every time. 

But if you expect me to rubbish all proprietary software, sorry I won't do that. I do use plenty of proprietary software too, and in my opinion it is great! The aforementioned Visual Studio 2005 is one of them, I have a HUGE list of issues I have with it. But none of the ones you mentioned.

As for the Norton Commander clones, I don't see what the argument is... So it is safe to say you won the argument, because I don't know what it is...

On a separate note, chill... I don't understand what your confrontational attitude is about, everyone you talk to here is already an Open Source software user. Some exclusively, some not. There's no point in antagonizing the very same people that use the products you so believe in. If I have offended you, I'll apologize. But all I was trying to say is that your system requirement claims for Visual Studio 2005 were false, because they are.

---

### Post by j_g on 2007-03-19
> I don't understand what your confrontational attitude is about

It's because you had the unmitigated gall not to dismiss everything associated with Windows as demonstrably inferior to, and useless compared to, Linux stuff.

Shame on you.

> your system requirement claims for Visual Studio 2005 were false, because they are.

What you'll discover from the fanboys here is that accuracy is irrelevant when they're "advocating". And BTW, you need to realize that they're all absolute authoritities on everything, especially anything to do with Windows, because don't you know that the only people who really know anything about Windows are people who use Linux all the time. Makes sense, doesn't it?

---

### Post by cunawarit on 2007-03-19
It has to be said that it goes for every OS, there is favouritism on all front.

---

### Post by bfree on 2007-03-20
> **Tomosaur said:**
> You've made FOSS less profitable because you charge so goddamn much for software.

Not sure who this was directed at.  As indicated earlier, I develop for both Windows and Linux environments... my FOSS code runs on both.

When my customers prefer OpenSource platforms, I use the tools appropriate for that environment.  When my customers prefer Windows, I develop Windows-specific solutions.  When I develop my own code, I make it portable across both.

I know many developers choose to avoid MS platforms, tools, and customers - and I respect their choices.  However, I don't understand why so many people get worked up when they encounter a developer that choses to work (in part or exclusively) with Windows.  Diversity is a good thing :)

---

### Post by j_g on 2007-03-20
> You've made FOSS less profitable because you charge so goddamn much for software.

Ah, the impeccable logic of fanboy advocacy. Here, we have people "advocating" that all developers should work for free (ie, what the "F" in FOSS means) so that these other people can make a bigger profit off of our work. How could any developer pass up a deal like that?

P.S. You don't happen to be an SCO executive, do you?

---

### Post by Tomosaur on 2007-03-20
> **j_g said:**
> Ah, the impeccable logic of fanboy advocacy. Here, we have people "advocating" that all developers should work for free (ie, what the "F" in FOSS means) so that these other people can make a bigger profit off of our work. How could any developer pass up a deal like that?

P.S. You don't happen to be an SCO executive, do you?

I am not a 'fanboy' - I just don't like being anally raped for products, much like any reasonable person. In any case, I think you're a little confused here. Apologies if I misunderstand you:

> 
Here, we have people "advocating" that all developers should work for free (ie, what the "F" in FOSS means) so that these other people can make a bigger profit off of our work.

Developers who work 'for free' (as in, don't receive a wage) do so at their own choice. Nobody is FORCING them to do it. It's not slave labour, they can do as much or as little as they want. Developers who work ON free (as in freedom) software, again, do so at their own choice. There are companies which are for profit, who make FOSS software. FOSS software is not limited to freeware. If they don't like it, they can leave the company, or leave the project, or whatever. There is absolutely no cajoling or arm-twisting involved. If you don't like FOSS, then don't contribute, it's as simple as that.

I am in no way advocating that ALL developers should work 'for free' (regardless of whether that means freedom or price). What I am saying is that software which is not free (in either respect) and popular, is frequently very, very highly priced. This makes the FOSS development model less profitable not because people expect it to be free as in freedom or free as in price, but because FOSS developers generally do not slap a massive markup on to their software. The price of propietary software is frequently completely out of touch with quality or supply, it is highly priced just because those who decide such things **want to charge a high price for it**. I'm not saying, nor have I ever said, that propietary development is 'bad', or 'wrong', but that I think FOSS development **is right, and fair, and better** than propietary. That is called an opinion. It doesn't make me a fanboy, and I don't think it warrants such sarcastic criticism.

So, to clarify:

FOSS is less profitable not because FOSS software is of a lower standard than propietary products, but because propietary products have far too high a price tag in relation to their quality, availability, and development time. 

The perfect example is Photoshop. The GIMP has MANY of Photoshop's features, and some that PS doesn't have, yet charges nothing. I am not saying that this means that PS is worthless, or anything like that, but it certainly leaves Photoshop's pricetag with a big question mark over it.

I do not for one minute propose that Adobe should suddenly give away Photoshop for free, like the GIMP. It is entirely within their rights to sell Photoshop for whatever price they see fit. However, the high price tags surrounding propietary software indirectly causes development for FOSS software to be less profitable and worthwhile (from a developer's stand-point, obviously), not for technical reasons, or for a lack of sales, but because the developers are used to charging lots for their work. I don't agree with it, but it's not illegal, and I don't really care one way or the other. I will continue using FOSS software, and developing my own little tidbits under a free licence (not necessarily GPL, but whichever licence I see fit), and you will continue using propietary software. I don't like paying high prices, you don't mind. Such is life.

And no, I am not an SCO executive, but I am increasingly wondering whether you work for MS or some other company.


@bfree -

It wasn't aimed at anyone in particular, it was just a rant.

---

### Post by pmasiar on 2007-03-20
Somewhere I read about "Denied commonality": experts in some area love to argue about subtle differences, skipping over what thay agree on. To avoid this, I want to state that I agree with Tomosaur 99%, except little juicy details of course :-)

> **Tomosaur said:**
> There are companies which are for profit, who make FOSS software. FOSS software is not limited to freeware. (...)
FOSS is less profitable not because FOSS software is of a lower standard than propietary products, but because propietary products have far too high a price tag in relation to their quality, availability, and development time. 

Some interesting areas where FOSS is trying to compete with extremely expensive proprietary software is on the other and of the price spectrum: [Compiere](http://www.compiere.org/erp.html) is [Enterprise resource planning](http://en.wikipedia.org/wiki/Enterprise_resource_planning) system, competing with giants like SAP and ORACLE. SAP implementation price may *start* at couple hundreds of thousands dollars, and easily goes to millions, and takes many many months to implement.

Compiere is GPL, code is free, expertise to implement and configure it properly is paid service.

> I am increasingly wondering whether you work for MS or some other company.

At [http://planet.ubuntulinux.org/](http://planet.ubuntulinux.org/) I noticed link to website which proves how afraid Microsoft is  of free software: [Linux Personas website](http://www.linuxpersonas.com/). Looks like "Get the facts" fud campaign is faltering, not enough people believe the crap, so MS has another marketing idea: sort out different Linux (~= free software) users to groups and prepare anti-Linux FUD arguments customized for each group (== persona). If MS is using [Know Your Enemy](http://en.wikipedia.org/wiki/Know_Your_Enemy_(disambiguation)), we should know what they think they know :-)

To have more fun responding to anti-Linux FUD, next time I may consider checking which "persona" FUD is used, and if FUD does not stray off the script.

BTW "Personas" website proves beyond any doubt that MS takes free software very seriously, is scared like hell and mostly lost about what to do -- and that plan for the world domination of free software is still in progress, doing fine. 
 
For people who did not read [Halloween documents](http://en.wikipedia.org/wiki/Halloween_documents) yet, follow the link. MS in internal documents understands what FOSS is, and why it will destroy their business model - their own developers said them why and how. FUD is only for users.

---

### Post by j_g on 2007-03-20
> the developers are used to charging lots for their work. I don't agree with it

And after your "thorough" analysis of Photoshop, how about if you break down the numbers for us to show us how you came to your conclusions? Tell us the average salaries of the Photoshop developers, versus how much you _think_ that they should earn, based upon all current expenses and income of Abode.

I'd really like to know upon what basis you self-proclaimed FOSS folks are determining the value of software, as well as what your definition of "fair" entails (or excludes).

Apparently, it boils down to "if some guy decides to freely give me something he does in his spare time as a hobby, then that means it's unfair that anyone else should expect me to pay for anything under any circumstances, even if that's his livelihood.".

You know, I hear lots of people making noise about "supporting FOSS", but how many of you have even contributed one damn cent to someone who has given you what you have? You come home from your own paying job, greedily clutching your paycheck in your hand (or worse, you're a college student at some publically funded institution, getting handouts from mom and dad), and then you download Ubuntu for free, from a server that makes it available to you for free, run synaptic to download all your software free, and log onto a free forum to go on about how awful it is that other people are trying to make a living writing software.

Mind you, I'm certainly not against free stuff. In fact, I've written, and continue to write, lots of free software. But I've had enough of you freeloaders who get something for free and therefore conclude that its value is 0. Here is what's fair. How about you come over to my house and clean my bathroom for free? How about washing my car for free? How about mowing my lawn for free? How about you go to work and tell your boss, "You don't have to pay me anymore. I'm going to volunteer just like all the other people whose stuff I'm using for free, and pass on the savings to those people.". How about if you tell your boss about how unfair it is that you and him are making money when there are charitible organizations all over the world doing stuff for free? Where's your conscience and righteous indignation when it comes to _you and your kin_ charging for doing something? When the hell are the FOSS flag wavers going to start giving _us_ something for free? (And no, the "Microsoft is evil" grandstanding ain't worth crap to me. If I want to hear empty polemisizing, I'll switch the TV to some televangelist).

---

### Post by Wybiral on 2007-03-20
> **j_g said:**
> You know, I hear lots of people making noise about "supporting FOSS", but how many of you have even contributed one damn cent to someone who has given you what you have?

Thats a large part of the point... Most FOSS developers are working on projects they like because they don't have to work on it if they don't want to...

Anyone who is helping with FOSS development is contributing back to the community as a whole. No need for money.

I contribute with every line of code I write for any FOSS project because future FOSS developers can use my code to make their lives easier.

Start looking at it from a community perspective, not an individual perspective.

Also, people still make money hosting and advertising, so it's not exactly 0% profit. And the projects that people really enjoy do make money from donations.

---

### Post by Tomosaur on 2007-03-20
> **j_g said:**
> And after your "thorough" analysis of Photoshop, how about if you break down the numbers for us to show us how you came to your conclusions? Tell us the average salaries of the Photoshop developers, versus how much you _think_ that they should earn, based upon all current expenses and income of Abode.

I'd really like to know upon what basis you self-proclaimed FOSS folks are determining the value of software, as well as what your definition of "fair" entails (or excludes).

Apparently, it boils down to "if some guy decides to freely give me something he does in his spare time as a hobby, then that means it's unfair that anyone else should expect me to pay for anything under any circumstances, even if that's his livelihood.".

You know, I hear lots of people making noise about "supporting FOSS", but how many of you have even contributed one damn cent to someone who has given you what you have? You come home from your own paying job, greedily clutching your paycheck in your hand (or worse, you're a college student at some publically funded institution, getting handouts from mom and dad), and then you download Ubuntu for free, from a server that makes it available to you for free, run synaptic to download all your software free, and log onto a free forum to go on about how awful it is that other people are trying to make a living writing software.

Mind you, I'm certainly not against free stuff. In fact, I've written, and continue to write, lots of free software. But I've had enough of you freeloaders who get something for free and therefore conclude that its value is 0. Here is what's fair. How about you come over to my house and clean my bathroom for free? How about washing my car for free? How about mowing my lawn for free? How about you go to work and tell your boss, "You don't have to pay me anymore. I'm going to volunteer just like all the other people whose stuff I'm using for free, and pass on the savings to those people.". How about if you tell your boss about how unfair it is that you and him are making money when there are charitible organizations all over the world doing stuff for free? Where's your conscience and righteous indignation when it comes to _you and your kin_ charging for doing something? When the hell are the FOSS flag wavers going to start giving _us_ something for free? (And no, the "Microsoft is evil" grandstanding ain't worth crap to me. If I want to hear empty polemisizing, I'll switch the TV to some televangelist).

Again, I don't quite know what the hell you're talking about - you're just picking out random sentences and applying to them your very own little special meaning.

> 
And after your "thorough" analysis of Photoshop, how about if you break down the numbers for us to show us how you came to your conclusions? Tell us the average salaries of the Photoshop developers, versus how much you think that they should earn, based upon all current expenses and income of Abode.

I'd really like to know upon what basis you self-proclaimed FOSS folks are determining the value of software, as well as what your definition of "fair" entails (or excludes).

Apparently, it boils down to "if some guy decides to freely give me something he does in his spare time as a hobby, then that means it's unfair that anyone else should expect me to pay for anything under any circumstances, even if that's his livelihood.".

If you had bothered to read my very last post (the one you just quoted), you would understand that:

1) I am not against people charging for software. I have ABSOLUTELY. NOTHING. AGAINST. PEOPLE. WHO. CHARGE. FOR. SOFTWARE. I hope that's clear enough.

2) I **am** against extortionate prices for software. Now, obviously, what is deemed a high price is subjective. What I do know, however is that:
a) The GIMP is free.
b) A single licence to use Photoshop STARTS at [£569.88](https://store2.adobe.com/cfusion/store/index.cfm?store=OLS-UK&view=ols_prod&category=/Applications/Photoshop&nr=0).

Now, whether that price is 'high' will be determined based upon your circumstances. I am a student (and not one which relies on my parents for financial backup! Imagine that!), and I count myself pretty damn lucky if and when I can afford ANYTHING more than £100, so obviously, Photoshop is taking the piss, for me, in my circumstances.

Note, however, that this is **only** Photoshop. If I want to do other stuff, I can buy the 'Adobe Creative Suite Standard' which is a bit less than double the price of Photoshop. Obviously, I am not going to be buying Photoshop any time soon.

Now, you seem to be confusing my argument by saying something about salaries and whatever. I have not argued any position on this at all. I have said that high prices for the end-user on propietary software, make FOSS environments, and thus FOSS development, less profitable. If you don't understand that, go back and read my last post, where I **thought** I had explained why this is so. I have no position on developer salaries. That is for each individual company to decide. It has no bearing on any of my arguments so far. What I do know is that the GIMP is free, whereas Photoshop, which the GIMP is more or less comparable to, would cost me more than I can conceivably afford at this point in my life. Clearly, the GIMP is not costing the developers an unreasonable amount to develop it, otherwise they **would be charging at least something for it**. The fact that they have subsisted entirely on donations so far certainly shows that it can be done.

Now, of course, we have to factor in the scale of development. The GIMP probably has far more developers working on it than Photoshop does, and it doesn't have all of the 'invisible' costs that propietary development entails, so it's only reasonable to assume that this would drive down development costs. Adobe **could** create the same situation by open-sourcing Photoshop. I know for a fact that many Linux users **want** photoshop, so there'd certainly be at least some market for it, regardless of whether or not it would match the sales experienced on Windows / Mac.

Your position though, is both misguided and pretty insulting. I do not 'owe' the FOSS developers anything. They have made their products free to use to me out of their own free will. I'm not depriving them of any income. I **am** extremely grateful to the developers for this, and I like to think I at least somewhat express my gratitude through thanks / filing bug reports / making small donations (when I am able to - remember, to say I live on a budget would be to overstate my current financial situation). In the same sense, FOSS developers do not 'owe' me anything, nor do I demand anything of them. I have not entered into some legally binding contract whereby they have to give me support, or upgrades, or anything of that nature. Ubuntu could disappear from the face of the earth tomorrow, and I wouldn't feel put out. I have had a 'good thing' - and it would be foolish to take it for granted.

That being said - stop being such a self-righteous idiot. I have not **once** said free = 0 value. You seem to be plucking accusations out of your backside, and, to be honest, you're getting pretty predictable. I don't think you will find anybody here who has said, or WOULD say, that free things are worthless. I haven't even said that PROPIETARY things are worthless. I just don't think that many propietary things are worth the price tag. If you think it's fine for manufacturers / developers to just charge whatever the hell they feel like for something, then be my guest - but don't come crying back here when you realise that civilisation has only gotten this far because people just **do not do that**. There needs to be moderation, and charging £600 for something which is 'more or less' available for free just does not fit that bill.

I will repeat this one last time:
[B]I am not against paying for software.
I am not against developers charging for software.
I am not anti-capitalist.
I am not a freeloader.[/B]

It is not 'freeloading' to look at two comparable products, and then go for the free one. It's just common sense. Would you rather I just bought the expensive one out of sheer brand loyalty or something? That is an idiotic position to to take. If anything, you should be grateful for many FOSS products being completely free (as in price). It is the ultimate form of competition, and it SHOULD engender innovation and competition (and, ultimately, more competitive prices). The reason it is not currently doing so is because people like you have some misguided view that things should be bought wherever possible. If I had two identical cakes, and offered you both, which would you choose? The one which is free, or the one which I slapped some outrageous price tag on, say, £5,000,000. I had to bake them both, so I put equal amounts of effort into them. Will you give me £5,000,000 for a cake, or will you be a reasonable person, and recognise that no cake I could bake is worth that kind of money? That is the situation we're talking about here. I'm not going to pay £600 for an image editing software that is not astoundingly better than the image editing software I can get for free. Are you a complete idiot, or can you finally recognise the point I am trying to make? Your last paragraph is so outrageously off the point that it's laughable. I am not going to wash your car for free, and the metaphor is completely wrong. I do not **want** to wash your car. FOSS developers **want** to create new products. You seem to be of the perception that any kind of development has to be for profit or some other gain. Can't people just develop because they enjoy developing, or they personally want to use the product they are developing? Is that so ******* alien to you that you need to come here and lambast everyone who has an opinion different to yours?

---

### Post by ZDemon on 2007-03-21
Flamewars. I like Beast Wars, Warcraft and God of War better, but don't have the time anymore these days.

To all the flamethrower wielding guys/trolls who posted :
> Bla bla bla. Bla bla, bla bla bla bla.....I like nuts...

Reply : [O rly?]("http://www.orlyowl.com")

[http://www.orlyowl.com](http://www.orlyowl.com)

Is this all really necessary.

You guys scared the forum poster away.

He probably asked the question here because most Linux programmers have experience programming in Windows. Most Windows programmers, on the other hand, don't have Linux. Thats all.

My opinion is its time somebody locked this topic.

---

### Post by j_g on 2007-03-22
> He probably asked the question here because most Linux programmers have experience programming in Windows.

Well, if the comments/advice about Windows programming, and especially Windows dev tools, of some of the folks I've identified around here reflect that "experience", then that experience is not to be trusted. I'm absolutely convinced that certain people who claim to have "experience" writing Windows software, couldn't write their way out of the cardboard box that Vista ships in.

I still say that the best place to get information about Windows is _not_ from a Linux site. That's the _worst_ place to get information about Windows. The proper place to get Windows programming info is a site like CodeProject, which has established its credentials at supplying good, detailed, peer-reviewed, professionally presented info about Windows programming. Ubuntu's forums have no such established credentials, and indeed, the presense of too much fanboy anti-everything-associated-with-Windows-and-MS flag-waving, such as seen earlier in this thread, strongly suggest that the main intent is advocacy rather than accuracy. You don't find that crap at CodeProject for good reason. Those are serious Windows developers over there.

Personally, I think that Ubuntu forums should stick exclusively to Linux (because they don't seem to engender much useful nor accurate information about Windows and other operating systems), and the moderators shouldn't even allow mention of Windows and Microsoft on any Ubuntu forum (unless it's for the purpose of discussing the incorporation of Windows/MS features into Linux). For example, this here thread should never have been allowed to start, and I think it should be deleted entirely.

---

### Post by lnostdal on 2007-03-22
lol @ j_g

---

### Post by j_g on 2007-03-22
> propietary products have far too high a price tag in relation to their quality, availability, and development 

time.

The perfect example is Photoshop.

the developers are used to charging lots for their work.

After your above comments, I asked you to break down the numbers for us to show us how you came to your conclusions about the "too high" price of Photoshop in terms of development time and effort (not to mention the other costs of manufacturing and marketing a product). I said "tell us the average salaries of the Photoshop developers, versus how much you think that they should earn, based upon all current expenses and income of Abode". I had suspected that you considered the value of a programmer's time to be 0 dollars (or close to it), which appears to be an increasingly common perception among Linux enduser's just because they start up Synaptic and download all of their software for free. (ie, "Hey, all these developers give me their stuff for free, so therefore a developer's time and energy can't be worth much money. And since their time and energy isn't worth much money, then they should all be working for less than minimum wage so that a college student like me can afford all their stuff").

You follow up with:

> I am against extortionate prices for software.
A single licence to use Photoshop STARTS at £569.88.
I am a student, and I <can't> afford ANYTHING more than £100

So there it is. Your rationale for why Photoshop is "priced too <extortionately> high in relation to their quality, availability, and development time" is because you don't have the money to buy it. In fact, it has nothing to do with the quality, availability, or whether the developers earned their money, but rather, because they aren't giving it to you free (or for a pittance) like the authors of the Gimp.

I hope you realize how distasteful your attitude is to developers. This sort of advocacy is _not_ going to make developers want to program for Linux. It's totally counter-productive.

---

### Post by Wybiral on 2007-03-22
You know what... I am not a Windows programmer. That's where I learned to program, but I much-much-MUCH prefer Linux for development. You can bash the tools all you want and praise MS tools all day, half of them aren't even necessary or essential for real productivity if you're good at what you do.

But my point, over-all, is this... Tools are just tools. Who are you to say that one is better for everyone or that one will make everyone's life easier? Because I CAN say, for certain, that Windows development tools will not make my life any easier.

So, accept the fact that Windows dev tools are NOT superior at all, and neither are Linux dev tools.

Windows tools are for one targeted platform with almost 0% support for anything else. If that's all you care about, fine... Go frolic in your MS world.

But for those of us looking to write portable code MS tools are an absolutely TERRIBLE idea.

Here's a little hint if you're wondering why there is so much "MS tools suck" attitude around here... Most of the developers here want to write portable code. They don't want to program for a platform that they don't use... Using non-MS tools gives you that ability. You can write code that will compile on either platform, and why wouldn't you?

So... You've came to a LINUX forum preaching against FOSS and in favor of MS and you're wondering why people are opposed to your beliefs???

---

### Post by j_g on 2007-03-22
> I am not a Windows programmer.

Fair enough. I have no problem with that, as long as you don't try to give advice to people wanting to write Windows programs. What I don't care for is people (like pmasiar and lnostdal), who do not have adequate experience with Windows programming, attempting to tell people how to write Windows software. They should be directing people to more authoritative sources, such as CodeProject.

> Who are you to say that one is better for everyone or that one will make everyone's life easier?

I never said anything was better for everyone. That's not a quote I would even make. I very much believe that software that tries to be everything to everyone is doomed to be not very useful to no one in particular. I've said that before. It sounds like you're attempting to read your own incorrect interpretation into my messages.

But perhaps you should be asking, who are these people like pmasiar to say that products made by MS are terrible? Perhaps it would be best if the moderators didn't allow _any_ discussion of Windows and Microsoft if people don't want to hear dissenting views of their "MS/Window is evil" mantra. (Frankly, I think that would be best because I personally saw misguided advocacy ruin both the Amiga and OS/2. It looks like those misguided advocates have moved on to Linux and plan to ruin that too by doing things like telling software developers that they're not even worth earning minimum wage. Yeah, that's a great way to get people to write Linux software).

> You can write code that will compile on either platform, and why wouldn't you?

That's another entirely different topic than the one discussed here. In fact, a lot of your discussion is entirely irrelevant. Look at the OP. He asked whether it was easier to write Windows or Linux software. Who said anything about cross-platform anything? I simply urged the OP not to ask about Windows programming here, because I have found that certain people have misrepresented their experience, and are giving bad/incorrect advice, favor advocacy over accuracy, and that if he wants to know anything about Windows programming, he should seek advice from a more reputable Windows programming site like CodeProject. I stand by this advice.

> You've came to a LINUX forum preaching against FOSS and in favor of MS

No, I came to this forum because I decided to start writing Linux software. I was horrified to see certain fanboys, who seem to have absolutely no experience in lots of the things they're discussing (Windows programming, the business of selling software, etc) engaged in the same sort of misguided advocacy that ruined the Amiga and OS/2. I already went through all that. I don't want to have to suffer these fools again, and frankly, neither does the professional world. For example, no software company wants some unemployed college kid telling all about how that company is an "extortionist" because it isn't selling its software at a miniscule cost so the kid can afford it. And if they're using MS/Windows tools, they're going to take a very dim view of some fanboy who says that all the stuff they're using is garbage. They aren't going to go near anything that has this sort of fanaticism around it.

---

### Post by lnostdal on 2007-03-22
lol .. right .. one need codeproject and its vc++ for writing, well say - a friggin opengl-screensaver for win32 for instance .. :rolleyes: .. 

(i'm referring to a previous discussion with absolutely no connection to the "real world" in any sense ..  i haven't bothered reading this thread but it seems the exact same thing is going on here .. said discussion lead to me "stealing" (an attempt to lead the discussion in another direction) an opengl-example and porting it to win32 to show how _easy_ and totally _trivial_ this is with no need for vc++ or ...bah ... i can't believe i'm stupid enough to be bothering with this again ... anyways, here: [http://ubuntuforums.org/showpost.php?p=2285826&postcount=28](http://ubuntuforums.org/showpost.php?p=2285826&postcount=28) ..edit:  j_g has also in another thread instantly told a newbie that KDevelop and linux-tools in general are unusable because he was not able to figure out where Project -> New Project in the menus where )

you see; what are we _actually_ talking about here? what is the _problem_ we are trying to solve? is there _anything concrete_ going on here? .. is there some kind of interest in solving an _actual problem_ here? c'moon .. indulge us!

..if not, i'll draw back into the shadows and ignore your foolish and pointless rant - reaping all the benefits of that..

..but.. i _will_ however report you if you continue spreading FUD like this .. it isn't hurting me (besides being totally annoying and tedious ofc.) because i already know that it is FUD .. but other less fortunate readers might not be aware of this - and we can't have that..

i'm gonna quote from something i said in the thread i linked to above:

[quote=lnostdal]
You add nothing to this discussion or even this forum, j_g. You do not belong here because while using MS tools, asking questions about them or even recommending them (when nothing else is possible or feasible) is OK. It is _wrong_ to promote them while saying real alternatives _do not exist_ in the consistent way you are doing here and in many other threads when the Linux/GNU-options will do _absolutely fine_ and are _very good_ and thus "exist" in a practical context or manner also.

You are in all ways in a _direct_ opposition of the Ubuntu, Linux and Open Source/Free Software movement .. and also me and just about 100% of all the other members on this forum by doing this. You are _directly_ provoking, insulting and hurting this community with your FUD. I strongly suggest you find another place to play your war-, FUD- and trolling-games.

..if this is not ultimately enforced upon you, then this is _not_ the kind of inconsistent forum/community I want to be a part of - and .. yeah, either _you_ change, or leave .. or _I_ leave. It's up to you; I can pretty much already predict what the community will prefer.
[/quote]

---

### Post by pmasiar on 2007-03-22
> **j_g said:**
>  you should be asking, who are these people like pmasiar to say that products made by MS are terrible? 

I am a programmer who moved from RSX to MS DOS to Windows to Linux and now back to Windows. I used many many tools in my life and i stand by my *opinion* that VS for VB sucks badly. Cannot say VS for C#, never used it. You do not have to agree with my opinion, I do not agree with yours. If a developers asks my opnion, I tell. I use java/Windows in my day job, and learning Linux and Python in my free time and fun projects in job, if I have opportunity. I believe that many programmers are exactly in situation like I am, and they can relate, and my advice is relevant to them. And I am trying genuinely to help, maintaining [http://learnpython.pbwiki.com/](http://learnpython.pbwiki.com/).

Who are you, j_g? You said you created loads of free software, but you know very well that any dog can claim to be human on internet, so IMHO is it BS. Show us some links you did to contribute to the community, or stop pretending. Sometime I agree with you and often I do not. Are you paid to astroturf for MS and to promote other forums? Well of course you will not tell the truth now, but it is funny to compare some of your posts. Looks like sometime your evil twin takes over and posts in your name... :-) Looking forward for another of your rants in response. :-)

> Perhaps it would be best if the moderators didn't allow _any_ discussion of Windows and Microsoft

Why you think you are in position to decide what questions other people are allowed to ask in this forum? Or are you trying to poison the atmosphere in this forum so people will leave? I hope not.

---

### Post by samjh on 2007-03-22
This thread is the most ridiculous I have ever seen in this forum.

Why does a simple question turn into such a flame war as this?  A rational answer such as: "use Linux for Linux development and Windows for Windows development", could have done the job, but no...

Lessons learned, for me at least:

1. Do not ever start a discussion comparing or contrasting Windows and Unix/Linux software.

2. If voicing perfectly legitimate, and positive opinion about Microsoft software, be prepared to get a virtual stoning.

~sigh~

As for the question itself, I will leave my already-posted answer, untouched.

Quite a disappointment, this thread.

---

### Post by pmasiar on 2007-03-22
> **samjh said:**
> This thread is the most ridiculous I have ever seen in this forum.

you are not here for long, are you? I remember worse flamewars :-) - I even participated in them :-)

> Why does a simple question turn into such a flame war as this?  

1. Do not ever start a discussion comparing or contrasting Windows and Unix/Linux software.

People will ask those questions, and express opinions. Better be prepared to apologize and forget what was misunderstood in haste of battle. Mistakes happen, experts like to pinpoint 3% where they disagree, and not 97% where they agree, so for non-experts it might look like they totally disagree when they do not.

> 2. If voicing perfectly legitimate, and positive opinion about Microsoft software, be prepared to get a virtual stoning.

it is not a problem to say "I prefer this MS solution". It is very different from saing "if you do not agree with me promoting MS, you are misinformed fanboy and linux kook". First is opinion, second is challenge to a fight. And yes, many people here have obviously bias for free software, for a reason. Would be foolish to expect something different, no?

---

### Post by Wybiral on 2007-03-22
> **pmasiar said:**
> Who are you, j_g? You said you created loads of free software, but you know very well that any dog can claim to be human on internet, so IMHO is it BS. Show us some links you did to contribute to the community, or stop pretending.

I agree... I've seen you say how you've written all of this helpful driver stuff for Linux (and a toolkit library for that), and then you said that you disassembled mingW and found a bug (when arguing that GCC was inadequate for MS dev in the "command line vs ide" thread)

I'm not saying you aren't a good programmer, I'm just saying that I would take you more seriously if I believed you.

The Mods don't need to filter MS talk on the forum, people need to be smarter about where they ask their questions. Being able to learn on your own is an essential skill for any programmer, and clearly it is a mistake to expect MS help on a Linux forum.

---

### Post by ZDemon on 2007-03-22
Serious Sam is also nice. War everywhere. You get to be a solo hero fighting for your life.

J_G aka John Rambo got lucky and picked up a turbocharged electrified nitro juiced flame thrower and screamed : 
> Bla bla bla windows bla bla bla bla bla bla bla. Bla bla bla bla.......... Ya rly.

Reply : o rly?

[http://www.orlyowl.com/](http://www.orlyowl.com/)

Why are you wasting so much of your time. What on earth are you trying to accomplish? Do you want all of us to remove Linux?

Ok ok you win. Im going to uninstall Ubuntu and get Vista.
Im going to miss Glade, cairo, GCC ..... :(
Im going to throw away GIMP. It was great, but you've changed my mind.
Goodbye sweet Beryl. It looked good. My girlfriend is going to scold me for this, but Ill show her Vista.
Im going to my closet, see if i still have MS VC++ 6.0. MFC was good. Got to polish back my skills.
Drivers was so easy to write..... NO!!!! MS SDK!!!! NO!!!!

:( 

You have crushed my fragile little mind. Thats what you wanted all along right?

:cry:

---

### Post by j_g on 2007-03-22
> j_g has also in another thread instantly told a newbie that KDevelop and linux-tools in general are unusable because he was not able to figure out where Project -> New Project in the menus where

Lying about what others have said again, I see. I've never used KDevelop.

---

### Post by samjh on 2007-03-22
> **pmasiar said:**
> you are not here for long, are you? I remember worse flamewars :-) - I even participated in them :-)Obviously. ;)

The problem is, threads like this do nothing to promote Linux.  It only portrays Linux users as blabbering zealots.

I do not know j_g or yourself, or any other people here at a personal level, so I presume nothing.  All I can see is that j_g obvious likes his MS products, and has made rational rebuttals to some of the posts against him, despite his snide initial post.

> People will ask those questions, and express opinions. Better be prepared to apologize and forget what was misunderstood in haste of battle.Ah, but I see no apologies forthcoming from any party here.  Care to state what the misunderstandings are between MS advocates like j_g, and FOSS advocates such as yourself, among the posts in this thread?  Perhaps that will start the ball rolling.

> Mistakes happen, experts like to pinpoint 3% where they disagree, and not 97% where they agree, so for non-experts it might look like they totally disagree when they do not.But it seems the other round for j_g and others.  Disagreements appear to be 97% and agreements only 3%, unless you wish to elaborate, establish some common ground, and discuss the topic like experts should. :)

All of this has nothing against you in particular.  It's just that whenever any discussion is made of Windows vs Linux, flamewars tend to follow, even though there is no reason why it should always be that way.

---

### Post by j_g on 2007-03-22
> I've seen you say how you've written all of this helpful driver stuff for Linux

I've never said such a thing. (Where do you folks get all of these supposed quotes. Are you using a browser that mangles text???). First of all, I've never written a linux device driver. Secondly, I've just started writing Linux stuff, and have completed one project. I'm currently working on a second, much larger project.

On the other hand, I have plenty of Windows programming experience (as well as writing tutorials about such), and that's why I know that some of the things I've read about Windows around here are from people who lack adequate experience to be discussing it (and are misrepresenting their experience in some cases).

> you said that you disassembled mingW

Again, I said no such thing. I said that I disassembled the "GUI designer" tool shipped with it.

> I'm just saying that I would take you more seriously if I believed you.

I very much doubt that certain people would take anything seriously if it has even a remote, non-negative association with anything to do with MS Windows.

> The Mods don't need to filter MS talk on the forum, people need to be smarter about where they ask their questions.

That's _exactly_ why I said that all questions about Windows programming should be posted at a web site that has proven its value regarding such, like CodeProject and many, many other good Windows sites -- not here. There are no fanboy flamewars over at CodeProject. There isn't even any need for moderators to guard against such. Those are serious, experienced Windows programmers over there, and the advice/discussion about Windows programming you get there reflects that. When you go there, you definitely do not get the impression that every question you ask about Windows is going to attract Linux fanboys who hate MS and everything associated with Windows. Why would a Windows programmer want Windows advice from such a person anyway?

It serves no purpose having such people discussing Windows and MS on a Linux site, except to reinforce the idea that there is fanboy fanaticism there. And no professional wants to get near that. It's _totally counterproductive_.

---

### Post by j_g on 2007-03-22
> threads like this do nothing to promote Linux. It only portrays Linux users as blabbering zealots.

Exactly. Actually, threads like this _dissuade_ people from using Linux. Believe me, I've seen the effects of fanboy fanaticism firsthand when those folks helped kill the Amiga and OS/2. It doesn't work (unless your intent is to kill what you're advocating).

> Disagreements appear to be 97% and agreements only 3%

That's to be expected. It's a Linux site. Wybiral himself has said as much.

And that's _why_ it's a bad idea to be discussing MS and Windows around here. Anyone who has had any experience with non-Linux sites will instantly recognize the taint of fanboy fanaticism when the discussion turns to MS and Windows, and be instantly turned off. It's not like they're going to say "Gee, after all of these years of developing Windows software, in conjunction with my interaction with Windows programming sites, only now do I realize that everything I know about Windows programming/tools/etc is all wrong thanks to some Linux programmer telling me so". That ain't gonna happen.

> It's just that whenever any discussion is made of Windows vs Linux, flamewars tend to follow

Here, that is true. There are no such flamewars on sites that are more appropriate venues for getting information about Windows programming. That's why the mods should enforce Linux discussion only, and people asking about Windows should be redirected to more appropriate sites.

---

### Post by pmasiar on 2007-03-22
> **samjh said:**
> threads like this do nothing to promote Linux.  It only portrays Linux users as blabbering zealots.

or people easy to fall prey to clever troll post, and then defending their positions, feeding the troll even more.

---

### Post by psychicist on 2007-03-22
While this site is not a Windows programming site there is nothing wrong with people discussing how to get their initially Linux-based code running on Windows as well.

You seem to feel that many are very hostile towards you and you are being attacked for advocating the ease of use you are accustomed to from your Windows development tools.

But this is not the issue. Many including myself are very happy with command line tools as they seem not to hide the internals of what's going on in the compilation and linking stages. GUI tools tend to clutter the makefiles so they are harder to understand.

That's probably the difference. UNIX and therefore Linux is all about simplicity. Although some may prefer GUI tools there are always ways to do things from the console and most wouldn't want it any other way. I myself use Netbeans for Java and am learning to use KDevelop for C/C++ programming.

I was a Windows user once as well but nowadays I don't touch it at all. If I really need it I have a virtual machine running Windows XP SP2. Using Linux is all about using an alternative OS, not a Windows clone. It has really nothing to do with Windows or Mac OS X at all.

Maybe initially people that switch are showing their anger at years of Windows use while there was something better all that time. After a while when they get really comfortable with the UNIX system that feeling makes place for something very different.

You start thinking about how you can make the environment you're using better than it was before. Windows doesn't come to mind. I am very indifferent to Windows nowadays. I don't care what the previous, current or future versions are or will be. I don't use it.

But when it comes to a piece of software that someone wants to have written for Windows I will look into it and use the tools that are most productive to finish this task as easily as possible. Nothing wrong with that.

I still don't care about Windows. Improving it is Microsoft's job. I won't even test it for them. I have downloaded Vista Beta2 and RC2 to see what's changed. Nothing much. I don't have time to provide feedback for a system that I don't use.

I understand that many new Ubuntu users are very vocal when it comes to their current and former experiences. I can only ask you to forgive them for they don't know any better (yet!). With Linux they at least have the opportunity to become experts if they want to learn and without spending big bucks.

That doesn't mean they're freeloaders. I bought a few distributions in the past but nowadays I run my own that's totally adapted to my own wishes. It's Slackware based and I don't run Ubuntu. Still I think that we're all in the same boat. And BSD and Solaris users are very much part of this team as well.

I hope the discussion about Windows could come to an end because both it and discussion about it are irrelevant.

---

### Post by Wybiral on 2007-03-22
> **j_g said:**
> I've never said such a thing. (Where do you folks get all of these supposed quotes. Are you using a browser that mangles text???). First of all, I've never written a linux device driver. Secondly, I've just started writing Linux stuff, and have completed one project. I'm currently working on a second, much larger project.

On the other hand, I have plenty of Windows programming experience (as well as writing tutorials about such), and that's why I know that some of the things I've read about Windows around here are from people who lack adequate experience to be discussing it (and are misrepresenting their experience in some cases).

Again, I said no such thing. I said that I disassembled the "GUI designer" tool shipped with it.



OK, I remembered incorrectly, it wasn't a driver, but still:
[http://www.ubuntuforums.org/showthread.php?t=380796&page=4#39](http://www.ubuntuforums.org/showthread.php?t=380796&page=4#39)

Stop being to technical, you're escaping the point, you did say you disassembled a component of it, and that you found a possible bug. Did you even have the decency to contact them and report it? Where is this bug?
[http://www.ubuntuforums.org/showthread.php?t=364233&page=9#84](http://www.ubuntuforums.org/showthread.php?t=364233&page=9#84)

---

### Post by pmasiar on 2007-03-22
> **psychicist said:**
> That doesn't mean they're freeloaders.

IMHO spending money in not the only option how to give back to the community. Providing help in forums and email list is another one, and might be even more valuable. Even with minimal salary (if paid to forum members heling to solve problems) $5/hr - free help provided here will be rather expensive to pay for.

Helping new usersr, creating good community is as much important as writing code, IMHO. So you don't have to feel like freeloader if you are giving back time and not money.

---

### Post by pmasiar on 2007-03-22
> **j_g said:**
>  Believe me, I've seen the effects of fanboy fanaticism firsthand when those folks helped kill the Amiga and OS/2. It doesn't work (unless your intent is to kill what you're advocating)..

You demand exact quotes from others, but are very flexible when spreading misinformation about others. You in my place, if I would said something like your quote above, would claim that that's lie (and technically it is, because *I* never used OS/2 so I cannot "helped to kill it"). I just note for myself: yet another blabbering of that troll. Oh well.

---

### Post by Tomosaur on 2007-03-22
> **j_g said:**
> After your above comments, I asked you to break down the numbers for us to show us how you came to your conclusions about the "too high" price of Photoshop in terms of development time and effort (not to mention the other costs of manufacturing and marketing a product). I said "tell us the average salaries of the Photoshop developers, versus how much you think that they should earn, based upon all current expenses and income of Abode". I had suspected that you considered the value of a programmer's time to be 0 dollars (or close to it), which appears to be an increasingly common perception among Linux enduser's just because they start up Synaptic and download all of their software for free. (ie, "Hey, all these developers give me their stuff for free, so therefore a developer's time and energy can't be worth much money. And since their time and energy isn't worth much money, then they should all be working for less than minimum wage so that a college student like me can afford all their stuff").

You follow up with:



So there it is. Your rationale for why Photoshop is "priced too <extortionately> high in relation to their quality, availability, and development time" is because you don't have the money to buy it. In fact, it has nothing to do with the quality, availability, or whether the developers earned their money, but rather, because they aren't giving it to you free (or for a pittance) like the authors of the Gimp.

I hope you realize how distasteful your attitude is to developers. This sort of advocacy is _not_ going to make developers want to program for Linux. It's totally counter-productive.

Once again, perhaps you ought to read my posts before trying to make me sound like some ingrate. I will repeat this one last time, I am absolutely convinced you have suffered some terrible head trauma and are thus unable to comprehend a word I am saying.

1: Photoshop is expensive.
2: The GIMP is comparable to Photoshop, but free.
3: Why is Photoshop so expensive?

Do you not **understand a word of what I am saying?**. Are you telling me that you HONESTLY believe that Photoshop's price, or **any expensive product, for that matter** is designed only to cover costs? Is it really that hard to conceive that this is the case? It is not that I cannot afford Photoshop, it is that I don't believe that Photoshop is worth it's price tag. I was under the assumption that we were free to form and express our own opinins. Obviously that's not the case, but I didn't get your 'What to think and what to say' pamphlet in the post (perhaps you can send it out again? I think others missed it too).

Obviously, I have no figures, so your request for a full breakdown of Adobe's expensives must unfortunately be dismissed. I have not once said that developers of propietary software don't deserve pay. Of COURSE they do. I don't know why you're so damn adamant on putting words in my mouth, trying to make me look bad. I have said time and time again, **I HAVE NO OBJECTIONS TO PEOPLE SELLING SOFTWARE**. Yes, MAYBE Photoshop's price is an adequate reflection of the cost of development, but I simply do not believe that. Why is it so hard for you to perceive the flipside? And why must you resort to childish beratement just because I'm a student? Oh yes I forgot, it's because I use Linux so I must be an elitist! Don't fool yourself, j_g. The only elitist person in this discussion is you. If you're quite happy to accept any old price any company slaps on to their product, then that's your choice, but don't think I'm just going to accept you accusing me of being an ungrateful, greedy child.

I absolutely am grateful for the time developers put in to their products. If anything, I am much, much more grateful for the time put in by FOSS developers - who give their time for free, while very often juggling a professional career alongside that. My objection to obscene prices is not at all related to how I view developers. Developers in big companies like Adobe don't even set the damn price for their products, that's marketing's job, or at least a whole different group of people. I object just as strongly to incredibly inflated prices elsewhere. Perhaps you were born with a silver spoon in your mouth, or perhaps you crawled your way to your evidently oh-so-esteemed position in the face of unbeatable odds. Perhaps, to you, Photoshop's price is a drop in the water. To me, it isn't. In any case, Photoshop (and Adobe) was just an example that people can relate to. The situation is similar across many industries and with many companies and products. I'm not even saying that Photoshop is a bad product. I have used it before, and it is obviously good. However, if you are so blinded that you think prices everywhere are perfect reflections of the development cost, then I guess you must be right.

One **final** time:

1: I do not 'hate' or otherwise dislike developers simply because they charge what I perceive to be a high price for software. I **do** dislike being charged prices which are not an accurate reflection of cost. I believe that Photoshop is one such case. You are entitled to your opinion, I am entitled to mine. Don't call me an ingrate just because I don't want to pay the price.

2: Companies are designed to make money. I am not 'anti-capitalist'. I am very pro-choice, and pro-not-taking-the-piss. Refer back to the cake analogy please.

3: My distaste at massive price-tags is not a reflection on my perception of the creators of such products. I dislike the company for charging so damn much. I have no opinion on the developers - I just feel that the price-tag is unfair for products which many people depend upon. That is an **opinion**. I am not trying to prove myself right, or you wrong, I am just expressing my thoughts. If you don't like that, then don't let the door hit you on the way out. I don't 'hate the chefs' at expensive restaurants when I see that the quantity and quality of food is not astoundingly better than something I could get for much cheaper elsewhere. I don't hate the engineers who make cars which, from my standing at least, are not amazingly superior to other cars, yet charge 10 times as much for them. I'm not going to waste my time tracking down budgets and figures just to appease you - any sane person can make the same judgements as myself.

I'm done arguing this now - I can see that debating anything with you is a fruitless endeavour.

---

### Post by bfree on 2007-03-24
I've just posted benchmarks comparing OpenGL performance on Linux vs Vista -
[http://graphcomp.com/opengl/bench.html](http://graphcomp.com/opengl/bench.html)

There are rumors (unsubstantiated) that MS is intentionally degrading OpenGL performance to to better position Direct3D.

I take that with a grain of salt - but if true, it would be very disappointing to me as a cross-platform 3D developer.  Definitely tilts the scales toward Linux in terms of server-side OpenGL development.

---

### Post by samjh on 2007-03-25
> **bfree said:**
> I've just posted benchmarks comparing OpenGL performance on Linux vs Vista -
[http://graphcomp.com/opengl/bench.html](http://graphcomp.com/opengl/bench.html)

There are rumors (unsubstantiated) that MS is intentionally degrading OpenGL performance to to better position Direct3D.

I take that with a grain of salt - but if true, it would be very disappointing to me as a cross-platform 3D developer.  Definitely tilts the scales toward Linux in terms of server-side OpenGL development.

Sounds like FUD.

Microsoft may be highly competitive, but they're not "evil".  They're also not stupid, either.

Deliberately degrading OpenGL performance on Vista would restrict their market appeal, which is not in line with Microsoft current strategy of adoption and expansion.  Also deliberate restriction of OpenGL on Vista has potential for new anti-trust action, which Microsoft doesn't need.  It also takes development resources to restrict OpenGL performance, which could be better spent in more productive work.  Finally, OpenGL performance is dictated largely by graphics chipset manufacturers and the drivers they release, not by Microsoft.

The degradation of performance might have to do with Microsoft's "safe" implementation of its C++ platform libraries (which are not friendly to run-of-the-mill C/C++ code), than any intentional sabotage.

---

### Post by bfree on 2007-03-26
> **samjh said:**
> Microsoft may be highly competitive, but they're not "evil".  They're also not stupid, either.

Didn't call them evil, nor stupid... I've been developing on MS platforms since the mid-80's (DOS/Win16/Win32) - and enjoy doing so.  I've been developing on unix systems since the mid-70's - enjoy that, as well.

> **samjh said:**
> Finally, OpenGL performance is dictated largely by graphics chipset manufacturers and the drivers they release, not by Microsoft.

I find it doubtful that nVidia would produce an OpenGL driver for Vista that is 60% slower than their drivers for Linux (they earn far more profits from Windows OEMs) - unless there were something in the OS that prevented them getting the same performance.

> **samjh said:**
> The degradation of performance might have to do with Microsoft's "safe" implementation of its C++ platform libraries (which are not friendly to run-of-the-mill C/C++ code), than any intentional sabotage.

My OpenGL benchmark is using straight Win32 SDK C code, with no MFC nor managed code.  The non-OpenGL portion of the code runs with the same performance on NT/XP/Vista/Fedora/Ubuntu - it's only the OpenGL/GPU execution that is slower on Vista than Linux.

My guess is that Vista is reserving a percentage (40%?) of non-D3D GPU cycles for Aero (to ensure UI performance).  When I get a chance, I'll put together some benchmarks comparing nVidia's OpenGL vs D3D drivers on XP and Vista.

Call it FUD if you like, but I'm a long-time Windows fan who is very disappointed in the OpenGL performance I'm seeing in Vista (at least to-date) - and this directly impacts my current OpenGL server-farm project.

---

### Post by samjh on 2007-03-26
> **bfree said:**
> Didn't call them evil, nor stupid... I've been developing on MS platforms since the mid-80's (DOS/Win16/Win32) - and enjoy doing so.  I've been developing on unix systems since the mid-70's - enjoy that, as well.Wasn't directed at you.  But if MS is willfully degrading OpenGL performance on Vista, one might class that as "evil" and "stupid". ;)

If what you say is true (and you have the data to support it), then I am also disappointed.

However, for a truly objective test, what is the difference in DirectX performance between XP and Vista?  Having that data can help normalize the differences you have witnessed in OpenGL performance and put it more into perspective.

**Hmmm, this is serious case of thread hijack! (TIme to discuss this further in another thread)**

---

### Post by guinra on 2007-04-12
In my opinion, what makes Linux better for most development is the console.  In fact, this is a major win for Linux in most cases except basic e-mail and web surfing.  Actually having a console and not an emulated DOS prompt with those blasted \ instead of / path separators makes a big difference when coding to me.

---

### Post by IronAvatar on 2007-04-13
> **Grey said:**
> The DS and the Wii are just fun though.  You don't really have to worry about writing some sophisticated monstrosity.  You just write your code, it runs, and everyone's happy.  You don't have to trick the hardware.

Is that so? You sort of forget to mention that on the DS, what little VRAM there is, is a complete pain to use and the poly renderer works in such a way that you can't use a caching scheme.  

And let's not get into the hell that is trying to support KANJI fonts and everything else :) But hey, it's a challenge and programming is all about solving a problem (or in some cases, finding a problem for your sollution) and having fun while doing it :)


I've only just started using Ubuntu, and the available IDE's have been less than impressive.  Eclipse is memory hungry and buggy. kDevelop while excellent at making KDE apps, is very cluncky and counter-intuitive to use if you have code you want to share across platforms/applications.

Finding the right pakcages to install depending on what you want to code, and which language, can be a bit of a pain in Ubuntu.  How many people have posted "can't compile Hello World on kDevelop" because they didn't install autoconf, automake and everything else?

I love using Code::Blocks though, even though it is rather buggy.  It's felxible and just NICE. So if there's one thing that makes coding on Linux easy, it's that and the fact that Ubuntu Linux in general is so fluffy to use.

But as a serious development platform that can be used "out of the box", it has a long way to go before it can claim to be as easy to setup and use as any Windows based development environments.  And really, this is an area that I think the Ubuntu team can address by including a "development environment" option in the setup process.  From what little coding I've done under Linux with Code::Blocks, I like it.  It beats every other windows based compiler/debugger suite (SN for DS, SN for PS2, SN for N64, Codewarror for Dreamcast, PS2 and DS) I've had to endure over the years except Dev Studio.

---

### Post by pmasiar on 2007-04-13
Seems to me that "intuitive" == "works exactly like editor/IDE I used for last 5-10 years"? :-)

Well, guess what: when you making change, things change - that was the whole point of making the change, no?

For so many years I used MultiEdit for all my needs, customized it heavily, and created custom macros for it. When switching to Linux, my first reflex was to check if MultiEdit works for Linux. Alas, it does not. 

My second reflex was to check and compare other full-featured [orthodox text editors](http://www.softpanorama.org/Editors/index.shtml). Of course features should include also ability to create own macros, in some reasonable scripting language - that's the whole point of customization.

Editor should be optimized for reading and refactoring the code. IDEs are optimized for creating more template-based code. And BTW templates for writing code are present in any decent full-featured text editor.

When selecting tool to master, and plan to invest hours of time to become expert in it, you want tool what is flexible enough to be used with many different languages, and stable enough so you don't have to abandon it and switch to another one in 5 years from now.

---

### Post by HolyJoe on 2007-04-13
The Microsoft give your windows, but linux give your whole house!

---

### Post by slavik on 2007-04-13
here's another reason why linux is better for dev work ... man pages (and apropos)

---

### Post by IronAvatar on 2007-04-13
> **pmasiar said:**
> Seems to me that "intuitive" == "works exactly like editor/IDE I used for last 5-10 years"? :-)

Well, guess what: when you making change, things change - that was the whole point of making the change, no?


Well, no.  The point of making change, is to improve things, not make them worse.  Change for the sake of change is pointless.  

The thing about an IDE is that it is an "Integrated Development Environment", and it's job is to provide an easy alternative to having separate applications for editing, compiling, debugging and managing projects. Its job is to save time, and let the programmer concentrate on actually programming.

I have nothing against positive change, and I try my best to embrace it.  But IDE's such as kDevelop and Eclipse try to lock the user into a certain way of working, which may not be the best practice or meet the requirements of your project.  The worst thing about this, is that the developers of those IDE's don't see anything wrong with how they work, and the **limitations the IDE's impose** on programmers.  The fundamentalist linux-user attitude seems to be "yeah, it's difficult to use but this a REAL operating system man! This isn't windows! Suck it down!"

If Code::Blocks is like Dev Studio, then that's a good thing because Dev Studios most powerful feature is its flexibility.  

And another thing, if I have to trawl through pages of incomplete documents to find out how a certain feature of the IDE works, then that's time I'm not coding.  If I constantly have to find work arounds to an IDE's lack of features or its limitations, then that's time I'm not coding.

In short, if even one of the above statements is true, then the IDE programming team has failed.  Remember "it just works" is the Ubuntu credo, and the rest of the Linux community would do well to take that to heart.

---

### Post by Wybiral on 2007-04-13
> **IronAvatar said:**
> The thing about an IDE is that it is an "Integrated Development Environment", and it's job is to provide an easy alternative to having separate applications for editing, compiling, debugging and managing projects. Its job is to save time, and let the programmer concentrate on actually programming.

... Any text editor with an embedded terminal (or terminal with embedded editor) can type "make" or "./compile.sh" or "scons" when needed.

You act like the compiler/linker/editor of those IDEs are all one program. I fail to see how they are more efficient then someone who knows his tools and has a terminal+editor in from of him/her. 

Anyone who isn't experienced with their compiler/linker enough to develop without an IDE should really consider expanding their knowledge.

Efficiency...

* Clicks mouse in terminal (in Gedit's bottom panel) *
* Types 'make' *
* Is done... *

---

### Post by pmasiar on 2007-04-14
I agree with most of you say. I may just see it differently - because last 10 years I did not used IDE, but really good editor :-)

> **IronAvatar said:**
> IDE is an "Integrated Development Environment", and it's job is to provide an easy alternative to having separate applications for editing, compiling, debugging and managing projects. Its job is to save time, and let the programmer concentrate on actually programming. (...)But IDE's such as kDevelop and Eclipse try to lock the user into a certain way of working, (...)developers of those IDE's don't see anything wrong with how they work, and the **limitations the IDE's impose** on programmers. 

Exactly! Thats why I prefer good editor, which works as I am used to, and which I can extent with small scriplets to do what *I* need.

>  The fundamentalist linux-user attitude seems to be "yeah, it's difficult to use but this a REAL operating system man! This isn't windows! Suck it down!"

Not so. I keep repeating that many experienced developers advise *against* using IDE: Learn real flexible scriptable editor instead. It might be little harder to learn when starting, but it's extensibility will pay off - and as a bonus, you do not have to switch to different sub-par editors in every new IDE you try.

Or pick any IDE you like, and extent it/add patches/fork it if needed.

> IDE programming team has failed.  Remember "it just works" is the Ubuntu credo, and the rest of the Linux community would do well to take that to heart.

**IDE programming team** LOL!!! **failed**? LOL!111

It is open source: created by users, every one "scratching her own itch" and sharing results with others. It relies that many people have the same itch. If not, you are out of mainstream, and basically on your own. Nobody owes you excellent free IDE which *just works* according to *your* tastes, wake up.

Do you think kernel you are running is optimized for your version of processor? Not so, I bet you run generic kernel. How optimized is your partition table? Same with all other tools - you just do not know enough to complain, and they are generic enough to "just work" in default mode. You know more about how you feel about programming, and programming is complex enough so "just work as default" is obviously not possible.

In open source, I do whatever is best for *me* and let you use it if you like it. I *may* add some features you request if I find them interesting, or *may* add your patch if I like it (but I may also reject it, if it complicates *my own* preferred enhancements). But if you don't like my free program, I don't owe you anything. If you don't like it, fork the code, or start a company and create better tool, and sell it to people like you. Complaining that some abstract non-existing "IDE programming team failed" will mark you as a whiner, subject to be ignored, not worth even a reply.

If you think your needs are mainstream, and many people are like you, than you need to select *one* IDE and convince it's developers to extent it to *your group* tastes.

---

### Post by IronAvatar on 2007-04-14
> **Wybiral said:**
> ... Any text editor with an embedded terminal (or terminal with embedded editor) can type "make" or "./compile.sh" or "scons" when needed.

You act like the compiler/linker/editor of those IDEs are all one program. I fail to see how they are more efficient then someone who knows his tools and has a terminal+editor in from of him/her. 


That's because, to all intents and purposes they are.  Sure they're seperate executeable that pipe thier output to some standard streams, but the beauty is that the IDE present everything as one package. 

When you work on large projects, you suddenly see the wisdom of an IDE that represents your project structure and manages the make process for you. You can be the best linux build guru on the planet, but it counts for nothing or large projects when you need people with entirely different skill sets.

I've dealt with command line tools in the past, and written major projects using them.  I've also found that it's a horrible and inneficient way to do things when you have to meet deadlines.  So you''ll have to excuse me if I'm not stuck in the stone age.

[qupte]
Anyone who isn't experienced with their compiler/linker enough to develop without an IDE should really consider expanding their knowledge.
[/quote]

I've developed using command line tools on many, many platforms.  I'd say the biggest problem here is not my lack of knowledge, but other peoples lack of understanding.  My first PS2 project was done using commanling tools and a seperate debugger, and it was a nightmare trying to maintain it.

You'll have to excuse me if I've moved on from inneficient processes.  When you worked on a project that is similtaneiusly developed for multiple platforms with over a thousand source files, THEN you can talk to me about expanding knowledge.

> 
Efficiency...

* Clicks mouse in terminal (in Gedit's bottom panel) *
* Types 'make' *
* Is done... *

Right...and just how long does it take to create a make file? To expand a make file for a new configuration or platform?  Not exactly efficient really, is it?

---

### Post by runningwithscissors on 2007-04-14
From personal experience I find developing on Linux easier. The docs available online for setting up libraries and tools are excellent, and you generally know what is happening.

Now I am not one of those fanatics that thinks that IDEs are bad. I just don't use them because they've never really worked right for me. Yes, I use VS.NET at work and I find it awfully slow and rather complicated.

---

### Post by Wybiral on 2007-04-14
> **IronAvatar said:**
> Right...and just how long does it take to create a make file? To expand a make file for a new configuration or platform?  Not exactly efficient really, is it?

When you have a good template to go off of... About as long as it take a big IDE to load :)

Using Windows dev tools... How easily is THAT going to be to configure and redo everything for a platform?

---

### Post by IronAvatar on 2007-04-14
> **Wybiral said:**
> When you have a good template to go off of... About as long as it take a big IDE to load :)

Using Windows dev tools... How easily is THAT going to be to configure and redo everything for a platform?


Hmm...let me see. Let's load up VS 2005 on my PC.  My watch around 5 seconds for it to load, and 3 seconds for it to open a workspace.  

As for using Windows tools to redo everything for a platform, that's easy. Again, in VS 2005; 

Step 1. Create a new build configuration, using the settings from an existing config.
Step 2. Set compiler settings as required (several ways of doing this)
Step 3. Set your output path
Step 4. Set compiler switches depending

And even in an open source project like Code::Blocks it's pretty straight forward, with even better support for different compilers.  

So what's going to be your next argument against IDE's and for managing a massive project manually?  

Look...it's comletely up to you which tools you do to don't use. I'm not against command line tools or the people who use them.  The while "which is faster to use" a purely subjective argument, because we can all come up with ways to do things really fast in the environments we're used to. 

The problem with coming up with workaround to the limitations of things like kDevelop, is that they also introduce thier own set of problems that you may have to constantly deal with.  So in reality, you swap one problem for another. 

And really...if you're sollution to any problem on Linux is "write a shell script" (or makefile, or use the command line) then you've just alienated 99.9% of the people who use computers on a regular basis.

---

### Post by Wybiral on 2007-04-14
> **IronAvatar said:**
> Look...it's comletely up to you which tools you do to don't use. I'm not against command line tools or the people who use them.  The while "which is faster to use" a purely subjective argument, because we can all come up with ways to do things really fast in the environments we're used to. 

OK... That's fair. I'm happy with that agreement.

> **IronAvatar said:**
> And really...if you're sollution to any problem on Linux is "write a shell script" (or makefile, or use the command line) then you've just alienated 99.9% of the people who use computers on a regular basis.

Because they don't have Linux? Or because they have Linux and don't use the terminal?
I like Makefiles because anyone who knows how to read them can use it to make a build on any other platform with GCC (which is a lot of platforms). When people get trapped in the world of MS point and click build systems and have no idea what is really going on, that is when they run into problems porting things... You MUST understand your tools.

Anyone can be efficient with any of their tools if they know them well enough and use them often enough. That's just how it is... That's why I don't complain about Linux dev tools, they work for me.

Your first statement was absolutely true, it's all about comfortability (I only responded because I thought you were going to be like that other guys who was like "no way... MS tools are always better, everyone likes them, that is why everyone uses them, Linux tools suck" but you are not, so yes, I agree 100%... Don't say anyones tools are inadequate, they are fine for anyone who knows how to use them properly, including MS tools... (but GCC is more portable :) ))

---

