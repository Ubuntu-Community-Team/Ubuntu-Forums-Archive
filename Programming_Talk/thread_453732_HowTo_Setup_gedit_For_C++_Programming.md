---
title: "HowTo: Setup gedit For C++ Programming"
date: 2007-05-24
forum: Programming Talk
---

### Post by Sabot on 2007-05-24
Here are a few settings that I set to make it easy for me to code in C++ using gedit:

1. Edit>Preferences>View>Bracket Matching>Highlight Matching Bracket
2. Edit>Preferences>Editor>Tab Width 4
3. Edit>Preferences>Editor>Automatic Indentation>Enable Automatic Indentation
4. Edit>Preferences>Syntax Highlighting>Highlight Mode>C++

If you have any additional tips please add them below.

---

### Post by BitTorrentBuddha on 2007-05-24
Also, if you're looking for an app with a bit more gusto, check out scite, it's in the repositories.

---

### Post by kanem on 2007-05-24
I show tabs and spaces (draw spaces plugin). You can pick the colour. Mine is very light grey so I can see them but they are not distracting.

I also have an integrated terminal at the bottom (another plugin). Better for me than having to keep going to a separate terminal to compile and run.

Word completion. Another plugin which isn't included by default. You can get it (and other experimental plugins) [here](http://live.gnome.org/Gedit/Plugins). It wasn't exactly the way I liked it, but since these plugins are written in Python, they're easy to change.

For me, these are all really useful regardless of what language I'm using. Would have been really helpful if I had known about them when writing my thesis in LaTex.

---

### Post by WW on 2007-05-24
Use the "External Tools" plugin.  For compiling a single C++ file, you can set up gedit so that a single key will compile the program.  For example, you can set up a **g++** tool with options set up like this:
```

Description:   g++
Accelerator:   F5
Command(s):    g++ $GEDIT_CURRENT_DOCUMENT_NAME -o ${GEDIT_CURRENT_DOCUMENT_NAME%.*}
Input:         Nothing
Output:        Insert in output panel
Applicability: All documents

```
With this tool set up, hitting the F5 function key opens up a console at the bottom of the window and runs g++ there.  And with this:
```

Description:   Run
Accelerator:   F6
Command(s):    ./${GEDIT_CURRENT_DOCUMENT_NAME%.*}
Input:         Nothing
Output:        Insert in output panel
Applicability: All documents

```
hitting the function key F6 will run the program.

(This idea was taken from [this thread]("http://ubuntuforums.org/showthread.php?t=433538").)

For a program with multiple source files, create a Makefile, and use the **Build** tool to run make.

---

### Post by engla on 2007-05-24
There are some plugins that could be useful. Of course the Text Snippets plugin is hugely useful for programming, for example for C++. Also the External Tools plugin is useful to let you run 'make' etc from gedit..

Third-party plugins are available at [the gnome wiki]("http://live.gnome.org/Gedit/Plugins#third_party"), I haven't tried them but some could be useful (like reindent, project manager, class browser etc..)

---

### Post by kknd on 2007-05-24
I still preffer Vim =)

Code completion (C/C++) + TextMate like snippets = Good one =)

---

### Post by Sabot on 2007-05-24
Kanem what are the actual names of the plugins that you mention in your comment?  I was not able to find an exact match for the terminal and the space showing plugins.  Thanks! They both seem very interesting.

---

### Post by kanem on 2007-05-25
> **Sabot said:**
> Kanem what are the actual names of the plugins that you mention in your comment?  I was not able to find an exact match for the terminal and the space showing plugins.  Thanks! They both seem very interesting.
Draw Spaces and Integrated Terminal. The terminal is in the gedit-plugins package you can get from Synaptic. I'm not sure where I got the Draw Spaces one. I think it came with gedit.

Word completion is a third party plugin under development that can be found on the same page I linked to, after the official ones. There are two versions for you to pick from.

---

### Post by Sabot on 2007-05-25
> **kanem said:**
> Draw Spaces and Integrated Terminal. The terminal is in the gedit-plugins package you can get from Synaptic. I'm not sure where I got the Draw Spaces one. I think it came with gedit.

Word completion is a third party plugin under development that can be found on the same page I linked to, after the official ones. There are two versions for you to pick from.

I was able to find the location of Drawspaces and another one that would be helpful called codecomment (it allows you to quickly comment out code).

[http://www.gnome.org/~pborelli/gedit-plugins/](http://www.gnome.org/~pborelli/gedit-plugins/)

To install the files read the readme at this same web location.

---

### Post by tht00 on 2007-05-25
I don't see the built in terminal being very useful... at least not for me.  I prefer to code with a text editor (usually gedit) and then I just keep a terminal handy.  I always use another workspace for coding, so I'm no overwhelmed with extra/non-important programs I've got up.

Ctrl+S
Alt-Tab
[up][up][Enter]  (Resends compile command)
[up][up][Enter]  (Resends run command)

Efficient enough for me.  Keeps my mouse movement to a minimum too. 

I may look into some other text editors though... see what all the rave is about emacs and vim, but it is hard to switch to something else when gedit 'just works'.

My $.02 anyways. :p

---

### Post by mr bob on 2007-07-13
Is it possible to setup gedit so it automatically highlights .h files with C++ syntax rather than C syntax? Currently I have to go into preferences for each file.

---

### Post by runningwithscissors on 2007-07-13
NowI don't use gedit, so can't help you, but why not use .hh as an extension for C++ headers? I think most editors would then recognise it as a C++ header file.

---

### Post by brunovecchi on 2008-01-13
I wish gedit had block folding.

---

### Post by nathanpc on 2009-07-16
Hello,
 This is a good question, because i'm trying to do the same thing.

---

