---
title: "gtkmm simple compile help"
date: 2009-02-18
forum: Programming Talk
---

### Post by msbealo on 2009-02-18
Hi, 

I'm trying to run through the gktmm tutorial and I've hit a rather early snag.

I can't compile the the simple.cc program found at 

[http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/chapter-basics.html#sec-basics-simple-example](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/chapter-basics.html#sec-basics-simple-example)

when I run

```
g++ simple.cc -o simple `pkg-config gtkmm-2.4 --cflags --libs`
```

I get

```
simple.cc:4: error: ‘argc’ was not declared in this scope
simple.cc:4: error: ‘argv’ was not declared in this scope
simple.cc:8: error: expected constructor, destructor, or type conversion before ‘(’ token

```

I'm currently compiling it from /usr/local/src as I was trying to follow a recommendation from somewhere, but I get the same problem if I run it from my user folder.

Initially I tried to find out what was wrong and found that I also couldn't compile a simple helloworld program. I sorted that out by installing the build-essential package, however I still can't get this simple gktmm program to compile. 

Considering my grand plans of what I was going to start programming, this is a rather humbling problem.

Please help,

Mark
8.10

---

### Post by cabalas on 2009-02-18
Would you be able to post the code you are trying to compile? I tried the sample code from the gtkmm site and it all compiled and ran fine.

---

### Post by SledgeHammer_999 on 2009-02-18
You will also need the -dev packages of gtkmm. Search synaptic for "libgtkmm-2.4-dev"
or in a terminal paste this:
```
sudo apt-get install libgtkmm-2.4-dev
```

---

### Post by PandaGoat on 2009-02-18
I going to guess you copied some code using gtkmm from a tutorial but wrote the main method yourself.  

Your main method should look like this:
[php]
int main(int argc, char** argv)
{
    . . .
    return 0;
}
[/php]

---

### Post by msbealo on 2009-02-19
The code, as copied from the tutorial pages...

Ah.. I think I've just realised what I've done.

I literally copied the code from the page as I didn't see the Source link. The code on the page is not entirely complete and the source should read:

```
#include <gtkmm.h>

int main(int argc, char *argv[])
{
    Gtk::Main kit(argc, argv);

    Gtk::Window window;

    Gtk::Main::run(window);
    
    return 0;
}
```

I'm not at my computer right now so I can't test if this works, but I bet having some working code can't hurt.

I was confused because I was also having more general compile problems with g++ at the time. I'll test this when i get home. 

Sorry for the waste of time and thanks for your replies.

Mark

---

