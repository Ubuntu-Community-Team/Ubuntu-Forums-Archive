---
title: "Really Simple Question regarding system() in c++"
date: 2007-02-21
forum: Programming Talk
---

### Post by jordoex on 2007-02-21
I haven't programmed a thing in c++ before, im making a automated cd ripper.  How do I get the output of a command using system()?
I've only used Java and their APIs are much more useful.

---

### Post by SoggyCornflake on 2007-02-21
> **jordoex said:**
> I haven't programmed a thing in c++ before, im making a automated cd ripper.  How do I get the output of a command using system()?
I've only used Java and their APIs are much more useful.

I'm curious:  Are you  using C++ because it's a better tool choice for making a CD Ripper?

or are you using a CD Ripper  program to be a good project to learn C++


I'm guessing the output is a string since system() invokes a terminal session and runs whatever command that is embedded.

---

### Post by xtacocorex on 2007-02-21
I don't think system() returns anything.  I tried using it in a code to see if a file was in a certain directory, but ended up checking fstream error codes.

---

### Post by po0f on 2007-02-21
jordoex,

Why are you using system() and not the CD ripping libraries directly?

---

### Post by WW on 2007-02-21
"I don't think system() returns anything. ..."

"I'm guessing the output is a string ..."

Why are you *guessing*?  Find the documentation and read it!  For example: [http://www.cplusplus.com/reference/clibrary/cstdlib/system.html](http://www.cplusplus.com/reference/clibrary/cstdlib/system.html)

---

### Post by jordoex on 2007-02-21
Wow, i can't believe it. 4 posts and none of you came up with the solution.  I figured it out myself about a half hour after I posted.  All I have to do is system(command >> outputfile)

And I'm using system because it's easier to config than using the libraries and Im using c++ because yes, i want to learn it and none of the GUI rippers are easy to config and can rip all of the tracks to wav, save the cddb data and then encode them to wahtever later really easily to rip lots of cds with as little time spent by the user inserting and ejecting CDs.  Im doing this for a friend, and partly for myself.  Also, I want to learn how to use QT designer and KDevelop and such, as, personally, I think KDE is better than Gnome.(Please don't make this into a KDE vs Gnome thread, there are other ones for that)

---

### Post by xtacocorex on 2007-02-21
> How do I get the output of a command using system()?
WW, I know system returns the exit code of the command that it ran, but it doesn't return a string value of data, which is what the OP asked. I also responded to this quickly as I was leaving for an appointment, which I shouldn't have done.

I'm glad you (OP) figured it out though.

---

