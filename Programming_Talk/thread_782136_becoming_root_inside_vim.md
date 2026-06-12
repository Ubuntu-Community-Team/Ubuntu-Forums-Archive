---
title: "becoming root inside vim"
date: 2008-05-04
forum: Programming Talk
---

### Post by purpleidea on 2008-05-04
Hey,
too often when browsing as normal user in say /etc i:

$ vim <filename>

to start editing and then when i go to :wq to save i realize i had forgotten to start it all off with:

$ sudo vim <filename>

and i now don't have permission to save. I know that i can :w /tmp/x and then:

$ sudo cp /tmp/x /etc/<filename>

but i was wondering if someone perhaps knew of some nice vim trick i could do so that i can save without retyping all the text..., sort of the way you can "become root" from within aptitude

many thanks!
_J

---

### Post by LaRoza on 2008-05-04
> **purpleidea said:**
> 
but i was wondering if someone perhaps knew of some nice vim trick i could do so that i can save without retyping all the text..., sort of the way you can "become root" from within aptitude


Yes, run the editor with sudo when you do it.

---

### Post by dwhitney67 on 2008-05-04
I'm not aware of any trick, other than perhaps doing something (stupid) like changing the permissions of the file so that it is writable by a regular user, and then after the write is complete, reverting back to the original permissions.

While in vim, you can issue shell commands using the :!<cmd>, where <cmd> could be something like "sudo chmod 666 filename".  When you are done, repeat the command but change the permissions to 644.

Personally I think this is crude and should be avoided.  When you use vim to open a protected file, it tells you at the very bottom of the editor that it is a read-only file.  Try to get into the habit at looking at the bottom of the editor when you first edit a file.

---

### Post by samjh on 2008-05-04
> **purpleidea said:**
> but i was wondering if someone perhaps knew of some nice vim trick i could do so that i can save without retyping all the text..., sort of the way you can "become root" from within aptitudeI don't know of any tricks like that within vim.

You could always [FONT="Courier New"]:w ~/temp.file[/FONT] first and then [FONT="Courier New"]sudo cp ~/temp.file /destination/dir[/FONT] later.

---

### Post by stroyan on 2008-05-04
That is an interesting question.
I sometimes find myself writing temporary files and thinking "I'll be baack".
There is a sudo vi feature at
[http://www.vim.org/scripts/script.php?script_id=729](http://www.vim.org/scripts/script.php?script_id=729)
that has a special sudo prefix for opening a file with sudo.
Then you could actually use split buffers to merge in changes.

Taking a tactic from that script it would be possible to use a command map
to do an sudo write from a : command.
Warm up with putting this in .vimrc-
```
cmap w!! %!sudo tee > /dev/null % 
```
then modify a protected file and try to write with
:w
then
:w!
then
:w!!

Got it!

---

### Post by mssever on 2008-05-05
I make a wrapper for vim. I call this script ~/bin/vi (I'm used to typing vi instead of vim, anyway):```
#!/bin/bash

precommand=
for i in "$@" ; do
    if [ -f "$i" -a ! -w "$i" ] ; then precommand="sudo " ; break ; fi
done

exec ${precommand}vim "$@"
```This script runs vim with sudo if any file mentioned on the command line isn't writable.

For the way I work, this isn't risky. Everything (with a few minor exceptions) outside of $HOME isn't user-writable. So the only safety against accidentally doing something stupid is knowing what I'm editing--no matter whether I typed sudo or not.

---

### Post by purpleidea on 2008-07-10
> **stroyan said:**
> That is an interesting question.
I sometimes find myself writing temporary files and thinking "I'll be baack".
There is a sudo vi feature at
[http://www.vim.org/scripts/script.php?script_id=729](http://www.vim.org/scripts/script.php?script_id=729)
that has a special sudo prefix for opening a file with sudo.
Then you could actually use split buffers to merge in changes.

Taking a tactic from that script it would be possible to use a command map
to do an sudo write from a : command.
Warm up with putting this in .vimrc-
```
cmap w!! %!sudo tee > /dev/null % 
```
then modify a protected file and try to write with
:w
then
:w!
then
:w!!

Got it!

took me a bit of effort to figure this out, but ultimately this was the perfect answer / solution.
many thanks !

_J

---

### Post by 542 on 2008-09-02
> **purpleidea said:**
> took me a bit of effort to figure this out, but ultimately this was the perfect answer / solution.
many thanks !

_J

This is exactly what I'd also like to do - I've placed the line in my .vimrc and tried typing w!! which seems to do nothing. What am I missing?

---

### Post by MONODA on 2008-09-02
whenever that happens to me I just do :q! which should force it to save.

---

### Post by samjh on 2008-09-02
> **MONODA said:**
> whenever that happens to me I just do :q! which should force it to save.
Actually that forces vim to quit without saving. ;)

---

### Post by lunchlady55 on 2008-12-21
This is what you're looking for.

:w !sudo tee %

It will then print "press [ENTER] to continue" and warn you the file's changed.

---

### Post by singlow on 2009-03-24
maybe you are looking for:

:w !sudo tee %

you can save the file after authenticating, but you will return to the buffer as the original user and it will inform you that it was changed by another user and you can reload the buffer to continue.

edit: (or maybe I should have looked at results page 2 before figuring this out myself)

---

### Post by monkeyking on 2009-03-24
> **samjh said:**
> actually that forces vim to quit without saving. ;)

lol

---

