---
title: "SWI Prolog: how to change working directory at startup?"
date: 2011-04-18
forum: Programming Talk
---

### Post by amanchesterman on 2011-04-18
I'm learning to program in Prolog (just for personal interest, on my laptop at home) and have installed SWI-Prolog since that is easily available for Ubuntu. It runs with no problem and my  programs generally work OK, but there is one niggle that annoys me and I hope someone here can help.

By default, SWI-Prolog expects my Prolog programs to be in my home directory, whereas in fact I keep them in a sub-directory called 'Programming'. Once Prolog has started, I can manually change the working directory so that it finds the files for the rest of the session, but it would be neat if I could get it to do that automatically when it starts.

I have created an entry for Prolog in the Applications menu (I am using Ubuntu 10.10) which simply invokes 'swipl' in the Terminal. Can I change that somehow so that it will do what I want? I have looked in the SWI-Prolog manual, but honestly I don't really understand most of it: what I need is simple guidance for a beginner.

Thanks
John

---

### Post by ve4cib on 2011-04-18
You can create an initialization file for prolog.  By default it's $HOME/.plrc, but the -F <file> flag lets you change that.

If you don't have a .plrc file yet, create one in your home directory, and enter the command you're using to change the directory.  It's been years since I've touched prolog, so I don't even remember what that command is.

As far as I can recall though, the initialization file is just a prolog script that gets executed every time you start up the interpreter.

---

### Post by amanchesterman on 2011-04-18
Thanks for your quick and helpful reply.

How should I name the initialization file? Is it something like 'user.plrc'? Or is '.plrc' what the file is called?

John

---

### Post by ve4cib on 2011-04-18
The file is simply called ".plrc" and should be located in your home directory.  It's like the Bash configuration file, .bashrc, or an X initialization script, .bashrc.

---

