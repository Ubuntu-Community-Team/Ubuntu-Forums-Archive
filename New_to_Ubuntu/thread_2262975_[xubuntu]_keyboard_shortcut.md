---
title: "[xubuntu] keyboard shortcut"
date: 2015-01-28
forum: New to Ubuntu
---

### Post by flex567 on 2015-01-28
Is it possible to assing this command as a keyboar shortcut and how can I do that?

```

sleep 3; xset dpms force off

```

---

### Post by ajgreeny on 2015-01-28
Simply go to Settings-manager ->Keyboard and in the Application Shortcuts tab add a new shortcut in these steps
[LIST=1]
[*]Click Add button at bottom 
[*]Enter your above command for the shortcut in the dialogue box that pops up. 
[*]Click OK 
[*]Enter your chosen keypresses for the shortcut 
[*]That's it; all done.  Just watch for any conflicts of you chosen keypresses with any other previously chosen shortcut. 
[/LIST]

Just out of interest, why use **sleep 3;** when you can simply do this anytime you want using your shortcut?
What is the reason for wanting to stop dpms?

---

### Post by Holger_Gehrke on 2015-01-28
> **ajgreeny said:**
> 
Just out of interest, why use **sleep 3;** when you can simply do this anytime you want using your shortcut?
What is the reason for wanting to stop dpms?

'xset dpms force off' shut down the display and it comes back at a key press. That's why he wants the system to wait a moment, so he can take his hands off the keyboard ...

---

### Post by flex567 on 2015-01-30
@ajgreeny: this doesn't work. Try it and you will see.

---

### Post by Holger_Gehrke on 2015-01-30
> **flex567 said:**
> @ajgreeny: this doesn't work. Try it and you will see.

Of course it doesn't: it starts sleep and passes the rest of the line to it as parameters including the semicolon and everything after it. This tool doesn't do all the splitting and analyzing a shell would do. Just set the command as 'bash -c "sleep 3;xset dpms force off'"' and it works.

---

### Post by flex567 on 2015-01-30
so what should type in as the command
```
bash -c "sleep 3;xset dpms force off'"'
```
or
```
bash -c sleep 3;xset dpms force off
```
or something else

---

### Post by ajgreeny on 2015-01-30
I think you need the command ```
 bash -c "sleep 3; xset dpms force off"
```

Sorry, I didn't even think about the need to use the complex command when using keyboard shortcuts.
Yyou also need such commands when using a sleep time for autostart application commands in your session configuration; what it does is tell the configuration utility you are using, eg, keyboard shortcuts or autostart applications, to use bash to run the command between the quotation marks.

---

### Post by Holger_Gehrke on 2015-01-30
```

bash -c "sleep 3;xset dpms force off"

```

The bash expects **one** string after the the -c option. By putting it in quotes, you're making it obvious to the shell (and to yourself or whoever else might read it) that it's all one command. Otherwise the shell will only execute 'sleep' without any parameters (resulting in an error message in '~/.xsession-errors') and treat the rest as parameters to the shell.

---

### Post by flex567 on 2015-01-30
gr8, thanx, it seems like it works.

---

