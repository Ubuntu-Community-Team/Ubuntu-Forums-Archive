---
title: "Alias command"
date: 2014-10-11
forum: New to Ubuntu
---

### Post by marino4 on 2014-10-11
Hello!
Im new to "alias" command and i know how to use it i made a alisas to run my game...

alias amnesia='cd [file directory here] ; ./Launcher.bin'

And i restarted my terminal and it did not exist so now here is my question...

How do i save my aliases?

Thanks in advance!

---

### Post by sudodus on 2014-10-11
A simple way to save them is to edit your ~/.bashrc file.

Add a line with your alias below the lines that already contain aliases

```

...
alias ll='ls -l'
alias la='ls -A'
alias l='ls -CF'
alias amnesia='cd [file directory here] ; ./Launcher.bin'
...

```

---

### Post by oldos2er on 2014-10-11
Put them in ~/.bashrc, or if you have a lot of them they can go in their own file ~/.bash_aliases

---

### Post by marino4 on 2014-10-11
Ok people i was using Windows and im kinda new to shell comands sooo...will you mind making a bit detailed tutorial?

---

### Post by marino4 on 2014-10-11
And how do i acess ~/.bashrc

---

### Post by sudodus on 2014-10-11
***In a terminal window***, run the following command (and finish the line with the Enter key)

```
nano ~/.bashrc
```

or if you have standard Ubuntu

```
gedit ~/.bashrc
```

---

### Post by deadflowr on 2014-10-11
FYI, you can also put them in a file named .bash_aliases.
If you want.
I usually, do. It's easier for me to find them, since the file only has aliases, and no other settings.

---

### Post by vasa1 on 2014-10-11
> **oldos2er said:**
> ... if you have a lot of them they can go in their own file ~/.bash_aliases
It's also safer. Avoids the risk of messing up .bashrc.

---

### Post by Dennis N on 2014-10-11
Another useful thing  to know is that once you have your aliases defined in one of those two files, just typing **alias** at the command prompt will show a list of all defined aliases. You can then just copy and paste the one you want after the command line prompt.

---

### Post by marino4 on 2014-10-11
Where is .bash_alises?

---

### Post by whitesmith on 2014-10-11
It may not exist on your system, depending on configuration. Linux allows aliases to be in any of these locations:
/etc/profile
~/.bashrc
and ~/.bash_profile
Note that /etc/profile is outside your home directory, so you probably won't be able to write to it (nor should you, most likely) without going through sudo.

---

### Post by nerdtron on 2014-10-11
> **marino4 said:**
> Where is .bash_alises?

It doesn't exist by default. And saving any file with a period (.) on the beginning will make the file hidden.
You can create the file using any text editor, save it as .bash_aliases and is save on your home folder /home/username
Same as the .bashrc and .bash_profile. Show hidden files to see the files.

It doesn't matter which of the 3 files you put your aliases (although there are technical differences of course). Logout and login again for changes to take effect.

---

### Post by marino4 on 2014-10-11
Well overall the point was that Im too lazy to type all that stuff so is there any way to make an executable file to automaticly run a command without using Ubuntu SDK (No C++ or HTML5)

---

### Post by nerdtron on 2014-10-11
> **marino4 said:**
> Well overall the point was that Im too lazy to type all that stuff so is there any way to make an executable file to automaticly run a command without using Ubuntu SDK (No C++ or HTML5)

Yup. That's what the aliases are for. I have some aliases too.

---

### Post by marino4 on 2014-10-12
> **nerdtron said:**
> Yup. That's what the aliases are for. I have some aliases too.

Yea but i was aming for something more like .exe file for Windows an executable or a shortcut...

---

### Post by nerdtron on 2014-10-12
> **marino4 said:**
> Yea but i was aming for something more like .exe file for Windows an executable or a shortcut...

Hhhmmm.. So shortcut you say? They are called Links in Ubuntu/Ubuntu. So your original command is this right?

```
alias amnesia='cd [file directory here] ; ./Launcher.bin' 
```


[LIST=1]
[*]Right click the file you want a link to in your file manager.
[*]Select "Create link" from the context menu.
[*]Move that link wherever you want it.
[/LIST]

---

