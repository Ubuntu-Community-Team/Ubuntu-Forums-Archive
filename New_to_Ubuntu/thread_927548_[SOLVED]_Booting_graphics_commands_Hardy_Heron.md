---
title: "[SOLVED] Booting graphics commands? Hardy Heron"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by Sabreful on 2008-09-23
Still kinda new as this is my second post, still kinda figuring things out as I go along. In any case I posted a thread a while back (Graphics Problems?) and learned about my (blacklisted) ATI graphics card.
 Checked out the thread 
([COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=764633[/COLOR]) a forum staff member recommended that explained my problem and showed about an unstable workaround with those cards; well by the good graces it worked by typing the commands into the terminal.


mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager

compiz --replace &

everything works fine and dandy as far as graphics go and what not, but only ***after*** I type those into the terminal. I have to manually open a terminal and enter it in every time I reboot my laptop, or Crtl+Alt+Backspace, or just boot my computer up for the first time of the day (have a laptop so don't just wanna leave it up and running for days at a time). Not that I mind too much just wondering if there's any way that it can be fixed so that those commands are part of the boot sequence, or whatnot. As a hopeful (unfortunately didn't work) went to my system>preferences>sessions and tried to get that to work, but no luck so far. Any suggestions?
Thanks in advance

---

### Post by Elfy on 2008-09-23
You have to run both commands at start or only the second?

You could make a script and then add it to your startup programs

---

### Post by Sabreful on 2008-09-23
Only the second
compiz --replace &

and when i do run that it fixes it so that the visual settings automatically go to 'normal' instead of 'none' but the terminal gives me some error after the checks that I don't really understand as well


GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

is that something I should be worrying about? or something I can fix?

in any case I would love to learn about scripts and just about everything else I can do with ubuntu due to the fact that I've been a windows guy for pretty much the last 7 years so with linux I'm pretty much new. 
Any chance of a redirect of some tutorials and pretty much basics so I can use this (awesome) operating system to it's fullest potential?

---

### Post by Elfy on 2008-09-24
It would probably be fixable - use the compiz settings manager, run ```
ccsm
``` in terminal and check the scale plugin. I can't give more on that as I don't use compiz very much at all.

I would have thought that you would only need to use the command once, I have run it from the Alt+F2 run dialogue in the past.

But if it doesn't you can make a script and run it at startup easily enough I think - I have to use a script to get menu working properly when I do use compiz.

Open gedit and paste in

> #!/bin/bash
compiz --replace &

save in your /home as, for example, startcompiz.sh then open a terminal and run

```
chmod +x startcompiz.sh
``` to allow the file to be executed. Now open session from the system > preferences menu and add the script to the list.

There are a couple of tutorials here, but it's not something I've gotten into as yet so not sure
[http://www.troubleshooters.com/codecorn/shellscript/index.htm](http://www.troubleshooters.com/codecorn/shellscript/index.htm)
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

### Post by Sabreful on 2008-09-25
awesome thanks alot was wondering why just adding the command to the sessions didn't work, alas now it does thanks a lot.
assuming that if i didn't want to boot it up would just remove what i added into sessions though eh?

---

### Post by Elfy on 2008-09-25
Not sure tbh.

As far as using it or not - I turn off the script I have if I'm not using compiz and turn it on when I need it.

---

