---
title: "Should I learn emacs, vi, or something else?"
date: 2007-07-07
forum: Programming Talk
---

### Post by GreenGirl on 2007-07-07
I'm a linux newbie, and I'm wondering what text editor to learn.  I've noticed that this seems to be a subject that people feel very strongly about, so I thought I'd see what you guys think.  I'm a web programmer, and I'm hoping to learn bash scripting and brush up on some non-web programming languages (open source programming looks like it could be a cool thing to get involved with in my spare time).  So the editor has to be good for many different types of programming.

I'm leaning toward emacs right now, because the idea of having to toggle between modes in vi seems like it would be really frustrating.  I also like how emacs has built in modes for specific programming languages, and how it can be customized with Lisp.  On the other hand, the commands in emacs seem sort of ridiculous (ctrl-x ctrl-s to save?  Seriously, why would something as simple and common as saving the file require two commands?) and the feature creep that it's apparently had over the years is just bizarre (there's something inherently wrong with being able to play Tetris in a text editor).

So what should I do?  Learn vi and just accept that I can't customize it and have to constantly toggle between modes, or learn emacs and get used to the absurd commands and ignore the useless features?  Or learn something else entirely?

---

### Post by Wybiral on 2007-07-07
I'm a gedit user and have been for some time now.

It's simple, has tabs, a good plugin system, and syntax highlighting.

Nothing fancy, but it works (especially when you jump between lots of languages like me)

---

### Post by Anonii on 2007-07-07
I personally prefer Vi. You will get used to mode switching after a while. I used to use emacs, but it has TOO many useless features to me. 
Anyway, I'm not going to make a lengthy post highlighting the good points of Vi and the weaknesses of Emacs, since they are not that many , and imo, Emacs is a more-than-excellent application, but it just doesn't make it fo-

OH SHI- IS THAT A BIRD? IS THAT A PLANE? OH NO! IT'S A FLAME WAR!

---

### Post by pbaumgar on 2007-07-07
I'd learn at least the basics in Vi.  How to edit files, move around, do global search and replace, etc.  Vi will almost always be on any Linux system you encounter that is not running X Windows; Programs like Emacs, Gedit, nano will not typically be installed by default without X Windows.

---

### Post by reacocard on 2007-07-07
I just switched to vim (from geany) about a month ago and I really like it. The moded editing is surprisingly easy to get used to, and the included tutorial is pretty good as well. there are a number of good addons for vim as well, I particularly like project.vim, which lets you easily keep tracks of and open the files for a project.

Geany is a very good editor too, give it a try.

---

### Post by Modred on 2007-07-07
I'm a die hard Vim fan, but that's probably mostly because I was introduced to Vim before Emacs.  Toggling between modes really isn't such a big deal; it becomes second nature very quickly.  With either editor you will likely take a while to get it fully customized to the level you want.  I've been using Vim for nearly two years and am still finding useful features that I wasn't aware of.

To continue on the mode bit, after the initial adjustment it doesn't feel like you're changing your environment so much as just making use of a normal feature like copy/paste.  If you don't like Vim starting in "normal" mode, then you can add "set insertmode" to your ~/.vimrc so that it will start up and stay in insert mode.  You can hit CTRL+O to enter normal mode for the duration of one command when needed.  Personally, this doesn't seem to make very adequate use of Vim's features and wide array of commands that are available from normal mode, but it's a matter of personal preference.

---

### Post by HermanAB on 2007-07-07
Hmm, you need to know how to open, edit and save a file using 'vi', since sometimes that is only damn thing you have available.  However, I always install 'nano' and 'joe' as soon as I have the opportunity, since those are far less annoying than 'vi' or 'emacs'.  Mostly I edit files using 'gedit' or 'kedit' though.

---

### Post by jayson.rowe on 2007-07-07
i like joe

---

### Post by geraldm on 2007-07-08
Saving a file in emacs is not a hangup.  It is just the (4) keys for 2 characters.  
Vi, or better, vim, 3 characters: <ESC>":w" 
Choosing between these is akin to choosing a religion.
Emacs has a steep learning curve, which becomes a very productive
working environment.
For a very simple, fast, emacs-like editor I use zile, which includes a brief tutorial.
Vim can be customized, and its syntax highlighting is definitely an advantage.
For use with many programming language editing, Vim and Emacs would be among
the top choices.  You can learn enough to edit simple files in less than a day in
either one.  Start simple, and see if you remain comfortable with it after using
it for several days.  If you do choose emacs, stay away from the bizarre!

Gerald

---

### Post by pmasiar on 2007-07-08
vi is installed everywhere - it is safer bet. vi has another important plus for me: it is scriptable in couple languages, Python being one of them. emacs uses lisp, so unless you are ready for major time investment, it will not be easy to customize emacs. But I did seen experts using it, and I did envy how much they were capable to accomplish by just couple keystrokes.

vim has many "plugins" to make it more like "standard" editors, cream being one of them.

But becoming proficient in either vim or emacs is major time investment. I decided for vi(m) but I am postponing real immersion, because of time commitment. So far I squeak by using simpler editors, like embedded mc, and scite.

If you are into cool tools, you may want to check mc - midnight commander. It is extremely efficient file manager: GUI-like, but character-based interface to all functions of your OS. Proven by 25 years of  usage - I am sure that if it was promoted more, people would be less afraid of commandline.

---

### Post by runningwithscissors on 2007-07-08
vim > *

---

### Post by krugman on 2007-07-08
Well, since everybody seems to be in favor of ViM, I will vote for Emacs.
But first, I want to add that I am in no way a programmer: indeed, I have just started learning C.
However, I have completed a PhD recently and I have used Emacs with AucteX for writhing my thesis and it was very efficient. Emacs is not that hard to learn and there are a lot of resources on the web. As to the keystrokes, yes it is a bit weird at the beginning, but doing Ctrl+X Ctrl+S for saving, Ctrl+X Ctrl+C to quit or Ctrl+C Ctrl+F Ctrl+B to write a word in bold (in AucteX) is actually not that hard and it becomes second nature (since F is for "font" and B for "bold") very quickly.

Furthermore, I know nothing about Lisp but I have been able to customize Emacs with the help of others on the web; for instance, there are a lot of examples of .emacs files which is the configuration file Emacs uses when it loads. There are also a lots of menus to help you customize without having to write code. Of course, there are many things I don't know how to do, but I keep learning.

Finally, I can't recall the name, but there is a ViM mode available in Emacs that allows you combine keystrokes from Emacs with keystrokes from ViM.

Hope this helps!

---

### Post by AnRa on 2007-07-08
In my opinion, you should try both. :)

---

### Post by GreenGirl on 2007-07-08
Thanks everyone.  I think I'll start learning Vim for now, but I won't delete Emacs from my computer just yet. :)  I'm still interested in hearing opinions, so if anyone else has a recommendation, please post it.

---

### Post by GreenGirl on 2007-07-08
Is there a GUI version of vim, or am I supposed to use the terminal?

---

### Post by xadder on 2007-07-08
Use gvim for the GUI mode. It may still be better to learn the terminal version first though, until the fast keystrokes become second nature. gvim allows use of keys or mice.

---

### Post by reacocard on 2007-07-08
> **GreenGirl said:**
> Is there a GUI version of vim, or am I supposed to use the terminal?

There's gvim, install the vim-full package and launch it with either gvim or vim -g.

---

### Post by reacocard on 2007-07-08
> **xadder said:**
> Use gvim for the GUI mode. It may still be better to learn the terminal version first though, until the fast keystrokes become second nature. gvim allows use of keys or mice.

You can do that with the terminal one too, although not all terminal emulators support all the features (eg. right-click doesn't work in gnome-terminal)

---

### Post by Ex-Cyber on 2007-07-08
You should learn at least the basics of vi simply to be able to use it when it's the only option (e.g. editing broken config files from a rescue disk). Beyond that it is simply a matter of personal preference. I usually end up using Emacs on Linux/BSD only because I'm used to it. That said, my favorite editor is [acme](http://www.cs.bell-labs.com/sys/doc/acme.html), though it loses a bit without the surrounding Plan 9 or Inferno environment. It can be installed on Linux or BSD as part of [Plan 9 from User Space](http://plan9.us), although I don't recommend that route until you're comfortable with the command line and building/installing programs yourself (i.e. without the package manager). There is also a decent but somewhat inferior clone called wily that runs natively on Linux.

---

### Post by nitro_n2o on 2007-07-08
> **GreenGirl said:**
> Is there a GUI version of vim, or am I supposed to use the terminal?
i don't think you should use the GUI vim for the following reasons: 
0- you'll ruin the keyboard fun :D .... 
1- you are a webprogrammer and might need to connect to a server, normally you don't forward X over ssh it's just slow most of the time. That is when Vim is really great.. 
2- gVim doesn't look very beautiful :( 

But, if you insist on using the gui... there is a nice version and has more features called "cream" 
sudo apt-get cream 

Yes the name might be silly, but it has so many features.. you can use it as a normal text editor or as a Vim expert with all the keyboard fun.... 

Have fun and welcome to Vim's world :)

---

### Post by maddog39 on 2007-07-08
I personally cant stand using command line editors, they are far to restrictive at a basic level, they take too much time to learn, and tend (in my case) not to be very productive. Im mostly referring to both vim and emacs. If I am not running X, then I use nano setup with syntax highlighting. Otherwise I use gedit or geany. I especially dont recommend highly advanced CLI text editors to beginner users, I just think that its too much, it goes a bit overboard.

---

### Post by ButteBlues on 2007-07-08
I like Emacs. With the right .emacs file, the GTK version becomes very simple but very beautiful.

Edit: Yes - this is the gtk version, not the terminal.

---

### Post by bread eyes on 2007-07-08
I like Xemacs.

---

### Post by primski on 2007-07-09
so much discussion for a simple editor :d

if this is going to be your major challenge, i dunno, man, should you be bothering at all?

I personally use all of them :P

---

### Post by pmasiar on 2007-07-09
> **primski said:**
> if this is going to be your major challenge, i dunno, man, should you be bothering at all?

I personally use all of them :P

1) I doubt you are *expert* in both. You may think you are, but it's not the same as being one.
2) OP nick contains "girl" so OP might easily be girl.
3) You are patronizing without providing any info. Does it feel like you are better than others?

IMHO OP is very smart to ask questions before investing lots of time in a tool. I did the same and (for reasons cited in my previous post) got to a conclusion. It was not based on random advice or random (good or bad) experience, but rational research of my options. I think that OP, by showing rational process when selecting a tool to learn well, shows substantial potential to growth - while your post, primski, shows attitude but without the potential :-)

---

### Post by primski on 2007-07-10
Since im a calm and friendly person i will not engage in any kind of hostile debate. 

I missed the 'nick' part, but the thought about making differences from your point of view suggest you are not very emancipation friendly person, so the fact 'she' really did come for help and your kind-of 'she's-a-girl-why-dont-we-all-jump-on-her-pretending-to-help-he'r kinda attitude suggest the patronizing it self.

im gonna let you keep your HO in your 'imho'  because u know nothing about me nor my skills, so I can calmly say mastering a text editor isnt my greatest achievement, which i cannot say for you.

Sorry man, being so offensive wasn't my primary goal, but your offensive couldnt keep me calm either.

---

