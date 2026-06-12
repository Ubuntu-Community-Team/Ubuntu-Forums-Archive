---
title: "Tabiture program for linux..."
date: 2007-03-13
forum: Programming Talk
---

### Post by rekahsoft on 2007-03-13
Hi all, i have been trying to get a program called tabit working and linux using wine and it just is a pain in the ****.  I believe it is basically imposable with the current state of midi in wine. I know that program a program for tabiture is deeply needed for linux and can cause some people not to switch (my brother "needs" his tabit program). So i was wondering if somebody would be interested in helping out in developing a good tabiture app for linux (gnome)...it could be writting in python, C, C++, C#, or whatever we decide. It would be open-source, it would have to support proprietary file formats from other tabiture programs like tabit, guitar pro, etc... Let me know what you think and if you would like to help out.

---

### Post by Wybiral on 2007-03-13
Tabbit was a good program... Guitar Pro 5 was even better!!!

Those are probably the only two programs I miss from windows... *** Sad sniffle ***

But, I found KGuitar and it's not bad, very tabbit-esque.

I'm willing to help write a gnome tabbing program, I haven't really messed with midi's or anything but I can help with the chord/interval/scale finding features (supposing you want to implement musician helping features like those)

Actually, if it's in C or C++, I can help bind a python interpreter to it so that users can write plugins and scripts! I think that would make it stand out in terms of tabbing programs.

So, whenever you get started, feel free to contact me.

---

### Post by rekahsoft on 2007-03-13
sweet...i as well do not know much about midi but i am sure i can learn...i would be willing to start at anyt time :D

---

### Post by rekahsoft on 2007-03-13
btw i like the idea of a built in python interpretter...what language would you prefer the app be written in?

---

### Post by Wybiral on 2007-03-13
I think C or C++ would be great. I must also warn you that I suck with GUI's... But, I'm good at interfacing with python, and I know a lot about guitar theory. I'm also pretty good at optimizing C and C++ code for size or speed.

But I'm not sure where to begin with this project, probably with the interface. Making a pleasantly editable tab sheet seems like one of the hardest parts.

OH, another thing... The notes should play when you write them. That's one thing I'm not fond of about KGuitar, you have to hit play to hear a particular note... It should play the notes as you're tabbing it out.

But, I can probably write some algorithms to analyze the notes and determine the most likely scale/key relationship, and preprogram the common scales and chords in so they can use them while they're writing.

But like I said... The GUI is probably the hardest part for me.

---

### Post by rekahsoft on 2007-03-13
ok...i would prefer C++ because i do not know C yet (it is on my to learn list)...also i do not know gtkmm so i will get learning that so that i can start making the interface...we have to find a good midi library for C++...give me a bit...in the mean time if you could find a good library that would be great...

---

### Post by rekahsoft on 2007-03-13
ok...i have started a thread looking for a midi lib ([http://ubuntuforums.org/showthread.php?p=2293756#post2293756)...i](http://ubuntuforums.org/showthread.php?p=2293756#post2293756)...i) would like to keep the option of C# open because it is really easy and nice for quick development...even if we did end of using C# we can link to C++/C code so it would work fine :D more research is definitly need before we start doing any coding :D...alsoI have to learn gtkmm or gtk#...i know part of pygtk but i have not started learning gtkmm or gtk#...so when we decide what language is best for the job i will start focusing on it. I know C++ better then i do C# (i just started learning C# a little while ago...anyways we will see..let me know what you think. Also if we were to create to project on a server where would it be? (launchpad, sourceforge, google code, on the gnome site (if possable), etc..)

---

### Post by Wybiral on 2007-03-13
OK, I don't have much experience with C#, I suppose this could be a good project to learn with. But once we get the core done and the python plugin system, I'll probably just help out from the python end. You know... We could also use shared objects and can people could write and compile plugins with C/C++.

I've been looking for midi lib's myself and haven't been too successful!

---

### Post by rekahsoft on 2007-03-13
yes it would be a good project ot learn C#...i myself just started learning so we would be learning together...also if it is writen in C# it has the possablity of easily being cross platform :D we'll see...i really only care about the linux side but it is a possablity...

---

### Post by pmasiar on 2007-03-14
> **rekahsoft said:**
> btw i like the idea of a built in python interpretter...what language would you prefer the app be written in?

[http://wiki.python.org/moin/PythonInMusic](http://wiki.python.org/moin/PythonInMusic) gives you plenty of ideas. You may want to create GUI in something simple yet flexible like Pygame, and/or integrate it with KeyKit. IMHO doing non-performance critical parts, like GUI, in C++ is lots of hard work and not much fun - better approach is IMHO start with Python, and optimice later in C parts not fast enough. Don't guess where bottlenecks are - measure.

Just my $0.02. Have fun!

---

### Post by lnostdal on 2007-03-14
this is an interesting project .. i also play the guitar - in fact i love playing guitar :)

i agree with pmasiar; do not focus on optimization by using a less expressive/flexible language/environment .. get it right and "pretty"(#1) first

while C# certainly seems good, doing this with an _interactive_ language/environment like Python will give you guys an extra boost

i'm sad to say i cannot participate much at this time .. i got to focus all coding-time on generating income for living-expenses .. i _might_ hack togheter a patch or two - maybe more later :)

#1: "pretty" also means good algorithms and software design regardless of language/micro-optimization .. these are the things which give the best optimizations anyway .. and they take much less coder time to do or get right in a more expressive/flexible language/environment

edit: and yes; just casual suggestions from me this .. :}

---

### Post by rekahsoft on 2007-03-14
ok...does anybody know of a good place to start learning about creating widgets in gtkmm? or be willing to help me out. Thanks

---

### Post by lnostdal on 2007-03-14
You might already have seen this, but: [http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/ch25.html](http://www.gtkmm.org/docs/gtkmm-2.4/docs/tutorial/html/ch25.html)

..as mentioned there you can also create a subclass of some already existing widget.

---

### Post by Wybiral on 2007-03-14
Well, I'm not going to be much help with the GUI, so I'm basically going to focus on the midi library. I think this should be done in C since it's pretty low-level stuff. Also, I'm going with portmidi as the interface, and it was written in C.

But, C is really easy to interface with either C++ or Python, so I think it's a good language to write the lower level midi communication stuff.

BTW, Inostdal, I've actually noticed a trend in programmers being guitarist's. I wonder why that is.

---

