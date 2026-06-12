---
title: "Please check my application :)"
date: 2012-06-14
forum: Programming Talk
---

### Post by Paradox27 on 2012-06-14
Heyyyy again :)

I like this forum, especially its look and feel!

Anyway, I've been programming for some time now for Ubuntu (I was programming for windows prior to this) and I have to say that it's awesome!

I am now getting used to Qt Creator and I have created a little, yet useful application, called Unity Launcher Creator, and let's you create launcher files (aka .desktop files) and add them shortcut actions, that's what actually makes this application differ from the simple desktop file creators!
Here's a screenshot for you:
[IMG]http://img221.imageshack.us/img221/4576/99945786.png[/IMG]

I am generally very interested on learning packaging and I'd be glad if you could download my .deb file and tell me if I've done something wrong:
[http://dl.dropbox.com/u/85430924/ulc_1.0-0ubuntu1_i386.deb](http://dl.dropbox.com/u/85430924/ulc_1.0-0ubuntu1_i386.deb)
 (for some inexplicable reason, this forum doesn't allow me to upload it here, so I have attached only the source code, which you could see and help me with it, especially with QT) 

I am waiting for comments about my DEB file, I am not sure that the image file is going where it should but it at least works for me, hah.

Anyway, I am looking forward to seeing your comments :)

---

### Post by Paradox27 on 2012-06-16
Any feedback :) ?

---

### Post by cgroza on 2012-06-16
Your application looks really nice. Definitely worth the work you put in it. You should announce this application on other websites, don't expect it to get very much traction from this subforum :D.
Good luck and have fun programming for Ubuntu.

---

### Post by Paradox27 on 2012-06-16
> **cgroza said:**
> Your application looks really nice. Definitely worth the work you put in it. You should announce this application on other websites, don't expect it to get very much traction from this subforum :D.
Good luck and have fun programming for Ubuntu.

Yeah, it was quite difficult to make it, it took me about 2 days searching on how to do things, but it looks nice!

Did you check the code? Any suggestion? What about the .deb file, did the installation worked out?

Also, what other forums do you suggest? I want people to use my application but I am not sure where to post this...

---

### Post by trent.josephsen on 2012-06-16
There is a forum for [Packaging and Compiling Programs](http://ubuntuforums.org/forumdisplay.php?f=44) that might have some input on your .deb file. Personally I haven't used Ubuntu in ages and I only stick around for the programming talk.

As for your code, I'm not a C++ programmer so I won't venture to critique your style, but you should comment! Learn correct documentation practices now and use them religiously; it may not be fun but it saves you a world of pain.

I recommend, for your actual code (no comment on the QtCreator files which I don't understand anyway):

1_ A comment at the top of every source or header file, before the #include lines or any other code, that describes how the stuff in the file is related and how it should be used.

2_ A comment for every definition: for class and struct definitions, one that describes what the type does and how it's used; for object (data) definitions, one that describes the data in the object and what functions depend on or modify it; for function definitions, one that clearly describes the purpose of the function, how it's used, what its parameters are and what ranges it accepts, and what the return value is (if any).

3_ Comments within functions *only* to walk the reader through complicated algorithms or explain the rationale for doing something in an unusual way. If your functions need comments to break up long lists of declarations or walls of code, then you should instead consider splitting your functions into smaller ones. (Your functions seem to be of reasonable length; the only one I might consider editing for clarity is on_createlauncher_clicked.)

Comments within code should explain **why**, not **what**. If you find yourself writing comments that just paraphrase what your code is doing in English, then you should instead write the code itself more clearly. In a well-written program, what the code *does* is obvious; the comments explain *why* the author chose to write it that way.

Comments on functions (at least, functions that are part of an external API) should describe **what** but not **how**: the caller shouldn't care what internal data structures or algorithms a function uses as long as the function's *behavior* is as described in the documentation. (An exception might be when the function uses an algorithm that might severely degrade performance when called with certain arguments, or has high memory requirements.)

hmm, I gotta go comment some recent code...

---

### Post by Paradox27 on 2012-06-16
> **trent.josephsen said:**
> There is a forum for [Packaging and Compiling Programs]("http://ubuntuforums.org/forumdisplay.php?f=44") that might have some input on your .deb file. Personally I haven't used Ubuntu in ages and I only stick around for the programming talk.

As for your code, I'm not a C++ programmer so I won't venture to critique your style, but you should comment! Learn correct documentation practices now and use them religiously; it may not be fun but it saves you a world of pain.

I recommend, for your actual code (no comment on the QtCreator files which I don't understand anyway):

1_ A comment at the top of every source or header file, before the #include lines or any other code, that describes how the stuff in the file is related and how it should be used.

2_ A comment for every definition: for class and struct definitions, one that describes what the type does and how it's used; for object (data) definitions, one that describes the data in the object and what functions depend on or modify it; for function definitions, one that clearly describes the purpose of the function, how it's used, what its parameters are and what ranges it accepts, and what the return value is (if any).

3_ Comments within functions *only* to walk the reader through complicated algorithms or explain the rationale for doing something in an unusual way. If your functions need comments to break up long lists of declarations or walls of code, then you should instead consider splitting your functions into smaller ones. (Your functions seem to be of reasonable length; the only one I might consider editing for clarity is on_createlauncher_clicked.)

Comments within code should explain **why**, not **what**. If you find yourself writing comments that just paraphrase what your code is doing in English, then you should instead write the code itself more clearly. In a well-written program, what the code *does* is obvious; the comments explain *why* the author chose to write it that way.

Comments on functions (at least, functions that are part of an external API) should describe **what** but not **how**: the caller shouldn't care what internal data structures or algorithms a function uses as long as the function's *behavior* is as described in the documentation. (An exception might be when the function uses an algorithm that might severely degrade performance when called with certain arguments, or has high memory requirements.)

hmm, I gotta go comment some recent code...

All that you had to comment about was comments;)? 

Thanks for the info, I will save this on a file somewhere on my disk and I will look at it while I'm programming...
Any other info about the code? Did the .deb worked for you (why nobody talks about my deb? It was hard to be made as well...!)

---

### Post by trent.josephsen on 2012-06-16
> **Paradox27 said:**
> All that you had to comment about was comments;)? 
Yeah, I don't really "do" C++ and I know nothing about packaging, but well-organized documentation is something of a hobby.

Hope you find the other answers you're looking for.

---

### Post by MG&amp;TL on 2012-06-16
You might want to provide a build system for those wwho do not like or have Qt Creator. Gnu Make is a good one, here's an example Makefile for your situation.

```

CPP=g++
CPPFLAGS=<insert Qt flags here>
OBJECTS=mainwindow.o
NAME=launcher-creator

make: $(OBJECTS)
    $(CPP) $(OBJECTS) main.cpp $(CPPFLAGS) -o $(NAME)

clean:
    rm -f $(OBECTS)

```You need to replace CPPFLAGS with the build flags, and indents with tabs. Also provide an install rule.

Hope that helped a bit.

---

### Post by Paradox27 on 2012-06-16
> **MG&TL said:**
> You might want to provide a build system for those who do not like or have Qt Creator. Gnu Make is a good one, here's an example Makefile for your situation.

```

CPP=g++
CPPFLAGS=<insert Qt flags here>
OBJECTS=mainwindow.o
NAME=launcher-creator

make: $(OBJECTS)
    $(CPP) $(OBJECTS) main.cpp $(CPPFLAGS) -o $(NAME)

clean:
    rm -f $(OBECTS)

```You need to replace CPPFLAGS with the build flags, and indents with tabs. Also provide an install rule.

Hope that helped a bit.
Thanks for your example, but I think that if I run 
```

qmake ulc.pro

```
such a Qt-style Makefile is being created? Can I have both Makefiles?

PS -> Looking forward for DEB-feedback and general about the application !

---

### Post by MG&amp;TL on 2012-06-16
> **Paradox27 said:**
> Thanks for your example, but I think that if I run 
```

qmake ulc.pro

```such a Qt-style Makefile is being created? Can I have both Makefiles?

PS -> Looking forward for DEB-feedback and general about the application !

Ah, I wondered what that did. ;) More of a G* guy than a Q* one I'm afraid.

As long as you have some sort of build system, fine. :)

---

### Post by Paradox27 on 2012-06-16
> **MG&TL said:**
> Ah, I wondered what that did. ;) More of a G* guy than a Q* one I'm afraid.

As long as you have some sort of build system, fine. :)

What about the deb file? Did that worked for you?

---

### Post by MG&amp;TL on 2012-06-17
> **Paradox27 said:**
> What about the deb file? Did that worked for you?

...I'm on 64-bit. If you want to make a PPA, fine by me. :)

---

### Post by Paradox27 on 2012-06-17
> **MG&TL said:**
> ...I'm on 64-bit. If you want to make a PPA, fine by me. :)

What is this exactly :) ?

---

### Post by MG&amp;TL on 2012-06-17
> **Paradox27 said:**
> What is this exactly :) ?

Right. 

When you compile a program locally, your compiler sets the program architecture to your local architecture-it would do-you don't want every architecture executables after you build a program.

This mean the the binary .deb you've posted is for 32-bit only. I can tell from the _i386 on the end. There's other problems with building your debs locally as well, such as getting updates to users.

Therefore, you can use launchpad to create a Personal Package Archive. Which means that people can add your repository to their software sources and they'll automatically get updates. Also, launchpad builds ppas for a variety of architecture and ubuntu releases, so you can get your software to the greatest number of people.

Anyway, launchpad has a good tutorial for PPAs here: [https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA) -if you've already made a deb, most of the work is already done. :)

---

### Post by Paradox27 on 2012-06-17
> **MG&TL said:**
> Right. 

When you compile a program locally, your compiler sets the program architecture to your local architecture-it would do-you don't want every architecture executables after you build a program.

This mean the the binary .deb you've posted is for 32-bit only. I can tell from the _i386 on the end. There's other problems with building your debs locally as well, such as getting updates to users.

Therefore, you can use launchpad to create a Personal Package Archive. Which means that people can add your repository to their software sources and they'll automatically get updates. Also, launchpad builds ppas for a variety of architecture and ubuntu releases, so you can get your software to the greatest number of people.

Anyway, launchpad has a good tutorial for PPAs here: [https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA) -if you've already made a deb, most of the work is already done. :)

Nice, interesting. Thanks for the info... I will search about it shortly...

I've yet to understand why I am not getting enough feedback for my application...
This is the default forums for ubuntu, isn't it? I was expecting something... bigger?

---

### Post by hakermania on 2012-06-17
> **Paradox27 said:**
> Nice, interesting. Thanks for the info... I will search about it shortly...

I've yet to understand why I am not getting enough feedback for my application...
This is the default forums for ubuntu, isn't it? I was expecting something... bigger?

Welcome to Ubuntu!

Yes, it is... Your application looks good and I downloaded it yesterday.
I saw this thread again and I remembered to test it, though!

It works fine, launchers create fine, all are fine, except the fact that I don't like very much the gui... you could redesign it so as to look more attractive...

Keep up the good work!):P

---

### Post by MG&amp;TL on 2012-06-17
> **Paradox27 said:**
> Nice, interesting. Thanks for the info... I will search about it shortly...

I've yet to understand why I am not getting enough feedback for my application...
This is the default forums for ubuntu, isn't it? I was expecting something... bigger?


There's quite a few applications, not so many people with developer skills (possibly a mark of Ubuntu's success). Also, convenience is an issue. PPAs are convenient, software centre is even better. Nobody likes compiling from source, the Qt-*-dev packages are quite big. So people do care, but not many people will like to do it at the stage it's at now.

Further feedback: I don't believe you have translation support in there. Have you considered this?

---

### Post by Paradox27 on 2012-06-17
> **MG&TL said:**
> There's quite a few applications, not so many people with developer skills (possibly a mark of Ubuntu's success). Also, convenience is an issue. PPAs are convenient, software centre is even better. Nobody likes compiling from source, the Qt-*-dev packages are quite big. So people do care, but not many people will like to do it at the stage it's at now.

Further feedback: I don't believe you have translation support in there. Have you considered this?

What? Nobody has to build from source! Did not you see the .deb file on my first post? I don't know many languages but the translation is a good idea, as long as many users use my applications, but they don't...

---

### Post by Paradox27 on 2012-06-17
> **hakermania said:**
> Welcome to Ubuntu!

Yes, it is... Your application looks good and I downloaded it yesterday.
I saw this thread again and I remembered to test it, though!

It works fine, launchers create fine, all are fine, except the fact that I don't like very much the gui... you could redesign it so as to look more attractive...

Keep up the good work!):P

Thanks! I know that the gui is not perfect, but I tried my best (I don't use QT for many time)

---

### Post by MG&amp;TL on 2012-06-17
> **Paradox27 said:**
> What? Nobody has to build from source! Did not you see the .deb file on my first post? I don't know many languages but the translation is a good idea, as long as many users use my applications, but they don't...

Correction: Anyone who doesn't use 32-bit has to build from source.

You may want to look at gettext for translations-it means you don't have to personally translate your application, and the actual source code stays the same.

You will gain users, slowly. :) Make a launchpad page and PPA, then maybe announce it to one of the Ubuntu news sites. You'll get there, but don't expect instant recognition. :)

---

### Post by Paradox27 on 2012-06-17
Thanks! I am still looking forward for more comments! I am designing version number 2, but I don't have many things to do. I want some opinions first. How else will I understand what needs fixing?

---

### Post by trent.josephsen on 2012-06-17
> **Paradox27 said:**
> Nice, interesting. Thanks for the info... I will search about it shortly...

I've yet to understand why I am not getting enough feedback for my application...
This is the default forums for ubuntu, isn't it? I was expecting something... bigger?
If I may enlighten you.

This is the Programming Talk forum. The content is not necessarily related to Ubuntu and it attracts people who are programmers, but not necessarily Ubuntu developers or anybody at all with packaging knowledge.

It also doesn't attract a lot of users.

If you wanted feedback on your coding style, this would be a good place to put it. If you want feedback on your package, you'd best look somewhere people who make packages hang out (like the forum I linked in my first post). If you want feedback from users, maybe there's somewhere else that would be appropriate; I don't know. Like I mentioned before, I don't even use Ubuntu and in fact this is the only forum on this site I frequent; everything else is boring to me.

Which is also why my only feedback for you had to do with your commenting style. I don't know anything about packaging and I can't install .deb files compiled for Linux without a lot of hassle (FreeBSD), so I haven't even run your program. There are probably plenty of other folks on this forum who are in a similar situation. It's not that you're not reaching a broad enough audience; you're just reaching the *wrong* audience.

---

### Post by Paradox27 on 2012-06-17
> **trent.josephsen said:**
> If I may enlighten you.

This is the Programming Talk forum. The content is not necessarily related to Ubuntu and it attracts people who are programmers, but not necessarily Ubuntu developers or anybody at all with packaging knowledge.

It also doesn't attract a lot of users.

If you wanted feedback on your coding style, this would be a good place to put it. If you want feedback on your package, you'd best look somewhere people who make packages hang out (like the forum I linked in my first post). If you want feedback from users, maybe there's somewhere else that would be appropriate; I don't know. Like I mentioned before, I don't even use Ubuntu and in fact this is the only forum on this site I frequent; everything else is boring to me.

Which is also why my only feedback for you had to do with your commenting style. I don't know anything about packaging and I can't install .deb files compiled for Linux without a lot of hassle (FreeBSD), so I haven't even run your program. There are probably plenty of other folks on this forum who are in a similar situation. It's not that you're not reaching a broad enough audience; you're just reaching the *wrong* audience.

Ok, yes, I understand. Is it ""legal"" to start a new thread there with quite the same topic as this one?

---

### Post by trent.josephsen on 2012-06-17
I think that would be fine. Cross-posting is annoying when it unnecessarily duplicates effort or is off-topic or spammy; none of those is the case for you.

---

### Post by Paradox27 on 2012-06-17
> **trent.josephsen said:**
> I think that would be fine. Cross-posting is annoying when it unnecessarily duplicates effort or is off-topic or spammy; none of those is the case for you.
DONE: [http://ubuntuforums.org/showthread.php?p=12034205](http://ubuntuforums.org/showthread.php?p=12034205) :)

Thanks alot!

---

