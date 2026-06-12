---
title: "[HOWTO] Edit as root, automaticall"
date: 2007-04-19
forum: Outdated Tutorials &amp; Tips
---

### Post by simplyw00x on 2007-04-19
This is for all the people in [this thread]("http://ubuntuforums.org/showthread.php?t=409852") that would like a prompt when editing files that they don't have permission to.

[COLOR="DarkSlateGray"][SIZE="4"]First: The command-line![/SIZE][/COLOR]
You want an alias, like the following:
```
vim () {
    for i in "$@" ; do
        if [ -f "$i" -a ! -w "$i" ] ; then precommand="sudo " ; break ; fi
    done

    ${precommand}/usr/bin/vim "$@"
}
```

Place in your bash aliases file, or in .bashrc, or really wherever you'd like that gets read at shell start-up. Replace 'vim' with $EDITOR, nano, emacs (...shudder) or even gedit (although you may want to add an additional test for the presence of X in this case).
This will check permissions on the file, and ask you via 'sudo' for your password if you need it. It doesn't (yet) test for files' existence, however, and creating a new file may result in it being owned by root. YMMV. You can replace sudo with gksudo if you'd like, but I personally hate gksudo, and not just because it won't work with beryl.

[COLOR="DarkSlateGray"][SIZE="4"]Second: The desk-top![/SIZE][/COLOR]
This is slightly more fiddly. Basically, you want the above function as an executable script somewhere, but it's up to you how this gets called. 
Obviously, having it as /usr/bin/gedit, and the gedit executable itself as /usr/bin/gedit-bin would work (as long as you called 'gedit-bin' within the script, of course :roll:), but would cause problems including (but not limited to):
[LIST]
[*]Unpredictable behaviour with remote files
[*]The script being over-written every time gedit updates
[*]No support for other programs, e.g. GIMP, which you might want to run as root on files
[/LIST]

[COLOR="Red"]**N.B. This tutorial is deliberately *not* 'n00b-friendly'. Feel free to ask questions, but if this is all way over your head, perhaps frequent editing of vital system config files is not the best idea. Just a thought.**[/COLOR]

EDIT: Another possibility would be gnome-open in a script like the one above, and then you could simply go right-click/open with/root-open on any file

---

