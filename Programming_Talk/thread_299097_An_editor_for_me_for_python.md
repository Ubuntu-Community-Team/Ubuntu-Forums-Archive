---
title: "An editor for me for python?"
date: 2006-11-13
forum: Programming Talk
---

### Post by Steveire on 2006-11-13
Hi, I want an editor for python. Kile does these things for me for latex(except abbreviation/svn sync), but I'd like a python equivalent. Here's my desired feature list:
[list]
[*] Highlighting (all do this)
[*] Smart indentation (Kate does this well)
[*] Complete '{', '[' '(' '"' with closing equivalents automatically (like Kate)
[*] Complete code based on the modules I've loaded and classes I've loaded (ipython the interactive shell does this, and vim does it too)
[*] Word completion (Kate does this, and I think I can make vim do it too)
[*] Abbreviations. These are available in KDevelop, but only for c/c++/html files. You can type tab<enter> and <table><tr><td>|</td></tr></table> is inserted where | is the cursor. If it allowed python files it would be fine. You could define 'classd' as ```

class |:
    def __init__(self, ):

``` and/or more complicated abbreviations. If you've seen the TurboGears 20 minute wiki video, I'm pretty sure the guy uses that feature of Textmate on the mac.
[*] (Auto)synchronisation with svn. I have svn running on my laptop for version control. It would be nice if everytime I saved a file it was committed with a prompt for a message.
[/list]
I think KDevelop would be perfect if it did code completion and allowed python abbreviations. The python support for it is just not very good. I hear it's plugin based though, so if you know how I can add these missing features go ahead and speak up.

I'm also starting to like vim. It does everything above except autocompleting '(' etc. It has abbreviations, but only one-sided. It can't put anything after the cursor AFAIK. If you can help me improve vim for python coding please put that up too. My current vimrc is this:
```

syntax on

if has("autocmd")
          filetype indent on
endif

if has("autocmd")
        augroup content
                autocmd BufNewFile *.py
                   \ 0put = '#!/usr/bin/env python'  |
                   \ 1put = '#-*- coding: utf-8 -*-' |
                   \ $put = '' |
                   \ $put = '' |
                   \ norm gg19jf]
        augroup END
endif

```
I'd prefer syntax highlighting only for *.py/c/cpp/h. I know that's possible, but I can't figure it out. The highlighting in vim for python is not very good anyway. Kate is much better for that highlighting 'self'(I know it's only a convention, not a keyword), True and False where vim doesn't and '=' signs etc.

So, preferably I'd like to get Kate/Kdevelop with these features. I'd also consider another editor altogether, but I'm sure at least vim should be modifiable to work with python. SPE is pretty good, but it doesn't complete '(' etc, which really annoys me.

Thanks for any help.

---

### Post by gerowen on 2006-11-13
The editor that comes with python in the Windows version can be installed in Linux and is called IDLE.  In ubuntu the package name is idle so apt-get install idle will get it for you.  It has "most" of the features you listed.  It has syntax highlighting, indentation helping (if you start an if statement and end it correctly with a : it will automatically indent the next line properly for you and tabs/backspaces keep your indentation right), and it highlights when you start closing ( ) so you can see how much of the brackets you have closed.  I've also seen it show tooltips for available commands when I start calling a function from an imported library.  For example if I imported string, and then started to type string. and stopped for a second, it would show a little window with valid commands for the string library.  Not sure if you've used it, but you didn't mention it so I thought I would.

---

### Post by DirtDawg on 2006-11-14
Nevermind :)

---

### Post by yabbadabbadont on 2006-11-14
I liked SPE when I tried it out.

---

### Post by zachtib on 2006-11-14
Give scribes a shot, I've been using it for all my python development. It is a GNOME/GTK application, however, I'm not sure what you're using.

[http://scribes.sf.net](http://scribes.sf.net)

---

### Post by ohgod on 2006-11-14
I like python-mode for emacs, though I'm not sure it does the auto-completion stuff (I does about everything else you mentioned I believe).

> *  (Auto)synchronisation with svn. I have svn running on my laptop for version control. It would be nice if everytime I saved a file it was committed with a prompt for a message.

Are you sure you want to commit on every save?   Emacs integrates with version control nicely, but I'm not sure there's a feature to do this exactly .

---

