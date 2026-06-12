---
title: "N00B Wants to pick your brains for a moment."
date: 2013-01-14
forum: New to Ubuntu
---

### Post by MoFro624 on 2013-01-14
First Off I Want  To Say Hi. I'm New To The Ubuntu World And So Far It's Great. I like it better than Windows and Mac. Never was a fan of bloat ware and filler programs. Ubuntu is not filled with useless stuff that I won't use. So thanks to Conical for such a great OS. 
Ok I do have a few questions and apologize if I am double posting. 
(1)- When I ran Windows I have to run defrag once a month to keep things running smoothly and Advanced system care to clean up the place. With Ubuntu is there such need for these things? Is there a need for defraying and registry cleaning?
(2)- What are some good moods to run? Right now I have the conky bar at the bottom. The conky weather "widget". I have Wallch installed to change my BG IMG. What about screen savers or is there such a need for these?
(3)- Anything you guys recommend for beginners?

---

### Post by The Cog on 2013-01-14
1: No need to defrag or the like.

2: Not sure what a good mood is. My wife will confirm that. You only actually *need* screensavers if you are leaving the computer unattended showing the same image for a long time. I sometimes get it to run some of the prettier ones just for the change of scenery.

3: Hang around here and just read the threads with titles that catch your interest. Don't make learning Linux a chore, just go where the urge takes you. Enjoy.

And welcome to the forums.

---

### Post by MoFro624 on 2013-01-14
> **The Cog said:**
> 1: No need to defrag or the like.

2: Not sure what a good mood is. My wife will confirm that. You only actually *need* screensavers if you are leaving the computer unattended showing the same image for a long time. I sometimes get it to run some of the prettier ones just for the change of scenery.

3: Hang around here and just read the threads with titles that catch your interest. Don't make learning Linux a chore, just go where the urge takes you. Enjoy.

And welcome to the forums.

Ugh. Auto Correct. I knew I should of proof read. It was supposed to be good mods.
Thank You for the reply

---

### Post by GrouchyGaijin on 2013-01-14
I'm not much more than a noob myself but one thing I found that I use a lot is a bash alias.  You can add an alias (abbreviation) for a command you use frequently so that you can type the alias into the terminal instead of the entire command.

The bash_aliases file is hidden in your home folder. (It has a . in front of the name.)  You can see it by opening the home folder and typing ctrl+h.

Two aliases I use a lot are:
```
alias flv='avconv -i foo1.avi -b 400000 -s qvga -acodec libmp3lame -ar 22050 bar.flv'
```  which takes an avi file and recodes it into a small flash file.
I have other aliases for mpegs and mov files.

I also use:
```
alias openba='gedit ~/.bash_aliases'
```

The important thing is that you need to follow this format:
```
alias name='command or path to script'
```

---

### Post by GrouchyGaijin on 2013-01-14
> **The Cog said:**
> 1: No need to defrag or the like.

2: Not sure what a good mood is. My wife will confirm that.

3: Hang around here and just read the threads with titles that catch your interest. Don't make learning Linux a chore, just go where the urge takes you. Enjoy.

And welcome to the forums.

# 2 - Funny my wife can confirm the same thing.

# 3 - Amen brother

---

### Post by bogan on 2013-01-14
Hi!,** GrouchyGaijin,**

Thanks for posting your 'Alias' Tip. ```
alias nux='~/usr/lib/nux/unity_support_test -p'
```

I just tried that and it worked fine, but it did not produce a '~/.bash_aliases' file in the home folder. [ This is with 12.10].

There is a .bshrc, a .bash_history and a .bash-logout file, none of which have recent dates last accessed, but no '.bash_aliases'.

Do you know where else they might be saved ? or is there a command to annul the alias or delete it, other than using gedit.??

Chao!,** bogan.**

---

### Post by GrouchyGaijin on 2013-01-14
> **bogan said:**
> Hi!,** GrouchyGaijin,**


There is a .bshrc, a .bash_history and a .bash-logout file, none of which have recent dates last accessed, but no '.bash_aliases'.

Do you know where else they might be saved ? or is there a command to annul the alias or delete it, other than using gedit.??

Chao!,** bogan.**

Open the .bashrc file
```
gedit .bashrc

```

and check that this is there:
```
# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

```
(It **should** be)
The create a new file and call it .bash_aliases
Save that file to your home folder.

---

### Post by 64Buntu on 2013-01-14
Depends very much what you are like for example I use Gnome 3 my personal preference 

If you are using unity you can install Myunity from The Ubuntu soft where centre.

And also what you are wanting to do. There is a app/install for everything pretty much

---

### Post by bogan on 2013-01-14
Hi!, **GrouchyGaijin**,

Thanks for that. Yes, the 'Alias definitions' was there, but there is no '/usr/share/doc/bash-doc/examples' folder or files.

I created the .bash-aliases file and made a new alias, which works, but the file is still zero bytes.

Mystery!!

Edit: mystery solved!  The aliases I created in a terminal only lasted until a reboot. I had to enter them directly into the .bas-aliases file. it was not automatic.

Chao!,** bogan**. Thanks again.

---

### Post by Impavidus on 2013-01-14
When you use **alias** the alias is active in your current shell (the terminal in which you gave that command), but it's not saved. Put the entire alias command in your .bash_aliases. It will be loaded whenever you open a new shell or when you use **source .bashrc**.

---

### Post by GrouchyGaijin on 2013-01-14
> **bogan said:**
> Hi!, **GrouchyGaijin**,

Thanks for that. Yes, the 'Alias definitions' was there, but there is no '/usr/share/doc/bash-doc/examples' folder or files.

I created the .bash-aliases file and made a new alias, which works, but the file is still zero bytes.

Mystery!!

Chao!,** bogan**.

There seems to be a basic misunderstanding.
I use the .bash_aliases file to keep a list of commands and their aliases I type in the terminal to run those commands.

For example:

I opened my .bash_aliases file and wrote
```
alias openba='gedit ~/.bash_aliases'
```
now when I type openba in the terminal gedit will open the .bash_aliases file (so I can add a new alias).

Another example:
In the .bash_aliases file I wrote
```
alias refreshfonts='sudo fc-cache -v -f'
```
now after I install a font I can simply type refreshfonts in the terminal and the command 
```
sudo fc-cache -v -f
```will be run.

---

### Post by rhoslug on 2013-01-14
Perhaps also check out Ubuntu Tweak:

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

Useful for making Ubuntu run a tab bit smoother.

---

### Post by d4m1r on 2013-01-14
Welcome to the world of Ubuntu!

To get you started on mods, google "psensors" or "sysmon" if you are interested in learning more about or monitoring your hardware.

---

### Post by 64Buntu on 2013-01-14
There are many videos on Youtube just type in 10 things to do after installing Ubuntu.

Some are not the best but there are some with good tips that could suit.

---

