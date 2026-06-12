---
title: "How to cd (change directory) on hidden files or folders?"
date: 2023-09-28
forum: New to Ubuntu
---

### Post by rifqilubis on 2023-09-28
I used konsole, and i wanna add files or folder to .minecraft folder.

but i wanna do it with konsole, like cd commands and mk commands. is it impossible to add folder to hidden folder?


im newbie.

---

### Post by MAFoElffen on 2023-09-28
In KDE Konsole File Manager, pressing the keys <Cntrl><H> are the hotkeys that toggles "view hidden file and folders".

---

### Post by guiverc on 2023-09-28
You use the cd & mkdir commands normally.

Use `cd` to change directory, eg.

```

cd .minecraft

```

will change directory to .minecraft which is a directory located within your present/current directory ($PWD).  You can use 

```

echo $PWD

```

to display where you are currently, though most of us have prompts ($PS1) that remind us where we are, with ~ short for our home directory (which is /home/$USER). The system keeps different details about us & where we are in variables we can actually use when we need to.

Your attempt at command was invalid, thus the error you received

```

/.minecraft~

```

did not include a command (no CD to change directory in front of it), and you didn't use the ~ to refer to a directory (you'll note I separated it above with a `/`) and used it in a location where it makes sense (your usage had it at the end, so your directory would have been expanded to .minecraft~ off the / or root directory with the directory named ".minecraft~" and not .minecraft.

Sorry the last paragraph may be confusing, key is it's

COMMAND *operand(s) options*

thus CD followed by where to change directory to.

---

### Post by rifqilubis on 2023-09-30
> **guiverc said:**
> You use the cd & mkdir commands normally.

Use `cd` to change directory, eg.

```

cd .minecraft
[/CODE

will change directory to .minecraft which is a directory located within your present/current directory ($PWD).  You can use 

[CODE]
echo $PWD

```

to display where you are currently, though most of us have prompts ($PS1) that remind us where we are, with ~ short for our home directory (which is /home/$USER). The system keeps different details about us & where we are in variables we can actually use when we need to.

Your attempt at command was invalid, thus the error you received

```

/.minecraft~

```

did not include a command (no CD to change directory in front of it), and you didn't use the ~ to refer to a directory (you'll note I separated it above with a `/`) and used it in a location where it makes sense (your usage had it at the end, so your directory would have been expanded to .minecraft~ off the / or root directory with the directory named ".minecraft~" and not .minecraft.

Sorry the last paragraph may be confusing, key is it's

COMMAND *operand(s) options*

thus CD followed by where to change directory to.


nice its working. i forgot the cd command. my bad. Thank you.

---

