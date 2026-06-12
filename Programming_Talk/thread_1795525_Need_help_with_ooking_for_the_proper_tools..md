---
title: "Need help with ooking for the proper tools."
date: 2011-07-02
forum: Programming Talk
---

### Post by Arukas on 2011-07-02
Hello All-

Short Story:
I've used various C/C++ IDE in Linux for doing console programing.  I'm trying to learn to do GUI, and I am missing some tools.  

1)  Some type of GUI editor.  Making simple windows looks easy without an editor but from what I'm reading a more practical window will require a gui editor.  

2)  A good library to use.  I'm more concern with what I'm doing to work in ubuntu than windows.  I'd like crossplatform capability, but it doesn't have to look to pretty in windows.

3)  A good help file.  I've notice that I'm going to have to use a lot of classes to find their parameters. I've been told you don't want to even bother trying to memorizing them.  The tools I've used in windows don't work because I'm using windows 7, and apparently Microsoft frowns on backwards compatibility.  

4) If possible, I'd like an all in one package for convenience.  I've played with more than one Linux IDE to know there's some complexity to them.  

Thanks- Arukas


Long Story:

I've done most my programming in C/C++.  Almost all of my programming I have done is for the console.  (Terminal and DOS Window)  I've never really called it console before but I think that he word for it.  And I have all the tools for that.  And its pretty simple.

I'm wanted to graduate and go into GUI.  Plus I'd like the possibility of cross platform compatibility.  With console programs, its pretty simple just recompiling code.  

I've programmed mostly in Ubuntu, and I think I want to stay in with Ubuntu.  For working in windows the "Microsoft Studio Express" looks like its exactly what I needed via their website and live chat associates, but they don't tell you till after you start installing it (license agreement) its only an evaluation.  I do not enjoy misinformation and will not use their products.  

I should also say, I've never done a GUI in Linux, I've used Visual Basic about 15 years ago.  

I've done a couple of tutorials with trying to program a GUI.  However, I'm not having trouble following the tutorials, but I sure notice I'm missing some useful tools.

---

### Post by cgroza on 2011-07-02
If you want cross platform applications that look and behave native on every platform I suggest you wxWidgets. It is a GUI library but has support for many things such as threads, networking and many others. It offers almost everything you need for cross platform programming.

The toolkit is written C++ but it has bindings for Python, Perl, Ruby and many other languages.

It's documentation is rich and you can find it easily on the net just by googling the class name.

A GUI builder for this toolkit is wxGlade, wxForms and wxSmith for the Code::Blocks IDE.

I have been using Code::Blocks before switching to Emacs.

---

### Post by Arukas on 2011-07-02
I've used Code::Blocks before. Are wxforms wxglades, wxsmith are plugins for code blocks?

---

### Post by cgroza on 2011-07-03
I am not sure about others but wxGlade is a stand-alone program.

---

