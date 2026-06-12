---
title: "TAPE's A Pixel Editor (an exploration of Ruby/TK)"
date: 2007-07-04
forum: Programming Talk
---

### Post by avik on 2007-07-04
Some time ago, I needed a simple pixel by pixel graphics editor.  It needed to be somewhat like MS Paint (what? I like Paint's simplicity!).  Unfortunately, I couldn't find anything that would allow me to push pixels so quickly and so efficiently.  What else could I do but make my own!

I got to work on that, and actually progressed quite far.  It was then that I discovered [KolourPaint]("http://kolourpaint.sourceforge.net/"), the MS Paint clone with a couple more features.  My program, dubbed TAPE for TAPE's A Pixel Editor, was slow and lacking in features, and so I discontinued it.

Making such an application using Ruby and the excellent Tk graphics toolkit was an interesting experience, and while my program is nowhere near the quality of other released products, I thought I would liberate it from the confines of my computer for two reasons:

[LIST]
[*]Ruby/Tk has notoriously little documentation.  Hopefully by looking at my code, other people can get an idea of the structure and practices Ruby/Tk entails.
[*]People can suggest improvements and we can learn something from each other.
[/LIST]

So without any further ado, here's TAPE and a screenshot of it running.

You'll need the following packages from the repos:

```
ruby libtk-ruby libimlib2-ruby
```

You'll want to compile and install [Tile]("http://tktable.sourceforge.net/tile/") to make some of the dialogs look good, but if you decide to not do so, just run TAPE using:

```
TAPE_USE_TILE=0 ruby tape.rb *[filename]*
```

Be sure to read the README for usage instructions and I hope you like it!

---

### Post by slavik on 2007-07-05
may I suggest using OpenGL? I don't think that you should drop this project ...

---

### Post by avik on 2007-07-05
> **slavik said:**
> may I suggest using OpenGL? I don't think that you should drop this project ...

Thanks.  I might do just that, but I'll keep this version around as an example of how to use Ruby/Tk, which under the right circumstances is very powerful.

So did you look at the application?  How was it?

---

