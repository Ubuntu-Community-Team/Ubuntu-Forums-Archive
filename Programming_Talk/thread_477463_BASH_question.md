---
title: "BASH question"
date: 2007-06-18
forum: Programming Talk
---

### Post by TheBuzzSaw on 2007-06-18
I run Ubuntu 7.04.

I am toying around with the alias command that lets you make console shortcuts. This is a wonderful tool, but I have a problem: I cannot execute the alias command if it is inside a 'sh' script file. It works at school in the Linux Lab (they run Red Hat). I made a very very simple test file called "test.sh".

alias bob='ls'

If I type test.sh, it executes, but the bob command does not work. If I type that line of code directly into the console then the bob shortcut works just fine.

Help!!!

---

### Post by tr333 on 2007-06-18
when you run "test.sh", you are executing the test.sh script.  once the script has finished, any changes you made inside the test.sh script are lost.  if you want to make the alias permanent, then place it inside the ~/.bashrc file.  this file is parsed each time bash is started.  similarly, the ~/.bash_profile is parsed once per system login, and the ~/.bash_logout file is parsed when you exit the bash shell.

---

### Post by AdamG on 2007-06-18
If you want to "run" the test.sh to have effects in your current shell, just run "source test.sh" and your alias will work for as long as your shell is running. Like tr333 said, you'll want to put it in your ~/.bashrc if you want to have it permanently.

---

### Post by s1ightcrazed on 2007-06-18
I believe that you can also do:

```
$ . test.sh
```

That would be 'dot - space - test.sh'

This should parse the file and set environment. 
I think.

---

### Post by dustigroove on 2007-06-18
[FONT=Arial][SIZE=2][COLOR=Black]Out of curiosity... is there benefit to putting ones aliases directly into *.bashrc* versus entering them into *.bash_aliases* and uncommenting the section in .bashrc to source that file?


[/COLOR][/SIZE][/FONT]

---

### Post by s1ightcrazed on 2007-06-18
If you come to a point when you DON'T want the aliases to run you can just:

```
$ chmod 660 .bash_aliases
```

to remove executable perms. If you put it all in bashrc then you have to vi the file and comment them out. Some may find one method preferable over the other.

---

