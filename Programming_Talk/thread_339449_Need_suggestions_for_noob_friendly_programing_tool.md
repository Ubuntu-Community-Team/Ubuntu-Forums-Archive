---
title: "Need suggestions for noob friendly programing tools. (I'm a student in Comp Science)"
date: 2007-01-15
forum: Programming Talk
---

### Post by braveerudite on 2007-01-15
Need suggestions for noob friendly programing tools. (I'm a student in Comp Science)

Is G++ (aka GCC) a good start?

---

### Post by Tomosaur on 2007-01-15
Depends entirely on what you want to do really. G++ is a compiler - not great to begin with since you need to have already written a program. Which language(s) will you be learning?

---

### Post by braveerudite on 2007-01-15
> **Tomosaur said:**
> Depends entirely on what you want to do really. G++ is a compiler - not great to begin with since you need to have already written a program. Which language(s) will you be learning?

C++ is what I'm tryin gto learn.  Also wanted to mention that according to synaptic g++ is already installed but wasn't listed in the application menu.  I went and looked for it in /usr/bin/g++ but pressed on the bin file and it didn't launch for some reason.  Anyways you said g++ is not very good anyways... then what should I start writting programs in?

---

### Post by Mike'sHardLinux on 2007-01-15
It sounds to me like you are looking for an IDE (integrated development environment) - a program to edit your source code. g++ is good, but it's not an IDE. You use g++ to compile your source code. It is a command line utility/program which is why there is not an icon in your desktop menus. You can look for Eclipse, or Anjuta. There are other good IDEs, too. I like Anjuta, but I am not a real programmer. I just like to tinker a bit with C++, and other languages.

---

### Post by Wybiral on 2007-01-15
g++ is a compiler

You use it from the command line.

Try making a hello world program and saving it as "hello.cpp"

Then go to the command line and enter "g++ hello.cpp"

Then you can execute your program with "./a.out" since "a.out" is the default output executable name for gcc

You can manually enter and output name with "g++ hello.cpp -o hello" which will cause the executable to compile with the name "hello" (where "./hello" will execute the file)

If you are looking for a C++ IDE, which is an editor for writing c++ programs, they aren't necessary to program C++ in (I don't use them but a ton of people cry when they have to use the command line or a normal text editor) then you might check out anjuta which you can find through synaptic. But for a lot of people, a text editor and the command line will do just fine.

Hello world program...

```

#include <iostream>

using namespace std;

int main(){
    cout << "Hello world!" << endl;
}

```

---

### Post by braveerudite on 2007-01-15
Hey! Thank you guys for your feedback I'm going to download anjuta right now and start playing with it.

---

### Post by cocteau on 2007-01-16
> **Wybiral said:**
> If you are looking for a C++ IDE, which is an editor for writing c++ programs, they aren't necessary to program C++ in (I don't use them but a ton of people cry when they have to use the command line or a normal text editor) then you might check out anjuta which you can find through synaptic. But for a lot of people, a text editor and the command line will do just fine.

Thank you for that :)

My main reason for using Anjuta is that, well... I'm a convenience junkie. I don't want to write something, switch to the commandline and type something, find out what I just wrote won't compile/crash, rewrite it and use the commandline again. I like the 'just press F11 and find out' deal. And if you can do that with a text editor, well then... my argument becomes pointless :P

---

### Post by Tomosaur on 2007-01-16
> **cocteau said:**
> Thank you for that :)

My main reason for using Anjuta is that, well... I'm a convenience junkie. I don't want to write something, switch to the commandline and type something, find out what I just wrote won't compile/crash, rewrite it and use the commandline again. I like the 'just press F11 and find out' deal. And if you can do that with a text editor, well then... my argument becomes pointless :P

XEmacs also allows this functionality after a little customising.

---

### Post by Wybiral on 2007-01-16
Gedit has a terminal plugin so that ctrl+f9 brings up a terminal.

I'm not trying to downplay IDE's, I just don't need them.

---

### Post by cocteau on 2007-01-16
> **Wybiral said:**
> Gedit has a terminal plugin so that ctrl+f9 brings up a terminal.
I'm not trying to downplay IDE's, I just don't need them.

Damn it! I kind of had a feeling that opening my mount regarding something like this would mean that I would widen my linux experience. :)

Currently I am eating my own words. I tried playing around with Gedit. And I read someone suggesting Geany so I gave that a shot and I must say I am impressed. It's far too easy to use so maybe using a text editor for coding isn't just for the hardcore...

However such a simple thing that I seem to be missing from is the ability to open two files and show them next to each other. The fullscreen feature is very nice in the vertical but I would like to be able to view another file in the empty half of the screen (seeing as how source files tend to be longer than wider).  Anyone know of an editor that will do this?

---

### Post by Wybiral on 2007-01-16
Actually... Press f9 in gedit to bring up the tab list on the left of the screen, much like most IDE's.

I am a Gedit junkie, I use it for almost every language, mostly because I can see more code and it doesn't have gobs of extra stuff to load.

Also, I have a personal issue with being distracted by all of the side stuff and menu's in most IDE's... But that's probably because I'm so used to using text editors.

EDIT:

Ooops I misunderstood what you meant... I guess you could open two instances of gedit, especially since it's so easy on the CPU and put them side-by-side.

---

### Post by Lord Illidan on 2007-01-16
Kate (a KDE tool) can do the vertical split. Try it out. Generally speaking, KDE programs have more features than Gnome programs. (I am not flaming Gnome, I actually use it myself because of its looks, but in the feature wars, KDE wins)

---

### Post by cocteau on 2007-01-16
> **Lord Illidan said:**
> Kate (a KDE tool) can do the vertical split. Try it out. Generally speaking, KDE programs have more features than Gnome programs. (I am not flaming Gnome, I actually use it myself because of its looks, but in the feature wars, KDE wins)

Yeah, I hate that. I used KDE years ago when I first came to linux with Fedora Core 1. I like that way you could split the view in Konqouror as much as you liked anyway you liked.

However since moving to Ubuntu (and Gnome) I feel so much more at home in this desktop than under KDE. I just miss this feature and there's got to be a Gnome app that can do it. And loading the kde-libs seems like a bit overkill just to run Kate...

---

