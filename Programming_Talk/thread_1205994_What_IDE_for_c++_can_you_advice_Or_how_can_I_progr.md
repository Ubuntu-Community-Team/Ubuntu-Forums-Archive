---
title: "What IDE for c++ can you advice? Or how can I programme better on c++ in linux?"
date: 2009-07-06
forum: Programming Talk
---

### Post by fr0d0 on 2009-07-06
Good time.

I've worked a lot in VS 2005. I've different experience in linux (debian&ubuntu&other systems). But the greatest experience was in Debian because I've tuned and supported internet+ftp(samba)+http servers about an year. And it works even now.

The question:
What can you advise me to programme on c++ in linux? Maybe NetBeans or so on? Maybe console+gdb? Maybe some IDE instead of VS 2005? I want to switch from windows to linux. And I must work in it without any problems with coding.

I'm waiting for your advices.
Thanks.
:guitar:

---

### Post by TheStatsMan on 2009-07-06
Try doing a search. This topic comes up every few days. I prefer vim + console FWIW.

---

### Post by pepperphd on 2009-07-06
I use Kdevelop. I understand that linux users are obsessed with their command line editors but i cant' see why. Being able to tab through your few dozen source files with the click of a mouse is just one thing I could never do without while programming. Type your linker flags once and forget them. Stuff like that. I found Eclipse very laggy and cluttered, but Kdevelop is just right.

---

### Post by OutOfReach on 2009-07-06
I also use KDevelop (3.x series, NOT the upcoming 4 release). I find that it has everything that I need, but it does have a few drawbacks, nothing serious tho.

---

### Post by TheStatsMan on 2009-07-06
> **pepperphd said:**
>  I understand that linux users are obsessed with their command line editors but i cant' see why.

I used to have this view, it has somewhat changed over time. I couldn't see why everybody seemed to prefer text editors, as all the shortcuts seemed to be in the IDE's anyway. One day I got curious and looked into vim and haven't looked back since.

> 
Being able to tab through your few dozen source files with the click of a mouse is just one thing I could never do without while programming. 


This can be done with any decent text editor.  

> 
Type your linker flags once and forget them. Stuff like that.


Well if you use a Makefile (or something equivalent) then you only type them once as well, but they can be changed a lot quicker. No clicking through menus.

---

### Post by Mad Hacker on 2009-07-06
[kdevelop]("http://www.kdevelop.org/")
[codeblocks]("http://www.codeblocks.org/")
[anjuta]("http://projects.gnome.org/anjuta/index.shtml")(i haven't used it much, but it seems pretty good)

---

### Post by bear24rw on 2009-07-06
codeblocks ftw

sudo apt-get install codeblocks

---

### Post by Mirge on 2009-07-06
Eclipse CDT

---

### Post by JordyD on 2009-07-06
Qt Creator. Only if you're making Qt programs, though. Otherwise go with something more general, like KDevelop or Code::Blocks.

---

### Post by c0mput3r_n3rD on 2009-07-07
> **TheStatsMan said:**
> I used to have this view, it has somewhat changed over time. I couldn't see why everybody seemed to prefer text editors, as all the shortcuts seemed to be in the IDE's anyway. One day I got curious and looked into vim and haven't looked back since


Vim is my absolute favourite way to wright my programs in any language.  You can do just as much in Vim as you can in any other text editor.  Plus the g++ compiler is great at error handling, and debugging; as well as being easy to use.  I also learned on the command prompt before I ever picked up a a gui in Linux.

---

### Post by fr0d0 on 2009-07-07
Thanks for your advices. I'll try this.

Another small question: I think all or major part of you have used Visual Studio. So, maybe there is any analog that works similarly (with gui for form design, properties and events.)
;) Thanks.
I'm waiting for your advices.

---

### Post by zolookas on 2009-07-07
QtCreator has GUI designer, similar to Visual Studio.

---

### Post by JordyD on 2009-07-07
> **zolookas said:**
> QtCreator has GUI designer, similar to Visual Studio.
:D Why I recommended it. You will want to read the Qt Designer manual first so that you can get used to it.

---

### Post by fr0d0 on 2009-07-07
I tried to use QT few years ago in Windows, when I even can't code(programme) on c++. So, I have some problems then. I've just download new Ubuntu cd and I'll install it on my notebook. I've sold my desktop(home) computer and bought notebook. Because of it I have no linux for few weeks. And now I'll solve this problem.:lolflag:
I'm glad to see and chat with all of you. Because it is very easy and greatfully to communicate with like-minded persons. ;)

---

### Post by JordyD on 2009-07-07
> **fr0d0 said:**
> I tried to use QT few years ago in Windows, when I even can't code(programme) on c++. So, I have some problems then. I've just download new Ubuntu cd and I'll install it on my notebook. I've sold my desktop(home) computer and bought notebook. Because of it I have no linux for few weeks. And now I'll solve this problem.:lolflag:
I'm glad to see and chat with all of you. Because it is very easy and greatfully to communicate with like-minded persons. ;)
Qt can be used with other languages, but you'd be unable to use the GUI designer. I definitely recommend Qt + C++, they even have a book for it: [C++ GUI Programming with Qt 4]("http://www.amazon.com/dp/0132354160/"). I plan on buying it. The only downside to Qt is that it looks really bad in a GNOME environment, so if you're using a GNOME environment, and you want your GUIs to look native, use Anjuta. It also has a GUI builder, although of lesser quality IMO. But if you're using KDE, Qt is great since it now looks native on Windows, Mac, and KDE, whereas GTK looks native on GNOME only. (Windows and Mac are possible if themed correctly). In either case you should learn C++, as it's the language in which you'll be able to use GUI builders (or Python with GTK) and it's supported very well (as in more people are available that can help you on problems).

My 2 cents.

---

### Post by fr0d0 on 2009-07-07
Simle question: what size will be the best for system ext3 partition?
And how you organaze your partitions?:p

---

### Post by resander on 2009-07-07
I left Windows for Ubuntu about a year ago having used Visual Studio for 10+ years. I looked at the Ubuntu forums and Googled and found people thinking codeblocks was a good choice. I installed it and have used it ever since. Don't know anything about other IDEs, but codeblocks has everything I need.

The Ubuntu upgrade system notifies Ubuntu codeblocks users about upgrades several times per year. To get the latest version I just click the 'upgrade' button and wait a few a minutes. Next time I enter codeblocks I would be using the latest version without having to lift a finger. Nice.

---

### Post by fr0d0 on 2009-07-14
Thank you. I'll try some/maby all and answer in this topic.

---

### Post by TheBuzzSaw on 2009-07-14
After many rigorous tests on my part, my loyalties remain with Code::Blocks. It does everything I need it to, and it runs lightning fast.

bloated IDEs suck

---

### Post by esaym on 2009-07-14
I use vim + screen

First I start a screen session by typing "screen"

Then press ctrl+a+c (note all screen commands are prefix with ctrl+a. Press ctrl+a then release that and press the next letter) a couple of times to create a few virtual terminals.  Then ctrl+a+1 to change to terminal 1.  In terminal 1 I open my files with vim in tabbed mode vim -p file.cpp file.h file2.cpp
Write code and then to compile I jump over to the next terminal with ctrl+a+2 and run g++ or on a bad day gdb

My .vimrc:
syntax on
set background=dark

My .screenrc:
caption always "%{Yk} %H %0c:%s %{k}|%{G} %l %{k}|%{W} %-w%{+u}%n %t%{-u}%+w"
defscrollback 10000
vbell off
deflogin on
defautonuke off

---

### Post by PandaGoat on 2009-07-14
Windows has Visual Studios which is probably the best IDE (some may argue), and  GNU/Linux has excellent terminal emulators, text editors, and programming tools.  I would say the latter provides a much better programming environment than any IDE can; the only downside is the learning curve, but it is worth it.

In conclusion, I would suggest you use a good programming editor like emacs (or vi I guess :mad:) and become very familiar with autotools and gdb.

---

### Post by JordyD on 2009-07-14
> **TheBuzzSaw said:**
> IDEs suck

Fixed.

*ducks*

---

### Post by TheBuzzSaw on 2009-07-14
> **JordyD said:**
> Fixed.

*ducks*
LOL! Touche...

...

*saws your legs off instead*

...

I like Code::Blocks because it is more of a smart text editor than a full blown IDE. It runs fast and doesn't get in the way.

---

### Post by Seed++ on 2009-07-14
I've been using Dev C++ for a long time now and it has not gave me any real problems.

---

### Post by rhchia on 2009-07-14
> **fr0d0 said:**
> Simle question: what size will be the best for system ext3 partition?
And how you organaze your partitions?:p

i'm about 1month old in ubuntu and still learning. i've somewhat read about partition on linux. this what i've got. u need about 2/3 partition.
1. root (/)
i've still have question over the size i should allocate.
2. swap
this is for the RAM thingy if i'm not wrong. normally the size allocated is 1.5 or 2 times your ram size.
3. home (/home)
if one day you decided to clean install or install another linux on your system, u can happily share this partition on either linux. 

regarding IDE/Editor, i've heard alot of them. there are...
Code::Block
Codelite
Vim/gVim
Eclipse
Netbeans

Currently i'm using Codelite to do C++ and gtkmm programming. I consider myself a beginner level so i don't think i will be comfortable with Vim.
My theory(for now)
Do you want to right click to copy a file or use "cp filename"?

---

### Post by Mirge on 2009-07-14
*cougH* [_Eclipse CDT rocks_]("http://www.eclipse.org/cdt/") *cougH*

:lolflag:

---

### Post by nvteighen on 2009-07-15
> **PandaGoat said:**
> Windows has Visual Studios which is probably the best IDE (some may argue), and  GNU/Linux has excellent terminal emulators, text editors, and programming tools.  I would say the latter provides a much better programming environment than any IDE can; the only downside is the learning curve, but it is worth it.

In conclusion, I would suggest you use a good programming editor like emacs (or vi I guess :mad:) and become very familiar with autotools and gdb.

Yup. By using your custom "toolkit", you can combine the tools at will... your programming environment will be effectively **yours** and not some "ideal environment" (no matter how good it is) created by the IDE's developers. Of course, chances are that the environment you like most is an IDE but to be sure that's what you like, you should try the "toolkit" solution first.

---

### Post by abhilashm86 on 2009-07-15
> **JordyD said:**
>  The only downside to Qt is that it looks really bad in a GNOME environment, so if you're using a GNOME environment, 
.
is it, when you download sdk and install Qt 4.5, it behaves well on Gnome, maybe kde most part is done using Qt, Qt looks are ok with Gnome and it is not as bad as kde's K3b burning tool, 
i really hated K3b looks on Gnome, which i deleted just one day after using it!!!

---

