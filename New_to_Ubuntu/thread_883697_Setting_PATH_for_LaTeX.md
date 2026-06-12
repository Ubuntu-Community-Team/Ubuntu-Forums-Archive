---
title: "Setting PATH for LaTeX"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by Ramekin on 2008-08-08
Hello there, I've just installed Ubuntu 8.04 - the Hardy Heron and then on Top LaTeX via LiveTex 2007 alongside the documentation in the terminal.

I am an absolute beginner with Ubuntu; this is my second day with it. Have mercy on me! :KS

After installation, LaTex prompts me to set the PATH environment variables:

   >  The syntax for setting the environment variables, and the initialization file to put them in,
depends on the shell you use. If you use a Bourne-compatible shell (sh, bash, ksh, et al.), put the
following into your $HOME/.profile file:
PATH=/mnt/cdrom/bin/archname:$PATH; export PATH
TEXMFSYSVAR=/opt/texlive2007/texmf-var; export TEXMFSYSVAR
 
I blush at the level of knowledge I am at, but how can I accomplish this step? What is the $HOME/.profile file? How do I edit it? I've browsed the net for the past 8 hours and couldn't find anyone who was as much beginner as I am. 

I'd be very, very grateful for a short line of code to enter into the terminal or elsewhere to edit the profile. Please be aware that there is no background knowledge on Ubuntu on my side. Thanks a lot!

---

### Post by shr2004 on 2008-08-08
Here is a quick help from another noob. 
Have you checked this thread:

[http://ubuntuforums.org/showthread.php?t=141934&highlight=Kile](http://ubuntuforums.org/showthread.php?t=141934&highlight=Kile)

It talks about how to install Texlive with Kile.....it is better to check whether your Latex installation is running.
From terminal (Application>Accessories>Terminal) type: 

tex --version 

then you will get some information of the isntalled latex, that means the installation is working. So far I have not done anything extra that you mentioned in your post. 
If you have any personal style files that you want to use, then put them in a directory (folder), named: "texmf" (without quote), in you home directory. Latex will find it.
And again check that tutorial, its very helpful

Good luck

---

### Post by waspbr on 2008-08-08
Ramekin, I am a latex hater, I don't like it and it doesn't like me, but I still have to use it every once in a while.

the easiest way to install the bugger that I have found was to simply go to synaptic and search for winefish, it is a very nice latex editor which already is in the repositories. Once you install that in synaptic, it also installs all the other dependencies, namely, latex itself. 

So if you really want to use latex 2007 manually, well, go for it. BUT I would much rather just use synaptic to do that. 

And what is the deal with the pronunciation (latec)...

yes I hate the damn thing, I would much rather use Open Office

---

### Post by Ramekin on 2008-08-08
Wee, those were two fast answers. Thanks to the link to the excellent how-to, I've got it installed. Just put Lyx on top of it. 

Thanks again for your time!

:popcorn:

---

