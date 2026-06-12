---
title: "[SOLVED] Nano, vi, gedit ....... what, when, where &amp;amp; why?"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by kansasnoob on 2008-07-05
Just curious. when restoring my sudoers yesterday I had to (or chose to) change my text editor to gedit ( I just couldn't get vi to do what I wanted to do), but I'm totally mind boggled.

Can someone explain the nano, vi, gedit relationship?

Does hardy use vi exclusively? Or for only certain progs?

Why vi? Gedit worked fine in Gutsy!

Is vi more secure?

NOOb questions ........... sorry!

---

### Post by avtolle on 2008-07-05
Gedit is a gui based text editor; vi is strictly command line (no graphics); nano has a "menu" at the bottom for commands. The three all do the same thing, that is, allow the user to edit text files (and more, in some cases, but for this discussion, that will do). Vi is the "old stand-by", but for a new user requires learning commands before it may effectively be used. Nano, with its "menu" is easier to use from the CLI; and gedit requires a running X system to operate. So, to further lengthen this, if the X system is running, and if you feel more comfortable with a GUI type interface, use gedit; if X is not running, then a CLI editor must be used, and nano is easier for a new user than vi. HTH.

---

### Post by Fass on 2008-07-05
Hardy does not use vi exclusively - it uses what you want to use. The thing is, the default for the sudoers file is that it be edited by visudo and visudo defaults to using vi. You can change which editor it uses by changing your shell's EDITOR variable.

Why visudo? Well, the man page says:

> visudo edits the sudoers file in a safe fashion, analogous to vipw(8). **visudo locks the sudoers file against multiple simultaneous edits, provides basic sanity checks, and checks for parse errors.** If the sudoers file is currently being edited you will receive a message to try again later.

---

### Post by avtolle on 2008-07-05
> **Fass said:**
> Hardy does not use vi exclusively - it uses what you want to use. The thing is, the default for the sudoers file is that it be edited by visudo and visudo defaults to using vi. You can change which editor it uses by changing your shell's EDITOR variable.

Why visudo? Well, the man page says:
AH, context is everything, isn't it; I completely read over the fact that he was editing the sudoers file. As you note, another editor may be used by changing the EDITOR variable.

---

### Post by ibuclaw on 2008-07-05
using Vi to edit the sudoers file is a bug fix.

Since the actual name "visudo" implies **vi** is the editor, it was set as the default in the upstream, and imported into Hardy as is.

Vim doesn't have any confusing behaviour about it (infact, it improves work load drastically when you learn how to use it)

Check out vimtutor, just type in
```
vimtutor
```
in the terminal. And read the file that teaches you the basics of how to use it (takes about 40 minutes to get through).

If the terminal isn't for you, I recommend **gvim**
```
sudo apt-get install vim-gtk
```
[EDIT]
then put this function inside your ~/.bashrc file
```

function vimtutor {
    tmptutor="$HOME/.vimtutor"
    tutorfile="/usr/share/vim/vim71/tutor/tutor"
    cp $tutorfile $tmptutor
    gvim $tmptutor
}

```
    

But, back on track.
To change it to gedit/nano.
Put in your ~/.bashrc file
```
[ $DISPLAY ] && export VISUAL="gedit" || export EDITOR="nano"
```
Close and reopen a new terminal.
Then run
```
sudo -E visudo
```
And put in the following that is in **bold**
```

**Defaults        env_keep = "EDITOR VISUAL"**
Defaults        env_reset

```
Save and quit.
And now
```
sudo visudo
```
Will open up in your preferred editor.

Regards
Iain

---

### Post by kansasnoob on 2008-07-05
Well, to get the whole "backstory": you must look here:

[http://ubuntuforums.org/showthread.php?t=849176](http://ubuntuforums.org/showthread.php?t=849176)

And here:

[http://ubuntuforums.org/showthread.php?t=850347](http://ubuntuforums.org/showthread.php?t=850347)

Now, to solve my sudoers prob I ended up having to :

> Update for Ubuntu 8.04: The default editor for visudo has changed to vi. To change this behavior, using any editor,

gedit ~/.bashrc

Add the lines :

[ $DISPLAY ] && \
export VISUAL="gedit" || \
export EDITOR="nano"

Replace "gedit" with vim, nano, kate, mousepad, any editor you like. Same is with "nano", but only replace it with a terminal specific editor, such as vim, emacs or ee.

Now launch visudo with sudo -E visudo in the terminal, and put in the command Defaults env_keep = "EDITOR VISUAL" in the file before the Defaults env_reset line.

So the file should now look like this:

Defaults        env_keep = "EDITOR VISUAL"
Defaults        env_reset

Save, and from now on launching visudo with gksu visudo for Ubuntu; kdesu visudo for Kubuntu or sudo visudo in the terminal will now open with your chosen editor.

The sudoers file is read in one pass so when multiple entries match for a user, they are applied in order. Where there are conflicting values, the last match is used (which is not necessarily the most specific match). Also you must set an alias before you can use it. Normally you will set the aliases at the beginning of the file and then set the user specifications after all the aliases are laid out.

You can insert comments by prefixing them with a # but this is also used to specify a uid in certain parts of the file when it is followed by a number. 

And I got that from:

[https://help.ubuntu.com/community/Sudoers#The%20Default%20Ubuntu%20Sudoers%20File](https://help.ubuntu.com/community/Sudoers#The%20Default%20Ubuntu%20Sudoers%20File)

That combined with forum help got me out of the woods!

Now I'm just wondering why I had to change text editors? In Gutsy I edited sudoers to make firestarter load at startup without having to do that. (I know now that's foolish)

But then it appears that a text editor change could be needed here:

[http://ubuntuforums.org/showthread.php?t=850347](http://ubuntuforums.org/showthread.php?t=850347)

Comment #8.

I'm just trying to learn ................. ever so slowly:confused:

---

### Post by kansasnoob on 2008-07-05
tinivole,

I am/will keep reading vimtutor.

How would I know that vi and vim are related?

The only dumb question is the one that goes unasked, eh?

---

### Post by original_jamingrit on 2008-07-05
VI is the original, VIM is supposed to be VI Improved.  VIM has a lot more functionality, but some people still prefer VI because it was/is simpler to use.

---

### Post by kansasnoob on 2008-07-05
> **Fass said:**
> Hardy does not use vi exclusively - it uses what you want to use. The thing is, the default for the sudoers file is that it be edited by visudo and visudo defaults to using vi. You can change which editor it uses by changing your shell's EDITOR variable.

Why visudo? Well, the man page says:

Excellent explanation!

I'm just catching up.

---

### Post by kansasnoob on 2008-07-05
Thanks all. I'm going to mark this solved so as not to distract from those needing actual help.

This will take a bit of studying. But thank you all!

---

### Post by ibuclaw on 2008-07-06
> **kansasnoob said:**
> Well, to get the whole "backstory": you must look here:

[http://ubuntuforums.org/showthread.php?t=849176](http://ubuntuforums.org/showthread.php?t=849176)

And here:

[http://ubuntuforums.org/showthread.php?t=850347](http://ubuntuforums.org/showthread.php?t=850347)

Now, to solve my sudoers prob I ended up having to :



And I got that from:

[https://help.ubuntu.com/community/Sudoers#The%20Default%20Ubuntu%20Sudoers%20File](https://help.ubuntu.com/community/Sudoers#The%20Default%20Ubuntu%20Sudoers%20File)

That combined with forum help got me out of the woods!

Now I'm just wondering why I had to change text editors? In Gutsy I edited sudoers to make firestarter load at startup without having to do that. (I know now that's foolish)

But then it appears that a text editor change could be needed here:

[http://ubuntuforums.org/showthread.php?t=850347](http://ubuntuforums.org/showthread.php?t=850347)

Comment #8.

I'm just trying to learn ................. ever so slowly:confused:

Haha!
I wrote that Wiki. :lolflag:

Regards
Iain

---

