---
title: "c++ in windows or ubuntu?"
date: 2010-05-13
forum: Programming Talk
---

### Post by l3ecl on 2010-05-13
whats your choice of programming software for c++? vi, emac, visual studio?  im a computer science major but i've never programmed in linux before. i've written alot of my programs in visual studio but never in emac or vi. since i've installed ubuntu, i thought i'd give it a shot. so what should i use?  ps:i like visual studio b/c of intellisense and drag and drop when making gui applications.

this is so awesome:

[LIST=1]
[*][vi inside eclipse]("http://www.satokar.com/viplugin/")
[*][visual debugger]("http://code.google.com/p/debugvisualisation/")
[/LIST]

---

### Post by sxmaxchine on 2010-05-13
i use visual studio because the only non web langauge i know is visual basic, but for my javascript and html i use bluefish o both widows and ubuntu.

on ubuntu i tried python and used geany, geany also supports other lagauges.

---

### Post by dribeas on 2010-05-13
If you want autocompletion then you better go with some IDE instead of plain editors. Some of the popular IDEs for C++ can be Eclipse CDT, Netbeans, QTCreator, Code::Blocks... But if you come from VisualStudio you will miss many things --the VS debugger is wonderful, intellisense is better in VS than in the versions I have tried of Eclipse, Netbeans or QTCreator.... I cannot talk about drag and drop GUI creation, but I would guess that you can get some of it with QT and QTCreator (or plugins for either Eclipse or Netbeans).

Vi and emacs are editors, not really IDE. You may get some sort of autocompletion with the use of ctags or the like, but the editor has no knowledge of the language, so the completion offers will in most cases be unrelated to context (do not expect 'object.?', where ? stands for whatever key combination pulls autocompletion, to show only methods and attributes of 'object')

I, myself, have used and would recommend Eclipse or QTCreator. People talk positively about Netbeans and Code::Blocks, but I never got used to the look and feel of Netbeans and I have never used Code::Blocks. In a daily basis I do most programming with vim+gcc+make in the command line over a screen session, but that is probably related to the specific environment where I work (chroot context where we cannot really install new software, so using IDEs implies having the IDE run in the real system with some sort of 'remote' compilation and debugging).

I would have liked to know how to really take advantage of emacs... but I guess is late for me. I feel clumsy moving within emacs as compared to vi, after 15 years using vi as my main editor.

---

### Post by mmix on 2010-05-13
[http://ubuntuforums.org/showthread.php?t=1481335](http://ubuntuforums.org/showthread.php?t=1481335)

or
[sam](http://en.wikipedia.org/wiki/Sam_%28text_editor%29) vs [acme](http://en.wikipedia.org/wiki/Acme_%28text_editor%29) from [plan9port](http://swtch.com/plan9port/)

or
[http://stackoverflow.com/questions/24109/c-ide-for-linux](http://stackoverflow.com/questions/24109/c-ide-for-linux)

or
openldev (abandoned, automake built-in)
[http://sourceforge.net/projects/openldev/files/](http://sourceforge.net/projects/openldev/files/)

HTH

---

### Post by lisati on 2010-05-13
You might find this interesting: [http://ubuntuforums.org/showthread.php?t=1006662](http://ubuntuforums.org/showthread.php?t=1006662)

---

### Post by TheStatsMan on 2010-05-13
I used to use visual studio when I coded in Windows, and I use Vim now. I tried a whole lot of IDEs in between. Whilst Visual Studio is good for an IDE, in my opinion it is very inefficient in comparison to Vim. I could never go back to IDEs. I find for C++ code completion works quite well in Vim. Actually of all the languages I code in I find Vim works best with C++.

---

### Post by l3ecl on 2010-05-14
i like using vi but holy **** eclipse just came out with a[ visual debugger]("http://code.google.com/p/debugvisualisation/"). that is very sexy.
has anyone used eclipse? if they came out with a [vi emulator ]("http://www.viemu.com/")for eclipse i'd orgasm so hard it'd hit my pocket protectors.

---

### Post by devilized on 2010-05-14
I just use either vi or gedit, and use gdb for debugging. There are probably easier ways of doing it, but I don't use C++ enough anymore to bother installing an IDE. When I was taking Computer Science classes, I used Visual Studio for the first semester but I wasn't a huge fan.

---

### Post by l3ecl on 2010-05-14
> **l3ecl said:**
> i like using vi but holy **** eclipse just came out with a[ visual debugger]("http://code.google.com/p/debugvisualisation/"). that is very sexy.
has anyone used eclipse? if they came out with a [vi emulator ]("http://www.viemu.com/")for eclipse i'd orgasm so hard it'd hit my pocket protectors.

[thrill]("http://www.satokar.com/viplugin/")

what are your opinions on an IDE with a vi emulator? don't you get best of both worlds?

---

### Post by leg on 2010-05-14
I think code::blocks would be a fairly good drop in for Visual Studio, free version anyway. I like using it and find it very useful and I now use it on Windows computers also which means I only use the one IDE. Geany is a very good little editor if you don't want to use a full IDE.

---

### Post by l3ecl on 2010-05-14
> **dribeas said:**
> 

I would have liked to know how to really take advantage of emacs... but I guess is late for me. I feel clumsy moving within emacs as compared to vi, after 15 years using vi as my main editor.


I have 0 experience with emacs. whats the deal with it?

---

### Post by BoneKracker on 2010-05-14
Eclipse or vi, depending on what you're doing.

---

### Post by l3ecl on 2010-05-14
> **BoneKracker said:**
> Eclipse or vi, depending on what you're doing.

you can have [vi inside eclipse]("http://www.satokar.com/viplugin/")
how cool is that?

---

### Post by TheStatsMan on 2010-05-14
> **l3ecl said:**
> [thrill]("http://www.satokar.com/viplugin/")

what are your opinions on an IDE with a vi emulator? don't you get best of both worlds?

 It probably depends on the person. I always find vi emulators a disappointment compared to the real thing. In many cases the IDE doesn't add anything it just slows you down. It is way faster to change configurations in Make than in an IDE. The equivalent plugins for a symbol browser is way faster to navigate between classes and functions than an IDE. You can take advantages of tools like the Terminator. Not to mention Vim is is lightweight and extremely fast, where as IDEs are often heavyweight and relatively slow.

---

### Post by BoneKracker on 2010-05-14
> **l3ecl said:**
> you can have [vi inside eclipse]("http://www.satokar.com/viplugin/")
how cool is that?
Yeah, and you can pitch a tent inside your house, but why would you? :P

---

### Post by lightstream on 2010-05-14
l3ecl --> Am I being cynical or are you just a bit over-enthusiastic about a paid-for Eclipse plug-in that emulates vim?

What does it do beyond reassigning Eclipse's keystrokes to match those of vim?

And how much money do get from it?

> **l3ecl said:**
> [QUOTE=l3ecl;9296981]i like using vi but holy **** eclipse just came out with a[ visual debugger]("http://code.google.com/p/debugvisualisation/"). that is very sexy.
has anyone used eclipse? if they came out with a [vi emulator ]("http://www.viemu.com/")for eclipse i'd orgasm so hard it'd hit my pocket protectors.[thrill]("http://www.satokar.com/viplugin/")

what are your opinions on an IDE with a vi emulator? don't you get best of both worlds?[/QUOTE]

And finally - this particularly applies if you answer 'none' to the previous question - how come you have linked to this plug-in several times in this thread, including one time where you appear to be ignorant of it, until you reply to your own post with another link to this plug-in (see above)??

Edit - OK my cynicism was unfounded, it's how you edited your posts, in particular the first one, to add the link to this VIM plugin that confused me! Still what does this plug-in do beyond add vim's keystrokes to Eclipse?

---

### Post by l3ecl on 2010-05-14
.

---

