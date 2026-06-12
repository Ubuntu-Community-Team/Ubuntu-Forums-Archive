---
title: "Bash: Scripts within a script"
date: 2005-11-11
forum: Programming Talk
---

### Post by ramdisc on 2005-11-11
Hello,

My list of scripts is getting longer and longer.  I don't like to keep many tiny files within a folder.  I think it is uneconomic space-wise.

Does anyone have a base script that I can use that will allow me to choose scripts within a script?

Okay, imagine this:  I run allscripts.sh in Console.  And allscripts would print out a list of all the options (scripts within allscripts) in Console, and ask me "Which script would you like to run?".  I enter the option, and it and the individual script within allscripts would do its thing.  After its done, it would return to the main options of allscripts.

Is it possible to do this?  If not too much trouble, would someone please give me the base script to do this with examples in it?  The examples could be just echo scripts I can choose rather than long scripts.

---

### Post by poptones on 2005-11-11
Just look at one of the scripts in /etc/init.d. Most init scripts accept three options start, restart, and stop

/etc/init.d/foo start #starts foo daemon
/etc/init.d/foo stop # stops it

So make your script accept command line variables....

./myscript dothis
./myscript dothat with this data

---

