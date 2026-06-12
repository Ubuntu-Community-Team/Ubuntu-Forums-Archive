---
title: "Bash or zsh?"
date: 2014-11-28
forum: Programming Talk
---

### Post by flaymond on 2014-11-28
hello, I see that zsh is more popular than Bash, why ? Is it powerful than Bash? Does syntax I/O in zsh in similar like in Bash? Also, it is possible that someday, Ubuntu devs will make zsh as default terminal shell?

---

### Post by tgalati4 on 2014-11-28
Don't know about making it default, but there are a lot of subtle differences:

[http://zsh.sourceforge.net/FAQ/zshfaq02.html](http://zsh.sourceforge.net/FAQ/zshfaq02.html)

[http://apple.stackexchange.com/questions/7657/bash-or-zsh-whats-the-difference-why-use-one-or-the-other](http://apple.stackexchange.com/questions/7657/bash-or-zsh-whats-the-difference-why-use-one-or-the-other)

[http://www.slideshare.net/jaguardesignstudio/why-zsh-is-cooler-than-your-shell-16194692](http://www.slideshare.net/jaguardesignstudio/why-zsh-is-cooler-than-your-shell-16194692)

If you want your scripts to work across a lot of different platforms stick to *sh* or *bash*.  If you like or need the new features in *zsh*, then use that.

---

### Post by Sasha_Aderolop on 2014-11-29
I'm just wondering which shell you guys prefer and why. I have been playing round with zsh and I enjoy using it because I think it has better command completion compared to bash.

---

### Post by ofnuts on 2014-11-30
I use bash. Looking at the feature list in the zsh description on Wikipedia:


[LIST]
[*]*Programmable command-line completion*: also in bash 
[*]*Sharing of command history among all running shells*: not useful, if I have different shells it's because I'm doing different things 
[*]*Extended file globbing*: also in bash 
[*]*Improved variable/array handling*: no opinion until I have seen it, but modern bash does cool things too. 
[*]*Editing of multi-line commands in a single buffer*: when it goes that bad I'm writing a script anyway. 
[*]*Spelling correction*: no opinion until I have seen it, not really missing it currently (command completion does the errorless typing for me....) 
[*]*Various compatibility modes, e.g. zsh can pretend to be a Bourne shell when run as /bin/sh*: on a decent computer, you can have sh/ksh installed too. Disk space is negligible. 
[*]*Themeable prompts, including the ability to put prompt information on the right side of  the screen and have it auto-hide when typing a long command*: can't see any purpose in this. 
[*]*Loadable modules, providing among other things: full TCP and Unix domain socket controls, an FTP client, and extended math functions*: Math functions, OK. For the rest, I woud be writing scripts anyway. 
[*]*Fully customizable*: they all are, for some value of "full":) 
[/LIST]

Not much incentive to change...

This post can come across as zsh-bashing :)

---

### Post by flaymond on 2014-12-01
I just downloaded and installed zsh on my Lubuntu. Well, I use them when I forgot the full <packagename> to install. At least, I know zsh got powerful auto-completion features than bash. ( I need to learn more before I made this statement, apparently).

---

