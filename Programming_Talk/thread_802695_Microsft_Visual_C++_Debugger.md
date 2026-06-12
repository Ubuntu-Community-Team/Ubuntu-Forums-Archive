---
title: "Microsft Visual C++ Debugger"
date: 2008-05-21
forum: Programming Talk
---

### Post by razlken on 2008-05-21
I'm running MV C++ using wine and it works fine, i had to install DOCM98 & C++ runtime too but it worked, but when i debug my code it doesn't work it's just blank gives no variables... so what should i do, is there a way to make it work or should i install something? thanks in advacne.

---

### Post by LaRoza on 2008-05-21
> **razlken said:**
> I'm running MV C++ using wine and it works fine, i had to install DOCM98 & C++ runtime too but it worked, but when i debug my code it doesn't work it's just blank gives no variables... so what should i do, is there a way to make it work or should i install something? thanks in advacne.

Any particular reason you are using a Windows specific IDE in Linux? 

Perhaps trying a Linux compiler?

---

### Post by razlken on 2008-05-21
only reason got a project to hand in and i'm late and i'm learned to program c++ on MV c++ only, so i don't want to lose time getting used to use another compiler, i never used another, but i'm planning to this summer..any help?

---

### Post by LaRoza on 2008-05-21
> **razlken said:**
> only reason got a project to hand in and i'm late and i'm learned to program c++ on MV c++ only, so i don't want to lose time getting used to use another compiler, i never used another, but i'm planning to this summer..any help?

I doubt it is the compiler you are used to. Perhaps the IDE though ;)

This is a complicated issue. If time is a factor, using Windows or using a native Linux compiler and editor are the quickest solutions.

---

### Post by razlken on 2008-05-21
hmmm but is there are way to make it work? or is it impossible? and if u got any guide or something could u post it? thx anyway

---

### Post by LaRoza on 2008-05-21
> **razlken said:**
> hmmm but is there are way to make it work? or is it impossible? and if u got any guide or something could u post it? thx anyway

I don't know if it is possible. (You don't know either it seems).

The time it takes to get this working would be less than the time it would take to install and get used to another editor.

Most of the time, Microsoft's IDE is used on Microsoft Windows to make Windows applications. That it works at all in Linux is a little short of amazing. The fact that you are having issues with it is not surprising and to be expected. 

As a Linux user (and having never used anything other than free software for compiling, with the exception of the brief time of using MiracleC for DOS just for the heck of it) I have no experience in doing what you are attempting to do.

---

### Post by Can+~ on 2008-05-21
If you're fond of big IDEs, maybe you'll get used to Eclipse with the C/C++ plugin (eclipse-cdt) in no time, and it's cross platform. (And available on the repository)

---

### Post by dwhitney67 on 2008-05-21
The easiest thing to do is use a gnome-terminal for one's "IDE".  Run 'gedit' to edit your source file(s), then 'gcc' (for C apps) or 'g++' (for C++) to compile the source file(s).

For example:
```

$ gedit hello.c
```

[INDENT]
[PHP]#include <stdio.h>

int main()
{
  printf( "hello world\n" );
  return 0;
}[/PHP]
[/INDENT]

To compile the application:
```
$ gcc hello.c -o hello
```

To run the application:
```
$ ./hello
```

It can't be any easier than that!

---

### Post by SNYP40A1 on 2008-05-22
I love Eclipse for Java, but I have tried the C++ CDT part of Eclipse and its...ok, not amazing.  I like Codeblocks better.  Although for my C++ programming, I just use a text editor.

When you debug, make sure you compiled your program with the optimizations off.  Go into your VCProj or makefile and make sure compiling optimizations are shut off.  I have had experiences where lines are skipped if the optimization is enabled.

---

### Post by razlken on 2008-05-22
ok i'll try eclipse and see how it goes or else i'll have to work on windows till i have more time to experiment with or compilers anyway thx to everyone

---

### Post by mrMango on 2008-05-22
The problem with debugging with MS Visual Studio is it uses several kernel tricks to get it to work properly. You have to be a member of the "Debugger Users" group to have permissions to do some of the nasty things it does. I would be very surprised if you would be able to get it to work in WINE. That said, even with the alternatives out there, Microsoft still seems to have the best IDE available.

If you're just looking at doing basic console C++ development, I would take a look at Anjuta. Anjuta is the Gnome IDE, and I think they're including it in the next release of Gnome. It has excellent integration with Glade as well, which is why I use it for GTK development.

Going with dwhitney67's suggestion, to debug ./hello you would use gdb: ```
gdb ./hello
```

gedit also has a terminal plugin, making the above suggestion rather trivial to implement in practice.

---

### Post by dempl_dempl on 2008-05-22
Hi!  Code::Blocks looks pretty much like VC++ .  It should be a lot easier to get used to it.

Cheers!

---

### Post by kragen on 2008-05-22
Haha - how predictable! Someone posts a question about a Microsoft product and the "solution" is to scrap possibly years of experience and use another IDE... :(

If you are not specifically developing for linux then I know for a fact that VS runs perfectly under VirtualBox.

If thats not an acceptable solution, then the first thing I'd do is try to identify if its a linux / wine specific problem. Try running the same project on a windows machine and see if you get the same issue. 

Also, can you post a screen shot of what your talking about? From your description I cant work out if your talking about a graphical / rendering error, or if visual studio is physically unable to debug correctly. Are you able to debug at all (if you set breakpoints are they hit?)

I'm probably just being condescending here... but your not trying to debug optimised code are you?

---

### Post by mrMango on 2008-05-22
The solution was not to scrap Microsoft entirely. He asked about running the Visual Studio debuggers in Wine, which is most likely impossible. We already mentioned that the best way to use the Microsoft IDE would be on the Microsoft operating system; that is, use windows. Unfortunately that is the reality of things.

He also mentioned that he was pressed for time, and therefore it would make sense that he doesn't want to spend a whole lot of time configuring something. Obviously installing Windows on VMware, VirtualBox, or something similar would work perfectly, and he already said he'd use windows if he couldn't find a viable alternative.

Given the tone of the OP, it seems to me that he's trying to do very basic C++ development, which wuold also indicate that he does not have "years of expierence" working in Visual Studio. He's only done debugging in MSVS before, so we showed him that you can do it elsewhere. 

This really isn't a shameless plus about OSS stuff; as I said before Microsoft has some of the best developer tools out there. But in the context of this particular situation, it may be eaiser and less time-consuming to go with an alternative product.

---

### Post by LaRoza on 2008-05-22
> **kragen said:**
> Haha - how predictable! Someone posts a question about a Microsoft product and the "solution" is to scrap possibly years of experience and use another IDE... :(

If you are not specifically developing for linux then I know for a fact that VS runs perfectly under VirtualBox.

I'm probably just being condescending here... but your not trying to debug optimised code are you?

Someone posts about a Microsoft Development Tool being used on Linux on a Linux forum and people try to help as best they can.

How would you react to someone wanting to make native Linux applications on Windows using Linux tools?

It doesn't take years to use an editor and compiler....

In my experience, getting things working exactly right in Wine is more of a hassle than using another editor. Of course, you may think otherwise. Perhaps you are a Wine genius, I don't know.

---

### Post by Can+~ on 2008-05-22
> **kragen said:**
> Haha - how predictable! Someone posts a question about a Microsoft product and the "solution" is to scrap possibly years of experience and use another IDE... :(

If your years of experience were wasted on learning the IDE, rather than learning how to use the language/modules/algorithms/structures, then you are doing it wrong.

What's the point on being a surfer if you're just gonna swim inside a pool?

---

