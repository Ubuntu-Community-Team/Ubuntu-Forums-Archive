---
title: "I need help to configure environement"
date: 2008-01-17
forum: Programming Talk
---

### Post by Green_Star on 2008-01-17
Hi everyone,

At my office I have a software running on unix, i have to frequently use Ctrl+X to run some report, Ctrl-E to exit from sub menu etc in this software. It will be useful if i can use numpad <Enter> for Ctrl+X and <Esc> for Ctrl+E.

So there is no option in that software to map these keys for that use, is there any way to write my own shell program and run it in .profile so that these keys will remapped as i wish? 

Thanks a lot.

---

### Post by naugiedoggie on 2008-01-17
> **Green_Star said:**
> Hi everyone,

At my office I have a software running on unix, i have to frequently use Ctrl+X to run some report, Ctrl-E to exit from sub menu etc in this software. It will be useful if i can use numpad <Enter> for Ctrl+X and <Esc> for Ctrl+E.

So there is no option in that software to map these keys for that use, is there any way to write my own shell program and run it in .profile so that these keys will remapped as i wish? 

Thanks a lot.

Hello,

If you are in X, then you might be able to use xmodmap.  If you are running in a terminal, bash uses an .inputrc file that allows some key remapping.  However, it does not appear to me that a similar option is likely available in ksh or sh, which are the two common commercial unix shells.

Thanks.

mp

---

### Post by Green_Star on 2008-01-17
thanks man.

this is the version of OS i am using, HP-UX B.11.23 U 9000/800. If your editing .inputrc file works in this OS, then could you please tell me where to edit this file and how to edit? i mean what codes i need to give for specific keys?

---

### Post by naugiedoggie on 2008-01-17
> **Green_Star said:**
> thanks man.

this is the version of OS i am using, HP-UX B.11.23 U 9000/800. If your editing .inputrc file works in this OS, then could you please tell me where to edit this file and how to edit? i mean what codes i need to give for specific keys?

Hello,

AFAIK, .inputrc is bash-specific.  

'echo $SHELL' will tell you what shell you are using.  I suspect it's /bin/sh, but you might get lucky.  Customization in Bourne shell is minimal.  You can do more in ksh, but I have only slight experience with it.  For some reason, I never liked it and always used csh and bash.

One thing you can do, even if your login shell is /bin/sh, is start a new shell just by typing '/bin/bash' at the prompt -- if bash is on the system.  

In my experience, commercial Unix systems are highly specialized and user behavioral options severely restricted.

Now that I think about it, your best bet for an indepth answer is probably going to be the newsgroup [comp.unix.shell]("http://groups.google.com/group/comp.unix.shell/topics?hl=en").  A lot of real Unix gurus hang there.

Thanks.

mp

---

### Post by Green_Star on 2008-01-24
thanks guys, 

Any ways I use this application on Win-xp via telnet client putty. is there any easy way to replace these keys on windows side (by tricking putty or running some free hotkey application which doesnt required installation)

<Numpad Enter> should send <Ctrl-X>      (keyboard enter shouldn't change)
<Esc> should send <Ctrl-E>

those only two keys i need badly because i hit Ctrl-X and Ctrl-E keys almost every 30 secs less, and it is little pain to press those combination that frequently.

---

