---
title: "Why is Vim popular in linux world?"
date: 2011-12-28
forum: Programming Talk
---

### Post by hoboy on 2011-12-28
Nmmmmmmmmm I am just curious about why Vim is very popular in linux world as ide.
I have tried to learn it for while now wihtout succes, maybe just because I am lazzy.
I am used to Eclipse, Netbeans, VS2010.
Maybe I am wrong I think it requires lots of works to do simple think with vim compared to the the ide I have mentionned.
As people usually know what they are doing ...why go through such hard work to learn an ide ?

---

### Post by schauerlich on 2011-12-28
For one, vi(m) is near universal. You can be pretty well guaranteed it will be on any unix installation anywhere. It's also very customizable, so that common tasks can be automated in just the way you like. Once you learn the commands (which admittedly have a steep learning curve), it's very quick to get things done as it often only takes a few keystrokes.

And this is coming from an emacs user. I feel a little dirty.

---

### Post by lisati on 2011-12-28
Not everyone here has used Vim. I've only every used it for [cleaning]("http://en.wikipedia.org/wiki/Vim_%28cleaning_product%29"). :)

---

### Post by gateway67 on 2011-12-28
> **hoboy said:**
> Nmmmmmmmmm I am just curious about why Vim is very popular in linux world as ide.
I have tried to learn it for while now wihtout succes, maybe just because I am lazzy.
I am used to Eclipse, Netbeans, VS2010.
Maybe I am wrong I think it requires lots of works to do simple think with vim compared to the the ide I have mentionned.
As people usually know what they are doing ...why go through such hard work to learn an ide ?
vim is not an IDE; it is an editor.  It, and its predecessor vi, have been around for a long time.  Even today, there are situations in which someone may need to edit a file on a system which does not offer "candy-coating" (a window manager), nor should one assume that the file being edited is software.  Such system are typically servers and/or systems that do not require a graphical user interface.

I learned what I needed to know in vim in a few weeks.  Naturally, I do not know every nook/cranny of vim, but I can typically "run circles" around the IDE lover's in my office when it comes to s/w development.

---

### Post by trent.josephsen on 2011-12-28
Open up your favorite IDE and try these exercises:

- Delete a line
- Delete four lines
- Delete up to and including the next semicolon
- Delete up to, but not including, the next semicolon
- Delete the newline at the end of the current line
- Open a new line before the current line
- Open a new line after the current line
- Search for a regular expression
- Go to the top of the file
- Go to the bottom of the file
- Go to line 300
- Transpose two adjacent characters
- Switch the case of a letter
- Increase an integer constant by 100

Now do each of the following in 3 to 5 keystrokes without using the mouse, looking at the keyboard, or stretching for Ctrl, Alt, Home, End, or Delete (which are usually a bit out of the way and often in weird places).

Most IDEs don't even have easy shortcuts for moving back and forth on a line without hitting Ctrl.  And I didn't even get into the mid-level stuff like regex-based substitution, much less macros and custom keybindings, which most IDEs don't have at all.  Furthermore, IDEs are usually designed for one language or another -- show me an IDE that handles SQL, HTML, CSS, Java, Perl, Python, C, C++, Lua, sh, Makefiles, and Git commit messages gracefully, and doesn't degrade to uselessness when used with something it doesn't recognize.

In sum, there are a lot of things Vim can do really well, and it beats the pants off having different IDEs for all the numerous different languages you might want to use.

---

### Post by Stovey on 2011-12-28
Hi.  I decided to use Vi because:

- I had used it a little bit previously (at university CS class)
- It seemed to me two popular text editors are Vi and emacs
- I read [this thread](http://ubuntuforums.org/showthread.php?t=23169) and decided upon Vi.

I spent a few minutes each day for a  couple weeks working through the tutorial in my signature, and now am comfortable moving around in Vi.  This wasn't "hard work", it was fun.

---

### Post by The Cog on 2011-12-28
Vi exists on pretty-much any unix installation, so even poor familiarity like mine gives you a get-out-of-trouble capability on any unix (or that new-fangled linux upstart) that you might be working on. It's well worth learning enough to be able to edit config files.

But its popularity amongst power users is because of its power-editing capabilities. It is astonishingly fast and powerful if you really know it well. Much faster than a GUI for most tasks.

---

### Post by hoboy on 2011-12-28
> **gateway67 said:**
> vim is not an IDE; it is an editor.  It, and its predecessor vi, have been around for a long time.  Even today, there are situations in which someone may need to edit a file on a system which does not offer "candy-coating" (a window manager), nor should one assume that the file being edited is software.  Such system are typically servers and/or systems that do not require a graphical user interface.

I learned what I needed to know in vim in a few weeks.  Naturally, I do not know every nook/cranny of vim, but I can typically "run circles" around the IDE lover's in my office when it comes to s/w development.

As you said "vim is not an IDE; it is an editor." this actually great answer. Because as I said I have asked only because of curiousity.

---

### Post by CptPicard on 2011-12-28
I'm an Emacs guy so I like a customizable text editor as much as the next guy, but I'll have to throw in a few good words for IDEs too, in particular when dealing with languages that have big associated projects that require quite a bit of managing... such as Java. I'd hate to have to work with a big J2EE project without appropriate IDE support; in particular refactoring things is just so much easier with one. And in comparison, I very rarely need to "go down exactly three lines" or somesuch as efficiently as possible. A "select forward/backward to matching parenthesis" feature might be nice.

I guess I'd say I'm not so much editing *text* as the things the text files represent in the programs...

---

### Post by bonevg on 2011-12-28
As every1 previously pointed - there are different reasons for why vi/vim is so widely used.
Once you become a bit more familiar - its power is overwhelming :)
So lazy man can do things fast and keep on being lazy afterwards
Hence, in the name of "lazy and proud to be" you may have the so called vi-vim cheat-sheet:

[http://www.viemu.com/vi-vim-cheat-sheet.gif](http://www.viemu.com/vi-vim-cheat-sheet.gif)

May the power be with you :)

---

### Post by Lars Noodén on 2011-12-28
I use vi for system administration (configuration and shell scripting) because it is present on all system and it is designed to work on low-speed, high-latency connections.

---

### Post by memilanuk on 2011-12-28
mmmm... I've used vim off and on over the years, mainly because it was there.  I'm starting dinking around with slrn again due to some frustration with TB, so along comes vim (not the only option, but it seems like the default one for most people using slrn).

I've been hopping back and forth between different editors and 'lite' IDEs a bit lately... and I think what I'd really like is gvim with code-completion built-in, code-folding, line-numbers, 'show whitespace' and 'show indent guides' (as used in Komodo Edit, Geany, etc.).  And the indenting/commenting blocks of code by simply highlighting, right-clicking and picking an option.  Some of the above is easy enough to turn on or off in (g)vim... others, not so much.

---

### Post by HotCupOfJava on 2011-12-29
I usually use an ide or fancy editor for coding with syntax highlighting, autocomplete, refactoring, etc. But for editing config files, vim is my go-to. I'm usually in the terminal already, and typing "sudo vim <path-to-file>", making my changes, saving and quitting is about as simple and easy as you can get.

---

### Post by aura7 on 2011-12-29
It is quite wrong to compare Vim with advanced IDE's like Eclipse, Visual Studio etc... Vim deserves its own quota of fame specially amongst the ide's that work on shell eg... emacs, nano and even edit in Windows...  

the real fun begins when you don't have a gui and you want the most of a single ide

---

### Post by ofnuts on 2011-12-29
> **aura7 said:**
> It is quite wrong to compare Vim with advanced IDE's like Eclipse, Visual Studio etc... Vim deserves its own quota of fame specially amongst the ide's that work on shell eg... emacs, nano and even edit in Windows...  

the real fun begins when you don't have a gui and you want the most of a single ide
I deal with servers all day long and I always have a GUI... the one on my PC. Instead of using only a shell window logged on the server and doing everything through it, I navigate the server file systems using my file explorer and edit files with my editor. I can even run a graphical compare between two config files on two different servers...

---

### Post by tariquex on 2011-12-29
I used to hate vi when I started using linux and always tried to avoid it as much as I could. Along came amazon cloud and I had to maintain a few servers at work over ssh. So I had no choice but to make my peace with vi. And once you get used to vi, trust me you will try to use h/j/k/l everywhere and wonder why this thing doesn't work!

---

### Post by Stovey on 2011-12-29
I am curious:

- why use "hjkl" instead on the arrows to move around?  The arrows seem more common / intuitive to me, but there must be some advantage to hjkl.

- why is the default tab spacing in Vim 8 spaces?  Shouldn't it be 4?

---

### Post by trent.josephsen on 2011-12-29
1) because hjkl is on the home row, and arrow keys (when they exist) not only require you to move your fingers from the natural typing position, but also generate control characters that can cause issues with weird terminal combinations.

2) Why would the default tab spacing be 4 spaces?  Default tab size has always been 8, ever since... well, since before anybody bothers to remember.  Same with 80 character line lengths; it's the only "standard" you can even begin to assume other people follow.  If you want tabs to appear as 4 spaces wide you can always change them

---

### Post by ofnuts on 2011-12-29
> **trent.josephsen said:**
> 1) because hjkl is on the home row, and arrow keys (when they exist) not only require you to move your fingers from the natural typing position, but also generate control characters that can cause issues with weird terminal combinations.You are using a good ol' teletype and Unix System IV? Data processing hardware and Unix have evolved since the early 80s.

---

### Post by memilanuk on 2011-12-29
> Why would the default tab spacing be 4 spaces?

Seems like its the standard for Python... indentation is spaces (4 of 'em), not tabs.

---

### Post by MG&amp;TL on 2011-12-29
I've never tried Emacs, but i use vi(m) when I have a huge text file that needs a lot of work, typically with another window open running make every so often. Otherwise I use nano. Of course, I could just have one window, and do the 'pause vim' thing, but I can never be bothered.

@OP:

```
vimtutor
```

..it's not that hard. :)

---

### Post by F.G. on 2011-12-29
hey, so regarding the 'HJKL' keys, when my fingers sit at 'home', they're usually on 'JKL;' which actually means i have to move one key to the left when in 'normal' mode in vim.  

do other people have this? am i a defective typist? should my fingers of my right hand be one space to the left? if so, why do the keyboard makers of the world put a dimple on the 'j' key, rather than the 'k'??

---

### Post by trent.josephsen on 2011-12-29
> **F.G. said:**
> hey, so regarding the 'HJKL' keys, when my fingers sit at 'home', they're usually on 'JKL;' which actually means i have to move one key to the left when in 'normal' mode in vim.  

do other people have this? am i a defective typist? should my fingers of my right hand be one space to the left? if so, why do the keyboard makers of the world put a dimple on the 'j' key, rather than the 'k'??
No, the movement keys are operated by the 3 strongest fingers of your right hand.  The up/down movement keys (which I at least use much more often than left/right) are operated by the 2 strongest fingers.  I swear, it makes sense!

Also it's the same scheme used in NetHack and a number of other programs... mutt and slrn come to mind.  Not sure if it was in vi first, but it's a formula that works.

---

### Post by F.G. on 2011-12-29
> **trent.josephsen said:**
> No, the movement keys are operated by the 3 strongest fingers of your right hand.  The up/down movement keys (which I at least use much more often than left/right) are operated by the 2 strongest fingers.  I swear, it makes sense!

Also it's the same scheme used in NetHack and a number of other programs... mutt and slrn come to mind.  Not sure if it was in vi first, but it's a formula that works.

hmm, ok, so you mean that when i use the movement keys i should stick to those three fingers, and use the index one for 'h' and 'j'. such that my little finger remains, useless, hovering over the semi-colon, however my hands do remain in place... right?

---

### Post by trent.josephsen on 2011-12-29
> **F.G. said:**
> hmm, ok, so you mean that when i use the movement keys i should stick to those three fingers, and use the index one for 'h' and 'j'. such that my little finger remains, useless, hovering over the semi-colon, however my hands do remain in place... right?

It's not useless; it's ready at a moment's notice to enter command mode. :)  But yes, you've got the idea.

---

### Post by Bachstelze on 2011-12-29
I must be the only person who uses the arrows in vim instead of hjkl. As you may have guessed, I am a terrible typer. :p

---

### Post by jwbrase on 2011-12-30
> **Bachstelze said:**
> I must be the only person who uses the arrows in vim instead of hjkl.

Nope. You're not.

Vim arrow key users of the world unite!

---

### Post by MG&amp;TL on 2011-12-30
> **jwbrase said:**
> Nope. You're not.

Vim arrow key users of the world unite!

Me too! I never quite got why; if you're a traditionally trained touch typist, you use "jkl;" not "hjkl". I don't usually use the arrow keys much, anyway, otherwise, what's the point of vim?

---

### Post by Bachstelze on 2011-12-30
> **MG&TL said:**
> I don't usually use the arrow keys much, anyway, otherwise, what's the point of vim?

Do you honestly think vim is only about hjkl vs. arrows?

---

### Post by MG&amp;TL on 2011-12-30
> **Bachstelze said:**
> Do you honestly think vim is only about hjkl vs. arrows?


..you miss my point, thankfully. :P


No, I mean that you can navigate much faster around a document with vim, rather than using arrow keys/hjkl. 

Mercifully not. :lol:

---

