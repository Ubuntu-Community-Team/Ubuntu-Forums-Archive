---
title: "Why use Vim or XEmacs?"
date: 2007-05-28
forum: Programming Talk
---

### Post by JetSirus on 2007-05-28
I always hear people saying that you should only use Vim or XEmacs for programming.  Why?  Both are HORRIBLE in the user friendliness department.  Is there something special I am missing?  From what I can tell after completing the tutorial for XEmacs it's basically an extremely bloated text editor that requires a degree to use.  Is it that once you get used to it, it's more productive?  I just don't understand the logic.  Fill me in.  

After rereading this post it may seem inflammatory, I really don't mean it to be.

---

### Post by bukwirm on 2007-05-28
> **JetSirus said:**
> Is it that once you get used to it, it's more productive?

Yes - although I prefer vim.

---

### Post by JetSirus on 2007-05-28
> **bukwirm said:**
> Yes - although I prefer vim.

Care to elaborate?

---

### Post by perce on 2007-05-28
XEmacs + x-symbols + kdi with inverse search are great to write in LaTeX. But in the end I guess every modern editor would do the job. And no, using XEmacs doesn't require a degree, unless you want to customize it heavily.

---

### Post by seamless on 2007-05-28
> **JetSirus said:**
> Care to elaborate?
Vim is designed to work completely with the keyboard. This has the advantage of never having to take the time to move your hand over to the mouse, move the mouse, click the menu and so on. The keyboard commands (once you have used them enough) become second nature and doing things like replacing, searching text and navigating a document becomes very quick.

There is also quite a lot it can do. Pretty much everything, spell check, multiple documents, code completion, syntax highlighting, automated building, configurable quick keys, auto indentation and code formating. Pretty much anything you could want when programming Vim can do. It's fully customizable and configurable to your liking. If you take the time you can make it work to your pleasing. It's much more than the archaic editor it appears.

Another good reason to use Vim is that (at least vi) it is on pretty much every *nix system you will encounter. Using Vim extensively to program will allow you to become failure with it in case you ever need to use it on a system where it is the only editor.

---

### Post by Mr. C. on 2007-05-28
Once you've seen an expert use vi/vim/emacs, you'll realize how powerful these editors are and how productive one can be.

But there is a heavy learning curve, which is only worthwhile if you'll be using them frequently and routinely.  Soon enough, you simply think what you want on the screen, and your fingers tap out the keystrokes on their own.

Their real power comes in their ability to interact so freely with any command line tool for providing input to an edit session.

MrC

---

### Post by DirtDawg on 2007-05-28
I also had this question until I got the Linux Cookbook from my local library. The author makes a strong case for using Vim. But to do so, he says, you first must know how to type. So I learned to type correctly (if not slowly), and now Vim makes way more sense (Nethack, too). Now I want to navigate with 'hjkl' on everything i do!

In addition, you can do things like "3dd" in command mode which erases 3 lines like magic. Easier for me than highlighting+backspace as my hands dont need to leave the keys.

That said, I use gvim because that way I have the option to use GUI if I want, which is often very nice, as my typing skillz are none too good yet.

One of the biggest turn-offs for me before was lack of syntax highlighting and auto indent. Linux Cookbook also told me about the .vimrc file, which never seems to come up in these conversations. It made [g]vim very nice indeed.

Also, consider giving [Cream]("http://cream.sourceforge.net/") a shot. If for no other reason then the beautiful syntax highlighting modes. It's in the repos.

---

### Post by perce on 2007-05-28
another reason for using text-based editors like vim (or in my case jed) is that you can use them efficiently in a remote connection. For example, I'm in Canada now, but my webpages are on a server in Italy, and I use jed if I need to modify some page. I could, in principle, use a GUI-based editor, but X forwarding across the ocean is unbearably slow.

---

### Post by nrs on 2007-05-29
*Emacs is an operating system with a text editor. 

If you don't plan on customizing it heavily I don't really see a point in using it or vim over any other editor. Most people that use it however have it refined to such a point that no other editor can come close to fitting their needs.

---

### Post by kevinlyfellow on 2007-05-29
Use whatever your most productive with, end of story.  Have you ever watched the Spongebob Squarepants episode where Squidward was trying to teach Spongebob how to be an artist?

---

### Post by DC@DR on 2007-05-29
> **kevinlyfellow said:**
> Use whatever your most productive with, end of story.
I strongly agree with this statement! :-)

---

### Post by rickardg on 2007-05-29
The main reason to use vim or emacs is IMHO not that they are customizable (as in changing keybindings and such) but that they are extendible. If you find yourself doing a repetitive task you can easily write a small function that automates it for you. 

Don't try to learn it all at once though, concentrate on learning to do simple text editing to begin with, both vim and emacs come with great tutorials (vimtutor and C-h t) and interactive help systems.

Since both of them have been around far a while you don't even have to learn to extend them yourself, there are heaps of snippets you can use at places like [EmacsWiki]("http://www.emacswiki.org") and [Vim online]("http://www.vim.org/").

In the long run it is well worth spending the time learning a 'real' text editor. My guess is that after a week you will be about twice as productive with something like notepad but after a year you will be more than twice as productive with emacs or vim than with notepad. There simply isn't much of a [learning curve ]("http://unix.rulez.org/~calver/pictures/curves.jpg") with the simple editors, you learn the key bindings and that's it, with vim or emacs you just keep learning (and increasing your productivity).

It does take some work though, in fact I had several false starts over a couple of years until [Steve Yegges Effective Emacs]("http://steve.yegge.googlepages.com/effective-emacs") post finally got me over the hump.

---

### Post by ankursethi on 2007-05-29
Most "old timers" who have used Linux/UNIX systems prefer Vim/Emacs because that's what they're used to. These two editors worked on all systems, supported a certain level of "multitasking" that the terminal could not provide and were probably the only two editors that were really worth looking at.

The productivity argument is farce. I cannot comprehend how hitting CTRL-X CTRL-W is more productive than hitting CTRL-S. The menus can be navigated using the ALT key, so you don't really have to use the mouse even with modern editors. Hell, I've used my computer without a mouse for a couple of days when my mouse had started malfunctioning, and I had absolutely no problems.

---

### Post by xtacocorex on 2007-05-29
> **JetSirus said:**
> I always hear people saying that you should only use Vim or XEmacs for programming.  Why?  Both are HORRIBLE in the user friendliness department.  Is there something special I am missing?  From what I can tell after completing the tutorial for XEmacs it's basically an extremely bloated text editor that requires a degree to use.  Is it that once you get used to it, it's more productive?  I just don't understand the logic.  Fill me in.  

After rereading this post it may seem inflammatory, I really don't mean it to be.
[joke]Why you may ask, well I think it's to keep the hardcore programmers more effective.  [/joke]

Let me pose a question, have you learned more from something more difficult or something easy?  If everything was easy, would you do it?  Learning curves are a fact of life.  Was it easy for you to switch to Linux after Windows?  Some people can't do that very well.  There was a learning curve when I started my job, going from wanting to design airplanes to laying out circuit boards.

I am a pretty hardcore VI user and yes there are times I'll open my code in Xcode on my Mac or Gedit, but mainly it's all terminal based for me because I think it's faster.  Why do I prefer it this way; it makes me feel at one with the code.  

You also used XEmacs, which is a GUI version of a very capable terminal based program.  I do credit you for trying, some people wouldn't have touched a terminal based editor with a ten foot pole. 

The beauty about life is that you can do whatever you want, so if you want a bloated IDE or something plain like Gedit, it's all you.  You won't have me telling you what to use because it's not my place to push ideals on you.

Hopefully I didn't go way off topic with this.

---

### Post by rickardg on 2007-05-29
> **ankursethi said:**
> 
The productivity argument is farce. I cannot comprehend how hitting CTRL-X CTRL-W is more productive than hitting CTRL-S. 

The keybindings are irrelevant to the productivity argument as long as you don't have to use the mouse, most decent editors let you change them to whatever you like anyway. 

What's great about emacs (and editors like vim or Textmate) is that you can make the save command automatically do other stuff with the files as well. E g you could have it upload all html files saved in a certain directory to your server, and check if the markup is valid in the process.

Personally I've long tried to keep a TODO file for my coding projects, but always failed because it broke my concentration to much to find the file, open it, type the todo item, save the file and return to where I was coding. I wrote a small elisp function that searches the current directory and its parents for a file named TODO, opens it, places the cursor at the end, optionally inserts the current selection, lets me type my todo item and returns me to where I was. So now I can go C-c t, type my todo item, C-c b and continue with what I was doing. For all practical purposes I've extended emacs with a simple todo list management feature since there is nothing that distinguishes my function from the built-in ones.

The above example might seem silly, but my point is that you  shouldn't have to do repetitive tasks yourself--that's what computers are for. As these small utility functions accumulate in your configuration file your productivity actually increases and you slowly mould your editor to suit your work style.

---

### Post by pmasiar on 2007-05-29
[http://www.softpanorama.org/Editors/vim.shtml](http://www.softpanorama.org/Editors/vim.shtml) - the Why and How of  "orthodox editors"

---

### Post by ankursethi on 2007-05-29
I can extend Scribes with Python plugins. I can even extend GEdit with plugins. There.

I don't think there's a clear winner in this debate. It's a matter of preference. You cannot with surety say whether pizza is better or a burger. To each his own, men.

---

### Post by Rogers on 2007-05-29
VI or VIM exists on every UNIX box.  So you can work on AIX/HP-UX/SCO/Linux/Solaris systems if you can use the simple Vi editor.  I never thought of VI as very user friendly--but it always works and is always there.

There is a lot to be said for reliability :D

---

### Post by treak007 on 2007-05-29
You will find that as you use vi more it becomes  second nature. Once you get used to all its commands ([http://tnerual.eriogerg.free.fr/vimqrc.html](http://tnerual.eriogerg.free.fr/vimqrc.html) thats a good resource to learn them), they become something you won't even think about and you will wish that every application used them. In other words, yeah it has a some what steep learning curve, but once you get used to it, its really productive, powerful and fast.

Also, knowing a terminal-based editor such as vi will make you much more comfortable next time your xserver won't start.

---

### Post by JetSirus on 2007-05-29
Wow, I am truly and completely shocked at how helpful, informative, and civil these responses are!  Thanks to everyone on your helpful and eye opening opinions!  I will defiantly be giving VIM a more detailed assessment tonight.  I have known for quite a time that VIM was available on almost every -NIX system, but had never been able to get much use out of it.  It's interface was as daunting and meaningless as trying to read tea leaves for a bit of crucial information.  It's something I should at least know how to use though.

Once more I thank everyone for their assistance and input on the topic!

---

### Post by pmasiar on 2007-05-29
> **JetSirus said:**
> Wow, I am truly and completely shocked at how helpful, informative, and civil these responses are! 

Nah, for good flamewar you would have to promote VisualStudio :-) 

Many people say Cream is user-friendly vim. I use midnight commander for everytying (including char-based crappy editor) so I was avoiding the inevitable so far.

One huge plus what vim has is IMHO: you can create your own macros in python (and not in lisp as in emacs). That is killer feature for me.

---

