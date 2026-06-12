---
title: "Python Program Idea"
date: 2006-09-03
forum: Programming Talk
---

### Post by Note360 on 2006-09-03
This is a simple one. I am thinking of writing a program that does the following:

from the command line you type in 
```
appname *
``` 
I have not come up with a name yet

and that will move all the files in the current directory to a folder called .trash (if I decide not to integrate with gnome's trash) or .Trash (if I decide to integrate with gnome's trash). 

So basically the app(script is probably a better word) [LIST]
[*]Moves files to the trash.
[*]It will also be able to wipe (shred) or rm the trash depending on a command line option
ex)
```
appname --clean
or -c
``` 
or 
```
appname --wipe
or -w
```
[*]It should also allow you to select what you want to remove
ex)
```
appname --rm *tar.gz
or -r *.tar.gz
``` 
or 
```
appname --wipe *.tar.gz
-w *.tar.gz
```
[/LIST] 
What do you think?

---

### Post by skymt on 2006-09-03
I have basically that (minus the secure wiping) as a shell function in my .zshrc:
```
del() {
    if [[ $# -eq 0 ]]; then
        print 'Usage: del [OPTIONS] FILE ...'
        print 'Read the source for more information. Moron.'
        return 1
    fi

    if [[ -d ~/.Trash && -w ~/.Trash ]]; then
        mv $* ~/.Trash
    elif [[ ! -e ~/.Trash ]]; then
        mkdir ~/.Trash
        mv $* ~/.Trash
    else
        print '~/.Trash is not writable or is not a directory.'
        print 'Please fix.'
    fi
}
```
You may have to change that to make it work in Bash, I haven't tried.

Yes, it really does call me a moron. If I can't use my own shell function right, I deserve it. :mrgreen: 

It wouldn't really make much sense to include secure wiping, since that already exists (shred, installed by default) and doesn't have much to do with a command-line trash can.

---

### Post by Note360 on 2006-09-03
true, true. Its just that I write these apps for myself mostly and I happen to like wipe more than rm or shred.

Oh and my shell is actually fish not bash. (though bash is nice too)

---

### Post by LordHunter317 on 2006-09-03
There are already several programs that do that.

---

### Post by Note360 on 2006-09-03
Actually this relates back to my first app I ever made. It was on OS X in Applescript. It was a droplet that you put on your desktop and you could drag items to it and it would automatically move those items to .Trash . Ahh the ok old days.

---

### Post by Note360 on 2006-09-03
Here is a perl application that does what I want.
[http://people.csail.mit.edu/gremio/code/rmv.pl.html](http://people.csail.mit.edu/gremio/code/rmv.pl.html)

---

