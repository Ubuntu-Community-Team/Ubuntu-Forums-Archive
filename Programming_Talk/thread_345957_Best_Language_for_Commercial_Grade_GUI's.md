---
title: "Best Language for Commercial Grade GUI's"
date: 2007-01-25
forum: Programming Talk
---

### Post by phossal on 2007-01-25
What is the easiest *and best* language to build commercial-grade GUI's in? Is it true that C++ is still significantly dominant?

---

### Post by amo-ej1 on 2007-01-25
I think you question is wrong. C++ by itself doesn't do anything at all on a GUI level basis. Personally I'd think you should investigate the frameworks people use for GUI rather than the language they're written in. Does selecting Java automatically imply the use of Swing or AWT ?    I think you should first ask which framework and after that in which language the framework is used.

---

### Post by Tomosaur on 2007-01-25
Most people tend to stick with already existing libraries, the GTK libs, for example, are commonly used on Linux. They're available for many different languages, so it's really just a matter of preference. If you prefer C, use the GTK for C, if you prefer Python, use GTK for Python etc etc etc. If you want to write your own libraries, that's your choice (and a lot of work), but I guess most people just tend to stick with what's already there.

---

### Post by phossal on 2007-01-25
Even using the GTK, which language would *you* most likely use in order to build an app that was GUI-intensive? (I'm guessing, not Java)

---

### Post by Tomosaur on 2007-01-25
Whichever language was best for the actual application, I guess. I really don't think the question is so clear cut. If I'm trying to write a physics simulation program, then I'd use C/C++, for obvious reasons. If I was writing a photo album, I may use Python. It just depends what you're doing.

---

### Post by lnostdal on 2007-01-25
Performance is seldom an issue these days if you're only taking into account human interaction with the interface/GUI-part of a solution. Thinking relatively there are eons between each human initiated event. Pick any language for this.

---

### Post by kalikiana on 2007-01-25
If you want to be productive choose Python - although this has nothing to do with GUI at all. If you'd asked what GUI I had said Gtk because it's really comfortable to code for and use as well.

---

### Post by phossal on 2007-01-25
And, before delivery, how do I protect that source code? Oh, and I'm working in Windows only environment.

---

### Post by lnostdal on 2007-01-25
Obfuscating then running it through py2exe is an option but this will probably make debugging harder. You'll be getting reports that show backtraces into the obfuscated version; it'll be harder to make sense of I think.

..but maybe it's not needed in the first place? Maybe you're actually developing something that depends on server-access for valuable data? Just add a login and a stolen version will be worthless.

---

### Post by runningwithscissors on 2007-01-25
C for GTK+, C++ for Qt. Both toolkits have libs for Unix and Windows.

Or there are a host of language bindings available for both toolkits. PyGTK, PyQt, gtkmm, GTK#, etc. Use whatever you like.

---

