---
title: "Question from a confused programming student who is new to OPEN SOURCE projects..."
date: 2006-09-13
forum: Programming Talk
---

### Post by mike41 on 2006-09-13
Hello.

I am a computer science major, and so I "know" how to program (i hope). I've figured out how to download source code, but in all honesty I dont know what to do with it. I would like to play around with pre-existing open source apps, and eventually be an active programmer in the community. There is just so much new stuff that I dont understand.

If I go to sourceforge and download c source code of an application, should I be able to open it in anjuta (importing a project) and then compile it using anjuta's 'build" option? I tried that with one project - gnomad2 - and it wouldnt compile. Now i know that if I use the configure command, and then the make files, it will compile and produce an executable, but how do I set up an IDE - not necessarily anjuta - so that I can play around with the code, and compile it within the IDE?

Any help would be great! 

-Mike

---

### Post by beathan on 2006-09-13
Why not edit the source files via a text editor in your shell, like emacs or vi? Heck, even nano or pico if you want something less involved. Learning emacs or vi (or whatever editor, not looking to stir up the Holy Wars here), will also help you get around in non-GUI environments should you encounter them in your future career.

As a CS major myself, I'm all for using an IDE if it helps you be a more productive worker, but getting your hands dirty with the code in a non-IDE environment will force you to know the ins-and-outs of the languages you're dealing with much more effectively. My humble opinion, of course.

Are you familiar with gcc/g++ ? Check [here]("http://users.actcom.co.il/~choo/lupg/tutorials/c-on-unix/c-on-unix.html") for a nice guide to both if not.

---

### Post by thumper on 2006-09-14
Gee, I don't know what they are using to teach these days, but when I did CS all you had was emacs/vi and a command line compiler with makefiles (perhaps I'm showing my age).

I'm not a big fan of IDEs.  When hiring people and talking with them about what they know, many (especially windows developers) just know an IDE (visual studio).  Creating a class is clicking on the wizard.  Adding methods is clicking on the wizard. 

If it helps, great, but much of the time I have used IDEs you spend a not inconsiderable amount of time fighting with it as the IDE wants you to work its way.

That all said, if you are creating an IDE project for something that doesn't have one, then it should just be a case of adding all the source file, then configuring the build options with the appropriate directories for object files, the appropriate command line options, the lib directories, and libraries to link in.

---

### Post by Tomosaur on 2006-09-14
Yeah, I've tried IDEs in the past and I've gotta say, I really don't like them. I always end up falling back to just a text editor and the compiler :S

Anyway, if you really want to use an IDE to do this kind of thing, I *think* (but I'm not really sure) the way to go about it is to create your own project file, then import the source files. It could be a bit tricky though. As thumper said, the IDE generally wants you to play by its own rules, thus importing a source file may be like banging your head against a brick wall.

---

### Post by thesmartace on 2006-09-14
I'm an Information Technology student from Australia. For all of the programming courses that I have done so far we have not used any IDEs (unless you count Flash as an IDE). C was just using vi and gcc/make. Java was along the same lines. It comes down to how the lecturer wants to teach I guess. A friend of mine did a C++ elective and the lecturer had them using Visual Studio.

---

### Post by mike41 on 2006-09-14
The only time i used an IDE for a course was when we learned Eiffel. Im all for using the command line, but I feel like I should also be able to use an IDE. And when Im editting someone else's huge project, isn't that the best way to get the big picture?

---

### Post by beathan on 2006-09-14
It may be the best way for you to get the big picture, and if you think that's the case, then go for it :) As mentioned above, it shouldn't be too difficult to get the source added in a new project in something like Anjuta.

If you can't get it working properly, why not use a plain text editor like gedit or an equivalent and edit graphically while compiling, etc., from within an open shell? That would still give you the ability to tab between different source files quickly while giving you easy access to the compiler.

---

### Post by sas917 on 2006-11-06
I second the motion for vi/emacs and a command line compiler. I believe you can get a better understanding of the code if you work with just the guts of it. IDE's hide a lot of things, certain ones fall in and out of popularity so you'll constantly be learning new ones ... etc.

I know it's a lot harder but in the long run you'll be glad you just trusted your favourite editor. You'll never be bothered with the never-ending task of fitting an app to an IDE again.

my two cents.

---

### Post by moberry on 2006-11-08
The best way to sift through existing source code is to first compile it. most large projects have their own makefiles as well as dependencies. Well made makefiles will give "pretty" errors letting you know what you need to install. Messy ones (mine) just fail with compilation errors. I usually goto packages.ubuntu.org and type in the header filename, and install the name of the package that header is in. To start sifting through code start at the obvious place. the "main" function. and branch off from there. I learned alot looking at other peoples code, and encourage it. It is what this community is about. Remember to always respect the work of others though.


p.s. I wouldnt recommend compiling a project in anjuta. I find it to be more of a pain in the *** than its worth. I personally use a pretty customised emacs setup. Emacs has alot of functionality built in for compiling and debugging. The learning curve is not as steep as might might look when firt starting it up. I could not figure out how to quit the program the first time I loaded it :p. There is a very handy walk-through guide located in the help menu that works wonders.

---

### Post by reynoldlariza on 2006-11-08
> **beathan said:**
> but getting your hands dirty with the code in a non-IDE environment will force you to know the ins-and-outs of the languages you're dealing with much more effectively. My humble opinion, of course.


talk about "passion vs productivity".... whichever you side in first is not important, sooner or later you'll get to both of it in no time.
;)

---

### Post by rplantz on 2006-11-08
> **thumper said:**
> Gee, I don't know what they are using to teach these days, but when I did CS all you had was emacs/vi and a command line compiler with makefiles (perhaps I'm showing my age).

When I learned how to program, I used a keypunch machine, then took my deck of cards half way across campus (Berkeley) to the computer center in the Math building. I left my deck in the inbox and returned in a couple of days to pick up the results. One learns not to make typos when the turn around on a compile is a couple of days. (I'm guessing that I have a few years on you.)

You haven't lived until you've programmed a gui in assembly language. :)

---

