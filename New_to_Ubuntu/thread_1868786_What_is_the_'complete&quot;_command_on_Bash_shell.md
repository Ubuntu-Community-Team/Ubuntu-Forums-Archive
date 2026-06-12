---
title: "What is the 'complete&quot; command on Bash shell"
date: 2011-10-24
forum: New to Ubuntu
---

### Post by MagicThinker on 2011-10-24
G'day, (Running Ubuntu 11.04 64Bit)

I have been using linux for nearly 10 years and this is the first time I have come across the 'complete' command.  This thing looks like a rootkit as it appears to be linked to most commands.  I looked into list of installed programs and it is not there or a dependency.

I have been getting this since I did an update.  I can only get it to spit out the following when I launch Gnome-Terminal from the Desktop, it looks like this :

complete: usage: complete [-abcdefgjksuv] [-pr] [-DE] [-o option] [-A action] [-G globpat] [-W wordlist]  [-F function] [-C command] [-X filterpat] [-P prefix] [-S suffix] [name ...]

This is was I am seeing multiple times on a clean launch of the Gnome-Terminal it looks like it is recording something or trying too.

I have run rkhunter, chrootkit, unhide and the like nothing is coming up.

Any help at want this is would be great.
As yet I have not setup Tripwire so I can't redo however I do have many backups. yer.

---

### Post by westie457 on 2011-10-24
Hi, only guessing at this. Do you have 'zeitgeist' running at all?

---

### Post by MagicThinker on 2011-10-24
Thanks for the quick reply

Just checked zeitgesit is installed.  I checked the History under synaptic and there is no date for the installation of this software.  
In fact the history file is also missing the last 4 days worth of activity???  I have updated the system last night and installed a few knowen programs since the 20th but these are no longer showing up in the history file?? Something is a miss??


Can zeitgesit be uninstalled as this is unneeded???
Also is there a way to find out what else has been installed in this time, as this seems to be a forensic thing?

I now wish that I installed Tripwire earlier.

---

### Post by haqking on 2011-10-24
it is a Bash command (builtin) command.

see here [http://linux.about.com/library/cmd/blcmdl1_builtin.htm](http://linux.about.com/library/cmd/blcmdl1_builtin.htm)

and here [http://www.linuxjournal.com/content/more-using-bash-complete-command](http://www.linuxjournal.com/content/more-using-bash-complete-command)

for more info

---

### Post by MagicThinker on 2011-10-25
> **haqking said:**
> it is a Bash command (builtin) command.

see here [http://linux.about.com/library/cmd/blcmdl1_builtin.htm](http://linux.about.com/library/cmd/blcmdl1_builtin.htm)

and here [http://www.linuxjournal.com/content/more-using-bash-complete-command](http://www.linuxjournal.com/content/more-using-bash-complete-command)

for more info
Thank you for the replies and links.  You learn something new everyday and today is one of those days.  After looking at the links and reading up about it this command may come in useful. 

Thank again for the quick responses.

Cheers

---

### Post by haqking on 2011-10-25
> **MagicThinker said:**
> Thank you for the replies and links.  You learn something new everyday and today is one of those days.  After looking at the links and reading up about it this command may come in useful. 

Thank again for the quick responses.

Cheers

no worries you are welcome.

peace

---

