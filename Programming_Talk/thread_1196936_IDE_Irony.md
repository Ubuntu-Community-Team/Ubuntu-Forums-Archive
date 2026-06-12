---
title: "IDE Irony"
date: 2009-06-25
forum: Programming Talk
---

### Post by jacensolo on 2009-06-25
In my search to find a good development environment in Linux I tried many things: Code::Blocks, Geany, Nano, Gedit, and Vim. All seemed to work and I used Geany and Vim for a while. Both worked fine for small-midsmall projects (especially vim's shortcuts), but when doing a larger project I needed something with code completion, or at least something that listed arguments of functions and members of objects. So,  after trying to get omnicomplete for vim to work for almost a week, I decided to move on. I tried Code::Blocks again, but completion didn't work properly. EX: It listed arguments after I backspaced over the "(", but it went away when I started typing. Geany is lightweight so I didn't expect it to have intellisense-ish autocomplete, and Nano and Gedit speak for themselves.

So I decided to try MonoDevelop. It's a great IDE with great completeion but cannot yet resolve types. So it will list arguments of a function but not members of an object. I don't know ifi this will be added since it is primarily a C# IDE. I may look into adding it myself, but I've never done much text parsing.

So next on my list is netbeans. I was pretty wary about this one because I thought it was mainly for Java with a quick C++ addon. Not to mention it was made in Java, so my 512mb of RAM on my laptop might not like it. But I took the plunge anyway and ~200mb later I had excellent code completion on-par with intellisense. It will list all the members of an objects and all of the arguments of a function. The downsize is the fact that it is huge and made in Java so it can be slow at times.

Anyway, I think it is ironic that the application that has the best code completion for c++ was written in Java for Java. I guess most C++ programmers think they are too cool for code completion.

---

### Post by Can+~ on 2009-06-25
Try Eclipse with the cdt plugin from the website.

It's also written on Java, but IMO it runs faster than Netbeans.

[http://www.eclipse.org/downloads/](http://www.eclipse.org/downloads/)

---

### Post by TheBuzzSaw on 2009-06-25
Not really. The C++ vs Java "war" is in most people's heads. I like Netbeans' interface a lot regardless of its slow/bloated nature. I'm still searching for a faster alternative, but Netbeans gets the job done for now.

---

### Post by Mirge on 2009-06-25
I tried netbeans, uninstalled it, re-installed it, uninstalled it, re-installed it... and I'm working on configuring it now... the text size was huge in the editor it seemed, got that lined out. Had to edit a config file (that wasn't even created yet) to get the line spacing fixed... small stuff like that really irked me. Looks like it has a lot of potential, and I would love to like it, but damn it makes it hard sometimes :P.

I primarily use Code::Blocks and Geany. I'd switch to any IDE really just for some really good intellisense/code completion/hints.. which I think NetBeans *can* offer.

---

### Post by Mirge on 2009-06-25
I'm installing MonoDevelop now... I didn't even think of it as an IDE for C++... some of the screenshots look pretty nice.

EDIT: I clicked the Classes tab after creating a new C++ solution, it crashed. Nice :).

---

### Post by Can+~ on 2009-06-25
> **Mirge said:**
> I'm installing MonoDevelop now... I didn't even think of it as an IDE for C++... some of the screenshots look pretty nice.

EDIT: I clicked the Classes tab after creating a new C++ solution, it crashed. Nice :).

Why no one trusts me when I suggest Eclipse?

:(

---

### Post by Mirge on 2009-06-25
> **Can+~ said:**
> Why no one trusts me when I suggest Eclipse?

:(

lmao

I tried eclipse cdt once... didn't like it so I uninstalled. I may try it again after work today.

---

### Post by Can+~ on 2009-06-25
> **Mirge said:**
> lmao

I tried eclipse cdt once... didn't like it so I uninstalled. I may try it again after work today.

I also went through all IDEs when I was just starting with C on ubuntu, IDEs not available in the repository, and all.

But in the end, I downloaded Eclipse and after a few struggles in the begining due to my ignorance, I finally managed to love it. Plus, having the SVN plugin and the pydev all in one, makes it even more great.

---

### Post by Mirge on 2009-06-25
heh yeah, I tried Eclipse (probably not being fair to it) when I tried a bunch of other IDE's too, most of which were also uninstalled. I don't even remember why I didn't like it.. I'll check it out here in a bit.

---

### Post by jacensolo on 2009-06-25
> **Can+~ said:**
> Why no one trusts me when I suggest Eclipse?

:(



I did try it, but a simple hello world doesn't compile. It tried to include everything under /usr/include

---

### Post by Mirge on 2009-06-25
> **jacensolo said:**
> i did try it, but a simple hello world doesn't compile. **it tried to include everything under /usr/include**

lmao :lolflag:

---

### Post by Can+~ on 2009-06-25
> **jacensolo said:**
> I did try it, but a simple hello world doesn't compile. It tried to include everything under /usr/include

[list=1]
[*]New Project > C project
[*]Empty Executable project, name it as you want
[*]Finish
[*]Add a Source folder, name is as you want
[*]Add a source file (.c)
[*]Write the hello world
[*]Click on the little hammer above
[*]Click on the "start" button.
[/list]

---

### Post by Mirge on 2009-06-25
I am liking Eclipse so far... seems pretty decent, but I'll definitely need to configure it to suit me better.

-rwxr-xr-x 1 mike mike 94582 2009-06-25 16:30 eclipse-helloworld

Why would that filesize be so high?

If I compile the .cpp file myself with g++ -o eclipse-helloworld eclipse-helloworld.cpp then it's much smaller:

-rwxr-xr-x 1 mike mike 11774 2009-06-25 16:34 eclipse-helloworld

Source:
```

//============================================================================
// Name        : eclipse-helloworld.cpp
// Author      : 
// Version     :
// Copyright   : 
// Description : Hello World in C++, Ansi-style
//============================================================================

#include <iostream>
using namespace std;

class HelloWorld
{
public:
    void greet() const;
};

int main() {

    HelloWorld *h = new HelloWorld;
    h->greet();

    delete h;
    return 0;
}

void HelloWorld::greet() const
{
    cout << "Hello, world!" << endl;
}

```

---

### Post by Can+~ on 2009-06-25
Probably because Eclipse is compiling with debug flags (-gdb) plus other stuff so you can debug it properly.

If you switch to "release mode" it would turn off all of it and just leave a plain executable.

---

### Post by Mirge on 2009-06-25
> **Can+~ said:**
> Probably because Eclipse is compiling with debug flags (-gdb) plus other stuff so you can debug it properly.

If you switch to "release mode" it would turn off all of it and just leave a plain executable.

Ahhh that makes sense. I didn't even think about that.

Release version (few KB more--big deal):
-rwxr-xr-x 1 mike mike 15901 2009-06-25 16:48 eclipse-helloworld

Much better thanks :). I'm gonna experiment with Eclipse some more, it's starting to grow on me now...

---

### Post by Can+~ on 2009-06-25
> **Mirge said:**
> Ahhh that makes sense. I didn't even think about that.

Release version (few KB more--big deal):
-rwxr-xr-x 1 mike mike 15901 2009-06-25 16:48 eclipse-helloworld

Much better thanks :). I'm gonna experiment with Eclipse some more, it's starting to grow on me now...

Add the debug panel on top right, and add some breakpoints and do a debug.

I particularly love Eclipse's debugging.

---

### Post by Mirge on 2009-06-25
Ok, I've got Eclipse set up exactly how I want it, minus one thing...

Whenever I click a function or class name in my source, it highlights it gray. I'm sure it's something simple I overlooked, but any idea how I can get rid of that? Or even if I click OFF the name... stop highlighting it?

Other than that, I think Eclipse just took over code::blocks and geany for my C++ coding...

---

### Post by Can+~ on 2009-06-25
> **Mirge said:**
> Ok, I've got Eclipse set up exactly how I want it, minus one thing...

Whenever I click a function or class name in my source, it highlights it gray. I'm sure it's something simple I overlooked, but any idea how I can get rid of that? Or even if I click OFF the name... stop highlighting it?

Other than that, I think Eclipse just took over code::blocks and geany for my C++ coding...

On the main toolbar there's an icon like a "highlighting pen" ("Toggle Mark Occurrences" (Shift + Alt + O)).

Tip: Also, you can Ctrl+Click on a function to jump to it's definition.

---

### Post by Mirge on 2009-06-25
> **Can+~ said:**
> On the main toolbar there's an icon like a "highlighting pen" ("Toggle Mark Occurrences" (Shift + Alt + O)).

Tip: Also, you can Ctrl+Click on a function to jump to it's definition.

Wow that's perfect. Eclipse rocks! Thanks!

---

### Post by Sockerdrickan on 2009-06-26
> **Mirge said:**
> lmao :lolflag:
 :lolflag:

---

### Post by Simian Man on 2009-06-26
I like Eclipse as well.  One thing though is that, at least when I used Ubuntu, the version in the repos was extremely old.  Anyone looking to use it on Ubuntu should get it right from the site rather than from the package manager.

---

### Post by Mirge on 2009-06-26
> **Simian Man said:**
> I like Eclipse as well.  One thing though is that, at least when I used Ubuntu, the version in the repos was extremely old.  Anyone looking to use it on Ubuntu should get it right from the site rather than from the package manager.

That's what I did too (from site, no repos).

---

### Post by Mirge on 2009-06-26
Goodbye, Qt Creator! No offense, I think it's a pretty decent editor, but I'm a serious Eclipse fan now... and [http://doc.trolltech.com/qt-eclipse-1.5.0/eclipse-integration-getting-started.html](http://doc.trolltech.com/qt-eclipse-1.5.0/eclipse-integration-getting-started.html) really sealed the deal. I've been playing around with it, and holy cow... so much better (for me) than Qt Creator.

---

### Post by TheBuzzSaw on 2009-06-28
I've been sucked back into using Netbeans. It still has unmatched code completion.

---

