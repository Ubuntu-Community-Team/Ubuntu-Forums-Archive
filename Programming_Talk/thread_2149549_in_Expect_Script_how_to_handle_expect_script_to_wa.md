---
title: "in Expect Script how to handle expect script to wait for &amp; execute another script?"
date: 2013-05-29
forum: Programming Talk
---

### Post by abhi4now on 2013-05-29
[COLOR=#333333][FONT=arial]Using Expect script I am trying to automate execution of 2 different scripts run by 2 different users on same server.[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]Script 1 needs to be run by user 1[/FONT][/COLOR]
[COLOR=#333333][FONT=arial]Script 2 needs to be run by user 2.[/FONT][/COLOR]

[COLOR=#333333][FONT=arial]The workflow of these scripts is: [/FONT][/COLOR]
[COLOR=#333333][FONT=arial]Script 1 is executed as user 1. During execution it creates Script 2 and halts for input. At this stage it asks to execute script2 as user 2 and once complete. Script 1 will resume when return key is pressed.[/FONT][/COLOR]

[COLOR=#333333][FONT=arial]The problem I am facing is when Script 1 halts and waits for input i don't know how to execute script2 as user2 and then resume script 1. [/FONT][/COLOR]

[COLOR=#333333][FONT=arial]I really need some help on this. I am very new to scripting.[/FONT][/COLOR]

---

### Post by ofnuts on 2013-05-29
If you script uses the 'sudo' command to execute script2 it just needs to wait until the sudo command terminates (in other words, the instruction after the sudo will be executed after script2 exits).

This may require a bit of setup of sudoers.

---

