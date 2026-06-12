---
title: "Looking for a text editor with specific features"
date: 2010-03-01
forum: Programming Talk
---

### Post by WarKirby on 2010-03-01
Having come from windows, to ubuntu karmic, I'm missing notepad++. I know I can run it in wine, and I may yet do that, but I'd really rather find a suitable replacement that runs natively in linux.

I have specific demands for a text editor though, which need to be met. I'm looking for a program which can do as many as possible of the following

1. Open multiple documents in tabs within a single window
2. Retains tabs that were left open, if you close the program and open it later, ideally including unsaved work
3. Can open the same document in multiple views
4. Can do a search/replace across all opened files
5. Can show line numbers in the left margin

These four things are key features of Notepad++ that I'm struggling to manage without.

1 is something Gedit manages to do, but that alone isn't sufficient.

 2 is by far the most important, though. At any given time, I'm working with 10+ open programs, manuals, and other documents, which are scattered all over my hard drive. I've been trying to work in gedit, and I waste a lot of time opening them one by one on every new session. I want documents to be retained in the editor until I close them individually, maintained across sessions.

3 I also find critical, since I can't remember what I named some variable 800 lines up, and it quickly becomes inefficient to scroll up the whole way to get it's name, and back down to write it in. being aarchive/index.phpble to have multiple views of the same document helps productivity greatly, as I can have one view at the variable declarations at tht etop, and another where I'm actually writing.

4 is a less used, but still quite important thing. It looks like Gedit doesn't have that. I use it quite often to correct design mistakes in a project with relative ease, like accidentally naming a variable in a manner not compatible with my usual scheme

5. line numbers are a no brainer for any coder. Gedit has this at least.

other features like language specific code highlighting are nice extras, but not necessary. The above 5 points are my most critical. And if there's nothing that can do all of them, anything that JUST does number 2 will suffice. 

Is there an app for me, or do I have to stick with windows software through wine ?

---

### Post by Simon17 on 2010-03-01
I am also a Windows user and I haven't found any decent alternative to notepad++. I have also tried running it in wine with less than satisfactory results.

What I am using right now is geany. It has a lot of IDE features, but is still light enough for use as a text editor. It doesn't have all the features of np++, but I'm content with it for now. Try it out and spend a few minutes messing with the settings to see how it works out.

---

### Post by swappo1 on 2010-03-01
Take a look at Geany.  I'm not sure if it does number three, but it has more features than Gedit.

---

### Post by oldfred on 2010-03-01
With geany I was not able to import a file twice. It does let you create projects that automatically open multiple files. I was able to search all files but it listed them all in the status bar by file & line number. I have not even used part of what geany has so I would at least recommend trying it. There are many settings to make things work the way you want.

---

### Post by WarKirby on 2010-03-01
Geany seems to do number 2 at least. good so far

---

### Post by sgosnell on 2010-03-01
Gedit does 2, with a plugin.  There are lots of plugins available for gedit, and I haven't investigated nearly all of them.  You might do a search for gedit plugins and see what you find.

---

### Post by snova on 2010-03-01
> **WarKirby said:**
> I have specific demands for a text editor though, which need to be met. I'm looking for a program which can do as many as possible of the following

1. Open multiple documents in tabs within a single window
2. Retains tabs that were left open, if you close the program and open it later, ideally including unsaved work
3. Can open the same document in multiple views
4. Can do a search/replace across all opened files
5. Can show line numbers in the left margin

I believe Kate can do all of these things, if you don't mind installing KDE stuff.

---

### Post by falconindy on 2010-03-01
Vim does all these things except #2, which I'm sure can be done -- [s]I just don't know how.[/s]

edit: Vim can be scripted to automatically create a session on logout, which will be restored on next startup. See [here](http://vim.wikia.com/wiki/Open_the_last_edited_file).

---

### Post by Queue29 on 2010-03-02
> **snova said:**
> I believe Kate can do all of these things, if you don't mind installing KDE stuff.

+1

KATE is the best thing I could find without getting into the heavy IDE's like eclipse or MonoDevleop

---

### Post by WarKirby on 2010-03-02
I'll consider Kate. For now, Geany seems to do almost everything, and I'm kind of settled into it now.

Consider this issue solved

---

### Post by cacycleworks on 2010-03-02
I currently use Quanta+ and am running ubuntu 9.10. Quanta is almost an IDE wrapped around Kate. You have to go into the options or preferences to turn on line numbering. I don't think it will retain unsaved work.

Kate (and thus KDevelop and Quanta+) open multiple files into tabs and absolutely will reopen all the files that were open upon the last close.

KDevelop has the ability to side-by-side 2 files, including the same file.

Quanta+ has php code completion and will search includes to find class functions and try to show you those, too. Quanta+ also has a class/function browser in the left pane. 

Kate also has sessions. I haven't bothered to see what Quanta+ does with sessions, but at one time I had 4 or 5 different sessions I would regularly use in Kate, each with a dozen or so of their own files. Coupled with some sshfs remote filesystem mounting, all yours sites can belong to you without ftp, etc.

Kate is an outstanding editor and I cannot recommend it highly enough. There is syntax highlighting for anything imaginable... assembly, sql, all languages.

:) Chris

---

### Post by cacycleworks on 2010-03-02
oh and Quanta and KDevelop can find/replace across files, including subdirectories. I don't know about Kate.

The one bone I have to pick with Kate is that you cannot search and replace newlines. Each line is a separate chunk of code and they're not linked together. Otherwise, with the regular expressions, you can make some creative and powerful search/replaces.

:) Chris

---

### Post by WarKirby on 2010-03-02
Marking unsolved again, geany isn't quite suitable enough.
So, trying Kate now. A few annoyances that come to mind:

If I open a file with it (right click > open with > kate) it creates a new session just for that file. This is annoying. is there any way to make it automatically add newly opened files to the existing session, [B]in the same window

[/B]Is there any way to not make it display the session name in the taskbar at the bottom**? **When I've got 10+ apps open, I need every millimetre of space down there to see the name of what's open. "Default session" is useless to me. For now I've just renamed the session to . becuase it wouldn't let me use a blank string, but it still takes up 3 chars before the filename.

In general i don't care for the concept of seperate sessions. I want one session, period, ever. And have all files open within it.

---

### Post by CptPicard on 2010-03-02
Of course Emacs does everything too, but I suspect the learning curve is a bit steep ;)

---

### Post by cacycleworks on 2010-03-02
I believe that googling kate a little bit can fix your multi-session issues. I forgot how my work flow went, but I'm not one to use right-click to open & edit files.

Also, do try Quanta+ and KDevelop. Although they are built upon Kate, they absolutely have some differences. It may be that Quanta can be configured to not allow multiple instances and I believe that while it saves all the open windows, I also know that I'm never presented with the Session dialog that Kate did...

:) Chris

---

### Post by michaelzap on 2010-03-02
> **WarKirby said:**
> Marking unsolved again, geany isn't quite suitable enough.
Can I ask why not? I'm a Notepad++ fan myself, and I've settled on Geany in Linux. I'm not always 100% happy with it either, but it does seem to meet your four requirements.

---

### Post by TheStatsMan on 2010-03-03
> **falconindy said:**
> Vim does all these things except #2, which I'm sure can be done -- [s]I just don't know how.[/s]

edit: Vim can be scripted to automatically create a session on logout, which will be restored on next startup. See [here]("http://vim.wikia.com/wiki/Open_the_last_edited_file").


Another way is

to save
:mksession name

to load
:source name

---

### Post by jpkotta on 2010-03-06
> **CptPicard said:**
> Of course Emacs does everything too, but I suspect the learning curve is a bit steep ;)

Yep.

> **WarKirby said:**
> 
1. Open multiple documents in tabs within a single window

Emacs has a tab mode but it doesn't really work like other editors' tabs.  Also, I've had trouble with it "acting weird".  Then I realized that tabs are a particular solution to a problem, and there are other ways to solve it.  

What I do is use ido-mode to quickly switch buffers.  ido-mode scales better than tabs when you start to have dozens of buffers.  You can also use the speedbar if you like the mouse.  [http://www.emacswiki.org/emacs/InteractivelyDoThings](http://www.emacswiki.org/emacs/InteractivelyDoThings)

> 2. Retains tabs that were left open, if you close the program and open it later, ideally including unsaved work

There are many solutions to this, but I use save-visited-files-mode.  It's simple and works well.  [http://nflath.com/2010/01/save-visited-files-v12/](http://nflath.com/2010/01/save-visited-files-v12/)

> 3. Can open the same document in multiple views

In Emacs, there is a clear distinction between the text being edited (the buffer) and the view of the buffer (the window).  Split the frame into several windows with C-x 2 or C-x 3, and switch to the same buffer in different windows.  (N.B. "frames" are what the rest of the world calls windows and "windows" are subdivisions of a frame)

> 4. Can do a search/replace across all opened files

I use findr.  [http://www.emacswiki.org/emacs/FindrPackage](http://www.emacswiki.org/emacs/FindrPackage)

> 5. Can show line numbers in the left margin

I use linum-mode.  It's included in Emacs 23.  [http://www.emacswiki.org/emacs/LineNumbers#toc4](http://www.emacswiki.org/emacs/LineNumbers#toc4)

> In general i don't care for the concept of seperate sessions. I want one session, period, ever. And have all files open within it.

I run Emacs in daemon mode (need Emacs 23), and open files with emacsclient.  This also gets around the problem of Emacs taking forever to start up (mine is ~2 s, which is too long for quick edits).

---

### Post by wannabegeek on 2010-03-07
hi all,

Is there a vim text high light in the repos for matlab .m  scripts ?

thanks
wbg

---

### Post by LKjell on 2010-03-07
> **wannabegeek said:**
> hi all,

Is there a vim text high light in the repos for matlab .m  scripts ?

thanks
wbg

Try [http://www.mathworks.com/matlabcentral/fileexchange/21798-editing-matlab-files-in-vim](http://www.mathworks.com/matlabcentral/fileexchange/21798-editing-matlab-files-in-vim) .

Extract it to your ~/.vim/

---

### Post by wannabegeek on 2010-03-07
thanks LKjell

I saw that but was afraid to try an install...I don't have a .vim directory...I made one
I did make a .exrc in my home dir.

I'll try it ...

update:
I found the docs. Is this package is for vim gui ?
I have been learning the terminal version. Do I need the full vim package installed to use 
the matlab features ?

thanks again...
wbg

---

### Post by cacycleworks on 2010-03-07
There are a number of vim packages. One of them comes with highlighting, maybe this one would be a great start before adding your matlab code?

---

### Post by wannabegeek on 2010-03-07
I get it now!

I have a .exrc file I added for line numbering, so I just opened the file in pico and read in the indent script and syntax script from the MathWorks blog site.

now when I start vim I have auto indent and highlights !

I only use vim for matlab so turning it off isn't such a big deal.

I suppose eventually I will want to...

wbg

---

### Post by cacycleworks on 2010-03-07
I've got a text file I call useful_cli.txt and in it are hints and tricks I've gathered from the net. It's almost always open in my editor. And lately, it is joined by its friends mysql_cmds.sql and pql_tricks.sql ... 

Here's the vi section from my useful_cli.txt file:
```

-----------------------------------------------------------------
>>>>> vi <<<<<<<<
http://staff.washington.edu/rells/R110/
se list lcs=tab:»· nowrap
:se list		" see tabs
:set lcs=tab:»·	" set tab as » and trailing spaces as ·
:set nowrap
:1,$s/oldstring/newstring/g  "This will change oldstring into newstring wherever it occurs throughout the entire text. The  1  (the number one) in the above command means "start the search on the first line". The  $  means "end the search on the last line". The  g  at the end executes the change globally on each line. If you omit the  g , the search will stop after finding the first occurrence of oldstring. 
:set nu 	" Display line numbers 
:set nonu 	" Hide line numbers.

Search/Replace:
vim filename
:g/\n/s//replaceword/gc
This will ask interactively y/n for replacing it.
You guys are really persistent - VI is tracking me down;-) (in the reinkarnation of VIM)
Here is a funny step by step guide that I found useful: 
    http://www.vi-improved.org/tutorial.php

-----------------------------------------------------------------

```

---

### Post by wannabegeek on 2010-03-07
thanks ca, I'll look it over...it seems a bit over my head at the moment...

I have another question, related perhaps...

Using the esc key to exit command mode kinda sucks on my keyboard layout.
Can I use :map to change it?

tia,
wbg

---

### Post by LKjell on 2010-03-07
Depends on how good you are to type touch but you can either use ctrl + c to get to normal mode or just map Caps lock to another ESC or swap Caps lock with ESC. You can do the maping in gnome-keyboard-properties.
You see on old keyboards ESC is located where Caps lock is now.

---

