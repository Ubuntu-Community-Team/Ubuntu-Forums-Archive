---
title: "[git] commit(ing) from editor"
date: 2010-10-08
forum: Programming Talk
---

### Post by phoda on 2010-10-08
i have a very simple question:

gedit is my default (commit) editor. in the terminal, when i type 'git commit -a', it is opened; then i type a commit message using gedit, save it, but git doesn't effectively commits!

so, when i type 'git status', it doesn't show me 'nothing to commit' message...

what should i do, in order to fix this problem?

---

### Post by StephenF on 2010-10-08
It won't actually do the commit until the editor exits. The other prerequisite for a commit is a non empty commit message. Lines starting with # don't count and neither do lines containing only white space.

The save of the commit message needs to occur before the editor exits. If gedit is already open for any reason and you open another gedit instance the new gedit quits immediately after instructing the currently running gedit to open another tab. By trying to be clever gedit makes itself unsuitable for being the git commit message editor.

If you need a very simple editor (and that's all you need for this task) try nano.

Edit:
At the very least the editor needs to load save and quit in that order and in a single process.

It seems to me the problem stems from gedit not following [Unix philosophy]("http://en.wikipedia.org/wiki/Unix_philosophy").
gedit
   1. [s]Small is beautiful.[/s] (nearly as big as Bash, a programming language of sorts)
   2. [s]Make each program do one thing well.[/s]
   3. Build a prototype as soon as possible. (shrug)
   4. [s]Choose portability over efficiency.[/s] (tied to the Gnome libraries)
   5. [s]Store data in flat text files.[/s] (gconf)
   6. Use software leverage to your advantage. (heavy use of Gnome libraries - see 4)
   7. [s]Use shell scripts to increase leverage and portability.[/s]
   8. [s]Avoid captive user interfaces.[/s] (yeah I know it's an editor)
   9. [s]Make every program a filter.[/s] (this is where it fails git)

git
   1. Small is beautiful.
   2. Make each program do one thing well. (it deviated somewhat when git-xxx became git xxx)
   3. Build a prototype as soon as possible. (this was running within weeks)
   4. Choose portability over efficiency. (git is multi-platform)
   5. Store data in flat text files. (the git object store is flat as hell)
   6. Use software leverage to your advantage. (uses an external editor)
   7. Use shell scripts to increase leverage and portability. (no shortage)
   8. Avoid captive user interfaces. (the interactive editor is optional)
   9. [s]Make every program a filter.[/s] (the sane design choice was to not although git filters on the repository)

---

