---
title: "vim or emacs? (i know that this is a recurring  issue, but now it is mine)."
date: 2011-12-22
forum: Recurring Discussions
---

### Post by F.G. on 2011-12-22
hi folkes,

so, until recently i did all my coding in gedit (or, prior to that kate) or netbeans, or eclipse. OR in windows in notepad++. 

however, i recently started to work in a company where i strongly believe that i will be laughed at, (or at least thuororghly mocked). ((out of house and home), most other people seem to use vi) for using something like gedit or nautilus ("tab" or autocomplete, on the command line would be preferable). i now have a few days to learn a new skill (before i will be back at the grind stone).

i know that there is a long standing split between the emacs folk and the vim enthusiasts. still, i have about five days. i tried vim yesterday and it really slowed me down (although this may just be a learning curve). i tried emacs a long time ago and it didn't seem to stick.

so, my question is WHY?? and which one??

can any useres of either editor help me decide which to learn???

---

### Post by doorknob60 on 2011-12-23
Inb4 recurring.

I use vim, once you leanr at least some of the more basic commands (not too hard, try vimtutor), it's pretty nice to use. Is it better than the GUI editors? Well, not necessarily, it's all up to user preference, but inn my opinion it's not worse either. It depends on what you prefer, and GUI and CLI editors both have their pros and cons, and both are good in my opinion, just use what you like best. Maybe use something like Gvim which is a GTK interface for vim.

---

### Post by matthew.ball on 2011-12-23
I don't really think you could go wrong with emacs (or vim for that matter, though I don't have any experience with vim).

As far as emacs goes, just spend 5 minutes (give or take?) going through the initial tutorial. It makes a bit more sense after that.

The "vanilla" emacs is pretty bare-bones, while there is a lot of functionality in there, most of it is hidden. So, you should look at some .emacs files (probably [this]("https://github.com/technomancy/emacs-starter-kit")) and find out how to get some things working for you.

I'm sure the same applies to vim, but as I said, I just have no experience with it.

---

### Post by ninjaaron on 2011-12-23
There are the traditional advantages and actual advantages today.

In the past, vim was a much smaller, lighter program, and emacs had more functionality because it is infinitely extensible with the elisp programming language.  However, vi has historically been a core Unix utility, and as such, it works well with a Unix system environment in a way that took some extra doing in emacs.

Today, Vim has more than one million lines of code, and is little "smaller" or "lighter" than emacs.  In addition, vim is extensible with vimscript, which is a pain to learn but it gets the job done.  Furthermore, Vim apparently supports python plugins now (don't know too much about that, but I read it somewhere recently).

Basically, emacs probably still has a very slight edge in functionality, and vim is still probably a tiny bit smoother in talking to the system (and does seem to use less RAM than emacs, thought they are both minuscule in comparison to most gui programs).  They both have tab completion and advanced tools for helping programmers, and both have syntax files for almost every language imaginable.  They both also have tools for writers like spell check, thesaurus, a multitude of wrapping options and more.

----------------------------------------

Probably the most important difference today is the key-bindings.  Most gui programs for manipulating text, including Open Office and Gedit, us key-bindings borrowed from Windows (for obvious reasons).  Emacs and vim are older than Windows, and they retain their legacy bindings.  Key-bindings in both can be redefined, but I can tell you now that it would be easier to set up emacs with windows bindings than vim.

This is because vim is a modal text editor (though emacs has plugins for vim modes, "evil" and "vile").  Emacs, like windows, relies heavily on modifier keys for key-bindings.  In vim, many commands are just single key strokes, or a series of single keys without any modifiers (but also sometimes with modifiers).  This is because vim has separate modes for entering text and entering commands (and for some other tasks), and those modes interpret keystrokes differently.

This has advantages and disadvantages.  The disadvantage is that you have to learn an entirely new way of working with a text editor.  The advantage is that there are many things you can do very, very quickly which are not possible without modes.  For example, in command mode, you could type `5G6wd3w`, which would jump to the fifth line and move six words in, and delete the next three words. It's a bit strange at first, but it becomes very fast once you get the hang of it.

vim's command system is said to be more ergonomic because the hands remain on home-row more, and are required to do less stretching, which can cause RIS.  Vim people had been saying this for a long time, when Richard Stallman, the creator of emacs, got RIS and lost the ability to type.  I'm sure some vim users have gotten RIS as well, but the irony was still delicious.  Of course, it's terrible that Stallman was injured.

---------------------------------

Emacs has tended to be more popular cross-platform with programmers.  This is due in part to the fact that it uses a more standard command system, rather than a modal system, and also due to the fact that it has always been infinitely customizable through elisp (though vim's python extensibility should mitigate this).  Stallman and Torvalds, the two great patron saints of Linux, are both emacs users.

On the other hand, vim arguably has a more devoted following among hardcore *nix hackers and sys-admin types.  This is partially because vi is the legacy Unix text editor which embraces Unix philosophy, and though vim has grown a lot over the years, it still arguably is more focused on "doing one thing well" than emacs, and still plays extremely well with a *nix system.  In fact, you will be hard-pressed to find any *nix system that does not have some version of vi or vim installed by default.  There is one other advantage to being a legacy Unix app, and that is the fact that vi keybindings are effectively legacy Unix bindings.  Many, many *nix terminal apps use vi bindings, as well as quite a few gui apps (like banshee, for example), such as / and ? to search rather that ctrl+f.  These are great to know for any Linux or BSD user.  Almost all of the programs I use regularly utilize a vi-based system of bindings.  As mentioned above, emacs can also be made to work with this system of bindings.

The steeper learning curve also gives it something of an elitist appeal, and partially for this reason, and partially because it's fast as heck, it tends to be rather popular with hackers.

------------------------------

to summarize:

Emacs
-----
Pros:
infinitely customizable (maybe vim is now too)
uses a 'normal' (aka: windows-like) binding system.

Cons:
Less ergonomic by default, reported to cause RIS (this can be fixed)

Vim
---
Pros:
a pillar of *nix culture
very ergonomic by default

Cons:
steep learning curve.

---------------------------------


I use vim in an xterm for the Unix-cred and the speed.  I seriously think that gedit is also a great editor for something too though, and I think you should use whatever editor helps you to be the most productive.  Of course, there is something to be said about the advantages maintaining credibility with your peers, even if it is by rather superficial means.

Should you decide to use vim, I would also suggest installing a firefox plugin called Pentadactyl, which makes firefox 100% keyboard accessible via vim bindings.  This will get you over the hump very quickly.

---

### Post by JDShu on 2011-12-23
Flip a coin, heads - vim, tails - emacs (even better, [flip a fair coin]("http://carlos.bueno.org/2011/10/fair-coin.html") ) then stick to it. It's really a lifelong thing either way. You'll continue to learn new tricks as your needs increase. I started using emacs 5 years ago, and I still know very little about editing the .emacs file and what scripts might be available to make my life easier. I believe the vim experience is similar.

All that said, emacs is better than vim.

---

### Post by ninjaaron on 2011-12-23
> **JDShu said:**
> emacs is better than vim.

no

---

### Post by Elfy on 2011-12-23
Thread takes an unsurprising move to Recurring.

---

### Post by Frak on 2011-12-23
> **forestpiskie said:**
> Thread takes an unsurprising move to Recurring.
It was Super Effective!

I think the largest difference between Emacs and Vim is the method of navigation and mode traversal. Emacs is all editing all the time, while Vim is focused around different modes, such as selection, navigation, editing, macros, etc. Emacs also use modes, but in a different way. They're abstractions between scripting, programming, markup, etc.

Anywho, Vim is better than Emacs.

---

### Post by F.G. on 2011-12-23
thankyou ninjaaron for your interesting and comprehensive response, i like your historical keybinding reasoning. (and thankyou everyone else).

i guess i'll probably do a short tutorial in both and then decide (although i'm currently inclined towards vim as i've been learning bits of it already).  when i say vim, i do actually mean gvim, with the gtk interface and everything, from the command line i generally use nano and i'm pretty happy with that (mainly because it has a cheat sheet at the bottom, so i don't wind up wondering "how the hell do i exit vi??")...  i have heard the argument that nearly all *nix machines have vi on, but then again nearly all the linux distros i've used recently seem to have nano on. i look forward to the next few days learning a bit of both emacs and vim.  i'm not at all surprised to see a bit of "x is better than y" smacktalk, and would expect no less from dyed in the wool users. no alternative suggestions though? i guess these are the two real contenders then.

it seems to me that a lot of Mac users seem to use emacs? i wonder if this is a general thing, or just my incidental experience?

---

### Post by BHEJU on 2011-12-23
VIM baby VIM...

---

### Post by Frak on 2011-12-23
> **F.G. said:**
> it seems to me that a lot of Mac users seem to use emacs? i wonder if this is a general thing, or just my incidental experience?

I tend to see the opposite, in fact, there's a lot of development around making popular Mac text editors (TextMate, Cappuccino, Coda, etc.) act like vi.

But, I did want to add that I like to use vim because I don't feel like I'm loading up a psuedo-windowed app in the terminal. Where Emacs provides several menus at the top with a code view and contextual information at the bottom, Vim uses a "code and mode" scheme. You see your code and the mode at the bottom, taking up a mere one line.

I work with a team at my university for academic research. Our lab consists of thin clients connected to a large server that handles our X Sessions and other shared resources. Our monitors are fairly small (800x600) and leaving that extra screen estate is helpful, besides just looking clean.

The commands are clean and can be strung. Modifier keys aren't as emphasized as they are in emacs, which is helpful since it keeps us working fluidly. A few of us find it difficult to move our hands in such a way to hit Ctrl and another key, especially on the left side of the keyboard, without lifting our hands. :wq is, IMHO, more fluid than Ctrl+x Ctrl-c. I can also think about what I'm doing before I finish, seeing what is about to happen. As a plus, you can use Esc as a universal "GET ME OUTTA HERE!" key. This isn't why Vim is *superior*, but why I find Vim to be *better* and more *suitable*.

I thought it might help to hear a use-case.

---

### Post by BrokenKingpin on 2011-12-23
I prefer VI, mainly because that is what I used in college. I only really use it on servers with no UI though. For most of my development I now use MonoDevelop, Eclipse, or Visual Studio (if I am in Windows).

If you get mocked for the text editor that you use, then I would consider fining a different job (if possible), as that is just ridiculous. I have worked as a Software Engineer for a few different companies, and for the ones that let you use whatever editor you want I have never been mocked for using a graphical tool like Eclipse.

The reality is, tools like Eclipse, Visual Studio, and MonoDevelop just makes your life easier as it helps manage large projects, and have a lot of really useful tools built in. I work with a few develops that use only VI, and they don't look down on people that use VS or any other editor.

---

### Post by cortman on 2011-12-23
I'll throw my voice in for emacs.

I've learned to use both, and I currently do pretty much ALL text related tasks with emacs, including editing system files, programming java/python/bash scripting, writing letters, taking notes, etc. Spend some time with the offical [manual]("http://www.gnu.org/software/emacs/manual/emacs.pdf") and once you have some basic concepts, keep [this chart]("http://refcards.com/docs/gildeas/gnu-emacs/emacs-refcard-a4.pdf") handy and you'll be amazed how fast and easy it is to use. The shortcuts and commands are super fast and once you learn them they become second nature (I catch myself using emacs command shortcuts in MS Word, Excel, etc. at work by mistake). In summary I have found it to be extremely powerful and very fast, albeit with a little learning.

Vim on the other hand I never got used to. The whole modal thing and various bizarre commands I found to be rather unintuitive. But you may find different.

If you want to use a power user text editor, go emacs! You won't regret the time spent learning it.

---

### Post by cgroza on 2011-12-23
I use emacs.  I pretty much spend all my text related time in it. I use it for IRC, programming, shell.  The editing tricks are awesome but what really impressed me is it's documentation modes. You almost never have to leave emacs for checking some documentation if you have it on your filesystem. A worst case scenario is to switch to the browser to consult some API.
I don't think vim has any decent counterpart for that.

That said, emacs is better for me.

---

