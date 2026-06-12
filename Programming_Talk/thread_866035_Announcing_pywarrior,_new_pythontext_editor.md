---
title: "Announcing pywarrior, new python/text editor"
date: 2008-07-21
forum: Programming Talk
---

### Post by Torajima on 2008-07-21
Released a new version (1.04)
Fixes a nasty little bug that sometimes caused the program to crash when loading small files.

You can download the zip file [HERE]("http://www.mindspring.com/~torajima/pywarrior/pywarrior.zip").
Or download the tar.gz file [HERE]("http://www.mindspring.com/~torajima/pywarrior/pywarrior.tar.gz").
Additional images [HERE]("http://www.mindspring.com/~torajima/pywarrior/other_images/").
--------------------------------------------

ABOUT PYWARRIOR

Pywarrior is a terminal based python editor and text editor which features:

1. Color support (both Linux & Mac)
2. Syntax highlighting
3. Automatic debugging
4. Comment formatting
5. Inline commands - no separate read/write modes!
6. Built-in help function - similar to help() in the python interpreter
7. Splitscreen mode
8. A 'run' command - test code before saving it
9. The ability to save encrypted files

REQUIREMENTS

Linux or Macintosh with Python 2.5 (or higher) and ncurses installed.

INSTALLATION

1. Download pywarrior and unzip if necessary.
[http://www.mindspring.com/~torajima/pywarrior/pywarrior.zip]("http://www.mindspring.com/~torajima/pywarrior/pywarrior.zip")

2. Open the terminal and move to whatever directory contains pywarrior.
   For example, if pywarrior was on the desktop you would type 'cd ~/Desktop'
   in the terminal and press [enter].

3. If pywarrior has a '.py' extension, rename the file.
   To view files: type 'ls' and press [enter].
   To rename file: type 'mv pywarrior.py pywarrior' and press [enter].

4. Now type 'chmod 755 pywarrior' and press [enter].
   This makes pywarrior executable, and you can launch it by entering
   './pywarrior'

5. To fully install, copy the executable file to somewhere in your path
   Example: 'sudo cp pywarrior /usr/bin'

You should now be able to launch pywarrior by typing 'pywarrior' 
in the terminal.

**[COLOR="DarkRed"]Enter 'pywarrior -h' to open the help guide and see a list of commands.[/COLOR]**

SCREENSHOTS
[IMG]http://www.mindspring.com/~torajima/pywarrior/pywarrior_screen7.jpg[/IMG]

[IMG]http://www.mindspring.com/~torajima/pywarrior/other_images/pywarrior_monochrome.jpg[/IMG]

[IMG]http://www.mindspring.com/~torajima/pywarrior/other_images/pywarrior_help_function.jpg[/IMG]

---

### Post by sp0nge on 2008-07-21
Looks to be worth playing with. Thanks for the post!

---

### Post by Torajima on 2008-07-21
> **sp0nge said:**
> Looks to be worth playing with. Thanks for the post!

Let me know if you find any bugs... especially one that causes a crash!

---

### Post by -grubby on 2008-07-21
Wow, that's the nicest CLI editor I've seen (that's easy to use, yes I know, vim, just don't go there, I don't want to learn vim).

---

### Post by rlameiro on 2008-07-21
I liked it very much :) Congrats!

I will try to use it sometimes.

---

### Post by Torajima on 2008-07-21
I just updated the version to 1.2.

It fixes a bug that would cause a crash if you attempted to open a file which you did not have permission to access.

You can download it from the links above.

---

### Post by Torajima on 2008-07-21
> **nathangrubb said:**
> Wow, that's the nicest CLI editor I've seen (that's easy to use, yes I know, vim, just don't go there, I don't want to learn vim).

Thanks!

And that's one of the reasons I wrote pywarrior, I didn't like 'vi' type editors that had separate read/write modes.

---

### Post by WW on 2008-07-21
Could you explain a few things?

To save a file, I press ctrl-e and then type "save".  Is there a shorter way?  I'd really prefer a simple ctrl-s.

The help file says something about entering a command in a blank line, but I don't understand what it is talking about.  Where can I enter a command?  What blank line?

---

### Post by Torajima on 2008-07-21
> **WW said:**
> Could you explain a few things?

To save a file, I press ctrl-e and then type "save".  Is there a shorter way?  I'd really prefer a simple ctrl-s.

The help file says something about entering a command in a blank line, but I don't understand what it is talking about.  Where can I enter a command?  What blank line?

You can type commands right in the editor, on any blank line and press [enter] to execute. 

If you're using color, executable commands will be highlighted in red (see the third picture above).

And I couldn't use control-s, as I believe it's already used by the Gnome Terminal. I might be able to add another shortcut though. Maybe control-w, as in 'write'?

---

### Post by Sockerdrickan on 2008-07-21
the line you get when you actually press CTRL+E? well cli aps arn't supposed to act like your average GTK2 app so I wouldn't hope for CTRL+S

---

### Post by WW on 2008-07-21
> **Torajima said:**
> You can type commands right in the editor, on any blank line and press [enter] to execute. 

OK, I see.  Thanks.

---

### Post by Torajima on 2008-07-21
> **Tux0r said:**
> the line you get when you actually press CTRL+E? well cli aps arn't supposed to act like your average GTK2 app so I wouldn't hope for CTRL+S

You don't need to press CTRL-E first, unless you've changed the settings or opened pywarrior in text mode.

Normally you can type a command on ANY blank line. If there aren't any blank lines, hit the down arrow, and one will be created.

---

### Post by Torajima on 2008-07-22
> **WW said:**
> 
To save a file, I press ctrl-e and then type "save".  Is there a shorter way?  I'd really prefer a simple ctrl-s.

I just released a new version. You can access the save window by pressing control 'w'.

---

### Post by escapee on 2008-07-22
Haven't played with it much, but I just wanted you to know that color support is working just fine on Mac OS X.  Should be noted I do have colors enabled in my .bash_profile.

[IMG]http://i13.photobucket.com/albums/a264/machuga/pywarriorcolors.png[/IMG]

---

### Post by Torajima on 2008-07-23
> **escapee said:**
> Haven't played with it much, but I just wanted you to know that color support is working just fine on Mac OS X.  Should be noted I do have colors enabled in my .bash_profile.

What version of OS X are you using?

And what did you type to enable it?

Thanks!

---

### Post by WW on 2008-07-23
Color works for me, too.  Mac OS X 10.4, Python 2.5.2.  $TERM is "xterm-color".

---

### Post by -grubby on 2008-07-23
Ok, perhaps you should put setting in another convienent file? I don't like going through hundreds of lines of code to edit some settings..

---

### Post by Torajima on 2008-07-23
> **nathangrubb said:**
> Ok, perhaps you should put setting in another convienent file? I don't like going through hundreds of lines of code to edit some settings..

Most settings can be changed within the program, just remember to use the 'saveprefs' command afterwards (else you'll lose your changes when you quit).

But yes, you can edit the preference file directly.

On Linux, it's a hidden file in your home directory called '.pywarrior_prefs'

On Mac, it's located in your preference folder, and is named 'pywarriror'

---

### Post by escapee on 2008-07-23
> **Torajima said:**
> What version of OS X are you using?

And what did you type to enable it?

Thanks!

No prob at all.  You did great work on the app (and made it Mac friendly) so I'm pretty happy about that.

I'm running Leopard and my colors are enabled via:
```
export CLICOLOR=cons25
```

It'd work with "CLICOLOR=1" as well, but I just left it as is after I set it.

---

### Post by Torajima on 2008-07-25
Okay, I figured out the easiest way to make color work on the Macintosh.

Just open Terminal Preferences and change 'xterm' to 'xterm-color'.

[IMG]http://www.mindspring.com/~torajima/pywarrior/terminal_settings.jpg[/IMG]

You may have to manually start color in pywarrior (use the -c or --color flag before launching, or 'color on' command after launching).

---

### Post by nvteighen on 2008-07-25
Hey, really nice!

And surprisingly intuitive... "save", "quit", "read"...

But a question: I saved a filed called "a", and then pywarrior's "explorer" (:p) couldn't find it. It just shows .txt files. And I got ocassional crashes loading a simple text file...

---

### Post by Torajima on 2008-07-25
> **nvteighen said:**
> Hey, really nice!

And surprisingly intuitive... "save", "quit", "read"...

Thanks!

> But a question: I saved a filed called "a", and then pywarrior's "explorer" (:p) couldn't find it. It just shows .txt files. 

This is actually a feature. To simplify navigation, pywarrior only shows files with certain extensions (".txt", ".py", ".cpp", ".sh", etc.)

But if you press period ('.') it shows all files, including hidden ones.

> And I got ocassional crashes loading a simple text file...

Obviously, this shouldn't be happening. Pywarrior can only understand normal USA ascii characters, but it performs a check for illegal characters before attempting to open any file. It should be giving you a warning, rather than crashing.

Can you post a link to a text file that causes it to crash?

---

### Post by nvteighen on 2008-07-25
> **Torajima said:**
> 
This is actually a feature. To simplify navigation, pywarrior only shows files with certain extensions (".txt", ".py", ".cpp", ".sh", etc.)

But if you press period ('.') it shows all files, including hidden ones.

Ah! I see; But, wouldn't be less confusing to change the key binding? When I saw '.', I thought it was to see the hidden .dotfiles.

> 
Obviously, this shouldn't be happening. Pywarrior can only understand normal USA ascii characters, but it performs a check for illegal characters before attempting to open any file. It should be giving you a warning, rather than crashing.

Can you post a link to a text file that causes it to crash?

I attach you the file. It contains "Hello!\n\n" (8 bytes) and was written in PyWarrior. I've tested the hexdump against an identical text file written in Gedit, and there were no differences.

---

### Post by Torajima on 2008-07-25
> **nvteighen said:**
> Ah! I see; But, wouldn't be less confusing to change the key binding? When I saw '.', I thought it was to see the hidden .dotfiles.

Yeah, the key does double duty. I probably ought to explain that somewhere in the Help Guide.

> I attach you the file. It contains "Hello!\n\n" (8 bytes) and was written in PyWarrior. I've tested the hexdump against an identical text file written in Gedit, and there were no differences.

Thanks, I'll try to figure out what's going on.

---

### Post by Torajima on 2008-07-25
> **nvteighen said:**
> <snip> I got ocassional crashes loading a simple text file...

I just released version 1.04 which fixes this bug, thanks for pointing it out to me.

---

### Post by nvteighen on 2008-07-26
> **Torajima said:**
> I just released version 1.04 which fixes this bug, thanks for pointing it out to me.
Yes, it works! What was the bug, anyway?

---

### Post by Torajima on 2008-07-26
> **nvteighen said:**
> Yes, it works! What was the bug, anyway?

Short answer:

I did a lot of bug fixing before releasing pywarrior, and one of the fixes broke something else.

Long answer:

According to the PEP guidelines, a text string should be able to continue to the next line if it ends in '\'.
```
print "hello \
world"
```

But pywarrior wasn't properly handling this, so I added a check to see if the previous line of text ended in '\'.

Files that are one line long don't have a "previous line", hence the bug.

Now, there was second component to the bug which I don't entirely understand yet, but fortunately the 'fix' seems to take care of that as well.

---

### Post by nvteighen on 2008-07-26
> **Torajima said:**
> 
Files that are one line long don't have a "previous line", hence the bug.

Obvious... after you have found it. Nice bug catching!

---

### Post by Torajima on 2008-08-04
After discovering iWeb on my Macbook, I decided to create a new website for pywarrior.

[http://www.mindspring.com/~torajima/pywarrior]("http://www.mindspring.com/~torajima/pywarrior")

It looks loads better than the old one.

---

