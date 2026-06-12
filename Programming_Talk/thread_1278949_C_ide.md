---
title: "C ide?"
date: 2009-09-30
forum: Programming Talk
---

### Post by achelis on 2009-09-30
Hi
I'm just about to start on a project which needs to be written in C - not C++.

There is no GUI programming involved as the hardware the program is for has no screen.

I'm basically looking for something with syntax highlighting, code completion and preferably some way of helping with the overview of files in the project. And if it supports git it'd be a nice bonus not to have to go command line for that.

Any suggestions?

---

### Post by pepperphd on 2009-09-30
Hi. There is a thread for this: [http://ubuntuforums.org/showthread.php?t=752224](http://ubuntuforums.org/showthread.php?t=752224)

But since you want a recommendation, I would say Vim ([http://www.vim.org]("http://www.vim.org/")) provides functionality, ease of use, customization possibilities, and an 'out of your way' style that when combined makes for an excellent environment.  It does however have a learning curve and you'll spend alot of time making it work just the way you want it to, which is worth it. After Vim, I'd say Kdevelop ([http://www.kdevelop.org/](http://www.kdevelop.org/)), and Code::Blocks ([http://www.codeblocks.org/](http://www.codeblocks.org/)) are also excellent choices.

---

### Post by davetv on 2009-09-30
I use code::blocks quite a lot and highly recommend it.


To understand recursion you must first understand recursion ;)

---

### Post by peetbull on 2009-09-30
Hello, everyone!

Although I am fan of Terminal+VI, I personally use  Netbeans with the C/C++ plugin installed. I will post a few information about this IDE, just in case someone want to try it.

It is a heavy environment in terms of memory and CPU but, still, it's friendly; for example you can Ctrl+click on a function's name and it then opens the file from which the function originates. 

And many more stuff like syntax highlighting, code completion, project-based and filesystem-based management and, at least to my knowledge, support for SVN, CVS, Mercurial versioning systems.

If your machine can stand it, then I guess it's worthy.

For more info: [http://www.netbeans.org/features/cpp/index.html](http://www.netbeans.org/features/cpp/index.html)
Download at: [http://www.netbeans.org/downloads/index.html](http://www.netbeans.org/downloads/index.html)
First steps: [http://www.netbeans.org/kb/trails/cnd.html](http://www.netbeans.org/kb/trails/cnd.html)
Configuration for Ubuntu: [http://ubuntuforums.org/showthread.php?t=1029485](http://ubuntuforums.org/showthread.php?t=1029485)

I hope this helps anyone who would try it. I would still vote for VIM or Code::Blocks, though. It takes some experimentation for your best fit, Achelis!

Happy coding!

:-({|=

---

### Post by samjh on 2009-09-30
> **achelis said:**
> I'm basically looking for something with syntax highlighting, code completion and preferably some way of helping with the overview of files in the project. And if it supports git it'd be a nice bonus not to have to go command line for that.

Any suggestions?

For that, you only really need a decent code editor with efficient file access features.  Geany or Gedit with the gedit-plugins package should be adequate.

Personally, I just go for vim when it comes to C programming.

---

### Post by ve4cib on 2009-09-30
Lately I've been a big fan of Geany.  I haven't used it for straight-C, but I've used it with some wonky hybrid C/C++ code and it worked fine.  Syntax highlighting, auto-completion (to some extent), symbol/function/variable list, and a terminal embedded in the application so you don't need to change windows to compile.  Very nice text editor overall.

---

### Post by diesch on 2009-09-30
IMHO Emacs is a good choice, but usually needs some customization.  See [http://www.emacswiki.org/emacs/CategoryProgramming](http://www.emacswiki.org/emacs/CategoryProgramming) for some tips.

---

### Post by napsy on 2009-09-30
use vim:

ctrl+n gives you code completion
install cscope and nerdtree plugins for browsing the source
configure your .vimrc and remap the keys to your liking.
set up your preferred colorscheme.

---

### Post by Can+~ on 2009-09-30
[Eclipse with the C plugin]("http://www.eclipse.org/downloads/").

---

### Post by achelis on 2009-09-30
Thanks a lot guys. Definitely given me some options to consider and play around with :)

So far I've installed emacs, eclipse and code::blocks and they all seem to do nicely for my needs. Code::blocks doesn't seem to have Git support though?

Now I just need to start coding :)

---

