---
title: "need advise"
date: 2012-10-30
forum: Programming Talk
---

### Post by jgw on 2012-10-30
I have a problem.  Almost 10 years ago I developed a package of business programs.  I used plain, vanilla, c and they all seem to compile without error.  My problem is that they run in a DOS window and something strange has happened.  After 10 years of working without a problem, problems are starting up.  I used codebase for the database (dbase) and Cscape for the interface (for anybody who has been around for a long time might recognize these packages).  

Anyway, people are using the programs and are having problems so I thought I might add a gui and, possibly, a different data base and see if I can get this stuff to run in something other than a DOS window. 

I am considering glade and anjuta for the interface and am not sure about the database although what I already have just might work. The reason for my choice of glade and anjuta is that I have messed with them some and they seem pretty straightforward.

I would appreciate anybody's thoughts on this stuff.  I would hire this job out but am not exactly rich and, I suspect, its pretty straight forward.

Thank you......

---

### Post by Tony Flury on 2012-11-01
Do you still want your code to run on DOS, or are you trying to make a unix version? Assuming you want tou build a unix version here are some comments : 

the thing to remember is that Anjuta is simply an IDE, There are plenty of other IDEs you can use, and they will all create an executable which will run in he same way, you can also use different languages under the same IDE.  You could even not use an IDE and just use text editors and make files and still get the same result. I think a more important choice is the language - stay with C or go with something else ?

Glade is graphical designer for Gtk. It is entirely possible (I know I have done it) to implement a complex gui with just code, and not using glade - as Gtk offers all the callable features you need to build a GUI as you go. 

As for the database depend on how much data you will have etc you have given no clues on that one.

---

### Post by jgw on 2012-11-01
Thank you for the reply

I want to abandon DOS (support is waning and it is not, I suspect, acting properly)  The code is pretty simple, as far as the gui stuff is concerned (the programs are well functioned and, I think, easily interfaced).  I just thought something like glade would be easier.  I mentioned anjuta because its pretty well integrated.  I messed with it a couple of years ago. Its different now but I think I can work with it.  I have a pile of programs to deal with and I just thought those might make the job easier.  I have tried just coding the gui's but......

In theory I can also use glade if I want to do a compile for both ubuntu and windows.  My problem is that users are now using windows machines.  Since one of the users is my own kid I am trying to stay friendly.  Given that other packages, that don't do the job as well, are going for around 20 grand, with serious monthly maintenance fees (waaaay overpriced!) he is willing to give me some latitude <g>

I suspect I might switch the databases to sql as there seems to be a lot of stuff available with that and I can probably use light as there is, really, not all that much data invoived.

As I have said, I have been, pretty much, away from this for about 10 years but have been studying up on it for about 2 weeks now as things are mysteriously crashing and it seems to be coming back.

The biggest dbase dbf file is around 20mb.

---

### Post by trent.josephsen on 2012-11-02
[chipppy's situation](http://ubuntuforums.org/showthread.php?t=2074752) is not too distant from yours. There might be some useful advice in that thread, although since you're starting from an existing codebase it's probably not a question of selecting a language to write in. As for my own reply, I'd still suggest SQLite if you're thinking of changing your database format, and for much the same reasons as described there.

---

### Post by jgw on 2012-11-02
Thanks for the reply.  I had actually come to the same conclusion, insofar as the database is concerned (sql lite).  Now I have to start figuring out the gui stuff.  Its changed a lot since I messed with it.  I am studying on it.  I still suspect glade is the way to go but its going to take a little time <g>

Thanks again!

---

