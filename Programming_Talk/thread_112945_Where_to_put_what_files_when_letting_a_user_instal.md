---
title: "Where to put what files when letting a user install my program?"
date: 2006-01-05
forum: Programming Talk
---

### Post by red_Marvin on 2006-01-05
I am developing a small console program that has linux as one of it target platforms.
Now, the project has grown in a direction that it would be good to make a "user options" file, perhaps in $HOME/.programname
Now would that place be the best to put the file? Also when going this far it would perhaps be practical to have a global installation
so I can reach the program from cli by typing the name, without the hazzle of doing a lot of cd'ing to get in the right directory.

So:
Where would I put the bin file? (do I have to enter it in a database or something)
Where would I put eventual data files?

Should I look into sh (bash?) scripting or deb packages to make an install?
Got any other tips?

...yes it's open source, I just haven't figured out a good way to include the gpl text file yet...


EDIT: Just discovered that there is a packaging and compiling subforum, if a mod considers it to be the more accurate forum, please move my thread...

---

### Post by dcraven on 2006-01-05
I suggest looking into the GNU autotools for installation in the proper places. That way a user can also specify a prefix, and dependancies can be checked etc. It generally helps portability across Unix-like platforms.

In general though, such executables could be put in /usr/local/bin and the required data could be put in /usr/local/share. These are for global usage. For a user only install, I typically stick executables in ~/bin with an entry like the following in my ~/.bashrc file:
```
PATH=$HOME/bin:$PATH
```

HTH,
~djc

---

### Post by David Marrs on 2006-01-06
what is /opt typically used for. Would it be suitable here?

---

### Post by dcraven on 2006-01-06
[QUOTE=David Marrs]what is /opt typically used for. Would it be suitable here?[/QUOTE]
Hmmm.. I'm not sure what /opt is "officially" for, but it is (I think) typically used for things like binary only static applications and such. I use it for the installation of test packages like gtk/pygtk testing versions etc. Some distrobutions use it for different things, I'm not sure there is a strict definition of what belongs there but I could be wrong.

You'd probably have more difficulty installing there as well because many distrobutions don't include /opt in the default $PATH. Ubuntu, in fact, is one such distro.

I would stick to autotools and the standard installation paths. If you do something non-standard, you'll have huge problems if users use your application across multiple Unices or even Linux distrobutions.

HTH,
~djc

---

