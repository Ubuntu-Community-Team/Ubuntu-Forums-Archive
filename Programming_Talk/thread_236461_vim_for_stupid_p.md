---
title: "vim for stupid :p"
date: 2006-08-14
forum: Programming Talk
---

### Post by string on 2006-08-14
Hey !

I am a hardcore emacs user (== I'm pretty much experienced with it and quite efficient), but I see that vi has many adorators in the war against emacs. I have tried vi but I've always been scared by the whole thing : vi is obviously not newbie-friendly (whereas emacs works as the most usual Notepad, which is very easy for beginners). Still, as I know that so many people cannot be wrong, I thought I'd give it a shot and spend some time on learning vim.

So does any of you guys have any good link `bout "vim for stupid" or "vi for the emacs user" or good tips or sumethin' like that ?

Thanks ^^

PS: For those that think vi is crap, or that I am crap for using emacs, please remain silent and let the good guys here.

---

### Post by Blazeix on 2006-08-14
Take a look [here](http://www.apmaths.uwo.ca/~xli/vim/vim_tutorial.html). I've found that this tutorial is really clear, and starts with the basics.

---

### Post by 23meg on 2006-08-14
[http://www.apmaths.uwo.ca/~xli/vim/vim_tutorial.html](http://www.apmaths.uwo.ca/~xli/vim/vim_tutorial.html)
[http://www.jmglov.net/unix/vi-for-emacs-users.html](http://www.jmglov.net/unix/vi-for-emacs-users.html)

---

### Post by skymt on 2006-08-14
Vim has a very nice tutorial built in. Just type "vimtutor" at a command line.

---

### Post by telengard on 2006-08-14
> **string said:**
> Hey !

I am a hardcore emacs user (== I'm pretty much experienced with it and quite efficient), but I see that vi has many adorators in the war against emacs. I have tried vi but I've always been scared by the whole thing : vi is obviously not newbie-friendly (whereas emacs works as the most usual Notepad, which is very easy for beginners). Still, as I know that so many people cannot be wrong, I thought I'd give it a shot and spend some time on learning vim.

So does any of you guys have any good link `bout "vim for stupid" or "vi for the emacs user" or good tips or sumethin' like that ?

Thanks ^^

PS: For those that think vi is crap, or that I am crap for using emacs, please remain silent and let the good guys here.

I have a few suggestions, the easiest one being viper on emacs, but if you are looking to learn vim there are some nice tutorials online and there is also a vim-easy script which I forget the name of.  If you are looking to learn the vi commands/keystrokes this probably isn't the best idea since I believe it tries to *not* be a modal editor which is what makes vi vi.

I'll see what I can dig up.  And you aren't "stupid" vi is quite hard to learn.  It took me a week of dedicated use to get really comfortable with it but I decided up front I was going to learn hjkl to move around.   :)

~telengard (posting via live cd blowing away gentoo and moving to ubuntu on his laptop)

---

### Post by Bushwack on 2006-08-14
$ vimtutor

Work your way through using the commands as you learn them and if your not hooked by the end stick with emacs.

---

### Post by Revert on 2006-08-14
vimtutor was how I got started.  Also, I kept a quick reference card nearby for when I was using it (there're a few different ones, but [this]("http://www.digilife.be/quickreferences/QRC/vi%20Reference%20Card%20(HP).pdf") seems to be one of the better ones).

Good luck; I still haven't gotten around to trying emacs. ;)

---

### Post by krypto_wizard on 2006-08-15
I read somewhere that VI/VIM might feel cryptic initially to use but it is more ergonomic friendly compared to other editors.

I am myself a new user of VI and trying to learn new tricks everyday. But vimtutor is something that helps. But more than that using it as the only editor might help...dont try or go back to emacs just because you cannot do something in VI quickyl and efficiently. Land into problem and then solve them. Thats my 2 cents.

---

### Post by Eric_T on 2006-08-15
My background is similar to yours. I've been an emacs user for the last year or so, and have taught myself most of the advanced features and they've definitely helped me become a better programmer.

But recently, I too have been learning vim, and right now, I actually like it quite a bit better. It just seems a bit "cleaner", for the lack of a better word... 

I started with "vimtutor", and from there just searched for "vim tutorial" on google. What I recommend is to make your own "cheat sheet" as you go along and learn new commands. This helps you remember them better, since you wrote it yourself with your own logic, syntax and layout. You also have a reference chart for later that is easier to use than what someone else has written. Check out this site for a good start:
[http://www.gentoo.org/doc/en/vi-guide.xml](http://www.gentoo.org/doc/en/vi-guide.xml)

Also, check out vim developer Bram Moolenaar's "7 habits of effective text editing", very useful not only for vim users but programmers in general!
[http://www.moolenaar.net/habits.html](http://www.moolenaar.net/habits.html)

Good luck, and stick to it! I've used vim for about two weeks now, and already feel as proficient as I am in emacs. I actually use advanced features like macros and text registers more in vim, because I feel they are more intuitive and easier to remember.

Also, be sure to download vim 7.0, it contains lots of nice features not present in earlier versions.

Ok, I'll stop ranting now:)

---

### Post by string on 2006-08-15
Thank you guys ! all of you !
I'll start right away.

btw, I see Dapper has 6.4 version and the latest is 7. I saw a thread about it, but to sum up : what to do ? stick to 6.4 ? download and compile myself v7 ? find some way to `apt-get install` the v7 ?

Thanks ^^

---

### Post by kaamos on 2006-08-15
> **string said:**
> (whereas emacs works as the most usual Notepad, which is very easy for beginners)

:shock:  :rolleyes:  :lol: 

I love emacs and I've done most of my programming with it at home for quite a while (eclipse at work), but this is just hilarious. I wouldn't call either vi or emacs one bit beginner friendly. ;)

---

### Post by string on 2006-08-15
What I meant :
When you start emacs : you type around just kile in notepad, and qui clicking the little cross the the right top.

When you start vi : whater you do, you hear weird beeps, meaningless error messages, and you quit it qith a weird combination :q, which never works because you actually managed to find 'i' to start typing so vi doesn't let you leave so you must override with ! ...

But I agree that the true power of both is not beginner friendly.

---

### Post by string on 2006-08-15
`bout my version question : anyone has an opinion ?

---

### Post by Christmas on 2006-08-15
emacs? vim? Neah, Kate rulz! :)

---

### Post by kernelpanicked on 2006-08-15
> **string said:**
> `bout my version question : anyone has an opinion ?


Just my opinion but you should probably stick with the stock 6.4 while you're just beginning. v7 (as far as useful features go) only added tabs, which makes it even more complex if you're not already comfortable with it.

---

### Post by Eric_T on 2006-08-16
> **string said:**
> `bout my version question : anyone has an opinion ?

Well, I think upgrading to version 7 is worth it. You have to compile the source yourself, search on the forum for "vim 7.0" and you'll find instructions. I think somebody made a .deb for it as well.

I don't agree that tabs are the only new feature that's any good. New features that I find useful are:
[LIST]
[*]Spell checking support for about 50 languages
[*]Intelligent completion for C, HTML, Ruby, Python, PHP, etc.
[*]Tab pages, each containing multiple windows
[*]Undo branches: never accidentally lose text again
[*]Highlighting of cursor line, cursor column and matching braces
[*]Internal grep; works on all platforms, searches compressed files
[*]Browsing remote directories, zip and tar archives
[/LIST]

In addition, the scripting support is a lot better, so we'll see more useful scripts being made that can also make your life easier.

---

### Post by string on 2006-08-16
> **Eric_T said:**
> Well, I think upgrading to version 7 is worth it. You have to compile the source yourself, search on the forum for "vim 7.0" and you'll find instructions. I think somebody made a .deb for it as well.

I don't agree that tabs are the only new feature that's any good. New features that I find useful are:
[LIST]
[*]Spell checking support for about 50 languages
[*]Intelligent completion for C, HTML, Ruby, Python, PHP, etc.
[*]Tab pages, each containing multiple windows
[*]Undo branches: never accidentally lose text again
[*]Highlighting of cursor line, cursor column and matching braces
[*]Internal grep; works on all platforms, searches compressed files
[*]Browsing remote directories, zip and tar archives
[/LIST]

In addition, the scripting support is a lot better, so we'll see more useful scripts being made that can also make your life easier.


k I'll see... though it'll be tough already to learn vim on 6.4 ...

Also, what about vim vs. gvim ? what's the point of gvim and should I use  iut ?

---

### Post by etank on 2006-08-16
gvim just adds a gui wrapper around vim. It is kind of nice ( that is what I run ) but if you want to learn the commands run it from terminal. You can always go to the gui later but it is harder to go from gui to cli.

---

### Post by deepspring on 2006-08-19
Give "Cream" a shot, it's basicly an addon for GVim that dumbs down the interface a tad (removes the need to use the vim command line).
```
sudo apt-get install cream
```

---

### Post by yigal.weinstein on 2006-08-27
I think most people have pointed out the necessary resources but to recapitulate for all of you interested in using (g)vim on Dapper:

1. vimtutor is installed I believe by defaults with vim and is useful for learnig the basic about the funcionality of vim basics.
so type
```
$vimtutor
```
into your terminal and spend the 1/2 hour necessary for learning the basic.

2. Do not compile vim 7 by yourself it has already been done:
[http://blog.publicidadpixelada.com/2006/07/31/small-how-to-vim-70-running-on-ubuntu-dapper/](http://blog.publicidadpixelada.com/2006/07/31/small-how-to-vim-70-running-on-ubuntu-dapper/)

3. Use vim 7 it has tabs which are great - like firefox vs. explorer.  Other than that vim 6.4 is no easier than vim 7.0x.

4. I find vim is great for latex, fortran and in general all coding as well as notes. It even has an easy to use outliner and it is fundamentally a very very simple program - and I am into what is simple.

---

