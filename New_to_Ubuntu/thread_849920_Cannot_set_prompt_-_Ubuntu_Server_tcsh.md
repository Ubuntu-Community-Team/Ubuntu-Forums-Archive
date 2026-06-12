---
title: "Cannot set prompt - Ubuntu Server tcsh"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by protogenesis on 2008-07-05
Recently installed the newest Ubuntu server edition.  Strange thing, I cannot set a custom prompt no matter what shell I use.  Currently running tcsh, no dice.  Tried the standard setenv approach, this didn't work.  Spent time searching the forums, other sites, using setenv, set.  Nothing seems to change the standard prompt which is, of course, my hostname.

Did I miss something about how to set prompts in Linux?  Was there a class I forgot to attend?  'setenv' works on my other linux boxes, but not the server side.  Maybe it's my breath?

---

### Post by bab1 on 2008-07-05
Are you using .tcshrc to set the prompt?  That file should be in your home directory.  Same with bash.  I use bash and set the prompt I want in .bashrc.

Google tcshrc or bashrc for more  info

---

### Post by protogenesis on 2008-07-07
Yep!  Setting the .tcshrc in my $HOME as always.  I try setting in in there, then from the command line, and nothing.  Always stays the same (which is hostname:{pwd})  

Also tried this in bash - ditto.

Am thinking Linux is starting to hate me?

---

