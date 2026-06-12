---
title: "Alias for clearing history"
date: 2014-05-23
forum: New to Ubuntu
---

### Post by thekernel2 on 2014-05-23
I have just begun learning Ubuntu and the BASH and thus make a lot of mistakes xD
Therefore I usually delete the terminal history using an alias like alias clsh="history -c && history -w" and execute the clsh alias to delete the terminal history.
But once the alias is executed the alias cant be run again as the history is completely wiped including all aliases.
So is there a way to use aliases for deleting terminal history?

Thanks
theKernel

---

### Post by deadflowr on 2014-05-23
your terminal history should be in the file
.bash_history
Your aliases should be in the file
.bash_aliases, or your .bashrc file.

Clearing your history should not have any effect on your aliases, if they are where they are suppose to be.

---

### Post by thekernel2 on 2014-05-24
Well googled a bit. It seems to create a permanent alias, the alias must be added to the ~/.bashrc file and then the ~/.bashrc must be executed.
The alias finally works for me when edited to : alias clsh="history -c && history -w && gnome-terminal && exit"

---

### Post by deadflowr on 2014-05-24
Like I stated, you can simply add an alias, or a lot of aliases, to the .bash_aliases file.
If you don't have one, make it.
```
touch .bash_aliases
```
```
nano .bash_aliases
```
add your aliases> Profit.
It's actually easier to maintain than putting them in your .bashrc file, since the .bashrc file is the bash configuration file, and therefore bloated with the configurations set to run bash. Making it a little more tedious to remember where in the file all your aliases are.

---

### Post by coldcritter64 on 2014-05-24
My bash alias histkill works quite nicely here, changes directory to home, echos nothing to (blanks) .bash_history, then does the same for recent file $HOME/.local/share/recently-used.xbel, doing so will clear all the user interface recent listings ... remove that bit if not wanted/needed; then it clears the history with "history -c" then clears the actual terminal you are in with "clear" and "resets" the terminal so the actual terminal your are in is not still holding any history. 

All is cleaned just by typing "histkill" in the terminal.  :)

```
yeti:~ $ aliasgrep histkill
alias histkill='cd ~ && echo > .bash_history && echo > $HOME/.local/share/recently-used.xbel && history -c && clear && reset'
```

When finished you are at a prompt with a clean history in the terminal and bash history file (also in the user interface recent listings if you keep that included). _*Note this immediately clears any current data displayed in the terminal when run.*_

Edit: I should note that "aliasgrep" is an alias to search the ~/.bash_aliases file for a word/string using cat and piping output to grep, example,
```
yeti:~ $ aliasgrep aliasgrep
alias aliasgrep='cat ~/.bash_aliases | grep'
```

Edit 2: you may find these next 2 aliases useful for managing aliases directly from your terminal or in gedit for a graphical text editor,
```
yeti:~ $ aliasgrep ed.aliases
alias ed.aliases='nano ~/.bash_aliases'
alias ged.aliases='gedit ~/.bash_aliases'
```

One final point to note: on saving the .bash_history file when adding a new alias, any currently open terminals will need to be restarted before the new alias is usable in them.

Regards, coldcritter64

---

### Post by whitesmith on 2014-05-24
Cold username, hot scripts. Got more? Share, please.

---

### Post by coldcritter64 on 2014-05-24
> **whitesmith said:**
> Cold username, hot scripts. Got more? Share, please.

:lol:, not here, will clutter up the OP's thread. Give me a PM if you seriously want some more aliases etc privately. Cheers :)

---

