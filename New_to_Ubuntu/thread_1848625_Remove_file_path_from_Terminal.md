---
title: "Remove file path from Terminal"
date: 2011-09-22
forum: New to Ubuntu
---

### Post by LeonardChurch on 2011-09-22
I'm just starting out using Linux, Ubuntu, and the terminal.
Having two issues.

1. I can't cd directly into a directory, I have to type out the whole path from the parent directory all the way down. I don't know if this is normal but it gets rather tedious if I want to get to something kind of buried.

2. When I do type out the path to the desired directory I end up having most of that path follow my user-name in the terminal

e.g.
```
user@computer:/$
user@computer:/$ cd /home/evan/Music/Genre/Artist
user@computer:~/Music/Genre/Artistl$
```Not much of an issue with the aforementioned example, but if I want to get to a directory that is 7-10 layers down it ends up taking up the majority of my terminal window, especially if the directory names are long. 

It seems like this could be fixed with a simple command but I don't know. Like I said I'm new to the terminal so the simpler the explanation the better.

---

### Post by wolfen69 on 2011-09-22
Once you cd through all those directories, the terminal will remember where you were. As soon as you open the terminal, you can use the up arrow to navigate to where you were, or start typing the path and hit the Tab key for auto-completion.

---

### Post by dniMretsaM on 2011-09-22
> **LeonardChurch said:**
> I'm just starting out using Linux, Ubuntu, and the terminal.
Having two issues.

1. I can't cd directly into a directory, I have to type out the whole path from the parent directory all the way down. I don't know if this is normal but it gets rather tedious if I want to get to something kind of buried.

2. When I do type out the path to the desired directory I end up having most of that path follow my user-name in the terminal

e.g.
```
user@computer:/$
user@computer:/$ cd /home/evan/Music/Genre/Artist
user@computer:~/Music/Genre/Artistl$
```Not much of an issue with the aforementioned example, but if I want to get to a directory that is 7-10 layers down it ends up taking up the majority of my terminal window, especially if the directory names are long. 

It seems like this could be fixed with a simple command but I don't know. Like I said I'm new to the terminal so the simpler the explanation the better.

Number 1 shouldn't happen I don't think. Might be a gnome-terminal thing, but I kinda doubt it (I use KDE's Konsole so I wouldn't really know). You might be typing it in wrong or it could be a bug. Try
```
./rest/of/path
```

The . tells the shell to look in the current directory.

Number 2 I don't know if you can change. The reason it stays like that is so you don't forget where you are (in which case you might accidentally delete something important), but there might be a way to make it so it doesn't display the entire path. Someone with more command line experience will have to help you with that one.

---

### Post by qyot27 on 2011-09-22
If #2's example is what you see in #1, then your problem is that you're trying to navigate from root for some reason.



/ is the file hierarchy root

~ is /home/username



If you're in /, it's no wonder why you can't go directly to something in ~, and why you have to type out the entire thing.

So the solution to #1 is figuring out why you're in / in the first place.



Any location starting with / refers to the very start of the hierarchy, if you want something relative to (and directly underneath) your current position, omit the /.

If you're in $HOME (another shorthand for /home/username), and want to get to /usr/local/bin, you can do either two things:

```
cd /usr/local/bin
```
Moves you directly there.

```
cd ..
cd ..
cd usr
cd local
cd bin
```
Which moves you there step by step, dropping to /home, then dropping to /, then moving up into usr, up into local, and up into bin.

Or if you're in $HOME and want to go into $HOME/Music,
```
cd Music
```

Or if you're in $HOME/Music and want to jump to $HOME/Documents,
```
cd ../Documents
```
which does it through relative paths, or
```
cd $HOME/Documents
```
which is an absolute path (/home/username/Documents is also an absolute path)

---

### Post by nothingspecial on 2011-09-23
For problem 2, I use an alias.

Edit your .bashrc

```
nano .bashrc
```

Put this at the bottom

```
alias here="PS1='${debian_chroot:+($debian_chroot)}\u@\h:\W\$ '"
```

note, it doesn't have to be "here", you can call it banana if you like.

Save it and close.

Then type

```
. ~/.bashrc
```

to get bash to read your modified .bashrc

Next time your prompt is too long type

```
here
```

(or banana, or whatever)

and to get it back to normal (the full path) type

```
. ~/.bashrc
```

---

### Post by drmrgd on 2011-09-23
I'd also like to add that if you need to quickly move to your home directory from anywhere in the file system, you can type "cd" with nothing after it.  That will take you to /home/<username>.

Also, as was pointed out earlier, "~" is a symbol that stands for your home directory, and can be used to substitute typing '/home/<username>'.  Combine that with auto-completetion (partially typing the name of the folder or file and then hitting tab), will get you around pretty quickly. 

As for the full path being displayed in the terminal, that can be changed.  Although I've never done it, since I find the pwd listing helpful, this link seems to have a couple good ideas to help you get a more concise prompt:

[http://lindesk.com/2009/03/customizing-the-terminal-the-prompt/]("http://lindesk.com/2009/03/customizing-the-terminal-the-prompt/")

---

### Post by el_koraco on 2011-09-23
You don't want your prompt to show you the location you're in at all, is that it?
Check out some [**stuff**]("https://wiki.archlinux.org/index.php/Color_Bash_Prompt") about the bash prompt

---

### Post by jnbutler1815 on 2012-06-12
#el_koraco that link wasn't very helpful for the question asked. 

It is very easy to remove the path from displaying in the prompt. Just edit the .bashrc file and where it says 
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
Just remove the w at the end by the \$. Save the file and then
type source .bashrc and hit enter. This is in Ubuntu 12.04.
You will still see your path location in the title bar of the terminal window. I don't know why they defaulted the prompt to include the path in Ubuntu, but that is the most ridiculous thing ever, especially since it is displaying in the title bar. And if you want to know where you are, do a pwd commmand!!!
Another thing, it is hard to believe that 6 responses never told the poor person how to resolve his 2nd issue and it is so easy to do. If you don't have that much experience with linux yourself, don't try to help others!!

---

### Post by idoitprone on 2012-06-12
> **jnbutler1815 said:**
> #el_koraco that link wasn't very helpful for the question asked. 

It is very easy to remove the path from displaying in the prompt. Just edit the .bashrc file and where it says 
PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
Just remove the w at the end by the \$. Save the file and then
type source .bashrc and hit enter. This is in Ubuntu 12.04.
You will still see your path location in the title bar of the terminal window. I don't know why they defaulted the prompt to include the path in Ubuntu, but that is the most ridiculous thing ever, especially since it is displaying in the title bar. And if you want to know where you are, do a pwd commmand!!!
Another thing, it is hard to believe that 6 responses never told the poor person how to resolve his 2nd issue and it is so easy to do. If you don't have that much experience with linux yourself, don't try to help others!!

welcome to the forums. Everyone has a say, but they all not necessary the best advice. I'm an idoit so of course mine is always bad

---

