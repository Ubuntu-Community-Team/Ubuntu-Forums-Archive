---
title: "Bash aliases/C++ FLTK help."
date: 2011-07-13
forum: Programming Talk
---

### Post by MG&amp;TL on 2011-07-13
As a beginner C++ programmer compiling from command-line (I found the various IDEs too hard, too pointless, too incompatible, too difficult to add libraries, too annoying...the list goes on. Command-line is simple and effective.) I am starting to use extension libraries such as SDL and FLTK. However, to compile FLTK requires me to type:

```
g++ -I/usr/local/include/FL mysourcecode.cxx -lfltk -lXext -lX11 -lm
```

every single time I want to compile a short tutorial program. And there's two issues with this. Normally, if I put a name for the program executable in front of the source, like this:

```
g++ -o myprogram mysource.cxx
```

it works and I get a project named. However, it throws errors with the FLTK libraries, and I have to stick with 'a.out'

The main problem I have is the effort of typing this out. Is there a way of writing a shortcut (possibly a bash alias?) so I don't have to type all or part of that code?

oh, and what does '-o' do, and why don't I use it when I link with FLTK libraries? And I realise this stems from ignorance :D , but ?its better than total ignorance of the processes behind a point-and-click IDE, isn't it?

---

