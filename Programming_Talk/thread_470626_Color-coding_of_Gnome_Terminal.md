---
title: "Color-coding of Gnome Terminal"
date: 2007-06-11
forum: Programming Talk
---

### Post by O-pos on 2007-06-11
Hello,

I would like to color-code text in Gnome terminal. More specifically, I would like to change the color of text, that I input in terminal in yellow, and do not change the output and leave as it is.

Also, if it's possible I'd like to make color of username "name@laptop $" green, for that I could easily find it.

Is it possible at all?

I saw one picture with settings like this, but it's a terminal in windows and not linux. Here's the picture:

[http://www.mplayerhq.hu/images/screenshots/WindowsXP-01.jpg](http://www.mplayerhq.hu/images/screenshots/WindowsXP-01.jpg)

---

### Post by FryerFox on 2007-06-11
There is a file called .bashrc in your home direcory that is executed whenever you start a shell. The variable, PS1 contains your prompt. Color codes are escaped, for more detail, look [here]("http://www.pantz.org/scripting/shell/colorterm.shtml").

The command to add in ~/.bashrc is:
> 
PS1='${debian_chroot:+($debian_chroot)}\[\033[0;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '

But before you add that, read through the script and you should notice that it's already in there and just needs to be uncommented.

---

### Post by NeoGreen on 2007-06-11
I was looking for something like that too.  Thanks for starting the thread O-pos and thanks for the reply Fryer Fox.:D

---

### Post by O-pos on 2007-06-14
Thanks. with the green prompt it worked super, but when I change the color of the text to yellow, it changes the whole text to yellow. But I want input text yellow, output - standard, white.

?? :(

---

### Post by Soybean on 2007-06-14
If it's possible to do what you want, the answer should be in here: [http://tldp.org/HOWTO/Bash-Prompt-HOWTO/](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/)

Don't change the colors in the gnome-terminal settings. Well, I mean, change them if you want... but that's not the correct place to change them to get the sort of effect that you want. ;) 

Good luck! :)

---

### Post by NeoGreen on 2007-06-23
Man, that is an awesome link.:D

---

### Post by mdalacu on 2010-01-12
The quickest way:
Open Gnome Terminal and:
1. **gedit .bashrc**
2. Search for line containing :"#force_color_prompt=yes" and change it to
"**force_color_prompt=yes**" (delete hash)
3. save, close gedit, close and reopen terminal !

Simple, no ?

---

