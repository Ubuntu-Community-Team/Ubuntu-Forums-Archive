---
title: "Emacs vs Vi"
date: 2010-07-16
forum: Recurring Discussions
---

### Post by NMFTM on 2010-07-16
I'm going to school to learn about network administration and am thinking that maybe it's time to move beyond using Nano on Linux and OSX and Notepad on Windows.
 
I've done a little programming and am definently not a fan. Supposidly Emacs Lisp is easy to learn. But I'm sure there are enough addons/modules avalible that I won't need to use it.
 
Unless I step into a time machine and go back at least 20 years I don't see why the fact that Emacs is bigger or takes longer to load is really a reason not to use it in an age where computers have gigabytes of RAM and multicore processors.
 
I wish to efficiently create and edit Bash scripts.
 
I don't mind the idea of having to hold down shortcut keys to do things.
 
I've read that in Emacs you can customize anything. I sort of like the idea of being able to use WASD to navigate through text files. Of course, I'd have to use a shortcut key.
 
So, what do you guys think?

---

### Post by RiceMonster on 2010-07-16
Vimacs

---

### Post by Dustin2128 on 2010-07-16
emacs is a really great text editor, especially for coding. I'd highly recommend it. Its fairly easy to learn, but more advanced than nano (read: harder), and it is fairly light compared to most text editors today.

---

### Post by cariboo on 2010-07-16
I hope you realized that before you created this thread, it is a recurring discussion. Moved.

---

### Post by &#32 Greg on 2010-07-16
I would love to tell you Emacs all the way. It's a fantastic way of life; I highly recommend it. If it sounds like it appeals to you, go jump on it.

Regardless, you're talking about bash scripting. Both vim and Emacs will do a stellar job at it. Once you start talking about Common Lisp and LaTeX, SLIME and AucTeX become must-haves, but bash can really go either way.

---

### Post by prodigy_ on 2010-07-16
> **NMFTM said:**
> it's time to move beyond using Nano on Linux and OSX and Notepad on Windows
Gedit and Notepad++. 'nuff said.

---

### Post by Tibuda on 2010-07-16
> **RiceMonster said:**
> Vimacs

This.

Alt+X term <ENTER> vim <ENTER>

---

### Post by juancarlospaco on 2010-07-16
**ED**

*/thread*

---

### Post by jpkotta on 2010-07-17
> **NMFTM said:**
> 
I've read that in Emacs you can customize anything. I sort of like the idea of being able to use WASD to navigate through text files. Of course, I'd have to use a shortcut key.

[http://www.emacswiki.org/emacs/ErgoMovementMode](http://www.emacswiki.org/emacs/ErgoMovementMode)

You can of course make it use wasd instead.

---

### Post by yaaarrrgg on 2010-07-17
I'd recommend vim instead of the classic vi.   You get more features like column-wise editing.  That's a separate install package and will replace vi.

---

### Post by NMFTM on 2010-07-17
> **cariboo907 said:**
> I hope you realized that before you created  this thread, it is a recurring discussion. Moved.
  Yeah, it's been a recurring discussion for several decades. If regular  users could post topics directly in Recurring Discussions I would have  done that.
 > **prodigy_ said:**
> Gedit and Notepad++. 'nuff said.
 Yeah, but those are GUI editors and I'd rather get in the habit of using  the CLI as much as possible. When I get out in the real world of network administration I will probably have to work on systems without a GUI.
> **yaaarrrgg said:**
> I'd recommend vim instead of the classic vi.   You get more features like column-wise editing.  That's a separate install package and will replace vi.
When I said Vi an Emacs I was just talking about the general families of editors. Vim being the most popular implementation of Vi and Gnu Emacs being the most popular implementation of Emacs.

---

### Post by MattBD on 2010-07-18
I'm a huge fan of Vim. It may have a steep learning curve, but once you get used to it you can work very efficiently indeed, and vimtutor is an excellent way to get started.

One thing worth bearing in mind is that Vim or another vi clone is almost always present on any Unix-like operating system so if you can use it you can do so on virtually any machine. Emacs, while still often present, is somewhat less likely to be available. If you're looking into a career in systems administration, it may therefore be a good idea to have at least a passing familiarity with vi even if you use Emacs most of the time.

---

### Post by NMFTM on 2010-07-19
> **MattBD said:**
> One thing worth bearing in mind is that Vim or another vi clone is almost always present on any Unix-like operating system so if you can use it you can do so on virtually any machine. Emacs, while still often present, is somewhat less likely to be available. If you're looking into a career in systems administration, it may therefore be a good idea to have at least a passing familiarity with vi even if you use Emacs most of the time.
That's something I've taken into consideration. But, the same argument could be made against using scripting or editing your bashrc file. Or using/modifying any software that's non standard. I find it odd that Vi editors are more prevalent than Emacs on Linux when Emacs is the flagship editor of the Gnu Project and it's founder.

A more accurate thread title would have probably been something like "I want to learn Emacs, someone talk me out of it".

---

### Post by MattBD on 2010-07-19
> **NMFTM said:**
> I find it odd that Vi editors are more prevalent than Emacs on Linux when Emacs is the flagship editor of the Gnu Project and it's founder.

I believe it's due to POSIX compliance - to be fully compliant with the POSIX standard an operating system has to have vi or a clone of it, while Emacs is optional. In the case of Ubuntu, I understand it's getting harder to fit everything they need in one CD, and Ubuntu has a minimal philosophy with there generally only being one of everything, so it makes sense to ship it with Vim, not Emacs, especially since Vim's the lighter of the two. Other Linux distros that come on DVD-sized images often ship with both - I also use Slackware a little and that ships with both. Mac OS X also includes command-line versions of both Vim and Emacs.

Personally I'm a little reluctant to try Emacs as I've had RSI in the past and Emacs is known to exacerbate that, but I would like to learn to use it properly at some point. However, I wholeheartedly recommend Vim as it's always worked extremely well for me - I've used it for config files, marking up HTML and CSS, and coding in JavaScript, Python, C and more recently Perl.

---

### Post by NMFTM on 2010-07-25
I just found a neat extension called [Firemacs]("https://addons.mozilla.org/en-US/firefox/addon/4141/") that allows Emacs like key bindings in Firefox. This should help with my learning of Emacs (as well as allow me to write posts more efficiently) since I spend much more time browsing the web than I do editing text files.

The only thing I don't get is why k / j scroll up or down respectively while in Gnu Emacs they just insert the letters k, and j and C-p / C-n do the same things. Anyone know?

---

### Post by yaaarrrgg on 2010-07-25
> **NMFTM said:**
> I just found a neat extension called [Firemacs]("https://addons.mozilla.org/en-US/firefox/addon/4141/") that allows Emacs like key bindings in Firefox. This should help with my learning of Emacs (as well as allow me to write posts more efficiently) since I spend much more time browsing the web than I do editing text files.

The only thing I don't get is why k / j scroll up or down respectively while in Gnu Emacs they just insert the letters k, and j and C-p / C-n do the same things. Anyone know?

If they used k and j for scrolling, how would one type the letters k and j?  vi can reuse the letters k and j for both input and navigation, since it's based more on modes, rather than using control/meta keys.  Of course, I suppose it could be done in emacs, but you'd need a "navigation mode" and an "input mode."

---

### Post by NMFTM on 2010-07-26
> **yaaarrrgg said:**
> **If they used k and j for scrolling, how would one type the letters k and j?** vi can reuse the letters k and j for both input and navigation, since it's based more on modes, rather than using control/meta keys. Of course, I suppose it could be done in emacs, but you'd need a "navigation mode" and an "input mode."
Exactly, to be sure I tried C, M, and shift in conjunction with k and j in Emacs but it ddn't scroll like the extension did. I'll have to check further into it once I get home. So, I don't know why an Emacs addon would have keys (especially input keys) that don't actually perform the same function in real Emacs.

---

