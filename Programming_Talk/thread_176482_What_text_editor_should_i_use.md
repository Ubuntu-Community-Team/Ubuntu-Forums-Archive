---
title: "What text editor should i use?"
date: 2006-05-14
forum: Programming Talk
---

### Post by Somenoob on 2006-05-14
been using gedit for a while now, it's fine but i was wondering what text editors you used.

---

### Post by cgjones on 2006-05-14
Vim. It's the only way to go.

---

### Post by Wallakoala on 2006-05-14
[QUOTE=cgjones]Vim. It's the only way to go.[/QUOTE]
vim is very nice, but it requires a little bit of learning in order to use effectivly. Personally, I think gedit is a very nice text editor, so stick with it.

---

### Post by cgjones on 2006-05-14
Yeah, I was kind of joking, although once you get good with it, it's faster then any graphical editor I've used. Plus, almost any *nix you use will have something vi-like.

---

### Post by wmcbrine on 2006-05-14
Will I have my geek license revoked if I say pico/nano?
;)

---

### Post by unbuntu on 2006-05-15
[QUOTE=wmcbrine]Will I have my geek license revoked if I say pico/nano?
;)[/QUOTE]

Yes you will.:p 

Just kidding, but I don't think pico is efficient, or maybe it's just my snap judgment.  I'd say vim, or if you want a smooth introduction to vi, gvim seems to be a good choice.

---

### Post by kaamos on 2006-05-15
Half of the forums will say vim and the other one (including me) will flag for emacs. ;)

Try different ones and see which one suits you. Try scribes, the learning curve is not that steep as with the two first mentioned, and it's pretty similiar to gedit but with cool extra features. [http://scribes.sourceforge.net/](http://scribes.sourceforge.net/)

---

### Post by pharcyde on 2006-05-15
My vote is for vi.  Though, like most people said there is a learning curve associated with it.  Its fairly efficient once you get used to it.

I've never really tried emacs, but there are a lot of people that like that too.  Since you are just starting out give either a try and see how you like it.

---

### Post by Kethinov on 2006-05-15
I prefer Kate for my PHP work and general web development. I use it even though I prefer GNOME as my desktop.

---

### Post by Gustav on 2006-05-15
I prefer emacs.

It seems to me that there are a majority for vi. I find the concept of modes in vi confusing (I even read a usability book where they took vi as a bad example (someone writes a lot of text, goes away while in the non-input (I don't remember what it's called) mode, comes back, thinks he is in input mode, writes edit, all the text is gone) then they say that emacs is much better :)) (wow, three levels of paranthesis :))

Emacs is quite simple to use even as a beginner, you can't say that about vi. (it's at least simpler)

(OK, I've been using emacs a lot more than vi so I am quite biased :))

---

### Post by thumper on 2006-05-15
[QUOTE=Gustav]Emacs is quite simple to use even as a beginner, you can't say that about vi. (it's at least simpler)[/QUOTE]

My biggest problem with emacs when I first started using it was getting out of the bloody thing.  Not such a problem now with the menus and such, but when I first started using it, I don't remember menus (it was some time ago now).

Personally I use emacs.  I finally have a configuration file that makes it look how I like (colours and such for different modes, and keybindings I am used to).

I am yet to find an editor that handles the equivalent of emacs keyboard macros - I am prepared to be enlightened if others know of any.

---

### Post by Gustav on 2006-05-15
[QUOTE=thumper]My biggest problem with emacs when I first started using it was getting out of the bloody thing.  Not such a problem now with the menus and such, but when I first started using it, I don't remember menus (it was some time ago now).

Personally I use emacs.  I finally have a configuration file that makes it look how I like (colours and such for different modes, and keybindings I am used to).

I am yet to find an editor that handles the equivalent of emacs keyboard macros - I am prepared to be enlightened if others know of any.[/QUOTE]
Yes, you're right. The command line version is not easy to use at all as a beginner. (I always recommend nano when someone (that is not an experienced user) should edit files without X)

---

### Post by Kethinov on 2006-05-15
[QUOTE=Gustav](wow, three levels of paranthesis :))[/QUOTE]

You must be a Lisp programmer. ;)

---

### Post by rydow on 2006-05-15
Personally I really like emacs for a number of reasons:
- Good and simple incremental search.
- Efficient with build / compile and jump to error.
- Good program for diffing (ediff).
- cvs aware.
- I may debug under emacs (gud)
- Requires no mouse and runs on many platforms.

The above is just mention a few of its capabilities. As already said it takes some time  to get used to but I think it is worth the effort to have an editor that works almost everywhere. To get stared run the built in tutorial and have a look at someones cheat sheet (e.g. mine at [http://members.chello.se/rydow/emacs_tips.html](http://members.chello.se/rydow/emacs_tips.html))

I have used emacs now for some years and I find myself comming back since I allways miss (or can't find) features of other editors.

Try it you might end up liking it!

Cheers
Jonas

---

### Post by Gustav on 2006-05-16
[QUOTE=Kethinov]You must be a Lisp programmer. ;)[/QUOTE]
I've programmed my share of Lisp. :)

---

### Post by i_m_meen on 2006-05-16
> 
I am yet to find an editor that handles the equivalent of emacs keyboard macros - I am prepared to be enlightened if others know of any.


:map X do_that_and_another_gazillion_things
:abbr foo foobar

And that's just the beginning. You might guess where it's from :D 

:wq

---

### Post by thirdmusketeer on 2006-05-16
I just installed Ubuntu, and it seems that vi is not giving me colors, is there an easy way to get colors on it or should I follow the lenghty VI tutorial available on the web.

---

### Post by Grey on 2006-05-16
I used emacs back in my first year of computer science.  Now I just use gedit, as I'm a lazy bugger.  When I am working on something large, I'll generally use either Anjuta or Eclipse.

---

### Post by xenmax on 2006-05-16
[quote=thirdmusketeer]I just installed Ubuntu, and it seems that vi is not giving me colors, is there an easy way to get colors on it or should I follow the lenghty VI tutorial available on the web.[/quote]
Either in /etc/vim/vimrc (this i guess affects all users) or your ~/.vimrc (create one if it does not exist and it obviously affects only you) have this line:
```
 syntax on
```
I think this line is commented out in /etc/vim/vimrc by default.

---

### Post by thirdmusketeer on 2006-05-16
[QUOTE=xenmax]Either in /etc/vim/vimrc (this i guess affects all users) or your ~/.vimrc (create one if it does not exist and it obviously affects only you) have this line:
```
 syntax on
```
I think this line is commented out in /etc/vim/vimrc by default.[/QUOTE]

Thanks, it worked.

---

### Post by jaypeasy on 2006-05-17
Use whichever editor you feel comfortable with. Personally I prefer emacs. There's very little you can't do with it.

---

### Post by Ptero-4 on 2006-05-17
use aee, or nano. Vim and emacs are quite unfriendly, and emacs is well "an OS inside a text editor".

---

### Post by Revert on 2006-05-17
While both Vi and Emacs have relatively steep learning curves and aren't really new user friendly, they are also extremely powerful tools once you get them down.  It's a tradeoff that should be taken into consideration when compared to text editors like nano and pico.  Also, even if you don't use them often, it's probably to your advantage to know the basics (editing, save, exit, etc.) of both of them, most especially Vi.  Pretty much any *nix box you go to is going to have some version of Vi installed, and knowing just the bare minimum of editing text files in it can be a life saver.

---

### Post by DirtDawg on 2006-05-17
I love [Cream]("http://cream.sourceforge.net/"). It's Vim, but with a delicious GUI wrapper. Plus, plenty of [beautiful color schemes]("http://cream.sourceforge.net/screenshots2-closeup.html") built right in and highlighting support for something like 300 languages.

In short, you get all the benifits of the Vim everyone loves without the complexities. I love it love it love it.

---

### Post by Jessehk on 2006-05-17
[QUOTE=DirtDawg]I love [Cream]("http://cream.sourceforge.net/"). It's Vim, but with a delicious GUI wrapper. Plus, plenty of [beautiful color schemes]("http://cream.sourceforge.net/screenshots2-closeup.html") built right in and highlighting support for something like 300 languages.

In short, you get all the benifits of the Vim everyone loves without the complexities. I love it love it love it.[/QUOTE]


Bah, you stole my reply. ;)

---

### Post by tehDeuce on 2006-05-17
Personally, I like emacs best.  It can do everything I've ever wanted a text editor to do.  I've never used it for a large project though, so I have no idea how it handles them.

---

### Post by tallganglyguy on 2006-05-18
I personally use emacs for just about everything from coding, to word processing to email checking. I've scaled it from simple projects (~3000 sloc) to large projects (>150k sloc). Tools exist to do just about anything one would desire in it. It's got a learning curve, but nothing steep in my opinion. I always found myself going: "It'd be nice if emacs did {insert desire here}." About 10 minutes of googling and configuration file editing later and I had what I wanted. 
I've also used vi, and use it regularly on platforms that don't have emacs on them. I personally like the power of emacs, but I'm not a zealot that thinks vi should burn in the inner bowels of hell. Play around with a number of options, and find one you like. Then stick with it. It's a personal choice. You'll be far more efficient with {your choice of editor} if you use it all the time than if you are capable of operating a handful of editors.

---

### Post by rplantz on 2006-05-18
You might wish to read [http://en.wikipedia.org/wiki/Editor_war](http://en.wikipedia.org/wiki/Editor_war).

In general, vi is modal. The keys have different meanings depending on which mode you're in. Emacs uses modifier keys (e.g., ctrl, alt) to give the keys different meanings. I'm a good typist and find it easy to hold the ctrl or alt keys down while pressing another key. I find moving back and forth between modes more cumbersome.

It's a good idea to know enough about both emacs and vi to be able to use them at least for simple things.

---

### Post by Basu on 2006-05-19
It depends on what you do really. Unless you program or edit configs for a few hours each day, you might want to just stick to good old Gedit. But if you really do want to use a power text editor, it would be best to play around with some of them until you like one. And if you happen not to like any of them and if you know enough code, you might want to try and roll your own. I know that many programmers decide to right their own text editors/IDEs coz they aren't happy with what's out there.
But I would recommend that you get a basic working knowledge of vi and emacs. Never know when you might be stuck on a box with only one of them to edit files with. Anyway keep posted with what you decide.

---

### Post by Van_Gogh on 2006-05-19
[QUOTE=DirtDawg]I love [Cream]("http://cream.sourceforge.net/"). It's Vim, but with a delicious GUI wrapper. Plus, plenty of [beautiful color schemes]("http://cream.sourceforge.net/screenshots2-closeup.html") built right in and highlighting support for something like 300 languages.

In short, you get all the benifits of the Vim everyone loves without the complexities. I love it love it love it.[/QUOTE]
I've been a bit stuck on Windows because I haven't yet been able to find an editor on GNOME that could surpass the fantastic Windows-only [Notepad++]("http://notepad-plus.sourceforge.net/uk/site.htm"). However, judging from the Flash-animation, Cream could be the program to finally overtake Notepad++. I'll definately try it out.

---

### Post by Van_Gogh on 2006-05-19
Ok, I've just meddled with Scribes for an hour and...I'm loving it! It's got all the features Gedit lacks, without being complex. It's Nice Stuff(t). Especially I like:
[LIST]
[*]automatic parentesis and quote completion
[*]bookmarks(One of my favorite Notepad++ features)
[*]word highlighting(press alt-w)
[*]line highlightning(alt-l)
[*]snippets
[/LIST]
Summary: It's Very Good, but still also Simple. A good combination and definitely my new text editor of choice. It blows Gedit away...

---

### Post by commodore on 2006-05-21
Vim and Emacs can't paste "normally" copied text?

---

### Post by cgjones on 2006-05-21
[QUOTE=commodore]Vim and Emacs can't paste "normally" copied text?[/QUOTE]

Vim can. Shift+Insert.

---

### Post by rydow on 2006-05-21
Sure emacs can paste as well (CTRL + y) and ctrl insert for copy.
But it's often faster using mouse to mark in another window and paste by clicking left end right mouse buttons at once where you want paste. (Yes i have an old 2 btn mouse)

Cheers
Jonas

---

### Post by Gustav on 2006-05-21
The latest emacs-snapshot has the option to make ctrl-c, ctrl-x and ctrl-v work as copy, cut and paste.

---

### Post by commodore on 2006-05-21
Oh. Thanks. If they couldn't do it, IMO they wouldn't be OK for confing files.

---

### Post by Somenoob on 2006-05-21
I have been using emacs now and it's ok.

But i wan't to try wim, but i'm having problems installing Vim 7.0

---

### Post by WirelessMike on 2006-05-22
Learning Vi can save you some work in the long run.  Pretty much every Unix/Linux derivative has it default.  It may not seem very user-friendly at first, but like anything, it becomes very easy over time.  Among the machines I admin, I regularly work on 3 Linux machines and 2 Unix servers.  Vi provides a nice, comfortable consistency among them.

Of course, a REAL geek would bring up sed and awk, and more than a handful of modern geeks still use those sometimes.  Personally, however, Vi/Vim has always been more than sufficient for my needs.

---

### Post by skunkydog on 2006-05-27
You should run notepad.exe on wine

---

### Post by mynimal on 2006-05-27
SciTE is BY FAR my favorite editor, hands-down. I tried Cream and Scribes but none of them came close to SciTE. It's a little bit harder to configure its settings, but once you're done it's worth it. I'm including my configuration file and a screenshot. Rename SciTEGlobal.properties.txt to SciTEGlobal.properties and put it in /usr/share/scite.

Edit: Also, it's set to adapt to your icon theme.

---

### Post by fos on 2006-05-27
emacs and xemacs are the most capable of all editors I have used. Jed is a simple alternative. Vi is always available. I probably use it more frequently than the others, it is quick and reliable.

fos....

---

### Post by B0rsuk on 2006-05-29
I prefer Kate. [http://kate.kde.org/images/kate_01.png](http://kate.kde.org/images/kate_01.png)

It's easy to jump into, because the interface is much friendlier than vim or emacs. It has many nice features, like line numbers, syntax highlighting for few dozen languages, hide/show for functions/html tables (the plus and minus thingy). Incremental search (like ctrl-F in firefox; requires kate-plugins package), search and replace using regexp... it has enough features to make my university programming convenient, and there are still things I don't need at the moment/waiting to be discovered.
About potential of Kate: our teacher says Kate has potential to become a very good tool, and this opinion comes from an emacs contributor.

---

### Post by IYY on 2006-05-29
vi is my editor. Takes a while to get used to, but then it works like magic.

---

