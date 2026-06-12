---
title: "commands"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by epicmono on 2008-07-02
i've installed a few softwares in ubuntu 7.10 how can i find out the commands that i can use to open those softwares from the terminal?

is there any kind of lists??

---

### Post by kuja on 2008-07-02
Well, if you remember the names of those packages, you could do this:

"dpkg -L <packagename> | grep bin"

---

### Post by tjwoosta on 2008-07-02
usually the command to open a file is the same as the name

(for instance  to open firefox the command is firefox)

this isnt always the case though

as far as i know there is no real list, you can just search google for the commands for your programs probably

---

### Post by scragar on 2008-07-02
normaly the command from the terminal is just the program name(ALWAYS lower case), if there's any you can't figure out list them.

you can also veiw the properties of the launchers in the menu(you have to right click and choose edit menu first :() to find the command.

---

### Post by epicmono on 2008-07-02
> **scragar said:**
> normaly the command from the terminal is just the program name(ALWAYS lower case), if there's any you can't figure out list them.

you can also veiw the properties of the launchers in the menu(you have to right click and choose edit menu first :() to find the command.

thanx man... it worked... :D

---

### Post by hyper_ch on 2008-07-02
and if you want to know how to use that command:

```

man COMMAND

```

---

