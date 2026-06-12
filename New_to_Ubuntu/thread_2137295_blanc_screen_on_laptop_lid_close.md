---
title: "blanc screen on laptop lid close"
date: 2013-04-20
forum: New to Ubuntu
---

### Post by Slackie0 on 2013-04-20
I am an absolute Ubuntu Novice.. so please go easy!!

I am using 12.04.2 LTS
[COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR]
I have an external monitor connected to my laptop and when the lid closes it blanks the screen. 
on opening the lid the screen immediately comes on no lock or hibernation delay

I have trawled the forumsand followed lots of guides but to no avail

I have changed the power management settings to lid close do nothing
In brightness and lock after a "helpful" search and a bit of innept terminal use my lock function is now greyed out.

I have tried the command

gconftool-2 --type string --set /apps/gnome-power-manager/buttons/lid_ac "nothing"I just get an error saying can only use to set a value

The end result I am after is that when the  laptop lid is closed the feed to the external monitor is unaffected can any one help?

This machine is just a learning machine for Ubuntu so if I need to strip and reinstall the software its all not a problem, and can any one recommend a beginners guide for the terminal side of the Ubuntu 

All the best

---

### Post by dave2001 on 2013-04-20
Welcome to Ubuntu! The learning curve can be steep at first, but the forums are your friend! Things can also be a bit frustrating sometimes in the beginning, but if you persevere, you'll find the freedom of linux is unparalleled. 

I am running 12.04 on a thinkpad T500 laptop, which I often use to output a signal to my TV (with the lid closed). If you'll give us your system specs it will help determine what the issue might be. What is model make is the laptop, what is your GPU, and what driver do you have installed for it?  Let us know if you don't know how to find any of this info.

Here is a nice, in-depth, introduction to using the terminal: [http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)

Don't let the terminal scare you off. Doing things through the terminal is quicker, but most anything can also be done with the GUI.

---

### Post by Slackie0 on 2013-04-20
Thanks for the quick response the unit is an old dell mini 10 (specs below)

driver in use is Intel 945GMEx86/MMX/SSE2
experience standard

it was the default driver installed during clean install

[TABLE="class: spectable, width: 100%"]
[TR]
[TH="bgcolor: #CCCCCC, colspan: 2"]Specifications (base version)[/TH]
[/TR]
[TR]
[TD="bgcolor: #DDDDDD"]Manufacturer[/TD]
[TD="bgcolor: #DDDDDD"]Dell[/TD]
[/TR]
[TR]
[TD="bgcolor: #DDDDDD"]Model name[/TD]
[TD="bgcolor: #DDDDDD"]Inspiron Mini 10[/TD]
[/TR]
[TR]
[TD="bgcolor: #DDDDDD"]CPU type[/TD]
[TD="bgcolor: #DDDDDD"]Intel Atom [/TD]
[/TR]
[TR]
[TD="bgcolor: #DDDDDD"]CPU speed[/TD]
[TD="bgcolor: #DDDDDD"]1.6 ghz x2[/TD]
[/TR]
[TR]
[TD="bgcolor: #DDDDDD"]Graphics[/TD]
[TD="bgcolor: #DDDDDD"][Intel GMA 500]("http://www.intel.com/design/chipsets/embedded/SCHUS15W/index.htm")[/TD]
[/TR]
[TR]
[TD="bgcolor: #DDDDDD"]OS[/TD]
[TD="bgcolor: #DDDDDD"]32bit[/TD]
[/TR]
[TR]
[TD="bgcolor: #DDDDDD"]Display Size
[/TD]
[TD="bgcolor: #DDDDDD"]10.1" 1024 X 576[/TD]
[/TR]
[TR]
[TD="bgcolor: #DDDDDD"]RAM[/TD]
[TD="bgcolor: #DDDDDD"]1024 MB[/TD]
[/TR]
[TR]
[TD="bgcolor: #DDDDDD"]Hard Disk[/TD]
[TD="bgcolor: #DDDDDD"]245.1 GB[/TD]
[/TR]
[TR]
[TD="bgcolor: #DDDDDD"][/TD]
[TD="bgcolor: #DDDDDD"][/TD]
[/TR]
[/TABLE]

---

### Post by dave2001 on 2013-04-21
Thanks for the info. Two more quick questions.
1. Is your Ubuntu installation completely updated? (Many problems with Intel drivers in 12.04 have been fixed through updates).
2. Have you tried hooking up laptop to external display, THEN turning on, and immediately shutting lid? 

Sometimes the hardware of a laptop will "like" the external display better if the lid is shut before the OS is booted.

---

