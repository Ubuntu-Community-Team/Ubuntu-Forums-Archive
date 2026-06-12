---
title: "Best tool for the job - Language choice question"
date: 2007-11-19
forum: Programming Talk
---

### Post by bobrocks on 2007-11-19
Evening everyone, it's one of those threads the – What language should I use threads.  It's also quite long, sorry about that.

I intend to write a windows explorer clone, one that does exactly what I want.  I know there is lots out there but there are few cross platform ones that I like.  I want to make a simple, hopefully very quick one for me to use.

Now it comes to language choices, I have been in a Java world for a while now.  I use it all almost all day at work for enterprise, quick scripts (usually perl for this actually) and desktop apps.  This gives me one huge advantage if I were to chose Java, familiarity and speed.  So much so that I decided to mock up a prototype on Sunday and in a day I had the basic windows explorer tree/table combo linked and working together with a queue history for the back/forward buttons.  In this short time I noticed some serious limitations in using Java for this project.

1)usability – my use case for explorer is to open it quickly find what I want and close it again.  The start up time for the Java app is, as usual, poor with all the loading of things it has to do.  Once up it is very fast in linux even on big directories like my bin folder.  But it doesn't really fit the use case.  I know this is being worked on in interim updates to 1.6 but no real numbers of what effect it will have.
2)Limitiations in the file API for java.  It seems in windows it is very slow for some reason.  Also when you query for file data like size it makes a new request to the file system for each property rather than getting them all when it interogates it the first time.  You have access to only three properties, modification time, size, isdirectory.  There is ways to get the others but they are not eligent. There is more problems, and they are all too be sorted in an upcoming JSR, but that might not even make it into 1.7 next year.

I have more and more reasons but I don't think I should waffle on anymore about it.  Don't get me wrong though, I really do like Java and I enjoy programming in it.  I also know using osgi I could build a nice plugin based system that could do most things I wanted but there is too much doubt in my mind that the language choice would effect even me using it.  But maybe it's time to expand my horizons and chose a language more suited for the task.

So I look to alternatives, outside Java apart from some Perl from back in the early days I don't really know any other languages.  I do like the sounds of Python and it is meant to be easy to learn, it is also OO and does memory management.  But I don't see that many desktop apps that are built in python, please prove me wrong.  Out of all the things I use I can only really name Deluge, which is based on a C++ torrent library at its core, I believe.  But it is very fast and very lightweight.

So after all this I guess I should explain my question.  What language would *you* recommend and why, even if it is Java!  I have no time limit, It's not like i'm going to die if I don't have this program in the six months time, but it's something to aim towards creating.  I have access to a reasonably varied library at work so I should be able to borrow books for most major languages, obviously not something like D if you were to recommend that.  But I'd rather get other peoples opions than read lots of prefaces and realise every language is perfect.

Cheers for any input

---

### Post by LaRoza on 2007-11-19
I would look at the Nautilus code, Dolphin code, and Thunar code first, to see what is involved. It is likely going to involve C or C++ if you use QT.

Python is a great language, and probably could be used, I am not sure of how complicated Explorer is. You can (should?) code it in Python and write only the most memory intensive parts in C.

-EDIT I don't know why you are making this app, but it looks like a personal project and not fulfilling a gap in existing applications.

---

### Post by pmasiar on 2007-11-19
if you need really fast file manager, you can look at midnight commander (mc). It is not GUI, but with curses they accomplish near-GUI experience. Is really fast, and extremely flexible.

---

### Post by kknd on 2007-11-20
Are you shure that you want to make a portable file manager? Beacuse there's so much differences between filesiystems from *nix and Windows, etc.

I would do it in C++ or Ocaml (evil).

---

### Post by bobrocks on 2007-11-20
> I would look at the Nautilus code, Dolphin code, and Thunar code first, to see what is involved. It is likely going to involve C or C++ if you use QT.

Python is a great language, and probably could be used, I am not sure of how complicated Explorer is. You can (should?) code it in Python and write only the most memory intensive parts in C.

-EDIT I don't know why you are making this app, but it looks like a personal project and not fulfilling a gap in existing applications.

It's kind of 50/50 why I am making this.  I doubt anyone else will want to use it but it is fulfilling a gap for me.  I've tried to use Nautilus, thunar, dolphin, krusader, konquerer, rox, xfe, various commanders etc.  Dolphin and rox are stupidly fast but rox especially I find very annoying to use.  XFE is sort of what i'm looking for but I have had nothing but trouble with it since I first use it about a year ago.  So I intend to make something simple, I know roughly what is involved already, if I added a sort of extension2command map for files my prototype would be a very simple explorer already.

> if you need really fast file manager, you can look at midnight commander (mc). It is not GUI, but with curses they accomplish near-GUI experience. Is really fast, and extremely flexible.

I don't need really fast, I meant that I wanted it to start up very fast.  The java one I did is very fast at listings in linux, much faster than I expected but it takes to long to load in especially from a cold start.  I'm sure most file operations will be tuned in all languages for the listings.  
I'll give mc a shot tonight, at the moment I use a bunch of aliases I have for the command prompt and do everything there anyway.

> Are you shure that you want to make a portable file manager? Beacuse there's so much differences between filesiystems from *nix and Windows, etc.

I would do it in C++ or Ocaml (evil).

It's a fair point, I'm sure I'll find these things out soon enough, other than some java ones I don't really see many cross platform ones.  It's mostly for linux as I still have explorer in windows and I only use windows at work.  But I'd see soon enough how difficult it would be.

I was assuming C/C++ would be the choice, I did always mean to learn C/C++ I just assume it will be a very long process.  I was unlucky (or maybe lucky) that we were the first year at my uni to do Java instead of C++.  I wasn't to sure about python being viable or not, I was hoping some pythonians would come along and say it would be perfect.  Python should be easy to pick up with a complete OO background and experience in Perl.  Maybe i'm just blinded because it's seems the buzz language just now.

Thanks for all your comments

---

### Post by smartbei on 2007-11-20
Well, Python is definately an option, and you definately got pythonians replying but they did not specifically recommend Python. I believe this is because the most important thing for you is startup time, which in Python is not minimal (though nowhere near as bad as Java). For really fast startup (meaning low memory usage and little initialization) you will probably want C/C++. Python might be fast enough though, and it will be far faster to develop in.

---

### Post by pmasiar on 2007-11-20
Someone started file manager in Python, clone of midnight commander (which is very old and crufty C code), called LFM. 

MC would start the fastest (has no GUI to initialize), but Python LFM might be just fast enough - and much easier to hack on than using Java, C or C++. IMHO, YMMV.

---

### Post by bobrocks on 2007-11-20
Looks like I will have to make a decision then.

Python + something like wxPython

or C/C++ with something like wxWidgets.

Even with my programming knowledge I can see it taking a long time to pick up C/C++ but I suppose for my future employment it can be no bad thing.

Then there is python that I can see me picking up reasonable quickly, can definetly do the job just don't know about how the performance will be.  With java it was easy for me to mock up a prototype and profile it and find where it was going to be problematic.  

hmmm.

---

### Post by pmasiar on 2007-11-20
Why you worry about the performance? IMHO you should worry first about your program working correctly. Performance is not a problem until you can prove it is a problem. Premature optimization is root of all evil.

---

### Post by bobrocks on 2007-11-21
> **pmasiar said:**
> Why you worry about the performance? IMHO you should worry first about your program working correctly. Performance is not a problem until you can prove it is a problem. Premature optimization is root of all evil.

Premature optimization when designing and writing the code is the root of all evil.  Taking performance into consideration when choosing the right tool for the job is a good thing.  You could write this in any language the real difference is in complexity and the possible performance you can achieve if done correctly.  As I am using this as a project to learn a new language I am taking into consideration the requirements and problems for this type of project, one being performance.

---

### Post by pmasiar on 2007-11-21
> **bobrocks said:**
> Premature optimization when designing and writing the code is the root of all evil.  Taking performance into consideration when choosing the right tool for the job is a good thing.  

I agree 100%. I re-read your original post, you do have enough experience to distinguish between the two. Quite often beginners post here, concerned about Python performance, without having a clue how to build the app they want in C++ "for speed".

Quite often you can build app in Python, measure the bottleneck, and recode that part only (5% of code) as C library. As a result, you can have almost all flexibility of Python, with almost C speed.

---

