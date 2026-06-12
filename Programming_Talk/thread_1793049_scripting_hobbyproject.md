---
title: "scripting hobby/project"
date: 2011-06-28
forum: Programming Talk
---

### Post by l3ecl on 2011-06-28
Hi there

I have a small project in mind but I wouldn't know where to start in implementing it.

I have 10 folders in my home directory that I frequently access, these folders pertain to classes, business, projects ect. I would like to have a shortcut system via terminal to quickly access these folders.

I would like to have a script, such that when executed, displays a list of shortcut keys and their destinations. For example, when I execute "MyScipt.sh" in the terminal, it displays:

> Key     Destination
cdm     ~/folder/somefolder/....math101 directory. 
cdp     ~/folder/folder/....projects directory. 
.....

then if i type 'cdm' in the terminal, it takes me to:
~/folder/somefolder/....math101 directory. 

I don't really have an idea of what's the best way to implement this. Ideas and suggestions are needed, and a finger towards the right direction would be really helpful.

---

### Post by Barrucadu on 2011-06-28
You could use aliases for the shortcuts, and a little script to manage the aliases.

---

### Post by Cheesehead on 2011-06-28
Shortcutting is one of the original use cases for symlinks.```
ln -s ~/folder/somefolder/....math101 ~/cdm
ls cdm   #test
```At the end of the semester, it's easy enough to rm your links instead of editing your aliases or scripts.

---

### Post by l3ecl on 2011-06-28
> **Barrucadu said:**
> You could use aliases for the shortcuts, and a little script to manage the aliases.

I was thinking that too, but just a few questions:

1. would the aliases be in the .bashrc file?
2. how would I write this script to manage the aliases?

---

### Post by fsleeman on 2011-06-29
> 1. would the aliases be in the .bashrc file?
2. how would I write this script to manage the aliases?

1) yes
Example:
alias la='ls -A'
alias ssh='ssh -X'

2) I would add a commented sections at the beginning and end of the directories aliases, like 
#### Directory Alias Start #####
aliases ...
...
#### Directory Alias End ####

Then you script can parse each alias line in this section of the .bashrc. If you block out your new alias section it will allow you to ignore any other aliases that have nothing to do with your directory mappings.

---

### Post by diesch on 2011-06-29
I've written [a similar script](http://www.florian-diesch.de/software/shell-scripts/) some time ago. Instead of different scripts it uses command line arguments and shell completion.

It's written for Zsh but except for the command line completion it works with Bash, too.

---

