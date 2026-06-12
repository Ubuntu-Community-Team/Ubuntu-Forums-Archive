---
title: "HOWTO: Persistent screen session in gnome terminal"
date: 2009-01-21
forum: Outdated Tutorials &amp; Tips
---

### Post by alegir on 2009-01-21
**[SIZE="5"]Introduction[/SIZE]**

This tutorial describes how to get a persistent [GNU Screen]("http://www.gnu.org/software/screen/") session in the gnome-terminal. 

The session is persistent in the sense that every gnome-terminal you open will open in to the same screen session. 

When you close the terminal window, what you were working on will still be there when you open the terminal.

-----------------

If you have never used or heard of screen, it is a terminal multiplexer which allows you to spawn new shells in the same terminal. 

It has a lot of other benefits as well. The link below is a good place to start:

[http://polishlinux.org/howtos/screen-tips-tricks/]("http://polishlinux.org/howtos/screen-tips-tricks/")

The usage of screen can seem overwhelming at first, but the benefits of using screen far outweigh the initial investment of time.

------------------

Some may not prefer this setup, but I find it very handy to only ever need a single gnome-terminal window. 

Others may find this setup restrictive, depending on their activities.

--------------------------

**[SIZE="5"]Making sure screen is installed:[/SIZE]**

GNU screen comes with Ubuntu, so it should be on your system. Open a terminal and type:

```
which screen
```

This should return:

```
/usr/bin/screen
```

If nothing is returned you need to install screen:

```
sudo apt-get install screen
```

--------------------

**[SIZE="5"]Creating a screen initialization file[/SIZE]**

1. First copy the system-wide screen initialization file from /etc/screenrc to your home directory:

```
cp /etc/screenrc ~/.screenrc_term
```

I chose to name it something other than just ~/.screenrc to indicate its particular purpose.

2. Edit the ~/.screenrc_term file and uncomment the line:

```
#startup_message off
```

so that it now reads:

```
startup_message off
```

This suppresses the startup banner that comes up when you open a new screen session.

-----------------------

**[SIZE="5"]Configure gnome-terminal to start and resume a screen session:[/SIZE]**

**Note:** I am running Intrepid, so the gnome-terminal dialogs and menus are slightly different than in past releases. 

1. Open gnome terminal and go to "Edit->Profiles".

2. The dialog that opens lists the available gnome-terminal profiles:

[CENTER][IMG]http://ubuntuforums.org/attachment.php?attachmentid=100566&stc=1&d=1232516285[/IMG][/CENTER]

3. Click "New" to make a new profile and call it Screen.

[CENTER][IMG]http://ubuntuforums.org/attachment.php?attachmentid=100564&stc=1&d=1232516285[/IMG][/CENTER]

4. After clicking "Create", you encounter the configuration dialog for your new gnome-terminal session. In the "Title and Command" tab:

[INDENT]a) Put "Screen" in the "Initial title" field.[/INDENT]
[INDENT]b) Check the box labeled "Run a custom command instead of my shell".[/INDENT]

5. Enter the following custom command in the box below that:

```
screen -c /home/alegir/.screenrc_term -dR -S terminal
```

The screen arguments are (from the screen manual page):

```
**-c file**     

Override the default configuration file from  "$HOME/.screenrc" to file.

**-dR**   

Reattach a session and if necessary detach or even create it first.

**-S sessionname**

When creating a new session, this option can be used to specify a meaningful name for the session. This allows screen to resume the same session.


```

Here is the configuration window afterwards:

[CENTER][IMG]http://ubuntuforums.org/attachment.php?attachmentid=100567&stc=1&d=1232516285[/IMG][/CENTER]

6. Click "Close", which brings you back to the list of profiles. Make sure to select your new profile for "Profile used when launching a new terminal" and click "Close".

**[SIZE="5"]How it behaves[/SIZE]**

[LIST]
[*]When you open a new gnome-terminal, you will find a screen session running.
[/LIST]

[LIST]
[*]If you run a command like 'top', close the gnome-terminal window, and re-open it, you should find 'top' still running.
[/LIST]

[LIST]
[*]The only time you will end up with a new screen session is if you close all buffers in the screen session, in which case screen itself terminates, causing the gnome-terminal to exit.
[/LIST]

[LIST]
[*]If the gnome-terminal is open and you happen to open "another" one, the window will disappear for a moment and reappear with no change.
[/LIST]

**There is one minor caveat:**

If you connect to a remote host through ssh, and then start a screen session at the remote host, you will be in a nested screen session.

So all screen commands at the remote host will have to be issued with "C-a a" instead of just "C-a". 

The second 'a' tells the local screen session that the commands apply to the remote, innermost screen session.

---

