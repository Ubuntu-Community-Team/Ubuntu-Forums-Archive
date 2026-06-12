---
title: "After update, can only acces Thunderbird via sudo"
date: 2013-11-11
forum: New to Ubuntu
---

### Post by koprov on 2013-11-11
[COLOR=#333333][FONT=Lucida Grande]Hello,[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]recently my Thunderbird has stopped opening as usual, I can only open it via the terminal "sudo thunderbird" command. I have looked on the internet for a solution but none seems to work for me...[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]So far I have tried:[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]- uninstall/reinstall[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]- creating a new profile and moving mail[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]- in desperation even "chmod -R 777 .thunderbird" (after I tried to chown -R with appropriate user:group)[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]What bugs me is that I can remove/rename the .thunderbird directory the program starts OK without the need for sudo and I can create an new user. But as soon as I transfer my mail to the new directory it starts to only work with sudo.[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]I thought it might be a problem with the files from inside the directory so I copied files from a backup I did 5 months ago and the same thing happens, no go. (I did not have the problem 5 months ago)[/FONT][/COLOR]

I have also posted this question on a Thunderbird specific forum, but heard nothing but silence from them.
[COLOR=#333333][FONT=Lucida Grande]
So, any suggestions on what I should try next or how to debug this problem?[/FONT][/COLOR]

---

### Post by Lars Noodén on 2013-11-11
You might set it back to regular permissions while we look at the rest.

```

sudo chown -R koprov:koprov ~/.thunderbird/
find ~/.thunderbird/ -type d -exec chmod 700 {} \;
find ~/.thunderbird/ -type f -exec chmod 600 {} \;

```

What kind of messages or errors does Thunderbird give you when you launch it from the terminal, but without sudo?

---

### Post by koprov on 2013-11-11
No luck with those permissions.

Well, there is no error at all, it just does not launch. In terminal it just returns to a new bash line and if I run it from a launcher it givers me the "loading wheel" for a sec and then does nothing.

Is there a way to view, step-by-step what an app does at launch and where it crashes?

---

### Post by koprov on 2013-11-12
bump? Anyone? It really feels uncomfortable (and unsafe) to be running Thunderbird with root permissions...

---

### Post by Lars Noodén on 2013-11-12
Looking at Thunderbird on my machine using [lsof](http://manpages.ubuntu.com/manpages/trusty/en/man8/lsof.8.html), I see it accessing other directories in my home directory. 

In particular I see Thunderbird using 

/home/user/.cache
/home/user/.config
/home/user/.local
/home/user/.thunderbird

What happens is you reset the permissions (sudo chown -R koprov:koprov ~) for your entire home directory?  That should get all the other hidden directories that are being accessed and may have gotten written to as root.

---

### Post by koprov on 2013-11-12
Yes, that did it! Much kudos! I only could not get a hold of the .gvfs directory, but it does not seem to matter ;)

---

