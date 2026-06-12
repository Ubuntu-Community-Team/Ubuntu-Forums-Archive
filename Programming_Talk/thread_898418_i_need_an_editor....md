---
title: "i need an editor..."
date: 2008-08-23
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-08-23
i know this is flame war territory but i dont want one...yes i know the holy war is in the sticky

im still looking for an editor for linux...and ive heard alot about vim and emacs

this is what i want to know:

what are the main differences...ive looked at both websites and cant really tell the difference...both are supped up editors that you all seem to love one or the other...

i would love if i could get straight unbiased facts about each like which one is harder to learn which one supports more languages...i also couldnt find a list of vim supported languages...any answers here would be great

also if these were answered in the holy war post thats in the sticky im sorry because i didnt read the whole thing

---

### Post by cprofitt on 2008-08-23
I actually use SciTE; which supports many languages and is cross platform.

---

### Post by jimi_hendrix on 2008-08-23
thats another one im looking at but id like to here an unbiased comparison of vim and emacs

---

### Post by lukjad on 2008-08-23
I always wanted to know the difference also but was too afraid to ask.

Out of curiosity, is gedit anything like Vim or emacs?

---

### Post by jimi_hendrix on 2008-08-23
from what ive seen on the websites they are suped up gedits...i havent been able to see much more (other then the syntax highlighting and that you can play tetris on emacs)

---

### Post by brunovecchi on 2008-08-23
It is difficult to find a complete, educated and unbiased opinion because few people are proficient in both vim and emacs.
There are many differences between them, but I suggest that you install both, do the tutorials that come with them, and see which of them fits better in your head. I did that and stuck with vim.
The main difference that comes to mind is the way they handle keyboard bindings: emacs accomplishes this with sequential key combinations (ie, crtl key1 key2), and vim does so by having two editing modes (insert and edit), which allows to have really short (one key) keybindings.
None of them have a low learning curve, but It's worth the time.
If you are going to install vim, note that there is a vim-gnome package that comes with a nice native-looking gui.

---

### Post by jimi_hendrix on 2008-08-23
are they in respetories?

---

### Post by lukjad on 2008-08-23
Yes! If Ubuntu didn't have them... geeks would kill them.
```
sudo apt-get install vim
sudo apt-get install emacs
```

---

### Post by jimi_hendrix on 2008-08-23
> **brunovecchi said:**
> 
If you are going to install vim, note that there is a vim-gnome package that comes with a nice native-looking gui.

were can i get this...the vim i installed runs in terminal

---

### Post by nvteighen on 2008-08-23
> **jimi_hendrix said:**
> from what ive seen on the websites they are suped up gedits...i havent been able to see much more (other then the syntax highlighting and that you can play tetris on emacs)

With such a post (vi and emacs = suped up Gedits) you'll be able to make peace between vi-ers an emacs-ers just to fight against you... :)

OK, being serious. My experience is with Gedit and Emacs.

1) Don't underestimate Gedit. It's a very nice text editor. Learn how to use it and you'll get some nice features: look at the plugins. It **does have** syntax highlighting (it's activated automatically when you save the file with the proper extension or manually through the View menu), smart tabs, parenthesis match, integrated shell...

2) Emacs is great... much more than a "suped up Gedit". It's strength relies on being absolutely customizable and programmable, because of it's Lisp interface. Check the Emacs Tutorial (C-h t) to learn how to use its most basic features.

The only truth is never use ed!

---

### Post by LaRoza on 2008-08-23
> **jimi_hendrix said:**
> were can i get this...the vim i installed runs in terminal

Yes, use that. Vim is a terminal editor. If you don't like it now, come back to it later. I use Gedit and Vim for editing.

If you need Vim references, see my wiki: [http://laroza77.wikidot.com/references](http://laroza77.wikidot.com/references)

If you are looking to get opinions on editors, that is silly ;) You can only try them for yourself and see what you like. Obviously, we are all going to recommend our editors of choice.

---

### Post by jimi_hendrix on 2008-08-23
thanks for the wiki help...and yes i installed both and will use the one i like more...last question does either one have a compiler or do i need an add on for that

---

### Post by loganwm on 2008-08-23
Kate is amazing in my opinion :)

clean interface, terminal built in, syntax highlighting (all I've tried is C and C++), multi document view, and it's simple and standard on KDE. ( I think? Correct me if I'm wrong)

---

### Post by jimi_hendrix on 2008-08-23
i use ubuntu though not kubuntu :)

---

### Post by jayson.rowe on 2008-08-23
Be sure to check out Cream - basically Cream makes gVim a little more "friendly" by using standard commands rather than VI specific commands.

Worth a look IMHO - I like it a lot.

---

### Post by lukjad on 2008-08-23
Kate works in Ubuntu!

---

### Post by Maveric3477 on 2008-08-23
I use Emacs simple because of Slime (To do with Common Lisp, and various other lisps). I have recently gone through the Vim tutorial, and I honestly say I can see why a lot of people prefer it over Emacs. 

Then again, I can say the same abotu emacs.

Both make it incredibly easy to edit things, as soon as you become comfortable with the editor. Like a few other comments, I think you should go through the tutorisl on them, and then pick one.

Really, the differences between the two aren't that great. Sure, it's completely two different ways to do the same thing, but when you know one, you'll be doing what you need to do a LOT faster and it'll soon become to feel like the computer is an extension of your brain, not a tool you have to fight to use!

P.S. Emacs is the shizniz, :P Anyone who says otherwise is just talking out of their... well, you know the 'a' word :P (Am joking here, we all love a giggle)

---

### Post by LaRoza on 2008-08-23
> **jimi_hendrix said:**
> last question does either one have a compiler or do i need an add on for that

Rethink that. An editor is not a compiler. It can be used with a compiler, but the editor itself is not a compiler. Use whatever you normally use in Linux (gcc, g++, etc)

---

### Post by pfdevil on 2008-08-23
In my opinion are you a programmer looking for an editor or are you looking to write some documents?

Programmer: vi 

Writing Docs: Open Office

Development Environments: Eclipse or Kdevelop

Do yourself a favor and learn vi in terminal, we are so use to a GUI that we seem scared of the terminal....

Download a vi cheat sheet and start editing.

---

### Post by snova on 2008-08-23
You said you wanted an unbiased comparison of vim and emacs, so who better to give it than someone who doesn't use either of them? And here I am, trying to stay in the middle.

vim is "modal". You have to press the I key to insert text (though it'll figure out what you want eventually if you just start typing). While in this mode, you can't do anything *but* insertion until you go back to command mode with the ESC key. Then everything does something different: for example, the HJKL keys are used for movement. I believe D is used to delete lines. I also believe you can attach a number to delete more than one.

Emacs has a zillion different key combinations to do a zillion different things. Actually, Emacs doesn't do anything by itself: the core of Emacs is an interpreter for a programming language similar to Lisp. Most of the editor proper is written in Elisp (as it's sometimes called).

As a result, Emacs can be programmed to do just about anything, if you know how. There are even games written for it, such as a Towers of Hanoi solver and a psycoanalysist ("Eliza").

Summed up: Vim is minimalistic. It does what it does and not much more, but it does so quickly. No control keys are used (as far as I know). Emacs is everything else: but you have to figure it the combinations (or change them, of course) first.

Vim users say Emacs is, "A great operating system, lacking only a decent editor" and Emacs people say that "vim has two modes: 'beep repeatedly' and 'break everything'".

I don't use either of them; but I'll admit that, forced to choose, I'd probably go with vim. I figured out enough of its functionality to get something done within a few minutes, but Emacs remains a mystery to me. There are simply too many key combos to remember.

Was I any help?

---

### Post by LaRoza on 2008-08-23
> **snova said:**
> 
vim is "modal". You have to press the I key to insert text (though it'll figure out what you want eventually if you just start typing). While in this mode, you can't do anything *but* insertion until you go back to command mode with the ESC key. Then everything does something different: for example, the HJKL keys are used for movement. I believe D is used to delete lines. I also believe you can attach a number to delete more than one.


Vim is modal, but there is a "visual" mode and there are more modes and keys to use.

---

### Post by slavik on 2008-08-23
> **jimi_hendrix said:**
> i know this is flame war territory but i dont want one...yes i know the holy war is in the sticky

im still looking for an editor for linux...and ive heard alot about vim and emacs

this is what i want to know:

what are the main differences...ive looked at both websites and cant really tell the difference...both are supped up editors that you all seem to love one or the other...

i would love if i could get straight unbiased facts about each like which one is harder to learn which one supports more languages...i also couldnt find a list of vim supported languages...any answers here would be great

also if these were answered in the holy war post thats in the sticky im sorry because i didnt read the whole thing
vim is probably harder to learn ...

---

### Post by LaRoza on 2008-08-23
> **slavik said:**
> vim is probably harder to learn ...

"Probably"?

Vim is simple. Of course memorizing everything would be hard, but just as hard for anything else.

---

### Post by pfdevil on 2008-08-23
"Real Programmers Use VI" <<-- Haha Flame Wars

---

### Post by jimi_hendrix on 2008-08-23
> **pfdevil said:**
> "Real Programmers Use VI" <<-- Haha Flame Wars

[http://xkcd.com/378/](http://xkcd.com/378/)

does either vim or emacs have text highlighting

---

### Post by LaRoza on 2008-08-23
> **jimi_hendrix said:**
> 
does either vim or emacs have text highlighting

Yes, of course.

For the Ubuntu package, install "vim". The default Ubuntu (Debian) Vim is "vim-tiny" which has minimal features.

---

### Post by monkeyking on 2008-08-23
I always use vi/vim if I just need to change small things.
change a value in a file, do a Makefile etc etc.

But If I need to spend hours in front of an editor,
I would use emacs.

emacs is much better at syntax highlighting and auto indentation.
But still vi has the possiblety to jump to matching bracket,paranthesis etc. which is rather nice.


So I would recommend getting to know both of them.

---

### Post by pfdevil on 2008-08-23
> **jimi_hendrix said:**
> [http://xkcd.com/378/](http://xkcd.com/378/)

does either vim or emacs have text highlighting

Haha, awesome.

---

### Post by jimi_hendrix on 2008-08-23
> **LaRoza said:**
> Yes, of course.

For the Ubuntu package, install "vim". The default Ubuntu (Debian) Vim is "vim-tiny" which has minimal features.

how do i get a vim with text highlighting

---

### Post by monkeyking on 2008-08-23
after you have installed the bigger vim type in

```
:syn on
```

---

### Post by jimi_hendrix on 2008-08-23
where do i type that...and what does it do?

---

### Post by pfdevil on 2008-08-23
Hey you wil need to open vim in the terminal

```
random@random-laptop:~$ vi
```

then when vi is open type ```
:syn on
```

---

### Post by mali2297 on 2008-08-23
> **jimi_hendrix said:**
> where do i type that...and what does it do?

When you're in command mode. You start in command mode so just type the command and you will see it at the bottom. It turns on syntax highlighting.

---

