---
title: "Alias are erased at reboot"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by lance bermudez on 2008-08-11
I have not problem creating my alias with the alias command here is an example
alias dir=ls
but when I restart the computer all the alias I have created are not their any more their have been erased. And If i try sudo alias I get an error message "sudo: alais: command not found" This command would be very help full if he was not erased every time I shutdown. Is their a way to stop the easing of the alias commands I create?

---

### Post by Brebs on 2008-08-11
Put the alias commands in ~/.bashrc

---

### Post by schauerlich on 2008-08-11
> **Brebs said:**
> Put the alias commands in ~/.bashrc

It's actually recommended to put them in ~/.bash_aliases. Open up ~/.bashrc and remove the # from the lines that look something like this:

```

# if [ -f ~/.bash_aliases ]; then
#     . ~/.bash_aliases
# fi

```

Then open up (or create, if necessary) ~/.bash_aliases and add your aliases.

```

alias example="command you want to alias"

```

---

### Post by Oldsoldier2003 on 2008-08-11
> **EDavidBurg said:**
> It's actually recommended to put them in ~/.bash_aliases. Open up ~/.bashrc and remove the # from the lines that look something like this:

```

# if [ -f ~/.bash_aliases ]; then
#     . ~/.bash_aliases
# fi

```

Then open up (or create, if necessary) ~/.bash_aliases and add your aliases.

```

alias example="command you want to alias"

```

+1 ! Using bash_aliases is considered to be the "better solution"

---

### Post by lance bermudez on 2008-08-11
I'm a little confussed over this. Do I edit the ~/.bashrc file by removing the # from
# if [ -f ~/.bash_aliases ]; then
#     . ~/.bash_aliases
# fi
then do i create a file called ~/.bash_aliases with my aliases in it? If so then how do create the new file ~/.bash_aliases? How do I enter the aliaes? I know the command alias example=command you want to alias. Could you provide an example please. Also thank you all for the help you have given so far.

---

### Post by schauerlich on 2008-08-11
Yes. Find those lines in your ~/.bashrc and remove the # sign from the beginning of the lines. This is called "uncommenting." Now start up gedit or whatever text editor you like and save a file called .bash_aliases in your home folder. Then, just add your aliases in the file named ~/.bash_aliases. In order for the changed to take affect, you will need to restart bash. The easiest way to do this is to close the terminal you have open and open it up again.

---

### Post by lance bermudez on 2009-04-25
I have avg 8.5 installed in the ~/.bash_aliases I have

alias update='sudo apt-get update'
alias upgrade='sudo apt-get upgrade'
alias home='cd /home/lance'
alias documents='cd /home/lance/Documents'
alias downloads='cd /home/lance/downloads'
alias openline='cd /home/lance/MyDownloads'
alias shared='cd /home/lance/Shared'
alias whereami=pwd
alias whereareyou=pwd
alias where=pwd
alias whoareyou=whoami
alias full=´avgscan -H /home/lance´
alias update2=´sudo avgupdate -p 2´

the last two error out with
lance@bermudez:~$ update2
bash: ¨sudo: command not found
lance@bermudez:~$ full
bash: ´avgscan: command not found

but if I type in the whole command in the command line the command works. What am i doing wrong?

---

### Post by schauerlich on 2009-04-25
It looks like you're using ticks (´) instead of quotation marks ("). Change your alias so it's using quotation marks, restart bash (close and reopen the terminal), and try again.

By the way, it's recommended to start a new thread when you have a new problem, even if it's on the same topic. Just a friendly reminder. :)

---

### Post by MrWES on 2009-04-25
> **lance bermudez said:**
> I have avg 8.5 installed in the ~/.bash_aliases I have

alias update='sudo apt-get update'
alias upgrade='sudo apt-get upgrade'
alias home='cd /home/lance'
alias documents='cd /home/lance/Documents'
alias downloads='cd /home/lance/downloads'
alias openline='cd /home/lance/MyDownloads'
alias shared='cd /home/lance/Shared'
alias whereami=pwd
alias whereareyou=pwd
alias where=pwd
alias whoareyou=whoami
alias full=´avgscan -H /home/lance´
alias update2=´sudo avgupdate -p 2´

the last two error out with
lance@bermudez:~$ update2
bash: ¨sudo: command not found
lance@bermudez:~$ full
bash: ´avgscan: command not found

but if I type in the whole command in the command line the command works. What am i doing wrong?


```
alias aka='cat ~/.bash_aliases | grep alias'

```

Nice little alias; type aka to get a nice list of your current aliases.

Bill

---

### Post by lance bermudez on 2009-04-26
i have moved my new problem to [http://ubuntuforums.org/showthread.php?p=7154866#post7154866](http://ubuntuforums.org/showthread.php?p=7154866#post7154866) please take a look. and also thank you for your help.

---

