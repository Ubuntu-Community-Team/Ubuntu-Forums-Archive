---
title: "HOWTO: Application launchers with File Selection Tool"
date: 2008-07-16
forum: Outdated Tutorials &amp; Tips
---

### Post by the_it on 2008-07-16
[SIZE="5"]**Problem statement:**[/SIZE]
I am a writer working on various kinds of text files. Because of this, I put an application launcher on my panel to shortcut to launching text. HOWEVER...

The normal process of opening a program either from the menu or from an application shortcut involves
[LIST=1]
[*]Opening the program
[*]Invoking the "open file" command in the program
[*]Hunting for your file in the file-selection utility
[/LIST]

This is a waste of time for me, and I finally was fed up. The ordinary unix way to do things was to open the program with the filename in mind in a single step. Doing things the GUI way was painful and annoying. So I thought to edit my menu item to add a file-selection utility, and here's how I did it.

My system is a 64-bit Hardy Heron running GNOME, but it should work for any version of ubuntu and any Desktop in general.

If you want to just read a quick summary, then look scroll to the bottom of this post or press ctrl+F then type "Phew!"

[SIZE="5"]**Solution:**[/SIZE]
It's a very simple idea. Just add an application launcher to your panel. That application launcher should invoke a command that opens a file dialog. The file dialog is called zenity.

First, make sure that you have zenity. Open a terminal and install zenity from the repos.
```
sudo aptitude install zenity
```

Zenity is a convenient command-line utility for opening graphical dialogs with the user. You can check how to use it from its manual page.
```
man zenity
```

In my examples below, I use the gvim editor. You don't need to use it just to be able to follow what I'm doing, but if you want to do exactly as I do, then you can go ahead and install it too.
```
sudo aptitude install vim-gnome
```


=====
Today, we're just interested in asking for an "open file..." dialogue with the application launcher. However, this involves some funky magic with quoting your commands. For you to understand what this means, I'll explain each step before giving the final command.

First, I'll show you how to open a file dialogue with zenity. This is how it's done:
```
zenity --file-selection --title "Open file"
```
The code above will open a file selector window with the title "Open file". When you select a file or type in a filename, you'll see it echoed on your terminal. But this isn't what we need. We need to tell another program to use the filename we selected. So we need to send that output to another command.

This output is normally sent to other commands in this way:

```
gvim "`zenity --file-selection --title \"Open file with gvim...\"`"
```
In the command above, I run the gvim editor from the command line. However, before running vim, a graphical dialogue will first appear and ask me what file I want to open. Upon selecting a file (or typing a filename, the file is opened in gvim. You'll notice that the quotes quickly become convoluted. They are explained below:
[LIST]
[*]pay close attention to the use of the ` character (backtick) to enclose the entire zenity command. This is a backtick - it is a different character from the single quote and can usually found to the left of the number 1 on a qwerty keyboard. The backtick tells the shell to put the output of the command in its place. That means everything between the two `` characters becomes substituted with the filename you select. Logically, the command looks like
```
COMMAND "`zenity-command`"
```
and upon execution, gets transformed into
```
COMMAND "`zenity-command-output`"
```
[*]notice that the backticks are themselves are enclosed in double quotes. Why? because filenames sometimes have spaces in them. If the filenames with spaces are passed to the command, then the command will think you want to open multiple files.
[*]Notice that the "Open file with gvim" is enclosed by backslash-double-quotes (\") and not double-quotes. The whole string is just a single argument to the --title command of zenity. Logically, the command looks like this:
```
zenity --file-selection --title "TITLE"
```
Where TITLE is anything you want. In our case above, TITLE is backslash-double-quoted instead of just double-quoted because we don't want to interfere with the double quotes already surrounding the whole zenity command.
[/LIST]

Still able to follow? Good. That's **not** the final command just yet. ;p

Normally, that command will work on the command-line. This is because the default command-line, bash, has advanced features that tell it to use the backtick character as a substitution rule. However, if we plug that command in to a Graphical Application Launcher, it won't always work. Why? Because not all Graphical Application Launchers doesn't use bash! For the command above to work on an application launcher, you should explicitly invoke bash first, just to be sure. So the command you need to pass to the application launcher is actually:
```
bash -c 'gvim "`zenity --file-selection --title \"Open file with gvim...\"`"'
```
Yes, please pay attention to the nesting of the ", `, and ' characters. Dont exchange them.
[LIST]
[*]the ' is used to enclose the argument to bash -c
[*]the " is used to enclose the backtick command, which is zenity
[*]the ` is used to enclose the zenity command
[*]the \" is used to enclose the argument to the --title command
[/LIST]

Actually, that's not even done yet!

Programs have a "current working directory" where they live. When they perform operations, open files, etc etc, they usually perform those actions from within the current working directory. If you've ever opened files from the command line, then you might be familiar with doing something like the following:
```
cd somedirectory
vim somefile
```
If you are running vim, and you open somefile, then vim is running under the directory somedirectory. If you change the filename and save it as anotherfile, then you'll have the ff files:
somedirectory/somefile
somedirectory/anotherfile 

By contrast, opening a program as we did above with the bash string is equivalent to running the following command
```
vim somedirectory/somefile
```
By default, your working directory is your home directory. If you change the filename and save it as anotherfile, then you'll have the ff files:
somedirectory/somefile
anotherfile

Which is different from our expected behavior! So what you really want is to (1) change into the directory of the file, and (2) THEN you open that file.  All while nested in a bash command that nests a command with a zenity string containing a quoted title. If it makes your head hurt, don't think about it. Just look at the command below:

```
bash -c 'PROGNAME="gvim";FULLPATH="`zenity --file-selection --title \"Open with $PROGNAME...\"`"; cd "`dirname \"$FULLPATH\"`"; $PROGNAME "`basename \"$FULLPATH\"`"'
```
Phew! You can plug the command above into an application launcher now. Here's how to do it:
[LIST=1]
[*] Copy the string above into a text editor
[*] Find out the name or full path of the command you want. For example, the gnome text editor is called gedit. The KDE text editors are kate and kwrite. Openoffice Writer is called oowriter.
[*] Replace gvim in the string PROGNAME="gvim" with the name of a command you'd like to use (for example, gedit, or oowriter).
[*] Right click on your panel.
[*] Add to Panel -> Custom Application Launcher (or select an application launcher, then right click and edit the properties)
[*] Paste your new command into the "Command" item.
[*] click Close
[*] Test the command by clicking the button.
[*] A file dialogue has to appear. After selecting a file, your program will then open with the file loaded in.
[/LIST]

[SIZE="5"]Possible problems[/SIZE]
**I click the button but nothing happens** OR
**I click the button and a dialogue appears, but my program doesn't run** OR
**basically, anything else**
There's a typo somewhere. Try pasting your command into a command line first and seeing if there's an error.

For your convenience, please don't type out the command by hand. Just copy paste it.

Comments? Suggestions? Other problems? Post here.

---

