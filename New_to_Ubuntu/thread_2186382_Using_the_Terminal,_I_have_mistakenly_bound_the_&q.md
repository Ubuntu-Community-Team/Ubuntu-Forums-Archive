---
title: "Using the Terminal, I have mistakenly bound the &quot;T&quot; key to a string"
date: 2013-11-07
forum: New to Ubuntu
---

### Post by tabloid on 2013-11-07
I opened the Terminal - I am using Trisquel OS - and *thought* I was pasting a string of letters into the Command Line. What I *actually* did was bind the key for lower case 't' to that string. So now whenever I need to type the letter 't' in the command line, I get this long string instead. Clever me! [ I lazily used the "ctrl alt V" to 'paste' into the comand line].

I tried uninstalling the Gnome Terminal and re-installing it - but this made no difference.

I am out of my depth as to how to sort it. Could anyone please advise?

I intend to use the Terminal a lot - have written some shell scripts.
Your help would be mightily appreciated.

from aka tabloid

---

### Post by TheFu on 2013-11-07
Open an **xterm**, then remove the settings for "Terminal" located in the ~/.config/ subdirectories ... er ... somewhere. That is why removing and reinstalling didn't matter. Settings are stored per-user and user settings are not touched when software is removed/purged.

As I only use xterms (have for 20+ yrs), I don't know the exact "Terminal" settings location. Sorry.

---

### Post by tabloid on 2013-11-07
Many thanks for the swift, helpful reply. I shall now get to grips with the config file - I need to learn more about how to personalise the settings - and get to know the 'workings'.

I also installed a different terminal as a quick fix - and the shell scripts worked ok. But I want to make the Gnome Terminal work properly. 

Thank you for taking the time and for your good advice

aka tabloid

---

