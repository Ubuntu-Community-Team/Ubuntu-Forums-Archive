---
title: "Getting a program to show up in 'Applications' menu"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by ConMan318 on 2008-06-28
I installed Sauerbraten from their website (the new version, which isn't yet in the repos).  It works fine, except that I have to do something like:
```

cd ~/sauerbraten/sauerbraten/
./sauerbraten_unix

```

to run it.

How can I get it to be in my Applications > Games menu?  I am pretty sure I have to move it from my home directory into /bin or /usr/bin or something, but I've tried that and it didn't change anything.  I also can't add it from Applications > Add/Remove since it doesn't show up as an installed app since I unpacked it from a .tar file.

Also, I would like to be able to run it from the command line just by typing 'sauerbraten'.

Basically, I'm asking what Synaptic would have done with it had it been in the repositories, since it does all this automatically.

Thanks.

---

### Post by bubba_169 on 2008-06-28
- Right click the menu bar and choose edit menus
- Highlight the games menu on the left hand side
- Click the new item button
- Fill in the fields how you want except the command field which must be '~/sauerbraten/sauerbraten/sauerbraten_unix'
- Done, try your link...

To make it so you can run the command from the terminal, run this command:

```
sudo ln -s ~/sauerbraten/sauerbraten/sauerbraten_unix /usr/bin/sauerbraten
```

You should now be able to type 'sauerbraten' in the terminal to run it!

---

### Post by drs305 on 2008-06-28
> **ConMan318 said:**
> 
How can I get it to be in my Applications > Games menu?  


You can add it to your menu by right clicking on Menu, Edit, the click on Games and New Item. If it runs via gui, leave it as "application". If it runs in terminal, select "Application in Terminal". The command would be "~/sauerbraten/sauerbraten/sauerbraten_unix"

> 
Also, I would like to be able to run it from the command line just by typing 'sauerbraten'.


You can create an alias for that if you wish. To make an alias to start sauerbraten by typing "sb" in terminal:
```

alias sb="~/sauerbraten/sauerbraten/sauerbraten_unix"

```

Note - aliases won't take effect until you open a new terminal or run "source ~/.bashrc"

There is more to know about aliases but that should get you started.

**Added:**  You might be interested in this thread from this week:
[sauerbraten ctf]("http://ubuntuforums.org/showthread.php?t=841846")

---

