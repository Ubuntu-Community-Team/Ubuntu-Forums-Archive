---
title: "C++ IDE's maybe Im just stupid"
date: 2007-06-05
forum: Programming Talk
---

### Post by headnoodle on 2007-06-05
Hi guys, I am a long time vb.net, vb6 programmer and have decided to learn c++.  I have been learning for a few weeks now using Kate as the editor.  I decided to try an IDE but the damn things seems so convoluted to use.  All I want to do is be able to create a single cpp file program and be able to debug it (step through it) line by line.  There seem to be so many things I need to setup to get it working properly.  Arrrrrrg, I feel like throwing my laptop through the window :P.

Can anyone give me any pointers?

Cheers,

Headnoodle.

---

### Post by networkfu on 2007-06-05
I've recently just started learning C++ as well. I'm using the Anjuta IDE, its pretty easy to use, I'm still trying to work out the debugging stuff but it looks like it would have all the things you would need.

its installable via synaptic.

---

### Post by headnoodle on 2007-06-06
Thanks, I will have a look at that.  Can you recommend any good guides on using it, or is the manual quite comprehensive?

---

### Post by networkfu on 2007-06-06
I haven't looked at any guides myself just the help files when i need to know how to do something, but they have online manual so i think thats all you would need. I was able to work it out without guidance for most things, its only when i got into the debugging i wasn't quite sure what i was doing.

---

### Post by Rui Pais on 2007-06-06
Hi,
anjuta is nice, but recent versions are a little unstable (sometimes more then unsatble) and Ubuntu version of that specific package uses the latest sources instead of the stable ones... And anjuta is more gnome oriented.
If you use KDE a better approach would be KDevelop.

Both are heavy IDES for GUI development. 
If you are only interested in learn basic c++, check codeblocks (check the [night builds]("http://forums.codeblocks.org/index.php/board,20.0.html") not the old "stable") or openldev (there are debs at [http://www.getdeb.net](http://www.getdeb.net)). 
Even lighter are text processors with support for compile/debug, like emacs, geany, scite or scribe.

---

### Post by headnoodle on 2007-06-06
I have had a look at Kdevelop and it does look nice but as you said it look very orientated towards UI development types which I will be looking to get into, but not just yet.  I never realised text editors had built in debugging and compilation support, I really do like using Kate but It would be nice to have a few extra features on it.  I will have a look at codeblocks tonight.  Hopefully it is easy to setup.

---

### Post by Rui Pais on 2007-06-06
> **headnoodle said:**
> ...  I never realised text editors had built in debugging and compilation support, I really do like using Kate but It would be nice to have a few extra features on it.  I will have a look at codeblocks tonight.  Hopefully it is easy to setup.

some of those  i mentioned (and others) are powerful text editors with syntax color and autocompletion (for C and other languages) that have embedded a terminal and allow running the compiler with a combination of keys,  avoiding the boring type of g++ -o ... and some (like emacs) have support for DDD or making basic makefiles. 
And some, like scite, are usually faster then kate or gedit, so it can be used as the normal text reader, beating the default ones of kde and gnome :)

But as IDE, for me codeblocks is the best in terms of features/heaviness and it's very independent of implementation or even of platform. 
Maybe Openldev is better, when i found that i was so used to codeblocks, that never take time to explore it more...

---

### Post by AaronMT on 2007-06-06
For such a simple program I always recomment you learn and use Vi/Vim. A complicated GUI is only recommended for a big project.

---

### Post by miggl on 2007-06-07
I have used CodeBlocks in the past: [http://www.codeblocks.org/](http://www.codeblocks.org/)
However, I am unsure if this is still being actively supported (at one point it was put on hold about a year ago or so).

---

### Post by WW on 2007-06-07
Code::Blocks is *very* active: [http://forums.codeblocks.org/index.php?board=20.0](http://forums.codeblocks.org/index.php?board=20.0)

---

### Post by miggl on 2007-06-07
> **WW said:**
> Code::Blocks is *very* active: [http://forums.codeblocks.org/index.php?board=20.0](http://forums.codeblocks.org/index.php?board=20.0)

Ah! Thanks for that. I was looking at the old codeblocks site, which doesn't have its download link updated. I'll have to check out the newer version here. :)

Cheers,
Mike

---

### Post by yabbadabbadont on 2007-06-07
The current nightly build has an unsatisfiable dependency on Feisty.  I'm guessing that you have to have the backports repo enabled to get a newer version of libwxbase-2.8-0.

---

### Post by headnoodle on 2007-06-07
> **yabbadabbadont said:**
> The current nightly build has an unsatisfiable dependency on Feisty.  I'm guessing that you have to have the backports repo enabled to get a newer version of libwxbase-2.8-0.

put this in your sources.list

deb [http://apt.tt-solutions.com/ubuntu/](http://apt.tt-solutions.com/ubuntu/) feisty main

more info can be found here  [http://www.wxwidgets.org/downloads/](http://www.wxwidgets.org/downloads/)

---

### Post by Rui Pais on 2007-06-07
> **yabbadabbadont said:**
> The current nightly build has an unsatisfiable dependency on Feisty.  I'm guessing that you have to have the backports repo enabled to get a newer version of libwxbase-2.8-0.

i do not tried to compile it yet wit the 2.8 but it compiles normally with the 2.6 (i just did it tight now to be sure).
And on the  [nightly builds]("http://forums.codeblocks.org/index.php?board=20.0") forum there are ubuntu debs for both libraries made by users :)


edit: you were faster headnoodle. 
But its more fun to build our own :)

---

### Post by headnoodle on 2007-06-07
> **Rui Pais said:**
> 

edit: you were faster headnoodle. 
But its more fun to build our own :)

Fun!, my god I never get anything but a headache building from source.

---

### Post by Rui Pais on 2007-06-07
{snapped}
strange ... i made an edit on this post and instead of edits appear here, the forum made a new post (bellow)...

---

### Post by Rui Pais on 2007-06-07
> **headnoodle said:**
> Fun!, my god I never get anything but a headache building from source.

Strange. The purpose of make code is building it... the purpose of install an IDE is to make code and build it.
With Ubuntu it's just a matter of apt-get the needed -dev package.

Anyway, [here]("http://ubuntuforums.org/showpost.php?p=2039057&postcount=16") a mini "how-to" on how-to make you own deb i put on another thread (a dup of this), based on a previous post on how-to build from code (it's a mtter of 4~5 command lines ;))

---

### Post by yabbadabbadont on 2007-06-07
Thanks for the pointers to the debs, but I'll just stick with vim for now.

---

