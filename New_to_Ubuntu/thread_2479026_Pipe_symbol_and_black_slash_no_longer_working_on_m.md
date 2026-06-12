---
title: "Pipe symbol and black slash no longer working on my Ubuntu 20.04 OS"
date: 2022-09-12
forum: New to Ubuntu
---

### Post by bhubunt on 2022-09-12
Hi,
in the past I have always been able to use the pipe symbol on my qwerty Lenovo Thinkpad laptop (Ubuntu 20.04 OS). But recently, I've been unable to type in the command line "last|head," to give but one example, because the | now comes out as a < and the back slash \ as a > [I am typing this on a spare Windows computer that I have sitting around at home.]

Does anyone know what kind of bug could have caused this sudden keyboard switch? 

Since the pipe symbol is important for all kinds of command lines, I'd be grateful for a suggestion.

Thanks.

---

### Post by ActionParsnip on 2022-09-12
Have you checked your keyboard layout and language settings?

---

### Post by bhubunt on 2022-09-12
Yes, I have checked the keyboard layout and the language settings and everything else works absolutely fine. Just the pipe and the backslash are now producing < and >. Everything else is in order.  I do have separate keys for < and > on the qwerty keyboard, so not sure what is going on.  Is there a command line I can type into a terminal to check on why the switch occurred?

---

### Post by yancek on 2022-09-12
Run the command:  xmodmap -pke from a terminal and the output will show a numerical value for each key.  If the \ and | keys show > and <, then remap the > and < keys to \ and |.  The link below explains how to do this one time and also how to add a script to run on boot so you don't have to go through the process each time you boot the computer.

  [https://ictsolved.github.io/remap-key-in-linux/](https://ictsolved.github.io/remap-key-in-linux/)

---

### Post by MAFoElffen on 2022-09-17
@Yancek -- +1  ( I wish we could "Like" a post. ) Good answer!

I don't know of anything in 20.04.5 that would do that. And others, even those with Lenonvo Laptops are not reporting this problem. So like one of my computers with another problem, I think this is sort of an isolated quark.

---

