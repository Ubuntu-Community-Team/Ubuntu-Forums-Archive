---
title: "Whats so special about VIM?"
date: 2007-08-27
forum: Recurring Discussions
---

### Post by rharriso on 2007-08-27
I've been hearing a lot about Vim. I've used the editor before, but found it unwieldy and never found any reason to go back to it. Why do so many people seem to be high on this editor? What features does it have that other editors don't?

---

### Post by mostwanted on 2007-08-27
Mainly, the reason why people rave on about vim and emacs is because they provide lots of nifty keyboard shortcuts that can improve coding speed. I personally think the investment in time learning it and the overall lack of streamlined GUI (they are hack-on GUIs) lessens productivity, but many people swear by it.

---

### Post by rharriso on 2007-08-27
I would think you could get those features out of a good IDE with a much smaller learning curve.

---

### Post by Lord Illidan on 2007-08-27
Or perhaps it is macho...hehe

Personally I prefer nano as compared to vi nowadays.

---

### Post by Zootropo on 2007-08-27
I only use vim when I have to use the console. Eclipse for programming, gedit to write some text and tomboy for reminders and such

---

### Post by Steve1961 on 2007-08-27
I'm sure, if you're a programmer, that emacs and vim have some great features.  However, personally I just use nano when I need an editor.

---

### Post by xtacocorex on 2007-08-27
One good reason to learn VI is that it is the default console based editor on all flavors of Unix and Linux.  This point comes up in every Emacs/VI flamewar and should be made here.  

I was required to learn it for my big Numerical Methods class in college and did not find the editor difficult at all.

---

### Post by slavik on 2007-08-28
because you can do things like:
5dd (when typed in command mode) to delete 5 lines in 1 go
or substitution by writing awk/perl regular expressions (same for searching for text).
it also does syntax highlighting.
vim can also run shell commands and report the output.

vim is the IDE which doesn't need X. much like mplayer is the media player that doesn't need X.

---

### Post by aks_! on 2007-08-28
What's so special about Vim? Everything. ;)

---

### Post by sacherjj on 2007-08-28
I prefer Scribes for my editor.  I know enough vi/vim to edit system files when it is more annoying to sudo or gksudo them into another editor.  Someone tried to tell me the different keystrokes to make vi really useful and my eyes started glossing over.

---

### Post by CptPicard on 2007-08-28
> **xtacocorex said:**
> One good reason to learn VI is that it is the default console based editor on all flavors of Unix and Linux.


Sorry but you're wrong, it's [ed that is the standard (default) text editor]("http://www.gnu.org/fun/jokes/ed.msg.html")...

Personally, I used to swear by Emacs' hallowed name, but then I grew up and graduated and started doing real work and moved to Netbeans and Eclipse...

---

### Post by RocketRanger on 2007-08-28
I read a four page tutorial on vi in Linux Format and thought that I would never get it, but it is surprisingly easy and extremely effective to use. I like to keep vi handy in a terminal for quick edits of scripts. Also vi's syntax highligting capabilities are exellent!

The only feature that I really miss is some kind of workspace with a list of open files, so for editing projects I usually go with geany (it's also pretty to look at :)

---

### Post by rharriso on 2007-08-30
I've never heard of scribes, its not in my Package manager. Whats the repository line?

---

### Post by DjBones on 2007-08-30
Like some people have already said, I think the main advantages of vim over fluffy editors is that its basically on every linux distro out there that isn't just a naked kernel haha.. and if you bust your xorg.conf it'll come in handy real fast when you have to use safe-mode ;]

((from what i gather, once you know how to use it people really like it because its no frills and has more keyboard shortcuts than you can shake a stick at. and keyboard shortcuts are like candy to nerds))
I've never used emacs, but after i learned how to use vim i didn't really see what the advantage would be..

---

### Post by AZzKikR on 2007-08-30
If you want to start learning the simple basics of VIM, type:
```
$ vimtutor
```
in your console. This will open up a tutorial type of text file, and if you take like 20 minutes, you're up to speed into working successfully with it.

I like VIM for a few reasons. I find the keyboard shortcuts more intuitive than emacs (and less CTRL+ALT+F+G+A+F1 = delete one line; kind of things ;)). The syntax highlighting is a help for a lot of files, especially when configuring XML files for Apache Tomcat, or Xorg.conf. It was the first console/terminal editor I've ever used and I stuck with it.

For the real-deal, as in, coding and coding and coding: I use Eclipse.

---

### Post by Compyx on 2007-08-30
Vim is an extremely powerful editor once you get used to it. The main reasons I use it are: regular expressions, scripting possibilities, excellent syntax highlighting (and you can create your own), code-folding and the shell/make integration.

It's also highly configurable, you can let it react to different file types and set options accordingly (scripted).

Modelines are another nifty feature I use a lot, these are vim-commands in the first couple of lines of a file, embedded in comments. This will make sure the editor behaves like you intend it to, even when opening the files in Vim on another system (with different settings).

This is what I usually have in my C sources as the first line:
```

/* vim: set et cin ts=4 sw=4 sts=4 fdm=marker: */

```

I could go on, but I think this is enough for now ;)

(Did I mention you never have to use the mouse?)

---

### Post by scooper on 2007-08-30
I almost exclusively use VIM.  I find the (initially unintuitive) modal interface very comfortable, because my hand never leaves the alpha-numeric portion of the keyboard.  Like Firefox, via plugins you can add a million different features and entirely change the way it works.  A plugin like [Cream]("http://cream.sourceforge.net/") makes it less quirky and friendlier to new users.  I wouldn't underestimate the ergonomic value of not having to use funny key combinations to get serious work done.

There are times I curse at it, because something I only do occasionally is hard to find.  But for those rare moments, I either use the help system. the menu, an external  tool, or even another editor.  Since it integrates very well with the shell using an external tool as a filter is pretty easy.

I'm a Python programmer.  Python, as a dynamic language, is incredibly hard to support well in an IDE, at least for refactoring and browsing features.  So I don't lose much sticking with VIM.  On the other hand, if you're a Java programmer (or C++), I think you might find Eclipse a much more productive environment.

It still pays to know vim/vi, due to all the reasons mentioned by other posters, e.g. it's always available and provides a lot of functionality and demands little of the system.

---

### Post by AlexThomson_NZ on 2007-08-30
Although I use eclipse/netbeans/geany for my day-to-day coding, for things like editing config files, etc I like to use VI, and I have a little one-page cheat-sheet of handy to refer to occasionaly when my memory fails me.

Where I work, I often find myself having to support older or non-gui servers, so knowing VI on at least a basic level is a must for me in my job.  I did hate it initially though!

---

### Post by slavik on 2007-08-31
and oldie but goody :)

[http://unix.rulez.org/~calver/pictures/curves.jpg](http://unix.rulez.org/~calver/pictures/curves.jpg)

---

### Post by Compyx on 2007-08-31
> **slavik said:**
> and oldie but goody :)

[http://unix.rulez.org/~calver/pictures/curves.jpg](http://unix.rulez.org/~calver/pictures/curves.jpg)

Hehe, nice one. I remember starting out with Vim and thinking 'OK, just how the hell do I actually enter text?'.
It does take a while to get used to, but once you get to know Vim, it's hard to use anything else.

These days, at my job I have to use some crappy MS software for coding and usually end up having a lot of 'dd' and ':wq' in my sources :D

---

### Post by sacherjj on 2007-10-03
> **rharriso said:**
> I've never heard of scribes, its not in my Package manager. Whats the repository line?

I don't know if it is in the repositories yet.  I go to getdeb to install it.

---

### Post by dwhitney67 on 2007-10-03
> **rharriso said:**
> I've been hearing a lot about Vim. I've used the editor before, but found it unwieldy and never found any reason to go back to it. Why do so many people seem to be high on this editor? What features does it have that other editors don't?

Another troll is born.

---

### Post by alencool on 2007-10-05
Visit the following page, for a well written response to why people use vim.

Why, oh WHY, do those #?@! nutheads use vi?
[http://www.viemu.com/a-why-vi-vim.html](http://www.viemu.com/a-why-vi-vim.html)

---

### Post by tjajab on 2008-07-25
The reason for me to use vim is simply because I find it limitless. I use Eclipse for coding projects, but for a lot of other raw text editing I find it hard to beat. I have never really tried emacs, but the few times I am forced to use it, I always end up with a lot of uncomfortable Ctrl+Letter Letter commands.

Though vim has a steep learning curve, it is very logical once you get used to it. The fundamental thing with vim is that the programmers realized that text editing is only to a limited extent writing new text, and more about, errm, text editing. Vim makes it extremely simple to edit files systematically.

I just have to mention my favourite: macros. By typing q and then a letter of choice, everything you do is put in a register. After pressing q again the macro is saved in the register. Afterwards you can simply do @ letter and the thing you just did gets done again. Or 1000@letter and it gets done a thousand times.

For example, to write "this is another line" on thousand line you do
qaithis is another line<Enter><Esc>q1000@a

You could actually paste commands to, for example you could copy
qaithis is another line
and paste this in your vim editor (being in normal mode from the beginning). Then you type <Enter> and then <Esc> and then you paste
q1000@a

Try the vimtutor, and you'll be as stuck as I am to vim.

---

### Post by mrgnash on 2008-07-25
> **slavik said:**
> and oldie but goody :)

[http://unix.rulez.org/~calver/pictures/curves.jpg](http://unix.rulez.org/~calver/pictures/curves.jpg)

:lolflag: @ the Emacs spiral.

I'm a relative newcomer to Vim, and I didn't find it that hard to pick up (using similar shortcuts in Vimperator helped a lot). I find it brilliant for what I need an editor for: composing documents in LaTeX. Being able to run all the necessary commands to compile the documents right from within the editor, without having to tab out or some such is a really nice feature :)

---

### Post by eentonig on 2008-09-06
basic editing is hard when you begin with it. But once you're passed that, you can only see the beauty of it.

Try to find a good tutorial, one day you're X will be broken and you'll be happy you know how to edit configs from CLI.

I do almost all my scripting and config-tweaking in vim.

---

### Post by doorknob60 on 2008-09-06
I guess vim and emacs are good for coders, but that's not me so nano and kate and gedit and leafpad are all good for me and most "average" users :) Vim is confusing TBH I tried to use it once (I was stuck in CLI and didn't know nano existed :P) and I ended up killing my xorg.conf a few times before I got it right :lolflag:

---

### Post by LaRoza on 2008-09-06
> **doorknob60 said:**
> Vim is confusing TBH I tried to use it once (I was stuck in CLI and didn't know nano existed :P) and I ended up killing my xorg.conf a few times before I got it right

No, Vim is not confusing. You were confused by Vim. All the problems were caused by the user, not the tool.

---

### Post by doorknob60 on 2008-09-07
> **LaRoza said:**
> No, Vim is not confusing. You were confused by Vim. All the problems were caused by the user, not the tool.

Yeah, but why spend hours of my time learning vim when I could just use something I'm already comfortable with. And ask anyone, vim is confusing the first time you use it, always. Unless you're god or something :-P

---

### Post by jimi_hendrix on 2008-09-07
> **slavik said:**
> it also does syntax highlighting.

how do you get syntax highlighting in console?

---

### Post by jimi_hendrix on 2008-09-07
> **CptPicard said:**
> Sorry but you're wrong, it's [ed that is the standard (default) text editor]("http://www.gnu.org/fun/jokes/ed.msg.html")...

why was it that i typed ed in terminal to take a look at it and the username@computer:~$ prompt went away and when i hit ctrl + c to exit what ever i started it printend a question mark with a line of whitespace on the top and bottom?

---

### Post by LaRoza on 2008-09-07
> **doorknob60 said:**
> Yeah, but why spend hours of my time learning vim when I could just use something I'm already comfortable with. And ask anyone, vim is confusing the first time you use it, always. Unless you're god or something :-P
I guess you have no idea how confusing it is for Vim users to use big GUI IDE's. Nothing makes sense.

Just because *you* didn't get it, doesn't mean anything. I once tried Visual Studio to see what the big deal was. I couldn't figure out how to use it. Is that my fault or VS's fault?


> **jimi_hendrix said:**
> how do you get syntax highlighting in console?

In Vim? The console doesn't have syntax highlighting.

In Vim, run:

```

sudo aptitude install vim

```

Then open a file with it. It should highlight by default by if it doesn't, type:

```

:syntax on

```

> **jimi_hendrix said:**
> why was it that i typed ed in terminal to take a look at it and the username@computer:~$ prompt went away and when i hit ctrl + c to exit what ever i started it printend a question mark with a line of whitespace on the top and bottom?
man ed

Such an elementary question ;)

---

### Post by CodeAlias on 2009-01-06
> **rharriso said:**
> I've been hearing a lot about Vim. I've used the editor before, but found it unwieldy and never found any reason to go back to it. Why do so many people seem to be high on this editor? What features does it have that other editors don't?

What I like about vim is how easy it makes adding macros and mappings.
See this example here "[Write and map vim macros/functions (howto and example)]("http://www.codealias.info/technotes/example_of_howto_write_vim_macros_and_map_them_to_key_sequence")"


---
[Networking and Coding Articles]("http://www.codealias.info/")
[Subscribe]("http://feedproxy.google.com/codealias")

---

