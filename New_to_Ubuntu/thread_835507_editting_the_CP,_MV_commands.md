---
title: "editting the CP, MV commands"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by moose4204l on 2008-06-20
how do i edit the cp and mv terminal commands to always prompt me about overwritting without having to pass the -i? param. Also, how do i make it print out the status of the commands, say if i was cp-ing a a folder, it prints out the bytes transfered and how long and size  believe?

thanks

---

### Post by Cypher on 2008-06-20
Use Bash aliases..play with this in the shell
```

alias cp="cp -i"
alias rm="rm -i"
alias mv="mv -i"

```
Now those 3 commands will constantly prompt you to continue.

To take it a step further and print information upon complete, you'd create Bash functions with the same name of the commands and there track the data you care about.

I don't believe CP returns the information you're talking about, at least, there is nothing mentioned in the man pages?

---

### Post by moose4204l on 2008-06-20
it might be over an ssh i am thinking about...i just type that into the terminal or in the cp files, which i dont know where they are located

edit:::typed in terminal and works...do i have to do it each boot up or does it stay that way?

---

### Post by Iandefor on 2008-06-20
You can setup aliases in ~/.bashrc, and the next time you open up a terminal it'll use the aliases.

An alias acts like a simple text substitution- when you run "cp" it'll run "cp -i" instead, for instance.

Setting up an alias is simple: just open up ~/.bashrc for editing and add the following:
```
alias cp="cp -i"
alias mv="mv -i"
```Regarding getting more detailed progress information, I don't know how to help you. The best I know is to enable verbose output (-v flag).

EDIT: Cypher beat me to it!

---

### Post by moose4204l on 2008-06-20
i tried to edit the bashrc file but i dont know where to put it. i also tried to make a bash_aliases file like the thiing said but it didnt work. any help?

---

### Post by fatality_uk on 2008-06-20
Your .bashrc file is in your home folder. It is hidden. To edit it you need to type the following into a terminal:
> 
gksudo gedit /home/$USER/.bashrc

---

### Post by Iandefor on 2008-06-20
Why should a user-specific file be edited with root permissions, fatality_uk?
> i tried to edit the bashrc file but i dont know where to put it. i also tried to make a bash_aliases file like the thiing said but it didnt work. any help?You can add it pretty much anywhere you like in the .bashrc file. I suggest the very end- and, just in case it wasn't entirely clear, the period at the beginning is significant (It's kind of a half-arsed way to hide a file- most utilities will pretend the file isn't there if it's prefixed with a period unless you specify the filename with the period).

.bashrc is in your home directory- so, /home/[your username]/.bashrc (or ~/.bashrc for short).

---

### Post by bodhi.zazen on 2008-06-20
> **fatality_uk said:**
> Your .bashrc file is in your home folder. It is hidden. To edit it you need to type the following into a terminal:

Yikes, that is too much typing :)

gedit ~/.bashrc

You do not need gksu to edit files you own ...

And if you are going to use $USER it might be shorter to use $HOME

:twisted:

---

### Post by fatality_uk on 2008-06-20
> **bodhi.zazen said:**
> Yikes, that is too much typing :)

gedit ~/.bashrc

You do not need gksu to edit files you own ...

Oops. Force of habit :D
Been gksudo'ing all day sorting out an issue. Gets into your head you know.
But principle is the same ;)

---

### Post by mali2297 on 2008-06-20
In addition, you can set the commands to use *verbose* mode:
```

alias cp='cp -vi'
alias mv='mv -vi'
alias rm='rm -vi'

```

---

