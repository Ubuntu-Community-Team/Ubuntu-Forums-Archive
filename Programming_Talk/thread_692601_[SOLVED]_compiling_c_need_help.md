---
title: "[SOLVED] compiling c? need help"
date: 2008-02-09
forum: Programming Talk
---

### Post by RadiationHazard on 2008-02-09
ok so i'm learning c and i made the normal hello world
```

 
#include <stdio.h>
 
int main(void)
{
    puts("Hello world!");
    return 0;
}
```
and i don't know how to compile it on ubuntu.
=\
it's on my desktop as hello.c
can someone please tell me how to compile it and run it?
:)

---

### Post by Haluci on 2008-02-09
Try using gcc, the c complier included in Ubuntu.  Type

```
man gcc
```

to see the documentation.

---

### Post by yabbadabbadont on 2008-02-09
First you need the standard build tools:
```
sudo apt-get install build-essential
```
Then compile your program:
```
gcc -o hello hello.c
```
Then run the program:
```
./hello
```

---

### Post by RadiationHazard on 2008-02-09
k
i read that
i'm still confused
haha
can someone just tell me a simple code i can use to compile the file
like i just change the files name for the file i'm wanting to compile?
i'm a n00b at this
so i need something short sweet and to the point

thank you :)

---

### Post by RadiationHazard on 2008-02-09
ok, i'll try that and reply back to let you know if it worked.
thanks for the reply by the way

---

### Post by LaRoza on 2008-02-09
[http://ubuntuforums.org/showthread.php?t=606009](http://ubuntuforums.org/showthread.php?t=606009)

(Moved to Programming Talk)

---

### Post by yabbadabbadont on 2008-02-09
Edit: Never mind.

---

### Post by LaRoza on 2008-02-09
> **yabbadabbadont said:**
> Edit: Never mind.

Can I rent you sig space?

```

[noparse]
[Learn to Program Portal]("http://laroza.freehostia.com/home/") | [Link in My Sig]("http://laroza.pbwiki.com/TheLinkInMySig") | [Codes of Conduct]("http://laroza.pbwiki.com/Code") | [Spam]("http://video.google.com/videoplay?docid=2496293981990713675")
[/noparse]

```

---

### Post by RadiationHazard on 2008-02-09
ok, so it said Hello World
so i'm guess it worked?
but it said it in the terminal
what happens when i get to where i making apps and stuff?
=/

---

### Post by RadiationHazard on 2008-02-09
and are you asking me to put that into my sig?

---

### Post by LaRoza on 2008-02-09
> **RadiationHazard said:**
> and are you asking me to put that into my sig?

No, yabbadabbadont. (See his/her sig)

---

### Post by LaRoza on 2008-02-09
> **RadiationHazard said:**
> ok, so it said Hello World
so i'm guess it worked?
but it said it in the terminal
what happens when i get to where i making apps and stuff?
=/

Yes, that means it worked.

What do you mean?

If you are just starting out, I suggest a different language (but you don't have to).

If you want GUI's, see my wiki.

It is best (and possibly the only way) to start with command line programs.

---

### Post by yabbadabbadont on 2008-02-09
> **LaRoza said:**
> No, yabbadabbadont. (See his/her sig)

His, just FYI.  :)

I'm sure that we could work out some sort of arrangement...  (wink, wink, nudge, nudge, say no more)

(It's still Monty Python week isn't it?  ;))

---

### Post by LaRoza on 2008-02-09
> **yabbadabbadont said:**
> His, just FYI.  :)

I'm sure that we could work out some sort of arrangement...  (wink, wink, nudge, nudge, say no more)

(It's still Monty Python week isn't it?  ;))

Not for me, but it is officially ending on 14 February 2008.

If you add it to you sig, I will allow you to post spam on the forum (but no singing)

---

### Post by RadiationHazard on 2008-02-09
i'm confused?
this isn't my first language
i know web languages
but i'm wanting to learn how to make apps and stuff
i'm pretty good with computers
i'm just one of those people who learns by seeing...
so it makes things a little harder.

---

### Post by LaRoza on 2008-02-09
> **RadiationHazard said:**
> i'm confused?
this isn't my first language
i know web languages
but i'm wanting to learn how to make apps and stuff
i'm pretty good with computers
i'm just one of those people who learns by seeing...
so it makes things a little harder.

You aren't making sense (sorry, if English isn't your first language)

C is a good language for making applications, and since you say you know other languages, it may be a good place to start.

If you know PHP already, you can make GUI applications in it. See my wiki for the tutorials.

You compiled and ran a C program, now you just have to learn C more. 

If by "apps and stuff" you mean GUI's, that is not the best way to start to use a language. Learn the language before using specific libraries. PHP as stated before would be a good place to start if you already know PHP.

---

### Post by RemmyLee on 2008-02-09
Graphical User Interfaces will require a GUI Toolkit such as GTK+, wXwidgets, QT, etc... You'll need to learn how to link to said libraries. Web languages are scripting languages where C/C++ is interpreted. While the fundamental idea is the same, they are different in many aspects.

You'll HAVE to read to learn it. Just watching someone else code can teach you things, but when you set off on your own, you'll almost always run in to snags that will require a bit of reading and problem solving, usually in the form of mathematical equation.

---

### Post by RadiationHazard on 2008-02-09
i know php
thanks.
i'll just read some tut's 
and sorry that i'm hard to understand
thanks for the help

---

### Post by LaRoza on 2008-02-09
> **RadiationHazard said:**
> i know php
thanks.
i'll just read some tut's 
and sorry that i'm hard to understand
thanks for the help
You can use PHP and GTK to make desktop applications. It may be better for you, because you know PHP already.

Then, you will know GTK which will make it easier to use it in other languages.

---

### Post by asmoore82 on 2008-02-10
gcc is not included in Ubuntu Desktop systems,
you can install it and other useful development tools like this:
```
sudo apt-get install gcc build-essential
```

EDIT: :lolflag: had not refreshed the page in a long time;
I thought I was going to be the 3rd poster.

---

### Post by lnostdal on 2008-02-10
> **RadiationHazard said:**
> what happens when i get to where i making apps and stuff?

at that point you apply your C skills to a library like for instance GTK+

[LIST]
[*][http://library.gnome.org/devel/gtk-tutorial/stable/](http://library.gnome.org/devel/gtk-tutorial/stable/)
[*][http://library.gnome.org/devel/gtk/stable/](http://library.gnome.org/devel/gtk/stable/)
[/LIST]

---

