---
title: "C++ ide"
date: 2010-04-12
forum: Programming Talk
---

### Post by FinalShot on 2010-04-12
Looking for an IDE, or a compiler and decent text editor.

I'm use to Visual C++, so I'm looking for something similar to that.

---

### Post by conradin on 2010-04-12
geany

---

### Post by Simian Man on 2010-04-12
Code::Blocks is nice and simple and should be familiar to you.  I'd recommend that.

---

### Post by FinalShot on 2010-04-12
I'll try them out, but first I need the G++ compiler. I been looking through [http://gcc.gnu.org/](http://gcc.gnu.org/), and I can't find a simple download, link.

---

### Post by Compyx on 2010-04-12
GCC is most likely already installed, to get the library headers, run:
```

sudo apt-get install build-essential

```

Don't download the stuff you need, all you need is available through the repositories. Just fire up the package manager and select what you need: System -> Administration -> Synaptic Package Manager.

---

### Post by FinalShot on 2010-04-12
Yeah thanks, I'm come from windows :lolflag:

---

### Post by phrostbyte on 2010-04-12
One click installs. :)

Geany is a lightweight IDE:
[geany]("apt://geany")

Another think that might be worth looking into:
[qtcreator]("apt://qtcreator")

More focused for Qt development, but pretty decent for C++ in general.

There is also Eclipse, Netbeans, MonoDevelop, Anjuta, and many many others.

---

### Post by matthew.ball on 2010-04-12
If you're on Ubuntu, try: [FONT="Courier New"]sudo apt-get install build-essential[/FONT] - this will install the C++ compiler.

I don't know if Visual C++ includes a GUI builder, but you'd be hard pressed to find a decent C++ IDE under Linux which did.

As far as I can recommend, just become familiar with [Makefiles]("http://www.gnu.org/software/make/") and the GNU debugger [(gdb)]("http://www.gnu.org/software/gdb/"). Use whichever editor you are most comfortable with for writing the code (gedit, vim, emacs etc), but learning how the g++ compiler works and debugging with gdb are pretty essential for a Linux developer I would say.

Anjuta does a fairly good job as a mature IDE (implementing both of the above utilities). Though I did find it incredibly complicated when I wanted to do simple projects, and I haven't looked at it since.

As a side note, if you are interested in learning new things, emacs couples the above utilities (and more!) into a very nice editor (one editor to rule them all sort of deal). You can check out google for results on "emacs with gdb" and "emacs with makefiles" if you want to take this further.

---

### Post by MCVenom on 2010-04-12
Vim is a good editor if you're willing to learn it; Gnome Vim (GVim) has a compiling feature built in, and running vimtutor in the terminal will teach you the basics in a half hour. :D

Geany is a great IDE, and much more... conventional ;)

---

### Post by FinalShot on 2010-04-12
So far I don't like either Geany or Code::Blocks, I'll check out the suggested ones though.

---

### Post by Simian Man on 2010-04-12
> **FinalShot said:**
> So far I don't like either Geany or Code::Blocks, I'll check out the suggested ones though.

What did you not like about them?  If you more clearly say what you're looking for, you'll get better answers.  There are a **ton** of options for programming under Linux, so people randomly suggesting things until you like one might take a while :).

---

### Post by FinalShot on 2010-04-13
> **Simian Man said:**
> What did you not like about them?  If you more clearly say what you're looking for, you'll get better answers.  There are a **ton** of options for programming under Linux, so people randomly suggesting things until you like one might take a while :).

I want the visual studio feel :lolflag:

---

### Post by Simian Man on 2010-04-13
> **FinalShot said:**
> I want the visual studio feel :lolflag:

Ah, well I have tried most of them and Code::Blocks feels the most like VS to me.  You can also try Monodevelop which is great for C# but I haven't tried it for C++ but apparently it supports it now.

---

### Post by ubun2warrior on 2010-04-13
You can try Anjuta a graphical interface for programming in c++.

---

### Post by TheStatsMan on 2010-04-13
> **Simian Man said:**
> Ah, well I have tried most of them and Code::Blocks feels the most like VS to me.  You can also try Monodevelop which is great for C# but I haven't tried it for C++ but apparently it supports it now.

  I also found Code::Blocks to be most similar to VS. Which is why I went to it when I moved from Windows. Fortunately, latter on I found there were better ways of doing things in linux (than the VS way), but at least for a start it was mostly familiar.

---

### Post by Søren on 2010-04-13
from what i can tell, linux has a different (more pure) philosophy to ide's than windows. if you are looking for a linix manifestation of VS you will be disappointed. IF those are your needs (not saying there's anything wrong with that) then you might as well stick to windows.

---

### Post by fallenshadow on 2010-04-13
Well if you really, really want something similar to Visual Studio you can check this out. However it isn't C++, more like visual basic.

[http://www.realsoftware.com/realbasic/](http://www.realsoftware.com/realbasic/)

Also you would need to pay for it! :lolflag:

--
On a serious note, I had a go with the trial and it is very good, probably better than Visual Studio. You can compile your program for all platforms just by ticking the boxes.

As a test I made a web-browser with 1 line of code and compiled it for all platforms. :D

---

### Post by FinalShot on 2010-04-13
Doesn't matter if I don't find what I want since I'm dual booting :)

---

### Post by ju2wheels on 2010-04-13
Might sound like a weird suggestion, but Netbeans is pretty nice and it does have plugins to support C++.

[edit] but of course nothing beats emacs + some color themes...

---

