---
title: "Why does nohup work on some executables and not others?"
date: 2013-06-14
forum: New to Ubuntu
---

### Post by jps2012 on 2013-06-14
It's a pragmatic question--not just a rhetorical one. I've got two applications I'm working with in /usr/bin. One is scrivener. The other (which I just downloaded) is vim. 

If I invoke "nohup scrivener" the application launches. 

If I invoke "nohup vim" the application doesn't launch. 

"scrivener" is a shell script (application/x-shellscript)

"vim" in usr/bin is a link to executable (application/x-executable)

So it looks like I'm trying to launch from a symbolic link, and I guess I can't do that. 

If I invoke "type -a vim" I get only the following: "/usr/bin/vim" 

Does that mean there's a symbolic link, but no executable? Does "type -a" respond with EVERY instance of vim on the harddrive? (Basically I'm trying to sort out why the Software Installer would (it seems) download a sym link but not an executable for vim. Even better would be understanding how to get vim to launch from Terminal.)

---

### Post by steeldriver on 2013-06-14
I don't think it's anything to do with symbolic links - 'vim' is a command line program, it needs its parent terminal's standard input in order to do anything and since nohup detaches the standard input stream it just terminates (nohup also detaches the terminal's standard output - although by default it sends it to a file called 'nohup.out' instead so that's not fatal)

If you look at the nohup.out file after trying to 'nohup vim' you should see

```

$ cat nohup.out 
Vim: Warning: Output is not to a terminal
Vim: Warning: Input is not from a terminal
Vim: Error reading input, exiting...
Vim: Finished.

```

I don't know anything about scrivener but I assume it's a GUI program? in which case it gets its input from X and doesn't need the terminal's stdin so can safely be detached

---

### Post by jps2012 on 2013-06-14
Steeldriver: I'm afraid I'm too new to Ubuntu to understand much of that, but I'm going to do some reading about the terms in your message. I'd downloaded vim today and was trying to lauch it. I thought I'd downloaded a GUI version of vim. 

Scrivener IS a GUI, and lauches fine (it's a beta version for Linux; somewhat downgraded--in the sense of functionality--from the full version for Windows and Mac). I learned a lot of command line invocations today while installing the Deb file (with your help, and that of a few others). 

Technically, the vim I downloaded is called vi Improved Enhanced Version (downloaded from the Software Center). I obviously didn't pay enough attention, because NOW I see (as you noted) that it's run from a Terminal. 

Here's what I was really after with the vim download: I wanted to avoid learning a vi (non-GUI) editing system, because I don't think I'm going to be doing much scripting. But I did want to make SOME scripts. I'm not even sure I can save scripts via one of the GUI editors. I have Text Editor, JuffEd Text Editor, JEdit and NEdit. 

Are those OK to use for writing scripts?

---

### Post by steeldriver on 2013-06-15
Yes you should be able to use absolutely any text editor for scripting - if you want a GUI version of vim you would need to install that specifically (e.g. vim-gnome or vim-gtk) however aside from the GUI aspect the actual text editing would still use the vi-style 'modal' behavior which will likely confuse the hell out of you at first - unless it's something you specifically want to learn, I'd suggest sticking with the editor(s) that you're comfortable with

---

