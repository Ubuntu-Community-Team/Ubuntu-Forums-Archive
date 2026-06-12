---
title: "PHP XDebug vs. Ubuntu"
date: 2010-03-11
forum: Programming Talk
---

### Post by jqp on 2010-03-11
I recently discovered XDebug for PHP and don't know how I made it this long in life without it.  But on Ubuntu I've had a really hard time finding an editor/IDE that does well wtih XDebug:

Eclipse is bloated and slow.  I can't get the debugger to work well without creating an entire 'Project' and letting it scan a series of subfolders just to edit a single file.  I can't get the debugger to work well without going through all that.

Netbeans is just as bad if not worse about being slow and requiring you to set up a 'Project' just to get debugging to work properly.

Komodo is nice, but Komodo gets slow when editing a large file (a PHP class file 2000+ lines).  When I type in Komodo, I can type faster than it can render letters on the screen.  Also, I can't tweak the interface the way I want, really.  I open a lot of files, so a Kate-style document list would be handy.  If Komodo wasn't slow on large files, though, it might be my best choice.

Protoeditor is exactly what I want: a simple text editor with xdebug support.  But it's a little 'unfinished': debugging variables only goes one level down a tree, the interface doesn't configure very well, it crashes, it insists on doing an HTTP request when you start the debugger with no option to just start the debugger.  Also it's an old KDE3 app.  But it would have been the right program.

I also tried Quanta 3 and it didn't work either.  It just crashed a lot.  (I'm on Ubuntu 9.04 with some kde4 apps installed)

I even tried Notepad++ in wine, and it also worked REALLY well, except as a wine application, opening files is a little clunky.  Also it tends to crash and give me some wine errors once in a while (I got stuck on a GetServerName error, I think)

KDevelop4 will support PHP and XDebug, but I can't find a binary to try out, and I couldn't get through the compilation instructions.  It looks like it'll be wonderful when the binary is released, though.

So, anybody know of any better solutions?  is there a binary of the Kdevelop4 php plugin yet?  Am I just doing it wrong in eclipse?  Can Komodo be made to run faster (I've tried various tweaks, like completely disabling the code explorer)

---

### Post by Hellkeepa on 2010-03-11
HELLo!

Personally I use Zend Studio for PHP development, and I'm quite pleased with it. Has a few issues from being based upon Eclipse, but the advantages far outweigh the negatives (and the negatives are getting cleaned up, one by one).
Now, I can't say whether or not it'll be faster than just Eclipse for you, but I usually don't have any problems with it being slow. Only for a little bit, if I've left it alone for a couple of days and its data has been swapped.

Might be worth a try, at least.

Happy codin'!

---

### Post by jqp on 2010-03-18
One of the big issues with me for Eclipse is that you can't debug* without using a project, and then Eclipse insists on 'refreshing' the entire project before the debugger will run.  And my situation is that our code isn't organized well enough to put into a project effectively, or if you do, it's thousands of files that take forever to 'refresh' in a project.  That's fixing itself over time in our work projects, but for foreseeable future the messy thousands of files are a fact of life for me.  While Komodo (for example) will happy edit a single file and debug without that problem.

*Actually, the debugger will run, but it won't find source code properly and show on screen the position of code execution, breakpoints, etc.  The debug console will show what's happening but the code editor won't.

I don't know if Zend Studio is any better.  Plus, that's a lot of money for something other programs are SO CLOSE to doing for free.  I'm glad it works for you, though... maybe I just need to cram some more hardware into the work machine and find a workaround for the project refreshing...

---

### Post by Visko on 2010-05-01
Count me in, I'm in the same boat.

Looking for a simple, lightweight, notepad++ like debugger client for XDebug. I don't mind if it sucks for editing, I only need it once in a while for debugging, since I'm coding in Vim. (have tried the debugger client for it, didn't work out)

---

