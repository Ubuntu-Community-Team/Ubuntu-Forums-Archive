---
title: "Best IDE for c and c++ for a beginner"
date: 2016-09-21
forum: Programming Talk
---

### Post by deepakdeshp on 2016-09-21
Hello,

I will be learning c python and c++ . Kindly suggest a good programming IDE for Ubuntu 16.04.
Are there any good books tutorials on c and c++ for Linux Ubuntu?

TIA

---

### Post by TheFu on 2016-09-21
Linux is the IDE.  This is the standard way to learn so important details aren't hidden inside some huge IDE.
 [https://sanctum.geek.nz/arabesque/unix-as-ide-introduction/](https://sanctum.geek.nz/arabesque/unix-as-ide-introduction/)

I still program this way 25+ yrs later.

---

### Post by deepakdeshp on 2016-09-22
That is awesome , that will make you explore the Linux tools and extend your Linux knowledge. Thank you.

---

### Post by TheFu on 2016-09-22
> **deepakdeshp said:**
> That is awesome , that will make you explore the Linux tools and extend your Linux knowledge. Thank you.

Start with Python, at least for the first 3-6 months. Then learn C.  [http://blog.jdpfu.com/2011/10/19/how-to-learn-to-program](http://blog.jdpfu.com/2011/10/19/how-to-learn-to-program)

---

### Post by deepakdeshp on 2016-09-24
Thank you for your time and advise.

---

### Post by TheFu on 2016-09-24
> **deepakdeshp said:**
> Thank you for your time and advise.

I'm kinda surprised that others didn't chime in with their favorite solutions too.  Since they didn't, I'll add some popular ones that I've heard about, but may not use myself or tried them many years ago.

* emacs - in the old days, before X/Windows, emacs was the windowing tool of choice. I suspect there isn't anything you'd do that emacs can't be made to support.  It definitely does C/C++, debugging, help lookup, email, web browsing, ctags, ftp, info-browsing, and it is highly scriptable (lisp-based).

* Geany - very lite IDE.  I've used it for Perl, bash, and a little C. You'll need to understand about compilers and debuggers to set it up yourself.

* Netbeans - huge, bloated, Java-based tool.  Think it is related to Eclipse in some way.

* Eclipse - this is the IDE that most Java developers use. It is the most bloated software that I know in the world. Worst than iTunes or Outlook. I usually tell people if they don't have a Core i7 CPU and 12G of RAM, forget it.  When I looked into Android programming around 2010, eclipse was the setup Google recommended.

* Code::Blocks - People show up here and ask about this all the time. Out of curiosity, I watched a youtube video about it and left more confused than understanding.  If you've read my background, that should say something about this method of learning C. 

To be completely fair, I learned C using Borland's Turbo C IDE.  It was an all-in-one setup that ran on MS-Dos.  A few yrs later, I learned C++ using Borland's Turbo C++ IDE, then moved the Borland's professional C++ compiler for DOS, then OS/2, then Window (16-bit and 32-bit), then learned C++ stuff on MVS, Ultrix, AIX, SunOS, Solaris, HP-UX, Irix, OSF/1, Digital Unix, and a few other platforms.  At the time, having a 32-bit OS was a big deal because it made live easier with 4G of RAM that could be accessed directly!  Basically, all 32-bit Unix-like platforms worked the same.  Use the platform compiler (or gcc), use gdb for debugging, and use gmake so your makefiles are cross platform.  These days, people seem to have switched to using cmake, but all the other stuff is about the same for C programming.  Borland is out of business, but I think the turbo-line of compilers will work under a DosBox environment - should be blazingly fast.  The entire env fit on a single 1.44MB floppy, including libraries, help files, examples.  

Oh and I used MSVC++ for about 8 yrs professionally. MSFT made the best development tools for Windows, if that is an interest for you. The hard part about using MSFT development tools was they suck in Windows-only extensions, so it is very hard to make a cross-platform program if you start on Windows as the first platform. My info on this is really old, so perhaps it has changed?  Last time I saw anything about it, was when it got out that MSFT's linker was adding spyware that phoned home to MSFT automatically in every program built. They call it something ... telemetry - yeah, that's their term.  [https://www.reddit.com/r/cpp/comments/4ibauu/visual_studio_adding_telemetry_function_calls_to/](https://www.reddit.com/r/cpp/comments/4ibauu/visual_studio_adding_telemetry_function_calls_to/) ... looks like their Dev manager is saying the right things - sorry they did it - stuff.

Anyways - there must be 20 other IDEs that people love. Hopefully they will chime in.

My favorite IDE on Unix platforms is still:
* 4 xterms
* vim - running in 1 xterm - gotta love those buffers and macros. If you've never seen vim being used by an expert, you have no idea how powerful it is. 
** [https://vi.stackexchange.com/questions/2046/how-can-i-integrate-gdb-with-vim](https://vi.stackexchange.com/questions/2046/how-can-i-integrate-gdb-with-vim) 
** [http://vim.wikia.com/wiki/Use_Vim_like_an_IDE](http://vim.wikia.com/wiki/Use_Vim_like_an_IDE)
* bash/make - running in another xterm (!!<enter> over and over)
* gdb - running in another xterm (sometimes I used xxgdb) - really need to learn to use the integrated solution 
* manpage lookups / ctags - running in another xterm.

My mouse is set "focus follows mouse" - a slight push of the mouse, no clicking, and the other window gets focus. Another nudge, focus moves. It is easy to understand, but if you've always used click to focus, could take some time to get used too. Also, if you are on Windows still, there is a program called x-mouse which does the same thing, but Windows seems to get confused about it all the time and loses the expected focus.

---

### Post by deepakdeshp on 2016-09-25
Thank you for your invaluable input.So many choices and such grand experience!

---

