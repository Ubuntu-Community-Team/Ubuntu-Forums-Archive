---
title: "noob"
date: 2007-05-27
forum: Programming Talk
---

### Post by yawningdog on 2007-05-27
I just started to write python code today. I wrote a script and saved it to my desktop. I want it to run when I double-click it, but it just opens it in a text editor. How do I fix this?

---

### Post by earobinson on 2007-05-27
you need to make the script executable, this can be done with a ```
chmod +x <file name>
``` ```
man chmod
``` for more info, or right clicking the file going to its properties then setting the file to executable.

Edit: you may want to edit the title of your post to be a bit more informing than "noob"

---

### Post by Bachstelze on 2007-05-27
Also, be sure the first line of your script says :

```
#!/usr/bin/env python
```

so the system know which interpreter it's supposed to run the script with.

---

### Post by Znupi on 2007-05-27
Also, unless you made a program that uses GTK, you will probably have to run it from the terminal:
```

~/Desktop$ ./script.py

```
:)

---

### Post by earobinson on 2007-05-27
Ubuntu will ask the user if they would like to run the program from the terminal or not AFAIK

---

### Post by yawningdog on 2007-05-27
Thanks everybody.

The permissions mod makes sense and I should have thought of that. I'm not exactly a Linux/Unix noob, but I am a python noob. I have a feeling this thread is going to span several subjects, thus the non-specific title.

It's not a shell script I've written, but a .py script (if that's the right terminology), so I don't think I need to state the path explicitly. Correct me if I'm wrong. The talk about GTK might as well be greek for all I get it. 

Anyway, the program seems to run now, but I don't see any output anywhere. Here is my code.```
# Game over
# Demonstrates the print command

print "Game over"
raw_input("\n\nPress the enter key to exit.")
```

Do I associate this with an RE somewhere to get output displayed?

---

### Post by earobinson on 2007-05-27
> **yawningdog said:**
> Thanks everybody.

The permissions mod makes sense and I should have thought of that. I'm not exactly a Linux/Unix noob, but I am a python noob. I have a feeling this thread is going to span several subjects, thus the non-specific title. Glad to help, Nothing wrong with making more than one thread IMO  as long as they are different subjects

> **yawningdog said:**
> It's not a shell script I've written, but a .py script (if that's the right terminology), so I don't think I need to state the path explicitly. Correct me if I'm wrong. The talk about GTK might as well be greek for all I get it.  I think at one point you needed the #! since this translates into a magic number that *nix uses to figure out what kind of file (yes a program is a file) it is dealing with, but the rules on magic numbers seem to be more gray than they used to be.

Edit: nope you need the magic number "#!/usr/bin/env python"

> **yawningdog said:**
> Anyway, the program seems to run now, but I don't see any output anywhere. Here is my code.```
# Game over
# Demonstrates the print command

print "Game over"
raw_input("\n\nPress the enter key to exit.")
```

Do I associate this with an RE somewhere to get output displayed? I figured when you double clicked the file a gui would pop up asking you if you wanted to run it in the terminal and you would click "run in terminal" since your outputting to standard out the program needs to be ran in some kind of shell in order for you to see the output.

---

### Post by Znupi on 2007-05-27
Are you simply double-clicking on the file and choosing "Run in Terminal"? If yes, take HymnToLife's advice. If you don't want to add that line, you can open up a terminal, cd into the directory with the file, and use
```

python file.py

```
When running files, in Linux it doesn't matter what the file's extension is.

---

### Post by yawningdog on 2007-05-27
When double-click the icon and select the "run in terminal" option, the terminal won't stay up even long enough to see the message. If I just click the "run" option, I don't even get that.

I bought a book which apears to teach python programming from a Windows angle, and not very well at that.

---

### Post by Znupi on 2007-05-27
Have you read my post? :| Just add
```

#!/usr/bin/python

```
To the top of your file.

---

### Post by yawningdog on 2007-05-27
I tried adding```
#!/usr/bin/env python
``` That didn't work. I then tried adding ```
[CODE]#!/usr/bin/python
```[/CODE] That didn't work either.

These entries show up as comments in the IDLE editor, owing to the # I suspect. SHould I remove that?

---

### Post by Znupi on 2007-05-27
I recommend that you don't use IDLE (I just tried it and it really sucks...), use gedit.
But, there's a slight problem, are you sure you have python installed? What's your Ubuntu version? What happens if you run:
```

python -V

```
?

---

### Post by yawningdog on 2007-05-27
Python is installed, I promise. It's installed by default in fact. The problem isn't with IDLE, which seems to work fine so far. If I want to use a different text editor, I'm pretty handy with VI. That's not the problem. I can run the program by opening IDLE in script mode and running the module. I want to run the .py file by double-clicking an icon. A shell window appears to pop up, but closes immediately. If you really must know the version to help out, it's 2.4.3.

And so far, two fixes have been suggested which, strictly interpreted, amount to nothing more than comment code. Sombody please clarify this for me.

---

### Post by Znupi on 2007-05-27
Open a terminal, cd into the directory with the script, and type:
```

./<script-name>

```
What's the output?

---

### Post by yawningdog on 2007-05-27
Someone beside Znupi please...

---

### Post by earobinson on 2007-05-27
> **yawningdog said:**
> Someone beside Znupi please...
Znupi is dead on correct

> **Znupi said:**
> Open a terminal, cd into the directory with the script, and type:
```

./<script-name>

```
What's the output?

Could you post an answer to this, maybe post the program your trying to run so I can run it here?

---

### Post by Znupi on 2007-05-27
> **earobinson said:**
> maybe post the program your trying to run so I can run it here?
He already did.
[QUOTE=yawningdog]Someone beside Znupi please...[/QUOTE]
Please excuse me for contributing in a community...

---

### Post by earobinson on 2007-05-27
> **Znupi said:**
> He already did. He posted ```
# Game over
# Demonstrates the print command

print "Game over"
raw_input("\n\nPress the enter key to exit.")
``` That can be the whole program, + he should now have the #! at the start.

I was hoping that the file would get posted

---

### Post by Znupi on 2007-05-27
That **is** the whole program. It works perfect for me if I use from the terminal
```

python <script-name>

```
Of course, it doesn't work by double-clicking and choosing **Run in Terminal**, but this works, of course:
```

#!/usr/bin/python
# Game over
# Demonstrates the print command

print "Game over"
raw_input("\n\nPress the enter key to exit.")

```

---

### Post by yawningdog on 2007-05-27
Fine. 
./Game_over.py produces
```
Warning-unknown mime-type for "Game over" -- using "application/*
Error: no such file "Game over"
./game_over.py: Line 6: syntax error near unexpected token '"\n\nPress the enter key to exit."'
./game_over.py: Line 6: 'raw_input("\n\nPress the enter key to exit.")'

```

All the programs I've written in C++ run using this convention. But this is not a program, it's a script. I didn't expect the ./ instruction to work because of this. so far, I'm right.

Don't take it personal Znupi.Yes, it works from the command line. But I have users who cannot manage a command line and aren't interested in learning it. I have to give them an icon they can double-click, or they will fight a linux migration tooth and nail. So...

...for the third time. Is there any way I can get this program to work by double-clicking an icon. I think it's running, but the window doesn't stay up.

And does anyone care to speak to the fact that the solutions suggested are, as far as i can tell, simply comments. Comments always start with #. Am I right about this, or am I wrong?

---

### Post by FuriousLettuce on 2007-05-27
About the 'comments', it's called a shebang line - check [http://en.wikipedia.org/wiki/Shebang_(Unix)](http://en.wikipedia.org/wiki/Shebang_(Unix)). 

In addition, you might find that people are more forthcoming when you don't come across so badly. The "someone else apart from Znupi" comment doesn't serve any purpose, he was right on about what he was saying. 

Make sure that the script is executable:
```
chmod +x script.py
```
and make sure that you have python-dev installed. 

If you want an icon, right click on the desktop, choose "create launcher". At the top choose "application in terminal", then name the shortcut, and give the absolute path to the file (e.g., /home/user/script.py rather than ~/script.py). You can now double-click this icon and it will work fine. If you go into the launcher properties you can also change the icon itself.

---

### Post by Znupi on 2007-05-27
If adding
```

#!/usr/bin/python

```
to the top of your file (the very first line, before any comments or anything, the **first**) doesn't work, there's something wrong with your python. It works excellent for me, by clicking "Run in Terminal".

A bit of explanation: by adding this line, that starts with #!, it (the line) will never reach the python interpreter. It will be taken by the shell interpreter, so it knows what to use to interpret it. In this case: python, which **should** be located in **/usr/bin/python**. If it's not there, and you know where it is, change that line to **#!/path/to/python**.

---

### Post by FuriousLettuce on 2007-05-27
/usr/bin/env contains a list of a lot of environment variables, one of which is the path to the python interpreter. That's why people put
```
#/usr/bin/env python
```
at the top of the scripts - it makes them more portable. Not all systems have python in /usr/bin (it might be in /bin or whatever), but almost all systems (meaning distros, flavours of UNIX etc) place env in /usr/bin, making the code more portable. 

Aside: env is a runnable binary - just type in /usr/bin/env to see what kind of info it contains.

As Znupi mentions, the shebang line (see my previous post) tells the terminal what program to use to run the file, otherwise it attempts to interpret the python code itself, and python is not valid bash code, so it will return errors. 

The other way to run it is to leave out the shebang line and do
```
python ./script.py
```
This will explicitly call the python interpreter to run the file. 

As Znupi said, if none of this works, your python install is messed up.

---

