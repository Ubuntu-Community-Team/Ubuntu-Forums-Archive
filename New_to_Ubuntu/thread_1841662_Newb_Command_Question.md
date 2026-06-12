---
title: "Newb Command Question"
date: 2011-09-09
forum: New to Ubuntu
---

### Post by anotherusernametoforget on 2011-09-09
I'm new to Ubuntu as of last night, and am not used to using the command screen. After every command I enter, the screen vanishes and I have no way to know wether the command was successful.

I've been unsuccessful in finding a rudamentary newb guide for ubuntu as of yet. Links would be appreciated.

I have also attempted to add additional repositories via vague online instruction with no success.

Lastly, once I understand the Command functions better I will attempt to correct whatever is preventing audio from being played.

Thanks for all consideration and any advice.

---

### Post by haqking on 2011-09-09
> **anotherusernametoforget said:**
> I'm new to Ubuntu as of last night, and am not used to using the command screen. After every command I enter, the screen vanishes and I have no way to know wether the command was successful.

I've been unsuccessful in finding a rudamentary newb guide for ubuntu as of yet. Links would be appreciated.

I have also attempted to add additional repositories via vague online instruction with no success.

Lastly, once I understand the Command functions better I will attempt to correct whatever is preventing audio from being played.

Thanks for all consideration and any advice.


Hi and welcome to the forums:

See here [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

there are others about bash and bash scripting and the like but this should get you started as a primer.

also see here [http://linuxcommand.org/](http://linuxcommand.org/)

However it really depends what you need to do as alot if not most can be done with GUI if the terminal is scary at the moment, so what exactly do you want to do ?

also very important that you read these

sudoers file
[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

rootsudo
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

The root (superuser) account is disabled by default in Ubuntu and we prefer to use sudo to carry out admin tasks and using terminal will often require you to place sudo before any command so make sure you read the links.

hope this helps and enjoy the community.

as for the repositories, what were trying to do, you can do it graphically with update manager or from terminal with the following:

gksudo gedit /etc/apt/sources.list

use gksudo for graphical apps and not sudo (see the links to sudo above)

then you can add the source URL in there, but dont play with it if you are unsure, post here for anything when you are unsure of what to do

---

### Post by anotherusernametoforget on 2011-09-09
Thank you so much for the links and help, I'll be reading those now.

I appreciate your quick response, and not being flamed for being ignorant.

Cheers

---

### Post by JC Cheloven on 2011-09-09
> **anotherusernametoforget said:**
> I'm new to Ubuntu as of last night, and am not used to using the command screen. After every command I enter, the screen vanishes and I have no way to know wether the command was successful.



I suspect you aren't really using the terminal to enter commands, but a small utility which pops up when Alt-F2 is pressed, right?
This is intended as a quick'n'dirty method to enter a single command, not really a terminal. To open a terminal window go to the menu, you'll find it at Accesories - Terminal. 
EDIT: Ctrl-Alt-T will also give you a terminal window (most likely).

Once this "little detail" is passed, you can get full advantage of haqking's advice.

Have fun, and try to not overcomplicate things! Everything should be easy :)

---

### Post by hansolo4949 on 2011-09-10
Don't worry, everyone has gone through this part of their Ubuntu experience. After all, no question is a dumb question!

What you may be doing, as someone else said, is pulling up the "run" dialogue instead of the terminal. The terminal is a (in Ubuntu purple) square box with something like "hansolo4949@gmail-pc:" in it. If that is not what you are seeing, tu are probably in the wrong place. I have forgotten where the terminal is in the menus (I have it on my desktop, and I have not used Ubuntu in a while, with school and everything), so can someone please help him with this? Thanks

Welcome to the forums!

---

### Post by anotherusernametoforget on 2011-09-10
> **JC Cheloven said:**
> I suspect you aren't really using the  terminal to enter commands, but a small utility which pops up when  Alt-F2 is pressed, right?

You are absolutely correct! I realized this when reading the recommended article, and felt foolish and relieved. 

> **hansolo4949 said:**
> Don't worry, everyone has gone through this part of their Ubuntu experience. After all, no question is a dumb question!

What you may be doing, as someone else said, is pulling up the "run" dialogue instead of the terminal. The terminal is a (in Ubuntu purple) square box with something like "hansolo4949@gmail-pc:" in it. If that is not what you are seeing, tu are probably in the wrong place. I have forgotten where the terminal is in the menus (I have it on my desktop, and I have not used Ubuntu in a while, with school and everything), so can someone please help him with this? Thanks

Welcome to the forums!

Thats what happened! Thanks!

---

