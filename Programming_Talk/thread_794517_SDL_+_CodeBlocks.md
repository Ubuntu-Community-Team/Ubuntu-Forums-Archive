---
title: "SDL + Code::Blocks"
date: 2008-05-14
forum: Programming Talk
---

### Post by Caz'ar Xiladys'varion on 2008-05-14
Hey...kinda new to this, but I'm trying to install SDL for code::blocks. I downloaded all the (supposedly) needed SDL stuff from synaptic, and when I try to compile the pre-made hello world app, I get an error "cannot find -lalld"

any ideas?

---

### Post by Caz'ar Xiladys'varion on 2008-05-16
anyone? =/

---

### Post by Caz'ar Xiladys'varion on 2008-05-16
the exact error is:

-------------- Build: Debug in test ---------------

Compiling: main.cpp
Linking console executable: bin/Debug/test
/usr/bin/ld: cannot find -lalld
collect2: ld returned 1 exit status
Process terminated with status 1 (0 minutes, 1 seconds)
1 errors, 0 warnings

---

### Post by Caz'ar Xiladys'varion on 2008-05-16
I'm getting the exact same error when trying to compile with allegro.

does no one know what's wrong? I would like to be able to actually compile something soon...

---

### Post by moma on 2008-05-17
Hello,

You do not need (lib**alld**.so) library to compile, link and run SDL-applications. I don't think it is wise to mix Allegro and SDL. Can you do it?

Create a SDL application and check the compile options. 
Check also under Debug and Release. It should look like this.
[[img]http://bildr.no/thumb/199627.jpeg[/img]](http://bildr.no/view/199627)

Check the library linking options. Check also under Debug and Release and remove the "alld" library if you see it. 
[[img]http://bildr.no/thumb/199628.jpeg[/img]](http://bildr.no/view/199628)

**Browse to this guide and read the [COLOR="Red"][ Note 7][/COLOR] carefully: **[http://www.futuredesktop.org/codeblocks_on_ubuntu_8.04.html](http://www.futuredesktop.org/codeblocks_on_ubuntu_8.04.html)

Some SDL tutorials: [http://lazyfoo.net/SDL_tutorials/index.php](http://lazyfoo.net/SDL_tutorials/index.php)
--------

[COLOR="Red"]EDIT:[/COLOR] I can help you to set up an Allegro-project if you like?
The first thing is to check the Allegro-demo (a shooter game). 
Install it 
[COLOR="SeaGreen"] sudo apt-get install allegro-demo[/COLOR]
Start it 
[COLOR="SeaGreen"]/usr/games/all-demo[/COLOR]

+ Check the allegro-examples
[COLOR="SeaGreen"]sudo apt-get install allegro-examples[/COLOR]
Run them
[COLOR="SeaGreen"]allegro-examples[/COLOR]
----
Study the manuals and source of the demo game and example programs.
[COLOR="SeaGreen"]sudo apt-get install liballegro-doc[/COLOR]
Read the docs
[COLOR="SeaGreen"]firefox /usr/share/doc/liballegro-doc/html/index.html[/COLOR]
----
You will need to use these in your projct's build options
`allegro-config --cflags` 
`allegro-config --libs`

---

