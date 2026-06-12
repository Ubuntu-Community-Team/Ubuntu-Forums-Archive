---
title: "Question on bin folder."
date: 2012-01-13
forum: New to Ubuntu
---

### Post by shizz on 2012-01-13
Ok so I thought I would try learn some bash scripting and after searching the forums I came across this website, [http://www.linuxcommand.org/wss0010.php](http://www.linuxcommand.org/wss0010.php)

I've successfully made the script and all is well, but when he said to move the script to the bin folder I moved it to the one in the File system not in my home folder. So naturally enough when I just put in "my_script" the command isn't found.

So basically what I am asking is, what is the bin directory in the file system and why would I need a separate one in my home directory for this?

---

### Post by MG&amp;TL on 2012-01-13
> **shizz said:**
> Ok so I thought I would try learn some bash scripting and after searching the forums I came across this website, [http://www.linuxcommand.org/wss0010.php](http://www.linuxcommand.org/wss0010.php)

I've successfully made the script and all is well, but when he said to move the script to the bin folder I moved it to the one in the File system not in my home folder. So naturally enough when I just put in "my_script" the command isn't found.

So basically what I am asking is, what is the bin directory in the file system and why would I need a separate one in my home directory for this?

Oh. You don't. :)

Do:

```
chmod +x my_script
sudo cp my_script /usr/bin/
my_script
```

Should do it. :)

IDK why /bin isn't working though. Should be. But /bin is system stuff, really. User program should go in /usr/bin/

---

### Post by shizz on 2012-01-13
Just to add to this, I made the new bin directory under my home folder but when I put in "my_script" in to the terminal the command still isn't found?

I must have to add the path for this I guess but why did he assume it would work?

---

### Post by shizz on 2012-01-13
> **MG&TL said:**
> Oh. You don't. :)

Do:

```
chmod +x my_script
sudo cp my_script /usr/bin/
my_script
```

Should do it. :)

IDK why /bin isn't working though. Should be. But /bin is system stuff, really. User program should go in /usr/bin/

So does the article mean a bin directory as a subdirectory to the usr directory and not the home?

---

### Post by MG&amp;TL on 2012-01-13
> **shizz said:**
> Just to add to this, I made the new bin directory under my home folder but when I put in "my_script" in to the terminal the command still isn't found?

I must have to add the path for this I guess but why did he assume it would work?

Your home folder will NOT work. :)

To find out which folders bash searches for your programs, run:

```
echo $PATH
```

---

### Post by MG&amp;TL on 2012-01-13
> **shizz said:**
> So does the article mean a bin directory as a subdirectory to the usr directory and not the home?

err...no, it means /bin, i.e. the bin/ folder in the root directory (the filesystem).

Great tutorial, btw, I learnt from that one.

---

### Post by nothingspecial on 2012-01-13
> **MG&TL said:**
> Your home folder will NOT work. :)

To find out which folders bash searches for your programs, run:

```
echo $PATH
```

It will if you add ~/bin to your $PATH

---

### Post by nothingspecial on 2012-01-13
Open a terminal and type

```
nano .bashrc
```

Put this at the end

```
PATH="$HOME/bin:$PATH"
```

Ctrl-O then enter to save, then Ctrl-X to close. Then source your .bashrc

```
. .bashrc
```

Now your bin directory in your $HOME is in your $PATH

---

### Post by MG&amp;TL on 2012-01-13
EDIT: ^^^ That way's better. :)

> **nothingspecial said:**
> It will if you add ~/bin to your $PATH

Yeah; sorry, I tell a lie. :)

You can do that by adding:

```
export PATH=$PATH:~/bin/
```

to your ~/.bashrc

---

### Post by shizz on 2012-01-13
Sorry guys ill come back to the discussion in a second but I was using the mv command to move the directories and I accidentily moved the file system bin to the usr bin. Now I can't open the terminal to rectify it and I can't copy it manually through nautilus as I don't have permission.

Any ideas?

---

### Post by nothingspecial on 2012-01-13
> **shizz said:**
> Sorry guys ill come back to the discussion in a second but I was using the mv command to move the directories and I accidentily moved the file system bin to the usr bin. Now I can't open the terminal to rectify it and I can't copy it manually through nautilus as I don't have permission.

Any ideas?

:shock:

Press Ctrl-Alt-F1 then log in and type

```
sudo mv /usr/bin/bin /
```

If that doesn't work you will have to boot a live cd and move it back from there.

---

### Post by shizz on 2012-01-13
> **nothingspecial said:**
> :shock:

Press Ctrl-Alt-F1 then log in and type

```
sudo mv /usr/bin/bin /
```

If that doesn't work you will have to boot a live cd and move it back from there.

Thanks man it worked. What is the Ctrl-Alt-F1 environment?

---

### Post by nothingspecial on 2012-01-13
It is running Ubuntu without a gui, you have tty1-6 then the Graphical Environment starts in tty7. So Ctrl-Alt-1-6 will switch you to a console :)

---

### Post by CharlesA on 2012-01-13
Unless something has changed, if you create a bin folder in your home directory, it is added to the $PATH variable automagically.

---

### Post by shizz on 2012-01-13
> **nothingspecial said:**
> It is running Ubuntu without a gui, you have tty1-6 then the Graphical Environment starts in tty7. So Ctrl-Alt-1-6 will switch you to a console :)

Ah ok. Thanks again. Anyway, in his article he says > "Most modern Linux distributions encourage a practice in which each user has a specific directory for the programs he/she personally uses. This directory is called bin and is a subdirectory of your home directory. If you do not already have one, create it with the following command:

So he assumed that there should be a bin directory in my home folder, which there wasn't, and that if I made one it shouldn't need to be added to the path.

---

### Post by nothingspecial on 2012-01-13
> **CharlesA said:**
> Unless something has changed, if you create a bin folder in your home directory, it is added to the $PATH variable automagically.

Because of this

```
# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
```

in your ~/.profile :)

---

### Post by shizz on 2012-01-13
> **nothingspecial said:**
> Because of this

```
# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
```

in your ~/.profile :)

I've done it all again and added the bin directory to my home and it seems to of added it to the path automagically :) Works now thanks guys.

---

### Post by nothingspecial on 2012-01-13
Great :)

Next time you solve an issue using the forums please use Thread Tools (at the top) to mark your thread solved.

I've done it for you this time :)

---

### Post by shizz on 2012-01-13
Sorry about that :).

---

### Post by nothingspecial on 2012-01-13
> **shizz said:**
> Sorry about that :).

No problem :p

---

